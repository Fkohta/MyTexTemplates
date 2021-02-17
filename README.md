# MyTexTemplates

自分用のLaTeXのテンプレートです．

## 対応環境

- TeXディストリビューション：TeX Live 2020
- TeXエンジン：`uplatex`又は`lualatex`
- コンパイルツール：`latexmk`
- エディタ：VSCode(Microsoft Visual Studio Code)

## 内容

- document：A4のドキュメントのテンプレートです．レポートや論文に使用します．
- poster：**凍結中**．学会発表用のポスターをLaTeXで作るためのテンプレート．
- slide：**凍結中**．発表スライドをLaTeXで作るためのテンプレート．

## TeX Live 2020のインストール(Windows10)

TeXのディストリビューションにはTeXLiveを使用します．  
TeXLiveを使用する理由は，パッケージマネージャである「tlmgr」が付属しており，パッケージの管理がかなり楽だからです．  
以前は日本語化が難しいとか言われていましたが，現在ではそんなことは無いのでこちらを選びます．

以下ではTeX Live 2020をWindows10にインストールする手順を説明します．

### インストーラのダウンロード

[TeXLiveのダウンロードサイト](https://www.tug.org/texlive/acquire-netinstall.html)
から`install-tl-windows.exe`をダウンロードします．

![texlive_download](https://user-images.githubusercontent.com/50233866/108153690-0236c200-711f-11eb-98ce-9b89eff36a4a.png)

### インストール

#### Unpackの実行

ダウンロードした`install-tl-windows.exe`を**管理者として実行**します．ファイルを右クリックしてメニューを表示させましょう．

インストーラを管理者として起動すると，最初に以下のような画面が現れます．

![texlive_installer_1](https://user-images.githubusercontent.com/50233866/108153647-e92e1100-711e-11eb-990e-6c9e1c70e13d.png)

ここでは**Unpack only**を選択します．

Unpack onlyを選択すると，インストーラをUnpackするディレクトリを指定する画面が現れます．
ここで指定するディレクトリはどこでも構いませんが，アクセスしやすい場所にすると良いでしょう．ここではダウンロードディレクトリを指定します．

![texlive_installer_2](https://user-images.githubusercontent.com/50233866/108153834-4a55e480-711f-11eb-872b-82e7e44e2a25.png)

nextボタンをクリックすると画面が遷移します．installボタンをクリックすると，インストーラのUnpackが開始します(TeXLive本体がインストールされるわけではありません)．

#### インストールの実行

Unpackが完了すると，指定したディレクトリにフォルダが生成されます．名前は`install-tl-XXXXXXXX`です(XXXXXXXXには年月日が入ります)．
フォルダの中に`install-tl-windows.bat`ファイルがあります．これを**管理者として実行**します．

インストーラが起動して，以下のような画面が現れます．

![texlive_installer_3](https://user-images.githubusercontent.com/50233866/108153889-635e9580-711f-11eb-8b4d-286cb48b5dc8.png)

デフォルトの設定だと，TeXLiveに含まれる全てのパッケージをインストールするようになっています．このままでは大量のストレージ(7GB近く)を消費してしまうので，インストールするパッケージを選別します．

インストーラの画面から，「高度な設定」をクリックします．

インストール時の設定画面が開くので，まずはスキームを選びます．

1. 画面左下のスキームの「変更」ボタンをクリックする
2. fullスキームから**basicスキーム**に変更する

![texlive_installer_4](https://user-images.githubusercontent.com/50233866/108153943-6eb1c100-711f-11eb-997c-53d63f17156b.png)

次に，インストールするコレクションを決めます．

3. 追加コレクションの数の「カスタマイズ」ボタンをクリックする
4. 言語の内「日本語」と「英語・米語」のチェックをONにする
5. ほかのコレクションの内，「LaTeX基本パッケージ」「LaTeX推奨パッケージ」「Windows専用プログラム」「必須プログラムとファイル」「数学，自然科学，計算機科学パッケージ」のチェックをONにする

![texlive_installer_5](https://user-images.githubusercontent.com/50233866/108153966-7b361980-711f-11eb-9335-bd633d2f530a.png)

※ 画像ではLuaTeXパッケージのチェックをONにしていますが，LuaLaTeXを使用する予定が無いならOFFにしたままで大丈夫です．

画面右側のオプションは，デフォルトのままにしておくのが良いと思われます．
Web上の記事によってはいくつかのオプションを無効にするよう書かれていますが，[TeXLive2020ガイド](https://wtsnjp.com/pdf/texlive-ja.pdf)を見る限り，各オプションは無効にするべきではないでしょう．

ただし，TeXWorksが欲しい場合は「TeXWorksをインストール」のチェックをONにしておきましょう．TeXWorksは非モダンなエディタで，常用するものではありませんが，動作確認をするのに役立つかもしれません．

必要な設定を済ませたら，右下の「インストール」ボタンをクリックします．TeXLive本体のインストールが開始されます．

ネットワーク環境にもよりますが，インストールには結構時間がかかります．気長に待ちましょう．

インストールが完了すると，Windowsメニューに「TeXLive」が追加されます．

### いくつかのパッケージの追加インストール

ここまでで，TeXLive本体のインストールが完了しました．  
しかし，作成する文書によっては必要なパッケージが不足している場合があります．その場合，手動でパッケージを追加しなければなりません．

TeXLiveには，パッケージを管理するためのソフトウェア「tlmgr」が付属しています．これを使うことでパッケージをインストールしたり，アップデートしたりすることができます．

早速tlmgrを使ってパッケージをインストールしましょう．tlmgrはGUIアプリからも使用することができますが，今回はコマンドプロンプトから操作します．

コマンドプロントを開きます．場合によっては管理者として開く必要があるかもしれません．

最初に，tlmgrコマンドが実行できるかテストします．次のコマンドを実行します．

```console
tlmgr update --self --all
```

このコマンドはtlmgr自身のバージョンをアップデートするコマンドです．このコマンドを実行した際，以下のようなエラーが出るならば，管理者として実行する必要があります．

```console
tlmgr.pl: package repository http://ftp.jaist.ac.jp/pub/CTAN/systems/texlive/tlnet (not verified: gpg unavailable)
You don't have permission to change the installation in any way,
specifically, the directory C:/texlive/2020/tlpkg/ is not writable.
Please run this program as administrator, or contact your local admin.
tlmgr.pl: An error has occurred. See above messages. Exiting.
```

では早速，TeX文書のコンパイルを自動化してくれるツール「latexmk」をインストールします．
これまでの手順でTeXLiveをインストールした場合，latexmkが入っていないことがあります．latexmkを使う場合はtlmgrを使ってインストールしましょう．

パッケージのインストールは以下のコマンドで行えます．

```console
tlmgr install latexmk
```

しばらくするとインストールが完了します．このように，コマンドを使用することでパッケージを簡単に追加することができます．

tlmgrの詳しい使い方は[TeX Wiki](https://texwiki.texjp.org/?tlmgr)に記載されています．

## `latexmk`の設定

### `latexmk`とは

`latexmk`とは，TeX文書のタイプセットを自動で実行してくれるツールのことです．
図表番号の参照など，タイプセットを数回行わなければならない文書であっても，必要回数分繰り返しコンパイルしてくれます．

TeX Liveをカスタムスキームでインストールした場合，`latexmk`が含まれていないときがあります．
コマンドプロンプト上で以下のコマンドを実行してエラーが生じた場合は，システムに`latexmk`が存在していません．

```console
> latexmk --version
# latexmkが入っている場合はバージョン情報が表示される
Latexmk, John Collins, 29 September 2020. Version 4.70b
```

その場合は追加でインストールしましょう．`tlmgr`を使えば簡単にインストールできます．
管理者としてコマンドプロンプトを開き，以下のコマンドを実行します．

```console
tlmgr install latexmk
```

これで`latexmk`を利用する準備が完了しました．

### `latexmkrc`の記述

`latexmk`を使ってTeXファイルをコンパイルするには，設定ファイルである`latexmkrc`を記述する必要があります．

`latexmkrc`はPerl言語を使って記述する設定ファイルです．
`latexmkrc`という名前のファイル(拡張子無し)を作成し，コンパイルしたい`*.tex`ファイルと同じディレクトリに置きます．

そして，`latexmkrc`に以下の内容を記述します．

```perl
#!/usr/bin/env perl

$latex      = 'uplatex'.
              ' -file-line-error'.
              ' -halt-on-error'.
              ' -no-guess-input-enc'.
              ' -kanji=utf8 -synctex=1'.
              ' -interaction=batchmode'.
              ' %S';
$dvipdf     = 'dvipdfmx %O -o %D %S';
$pdf_mode   = 3;
$max_repeat = 5;
```

この`latexmkrc`は，`uplatex`+`dvipdfmx`を使って`*.tex`ファイルをコンパイルする際の設定例です．

`latexmkrc`を記述したら，`latexmk`コマンドで`*.tex`ファイルをコンパイルすることができます．

```consol
latexmk hogehoge.tex
```

ただし，コマンドラインからTeX文書をコンパイルすることはあんまり無いです．
多くの場合，モダンなテキストエディタのコマンド呼び出し機能を使って`latexmk`を呼び出して`*.tex`ファイルをコンパイルする方が便利です．

ここではLaTeXエディタとしてMicrosoftの[VSCode](https://code.visualstudio.com/)(Visual Studio Code)を利用することにします．

## VSCodeのインストール

VSCodeをLaTeXエディタとして使用するには，VSCode本体及び[LaTeX-Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)拡張機能が必要となります．

### VSCode本体のインストール

インストーラを[公式サイト](https://code.visualstudio.com/)からダウンロードして実行するだけでインストールを行うことができます．
特別つまずくような要素は無い上，ネット上に解説記事が沢山あるので困ることは無いと思われます．

### LaTeX-Workshop拡張機能のインストール

VSCodeの各種拡張機能は，VSCodeのサイドバーの拡張機能メニューからインストール作業を行うことができます．

![vscode_extention_1](https://user-images.githubusercontent.com/50233866/108154240-ea137280-711f-11eb-87e8-b4dcabfd0435.png)

検索欄に「latex」とでも入力すれば一番上にLaTeX-Workshopが出てくるはずです．  
「install」ボタンをクリックしてインストールしましょう(画像では既にインストールした状態です)．

インストール完了後，VSCodeの再起動を促される場合があります．その際はVSCodeを再起動しましょう．

![vscode_extention_2](https://user-images.githubusercontent.com/50233866/108154267-f3044400-711f-11eb-95f2-065ef9c76ad6.png)

### LaTeX-Workshopの設定

拡張機能をインストールしただけでは，VSCode上でTeX文書をコンパイルすることはできません．コンパイルを行うには，LaTeXのコンパイルに使用するツールやレシピの設定を，VSCodeの設定ファイルに追記しなければなりません．

`Ctrl+,`(Ctrlキーとカンマを同時押し)によってVSCodeの設定を開くことができます．それから，右上のアイコンをクリックして設定ファイル(JSON形式)を開きます．
LaTeX Workshopのコンパイル設定はJSONファイルに追記する形でしか行うことができません．

![vscode_extention_3](https://user-images.githubusercontent.com/50233866/108154332-07e0d780-7120-11eb-8daf-a26627c6bdca.png)

開いたJSONファイルに，以下の内容を**追記**します．
追記する場所は，ファイルの末尾ではなく，一番外側の波括弧の中です．最初からあるいくつかの項目の次に追記します．
尚，以下の内容を追記する場合は，最初からある項目の末尾にカンマを入力してから行います(これはJSONの記述ルールです)．

```json
"latex-workshop.latex.tools": [
    {
      "name": "latexmk",
      "command": "latexmk",
      "args": [
          "-interaction=batchmode",
          "%DOC%"
      ],
    }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "latexmk ",
      "tools": [
        "latexmk"
      ]
    }
  ],
  "latex-workshop.view.pdf.viewer": "tab",
  "latex-workshop.latex.clean.fileTypes": [
    "*.aux", "*.bbl", "*.blg", "*.idx", "*.ind", "*.lof", "*.lot", "*.out", "*.toc", "*.acn", "*.acr", "*.alg", "*.glg", "*.glo", "*.gls", "*.ist", "*.fls", "*.log", "*.fdb_latexmk", "*.synctex.gz", "_minted*", "*.nav", "*.snm", "*.vrb",
  ],
  "latex-workshop.latex.autoClean.run": "never",
  "latex-workshop.latex.autoBuild.run": "never",
  "[latex]": {
    "editor.formatOnPaste": false,
    "editor.formatOnSave": false,
    "editor.suggestSelection": "recentlyUsedByPrefix",
    "editor.tabSize": 2,
  }
```

この設定により，`latexmk`を使用したuplatex+dvipdfmxエンジンによるコンパイルが可能になります．

LaTeX Workshopでは，コンパイルに使うツール及びそれに与えるオプションを設定する`latex-workshop.latex.tools`と，`tools`を使ってコンパイルを行うシーケンスを設定する`latex-workshop.latex.recipes`の2つの項目を設定する必要があります．

上の例では`latex-workshop.latex.tools`にて`latexmk`を使用したコンパイルの設定を行っています．設定したツールには「`latexmk`」という名前を付けています．

また，`latex-workshop.latex.recipes`では単純に，`tools`で設定したツールを1回だけ使ってコンパイルするように設定しています．レシピの名前はツールと同様，「`latexmk`」にしています．

### TeX文書のコンパイル

設定が完了したので，早速コンパイルを行ってみます．適当な`*.tex`ファイルを開きます．

`*.tex`ファイルを開いた状態で，`Ctrl+Shift+p`を押してVSCodeのコマンドパレットを開きます．  
コマンドパレットに「latex」と入力すると，LaTeX Workshopのコマンドの候補が表示されるので，その中の「Build with recipes」を選択し，先ほど設定したレシピ(`latexmk`)を選択します．

![vscode_compile](https://user-images.githubusercontent.com/50233866/108154986-5b075a00-7121-11eb-8098-5c98a070e5f6.png)

設定が適切ならば，コンパイルが実行され，中間ファイルやPDF文書が生成されます．

もしくは，LaTeX-Workshopのバージョン8.12.0から追加されたビルドアイコンをクリックすることでもコンパイルを実行することができます．
この場合は，`latex-workshop.latex.recipes`に設定したレシピのうち，一番上に設定したレシピが実行されます．

![latex_workshop_build_icon](https://user-images.githubusercontent.com/50233866/108155040-770afb80-7121-11eb-9ded-f9d024e013ee.png)

PDF文書のプレビューもVSCode内で行うことができます．画面右上のプレビューボタンをクリックすると，画面が分割され，右側のタブにPDFが表示されます．

![vscode_preview_pdf](https://user-images.githubusercontent.com/50233866/108155067-84c08100-7121-11eb-8447-842aa85bde2b.png)
