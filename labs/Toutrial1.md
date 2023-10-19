 ### 1)	The code in Figure 2 has two functions: The first initializes the UART in the ATMega328 to operate at 9600 baud rate assuming a clock frequency of  16MHz.the second function sends a byte through the UART. When the MCU is connected to a serial terminal, the terminal will print the character equivalent to the ASCII code sent in the byte. Examine and test the cod

 

 ```C++
 
 void setup() {
  Serial.begin(9600);
}

void loop() {
  // Call my print with different type arguments
  uint8_t a = 10;
  my_print(a);

  char b = '1';
  my_print(b);

  char c[] = "Hello World!";
  my_print(c);

  while(1);
}

void my_print(uint8_t x){
  Serial.println("This function prints a uint8_t");
}

void my_print(uint16_t x){
  Serial.println("This function prints a uint16_t");
}

void my_print(uint32_t x){
  Serial.println("This function prints a uint32_t");
}

void my_print(char x){
  Serial.println("This function prints a char");
}

void my_print(char x[]){
  Serial.println("This function prints an array of chars terminated with a null");
}


 
 ```

ASCII code for 10 is new line character 

 ```C++
 
 void setup() {
  USART_Init();
}

void loop() {
  
  uint8_t a = 65; //ASCII code for A
  USART_send_byte(a);

  
  while(1);
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


###	The function get_digits() in Figure 3 extracts the digits in a uint32_t number (num) passed as an argument and store the digits in an array also passed as an argument. The function also returns the total number of digits in the number. Run and examine the code in Figure 3. 

```C++


void setup() {
  USART_Init();
}

void loop() {
  
  uint32_t num = 1056;
  uint8_t arr[10]; //10 is maximum number of digits in a uint32_t
  uint8_t digits =  get_digits(num, arr);
  for(int i= (digits-1); i>=0; i--){
    USART_send_byte(arr[i] + 48); //48 ASCII for 0
  }
  while(1);
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



### 1)	The previous steps contain all the functions necessary to create a custom overloaded serial function. Figure 4 contains an example of an overloaded print function supporting uint32_t, uint16_t, uint_8t, char and array of chars.     


```C++

void setup() {
  USART_Init();
}

void loop() {
  
  uint8_t a = 255;
  my_print(a);
  my_print("\n\r");//new line

  uint16_t b = 1060;
  my_print(b);
  my_print("\n\r");//new line

  my_print("Hello World!");
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