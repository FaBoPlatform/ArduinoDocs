# #119 Reflector Brick

![](../img/100_analog/product/119.jpg)
<!--COLORME-->

## Overview
Reflectorを使用したBrickです。

I/OピンよりReflectorのON/OFFをデジタル値で取得できます。

## 接続

![](../img/100_analog/connect/119_new_with_arduino.jpg)

## ソースコード

A0コネクタにReflectorを接続し、D2にLEDを接続する。

```c
#define reflectorPin A0 // Reflectorピン
#define ledPin 2 // LEDピン

void setup() {
  // Reflectorピンを入力用に設定
  pinMode(hallhPin, INPUT);
  // LEDピンを出力用に設定
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // Hallの値を取得
  int reflectorFlag = digitalRead(reflectorPin);

  // スイッチがONならLEDをつける
  if (reflectorFlag == HIGH) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }
}
```

## 構成Parts
- Reflector

## GitHub

https://github.com/FaBoPlatform/FaBo/tree/master/119_reflector
