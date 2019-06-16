# Runner3680 Build Guide
**一度すべて読んでから組み立てることをお勧めします。**  

## 0 準備
組みたいレイアウトによってPCBを切断します。  
<img width="700" alt="PCB" src="https://github.com/omkbd/Runner3680/blob/master/Picture/PCB.jpg">  
<img width="700" alt="PCBcut" src="https://github.com/omkbd/Runner3680/blob/master/Picture/PCB_cut.jpg">  
手で力をかければ割れます。  

## 1 Backlight RGB LEDの取付け[Option]

<img width="700" alt="RGB_LED" src="https://github.com/omkbd/Runner3680/blob/master/Picture/RGB_LED.jpg">  

## 2 ダイオードの取付け
ダイオードの黒いほうが四角いフットプリントに合うように配置します。  
<img width="400" alt="diode" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Diode.jpg">  

## 3 TRRSジャックの取付け  
内側上部の白い四角い枠のシルクに沿って取り付けます。  

## 4 リセットスイッチの取付け  
取り付けます。  

## 5 Pro Micro用ピンヘッダの取付け
白い四角い枠がついているほうにピンヘッダを取り付けます。  
**この時点でPro Microを取り付けてはいけません。**  
**※コンスルー（スプリングピンヘッダ）を使う場合はこの工程は不要です。**  

## 6 キースイッチの取付け
**スイッチを取り付ける前に部品の取付けやはんだ付けができているか確認します。**  
（TRRSジャックとリセットスイッチは特に注意が必要です。）  
アクリルプレートにキースイッチをはめて取り付けします。  
<img width="700" alt="switch" src="https://github.com/omkbd/Runner3680/blob/master/Picture/switch.jpg">  
※スプリングピンヘッダを使用する場合は7の工程を先に行い、動作確認をすると失敗する可能性が減ります。

## 7 Pro Microの取付け
**作業前にPro MicroをUSBでPCと繋げて動作を確認しておきましょう。**  
取り付ける前にはんだ忘れがないか確認します。  
両手ともProMicroを裏にして取り付けられるようになります。  
取り付けたときにPro Microの浮きがないか確認し、浮きがあればPro Micro下のスイッチの足を少しカットします。  

※コンスルーを使う場合はPro Micro側のみをはんだ付けします。  
コンスルーの使い方は下記ページをご参照ください。  
https://github.com/MakotoKurauchi/helix/blob/master/Doc/buildguide_jp.md#pro-micro  

## 8 ケースの組み立て
5mmのねじと6mmのスペーサーを取り付けます。  
<img width="700" alt="spacer" src="https://github.com/omkbd/Runner3680/blob/master/Picture/pacer.jpg">  
5mmのねじと8mmのねじを取り付けます。  
<img width="700" alt="case" src="https://github.com/omkbd/Runner3680/blob/master/Picture/case.jpg">  
ゴム足を取り付けます。  
<img width="700" alt="gom" src="https://github.com/omkbd/Runner3680/blob/master/Picture/gom.jpg">  

## 9 Firmwareの書き込み
以下を参考に書き込んでください。または、QMKで検索すると書き込み方がすぐに出てくるはずです。  
https://docs.qmk.fm/#/getting_started_build_tools  
Runner3680のFirmwareは以下にあります。  
https://github.com/qmk/qmk_firmware/tree/master/keyboards/runner3680

右手側をマスターにした場合はqmkのkeymap内のconfig.hファイルで
`MASTER_RIGHT`を指定してファームウェアをビルドする必要があります。
https://docs.qmk.fm/#/config_options?id=defines-for-handedness

Backlightを点けるにはkeymap内のrules.mkに以下を追記します。AUDIOについてはサポート外です。  
`RGBLIGHT_ENABLE = yes  `

初めての方は以下のツールを使うことをお勧めします。（これらを使用する場合LED系は点灯しません。）  
https://config.qmk.fm/#/ergodash/rev2/LAYOUT  
https://github.com/qmk/qmk_toolbox
