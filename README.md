# UART_LOOP_BACK

UART Loopback Test Code for STM32
This project verifies the UART loopback functionality by checking if the transmit (Tx) and receive (Rx) paths are correctly established.

Purpose
The code ensures that data transmitted through the Tx pin can be correctly received by the Rx pin in a loopback configuration. It helps validate the UART hardware and connections within the system.

Pin Details
Tx Pin: PA2
Rx Pin: PA3
How to Use
Connect the Pins:
Short the Tx (PA2) pin and Rx (PA3) pin.
Load the Code:
Open the project in STM32CubeIDE.
Run the project in Debug Mode.
Resume Execution:
After entering debug mode, click Resume to start the code execution.
Check Data:
Use the Live Expressions view in STM32CubeIDE to monitor the variable rx_data.
The code sends one byte, "H", through the Tx pin.
If the loopback is successful, the same byte ("H") should be received and stored in rx_data.
Expected Outcome
If "H" is observed in rx_data, the UART loopback is functioning correctly, indicating the connection between Tx and Rx is established.
Notes
Ensure no external devices are connected to the Tx and Rx pins during the loopback test.
Use jumper wires to create the physical connection between the pins if needed.
