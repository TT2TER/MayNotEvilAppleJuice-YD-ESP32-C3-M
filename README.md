# 只能说还挺好玩的
放一些参考文档和链接吧

在 `./doc`中有我这款板子的图

[源地工作室资料链接](http://vcc-gnd.com:8080/yd-data/YD-ESP32-C3/ESP32-C3-M/)

![esp32-c3-yd_pinouts_zl](https://pic.1314171.xyz/i/2023/11/03/esp32-c3-yd_pinouts_zl.jpg)

[购买链接](https://99tech.com.au/product/esp32-c3-yd/)
[taobao](https://m.tb.cn/h.58Cl34j?tk=NrSqW2Ren0D)

## 简介
This board is assembled with an original ESP32-C3-MINI-1 module from Espressif, with 4MB Flash(ESP32-C3-MINI-1-N4). It is a general-purpose Wi-Fi + Bluetooth® LE MCU module that integrates complete Wi-Fi and Bluetooth LE functions.

PLEASE NOTE: The pin headers are yellow(as shown in photos) or red.

Most of the I/O pins on the module are broken out to the pin headers on both sides of this board for easy interfacing. Developers can either connect peripherals with jumper wires or mount the module on a breadboard.

There is a RGB WS2812 LED connected to IO8. It has a Red, Green and Blue LED that are individually addressable. There are plenty of examples on the internet showing how to drive a WS2812 LED. For example, Google "WS2812 Arduino" or "WS2812 c code".

There are two USB C connectors. The one is connected to the USB peripheral of the ESP32-C3 chip. The second is connected to the ESP32-C3 modules UART via a CH340 virtual com port.
Features

    2.4 GHz Wi-Fi: IEEE 802.11 b/g/n-compliant
    Bluetooth and Bluetooth LE: Bluetooth 5, Bluetooth mesh
    4 MByte(32Mbit) SPI Flash
    384 KByte ROM
    400 KByte SRAM
    PCB Antenna
    Dual Type-C USB connectors
    Reset and User/Firmware buttons
    RGB WS2812 User LED
    Power LED
    Virtual USB port provided by CH340 for debugging and firmware upgrade
    Assembled with ESP32-C3 module
    Compact size of 35.6 x 30
    Supply Voltage: 5V via USB
    Circuit Voltage: 3.0 to 3.6V Circuit Operation

## 淘宝官方发的链接
    这段文字是ESP32-C3的资料。
    基础资料包括（原理图尺寸图等）：http://124.222.62.86/yd-data/YD-ESP32-C3/
    如果查看引脚功能图可以参考链接如下：
    https://docs.espressif.com/projects/esp-idf/zh_CN/latest/esp32c3/_images/esp32-c3-devkitc-02-v1-pinout.png
    如果计划使用官方的idf-C语言编程详细资料链接（例程就是的API参考）：
    https://docs.espressif.com/projects/esp-idf/zh_CN/latest/esp32/get-started/index.html
    如果计划使用Ardiuno编程资料链接：
    https://docs.espressif.com/projects/arduino-esp32/en/latest/getting_started.html#about-arduino-esp32
    如果计划使用micropython语言编程资料链接如下：
    https://docs.micropython.org/en/latest/esp32/quickref.html
    如需要安装核心板的硬件usb转串口驱动：
    https://www.wch.cn/products/CH340.html?from=list
    micropython的ESP32-C3固件注意有两个固件：https://micropython.org/download/

    核心板上有个两个USB口， 一个是USB转串口硬件的USB口，另一个是直连MCU的USB功能（注意是USB功能，不要直觉的把USB功能就当做串口，可以通过程序实现虚拟出串口）。

## 我自己找的链接
[platformio](https://docs.platformio.org/en/latest/boards/espressif32/esp32-c3-devkitm-1.html)

[乐鑫](https://docs.espressif.com/projects/esp-idf/zh_CN/latest/esp32c3/hw-reference/esp32c3/user-guide-devkitm-1.html)

## 痛心，买到盗版了
我之所以上面附上真这么多资料，是因为我买到盗版的板子了

找店家要文档，店家不仅没有，还反倒找我要我找到的文档

一开始是真的没意识到买了盗版，难过

各个领域盗版猖獗啊~
# 以下是原项目的Readme
# EvilAppleJuice ESP32

Spam BLE advertisements on iPhones!

|iPhone 15s (latest)|Older iPhones|
|-------------------|-------------|
|<video controls width="250" src="https://user-images.githubusercontent.com/6680615/274864225-53ed6d7c-0569-4f22-b55b-bc9973c4bc93.mp4"></video>|<video controls width="250" src="https://user-images.githubusercontent.com/6680615/274864287-c6e871fd-9fdf-4507-ae21-a566beead5cc.mp4"></video>|

Based off of the work of [ronaldstoner](https://github.com/ronaldstoner) in the [AppleJuice repository](https://github.com/ECTO-1A/AppleJuice/blob/e6a61f6a199075f5bb5b1a00768e317571d25bb9/ESP32-Arduino/applejuice.ino).

With the randomization optimizations it can render an iPhone almost useless with a single ESP32 (a new notification as soon as you close the old one).

Confirmed on:
* iPhone 14 Pro (running iOS 16.6.1)
* iPhone 13 Pro (TBD which iOS)
* iPhone 11 (running iOS 16.6.1)
* iPhone X (running iOS 14.8 (18H17)) - only "AppleTV Keyboard", "TV Color Balance", "AppleTV Setup", "AppleTV Homekit Setup", "AppleTV New User".

Not working on:
* iPhone 4S (running iOS 10.3 (14E277))

Other observations:
* Doesn't seem to spawn notifications if Keyboard is open / Camera is open

### Video Demo

Single ESP32 vs. iPhone 14 Pro @ iOS 16.6.1

https://github.com/ECTO-1A/AppleJuice/assets/6680615/47466ed6-03c9-43b2-a0d0-aac2e2aaa228

## Notable Differences

This implementation makes the following changes:

* Random source MAC address (including `BLE_ADDR_TYPE_RANDOM`)
* Randomly pick BLE Advertisement Type ([this may lead to more success](https://github.com/ECTO-1A/AppleJuice/pull/25))
* Randomly pick one of the possible devices

And it makes these random choices every time it runs (default re-advertise every second).

Given the 29 devices and the 3 advertisement types, there are a total of 87 unique possible advertisements (ignoring the random source MAC) possible, of which one is broadcast every second.

## Usage

Clone the repo, and easiest would be to use VS Code w/ PlatformIO to upload it to your ESP32.

This project has been tested on an [ESP32-C3 from AirM2M](https://wiki.luatos.com/chips/esp32c3/board.html).

