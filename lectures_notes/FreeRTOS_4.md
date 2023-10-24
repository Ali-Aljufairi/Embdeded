
## FreeRTOS Mutex Explained What is a Mutex?

A Mutex is like a magic key that helps keep order when many people (or things) want to use the same toy (or resource) at the same time. It makes sure that only one person (or thing) can use the toy (or resource) at any given moment.

## Why do we need Mutex?

Imagine a group of friends playing with a single toy train. They all want to play with it, but if everyone tries to grab it at once, they might break it or not have fun. A Mutex helps them take turns nicely, so the toy train stays safe and everyone gets a chance to play.

## How does it work?

Let's say you and your friend want to play with a special toy car, but only one person can have it at a time. You grab the Mutex (the magic key) first and tell your friend, "I have the key; I'm playing with the toy car now." Your friend has to wait patiently until you're done. When you finish, you give the Mutex (the key) to your friend, and now it's their turn to play.

In computer programs, it's like different parts of the program wanting to use the same piece of information. The Mutex helps them take turns, so the information doesn't get messed up, just like with the toy car.


```C++


#include <Arduino.h>
#include <FreeRTOS.h>
#include <task.h>
#include <semphr.h>

// Define a global mutex
SemaphoreHandle_t xMutex;

// Shared resource
int sharedResource = 0;

// Task 1
void Task1(void *pvParameters) {
  while (1) {
    // Take the mutex to access the shared resource
    xSemaphoreTake(xMutex, portMAX_DELAY);

    // Access the shared resource (increment it)
    sharedResource++;

    // Release the mutex to allow other tasks to use the resource
    xSemaphoreGive(xMutex);

    // Do some work
    // ...

    vTaskDelay(pdMS_TO_TICKS(1000)); // Sleep for 1 second
  }
}

// Task 2
void Task2(void *pvParameters) {
  while (1) {
    // Take the mutex to access the shared resource
    xSemaphoreTake(xMutex, portMAX_DELAY);

    // Access the shared resource (decrement it)
    sharedResource--;

    // Release the mutex to allow other tasks to use the resource
    xSemaphoreGive(xMutex);

    // Do some work
    // ...

    vTaskDelay(pdMS_TO_TICKS(1000)); // Sleep for 1 second
  }
}

void setup() {
  // Create the mutex
  xMutex = xSemaphoreCreateMutex();

  if (xMutex != NULL) {
    // Create Task 1
    xTaskCreate(Task1, "Task1", 1000, NULL, 1, NULL);

    // Create Task 2
    xTaskCreate(Task2, "Task2", 1000, NULL, 2, NULL);

    // Start the FreeRTOS scheduler
    vTaskStartScheduler();
  }
}

void loop() {
  // The loop should not be used with FreeRTOS; tasks run independently.
}




```