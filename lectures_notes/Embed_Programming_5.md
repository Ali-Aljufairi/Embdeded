## Functions 


```C++
//forward declaration
int add(int a,int b)


void hello_world() {
   Serial.println("Hello World");
}   

int add (int a, int b) {
   return a + b;
}
void setup() {
   Serial.begin(9600);
   hello_world();
}
```

## global vs local variables vs static variables
 - global variables are declared outside of any function, and they can be accessed (used) on any function in the program.

- local variables are declared inside a function, and they can be used only inside that function.

- static variables are declared with the static keyword, and can be used only inside the function where they are declared.

```C++
int global_variable = 10;


void setup() {
   Serial.begin(9600);
   int local_variable = 20;
   Serial.println(global_variable);
   Serial.println(local_variable);
}
```
## Static Data 

This is a block of resevered space in memory that is not destroyed when the function is exited. 


## The  Stack

The stack is a block of memory that is used to store local variables and parameters used by any function.

## The Heap

The heap is a block of memory that is used for dynamic memory allocation.


![Memory](./images/memory.png) 