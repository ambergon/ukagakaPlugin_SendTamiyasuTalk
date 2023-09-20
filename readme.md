# ukagakaPlugin_SendTamiyasuTalk
ukagakaPlugin_SendTamiyasuTalkは、VOICEROID2など合成音声ソフトで、外部連携APIを持たないものを使用するために作成されました。
[民安Talk](https://publish-tool.blogspot.com/2012/09/voiceroid-live-gear2ch-niconama-comment.html)を使用してゴーストの発言を読み上げます。


## メリット
民安Talkは多くの合成音声ソフトに対応しているため、大体のものは使えます。
私はこのプラグインではVOICEROID2しか使用していませんが、きちんと設定すれば複数の音声合成ソフトをまたいで使うこともできるかもしれません。


## デメリット
専用設計ではなく、投げられたテキストをすべて順番に再生してしまうので、Ctrlキーなどを使って大量のテキストを読んだ場合、
いつまでも音声の再生が続くことになります。
[GitHub - ambergon/ukagakaPlugin_CeVIO-TalkerV2](https://github.com/ambergon/ukagakaPlugin_CeVIO-TalkerV2)の場合は再生を中断して新しいテキストに切り替え・処理しきれないテキストのカットなどを実装しているので、CeVIO AIだけを使用する場合はこちらをお勧めします。


## 動作環境
こちらでは下記の環境でテストしています。
VOICEROID2以外でのテストはしておりません。

- SSP 2.6.50
- 民安Talk 1.45.0
- VOICEROID2 2.1.1.0


## このプラグインの設定
config.ukaの中のOnPluginLoad.Config関数内を編集します。
utf-8で編集してください。


#### 民安トークのパスを設定する。
絶対パスで指定してください。
```{ .config.uka }
//例
TamiyasuTalkPATH = 'C:\Users\yourName\Documents\exe\tamiyasu_talk\vrx.exe'
```


#### テキストを特定のキャラクターで読み上げる。
￥1・￥0をそれぞれ置換する機能があります。
```{ .config.uka }
//Defaultの\0 -> A \1 -> BにそれぞれVOICEROIDで使用する接頭辞に置換できます。
//下記のようにすれば、VOICEROID2にインポートしたVOICEROID+のデフォルトを呼ぶことができます。
//デフォルトのボイスプリセットタグは > ですが、私は : を使用しています。
//VOICEROID2のツール -> オプション -> ボイスプリセットタグをご確認ください。
TalkerA = "東北きりたん(v1):"
TalkerB = "民安ともえ(v1):"
```


#### ゴーストごとに読み上げるキャラクターを変更する。
```
//ゴーストメニュー名.TalkerA and Bの変数が存在した場合、こちらが使用されます。
//この設定だと、ゴースト名[静かな団欒]で\0 \1 どちらも接頭辞に結月ゆかり:が挿入されます。
静かな団欒.TalkerA = "結月ゆかり:"
静かな団欒.TalkerB = "結月ゆかり:"
```


## 民安トークの設定
ここではVOICEROID2のみを使用することを想定した設定をします。
民安Talk -> 設定 -> 基本タブ -> ウィンドウタイトル/SAPI音源/CeVIO/CeVIO AI -> VOICEROID2
VOICEROIDまたはSofTalkの場所 (適時書き換えてください) -> C:\Program Files (x86)\AHS\VOICEROID2\VoiceroidEditor.exe


## 他
このプログラムを使用したことによるいかなる問題や損害に対して、私は責任を負いません。


## 製作動機
VOICEROID+の弦巻マキや東北きりたんは、他の競合ツールがたくさん出てきた今でも魅力的な製品だと思うので連携させました。


## Author
ambergon


