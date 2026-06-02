# SPI通信

todo:あとarduino側の対応ピンを書く
## 特徴

一対一の場合四本の線でつなげる。
I2Cと違いデータを送りながらデータを受け取れる。

## 利点

I2Cより圧倒的に速い　(数Mpps~数十Mpps)
アドレス設定が不要
(通信したいデバイスの電圧をいったん落として識別)

## 短所

デバイスが増えるとピンも一本ずつ増えるので配線がややこしくなる
(SS/CSピン)

## 配線について

- SCK (Serial Clock)
タイミングを合わせるクロック信号(I2CのSCLに相当)

- COPI (Controller Out Peripheral In) (MOSI)
親機から子機へデータを送る線

- CIPO (Controller In Peripheral Out) (MISO)
子機から親機へデータを返す線

- CS(Chip Select) 
通信したい子機を指名するための線
いったん通信したいデバイスの電圧を落とすことで判別している

## arduino配線

- D10: SSLB0 - CS
- D11: COPIB - SI
- D12: CIPOB - SO
- D13: RSPCKB - SCK


### 補足

- SS(Slave select) →　CS
- SS → (PCS Peripheral Chip Select)
- MOSI (Master Out Slave In) 
- MISO (Master In Slave Out) 

