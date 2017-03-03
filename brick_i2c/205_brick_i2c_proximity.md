# #205 Proximity I2C Brick

<center>![](/img/200_i2c/product/205.jpg)
<!--COLORME-->

## Overview
近接センサーを使ったBrickです。

I2Cでデータを取得できます。

## Connecting
I2Cコネクタへ接続します。

![](/img/200_i2c/connect/205_new_with_arduino.jpg)


## VCNL4010 Datasheet
| Document |
|:--|
| [VCNL4010 Datasheet](https://www.adafruit.com/images/product-files/466/vcnl4010.pdf) |

## Register
| I2C Slave Address |
|:-- |
| 0x13 |

## Schematic
![](/img/200_i2c/schematic/205_proximity.png)

## Library

![](/img/common/install_lib.png)

![](/img/200_i2c/docs/205_proximity_docs_001.png)

  ライブラリ名：「FaBo 205 Proximity VCNL4010」

- [Library GitHub](https://github.com/FaBoPlatform/FaBoProximity-VCNL4010-Library)
- [Library Document](http://fabo.io/doxygen/FaBoProximity-VCNL4010-Library/)

## Sample Code
上記のArduino Libraryをインストールし、スケッチの例から、「FaBo 205 Proximity VCNL4010」→「proximity」を選択してください。

```c
/**
 @file proximity.ino
 @brief This is an Example for the FaBo Proximity I2C Brick.

   http://fabo.io/205.html

   Released under APACHE LICENSE, VERSION 2.0

   http://www.apache.org/licenses/

 @author FaBo<info@fabo.io>
*/

#include <Wire.h>
#include <FaBoProximity_VCNL4010.h>

FaBoProximity faboProximity;

void setup() {
  Serial.begin(9600);
  Serial.println("RESET");
  Serial.println();

  faboProximity.begin();
}

void loop() {
  // proximityデータの出力
  if(faboProximity.checkProxReady()){
    Serial.print("Prox:");
    Serial.println(faboProximity.readProx());
  }

  // ambientデータの出力
  if(faboProximity.checkAmbiReady()){
    Serial.print("Ambi:");
    Serial.println(faboProximity.readAmbi());
  }

  delay(1000);
}
```

## 構成Parts
- Vishay VCNL4010

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/205_proximity
