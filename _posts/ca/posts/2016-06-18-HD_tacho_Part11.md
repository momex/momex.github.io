---
type: posts
layout: post
lang: ca
comments: true
title: Tacòmetre Digital per a Harley Davidson Sportster (Part 11 - Codi font i llibreries)
name: HD-tacho-part11
permalink: HD-tacho-part11
category: tacho
keywords: HD, harley, davidson, tachometer, tacho, tacòmetre, rpm, J1850, codi, llibreries
---
<p>
<font size="2"> 
<a href="/HD-tacho-part1">Part1 </a>/
<a href="/HD-tacho-part2"> Part2 </a>/
<a href="/HD-tacho-part3"> Part3 </a>/
<a href="/HD-tacho-part4"> Part4 </a>/
<a href="/HD-tacho-part5"> Part5 </a>/
<a href="/HD-tacho-part6"> Part6 </a>/
<a href="/HD-tacho-part7"> Part7 </a>/
<a href="/HD-tacho-part8"> Part8 </a>/
<a href="/HD-tacho-part9"> Part9 </a>/
<a href="/HD-tacho-part10"> Part10 </a>/
<b>Part11</b> /
<a href="/HD-tacho-part12"> Part12 </a>/
<a href="/HD-tacho-part13"> Part13 </a>/
<a href="/HD-tacho-part14"> Part14 </a>/
 Part15
 </font>
</p>
Un cop pujat el codi al nou repositori de Github (<a href="https://github.com/momex/DIGTACHO" target="_blank">DIGTACHO</a>), en aquesta entrada miraré de resumir les parts més importants del projecte. Com es veu a continuació, caldria separar els fitxers del repositori en 4 grups diferents:<br>

<b>Llibreries genèriques</b><br>
- cdefs.h<br>
- inttypes.h<br>
<b>Nota</b>: <font size="3">altres llibreries necessàries per compilar aquest projecte com p18f2553.h, timers.h, string.h, usart.h, stdio.h, pwm.h ja estan incloses al <i>software</i> MPLAB de Microchip i per això no estan incloses aquí.</font>

<b> Funcions relacionades amb el protocol SAE J1850</b><br>
- j1850.c<br>
- j1850.h<br>

<b> Funcions relacionades amb el driver MM5450</b><br>
- MM5450.c<br>
- MM5450.h<br>

<b> Main</b><br>
- macros.h<br>
- main.c<br>

He mirat que hi hagi anotacions (en anglès) a tot el fitxer per entendre què és el que fa cada part. De totes maneres, per no fer massa llarga aquesta entrada, copiaré a continuació les parts de codi que considero més interessants:

### Codi destacat a j1850.h
Definició del <i>timming</i> i la corresponent funció usant el Timer0 del <i>PIC</i> d'acord amb l'Standard SAE J1850.

{% highlight c %}

// define J1850 VPW timing requirements in accordance with SAE J1850 standard
// all pulse width times in us 
// receiving pulse width
#define RX_SHORT_MIN	us2cntT0CON8(34)      // minimum short pulse time
#define RX_SHORT_MAX	us2cntT0CON8(96)      // maximum short pulse time
#define RX_LONG_MIN	us2cntT0CON8(96)      // minimum long pulse time
#define RX_LONG_MAX	us2cntT0CON8(163)     // maximum long pulse time
#define RX_SOF_MIN	us2cntT0CON8(123)     // l'he posat a 153 (abans 163) minimum start of frame time
#define RX_SOF_MAX	us2cntT0CON8(279)     // l'he posat a 249 (abans 239) maximum start of frame time
#define RX_EOD_MIN	us2cntT0CON8(163)     // minimum end of data time
#define RX_EOD_MAX	us2cntT0CON8(239)     // maximum end of data time
#define RX_EOF_MIN	us2cntT0CON8(239)     // minimum end of frame time, ends at minimum IFS
#define RX_BRK_MIN	us2cntT0CON8(239)     // minimum break time
#define RX_IFS_MIN	us2cntT0CON8(280)     // minimum inter frame separation time, ends at next SOF

{% endhighlight %}

<!--more-->

### Codi destacat a j1850.c
Definició de la funció que tractarà amb qualsevol missatge que arribi pel bus J1850.

{% highlight c %}
/* 
**--------------------------------------------------------------------------- 
** Abstract: Receive J1850 frame (max 12 bytes)
**           Rebre trama J1850 (màxim 12 bytes)
** Parameters: Pointer to frame buffer / punter al missatge al buffer
** Returns: Number of received bytes OR in case of error, error code with bit 7 set as error indication
**          Número de bytes rebuts o en cas d'error, el codi d'error amb el bit 7 usat com a inidcador d'error
**
** NOTE: This file is based on a project from Michael for arduino platform.
** (www.Mictronics.de)
** Code has been modified in order to be compatible with Microchip PIC MCUs.
** Based on Mictronics file j1850.c v1.07
**--------------------------------------------------------------------------- 
*/ 
uint8_t j1850_recv_msg(uint8_t *msg_buf )
{
	uint8_t nbits;			// bit position counter within a byte
	uint8_t nbytes;			// number of received bytes
	uint8_t bit_state;		// used to compare bit state, active or passive
	uint16_t tcnt1_buf;		//XM: used to compare counter
	
	/*wait for responds (if 100us pass without detection of a SOF--> answer with an error)*/	
	timer0_16start(CK16B128);

	while(!is_vpw_active())	// run as long bus is passive (IDLE)
	{
		if(timer0_get() >= WAIT_300us)	// check for 300us
		{
			timer0_stop();
			
			return J1850_RETURN_CODE_NO_DATA | 0x80;    // error, no responds within 100us
		}
	}
	// wait for SOF
	timer0_start(CK8);	// restart timer1
	while(is_vpw_active())	// run as long bus is active (SOF is an active symbol)
	{
		if(timer0_get() >=  RX_SOF_MAX) return J1850_RETURN_CODE_BUS_ERROR | 0x80;	
                // error on SOF timeout
	}

	
	timer0_stop();
	if(timer0_get() < RX_SOF_MIN) return J1850_RETURN_CODE_BUS_ERROR | 0x80; 
             // error, symbol was not SOF

	bit_state = is_vpw_active();   // store actual bus state
	timer0_start(CK8);
	for(nbytes = 0; nbytes < 12; ++nbytes)
	{
		nbits = 8;
		do
		{
			*msg_buf <<= 1; 	//this is for refer bit by bit for every for cycle

			while(is_vpw_active() == bit_state) 
                        // compare last with actual bus state, wait for change
			{
	
				if(timer0_get() >= RX_EOD_MIN	)	// check for EOD symbol
				{
					timer0_stop();
					return nbytes;	// return number of received bytes
				}
			}
			bit_state = is_vpw_active();	// store actual bus state
			tcnt1_buf = timer0_get();
			timer0_start(CK8);

			if( tcnt1_buf < RX_SHORT_MIN) return J1850_RETURN_CODE_BUS_ERROR | 0x80;   
                        // error, pulse was to short

			// check for short active pulse = "1" bit
			if( (tcnt1_buf < RX_SHORT_MAX) && !is_vpw_active() )
				*msg_buf |= 1;

			// check for long passive pulse = "1" bit
			if( (tcnt1_buf > RX_LONG_MIN) && (tcnt1_buf < RX_LONG_MAX) && is_vpw_active() )
				*msg_buf |= 1;

		} while(--nbits); 
                   // end 8 bit while loop. XM: Part of the Do-While. 
                   // While nbits is not 0 has to Do all that above and decrement on bit each time.
		
		++msg_buf;  // store next byte. 
                     // XM: Goes to the next memory direction, this means the next byte on the struct[]
	
	}	// end 12 byte for loop

	// return after a maximum of 12 bytes
	timer0_stop();	
	return nbytes;
}

{% endhighlight %}

### Codi destacat a MM5450.c
Definició de la funció que enviarà la informació al <i>LED Driver</i>.

{% highlight c %}
/* 
**--------------------------------------------------------------------------- 
** Abstract: Subroutine that sends all of the DATABITS to the chip. It begins by first sending the startbit, then it
**           sends all the bits in each byte of the ledArray.
**           Subrutina que envia tots els DATABITS al chip MM5450. Primer envia l'Start of Frame i després la resta de bits del ledArray
** Parameters: pointer ledArray
** Returns: none
**
** NOTE: This file is based on a project from l.e. hughes for arduino platform
** (http://www2.cs.uidaho.edu/) 
** Code has been modified in order to be compatible with Microchip PIC MCUs.
** Project: stairway_v_1_code.pde 
**--------------------------------------------------------------------------- 
*/ 

void sendDatabits(uint8_t *ledArray_buf) {

	uint8_t temp_byte;	// temporary byte store
	uint8_t nbits;		// bit position counter within a byte
	uint8_t MMbits;
	uint8_t nbytes;

	MMbits=35;
	nbytes=5;

	//Start of frame
  	MMClock_passive();
  	delay20us();
	MMData_active();
	delay20us();
  	MMClock_active();
	delay50us();
  	delay50us();
  	MMClock_passive();
  	delay20us();
	

	do
	{// end nbytes do loop
		temp_byte=*ledArray_buf;	//store byte termporary
		nbits=8;
		delay50us();
		//delay50us();
		delay50us();
		while(nbits-- && MMbits--)	//send 8 bits
		{
			if (temp_byte & 0x80){
				MMData_active();
				delay20us();
				MMClock_active();
	  			delay50us();
	  			MMClock_passive();
	  			delay20us();
			}else{
				MMData_passive();
				delay20us();
	  			MMClock_active();
	  			delay50us();
	  			MMClock_passive();
	  			delay20us();
			}
			temp_byte <<= 1;  // next bit (desplaça els bits cap a la dreta) 0101 -->0010
		}// end nbits while loop
		++ledArray_buf;	// next byte from buffer
	
	} while(--nbytes);
	MMData_passive();
		

}
{% endhighlight %}

### Codi destacat a macros.h
Definició d'algunes dreceres que ajudaran a simplificar el codi.

{% highlight c %}
// convert microseconds to counter values for each preescaler
//  x usec * (1 sec / 1000000 usec) * (CLOCK clks / 1 sec) * (1 cnt / 8 clks)
//((unsigned char) (((us) * ((unsigned long)(INT_CLK) / 8L) + 500000L) / 1000000L))
#define us2cntT0CON8(us) ((unsigned char) (((us) * ((unsigned long)(INT_CLK) / 8L) + 500000L) / 1000000L))
//  x usec * (1 sec / 1000000 usec) * (CLOCK clks / 1 sec) * (1 cnt / 64 clks)
#define us2cntT0CON64(us) ((unsigned char) (((us) * ((unsigned long)(INT_CLK) / 64L) + 500000L) / 1000000L))
//  x usec * (1 sec / 1000000 usec) * (CLOCK clks / 1 sec) * (1 cnt / 128 clks)
#define us2cntT0CON128(us) ((unsigned char) (((us) * ((unsigned long)(INT_CLK) / 128L) + 500000L) / 1000000L))
//  x usec * (1 sec / 1000000 usec) * (CLOCK clks / 1 sec) * (1 cnt / 256 clks)
#define us2cntT0CON256(us) ((unsigned char) (((us) * ((unsigned long)(INT_CLK) / 256L) + 500000L) / 1000000L))
//FOR TIMER3
//  x usec * (1 sec / 1000000 usec) * (CLOCK clks / 1 sec) * (1 cnt / 8 clks)
//((unsigned char) (((us) * ((unsigned long)(INT_CLK) / 8L) + 500000L) / 1000000L))
#define us2cntT3CON8(us) ((unsigned char) (((us) * ((unsigned long)(INT_CLK) / 8L) + 500000L) / 1000000L))
{% endhighlight %}

Definició de les dreceres per configurar els Timers 0, 1 i 3. <br>

{% highlight c %}
//REGISTER T0CON (TIMER 0)
//bit7 (TMR0ON)--> 1=Enables Timer0 / 0=Disables Timer0
//bit6 (T08BIT)--> 1=T0 as 8bit counter / 0=T0 as 16bit counter
//bit5 (T0CS)--> 1=Transtion on T0CK1 pin / 0=internal instruction cycle
//bit4  (T0SE)--> if bit5=0 not used
//bit3 (PSA) --> 1=T0 preescaler not assigned / 0=T0 preescaler assigned (bit2-1-0)
//bit2-1-0 (T0PS2-T0PS0)
/* Define Timer0*/
#define timer0_start(x)	T0CON=x;TMR0L=0;  // Timer0 enabled with a preescaler x
#define timer0_16start(x)	T0CON=x;WriteTimer0(0);  // Timer0 16bit enabled with a preescaler x
#define timer0_get()	TMR0L
#define timer0_stop()	T0CON=STOP;
#define INT_CLK	20000000L/4L

//TIMER1 - enumeration of the preescalers (16 bit counter 0-65535)(8 bit counter 0-255), internal clock = F_CPU/4
//bit7 (RD16)--> 1=Enables timer3 in one 16bit operation / 0= Enables timer3 in two 8bit operation
//bit 6(T1RUN): Timer1 system clock status bit --> fixed to 0
//bit5-4 (T1CKPS1:T1CKPS0) -->Preescaler 11(1:8),10(1:4),01(1:2),00(1:1)
//bit3 (T1OSCEN -Timer1 oscillator enable bit) fixed to 0
//bit2 (T1SYNC) fixed to 0
//bit1 (TMR1CS): 1: External Clock / 0: Internal clock Fosc/4 --> fixed to 0
//bit0 (TMR1ON): 1:Enables T1 / 0: Stops Timer1
/* Define Timer1*/
#define timer1_start(x)	T1CON=x;WriteTimer1(0);  // Timer3 16bit enabled with a preescaler x
#define timer1_get()	ReadTimer1()
#define timer1_stop() T1CON=T1STOP;

//TIMER3 - enumeration of the preescalers (16 bit counter 0-65535), internal clock = F_CPU/4
//REGISTER T0CON (TIMER 0)
//bit7 (RD16)--> 1=Enables timer3 in one 16bit operation / 0= Enables timer3 in two 8bit operation
//bit6 and 3 (T3CCP2:T3CCP1)--> fixed to 00
//bit5-4 (T3CKPS1:T3CKPS0) -->Preescaler 11(1:8),10(1:4),01(1:2),00(1:1)
//bit2 (T3SYNC) fixed to 0
//bit1 (TMR3CS): 1: External Clocl / 0: Internal clock Fosc/4
//bit0 (TMR3ON): 1:Enables T3 / 0: Stops Timer3
enum {
T3STOP	= 0b00000000,
T3CK8	= 0b10110001,
T3CK1	= 0b10000001
};

/* Define Timer3*/
#define timer3_start(x)	T3CON=x;WriteTimer3(0);  // Timer3 16bit enabled with a preescaler x
#define timer3_get()	ReadTimer3()
#define timer3_stop() T3CON=T3STOP;

{% endhighlight %}

### Codi destacat a main.c

Definició de les llibreries incloses a MPLAB.<br>

{% highlight c %}

/*INCLUDES*/
#include <p18f2553.h>
#include <timers.h>		//TO:j1850 functions	T1:used on main 	T2:PWM for brightness control on Micrel IC    T3:MICREL
#include <string.h>
#include <usart.h>
#include <stdio.h>
#include <pwm.h> //Used to vary the brightness of the MICREL MM5450
{% endhighlight %}

Configuració del Timer2 per controlar la lluminositat dels 7 segments. <br>

{% highlight c %}
/******************************************************************
** Configuring timer 2 which provides timing for PWM
** TIMER_INT_OFF: disable timer interrupt
** T2_PS_1_4: Timer2 prescaling set to 16
** T2_POST_1_1: Timer2 postscaling set to 16
********************************************************************/
OpenTimer2(TIMER_INT_OFF & T2_PS_1_16 & T2_POST_1_4);
/******************************************************************
**  configuration of PWM Brightness regulation on MM5450
** PWM period =[(period ) + 1] x 4 x TOSC x TMR2 prescaler. The value of period is from 0x00 to 0xff
** PWM Period= [(30)+1]*4*(1/20e6)*16=0,099ms -->10Hz
*******************************************************************/
OpenPWM1(30); // configuring PWM module 1 --> aprox 1221Hz amb prescaler de 16

//set brightness 
brightness=60;
SetDCPWM1(brightness); // Range goes from (0-1023). 1023 sets PWM duty cycle 100% (full speed).
{% endhighlight %}

Configuració de la interrupció del PIC per tal de poder llegir qualsevol missatge que arribi pel bus de dades. <br>

{% highlight c %}
//CONFIG: EXTERNAL INTERRUPTION - RB0 (INT0)
	INTCON2bits.RBPU=0;	//pull-ups deactivated from ports RB (RB0 has alreday one on the circuit)
	INTCONbits.INT0IE = 1; 	//enable INT0 external interrupt
	INTCON2bits.INTEDG0=0;	//INT0 on falling edge.    It was inverted due to the Hardware is already inverted (j1850 vs TTL: 7V is 0V and 0V is 5V. 
				//If schematic changes and INTEDG0 goes to 1, j1850.h has to be changed as well (delete ! in (#define is_vpw_active()	!PORTBbits.RB0)
	RCONbits.IPEN = 1; 	//enable priority levels on interrupts
	INTCONbits.GIEH = 1; 	//enable all high-priority interrupts
INTCONbits.INT0IF = 0; //clear INT0 flag
{% endhighlight %}

Codi que permetrà diferenciar entre una pulsació curta al botó per canviar de mode i una pulsació llarga per canviar la lluminositat. <br>

{% highlight c %}
		/**************************************************************************************
		**************   BRIGHTNESS AND MODE CHANGE   *****************************************
		***************************************************************************************/
			if(BUTTON==0){			//rear switch depressed.
				if(counter_switch>25000){
					//do nothing, once switch is released brightness will change
				}else{
					counter_switch=counter_switch+1;
				}				
			}else if(BUTTON==1){		//switch released
				//do nothing
			}

			//change of mode
			if(counter_switch>2000 && counter_switch<10000 && BUTTON==1){
				counter_switch=0;
				if(mode==0){		//RPM
					mode=1;		//--> Fuel Consump
					LED_MODE0=0;
					LED_MODE1=1;
					LED_MODE2=0;
				}else if(mode==1){	//Fuel consump
					mode=2;		//--> Temp
					LED_MODE0=0;
					LED_MODE1=0;
					LED_MODE2=1;
				}else if(mode==2){	//Temp
					mode=3;		//--> Speed
					LED_MODE0=0;
					LED_MODE1=0;
					LED_MODE2=0;
				}else if(mode==3){	//speed
					mode=0;		//--> RPM
					LED_MODE0=1;
					LED_MODE1=0;
					LED_MODE2=0;
				}
			}else if(counter_switch>10000 && BUTTON==1){
			//max value=120, but for safety reasons (too much heat) is software limited to 60
				counter_switch=0;
				//brightness=brightness+10;
				if(brightness==60){		
					brightness=10;
				}else if(brightness==10){
					brightness=60;					
				} //values will be either 10 or 60
				SetDCPWM1(brightness);
			}

{% endhighlight %}

Tractament del missatge SAE que hi ha al buffer temporalment fins que un altre missatge nou arribi.<br>

{% highlight c %}
if (recv_nbytes & 0x50){	//Until first signal is not received it will show a "-"
	LATB=display7seg[17];		// "-"
}else{
	if(recv_nbytes & 0x80){	//in case of error
		//rpm[1]=(recv_nbytes && 0x0F);
	}else{		//use the array[2] to save the current value and to store new value in array[1]
		if (j1850_msg_buf[0]==0x28 && j1850_msg_buf[1]==0x1B && j1850_msg_buf[2]==0x10 && j1850_msg_buf[3]==0x02){   	//rpm
			rpm[2]=rpm[1]; 	//save the previous value
			rpm[1]= (((unsigned char)j1850_msg_buf[4]*0x100+(unsigned char)j1850_msg_buf[5])/4);			//0x100=256dec
			//way to know if engine on or not (and a filter to avoid strange values on display)
			if ((engon==0 && rpm[1]>500) || (engon==1 && rpm[1]<500)){
				comptengon=comptengon+1;
				if (comptengon>=4){
					engon=1;	//Engine is ON
					comptengon=0;
				}else{
					//no fer res
				}
			}else{
				comptengon=0;
			}

		}else if(j1850_msg_buf[0]==0xA8 && j1850_msg_buf[1]==0x3B && j1850_msg_buf[2]==0x10 && j1850_msg_buf[3]==0x03){	//Gear
			//current gear, 0xXX = 0x02,0x04,0x08,0x10,0x20, for gears 1-5
			//also filter to avoid strange gear display behaviour (it will check 4 times gear is the same before changing the display)
			gear[0]=j1850_msg_buf[4];
			if (comptcurrentgear==0){		//start counter
				nextgear=gear[0];
				comptcurrentgear=comptcurrentgear+1;
			}else if(comptcurrentgear>=3){	//display will be updated here
				if(mode==3){		
					LATB=display7seg[10];						
				}else{
					if(gear[0]==0x00 ){
						LATB=display7seg[0];
					}else if(gear[0]==0x02){
						LATB=display7seg[1];
					}else if(gear[0]==0x04){
						LATB=display7seg[2];
					}else if(gear[0]==0x08){
						LATB=display7seg[3];
					}else if(gear[0]==0x10){
						LATB=display7seg[4];
					}else if(gear[0]==0x20){
						LATB=display7seg[5];
					}else{
						LATB=display7seg[17];
					}
					comptcurrentgear=0;
				}
			}else{
				if(gear[0]==nextgear){
					comptcurrentgear=comptcurrentgear+1;
				}else{
					comptcurrentgear=0;
				}
			}

		}else if(j1850_msg_buf[0]==0xA8 && j1850_msg_buf[1]==0x49 && j1850_msg_buf[2]==0x10 && j1850_msg_buf[3]==0x10){	//Engine Temp
			temp[1]= (unsigned char)j1850_msg_buf[4]-40;

		}else if(j1850_msg_buf[0]==0x48 && j1850_msg_buf[1]==0x29 && j1850_msg_buf[2]==0x10 && j1850_msg_buf[3]==0x02){	//Speed
			speed[1]= (((unsigned char)j1850_msg_buf[4]*0x100+(unsigned char)j1850_msg_buf[5])/128);		//0x100=256dec
		}
	}
}
{% endhighlight %}

Codi inclòs a la rutina d'interrupció. Bàsicament, rebre el missatge i transmetre'l pel RS232.

{% highlight c %}
/****************************************
***********INTERRUPCION ROUTINE********
*****************************************/

#pragma interrupt InterruptHandlerHigh

void InterruptHandlerHigh(){

char i;
char buffer[20];

recv_nbytes=j1850_recv_msg(j1850_msg_buf);
if(recv_nbytes & 0x80){
}else{
	i=0;
	while(i<recv_nbytes){
		USART_hex2ascii(j1850_msg_buf[i]);
		if(i==recv_nbytes-1){
			send_byte(0x0D);	//intro	
		}else{
			send_byte(0x20);	//space
		}
		i=i+1;
	}

}
INTCONbits.INT0IF = 0; //clear INT0 flag
}
{% endhighlight %}

Fins aquí els detalls del codi. Per més detall, aneu directament al repositori de Github: <a href="https://github.com/momex/DIGTACHO" target="_blank">DIGTACHO</a>.

<p>
<font size="2"> 
Índex de projecte:<br>
<a href="/HD-tacho-part1">Part1 </a>/
<a href="/HD-tacho-part2"> Part2 </a>/
<a href="/HD-tacho-part3"> Part3 </a>/
<a href="/HD-tacho-part4"> Part4 </a>/
<a href="/HD-tacho-part5"> Part5 </a>/
<a href="/HD-tacho-part6"> Part6 </a>/
<a href="/HD-tacho-part7"> Part7 </a>/
<a href="/HD-tacho-part8"> Part8 </a>/
<a href="/HD-tacho-part9"> Part9 </a>/
<a href="/HD-tacho-part10"> Part10 </a>/
<b>Part11</b> /
<a href="/HD-tacho-part12"> Part12 </a>/
<a href="/HD-tacho-part13"> Part13 </a>/
<a href="/HD-tacho-part14"> Part14 </a>/
 Part15
 </font>
</p>
