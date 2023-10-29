### Compelete the follwoing C function that returns ASCII code of 'x'

```C++
int return_ascii(char x){
return (int)x;
// 7
}
```

<br>

### What would be following code print


```C++
char s[]= "Hello";

Serial.println(sizeof(s));


```

> 5 for each charcter + 1 for the null to when the string end

<br>

### What would the following code print

```C++

struct my_struct{
uint8_t a:4 ;
uint8_t b:3 ;
float   c   ;
}x;


Serial.print(sizeof(x));


```

> 5 Since this is a struct and in struct we add all bits and byte float is 4 byte and 4 and 3 is equal to almost of 1 byte

<br>

### what would the following code print ?

```C++
int a = -3;

Serial.println((uni8_t) a);

// convert -3  to Binary  0000011

// Flip all bits  1111100

// Add  1

// 1111101 = 253

```

<br>

### What would the following code print ?

```C++
uint8_t a = 255;

Serial.println((int8) a);

// 11111111

// -1
```

<br>

### What would the follwoing code print ?

```C++

// assume x is stored in address 2298

int x  =10 ;

int *a = &x;

Serial.println(*a);

// 10

```

<br>

### What is the use of the static word C keyword ?

> static variables are declared with the static keyword, and can be used only inside the function where they are declared.

<br>

### What is the use the volaite c Keyword ?

> Declaring a variable as volatile in Arduino code prevents the compiler from optimizing it, which can slow down the code

<br>

### What is the decimal equivalent of the following IEEE751 number

```
 1 10000010 111100000000000000
```

$Formula = 1^{sign}\cdot mantisa \cdot 2^{expontent}$

130 -127 = 3

$2^{3}$

Shift left by 3

1 1111.100000000000000000000 x $2^{3}$

-15.5

<br>

### Write a C type called Base which is an Enum of the following dec , hex, oct, binary

```C++
typedef enum base {

    decimal =10;
    Hexamdecimal =16;
    octal = 8 ;
    binary= 2;

}base;


```

<br>

### Write a function that prints the character of the arugment my_string in sperline using Serial.Println() function

```C++
void print_string(char my_string[]){

 for (uint16_t i=0 ; i  ;i++ )
    Serial.println(my_string[i])
}


```

<br>

### Assume you have an overloaded function my_print(), which prints arguments of types: uint32_t, int32 t, char, string. Extend the function to support printing a float argument (up to 3 digits of the fraction is enough!).void my_print (float x){ ... }

```C++


void my_print(float x) {
  Serial.print(x, 3); // Print with 3 decimal places
}

```

### Explain the advantages of the C programming language over other high-level programming languages for embedded system’s programming

- The low level languages as C provides for us easier ways to write loops and statements

- We will be able to use and call pre-declared functions.

- It is much easier to learn and use C language than using high-level language such as assembly.

<br>

### List three unique characteristics of microcontrollers compared to microprocessors

- Microprocessors have higher power consumption than microcontrollers that has ultra low power

- RAM, storage and even I/O ports are external in the Microprocessors but the Microcontrollers has its built-in ports with the ability to extend it with external connections.

- Microcontrollers are less expensive than Microprocessors and some of them has a really cheap price

### Explain why it is preferable to use the standard integer types defined in the “stdint.h” library such as the “uint8_t “in embedded systems

- Sometimes we need to avoid any overflows to we need to allocate the specific size for the integer data type and also to remove the ambiguity of integer sizes.

<br>

![Float](./images/float1.jpg)

<br>

### Describe Void, bool memory map in a MCU and 96000 stament in Serial print

```
Void: In programming, "void" is used to indicate that a function doesn't return a value.

Bool Memory Map in MCU: In microcontrollers, the memory map organizes memory for different purposes, and "bool" might represent Boolean variables stored in memory to represent states or conditions.


96000 Statements in Serial Print: This likely means sending a large amount of data (96,000 pieces of information) through a serial communication interface using a "Serial.print" function, which is common in microcontroller programming. It's important to manage this volume properly to avoid issues.
```

<br>
![program](images/program1.jpg)
<br>

### List two popular architecture and two main vendors of Microcontrollers. ​​(2 Marks)

> Vendors (Microchip, NXP, Texas Instruments, STMicroelectronics, etc.) Architectures (ARM M, AVR, PIC, RISC V, etc.)

 <br>

### Explain what is in-circuit debugging?​​(1 Mark)

> Testing the embedded code in debug mode while running on the device itself (this may require special debug hardware between the PC and the tested device)

<br>

### Why is it preferable to use integer types defined in the “stdint.h” when developing embedded applications?​ ​​(1 Mark)
>
> Remove ambiguity with integer C types (make the code more portable)

<br>

### List three main operations that can be performed using the development toolchain of an MCU.​​​(3 Mark)
>
> Compile, link, program device

<br>

### What is the “double” data type, and what is it typically used for?​(1 Marks)

> Double precision floating point (64-bit). Used for floating point numbers requiring extra precision.
> <br>

### Convert the following decimal number to IEEE754 single precision floating number showing all steps. ​​​(3 Marks)

```
-15.5
Sign:1
Exponent: 10000010
Mantissa: 1111 (followed by 19 0s)

```

<br>

### Explain what is the baud rate in serial communication.​(1 Marks)

Number of bauds per second (signal characters per second)

<br>

### What is the purpose of the following memory types inside an MCU?​(3 Mark)

- Flash: store code

- EEPROM: store non-volatile user data (accessible by programmer)
- SRAM: run-time memory

<br>

### In an embedded system program, list the three sections of the SRAM memory and their uses:​​​(3 Marks)

- Stack: local variable, function call info.,interrupts info.

- Heap: dynamically allocated data

- Static Section: Static variables, constants, global variables

<br>

### List three common SRAM optimization techniques when writing embedded code for small microcontrollers. ​(3 Marks)

>Use smallest integer types possible Use local variables whenever possible Store long strings in flash and access directly from flash using F(). Store constants in flash and access directly from flash

<br>

### Explain why extra care must be taken when performing dynamic memory allocation in small microcontrollers? ​(1 Mark)

> To avoid stack-heap collision in small SRAM memory

<br>

### List three common flash optimization techniques when writing embedded code for small microcontrollers.​(3 Marks)

- Use functions whenever possible
- Remove dead code
- Remove bootloader
<br>

### Identify a typical file format for programming microcontlers

- .hex
- .ino
- .elf
- .cpp
  <br>

### Why is it prefarable to use integer arithmic wheneven possible rather than floating point arithmtic in MCU

> Because integer is fast operation and it is supported by ALU of microcontroller .

<br>

### Explain what an overloaded function in C++ is and where such a function would be used in embedded software

> A function that has several implementations with the same name but different arguments. Used for software libraries and packages.
> <br>

### What Would the following C code print and why ?

```C++

int a = 5;
int b = 2;
float c = a/b ;

Serial.print(c);
```

<br>

## What would the following C code print

```C++

int8_t a =-2;
uint8_t c = a;

Serial.println(c);

//254

```

<br>

### What would the following C code print

```C++
Struct s{

uint16_t a ;
bool b ;
float c;
};

Serial.println(sizeof(s));

//7

```

- 2 byte uint16_t
- 1 byte bool
- 4 byte float
  <br>

### What would the following C code print

```C++
union u{

uint16_t a;

float b;
};
Serial.println(sizeof(u))

// 4

```

<br>

### In an embedded system program, list the three sections of the SRAM memory and their uses

- Stack : local variables

- Heap : dynamically allocated variables

- Static data : constant and global variables and static variables
  <br>

### List three common SRAM optimization techniques when writing embedded code for small microcontrollers

- Use the smallest variable type possible
- Use unios when possible

- Remove all function and variables that not used

- Read strings and constants directly form flash

<br>

### The PORTB Data Direction Register (DDRB) is in address 36 in the ATmega328 MCU. Using a pointer to this register, write a C code that sets PIN5 of PORTB to an output

```C++
uint8_t *p = 36; // pointer to location 36 in memory
*p |= (1<<5); // the value in location 36
*/
DDRB |= (1<<5);
PORTB |= (1<<5);
*/

```

<br>

### Write a C code for the following function. This function stores the binary digits of “num” in array “digits” (starting with the least significant bit). It also returns the total number of digits

```C++
uint8_t my_num_bin_dig(uint8_t num , unit8_t digits[])

{

uint8_t num_dig = 0 ;

while (num != 0){
  
uint8_t remainder= num %2 ;
digits[7-num_dig] = remainder;
num = num/2 ;

num_dig++ ;

return num_dig


}


}

```

<br>

### What would the following C code print

```C++

struct s {

uint8_t a:3 ;
uint8_t b:4 ;
uint8_t c:4 ;
uint8_t :0 ;
uint8_t d:2 ;

// 3

}

```

### Write a C function that returns the average of an array of intgers

```C++

float get_average(int *array, uint8_t size) {
    if (size == 0) {
        // To avoid division by zero, you might want to handle this case.
        // You can return an error code or some appropriate value.
        return 0.0;
    }

    int sum = 0;
    for (uint8_t i = 0; i < size; i++) {
        sum += array[i];
    }

    return (float)sum / size;

}
```

### Write a C function that swap the elements of 2 arrays with equal size

```C++

#include <stdint.h>

void swap_arrays(uint16_t *array1, uint16_t *array2, uint16_t size) {
    for (uint16_t i = 0; i < size; i++) {
        // Swap elements between the two arrays
        uint16_t temp = array1[i];
        array1[i] = array2[i];
        array2[i] = temp;
    }
}
```

### Assume you have an overloaded function my_print(), which prints arguments of types: uint32_t, int32_t, char, string. Extend the function to support printing a float argument (up to 3 digits of the fraction is enough!)   

```C++
void my_print(float x){

  uint32_t my_int;
  float my_float;
  union u{
    uint32_t a;
    float b;
  };
  union u my_union;
  my_union.b = x;
  uint32_t temp =  my_union.a;
  uint32_t mask = 1;
  mask = (mask<<31);
  temp = temp & mask;
  temp = (temp>>31);
  my_float = x;
  if (temp == 1){
    my_print("-");
    my_float *= -1;
  }
  my_int = my_float;
  my_print (my_int);
  my_print(".");
  my_float = (my_float - my_int)*1000;
  my_print((uint32_t) my_float);
   }



```
