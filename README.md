1] # STM32_HAL_PROGRAM
HAL-based programming is an embedded programming approach where the application code , controls hardware using HAL APIs instead of directly accessing hardware registers.
A HAL API is a function provided by the HAL library that allows the programmer to control hardware peripherals.


2] | Peripheral | HAL API Example        |
| ---------- | ---------------------- |
| GPIO       | `HAL_GPIO_WritePin()`  |
| GPIO       | `HAL_GPIO_ReadPin()`   |
| UART       | `HAL_UART_Transmit()`  |
| ADC        | `HAL_ADC_Start()`      |
| TIMER      | `HAL_TIM_Base_Start()` |
| Delay      | `HAL_Delay()`          |


3] Application Code
       ↓
HAL API functions
       ↓
HAL Drivers
       ↓
Hardware Registers
       ↓
Microcontroller Hardware

4] In HAL, each peripheral has a driver module, and the HAL API function call executes that driver code to control the hardware peripheral.

5]  What HAL does:
Initializes peripherals (GPIO, UART, ADC, SPI, I2C, TIM)
Manages clocks and interrupts
Handles hardware differences between MCU families


6] 1️⃣ HAL provides driver programs
For each peripheral:
GPIO → stm32xx_hal_gpio.c
UART → stm32xx_hal_uart.c
ADC → stm32xx_hal_adc.c
TIM → stm32xx_hal_tim.c
These files contain driver code written by the vendor.

2️⃣ HAL API = entry point to the driver

Example:
HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
This is a function call

Inside this function:
Clock check
Parameter validation
Register write
Hardware pin is controlled

👉 You call, not define, the driver.

3️⃣ Who defines the driver?
Component	Who writes it
HAL driver code	MCU vendor (ST, Espressif, NXP)
HAL API functions	Vendor
Application logic	You (developer)

