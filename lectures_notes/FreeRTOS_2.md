<h2 align="Center"> FreeRTOS Multitasking </h2>

- FreeRTOS is a multitasking RTOS

- Priorities are used to determine which task should be executed first

- Amazone FreeRTOS is a real-time operating system kernel for microcontrollers that makes small, low-power edge devices easy to program, deploy, secure, connect, and manage.

<h3 align="Center"> Watchdog Timer </h3>

- A watchdog timer (WDT) is a hardware timer that automatically generates a system reset if the main program neglects to periodically service it.

<h3 align="Center"> Creating Task </h3>

```C++

void setup(){

Serial.begin(9600);

xTaskCreate(

  blink_task, /* Task function. */
  "Blink Task", /* String with name of task. */
    128, /* Stack size in bytes. */
    NULL, /* Parameter passed as input of the task */
    2, /* Priority of the task. */
    NULL); /* Task handle. */

}


Void loop(){

}


void blink_task(void *pvParameters){

  (void) pvParameters;

  pinMode(LED_BUILTIN, OUTPUT);

for (;;)
    {
        Serial.println("Blink");
        dely(1000);
    }

}
```

<h3 align="Center"> vTaskDelay </h3>

> The delay function is used to delay the execution of the task for a specific time which is not blocking the other tasks


```C++
//  Task delay
void blink_task(void *pvParameters){

  (void) pvParameters;

  pinMode(LED_BUILTIN, OUTPUT);
  Serial.println("Blink");
  VTaskDelay(1000/portTICK_PERIOD_MS);  // 1000 ms

}


```




<h3 align="Center"> vTaskDelay until </h3>

#### The function take 2 paramerters 
 
  PxPerviousWakeTime pointer to variable that holds th etime at which the task was last unblokded

  XTimeIncremenet : the cycyle time period the task will be unblocked  at time

    $*pxPereviousWakeTime + XTimeIncrement$



```C++

void task2(void *pvparamaterts)
 {

  (void) pvParameters; 

  TickType_t xLastWakeTime

 for(;;)
   {

    Serial.println("Hello from task2")
    vTaskDelay(&xLastWakeTime,(1000/portTick_PERIOD_MS))

   }


 }






```

