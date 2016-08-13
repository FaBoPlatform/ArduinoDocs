# #214 OLED I2C Brick

<center>![](/img/200_i2c/product/214.jpg)
<!--COLORME-->

## Overview
有機ELモジュールを使用したBrickです。

I2Cで表示データを制御できます。

## Connecting
I2Cコネクタへ接続します。


## ER-OLED0.96 Datasheet
| Document |
| -- |
| [ER-OLED0.96 Datasheet](http://www.buydisplay.com/download/manual/ER-OLED0.96_Series_Datasheet.pdf) |

## Register
| Slave Address |
| -- |
| 0x3C |

## Schematic
![](/img/200_i2c/schematic/214_oled.png)

## Library


![](/img/common/install_lib.png)

![](/img/200_i2c/docs/214_oled_docs_001.png)

  ライブラリ名：「FaBo 214 OLED EROLED096」

- [Library GitHub](https://github.com/FaBoPlatform/FaBoOLED-EROLED096-Library)
- [Library Document](http://fabo.io/doxygen/FaBoOLED-EROLED096-Library)

### for RapberryPI
- pipからインストール
```
pip install FaBoOLED_EROLED096
```
- [Library GitHub](https://github.com/FaBoPlatform/FaBoOLED-EROLED096-Python)
- [Library Document](http://fabo.io/doxygen/FaBoOLED-EROLED096-Python/)

## Sample Code
上記のArduino Libraryをインストールし、スケッチの例、「FaBo 214 OLED EROLED096」からお選びください。

```c
/**
 @file oled.ino
 @brief This is an Example for the FaBo OLED I2C Brick.

   http://fabo.io/214.html

   Released under APACHE LICENSE, VERSION 2.0

   http://www.apache.org/licenses/

 @author FaBo<info@fabo.io>
*/

#include <Wire.h>
#include <FaBoOLED_EROLED096.h>

FaBoOLED_EROLED096 faboOled;

void setup() {
  Serial.begin(9600);
  Serial.println("RESET");
  Serial.println();

  faboOled.begin();

  faboOled.showBitmap();
  delay(1000);
  faboOled.clear();
  faboOled.print("Hello! FaBo");
}

void loop() {
  faboOled.setCursor(0, 1);
  faboOled.print(millis() / 1000);
}
```

## Parts
- 128x96 0.96OLED Module

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/214_oled
