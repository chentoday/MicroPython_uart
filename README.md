# mircopython - uart
#### 📖 [English document](https://github.com/aJantes/MircoPython-uart/blob/master/English_Document.md)
![](album/bit.gif)
> 硬件介绍： [BPI:bit(ESP32)](https://github.com/aJantes/introduce-bpi-bit/blob/master/README.md)   

# 串口通信

ESP32芯片上，有3个 UART控制器。

Pin|RX|TX
--|:--:|--:
UART0|3|1
UART1|23|19
UART2|5|18

注意： UART0 已经被 REPL 使用。
## **串口初始化与使用**
## 主要函数
1. `uart=UART(1)`

例如: `uart = UART(1) `, 使用给定波特率初始化串口1。

2. `uart.init((baudrate, bits, parity, stop, tx, rx, rts, cts, timeout))`:

给指定的串口初始化
参数|作用
--|--
`id` | 串口号:1、2
`baudrate` | 波特率
`bits` | 每个字符的位数
`parity` | 奇偶校验:0-偶数,1-奇数
`rx , tx` | UART读、写引脚
`stop` | 停止位数量:1、2
`timeout` | 超时时间（单位：毫秒） < timeout ≤ 0x7FFF FFFF (十进制：0 < timeout ≤ 2147483647)


例如: `uart.init(9600, bits=8, parity=None, stop=1)` 使用给定参数初始化串口。`9600` 为设置波特率，`bits=8`为设置数据位,`parity=None`为设置是否开启奇偶校验,`stop=1`为设置停止位。

3. `uart.any()`:

返回一个整数，该整数即为在不阻塞情况下可读取的字符数。若无可用字符，则返回0,；若有可用字符，则返回一个正数。若有超过1个可读取字符，该方法则返回1。

---
## usart 例子

1.  [uart.py](https://github.com/aJantes/MircoPython-uart/blob/master/example/uart.py)     -使用 uart2 收发消息