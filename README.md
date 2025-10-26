## YUGANTHIRAN P S 
## 212223060313
# SKILL ASSESSMENT - 2
# 

## AIM
Write an assembly language program in 8051 to generate a 50 ms delayusing Timer 0 in Mode 2 (8-bit auto-reload mode) and blink an LED connected to Port3.0.

---

## APPARATUS REQUIRED
- Personal computer with Keil software

---

## ALGORITHM
1.Initialize Port: Set P3.0 as output and turn OFF LED.

2.Configure Timer0: Set Timer0 in Mode 2 (8-bit auto-reload) and load TH0 with reload value for 50 ms delay.

3.Start Timer: Enable Timer0 (TR0 = 1).

4.Blink LED: Turn ON P3.0, wait for Timer0 overflow, turn OFF P3.0, wait for next overflow.

5.Repeat: Continuously loop Step 4 for blinking.
6. **End**

---

## SCHEMATIC DIAGRAM
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/208048f4-e428-4f73-843c-8285223d9430" />




---

## PROGRAM
```asm
ORG 0000H
MAIN:
    MOV TMOD, #02H   
    MOV TH0, #06H    
    MOV P3, #00H     

HERE:
    CPL P3.0         
    ACALL DELAY_50MS 
    SJMP HERE        
DELAY_50MS:
    MOV R2, #200     
    SETB TR0         
WAIT_LOOP:
    JNB TF0, $       ; Wait for overflow
    CLR TF0          ; Clear overflow flag
    DJNZ R2, WAIT_LOOP
    CLR TR0          ; Stop timer
    RET
END

```
OUTPUT
<img width="1286" height="769" alt="image" src="https://github.com/user-attachments/assets/41ce0290-d3e2-4398-98e3-812142950b8c" />


<img width="284" height="154" alt="image" src="https://github.com/user-attachments/assets/1453b047-d5fa-4c4d-b045-dc9f42fe93d8" />





---


---

RESULT

Thus, the generate a 50 ms delayusing Timer 0 in Mode 2 in port 3 and executed successfully using 8051 Keil software.

---


