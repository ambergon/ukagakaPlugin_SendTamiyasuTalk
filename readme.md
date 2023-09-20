# ukagakaPlugin_SendTamiyasuTalk
ukagakaPlugin_SendTamiyasuTalkは、VOICEROID2など合成音声ソフトで、外部連携APIを持たないものを使用するために作成されました。<br>
[民安Talk](https://publish-tool.blogspot.com/2012/09/voiceroid-live-gear2ch-niconama-comment.html)を使用してゴーストの発言を読み上げます。<br>

類似プラグインとしてCeVIO AI専用のプラグインを作っています。
CeVIOを所持している場合はそちらをお勧めします。




|項目|CeVIO AI Talker V2のメリット|SendTaymiyasuTalkのメリット|
|:--:|:--:|:--:|
|使用できる合成音声ソフト|CeVIO AIのみ|多くのものが使える。|
|1セットのゴーストに対して|3人まで声を充てることができる。|2人まで。|
|必要なウィンドウの数|SSP + ゴースト だけ| SSP + ゴースト + 民安Talk|
|新しいテキストが来たとき|現在のトークを切り上げて新しいテキストを読み上げる。|今のテキストを読み上げ終わった後に新しいテキストを読み上げる。|
|英文切り替え機能|送られたテキストが英文のみの場合CeVIO AI 弦巻マキ(英)に切り替えることができる|対応予定なし。|
|コスト|非常に高い。初回はトークスターター(本体+トークボイス)が必要になる。DLsiteでクーポンを使っても一万は超えるだろう。以降はトークボイスのみで済むので5-8千円くらい。質はとても良い。|VOICEVOXにも対応しているのでコストがかからない。素晴らしい。|
|リンク| [GitHub - ambergon/ukagakaPlugin_CeVIO-TalkerV2](https://github.com/ambergon/ukagakaPlugin_CeVIO-TalkerV2) |[Releases · ambergon/ukagakaPlugin_SendTamiyasuTalk · GitHub](https://github.com/ambergon/ukagakaPlugin_SendTamiyasuTalk/releases)|
||||


投げられたテキストをすべて順番に再生してしまうので、Ctrlキーなどを使って大量のテキストを読んだ場合、<br>
いつまでも音声の再生が続くデメリットが大きいです。<br>


## 動作環境
こちらでは下記の環境でテストしています。<br>
VOICEROID2以外でのテストはしておりません。<br>

- SSP 2.6.50
- 民安Talk 1.45.0
- VOICEROID2 2.1.1.0


## このプラグインの設定
config.ukaの中のOnPluginLoad.Config関数内を編集します。<br>
utf-8で編集してください。<br>


#### 民安トークのパスを設定する。
config.ukaを編集して絶対パスで指定してください。<br>
```{ .config.uka }
//例
TamiyasuTalkPATH = 'C:\Users\yourName\Documents\exe\tamiyasu_talk\vrx.exe'
```


#### テキストを特定のキャラクターで読み上げる。
￥1・￥0をそれぞれ置換する機能があります。<br>
同じくconfig.ukaの中を編集してください。<br>
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
ここではVOICEROID2のみを使用することを想定した設定をします。<br>
民安Talk -> 設定 -> 基本タブ -> ウィンドウタイトル/SAPI音源/CeVIO/CeVIO AI -> VOICEROID2<br>
VOICEROIDまたはSofTalkの場所 (適時書き換えてください) -> C:\Program Files (x86)\AHS\VOICEROID2\VoiceroidEditor.exe<br>


## 他
このプログラムを使用したことによるいかなる問題や損害に対して、私は責任を負いません。<br>


## 製作動機
VOICEROID+の弦巻マキや東北きりたんは、他の競合ツールがたくさん出てきた今でも魅力的な製品だと思うので連携させました。<br>


## Author
ambergon


