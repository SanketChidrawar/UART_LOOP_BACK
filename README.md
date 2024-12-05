UART Loopback Test for STM32
Project Description
This project verifies the UART loopback functionality on an STM32 microcontroller by transmitting a byte and checking if it is correctly received. It helps validate the UART hardware and connections.

Objective
To ensure the UART transmit (Tx) and receive (Rx) paths are correctly established by sending a test byte ('H') from Tx and receiving it on Rx in a loopback configuration.

Hardware Setup
Microcontroller: STM32F4 Series
Pin Connections:
Tx (PA2) → Rx (PA3) (connected via jumper wire).
Pin Configuration:
Tx Pin: PA2
Rx Pin: PA3
Software Setup
IDE: STM32CubeIDE
Debugger: ST-LINK
Configuration:
Baud Rate: 115200
Word Length: 8 bits
Stop Bits: 1
Parity: None
Mode: TX/RX
How to Run the Project
Connect the Pins:
Short the Tx (PA2) and Rx (PA3) pins using a jumper wire.
Load the Code:
Open the project in STM32CubeIDE.
Compile and flash the code.
Execute:
Enter Debug Mode in STM32CubeIDE.
Click Resume to start code execution.
Check Data:
Use the Live Expressions window to monitor the rx_data variable.
The code transmits one byte ('H'). If the loopback is successful, the same byte should be received and stored in rx_data.
Expected Outcome
If the character 'H' is observed in rx_data, the UART loopback is functioning correctly, confirming the connection between the Tx and Rx pins.

File Structure
main.c: Contains the main logic, including initialization and the loopback test.
main.h: Header file with pin configurations and function prototypes.
stm32f4xx_it.c/h: Contains interrupt service routines, including the handler for UART.
stm32f4xx_hal_conf.h: HAL configuration file enabling the UART module.
Code Overview
UART Initialization:

c
Copy code
static void MX_USART2_UART_Init(void) {
    huart2.Instance = USART2;
    huart2.Init.BaudRate = 115200;
    huart2.Init.WordLength = UART_WORDLENGTH_8B;
    huart2.Init.StopBits = UART_STOPBITS_1;
    huart2.Init.Parity = UART_PARITY_NONE;
    huart2.Init.Mode = UART_MODE_TX_RX;
    huart2.Init.HwFlowCtl = UART_HWCONTROL_NONE;
    huart2.Init.OverSampling = UART_OVERSAMPLING_16;
    HAL_UART_Init(&huart2);
}
Main Loop:

c
Copy code
uint8_t tx_buffer[] = "H";
uint8_t rx_data[1];

HAL_UART_Receive_IT(&huart2, rx_data, 1);

while (1) {
    HAL_UART_Transmit(&huart2, tx_buffer, sizeof(tx_buffer), HAL_MAX_DELAY);
}
Interrupt Handler:

c
Copy code
void USART2_IRQHandler(void) {
    HAL_UART_IRQHandler(&huart2);
}
Troubleshooting
No Data Received:
Check the physical connection between Tx and Rx.
Ensure proper HAL configuration for UART.
Incorrect Data:
Verify the baud rate and data format.
Notes
Ensure no external devices are connected to the Tx and Rx pins during testing.
This project is for debugging and validation purposes only.
