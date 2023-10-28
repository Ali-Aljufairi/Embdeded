# Embedded Programming 1



## Advantages of programming in Assembly

- can result in better performance

- Better code Efficiency 


- Good to understand hardware architecture ! IN ORDER TO WRITE BETTER CODE

<br>

## High level language 

- better productivity

- Extensive library support

- compiler is available for different platforms

<br>

## Why C


- C is a middle level language

- C is a structured language


<br>



## C program structure


```c
#define  F_CPU 16000000UL
#include <avr/io.h>

int main(void)
{
    DDRB |= (1<<PB5);
    while (1) 
    {
        PORTB ^= (1<<PB5);
        _delay_ms(1000);
    }
}
```


<br>

## Arduino way

```C++

void setup() {
  // put your setup code here, to run once:
  pinMode(13, OUTPUT);

}


void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(13, HIGH);
  delay(1000);
  digitalWrite(13, LOW);
  delay(1000);
}
```


### Compiler vs Linker vs Assembler

- Compiler: converts high level language to assembly language

- Assembler: converts assembly language to machine code


- Linker: links all the object files together to create an executable file


### Debugging

- Debugging is the process of finding and fixing errors in a computer program