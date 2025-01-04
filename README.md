# Berrycake.js

**Berrycake.js** は、設定ファイルと JavaScript で動かす名前変換スクリプトです。<br>
デフォルト名を書いた設定ファイルとJavaScriptをアップロードし、各ページで読み込んで使用します。<br>
夢小説や名前変換小説などに使用することが出来ます。

指定した範囲から文字を読み取り、設定ファイルに沿って変換していく仕組みです。<br>
JavaScriptがわからなくても、設定ファイルとHTMLの編集だけで名前変換機能を使えます。

> **注意**  
> 本リポジトリはあくまで **バックアップ / アーカイブ** 用として公開しています。<br>
> **最新情報や詳しい使い方は公式サイトをご確認ください：**  
> [Berrycake.js 公式サイト](https://lanama.net/scripts/berrycake/)

<br>

## Berrycake.jsの特徴

- **小説本文に名前専用のタグを埋め込まなくてもOK**  
  指定した範囲を一括で検索・変換します。  
- **スクリプトがHTMLから独立していて管理が容易**  
  設定ファイルはスクリプト本体が自動で読み込みます。  
  HTML にはスクリプトファイルだけを読み込む形です。  
- **他ライブラリやサーバーサイドに依存しません**  
  jQuery や PHP を用意しなくても動きます。  
- **スマホでも動作（例外はあるかも）**  
  登録データは LocalStorage または SessionStorage に保存され、サーバーへ自動送信しません。  
- **カスタム変換にも対応**  
  「な、な、なまえ」「なーまーえ」といった変換なども設定可能です（本文へのタグ追加が必要）。

> 名前変換小説、単語変換小説、夢小説などにどうぞ。  
> デフォルト名が一般的な単語の場合は思わぬ箇所まで置き換えされることがあるため、  
> 回避専用タグによる対策をおすすめします。回避タグは [Berrycake.jsのカスタム変換](Custom.md) をご覧ください。

<br>

## ご利用上の注意

- InternetExplorer 等の一部の環境では動作しません。  
- ファイルのアップロード・タグ打ちなど、ある程度のWebサイトアップロードと編集知識が必要です。  
- 変換対応タグは初期設定で `p, li, ruby, rt, h1, h2, h3, h4, h5, a, th, td, span, div` のどれかで囲んだ文字のみです。<br>
※サポート対象外ですが、変換対応タグはスクリプト本体を編集すれば追加可能です。<br>
タグの追加方法は公式サイトのQ&Aをご覧いただくか、ソースコードのコメントを参照してください。
- **berrycake.js と berrycake_recipe.conf を必ず同じフォルダ** にアップロードしてください。  
- **ID やファイル名のスペルミスに特に注意してください。**  
  わずかな入力ミスでもスクリプトが正しく動作しなくなる場合があります。
- 日本語以外の名前変換はカスタムに対応していません。

<br>

## リポジトリフォルダのファイル

archivesフォルダには以下のものがあります。

- berrycake.X.X.X.zip（Xはバージョン番号）：Berrycake.jsの本体とサンプルファイルのセット
  - berrycake.js：名前変換スクリプト本体のJavaScript
  - berrycake_recipe.conf：デフォルト名の設定ファイル
  - berrycake.html：名前登録ページのHTML
  - sample.html：小説ページサンプルのHTML
  - berrycake.css：各ページの外観を整えているCSS
- wp-berrycake.x.x.x.zip（Xはバージョン番号）：Berrycake.jsをWordPressにインストールするためのZipファイル<br>
WordPressで使いたい場合のみご利用ください。WordPressへのインストール方法は [note（外部サイト）](https://note.com/shimamizuna/n/nf3198db19f6c) で解説しています。 

<br>

## ライセンス

ライセンス（利用条件等）を確認し、同意できる方のみご利用ください。  
日本語版も英語版も内容は同じです。お好きな方をご確認ください。  
[ライセンス](LICENSE.txt)

<br>

## ダウンロード

- このリポジトリのarchivesフォルダ > ファイル名右の「・・・」 > Download
- [Berrycake.js ダウンロード (公式サイト内)](https://lanama.net/scripts/berrycake/)  

<br>

## 使い方（簡易版）

1. **設定ファイル「berrycake_recipe.conf」を編集**  
   例：
   ```
   cake1=実小麦
   cake2=蜜花
   cake3=みこむぎ
   cake4=みつか

   label1=苗字
   label2=名前
   label3=みょうじ
   label4=なまえ
   ```
   - `cake●=` に書かれた部分が「デフォルト名」です。<br>
   ●部分は数字であればいいので10も999も設定可能です。
   - 自動出力フォームを使う場合は `label●=` も追記しておくと、入力欄のラベルとして表示されます。
   - berrycake_recipe.confを上書き保存するときは文字コードを「UTF-8」にしてください。

2. **`berrycake.js` と `berrycake_recipe.conf` を同じ場所にアップロード**  
   たとえば以下のようなディレクトリ構成にしてください:
   ```
   /Webサイトフォルダ/
     ├─ berrycake.js
     ├─ berrycake_recipe.conf
     ├─ berrycake.html
     └─ ...
   ```

3. **名前登録ページ「berrycake.html」でberrycake.jsファイルを読み込み**

    - スクリプトを読み込みます。おすすめはbody終了タグの直前での読み込みです。

      ```html
      <script src="berrycake.js"></script>
      ```

4. **自動出力を使わずに名前登録フォームを自作する場合**

    - 自動出力フォームを使わず、独自デザインや構造でフォームを作りたい場合は、下記のように `input` や `button` を手動で配置してください。
    - **入力欄（inputタグ）**  
      - `id="cake●"` のように、設定ファイルの `cake●=` と同じ数字を合わせます。  
      - デフォルト値を入れたい場合は `value="初期値"` を追加します。

      ```html
      苗字 <input type="text" id="cake1" value="">
      名前 <input type="text" id="cake2" value="">
      みょうじ <input type="text" id="cake3" value="">
      なまえ <input type="text" id="cake4" value="">
      ```

    - **登録ボタン / 一時登録ボタン / 削除ボタン**  
      - `id="cakeSet"` が通常の登録ボタン  
      - `id="cakeSession"` が一時登録ボタン（タブを閉じるとデータ削除）  
      - `id="cakeUnset"` が削除ボタン  
      - **ID 名に大文字の混在があるので、スペルミスには十分ご注意ください。**

      ```html
      <button type="button" id="cakeSet">登録</button>
      <button type="button" id="cakeSession">一時登録</button>
      <button type="button" id="cakeUnset">削除</button>
      ```

5. **（オプション）自動出力フォームを使いたい場合**  
   - `<div id="cakeMix"></div>` をページに追加しておくと、設定ファイルに対応した名前登録フォームが自動生成されます。  
   - **サーバーにアップロードしないと自動生成フォームは動きません** のでご注意ください。  

   ```html
   <!DOCTYPE html>
   <html lang="ja">
     <head>
       <meta charset="UTF-8">
       <title>Berrycake Form</title>
     </head>
     <body>

       <!-- この部分にフォームが自動生成される -->
       <div id="cakeMix"></div>

       <!-- 変換範囲 -->
       <div id="berrycake">
         <p>登録名は実小麦蜜花（みこむぎみつか）です。</p>
         <p>小説の主人公はこの名前で変換されます。</p>
       </div>

       <script src="berrycake.js"></script>
     </body>
   </html>
   ```
  
6. **小説ページで変換範囲を設定**  
   - スクリプトを閉じタグ直前で読み込みます。  
   - `<div id="berrycake">` で囲んだ部分が変換対象になります。  

   ```html
   <!DOCTYPE html>
   <html lang="ja">
     <head>
       <meta charset="UTF-8">
       <title>Berrycake Test Page</title>
     </head>
     <body>

       <!-- 変換範囲 -->
       <div id="berrycake">
         <p>実小麦蜜花（みこむぎみつか）は今日も元気です。</p>
         <p>彼女は歌いながらベリーケーキを焼き、ベリーケーキタワーを作っています。</p>
       </div>

       <!-- スクリプト読み込み -->
       <script src="berrycake.js"></script>
     </body>
   </html>
   ```
<br>

これで導入完了です。
特殊な変換は [Berrycake.jsのカスタム変換](Custom.md) をご覧ください。

## 免責事項

利用により生じたいかなる損害・トラブルに対しても、著作者および関係者は一切の責任を負いません。  
あらかじめご了承ください。

<br>

---

上記の内容はあくまで簡易説明です。詳しい解説公式サイト [Berrycake.js 公式サイト](https://lanama.net/scripts/berrycake/) をご確認ください。
