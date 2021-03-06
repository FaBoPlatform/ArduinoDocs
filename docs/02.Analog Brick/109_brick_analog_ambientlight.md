# #109 Light Brick

![](../img/100_analog/product/109.jpg)
<!--COLORME-->

## Overview
CDSセルを使用した光センサーBrickです。

周囲の明るさの変化をアナログ値として取得することができます。

## 接続
アナログコネクタ(A0〜A5)のいずれかに接続します。

![](../img/100_analog/connect/109_new_with_arduino.jpg)

## Parts Specification
| Document |
|:--|
| [MI527](http://akizukidenshi.com/catalog/g/gI-00110/) |

## 回路図
![](../img/100_analog/schematic/109_light.png)

## ソースコード
A0コネクタにLight Brickを接続して、明るさに応じたアナログ値をシリアルモニタへ出力します。

```c
//
// FaBo Brick Sample
//
// #109 Light Brick
//

#define lightPin A0

int lightValue = 0;

void setup() {
  pinMode(lightPin,INPUT);
  Serial.begin(9600);
}

void loop() {
  lightValue = analogRead(lightPin);
  Serial.println(lightValue);
  delay(100);
}
```

#### シリアルプロッタ

AndroidIDEではシリアルプロッタでも値を確認することが可能です。

ArduinoIDEのメニューより[ツール]->[シリアルプロッタ]を選択することで起動できます。

![](../img/100_analog/docs/109_light_docs_001.png)


## 構成Parts
- CDSセル(5mm)

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/109_light
