#　PowerShellコマンドで知ったもののメモ

## ファイル系

"()"の中の相当コマンドは参考程度

- ni(new item): ファイル生成(touch)
- gc :ファイルの中身を見るの(cat)

## arduino実行系(管理者として実行しなければならない)

pio(platformio)

- pio run -t upload : arduinoのプログラムをマイコンに読み込ませ実行させる
- pio device monitor : arduino IDE のSerial monitor 相当のもの

