### You are required to extend the support for the overloaded my_print() function discussed in Lab Tutorial 1 to include support for:

-     Int8_t, int16_t, int32_t signed data types.
- he float data type (printing with a precision of three fraction digits).

<br>

```C++

void setup() {
  USART_Init();
}

void loop() {

  int8_t a = 8;
  my_print(a++);
  my_print("\n\r");//new line

  int16_t b = -150;
  my_print(b);
  my_print("\n\r");//new line

  int32_t c = -300;
  my_print(c);
  my_print("\n\r");//new line

  float d = 20.61232312;
  my_print(d);
  my_print("\n\r");//new line


  while(1);
}

//print a uint32_t
void my_print(uint32_t x){
  uint8_t arr[10]; //10 is maximum number of digits in a uint32_t
  uint8_t digits =  get_digits(x, arr);
  if (digits == 0){
    USART_send_byte(48);//48 ASCII for 0
  }else{
    for(int i= (digits-1); i>=0; i--){
    USART_send_byte(arr[i] + 48);
  }
  }
}
//print a uint16_t
void my_print(uint16_t x){
  uint8_t arr[5]; //5 is maximum number of digits in a uint16_t
  uint8_t digits =  get_digits(x, arr);
  if (digits == 0){
    USART_send_byte(48);//48 ASCII for 0
  }else{
    for(int i= (digits-1); i>=0; i--){
    USART_send_byte(arr[i] + 48);
  }
  }
}
//print a uint8_t
void my_print(uint8_t x){
  uint8_t arr[3]; //3 is maximum number of digits in a uint8_t
  uint8_t digits =  get_digits(x, arr);
  if (digits == 0){
    USART_send_byte(48);//48 ASCII for 0
  }else{
    for(int i= (digits-1); i>=0; i--){
    USART_send_byte(arr[i] + 48);
  }
  }
}
//print a int32_t
void my_print(int32_t x){
  if (x < 0) {
    USART_send_byte('-');
    x = -x;
  }
  my_print((uint32_t)x);
}

//print a int16_t
void my_print(int16_t x){
  if (x < 0) {
    USART_send_byte('-');
    x = -x;
  }
  my_print((uint16_t)x);
}
//print a int8_t
void my_print(int8_t x){
  if (x < 0) {
    USART_send_byte('-');
    x = -x;
  }
  my_print((uint8_t)x);
}

//print a float
void my_print(float x) {
  uint8_t decimalPlaces = 3;
  int32_t intValue = int32_t(x);
  my_print(intValue); // Print the integer part

  float decimalValue = x - float(intValue);
  if (decimalValue < 0) {
    decimalValue = -decimalValue; // Make it positive if it's negative
  }

  // Print the decimal point
  USART_send_byte('.');

  // Print the decimal part with the specified number of decimal places
  for (int i = 0; i < decimalPlaces; i++) {
    decimalValue *= 10;
    int digit = int(decimalValue);
    USART_send_byte(digit + '0');
    decimalValue -= float(digit);
  }
}


//print a char
void my_print(char x){
  USART_send_byte((uint8_t) x);
}

//print a string of chars
void my_print(char x[]){
  int i = 0;
  while(x[i] != NULL){
      USART_send_byte((uint8_t) x[i]);
      i++;
    }
}

uint8_t get_digits(uint32_t num, uint8_t arr[]){
  uint32_t temp = num;
  int i = 0;
  while(temp !=0){
    arr[i] = (uint8_t)(temp%10);
    temp/= 10;
    i++;
  }
  return i;
}

void USART_Init()
{
  // Set Baud Rate tp 9600 for 16MHZ clock
  UBRR0H = 0;
  UBRR0L = 103;
  // 8 bit data, one stop bit, no parity
  UCSR0C = 6;
  // Enable Receiver and Transmitter
  UCSR0B = 24;
}

void USART_send_byte(uint8_t DataByte)
{
  while (( UCSR0A & (1<<UDRE0)) == 0) {}; // Do nothing until UDR is ready
  UDR0 = DataByte;
}
```
