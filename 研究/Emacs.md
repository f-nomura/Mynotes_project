
# Table of Contents

1.  [Emacs 構成と基本の操作](#orgda8a565)
    1.  [画面の構成](#org62d8e64)
        1.  [フレーム](#org96609a9)
        2.  [ウィンドウ](#org3ecca8b)
        3.  [フリンジ](#org67c2705)
        4.  [バッファ](#org030ab07)
        5.  [モードライン](#orge3c1d7a)
        6.  [ミニバッファ](#org8e36cd7)
    2.  [モード](#org8840d85)
        1.  [メジャーモード](#org15f7295)
        2.  [マイナーモード](#org86b3b0f)
        3.  [フック](#org897bfd0)
    3.  [コマンド](#orgffe85b1)
        1.  [コマンド検索](#org504f506)
        2.  [まず覚えるコマンド](#orgc202c1f)
        3.  [ファイル(バッファ)操作](#orgdd7093c)
        4.  [カーソル移動](#org765c305)
        5.  [文字の入力や文字列の操作](#org93d44ca)
        6.  [検索](#orgca8e7ed)
        7.  [ウィンドウ操作](#org2573d23)
        8.  [ディレクトリ操作](#orgb763dff)
        9.  [org-mode 関連](#orgf96cb9e)
    4.  [設定ファイルの編集](#orgff04345)
        1.  [**;;** コメントはセミコロン](#orgc4a69ca)
        2.  [**t と nil** True/False](#org62dd436)
        3.  [**&rsquo; と #&rsquo;** 変数と関数(関数名)の区別](#org63db421)
        4.  [**seq** 変数の定義と代入](#org7fe2350)
        5.  [**map!** キーの割り当て](#orge82710e)
        6.  [**add-hook** フック（特定のモードでのみ動かす）](#orgf512955)
    5.  [補足：追加設定](#orgee26d9d)
        1.  [Ctrl と Alt キーを使いやすい位置に設定する](#org994ba85)
2.  [標準機能](#org9b2e9a4)
        1.  [選択範囲（リージョン）に文字を上書き入力できるようにする](#orgdae3c3f)
        2.  [next line で最終行の場合に改行を追加する](#orgcc1f2f3)
        3.  [マウスでテキストを選択したときに、自動的にキルリング(=クリップボード)に保存する](#orga963548)
        4.  [**treemacs** : ファイルツリーを表示する](#orgde625c0)
        5.  [**eshell** : ターミナルバッファを使う](#org95ac3ef)
3.  [拡張機能](#org2a15772)
        1.  [**Magit** : Git 管理](#org69e6339)
        2.  [**consult** : キルリング(=クリップボード)を可視化する](#org6a5061b)
        3.  [**cmigemo** : ローマ字で打つだけで日本語がヒットするようにする](#org7275a53)
        4.  [**rainbow-delimiters** : コード内のカッコの色を、階層（深さ）ごとに自動で色分けする](#orgd5feeb4)
        5.  [**vundo** : ファイルの変更履歴（Undo/Redo）を、分岐を含めて視覚的に表示する(Visual Undo)](#org21bd491)
        6.  [**anzu** : 文字検索のヒット数と何番目かの表示](#org085a373)
        7.  [**multiple-cursors** : 複数カーソル](#org46bb8b1)
4.  [Org-mode 基本の文法](#org306fdd7)
    1.  [見出し](#org195a81e)
    2.  [リスト](#orgc69226d)
        1.  [チェックリスト<code>[1/2]</code><code>[50%]</code>](#orgff852a8)
    3.  [文字装飾](#org704e533)
    4.  [リンク](#orgcdd65de)
    5.  [テーブル](#org78cadd6)
    6.  [ToDo 管理](#org21dee79)
        1.  [今週のレポートを作成する](#orga73aeea)
        2.  [課題を提出する](#org815f6ee)
    7.  [ブロック](#org0bab67c)
        1.  [コードブロック](#org67d38b0)
        2.  [メモ／example の枠](#org8ef9349)
        3.  [引用](#orga71193b)
    8.  [エクスポートオプション](#org4622b1d)
        1.  [代表的なオプション](#org4247bb7)
        2.  [#+OPTIONS の使用例](#org0c73e48)
5.  [Org-mode + jupyter + Python](#orgc85fa53)
    1.  [処理の流れ](#orga97c613)
    2.  [環境構築](#orgc328191)
        1.  [Emacs が動的モジュールサポート付きかどうか確認する](#orgca515fa)
        2.  [**MELPA** を使えるようにする](#org78351a5)
        3.  [`init.el` で `jupyter` を有効にする](#org93ad3b4)
        4.  [`package.el` でパッケージを記述する](#org7bafbf8)
        5.  [仮想環境を作成する](#orgee40609)
        6.  [`config.el` に `jupyter.exe` が入っているフォルダのパスを明記する、または Windows の環境変数に登録する](#org07562f1)
        7.  [実行の確認](#orgc3ce3e8)
        8.  [実行場所の確認](#org67ac2a9)
    3.  [Org-Babel の :session について](#org2e61d1c)
        1.  [`:session` とは](#org9ad9c52)
        2.  [詳しく説明](#orgd57132c)
        3.  [セッション名の意味](#org1fd52c9)



<a id="orgda8a565"></a>

# Emacs 構成と基本の操作


<a id="org62d8e64"></a>

## 画面の構成


<a id="org96609a9"></a>

### フレーム

Windows や Mac でウィンドウと呼ばれるアプリケーションの表示枠のことを Emacs では **フレーム** といいます。


<a id="org3ecca8b"></a>

### ウィンドウ

フレーム内でファイル（≒ バッファ）を表示する領域を **ウィンドウ** といいます。
ウィンドウは分割が可能です。


<a id="org67c2705"></a>

### フリンジ

ウィンドウの両端にある追加情報を視覚的に表示するための領域。空行を「~」で表したり、折り返しを示したりします。


<a id="org030ab07"></a>

### バッファ

メモリ上に作成された **オブジェクト** を **バッファ** といいます。

1.  **ファイルバッファ** ：実際のファイルと連結しているバッファ

2.  **非ファイルバッファ** ：Emacs が画面表示や作業のために一時的に作っているバッファ

    -   \*eww\*（プレビューバッファ）
    -   \*scratch\*（スクラッチバッファ）
    -   \*Messages\*（ログバッファ）
    -   Dired（フォルダ一覧バッファ）


<a id="orge3c1d7a"></a>

### モードライン

ウィンドウの下部にある領域のことを **モードライン** といいます。
カレントバッファに関する情報や、その他 Emacs が取得できる情報であればなんでも表示させることができます。


<a id="org8e36cd7"></a>

### ミニバッファ

モードラインの下にある領域。コマンドなどが表示されます。


<a id="org8840d85"></a>

## モード


<a id="org15f7295"></a>

### メジャーモード

バッファに対して必ず 1 つ適用されるモードのこと。モードライン右端に表示されます。


<a id="org86b3b0f"></a>

### マイナーモード

マイナーモードはメジャーモードとは異なり、いくつでも適用可能でそれぞれについて有効化／無効化が設定できます。


<a id="org897bfd0"></a>

### フック


<a id="orgffe85b1"></a>

## コマンド

C- : Ctrl キーを押しながらの操作
M- : Alt(Esc) キーを押しながらの操作


<a id="org504f506"></a>

### コマンド検索

-   **M-x コマンド名**


<a id="orgc202c1f"></a>

### まず覚えるコマンド

-   **C-/** : UNDO
-   **C-Shift-/** : REDO
-   **C-g** : 現在行っている操作のキャンセル
-   **C-x C-c** : Emacs を終了する


<a id="orgdd7093c"></a>

### ファイル(バッファ)操作

-   **C-x C-f** : ファイルの作成(File)
-   **C-x C-s** : ファイルの保存(Save)
-   **C-x C-w** : 別名で保存(Write)
-   **C-x i** : 現在のバッファに別のファイルを挿入する(Insert)。別のファイルの内容を貼り付けできる

-   **C-x b** : バッファを切り替える(Buffer)。削除しない限りバッファは残っているので、画面に表示されていなくても切り替えできる
-   **C-x k** : バッファを削除する(Kill)


<a id="org765c305"></a>

### カーソル移動

-   前の行(Previous) **C-p** , 次の行(Next) **C-n** , 次の文字(Forward) **C-f** , 後ろの文字(Backward) **C-b** , 行頭(Abcde&#x2026;) **C-a** , 行末(End) **C-e**
-   **C-l** : カーソル行が画面中央の位置になるようにスクロールされる(Line)
-   **C-v** : １画面下にスクロール(View)
-   **M-v** : １画面上にスクロール(View)
-   **M-<** : バッファの先頭へ
-   **M->** : バッファの終端へ
-   **M-g g** : 指定行に移動(Go to)


<a id="org93d44ca"></a>

### 文字の入力や文字列の操作

-   **C-SPC** : リージョン(開始位置)を決定する→カーソル移動で範囲選択
-   **C-M-SPC** : リージョンを決定、SPC でブロックごとに範囲選択
-   **M-w** : コピー
    キルリング(= Emacs 内のクリップボード)に保存される
-   **C-y** : ペースト
    Windows 内のクリップボードからペーストしたい場合は、Win+V でクリックしてから C-y で貼り付けできる
-   **C-w** : カット＆コピー


<a id="orgca8e7ed"></a>

### 検索

-   **C-s** : バッファ内の文字の検索。次の候補に進むには再度 **C-s** 、前の候補に戻るには **C-r**
    init.el で ;;japanese のコメントアウトを外している場合は、cmigemo が必要です。


<a id="org2573d23"></a>

### ウィンドウ操作

-   **C-x 3** : 左右分割
-   **C-x o** : ウィンドウ移動
-   **C-x 0** : カレントウィンドウを閉じる（バッファは消えていないので **C-x b** で再表示できる）
-   **C-x 1** : カレントウィンドウ以外のウィンドウを閉じる


<a id="orgb763dff"></a>

### ディレクトリ操作

-   **C-x d** : Dired バッファを開く
-   **+（Shift-;）**: 新規ファイル、新規フォルダを作る
-   カーソル行で **d** → **x** : ファイルの削除フラグを立てる(delete) **x** で一括削除
-   **R** : 名前の変更(Rename)
-   **C** : ファイルのコピー、ペースト


<a id="orgf96cb9e"></a>

### org-mode 関連

-   **M-x org-md-export-to-markdown** : .org ファイルを .md ファイルに変換する


<a id="orgff04345"></a>

## 設定ファイルの編集

Emacs は Elisp(Emacs Lisp エルリスプ) というプログラミング言語で書かれています。
設定ファイルを編集することでショートカットを作成したり表示を変更したりできます。


<a id="orgc4a69ca"></a>

### **;;** コメントはセミコロン

    ;; コメント


<a id="org62dd436"></a>

### **t と nil** True/False

    ;; t=True  例）カーソルの点滅を有効にする
    (blink-cursor-mode t)
    
    ;; nil=False  例）カーソルの点滅を無効にする
    (blink-cursor-mode nil)


<a id="org63db421"></a>

### **&rsquo; と #&rsquo;** 変数と関数(関数名)の区別

    ;; my-list という変数にリストを代入する
    (setq my-list '(apple banana orange))
    
    ;; M-y というキーに consult-yank-pop を登録する
    (map! "M-y" #'consult-yank-pop)


<a id="org7fe2350"></a>

### **seq** 変数の定義と代入

    ;; my-name という変数に "Alice" という文字を代入する
    (setq my-name "Alice")


<a id="orge82710e"></a>

### **map!** キーの割り当て

    ;; (map! "押すキー" #'動かしたい関数名)
    (map! "C-c f" #'find-file)


<a id="orgf512955"></a>

### **add-hook** フック（特定のモードでのみ動かす）

    ;; (add-hook 'モード名-hook #'動かしたい関数)
    (add-hook 'prog-mode-hook #'display-line-numbers-mode)


<a id="orgee26d9d"></a>

## 補足：追加設定


<a id="org994ba85"></a>

### Ctrl と Alt キーを使いやすい位置に設定する

Windows の場合 Power Toys > Keyboard Manager > キーの再マップ から変更できます。
ただし Capslock キーへの割り当ては非推奨です。

(参考：[Windowsのキーボードの割り当てを変更して生産性を高める](https://qiita.com/EkaTaro3/items/37d7c19acea7bc777749))


<a id="org9b2e9a4"></a>

# 標準機能


<a id="orgdae3c3f"></a>

### 選択範囲（リージョン）に文字を上書き入力できるようにする

    (delete-selection-mode t)


<a id="orgcc1f2f3"></a>

### next line で最終行の場合に改行を追加する

    (setq next-line-add-newlines t)


<a id="orga963548"></a>

### マウスでテキストを選択したときに、自動的にキルリング(=クリップボード)に保存する

    (setq  mouse-drag-copy-region t)


<a id="orgde625c0"></a>

### **treemacs** : ファイルツリーを表示する

    ## init.el
    :ui
    (treemacs)  ;; コメントアウトを外す

-   **C-c o p** : ファイルツリーを表示する、非表示にする(Open Project)
-   **C-x p** : ファイルツリーにフォーカスを合わせる(Project)
-   **c f** : ファイル作成(File)
-   **c d** : フォルダ作成(Directory)
-   **R** (Shift + r) : 名前の変更(Rename)
-   **d** : 削除(Delete)
-   **y f** : コピー＆ペースト(Yank)
-   **m** : 移動（カット＆ペースト, Move）


<a id="org95ac3ef"></a>

### **eshell** : ターミナルバッファを使う

Windows 環境では vterm の導入が難しいそうです。そこで完全 Emacs 製の Eshell を導入します。

    ## init.el
    :term
    eshell    ;; コメントアウトを外す

-   **C-x p** : フォーカスを合わせる


<a id="org2a15772"></a>

# 拡張機能


<a id="org69e6339"></a>

### **Magit** : Git 管理

    ;; init.el
    ;; magit のコメントアウトを外す
    :tools
    magit           ; a git porcelain for Emacs

1.  **C-c v g**
2.  **s** (Stage) : 変更があったファイルや行にカーソルを合わせて s を押すと、ステージ
3.  **c c** (Commit) : c を 2 回押すと、コミットメッセージを書く画面が開く
4.  **C-c C-c** (Commit) :
    コミット
5.  **P p** （Push）: P（Shift + p）を押したあと、もう一度 p を押すとリモートへプッシュ
6.  **F** (Fetch/Pull) : Pull 関連の操作


<a id="org6a5061b"></a>

### **consult** : キルリング(=クリップボード)を可視化する

    ;; config.el
    ;; クリップボード履歴（キルリング）を一覧から選んで貼り付ける設定
    (map! "M-y" #'consult-yank)


<a id="org7275a53"></a>

### **cmigemo** : ローマ字で打つだけで日本語がヒットするようにする

[インストール](https://github.com/koron/cmigemo/releases/tag/v1.8.0)して解凍後、環境変数に登録するか config.el に記述してください。

    ## 環境変数の編集
    変数 > Path > 新規 > .exe ファイルが入っている「フォルダ(￥bin)」のパスを登録
    
    ## 反映
    再起動 → doom sync

Windows の場合は msvc 版と ucrt64 版がありますがどちらでもいいです。ucrt64 版は Windows10 以降の新しい標準規格に合わせて作られたものです。


<a id="orgd5feeb4"></a>

### **rainbow-delimiters** : コード内のカッコの色を、階層（深さ）ごとに自動で色分けする

    ;; package.el
    (use-package! rainbow-delimiters
        :hook (prog-mode . rainbow-delimiters-mode))


<a id="org21bd491"></a>

### **vundo** : ファイルの変更履歴（Undo/Redo）を、分岐を含めて視覚的に表示する(Visual Undo)

    ;; package.el
    (package! vundo)

    ;; config.el
    ;; ショートカットを登録
    (map! "C-c u" #'vundo)
    
    ;; vundo モードで Enter キーを押すと決定する
    (after! vundo
      (define-key vundo-mode-map (kbd "RET") #'vundo-confirm))


<a id="org085a373"></a>

### **anzu** : 文字検索のヒット数と何番目かの表示

    (package! anzu)

    ;; config.el
    (use-package! anzu
      :defer t                     ;; 遅延
      :init (global-anzu-mode +1)  ;; 常時
      :config
       (setq anzu-use-migemo t))   ;; cmigemoに対応


<a id="org46bb8b1"></a>

### **multiple-cursors** : 複数カーソル

    ;; package.el
    (package! multiple-cursors)

    ;; config.el
    (use-package! multiple-cursors
      :defer t
      :bind
      (("C-S-c C-S-c" . mc/edit-lines)
       ("C->" . mc/mark-next-like-this)
       ("C-<" . mc/mark-previous-like-this)))

-   **C-S-c C-S-c** （Ctrl + Shift + c を 2 回） : 複数行にまたがる範囲を選択した状態でこれを押すと、選択したすべての行の末尾（または先頭）に一斉にカーソルが出現する

-   **C->** : 今カーソルが当たっている単語と同じ単語の「次の位置」に向か

ってカーソルを追加する

-   **C-<** : 「前の位置」に向かって同じ単語にカーソルを追加する


<a id="org306fdd7"></a>

# Org-mode 基本の文法


<a id="org195a81e"></a>

## 見出し

    * 第1階層の見出し（最上位）
    ** 第2階層の見出し
    *** 第3階層の見出し


<a id="orgc69226d"></a>

## リスト

-   箇条書きアイテム 1
-   箇条書きアイテム 2

-   最初のステップ
-   次のステップ


<a id="orgff852a8"></a>

### チェックリスト<code>[1/2]</code><code>[50%]</code>

チェックリストは **C-c** でチェックの付け外しができます。
また、チェックリストの親要素に **クッキー** を付けると進捗状況を自動計算して表示してくれます。

    * 見出し[/]
    * 見出し[%]

-   [ ] 未完了のタスク
-   [X] 完了したタスク


<a id="org704e533"></a>

## 文字装飾

フォントが対応していない場合は反映されません。例えば HackGen は Itaric に対応していません。

-   太字（Bold）: ****太字****
-   斜体（Italic）: ***斜体***
-   下線（Underline）: **<span class="underline">下線</span>**
-   取り消し線（Strikethrough）: **<del>取り消し線</del>**
-   インラインコード: **`コード`** または **`等幅フォント`**
    
    **太字**
    *斜体*
    <span class="underline">下線</span>
    
    <del>取り消し線</del>
    `コード`  `等幅フォント`


<a id="orgcdd65de"></a>

## リンク

URL はもちろん、ファイルへのパスやファイル内の見出しへのリンクも可能です。

    [[https://orgmode.org][Org-mode 公式サイト]]
    [[https://orgmode.org]] （説明文なし）
    
    [[* 文字装飾][さっきのリストへ移動]]
    [[file:Emacs.md][別のファイルを開く]]
    [[file:./線形代数/入門微分積分代１章連続関数.md][別の階層のファイルを開く]]

[Org-mode 公式サイト](https://orgmode.org)
<https://orgmode.org> （説明文なし）

[さっきのリストへ移動](#org704e533)
[別のファイルを開く](Emacs.md)
[別の階層のファイルを開く](./線形代数/入門微分積分代１章連続関数.md)


<a id="org78cadd6"></a>

## テーブル

-   |表題１|表題２|表題３| + TAB ：表題揃え

-   |- + TAB ：区切り線を補完

    | 名前     | 年齢 | 職業       |
    |----------+------+------------|
    | 田中太郎 |   28 | エンジニア |
    | 山田花子 |   35 | デザイナー |

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-right" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">名前</th>
<th scope="col" class="org-right">年齢</th>
<th scope="col" class="org-left">職業</th>
</tr>
</thead>
<tbody>
<tr>
<td class="org-left">田中太郎</td>
<td class="org-right">28</td>
<td class="org-left">エンジニア</td>
</tr>

<tr>
<td class="org-left">山田花子</td>
<td class="org-right">35</td>
<td class="org-left">デザイナー</td>
</tr>
</tbody>
</table>


<a id="org21dee79"></a>

## ToDo 管理

    * TODO 今週のレポートを作成する
    * DONE 課題を提出する


<a id="orga73aeea"></a>

### TODO 今週のレポートを作成する


<a id="org815f6ee"></a>

### DONE 課題を提出する


<a id="org0bab67c"></a>

## ブロック


<a id="org67d38b0"></a>

### コードブロック

    ## コードブロック
    print("Hello world!")


<a id="org8ef9349"></a>

### メモ／example の枠

    メモ


<a id="orga71193b"></a>

### 引用

> 引用文


<a id="org4622b1d"></a>

## エクスポートオプション

Org モードのエクスポートオプションは、Org 文書を HTML や Markdown などの外部フォーマットに変換する際の出力挙動を、ファイルごとに制御するために使われます。


<a id="org4247bb7"></a>

### 代表的なオプション

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">キーワード</th>
<th scope="col" class="org-left">説明</th>
</tr>
</thead>
<tbody>
<tr>
<td class="org-left">#+TITLE:</td>
<td class="org-left">タイトルを指定する</td>
</tr>

<tr>
<td class="org-left">#+AUTHOR:</td>
<td class="org-left">著者名を指定する</td>
</tr>

<tr>
<td class="org-left">#+DATE:</td>
<td class="org-left">日付を指定する</td>
</tr>

<tr>
<td class="org-left">#+EMAIL:</td>
<td class="org-left">メールアドレスを指定する</td>
</tr>

<tr>
<td class="org-left">#+DESCRIPTION:</td>
<td class="org-left">文書の説明を記述する</td>
</tr>

<tr>
<td class="org-left">#+KEYWORDS:</td>
<td class="org-left">文書のキーワードを記述する</td>
</tr>

<tr>
<td class="org-left">#+LANGUAGE:</td>
<td class="org-left">文書の言語を記述する</td>
</tr>

<tr>
<td class="org-left">#+TEXT:</td>
<td class="org-left">文書の最初に現れる文章を記述する(複数行可)</td>
</tr>

<tr>
<td class="org-left">#+OPTIONS:</td>
<td class="org-left">オプションを指定する</td>
</tr>

<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">&#xa0;</td>
</tr>
</tbody>
</table>


<a id="org0c73e48"></a>

### #+OPTIONS の使用例

-   `#+OPTIONS: toc:nil` : 目次を生成しない
-   `#+OPTIONS: num:t` : 見出しに自動で番号を振る
-   `#+OPTIONS: author:nil` : 著者名を非表示にする
-   `#+OPTIONS: \n:t` : Org ファイル内の改行をそのままエクスポート結果の改行に反映する


<a id="orgc85fa53"></a>

# Org-mode + jupyter + Python

文芸的プログラミングのための環境構築を行います。
今回は非同期処理と描画埋め込みのできる **emacs-jupyter** を導入します。

-   **Org Babel** : Org-mode でコードブロックを実行する仕組み
-   **emacs-jupyter** : その中で Jupyter kernel を使って Python などを実行する拡張


<a id="orga97c613"></a>

## 処理の流れ

1.  Org-mode で Python コードを記述する
2.  **C-c C-c** で実行する
3.  emacs-jupyter が **ZeroMQ** という通信を通して **Jupyter Kernel** に送る
4.  Jupyter Kernel から出力が返ってくる
5.  emacs-jupyter が結果を Org-mode に返す


<a id="orgc328191"></a>

## 環境構築


<a id="orgca515fa"></a>

### Emacs が動的モジュールサポート付きかどうか確認する

Elisp では記述しきれない **ZeroMQ** などの高度な技術を呼び出すために
「動的モジュールサポート」が必要です。

最近の OS 標準パッケージや Homebrew 等でインストールした Emacs であれば概ね有効になっているそうですが、念のため確認します。

1.  `M-:` を押し、評価モードに入る
2.  ミニバッファに `Eval:` と出るので、以下を入力する。 `t(=True)` であれば動的モジュールサポートが付いている

    (functionp 'module-load)


<a id="org78351a5"></a>

### **MELPA** を使えるようにする

MELPA は 「Emacs のための非公式パッケージストア」 です。
GNU ELPA という公式のパッケージストアが標準機能としてありますが、
条件が厳しいためほとんどの拡張機能は MELPA にて配布されています。

Doom Emacs では既に有効化されています。


<a id="org93ad3b4"></a>

### `init.el` で `jupyter` を有効にする

(org +jupyter) に変更します。

    ;; init.el
    :lang
    (org +jupyter)


<a id="org7bafbf8"></a>

### `package.el` でパッケージを記述する

    ;; package.el
    (package! jupyter)
    (package! simple-httpd :recipe (:host github :repo "skeeto/emacs-web-server"))
    (package! emacs-websocket :recipe (:host github :repo "ahyatt/emacs-websocket"))


<a id="orgee40609"></a>

### 仮想環境を作成する

1.  現在の環境の確認

        py -0p
        where python
        where jupyter

2.  仮想環境の作成

        py -3.12 -m venv C:\Users\nomura\myenv312

3.  必要なパッケージ

        C:\Users\nomura\myenv312\Scripts\python.exe -m pip install -U pip
        C:\Users\nomura\myenv312\Scripts\python.exe -m pip install jupyter ipykernel
        C:\Users\nomura\myenv312\Scripts\python.exe -m ipykernel install --user --name emacs-venv --display-name "Python (Emacs Venv)"

4.  確認

        C:\Users\nomura\myenv312\Scripts\jupyter.exe kernelspec list


<a id="org07562f1"></a>

### `config.el` に `jupyter.exe` が入っているフォルダのパスを明記する、または Windows の環境変数に登録する

    ;; config.el
    (after! jupyter
      (setq jupyter-executable "C:/Users/light/myenv312/Scripts/jupyter.exe")
      (add-to-list 'exec-path "C:/Users/light/myenv312/Scripts"))

デバイスごとにユーザー名が異なる場合は以下のように設定することで対応できます。
`~` は自動的に現在のユーザーのホームディレクトリ（Windows なら C:/Users/ユーザー名）に展開されます。

    ;; Windows + Doom + emacs-jupyter 向けの強制パス
    (let* ((venv "~/myenv312/Scripts/")
           (py   (concat venv "python.exe"))
           (jup  (concat venv "jupyter.exe")))
      (setq python-shell-interpreter py
            jupyter-executable jup)
      (setenv "PYTHON" py)
      (setenv "PATH" (concat venv ";" (or (getenv "PATH") "")))
      (setq exec-path (cons venv (delete venv exec-path))))
    
    (after! jupyter
      ;; ob-jupyter の python 探索を上書き
      (defun jupyter-locate-python ()
        (or (and (stringp python-shell-interpreter)
                 (file-exists-p python-shell-interpreter)
                 python-shell-interpreter)
            (let ((py (getenv "PYTHON")))
              (and py (file-exists-p py) py))
            (executable-find "python")
            "~/myenv312/Scripts/python.exe")))
    
    (after! org
      (require 'jupyter)
      (setq org-babel-jupyter-command
            "~/myenv312/Scripts/python.exe -m jupyter")
      (org-babel-do-load-languages
       'org-babel-load-languages
       '((jupyter . t))))


<a id="orgc3ce3e8"></a>

### 実行の確認

    C:\Users\nomura\myenv312\Scripts\python.exe -m pip install -U numpy matplotlib

    import matplotlib.pyplot as plt
    import numpy as np
    
    x = np.linspace(0, 10, 100)
    plt.plot(x, np.sin(x))
    plt.show()


<a id="org67ac2a9"></a>

### 実行場所の確認

    import sys
    print(sys.executable)


<a id="org2e61d1c"></a>

## Org-Babel の :session について


<a id="org9ad9c52"></a>

### `:session` とは

`:session` は、 **複数のコードブロック間で Python の状態を共有する** ための機能です。


<a id="orgd57132c"></a>

### 詳しく説明

1.  **:session がない場合**
    -   各コードブロックは独立した別々の Python プロセスで実行される
    -   前のブロックで定義した変数は、次のブロックでは使えない

    # ブロック1
    x = 10
    
    # ブロック2 (x は定義されていない状態)
    print(x)  # エラー

1.  **:session py がある場合**
    -   同じセッション名（ここでは \`py\`）のコードブロックは **同じ Python プロセス内** で実行される
    -   前のブロックで定義した変数や関数が、後のブロックで使える

    # ブロック1 :session py
    x = 10
    
    # ブロック2 :session py
    print(x)  # 10 が出力される


<a id="org1fd52c9"></a>

### セッション名の意味

`:session py` の `py` はセッション名です。
異なる名前にすれば、別のセッションを作ることができます。

    # :session py → py セッション内で実行
    x = 10
    
    # :session another → 別のセッション内で実行
    print(x)  # エラー（別セッションなので x が見えない）

