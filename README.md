# LED Blink Using Timer0 in PIC Microcontroller

###### Implemented an LED blinking system using Timer0 in the PIC16F877A microcontroller with Proteus simulation. The project demonstrates timer-based delay generation for periodic LED control without relying on software delays, showcasing efficient use of hardware timers in embedded systems.
---
## Here is the references...

Circuit Connections :-

<img src=https://github.com/lingeshkumarkamaraj/LED-Blink-Using-Timer0/blob/main/1.png> 
<img src=https://github.com/lingeshkumarkamaraj/LED-Blink-Using-Timer0/blob/main/3.png> 
<img src=https://github.com/lingeshkumarkamaraj/LED-Blink-Using-Timer0/blob/main/2.png> 

Working :- 

[<img width="300" height="300" src="https://img.icons8.com/color/96/start.png" alt="video"/>](https://youtu.be/OrODncMhrcE)


---
Code :-
```

#include<Servo.h>
Servo clnup;
Servo clndn;
int pr, sp;

void setup(){
  clnup.attach(7);
  clndn.attach(6);
  pinMode(A1,INPUT);
  pinMode(A0,INPUT);
  
  clnup.write(0);
  clndn.write(0);
  
  if(pr>100){
    clnup.write(90);
    delay(500);
    clndn.write(90);
    delay(1000);
    clnup.write(0);
    delay(500);
    clndn.write(0);
    delay(1000);
  }
}
void loop(){
  pr = analogRead(A0);
  sp = analogRead(A1);
  
  if(sp<820 && sp>100){
    clnup.write(90);
    delay(500);
    clndn.write(90);
    delay(1000);
    clnup.write(0);
    delay(500);
    clndn.write(0);
    delay(1000);
  }
  
  if(pr<800 && pr>100){
    clnup.write(90);
    delay(500);
    clndn.write(90);
    delay(1000);
    clnup.write(0);
    delay(500);
    clndn.write(0);
    delay(1000);
  }
  delay(2000);
}


```
---
[TINKERCAD LINK](https://www.tinkercad.com/things/lRvBoGBZoyM-panel-clean?sharecode=exMkYOFheM__0TgxbhVHY7pibX1ZsfoSd3sjNemLcS4)
---
