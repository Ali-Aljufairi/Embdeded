## Struct

```c++
struct my_struct {
    unint8_t a;
    unint8_t b;
    float c;

}


void setup() {
    Serial.begin(9600);
}

void loop() {
    my_struct s;
    s.a = 10;
    s.b = 20;
    Serial.println(s.a);
    Serial.println(s.b);
    Serial.println(sizeof(s));//6
}
```

> Struct is a user-defined data type in C/C++. It allows you to combine multiple variables of different data types into a single variable.

## Union

```c++
union my_union {
    unint8_t a;
    unint8_t b;
    float c;
}

 void setup() {
    Serial.begin(9600);
 }

    void loop() {
        my_union u;
        u.a = 10;
        u.b = 20;
        Serial.println(u.a);
        Serial.println(u.b);
        Serial.println(sizeof(u));//4
    }

```

> union is a user-defined data type in C/C++. It allows you to combine multiple variables of different data types into a single variable. However, a union can only store the value of one member at a time.

## Bitfield

```c++

struct my_bitfield{
    unint8_t a:1;
    unint8_t b:2;

}

void setup() {
    Serial.begin(9600);
}

void loop() {
    my_bitfield b;
    b.a = 1;
    b.b = 2;
    Serial.println(b.a);
    Serial.println(b.b);
    Serial.println(sizeof(b));//1
}
```

> A bit field is a structure that allows the programmer to control how the data is packed into memory. This is especially useful when you are trying to save memory or when you are trying to send data over a network.

## Enum

```c++
typedef enum {
 p0 = 1,
 p1 =(1<<1),
 p2 =(1<<2),
 p3 =(1<<3),
 p4 =(1<<4),
 p5 =(1<<5),
 p6 =(1<<6),
 p7 =(1<<7),
}port_mask;


void setup() {

    Serial.begin(9600);

    port_mask mask = p0 | p1 | p2;

    DDRB |= mask;
}
```
