### Q1 Write a C code that calculates and prints the memory addresses associated with the macros PORTB and DDRB defined in the Arduino IDE for the Arduino Uno board: 

(Answer should be: 37 for PORTB and 36 for DDRB). 

 ```C++
 
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("The address of PORTB is: ");
  Serial.println((int)&PORTB);
  Serial.println("The address of DDRB is: ");
  Serial.println((int)&DDRB);
  
}  

void loop() {
  // put your main code here, to run repeatedly:
}
 
 ```


### Q2  Without using the PORTB and the DDRB macros defined in the Arduino IDE, write a C code that blinks the led connected to pin 5 of port B in the Arduino Uno board.  

 
 ```C++

unint8_t *ptr ;

void setup(){

    ptr =36;
    *ptr |= (1<<5);
    ptr++;
}
 
 void loop(){
    *ptr ^= (1<<5);

    delay(1000);
 
 }
 
 
 ```
 

 a. Why uint8_t operations are faster than the float type? 

[Float point are more complex operation and require more processing ](https://electronics.stackexchange.com/questions/493554/does-the-avoid-using-floating-point-rule-of-thumb-apply-to-a-microcontroller-w 
)
 

[Floating-point operations require additional hardware to be performed, such as a floating-point unit (FPU) which is not present in a microncotroller which make their operation slower. ](https://electronics.stackexchange.com/questions/493554/does-the-avoid-using-floating-point-rule-of-thumb-apply-to-a-microcontroller-w )


b. Remove the volatile keyword before variables a, b, and c. Re-run the code for any data type and any operation. What is the printed execution time value? Explain why you get such value. 

The printed execution time value for all the types is 0. Declaring a variable as volatile in Arduino code prevents the compiler from optimizing it, which can slow down the code

