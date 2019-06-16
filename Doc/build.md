# Runner3680 Build Guide
**一度すべて読んでから組み立てることをお勧めします。**  
**アクリルプレートを使用する場合はChocスイッチは使用できません。**  

## 0 準備
組みたいレイアウトによってPCBを切断します。  
<img width="700" alt="PCB" src="https://github.com/omkbd/Runner3680/blob/master/Picture/PCB.jpg">  
左右に分割します。手で力をかければ割れます。  
<img width="700" alt="PCBcut" src="https://github.com/omkbd/Runner3680/blob/master/Picture/PCB_cut.jpg">  
不要な行と列を切り離します。分割したい部分を雑誌等で押さえて上から力をかけて割ります。  
<img width="700" alt="PCBcut" src="https://github.com/omkbd/Runner3680/blob/master/Picture/PCB_cut2.jpg">  
断面はニッパー等で整えます。  

## 1 Backlight RGB LEDの取付け[Option]
バックライト用のチップLEDはPCBの下面側から実装します。向きに注意して穴に入れてください。裏から見て、一番大きいパッドとシルクの○が同じ位置になります。  
温調半田ごてを使い、約220℃ではんだ付けします。温度が高いとLEDが壊れますので注意してください。  
<img width="300" alt="RGB" src="https://github.com/omkbd/Runner3680/blob/master/Picture/RGB.png">  
<img width="700" alt="RGB_LED" src="https://github.com/omkbd/Runner3680/blob/master/Picture/RGB_LED.jpg">  

6列、7列にした場合は下図の位置2ヶ所をはんだでジャンパします。  
<img width="700" alt="Jumper" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Jumper.png">  

## 2 ダイオードの取付け
ダイオードの黒いほうが四角いフットプリントに合うように配置します。  
<img width="300" alt="diode" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Diode2.png">  
<img width="700" alt="diode" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Diode.jpg">  

## 3 リセットスイッチとTRRSジャックの取付け  
白い四角い枠のシルクに沿って裏側に取り付けます。  
<img width="700" alt="S_T" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Switch_TRRS.JPG">  

## 4 Pro Micro用ピンヘッダの取付け  
**※コンスルー（スプリングピンヘッダ）を使う場合はこの工程は不要です。**  
白い四角い枠のシルクに沿って裏側にピンヘッダを取り付けます。  
一番上のピンは使いません。（BLE Micro Pro用）  
**この時点でPro Microを取り付けてはいけません。**  

## 5 キースイッチの取付け
**スイッチを取り付ける前に部品の取付けやはんだ付けができているか確認します。**  
（TRRSジャックとリセットスイッチは特に注意が必要です。）  
アクリルプレートにキースイッチをはめて取り付けします。  
<img width="700" alt="switch" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Switch.jpg">  
※スプリングピンヘッダを使用する場合は6と8の工程を先に行い、動作確認をすると失敗する可能性が減ります。

## 6 Pro Microの取付け
**作業前にPro MicroをUSBでPCと繋げて動作を確認しておきましょう。**  
取り付ける前にはんだ忘れがないか確認します。  
両手ともProMicroを裏にして取り付けられるようになります。  
取り付けたときにPro Microの浮きがないか確認し、浮きがあればPro Micro下のスイッチの足を少しカットします。  

※コンスルーを使う場合はPro Micro側のみをはんだ付けします。  
コンスルーの使い方は下記ページをご参照ください。  
https://github.com/MakotoKurauchi/helix/blob/master/Doc/buildguide_jp.md#pro-micro  

## 7 ケースの組み立て
図の赤丸の位置に5mmのねじと6mmのスペーサーを取り付けます。  外側の穴はオプションです。
<img width="700" alt="spacer" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Spacer.png">  
図の赤丸の位置に5mmのねじ、青丸の位置に8mmのねじを取り付けます。  
青丸の位置は図の上下のパーツを組み合わせます。  
<img width="700" alt="case" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Case.png">  
緑丸の位置にゴム足を取り付けます。  
<img width="700" alt="gom" src="https://github.com/omkbd/Runner3680/blob/master/Picture/Gom.png">  

## 8 Firmwareの書き込み
以下を参考に書き込んでください。または、QMKで検索すると書き込み方がすぐに出てくるはずです。  
https://docs.qmk.fm/#/getting_started_build_tools  
Runner3680のFirmwareは以下にあります。  
https://github.com/qmk/qmk_firmware/tree/master/keyboards/runner3680  
レイアウトによってファームウェアが異なります。  
例えば5行6列の場合は5x6を使用します。  
左右で異なるレイアウトの場合は大きいほうのファームウェアを使用します。  
デフォルトのキーマップは使い物にならないので、ご自分で調整してください。  

右手側をマスターにした場合はqmkのkeymap内のconfig.hファイルで
`MASTER_RIGHT`を指定してファームウェアをビルドする必要があります。
https://docs.qmk.fm/#/config_options?id=defines-for-handedness

Backlightを点けるにはkeymap内のrules.mkに以下を追記します。  
`RGBLIGHT_ENABLE = yes  `

初めての方は以下のツールを使うことをお勧めします。（これらを使用する場合LED系は点灯しません。）  
https://config.qmk.fm/#/runner3680/LAYOUT  
https://github.com/qmk/qmk_toolbox
