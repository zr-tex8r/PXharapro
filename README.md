PXharapro パッケージバンドル
============================

LaTeX： pLaTeX／upLaTeXでもっともっと原ノ味フォントする

pLaTeX／upLaTeXの標準の和文フォントを「原ノ味フォント」にする場合に、
それに適した補助的なフォント設定を行うためのパッケージ群。
以下の2つのパッケージからなる。

  * pxharaproパッケージ (予定)： Source Serif/Sans Proの欧文と合わせる
  * pxharaprojパッケージ： プロポーショナル和文を利用する

### 前提環境

  * フォーマット： LaTeX
  * エンジン： e-pTeX、e-upTeX
  * DVIウェア(pxharaproj)： dvipdfmx
  * 依存パッケージ：
      - ifptexパッケージ
      - etoolboxパッケージ

### インストール

  - `tfm/*.tfm`  → $TEXMF/fonts/tfm/public/pxharapro/
  - `ofm/*.ofm`  → $TEXMF/fonts/ofm/public/pxharapro/
  - `vf/*.vf`    → $TEXMF/fonts/vf/public/pxharapro/
  - `map/*.map`  → $TEXMF/fonts/map/dvipdfmx/pxharapro/
  - `*.sty`      → $TEXMF/tex/platex/pxharapro/

### ライセンス

MITライセンスの下で配布される。


pxharaproj パッケージ ー プロポーショナル和文を利用する
-------------------------------------------------------

### パッケージ読込

    \usepackage[<オプション>,...]{pxharaproj}

利用可能なオプションは以下の通り。

  * ドライバオプション： `dvipdfmx`／`dvips`／`nodvidriver`が指定可能。
    `dvipdfmx`を指定するとマップファイルが読み込まれるようになる。
    既定は`nodvidriver`。
  * `scale=<実数>`： 和文スケール値を指定する。既定値は`\Cjascale`の値で、
    それが未定義の場合は1になる。

### 機能

  * プロポーショナルの仮名字形をもつ「原ノ味フォント」用の和文フォント
    ファミリの`pxharapmc`（原ノ味明朝）と`pxharapgt`（原ノ味ゴシック）
    が定義される。（横組のみ）
      - `pxharapmc/el/n`： Harano Aji Mincho ExtraLight
      - `pxharapmc/l/n`：  Harano Aji Mincho Light
      - `pxharapmc/m/n`：  Harano Aji Mincho Regular
      - `pxharapmc/sb/n`： Harano Aji Mincho Medium（※SemiBoldではない）
      - `pxharapmc/b/n`：  Harano Aji Mincho Bold
      - `pxharapmc/eb/n`： Harano Aji Mincho Heavy
      - `pxharapgt/el/n`： Harano Aji Gothic ExtraLight
      - `pxharapgt/l/n`：  Harano Aji Gothic Light
      - `pxharapgt/m/n`：  Harano Aji Gothic Regular
      - `pxharapgt/sb/n`： Harano Aji Gothic Medium
      - `pxharapgt/b/n`：  Harano Aji Gothic Bold
      - `pxharapgt/eb/n`： Harano Aji Gothic Heavy

  * 標準の和文フォントファミリ（`\mcdefault`／`\gtdefault`）について、
    `prp`シェープに、前述の`pxharapmc`／`pxharapgt`のシェープのエイリアス
    を割り当てる。
      - japanese-otfパッケージ（`deluxe`付）における和文ファミリの`prp`
        シェープ割当（ヒラギノ用）と同様の動作である。japanese-otfが
        `prp`への割当を行っている場合、本パッケージの設定で上書きされる。
      - 原ノ味フォントのウェイトについては、「updmapで標準和文フォントを
        `haranoaji`に設定した状態」を想定して、その場合の標準和文シェープ
        に対するウェイトと同じものが選択される。例えば既定（japanese-otf
        非読込）では「明朝（`mc/m/n`）はRegular、ゴシック（`gt/m/n`）は
        Medium」となっているため、  
        `mc/m/prp`→`pxharapmc/m/n`； `gt/m/prp`→`pxharapgt/sb/n`  
        というエイリアス設定がなされる。japanese-otfが読み込まれた場合も
        同様に標準シェープのウェイトに追随する。
      - さらに、pxchfonが読み込んで物理フォントを置換した場合については、
        そのフォントが原ノ味フォントである時に限ってウェイトを追随する。
        例えば、  
        `\setminchofont{HaranoAjiMincho-Light.otf}`  
        を実行した場合、`mc/m/prp`の参照先も`pxharapmc/l/n`に変わる。

  * 和文を`prp`シェープに切り替えるユーザ命令`\propshape`を提供する。  
    ※japanese-otfパッケージと同様。

更新履歴
--------

  * Version 0.2  〈2020/06/28〉
      - 最初の公開版。

--------------------
Takayuki YATO (aka. "ZR")  
https://github.com/zr-tex8r
