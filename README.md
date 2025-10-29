GENERATE A 5 SECOND DELAY USING TIMER0 IN MODE1 AND TOGGLE PORT 2.7 CONTINUOUSLY

**Aim**

   To write and execute a program using Timer0 in Mode 1 (16-bit timer mode) of the 8051 microcontroller to generate a 5-second delay and toggle Port 2.7 continuously.

Apparatus Required

  8051 Microcontroller or AT89C51 Trainer Kit

  Keil µVision IDE

  Proteus (for simulation)

   Connecting Wires and Power Supply
   
 Algorithm

  1. Start the program.

  2. Configure Timer0 in Mode 1 (16-bit timer) by loading TMOD = 0x01.

  3. Load TH0 and TL0 with initial values for the desired delay.

  4. Start the timer by setting TR0 = 1.

  5. Wait until the TF0 flag is set (timer overflow).

  6. Stop the timer and clear TF0.

  7. Repeat the above delay multiple times to achieve approximately 5 seconds.

  8. Toggle P2.7 every 5 seconds.

  9. Repeat the process continuously.
     
PROGRAM
 ```asm
ORG 0000H

MAIN:   
    MOV P2, #00H          

HERE:
    ACALL DELAY5S        
    CPL P2.7              
    SJMP HERE            
DELAY5S:
    MOV R7, #76            
REPEAT:
    MOV TMOD, #01H
	MOV TH0, #00H         
    MOV TL0, #00H         
    SETB TR0              

WAIT_OV:
    JNB TF0, WAIT_OV      
    CLR TR0               
    CLR TF0                
    DJNZ R7, REPEAT        

    RET                  
END
```
 OUTPUT
<img width="1683" height="957" alt="Screenshot 2025-10-29 083942" src="https://github.com/user-attachments/assets/9db928eb-3638-401a-a650-ab75fe77c03a" />


RESULT

  The program successfully generates a 5-second delay using Timer0 in Mode1, and the LED connected to Port 2.7 blinks continuously every 5 seconds.


 
