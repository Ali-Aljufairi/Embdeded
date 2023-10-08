## arrays

```C++
//
uni16_t arr[5] = {1,2,3,4,5};



for (int i=0; sizeof(arr)/sizeof(arr[0]); i++) {
    Serial.println(arr[i]);
}

// this is the same as above
for (int i=0; i<5; i++) {
    Serial.println(arr[i]);
}


// this is the same as above
for (auto& i: arr) {
    Serial.println(i);
}

// multi dimentional array
int arr[2][3] = {{1,2,3},{4,5,6}};

//  print 2d array
for (int i=0; i<2; i++) {
    for (int j=0; j<3; j++) {
        Serial.println(arr[i][j]);
    }
}

```

## common mistakes with arrays

1. array index out of bound

1. forgetting to initialize array

1. forgetting to check array size

1. calling function with array without passing array size

## Pointers

```C++
//  declare pointers

void setup{
Serial.begin(9600);

}

void loop {

int x = 10;
int *ptr = &x;


Serial.println(x);//10


Serial.println((unit32_6)ptr);//0x7ff

fuc(x);
Serial.println(x);//since x is pass by value, x is still 10

func_ptr(&x);
Serial.println(x);//since x is pass by reference, x is now 11

func_ref(x);

}


void fuc(int x) {
    Serial.println("Change x from func");
    x=+1;
}

void func_ptr(int *ptr) {
    Serial.println("Change x from func");
    *ptr=+1;
}

void func_ref(int &ref) {
    Serial.println("Change x from func");
    ref=+1;
}

```

## Explain the difference between pass by value and pass by reference

1. pass by value: the value of the variable is copied and passed to the function. The function will not change the value of the variable.

1. pass by reference: the address of the variable is passed to the function. The function can change the value of the variable.

1. pass by pointer: the address of the variable is passed to the function. The function can change the value of the variable.

```C++

void setup{
Serial.begin(9600);

}
void loop {

// you can't use sizeof() to get the size of a pointer
int  func (int arr[] ,int size )
{
int sum = 0;

for (int i = 0; i < size; i++)
{
sum += arr[i];
// or sum += *(arr);
// arr++;

}

}

}
```
### null pointer

```C++
float *ptr = nullptr;

``` 

1. initialize pointer 
2. check if pointer is valid
3. pass pointer to function
4. return pointer from function



## cast pointer

```C++
float *fp =&x;

uint32_t *ptr = (uint32_t*)fp;

Serial.println("float value is decemial" ); 

Serial.println(*fp,BIN); 

```


