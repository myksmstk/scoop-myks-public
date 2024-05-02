# scoop-myks-public

[Scoop](https://scoop.sh/) [bucket](https://github.com/lukesampson/scoop/wiki/Buckets) useful for me.

## Apps

* [CD Manipulator](http://www.storeroom.info/cdm/) / [cdmanipulator](bucket/cdmanipulator.json)  
	シンプルなCDバックアップ、ライティングツール。

* [Hash My Files](https://www.nirsoft.net/utils/hash_my_files.html) / [hashmyfiles](bucket/hashmyfiles.json)  
	ファイルの各種ハッシュ値を計算するツール。  
	[scoop-nirsoft の bucket](https://github.com/MCOfficer/scoop-nirsoft) にあるマニフェストが設定値の persist 化に対応できていなかったので修正版を作成。

* [まうじゃん](http://www.amy.hi-ho.ne.jp/ishihata/maujong/) / [maujong](bucket/maujong.json)  
	懐ゲー（死語）、簡易麻雀ゲーム「まうじゃん」。

* [Mery](https://www.haijin-boys.com/software/mery) / [mery](bucket/mery.json)
	シンプルなテキストエディター「Mery」ベータ版。

* [OmniSSHAgent](https://github.com/masahide/OmniSSHAgent) / [omnisshagent](bucket/omnisshagent.json)  
	Windows 用 代替 SSH Agent。

* [D2D/DW Putty](https://ice.hotmint.com/putty/d2ddw.html) / [putty-d2ddw](bucket/putty-d2ddw.json)
	テキストレンダリングエンジンを Direct2D/DirectWrite へ変更し、より高品質なテキストレンダリングが可能な putty。

* [PuTTYrv (PuTTY-ranvis)](https://www.ranvis.com/putty) / [putty-ranvis](bucket/putty-ranvis.json)  
	ini ファイルパッチが適用されている putty のカスタムビルド。  

* [サクラエディタ](https://sakura-editor.github.io/) / [sakura-editor](bucket/sakura-editor.json)  
	設定値の persist 化に対応した。設定値は persistentprofile という名前のプロファイルを使って保存する。

* [Wake up On Lan Tool](https://www.vector.co.jp/soft/dl/win95/util/se241927.html) / [wol](bucket/wol.json)  
	Wake up On Lan マジックパケット送信ツール。

* [pdf_as](http://uchijyu.s601.xrea.com/wordpress/pdf_as/) / [pdf_as](bucket/pdf_as.json)  
	PDFファイルの**セキュリティ設定**、結合、追加、分割、抽出、削除、回転、プロパティ設定、ヘッダー・フッター設定、しおり追加ができるツール。

---
## その他メモ

### persist ファイルの掟

* persist に永続化したいファイル／フォルダー名を配列で列挙する
* 列挙した対象が persist/アプリ名のフォルダーに無く $dir 以下にあれば、persist/アプリ名フォルダーに move される
* 列挙した対象が persist/アプリ名のフォルダーに無く $dir 以下にも無ければ、persist/アプリ名フォルダーにフォルダーとして作成される
* $dir 以下に列挙した対象へのリンクが作成される
* アーカイブ内に存在しないファイルを persist 化したい場合、pre_install で空ファイルなりを用意しておく必要がある
* $dir 以下に空ファイルを用意するか、$persist_dir を先に掘っておくかどちらでも良い

```
    "persist": [
        "App.ini"
    ],
    "pre_install": [
        "$src = \"$dir\\App.ini\"",
        "if (!(Test-Path \"$src\")) {",
        "  New-Item -ItemType file \"$src\" | Out-Null",
        "}"
    ]

```

### Google Drive の直リンク URL の掟

* ファイルの共有リンクを生成して id を抜き出す  
	例）https://drive.google.com/file/d/1234567890ABCDEFGHIJKLMNOPQRSTUVW/view?usp=sharing  
	→ id = 1234567890ABCDEFGHIJKLMNOPQRSTUVW
* 直リンク URL と id を組み合わせる  
	例）https://drive.google.com/uc?export=download&id=1234567890ABCDEFGHIJKLMNOPQRSTUVW  

ただし、ある程度大きなファイルはウィルスチェックができない旨の警告表示が挟まり直リンクにならない。

---
* [MD の参考](https://guides.github.com/features/mastering-markdown/)

