# scoop-myks-public

[Scoop](https://scoop.sh/) [bucket](https://github.com/lukesampson/scoop/wiki/Buckets) useful for me.

## Apps

* [CD Manipulator](http://www.storeroom.info/cdm/) / [cdmanipulator](bucket/cdmanipulator.json)

* [Hash My Files](https://www.nirsoft.net/utils/hash_my_files.html) / [hashmyfiles](bucket/hashmyfiles.json)  
	本家の bucket にあるマニフェストが設定値の persist 化に対応できていなかったので修正版を作成。

* [Lame Ivy Frontend Encoder](https://www.vector.co.jp/soft/win95/art/se233905.html) / [life](bucket/life.json)  
	**※注）vector などの配布元は若干古いバージョン（2.97）のため、より新しい 2.98alpha4 をインストールする。**  
	**（Google Drive に保存したファイルからインストールする）**  
	ついでに 2.97 のヘルプファイルを同梱した。

* [まうじゃん](http://www.amy.hi-ho.ne.jp/ishihata/maujong/) / [maujong](bucket/maujong.json)  
	簡易麻雀ゲーム「まうじゃん」。

* [PuTTY-ranvis](https://www.ranvis.com/putty) / [putty-ranvis](bucket/putty-ranvis.json)  
	ini ファイルパッチが適用されている putty。  
	**※注）本家ダウンロード元は User-Agent を確認するらしく scoop ではダウンロードできない。**  
	**（Google Drive に保存したファイルからインストールする）**

* [サクラエディタ](https://sakura-editor.github.io/) / [sakura-editor](bucket/sakura-editor.json)  
	設定値の persist 化に対応した。設定値は persistentprofile という名前のプロファイルを使って保存する。

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

---
* [MD の参考](https://guides.github.com/features/mastering-markdown/)

