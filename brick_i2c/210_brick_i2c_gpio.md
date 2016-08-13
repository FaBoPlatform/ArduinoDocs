# #210 GPIO I2C Brick

<center>![](/img/200_i2c/product/210.jpg)
<!--COLORME-->

## Overview
汎用I/O拡張チップを使用したBrickです。

I2Cで8個のLEDを制御できます。

## Connecting
I2Cコネクタへ接続します。

![](/img/200_i2c/connect/210_gpio_connect.jpg)

## PCAL6408 Datasheet
| Document |
| -- |
| [PCAL6408 Datasheet](http://www.nxp.com/documents/data_sheet/PCAL6408A.pdf) |

## Register
| Slave Address |
| -- |
| 0x20 |

## Schematic
![](/img/200_i2c/schematic/210_gpio.png)

## Library

![](/img/common/install_lib.png)

![](/img/200_i2c/docs/210_gpio_docs_001.png)

  ライブラリ名：「FaBo 210 GPIO PCAL6408A」

- [Library GitHub](https://github.com/FaBoPlatform/FaBoGPIO-PCAL6408-Library)
- [Library Document](http://fabo.io/doxygen/FaBoGPIO-PCAL6408-Library/)

## Sample Code
I2CコネクタにGPIO Brickを接続し、GPIO Brickについている8つのLEDを左上から右下に向かって順番に点灯させます。

```c
/**
 @file LED.ino
 @brief This is an Example for the FaBo GPIO I2C Brick.

   http://fabo.io/210.html

   Released under APACHE LICENSE, VERSION 2.0

   http://www.apache.org/licenses/

 @author FaBo<info@fabo.io>
*/

#include <FaBoGPIO_PCAL6408.h>

FaBoGPIO faboGPIO;
int i = 0;

void setup() {
  Serial.begin(9600);
  Serial.println("RESET");
  Serial.println();

  faboGPIO.configuration();
}

void loop() {
  Serial.println(i);
  if(i == 0){
    faboGPIO.setDigital(PCAL6408_IO0, HIGH);
  } else if (i == 1){
    faboGPIO.setDigital(PCAL6408_IO1, HIGH);
  } else if (i == 2){
    faboGPIO.setDigital(PCAL6408_IO2, HIGH);
  } else if (i == 3){
    faboGPIO.setDigital(PCAL6408_IO3, HIGH);
  } else if (i == 4){
    faboGPIO.setDigital(PCAL6408_IO4, HIGH);
  } else if (i == 5){
    faboGPIO.setDigital(PCAL6408_IO5, HIGH);
  } else if (i == 6){
    faboGPIO.setDigital(PCAL6408_IO6, HIGH);
  } else if (i == 7){
    faboGPIO.setDigital(PCAL6408_IO7, HIGH);
  } 
  i++;

  if(i > 8){
    i = 0;
    faboGPIO.setAllClear();
  }
  delay(1000);
}
```

## Parts
- NXP PCAL6408

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/210_gpio
