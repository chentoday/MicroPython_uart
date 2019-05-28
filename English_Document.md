# mircopython - uart
#### 📖 [English document](https://github.com/aJantes/MircoPython-uart/blob/master/README.md)
![](album/bit.gif)
> ardware introduction： [BPI:bit(ESP32)](https://github.com/aJantes/introduce-bpi-bit/blob/master/README.md)   

# Serial port communication

There are three UART controllers on ESP32 chip.

Pin|RX|TX
--|:--:|--:
UART0|3|1
UART1|23|19
UART2|5|18

Note: UART0 has been used by REPL.
## **Initialization and Use of Serial Port**
## Main functions
1. `uart=UART(1)`

For example: `uart = UART(1) `, Initialize serial port 1 with a given baud rate.

2. `uart.init((baudrate, bits, parity, stop, tx, rx, rts, cts, timeout))`:

Initialize the specified serial port
parameter|function
--|--
`id` | Serial slogans: 1, 2
`baudrate` | baud rate
`bits` | Number of digits per character
`parity` | Parity check: 0-even, 1-odd
`rx , tx` | UART read and write pins
`stop` | Stop number: 1, 2
`timeout` | Timeout < timeout < 0x7FFF FFFFFF (decimal: 0 < timeout < 2147483647)


For example: `uart.init(9600, bits=8, parity=None, stop=1)` Initialize the serial port with a given parameter.` 9600 `  is set baud rate，`bits=8` is set data bits,`parity=None` is set whether parity is turned on,`stop=1` is set the stop bit.

3. `uart.any()`:

Returns an integer, which is the number of characters that can be read without blocking. If there are no available characters, 0 is returned; if there are available characters, a positive number is returned. If there is more than one readable character, the method returns 1.

---
## Usart Example

1.  [uart.py](https://github.com/aJantes/MircoPython-uart/blob/master/example/uart.py)     -Use UART2 to send and receive messages