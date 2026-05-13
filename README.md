# ESP32 LogicAnalyzer
### A *SUMP* compatible 16Bit Logic Analyzer for ESP32 MCUs.

![PulseView](/ESP32_LogicAnalyzer_in_PulseView.png)

* Use Arduino to compile and flash your ESP32.
* Uses **ESP32 I2S DMA** and could capture speeds up to **20 Mhz**.
* Support **8 bit** and **16 bit** operations.
* Maximum **128k** samples. (Even using 8bit capturing mode.)
* RLE compression supported.
* Analog input is **NOT** available.
* ~~WROOVER modules support **2M** samples but only up to **2 Mhz** due bandwith limit on PSRAM access.~~ Under development.
* Default OLS port is **UART0** and default baudrate is **912600**.
* You can use **UART2** and or higher baud rates for high speed OLS communication by altering the lines at top of the header file...
* **WARNING:** 
  - For OLS port at UART0
    - Set **"Core Debug Level"=None** before compiling code at arduino, specially for > 10Mhz capture operations.
  - **GPIO23** used for I2S input clk and  **GPIO22** LEDC clk output.  Don't use those for IO or change them and connect them to another unused pins at code.


## Quick start guide
1. Use PlatformIO (in VS Code) to open the project folder
2. Modify ESP32_LogicAnalyzer.h for make a fit to your board.
3. Build the project and flash with PlatformIO
4. Connect cfg.gpio_clk_in (default pin23 )and cfg.gpio_clk_out (default pin22).
5. Open PulseView with `pulseview -D -d ols:conn=/dev/ttyUSB0::serialcomm=921600/8n1`  ,or from gui, connect device and select Openbench Logic Sniffer & SUMP compatibles (ols)
6. Channels vs PINS are also available at setup() function. You can also change ports/baud from ESP32_LogicAnalyzer.h file. Please check it out before use.





### Original project
*[ESP32_LogicAnalyzer](://github.com/EUA/ESP32_LogicAnalyzer/blob/master/README.md)*
