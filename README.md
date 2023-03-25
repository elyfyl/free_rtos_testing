The operating system does many things at once. In the same way, in RTOS, will do many things at the same time, sometimes the order of priority will be different, and we will see what we can do according to the priority situation.

In Cube IDE, we see FreeRtos in Midlleware. CMSIS V2 provides us with the interface, it allows us to use STM32's HAL library in FreeRtos. 

We can add tasks from the Tasks and Queues section and set them in order of priority.

Ticks from the clock signals we call SysTick in System Core are used to divide these tasks, so it would be more appropriate to choose a timer that belongs to our card in the Timebase Source.

We will use the USART to receive the data in the port and print text to our computer, we can see the tasks as text.

We will not write anything in the while part of the code, we will do the operations in the startTask functions.

Although there is an infinite loop inside the functions since it is RTOS, it can switch to the other loop, it does this by dividing the clock signals.

For a task with a low priority order, if that task enters an infinite loop, other tasks continue.

I created 4 different tasks. The first one is high-priority LED lighting, the second one is sending data by polling over the normal priority Uart with a button, and the third one is low-priority reading with a potentiometer.

osDelay focuses on the specific task, HAL_Delay provides a general delay.
