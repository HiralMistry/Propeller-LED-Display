#include"reg51.H"
//sbit Fan_On = P0^0;
//sbit Cfl_On = P0^1;
#define led P1 //port1 will be connected to leds
unsigned int del=1;//variable to control delay
unsigned int del1=8;//variable to control delay
unsigned char i=0;
//char b[]="BAHDRESH SWETANK";
//char b[]=" PARUL UNIVERSITY";
char b[]=" MS UNIVERSITY   ";
void tx1(unsigned char y);
void sendserial(unsigned char*);
char *pb;
///char send1[]="AT\r\n";
void rx(void) interrupt 4
{

     if(RI)
	 {
	   *(pb++) = SBUF;
	   RI=0;
	 }
	 *pb='\0';

}
/*void tx1(unsigned char y)
{
  SBUF=y;
  while(TI==0);
  TI=0;
}*/
void serial_init(void)
{
	  SCON=0x50;
	  TMOD=0x20;
	  TH1=-3;
	  TR1=1;
}
void delay(void)
{
	unsigned int i,j;
	for(i=0;i<del;i++)
	for(j=0;j<70;j++);

}
void delay1(void)
{
	unsigned int i,j;
	for(i=0;i<del1;i++)
	for(j=0;j<100;j++);

}
void display(unsigned char car); // declaration of a function 
void main()
{
	unsigned char index,i1;
	pb=b;
	*pb='\0';
	serial_init();
	IE=0x90;
	led=0x00;
	delay( );
	while(1)
	{
  		for(i1=0;i1<16 ;i1++)
		{
			index = b[i1];	
			display(index);
		}
		delay1();
	}

}

void display(unsigned char car)
{
	switch(car)
	{
	 
		case 32 ://////////////space
	 	{
			led=0xff;  delay( ); 	led=0xff;  delay( );  led=0xff;  delay( ); led=0xff;  delay( ); led=0xff;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	} break;

		case 65 ://///////////////A
	 	{
			led=0x81;  delay( ); led=0x6F;  delay( );  led=0x6F;  delay( ); led=0x6F;  delay( ); led=0x81;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 66 : // letter B 
      	{ 
             led=0x01;  delay( );   led=0x6D;  delay( );     led=0x6D;  delay( );  led=0x6D;  delay( );   led=0x93;  delay( );  led=0xFF;  delay( );// to make one column gap between letters   
        }  
        break; 

		case 67://///////c
	 	{
			led=0x81;  delay( ); led=0x7E;  delay( );  led=0x7E;  delay( ); led=0x7E;  delay( ); led=0x7E;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 68 ://////////////D
	 	{
			led=0x00;  delay( ); led=0x7E;  delay( );  led=0x7E;  delay( ); led=0x7E;  delay( ); led=0x81;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 69 ://////////////E
	 	{
			led=0x01;  delay( ); 	led=0x6D;  delay( );  led=0x6D;  delay( ); led=0x6D;  delay( ); led=0x6D;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	} break;

		case 70 ://///////////////F
	 	{
			led=0x01;  delay( ); led=0x6F;  delay( );  led=0x6F;  delay( ); led=0x6F;  delay( ); led=0x6F;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 71 : // letter G 
      	{ 
           led=0x81;  delay( );   led=0x7D;  delay( );     led=0x70;  delay( );  led=0xF3;  delay( );   led=0xF5;  delay( );  led=0xFF;  delay( );// to make one column gap between letters   
        }  
         break; 

		case 72://///////H
	 	{
			led=0x01;  delay( ); led=0xEF;  delay( );  led=0xEF;  delay( ); led=0xEF;  delay( ); led=0x01;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 73 ://////////////I
	 	{
			led=0x7E;  delay( ); led=0x7E;  delay( );  led=0x00;  delay( ); led=0x7E;  delay( ); led=0x7E;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 74 ://////////////J
	 	{
			led=0x7D;  delay( ); 	led=0x7E;  delay( );  led=0x01;  delay( ); led=0x7F;  delay( ); led=0x7F;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	} break;
		
	
		case 75 ://///////////////K
	 	{
			led=0xEF;  delay( ); led=0xD7;  delay( );  led=0xBB;  delay( ); led=0x7D;  delay( ); led=0xFF;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 76 : // letter L 
      	{ 
         	led=0x00;  delay( );   led=0xFE;  delay( );     led=0xFE;  delay( );  led=0xFE;  delay( );   led=0xFE;  delay( );  led=0xFF;  delay( );// to make one column gap between letters   
   		}  
        break; 

		case 77://///////M
	 	{
			led=0x01;  delay( ); led=0xBF;  delay( );  led=0xBF;  delay( ); led=0xBF;  delay( ); led=0x01;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 78 ://////////////N
	 	{
			led=0xC1;  delay( ); led=0xEF;  delay( );  led=0xF7;  delay( ); led=0xFB;  delay( ); led=0x81;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 79 ://////////////O
	 	{
			led=0x81;  delay( ); 	led=0x7E;  delay( );  led=0x7E;  delay( ); led=0x7E;  delay( ); led=0x81;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	} break;

		case 80 ://////////////////p
	 	{
			led=0x00;  delay( ); led=0x6F;  delay( );  led=0x6F;  delay( ); led=0x6F;  delay( ); led=0x8F;  delay( ); led=0xff;  delay( );
	 	}
		break;


			case 81 ://///////////////Q
	 	{
			led=0x83;  delay( ); led=0x7D;  delay( );  led=0x7D;  delay( ); led=0x7D;  delay( ); led=0x82;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;


		case 82 ://////////////R
	 	{
			led=0x01;  delay( ); led=0x6F;  delay( );  led=0x67;  delay( ); led=0x6B;  delay( ); led=0x9D;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 83 ://////////////S
	 	{
			led=0x9D;  delay( ); 	led=0x6D;  delay( );  led=0x6D;  delay( ); led=0x6D;  delay( ); led=0x73;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	} break;

		case 84://///////T
	 	{
			led=0x7F;  delay( ); led=0x7F;  delay( );  led=0x00;  delay( ); led=0x7F;  delay( ); led=0x7F;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 85 ://////////////U
	 	{
			led=0x01;  delay( ); led=0xFE;  delay( );  led=0xFE;  delay( ); led=0xFE;  delay( ); led=0x01;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 86 ://////////////V
	 	{
			led=0x03;  delay( ); 	led=0xFD;  delay( );  led=0xFE;  delay( ); led=0xFD;  delay( ); led=0x03;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	} break;

		case 87 ://////////////////W
	 	{
			led=0x00;  delay( ); led=0xFD;  delay( );  led=0xFB;  delay( ); led=0xFD;  delay( ); led=0x00;  delay( ); led=0xFF;  delay( );
	 	}
		break;


		case 88 ://///////////////X
	 	{
			led=0xBB;  delay( ); led=0xD7;  delay( );  led=0xEF;  delay( ); led=0xD7;  delay( ); led=0xBB;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;


		case 89 ://////////////Y
	 	{
			led=0xB9;  delay( ); led=0x6DD;  delay( );  led=0xE1;  delay( ); led=0xDF;  delay( ); led=0xBF;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	}
		break;

		case 90 ://////////////Z
	 	{
			led=0xBB;  delay( ); 	led=0xB3;  delay( );  led=0xAB;  delay( ); led=0x9B;  delay( ); led=0xBB;  delay( ); led=0xFF;  delay( );// to make one column gap between letters  
	 	} break;


	 	default:
	 	led=0xfe;
	}
}
