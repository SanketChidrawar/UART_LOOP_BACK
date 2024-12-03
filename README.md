# UART_LOOP_BACK
UART Loopback Test for STM32
This project demonstrates a simple method to verify the UART loopback functionality on an STM32 microcontroller. It checks whether the transmit (Tx) and receive (Rx) connections are properly established by sending and receiving a test byte.

Objective
To validate the UART communication path by transmitting a byte through the Tx pin and checking if the same byte is received on the Rx pin in a loopback configuration.

Pin Configuration
Tx (Transmit): PA2
Rx (Receive): PA3
Setup Instructions
Hardware Connection:

Connect Tx (PA2) to Rx (PA3) directly by using a jumper wire or shortening the pins.
Running the Test:

Open the project in STM32CubeIDE.
Compile and run the code in Debug Mode.
Execution:

In debug mode, click Resume to continue program execution.
The code will transmit a single byte ("H") through the Tx pin.

Verification:
Open the Live Expressions window in STM32CubeIDE.
Monitor the variable rx_data.
If the test is successful, you should see the byte "H" received and stored in rx_data.

Expected Outcome
If the character "H" appears in rx_data, the UART loopback is confirmed to be working correctly, indicating a successful connection between the Tx and Rx pins.
Notes
Make sure no external devices are connected to the Tx and Rx pins during this test.
Use this loopback test only for debugging and validation purposes.
