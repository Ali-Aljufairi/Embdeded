## What is a microcontorller 

- single board device thatcan be programmerd to interface with a variety of sensors and actuators. 


## code example 

```c++
void setup() {
    // put your setup code here, to run once:
    serial.begin(9600);
}

void loop() {
    

    // put your main code here, to run repeatedly:
    serial.println("Hello World");
    
    // without new line
    serial.print("Hello World");

    // print number with 3 decimal places
    serial.print(1.233, 3)

    // print number in hex format 
    serial.println(11,Hex)
    
    // print number in binary format
    serial.println(11,BIN)

    delay(1000);
}
```

```c++
void setup()

```
## functions
- can be called from anywhere in the program
- can be called multiple times
- can be overloaded
- can be recursive 
- return a value should be declared before

## types of file for microcontroller
1. .ino

1.  .hex 

1. .elf

1. .cpp


## How to run the program with  with simulator

1. open the program in arduino IDE

1. click on the verify button

1. see the compile file Path 

1. load into the simulator 


## String structure 

- char array which is terminated by a null character '\0'


## define vs const 


```c++
#define PI 3.14
const  PI  = 3.14
```

The difference between the two is that the preprocessor directive is a simple text replacement, while the const declaration is a true variable declaration that the compiler can check for type correctness, etc.

