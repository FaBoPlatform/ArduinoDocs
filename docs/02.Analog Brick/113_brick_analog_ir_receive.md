# #113 IR Receiver Brick

![](../img/100_analog/product/113.jpg)
<!--COLORME-->

## Overview
フォトトランジスタを使った赤外線受信Brickです。

I/Oピンから赤外線受信のON/OFFを取得することができます。

## 接続

アナログコネクタ(A0〜A5)、またはデジタルコネクタ(2〜13)のいずれかに接続します。
![](../img/100_analog/connect/113_new_with_arduino.jpg)

## Parts Specification
| Document |
|:--|
| [L-51ROPT1D1](http://akizukidenshi.com/catalog/g/gI-04211/) |
| [2SC1815L-Y](http://akizukidenshi.com/catalog/g/gI-06475/) |

## 回路図
![](../img/100_analog/schematic/113_ir_receive.png)

## ソースコード

A0コネクタに赤外線受信Brick、A1コネクタにLED Brickを接続し、赤外線を受信したらLEDを発光させます。


```c
#define receivePin A0
#define irledPin 2

void setup() {
  pinMode(receivePin, INPUT);
  pinMode(irledPin, OUTPUT);
  digitalWrite(irledPin, HIGH);

  Serial.print("SETUP");
}

void loop() {
  int irState = digitalRead(receivePin);

  if (irState == HIGH) {
    Serial.println("Received");
  }
}
```

## 構成Parts
- 赤外線フォトトランジスタ

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/113_ir_receive
