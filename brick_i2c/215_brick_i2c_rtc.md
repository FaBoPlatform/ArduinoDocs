# #215 RTC I2C Brick

<center>![](/img/200_i2c/product/215.jpg)
<!--COLORME-->

## Overview
リアルタイムクロックを使用したBrickです。
I2Cでデータを取得できます。

## Connecting
I2Cコネクタへ接続します。

![](/img/100_analog/connect/215_new_with_arduino.jpg)

## PCF2129 Datasheet
| Document |
| -- |
| [PCF2129 Datasheet](http://cache.nxp.com/documents/data_sheet/PCF2129.pdf) |

## Register
| Slave Address |
| -- |
| 0x51 |

## Schematic
![](/img/200_i2c/schematic/215_rtc.png)

## Library

![](/img/common/install_lib.png)

![](/img/200_i2c/docs/216_rtc_docs_001.png)

  ライブラリ名：「FaBo 215 RTC PCF2129」

- [Library GitHub](https://github.com/FaBoPlatform/FaBoRTC-PCF2129-Library)
- [Library Document](http://fabo.io/doxygen/FaBoRTC-PCF2129-Library/)

## Sample Code


```c
/**
 @file rtc.ino
 @brief This is an Example for the FaBo RTC I2C Brick.

   http://fabo.io/215.html

   Released under APACHE LICENSE, VERSION 2.0

   http://www.apache.org/licenses/

 @author FaBo<info@fabo.io>
*/

#include <Wire.h>
#include <FaBoRTC_PCF2129.h>

FaBoRTC_PCF2129 faboRTC;

void setup() {
  Serial.begin(9600);
  Serial.println();
  Serial.println("RESET");

  // デバイス初期化
  Serial.println("Checking I2C device...");
  if (faboRTC.searchDevice()) {
    Serial.println("configuring FaBo RTC I2C Brick");
    faboRTC.configure();
  } else {
    Serial.println("device not found");
    while(1);
  }

  // 日付時刻の設定
  Serial.println("set date/time");
  faboRTC.setDate(2016,4,1,12,1,50);

}

void loop() {
  // 日付時刻の取得
  DateTime now = faboRTC.now();

  // 日付時刻の表示
  Serial.print("Time: ");
  Serial.print(now.year());
  Serial.print("/");
  Serial.print(now.month());
  Serial.print("/");
  Serial.print(now.day());
  Serial.print(" ");
  Serial.print(now.hour());
  Serial.print(":");
  Serial.print(now.minute());
  Serial.print(":");
  Serial.print(now.second());
  Serial.println();

  delay(1000);
}
```


## Parts
- NXP PCF2129

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/215_rtc
