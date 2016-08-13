# #211 7Segment LED I2C Brick

<center>![](/img/200_i2c/product/211.jpg)
<!--COLORME-->

## Overview
７セグメントLEDを使ったBrickです。

I2Cで表示パターンを制御できます。

## Connecting
I2Cコネクタへ接続します。

<center>![](/img/200_i2c/connect/211_7seg_connect.jpg)

## TLC59208F Datasheet
| Document |
| -- |
| [TLC59208F Datasheet](http://www.ti.com/jp/lit/gpn/tlc59208f) |

## Register
| A0 | A1 | A2 | Slave Address |
| -- | -- | -- | -- |
| LOW | LOW | LOW | 0x20 |

FaBo Brickでは、初期値に0x20が設定されています。Brick裏面のソルダージャンパーで設定を変更できます。

## Schematic
![](/img/200_i2c/schematic/211_7seg.png)

## Library


![](/img/common/install_lib.png)

![](/img/200_i2c/docs/211_7segment_docs_002.png)

  ライブラリ名：「FaBo 211 7Segment LED TLC59208F」

- [Library GitHub](https://github.com/FaBoPlatform/FaBo7Seg-TLC59208-Library)
- [Library Document](http://fabo.io/doxygen/FaBo7Seg-TLC59208-Library/)

## Sample Code
PWM出力値は、"0x02"でほぼ視認できる明るさで点灯されます。あまり高い数値にすると、点灯しなくなるおそれがあります。

### Sample Code1
I2Cコネクタに7Segment LED Brickを接続し、「0〜9を順番に表示させます。
```c
/*************************************************** 
 This is an Example for the FaBo 7Seg I2C Brick.

  http://fabo.io/211.html

 author:FaBo<info@fabo.io>
 maintainer:Hideki Yamauchi<yamauchi@fabo.io>

 Released under APACHE LICENSE, VERSION 2.0
  http://www.apache.org/licenses/
 ****************************************************/

#include <Wire.h>
#include <FaBo7Seg_TLC59208.h>

FaBo7Seg_TLC59208 fabo_7seg;

void setup() {
  Serial.begin(9600);
  Serial.println("RESET");
  Serial.println();

  Serial.println("configuring device.");
  if (fabo_7seg.configure()) {
    Serial.println("configured FaBo 7Seg Brick");
  } else {
    Serial.println("device error");
    while(1);
  }
}

void loop() {
  for (int i = 0; i<10; i++) {
    fabo_7seg.showNumber(i); // show a number
    delay(1000);
  }
}
```

### Sample Code2

それぞれの部位を光らせます。

```c

/*************************************************** 
 This is an Example for the FaBo 7Seg I2C Brick.

  http://fabo.io/211.html

 author:FaBo<info@fabo.io>
 maintainer:Hideki Yamauchi<yamauchi@fabo.io>

 Released under APACHE LICENSE, VERSION 2.0
  http://www.apache.org/licenses/
 ****************************************************/

#include <Wire.h>
#include <FaBo7Seg_TLC59208.h>

FaBo7Seg_TLC59208 fabo_7seg;

void setup() {
  Serial.begin(9600);
  Serial.println("RESET");
  Serial.println();

  Serial.println("configuring device.");
  if (fabo_7seg.configure()) {
    Serial.println("configured FaBo 7Seg Brick");
  } else {
    Serial.println("device error");
    while(1);
  }
}

void loop() {
  fabo_7seg.showPattern(TLC59208_LED_PIN_A|TLC59208_LED_PIN_G|TLC59208_LED_PIN_D);
  delay(1000);

  for (int i = 0; i<10; i++) {
    fabo_7seg.showPattern(TLC59208_LED_PWM5);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM4);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM2);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM1);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM0);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM6);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM5);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM4);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM2);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM1);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM0);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM6);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_PWM5);
    delay(50);
    fabo_7seg.showPattern(TLC59208_LED_OFF);
    delay(50);

    fabo_7seg.showNumber(i);
    delay(1000);
    fabo_7seg.showDot();
    delay(1000);
    fabo_7seg.showPattern(TLC59208_LED_OFF);
    delay(100);
  }
}
```

## Parts
- 7セグメントLED
- Texas Instruments TLC59208F

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/211_7seg
