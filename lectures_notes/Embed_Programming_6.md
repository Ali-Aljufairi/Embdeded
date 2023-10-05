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
## common  mistakes with arrays

1. array index out of bound

1. forgetting to initialize array

1. forgetting to check array size

1. calling function with array without passing array size