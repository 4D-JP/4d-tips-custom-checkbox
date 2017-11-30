## チェックボックスのカスタマイズ

フォームオブジェクトの[チェックボックス](http://doc.4d.com/4Dv16/4D/16.1/Check-Boxes.300-3373477.ja.html)は，プラットフォームの標準的なデザインのもので表示されます。macOSでは，オブジェクトの高さ（``15``, ``16``, ``17``以上）に合わせたサイズのものが表示されます。

* 図1. 標準チェックボックス（macOS）

<img width="180" alt="2017-11-30 15 31 28" src="https://user-images.githubusercontent.com/10509075/33419365-611668a0-d5ed-11e7-9a95-699fbe253968.png">

### 3Dチェックボックス

3Dチェックボックスは，[3Dボタン](http://doc.4d.com/4Dv16/4D/16.1/3D-Buttons-3D-Check-Boxes-and-3D-Radio-Buttons.300-3373467.ja.html)，つまりプラットフォームの標準的なボタンの代わりにピクチャを使用し，自由にカスタマイズできる「擬似的な」ボタンで表現されたチェックボックスです。このタイプのボタンでは，状態数に応じた「コマ割り」ピクチャをアイコンに指定できます。

アイコン画像は「アクティブ・クリック・ロールオーバー・無効」の4つまで設定することができます。状態の数を3以下に減らすのであれば，アイコン画像のコマ数も少なくする必要があります。その場合，アイコンが設定されていない状態のときには，ボタンのアイコンが表示されません。

3Dチェックボックスの場合，ロールオーバー画像はデータソースの値に対応していなければならないので，クリックイベントでアイコン画像を切り替えることが必要になります。具体的には，下記のような画像を用意することになります。

* 図2. 3Dチェックボックス - 値が``0``のとき

<img alt="0" width="24" src="https://user-images.githubusercontent.com/10509075/33419452-cb5b33a8-d5ed-11e7-9c62-68906687cdec.png" />

* 図3. 3Dチェックボックス - 値が``1``のとき

<img alt="1" width="24" src="https://user-images.githubusercontent.com/10509075/33419472-e497c674-d5ed-11e7-8129-3e47b37e6b72.png" />

オブジェクトメソッドは下記のようになります。

```
$name:=OBJECT Get name(Object current)

If (Form event=On Clicked)
	
	If (Self->=1)
		OBJECT SET FORMAT(*;$name;";#checkbox.1.svg")
	Else 
		OBJECT SET FORMAT(*;$name;";#checkbox.0.svg")
	End if 
	
End if 
```

* 図4. 3Dチェックボックス 

<img width="405" alt="2017-11-30 16 48 55" src="https://user-images.githubusercontent.com/10509075/33419575-624ea8d0-d5ee-11e7-984e-562e5e478293.png">
