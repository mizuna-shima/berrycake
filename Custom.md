# Berrycake.js [Custom] - カスタム変換

**Berrycake.js** には、基本の名前変換のほかにカスタム変換機能があります。  
カスタム用のタグや class を活用することで、以下のような特殊な変換を行うことができます。

> **注意**  
> ここに掲載されている情報は**バックアップ / アーカイブ**用として公開しているものです。  
> **最新情報や詳しい使い方は公式サイトをご確認ください：**  
> [Berrycake.js 公式サイト](https://lanama.net/scripts/berrycake/)

---

## 目次

- [変換回避](#no_cake)
- [ひらがな→カタカナ変換](#custom_kana)
- [カタカナ→ひらがな変換](#custom_hira)
- [省略表現（な）](#custom_short)
- [詰まり表現（な、な、なまえ）](#custom_stutter)
- [区切り表現（な……ま……え）](#custom_pause)
- [母音のばし表現（みょうじいいい）](#custom_vowel)

<br>

## カスタム変換のポイント・注意事項

- カスタム変換では**特殊なタグ**をピンポイントで使用します  
- **変換回避**は別として、カスタム用タグ内には「デフォルト名」をそのまま入れる必要があります  
- カスタム用タグを埋め込んだ文字は、**未登録**の状態でもカスタムが適用されます  
- ここで紹介するタグはすべて**変換範囲の中**に記載してください（参考：[登録名の変換範囲を設定](../#target)）

<br>

## <span id="no_cake">変換回避</span>

### class="no_cake"

- `class="no_cake"` のタグ（例：`<span>`）で囲むと、タグ内の文字は変換されなくなります。  
- 例：デフォルト名が「パン」だと「パンダ」まで変換されてしまう場合、このタグで「パンダ」を変換回避できます。

```html
<span class="no_cake">パンダ</span>
```

`<span>` 以外にも `<p>` や `<h1>` などでも回避できます。  
デフォルト名が日常的に使用される単語の場合に便利です。

<br>

## <span id="custom_kana">ひらがな→カタカナ変換</span>

### class="cake_custom_kana"

- `class="cake_custom_kana"` のタグ内の**ひらがな**が、表示時に**カタカナ**へ変換されます。  
- ひらがな以外はそのままです。  
- 他のカスタムクラスと同時指定が可能です。

**例：** なまえ → ナマエ

```html
<span class="cake_custom_kana">なまえ</span>
```

**例：** しゅじんこう → シュジンコウ

```html
<span class="cake_custom_kana">しゅじんこう</span>
```

<br>

## <span id="custom_hira">カタカナ→ひらがな変換</span>

### class="cake_custom_hira"

- `class="cake_custom_hira"` のタグ内の**カタカナ**が、表示時に**ひらがな**へ変換されます。  
- カタカナ以外はそのままです。  
- カタカナで呼ばれることが多い名前を、特定の場面だけひらがな表記にしたいときなどにどうぞ。

**例：** ナマエ → なまえ

```html
<span class="cake_custom_hira">ナマエ</span>
```

<br>

## <span id="custom_short">省略表現（な）</span>

### class="cake_custom_first"

- `class="cake_custom_first"` で囲んだ文字列の、先頭1文字分だけを表示します。  
- 「しゅ」「きょ」などの拗音や長音符は1文字として扱います。

**例：** なまえ → な

```html
<span class="cake_custom_first">なまえ</span>
```

<br>

### class="cake_custom_num_●● (02～10)

- `cake_custom_num_02`～`cake_custom_num_10` を併用すると、最大文字数が指定できます。  
- たとえば `cake_custom_first cake_custom_num_02` なら先頭2文字を表示。  
- 文字数が指定より短い場合はそのまま全部表示します。

**例：** しゅじんこう → しゅじ（先頭2文字）

```html
<span class="cake_custom_first cake_custom_num_02">しゅじんこう</span>
```

<br>

## <span id="custom_stutter">詰まり表現（な、な、なまえ）</span>

### class="cake_custom_fold"

- `class="cake_custom_fold"` で囲んだ文字の**最初の1文字**を「、」付きで表示します。  
- 拗音や長音符も最初の文字に含めます。  

**例：** なまえ → な、

```html
<span class="cake_custom_fold">なまえ</span>
```

<br>

### class="cake_custom_num_●● (02～10)

- `cake_custom_fold cake_custom_num_02` のように併用すると、詰まり回数を指定できます。  
- たとえば2回なら「な、な、」が表示されます。

**例：** なまえ → な、な、

```html
<span class="cake_custom_fold cake_custom_num_02">なまえ</span>
```

<br>

## <span id="custom_pause">区切り表現（な……ま……え）</span>

### class="cake_custom_split"

- `class="cake_custom_split"` で囲んだ文字を、一文字ずつ「……」などで区切って表示します。  
- 拗音や長音符は前の文字と一緒に区切ります。  

**例：** なまえ → な……ま……え

```html
<span class="cake_custom_split">なまえ</span>
```

<br>

### class="cake_custom_symbol_●● (01～20)

- `cake_custom_symbol_01`～`cake_custom_symbol_20` を併用すると、区切り記号を変更できます。  
- 01は「……」、02は「ー」、03は「――」など。  
- 詳細は下記の一覧を参照してください。

| 表示 | 補足           | class                  |
|:----:|:--------------:|:-----------------------|
| ……   | デフォルト     | cake_custom_symbol_01  |
| ー    |                | cake_custom_symbol_02  |
| ――   |                | cake_custom_symbol_03  |
| 〰〰  |                | cake_custom_symbol_04  |
| 〜    |                | cake_custom_symbol_05  |
| ！    |                | cake_custom_symbol_06  |
| ！␣  | ！＋スペース   | cake_custom_symbol_07  |
| 、   |                | cake_custom_symbol_08  |
| 。   |                | cake_custom_symbol_09  |
| ・   |                | cake_custom_symbol_10  |
| ,    | 半角           | cake_custom_symbol_11  |
| ，   | 全角           | cake_custom_symbol_12  |
| ☆    |                | cake_custom_symbol_13  |
| ☆␣   | ☆＋スペース    | cake_custom_symbol_14  |
| ★    |                | cake_custom_symbol_15  |
| ★␣   | ★＋スペース    | cake_custom_symbol_16  |
| ♡    |                | cake_custom_symbol_17  |
| ♡␣   | ♡＋スペース    | cake_custom_symbol_18  |
| ♪    |                | cake_custom_symbol_19  |
| ♪␣   | ♪＋スペース    | cake_custom_symbol_20  |

<br>

## <span id="custom_vowel">母音のばし表現（みょうじいいい）</span>

### class="cake_custom_vowel"

- `class="cake_custom_vowel"` は、タグ内の文字列の最後がひらがなorカタカナだった場合、その**母音**を表示します。  
- 拗音・濁音も「あいうえお」のどれかに変換されます。  
- 「ん」「ン」「ー」で終わる文字はそのまま、「漢字」は空文字になります。

**例：** みょうじ → い

```html
<span class="cake_custom_vowel">みょうじ</span>
```

<br>

### class="cake_custom_vowel_min"

- `class="cake_custom_vowel_min"` は、上記の小さい母音版（例：ぁぃぅぇぉ）です。  
- みょうじ → ぃ

```html
<span class="cake_custom_vowel_min">みょうじ</span>
```

<br>

### class="cake_custom_num_●● (02～10)

- `cake_custom_vowel` や `cake_custom_vowel_min` と併用可能。  
- 繰り返し回数を指定すると、その母音を繰り返して表示します。

**例：** みょうじ → いいいいい（5回繰り返し）

```html
<span class="cake_custom_vowel cake_custom_num_05">みょうじ</span>
```

---

以上、Berrycake.js のカスタム変換機能についてまとめました。  
組み合わせ次第で、個性的な表現が可能です。もしよろしければ感想や使い方のご報告などお待ちしています。

  
