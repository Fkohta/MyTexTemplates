# MyTexTemplates

自分用のLaTeXのテンプレートです．

## 内容

- document：A4のドキュメントのテンプレートです．レポートや論文に使用します．
- poster：**凍結中**．学会発表用のポスターをLaTeXで作るためのテンプレート．
- slide：**凍結中**．発表スライドをLaTeXで作るためのテンプレート．

## LaTeXエンジンの種類

- `uplatex`及び`dvipdfmx`
- `lualatex`

の2つのLaTeXエンジンのためのテンプレートを用意しています．
コンパイルオプションは以下の通りです．

### uplatex

- コマンド：`upLaTeX(ptex2pdf)`
- 引数：
  - `-u`
  - `-l`
  - -`ot`
  - `-kanji=utf8`
  - `-synctex=1`
  - `-interaction=nonstopmode`

### lualatex

- コマンド：`lualatex`
- 引数：
  - `-cmdx`
  - `-synctex=1`
  - `-interaction=nonstopmode`

## `latexmkrc`を使用する

適切なコンパイルオプションを使用することでコンパイルが可能ですが，ここでは`latexmk`を使用することを推奨します．
それぞれのTeX文書のための`latexmkrc`ファイルを用意しているため，トップレベルの`.tex`ファイルと同じディレクトリに`latexmkrc`を置き，`latexmk master.tex`コマンドを実行することで適切なオプションでコンパイルすることができます．
