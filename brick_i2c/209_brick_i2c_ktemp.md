# #209 Ktemp I2C Brick

<center>![](/img/200_i2c/product/209.jpg)
<!--COLORME-->

## Overview
K型熱電対を接続できるBrickです。
I2Cでデータを取得できます。

## Connecting
I2Cコネクタへ接続します。

![](/img/100_analog/connect/209_new_with_arduino.jpg)

## MCP3421 Datasheet
| Document |
| -- |
| [MCP3421 Datasheet](http://ww1.microchip.com/downloads/en/DeviceDoc/22003e.pdf) |

## Register
| Slave Address |
| -- |
| 0x68 - 0x6F |

MCP3421のSlave Addressは0x68〜0x6Fのものが存在し、その値は工場出荷時に決まっており、後から変更することはできません。
FaBoBrickでは、0x68、または0x69の２種類を使用しています。

## Schematic
![](/img/200_i2c/schematic/209_ktemp.png)

## Library

![](/img/common/install_lib.png)

![](/img/200_i2c/docs/209_ktemp_docs_001.png)

  ライブラリ名：「FaBo 209 KTemp MCP3421」

- [Library GitHub](https://github.com/FaBoPlatform/FaBoKTemp-MCP3421-Library)
- [Library Document](http://fabo.io/doxygen/FaBoKTemp-MCP3421-Library/)

## Sample Code

I2Cコネクタに接続したKtemp BrickにK型熱電対を接続し、熱電対から取得した値を温度に変換してシリアルモニタに出力します。
```c
/**
 @file ktemperature.ino
 @brief This is an Example for the FaBo KTemp I2C Brick.

   http://fabo.io/208.html

   Released under APACHE LICENSE, VERSION 2.0

   http://www.apache.org/licenses/

 @author FaBo<info@fabo.io>
*/

#include <Wire.h>
#include <FaBoKTemp_MCP3421.h>

FaBoKTemp faboKTemp;

void setup() {
  Serial.begin(9600);
  Serial.println("RESET");
  Serial.println();

  faboKTemp.configuration();
}

void loop() {
  double temp = faboKTemp.readTemperature();
  Serial.print("Temp: ");
  Serial.println(temp);
  delay(1000);
}
```

## 構成Parts
- Microchip Technology MCP3421

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/209_ktemp
