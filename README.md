# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.

 <img width="1919" height="1198" alt="Screenshot 2025-10-27 212235" src="https://github.com/user-attachments/assets/d8fc724c-1581-4fc7-9339-21854397be2e" />



3. Click **File → New STM32 Project**.
<img width="692" height="402" alt="image" src="https://github.com/user-attachments/assets/7e0b8214-ac5b-41ae-8085-9146319e36ce" />

4. Select the **target microcontroller** or board and click **Next**.
<img width="692" height="397" alt="image" src="https://github.com/user-attachments/assets/b519300b-d8b6-41da-b1fe-1955f6aa572d" />



5. Name the project.
<img width="692" height="408" alt="image" src="https://github.com/user-attachments/assets/b3c56a6e-8bf1-4f62-82d6-b1ae92bddcf8" />

6. The corresponding `.ioc` file will be generated automatically.
<img width="692" height="409" alt="image" src="https://github.com/user-attachments/assets/0c636a40-1f12-4133-a9dc-692db9e28611" />

7. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="692" height="400" alt="image" src="https://github.com/user-attachments/assets/32afc88d-2f2c-4df0-a8b6-6bccdc6ce89b" />

8. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="692" height="400" alt="image" src="https://github.com/user-attachments/assets/f410b950-362a-4b85-b8a5-4b30e569b79b" />
 
9. Edit the generated main program as required.
<img width="692" height="411" alt="image" src="https://github.com/user-attachments/assets/ea75fbde-e9e0-41a4-be3c-b6325b275664" />

10. Click **Project → Build All**.
<img width="692" height="409" alt="image" src="https://github.com/user-attachments/assets/28eaef15-6f6b-4c36-bbbe-4118b83c7337" />

11. Link the **HEX file** using the post-build process.
<img width="692" height="144" alt="image" src="https://github.com/user-attachments/assets/ec3db784-99be-407b-a7c2-77ad25a9bac1" />

12. Click **Debug** and connect the **STM Nucleo Board**.
<img width="692" height="400" alt="image" src="https://github.com/user-attachments/assets/815eb855-a1c0-49fa-ab5c-207e985851ce" />
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

<img width="603" height="432" alt="image" src="https://github.com/user-attachments/assets/672cdac1-6e33-4784-8b56-fcc602c9f0c5" />

CASE 2: LED OFF

<img width="596" height="416" alt="image" src="https://github.com/user-attachments/assets/ef9e14a5-c263-46ec-9622-ec9400757c7f" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
