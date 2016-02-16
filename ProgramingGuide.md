# Programing guide #

Software module "DS18B20" designed for reading 1-wire temperature sensors DS18B20 by serial port of Crestron controller. How to connect 1-wire bus to serial port please see [Connection guide](https://code.google.com/p/1wire-for-crestron/wiki/ConnectionGuide) . [You can download example program.](https://googledrive.com/host/0B8F7wnwnAleGWmhzZWpKS0FMOXc/)

<a href='http://www.youtube.com/watch?feature=player_embedded&v=ocAxn-JHd38' target='_blank'><img src='http://img.youtube.com/vi/ocAxn-JHd38/0.jpg' width='425' height=344 /></a>

![https://googledrive.com/host/0B8F7wnwnAleGWmhzZWpKS0FMOXc/module.png](https://googledrive.com/host/0B8F7wnwnAleGWmhzZWpKS0FMOXc/module.png)

# Inputs #

|scan\_addr|On rising edge receives sensor address and sends it into a serial join scanned\_addr. Only one sensor must be connected in this procedure! Polling must be switched off in this time.|
|:---------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| polling  |When its value is high, module polling of the values of all sensors.                                                                                                                 |
|rx$       |It is a "rx$" serial join of the serial port.                                                                                                                                        |
|addr$**[n**]|Address of the sensor in 1-wire bus.                                                                                                                                                 |

# Outputs #

|val\_ok**[n**]|If it value is high, then connection with corresponding sensors is good and its value is correct.|
|:-------------|:------------------------------------------------------------------------------------------------|
|ComSpec$      |This serial join must be connected to Device Extender "Packet Transmission" of serial ports slot.|
|scanned\_addr$|String with sensor address, received after pressing digital join "scan\_addr".                   |
|tx$           |It is a "tx$" serial join of the serial port.                                                    |
|val**[n**]    |Temperature value of corresponding sensor. Value format XX.X.                                    |

# Parameters #

|port|Select the port to which the signals  rx$ and tx$ are connected.|
|:---|:---------------------------------------------------------------|
|license|License key. Without license key module can work in demonstration mode during 1 hour. License key is associated with an address of first sensor. [Read more about licensing ](https://code.google.com/p/1wire-for-crestron/wiki/GetLicense) |

# Commissioning #

Firstly, you must connect each sensor separately and, pressing the "scan\_addr" digital join, will get its address.Then you must paste this addresses in "Serial Send" symbol, connected to corresponding "addr$[n](n.md)" serial join in module. Then after compiling and downloading you can switch on digital join "polling" and get temperature values from sensor.