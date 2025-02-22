---
$title: スタイルとレイアウト
---
[TOC]

AMP HTML のスタイルとレイアウトには、通常の HTML と同じように CSS を使用します。

ただし AMP の場合は、パフォーマンスと操作性の関係で、一部の CSS が制限されています。一方、レスポンシブ デザイン機能は、 [プレースホルダとフォールバック]({{g.doc('/content/docs/design/responsive_amp/placeholders.md', locale=doc.locale).url.path}})、[srcset による高度な画像読み込み](/ja/docs/design/responsive/art_direction.html)、[レイアウト属性](/ja/docs/design/responsive/control_layout.html) などの機能で拡張されているため、要素の表示方法を細かく制御できます。

ヒント: AMP で要素をレスポンシブにするのはとても簡単で、`layout="responsive"` を追加するだけです。AMP でのレスポンシブ デザインについて詳しくは、[レスポンシブな AMP ページを作成する](/ja/docs/design/responsive/responsive_design.html)をご覧ください。

{{ youtube('y6kA3u3GIws', 480, 270, caption='初めて AMP を利用するにあたっての課題など、UpperQuad における AMP プロジェクトでのサイト再設計に関する話をご覧になれます。') }}

## ページにスタイルを追加する

すべての CSS は、ドキュメントの `<head>` の `<style amp-custom>` タグ内に追加します。次の例をご覧ください。

[sourcecode:html]
<!doctype html>
<head>
...
<style amp-custom>
/* any custom styles go here. */
body {
background-color: white;
}
amp-img {
border: 5px solid black;
}

amp-img.grey-placeholder {
background-color: grey;
}
</style>
...
</head>
[/sourcecode]

重要: ページ内の `<style amp-custom>` タグが 1 つのみであることを確認してください。AMP では、このタグを複数使用することはできません。

一般的な CSS プロパティを使用し、クラスセレクタまたは要素セレクタでコンポーネントのスタイルを定義します。次に例を示します。

[sourcecode:html]
<body>
<p>Hello, Kitty.</p>
<amp-img
class="grey-placeholder"
src="https://placekitten.com/g/500/300"
srcset="/img/cat.jpg 640w,
/img/kitten.jpg 320w"
width="500"
height="300"
layout="responsive">
</amp-img>
</body>
[/sourcecode]

重要: 使用するスタイルが AMP でサポートされているかどうかを確認してください。一部のスタイルは、パフォーマンス上の理由でサポートされていません（[サポートされる CSS]({{g.doc('/content/docs/design/responsive_amp/style_pages.md', locale=doc.locale).url.path}}) もご覧ください）。

## 要素をレスポンシブにレイアウトする

`width` 属性と `height` 属性を使用して、表示されるすべての AMP 要素のサイズと位置を指定します。これらの属性を指定することで、必然的に要素のアスペクト比が決まり、コンテナによる拡大、縮小が可能になります。

レイアウトはレスポンシブに設定してください。これにより、要素の幅がコンテナ要素に合わせて調整され、width 属性と height 属性で決まったアスペクト比に応じて高さが調整されます。

参照: 詳しくはこちら: [AMP でサポートされるレイアウト]({{g.doc('/content/docs/design/responsive_amp/control_layout.md', locale=doc.locale).url.path}})

## プレースホルダとフォールバックを提供する

プレースホルダとフォールバックがビルトイン サポートされていますので、ユーザーに対して何もない画面が表示されることはありません。

参照: 詳しくはこちら: [プレースホルダとフォールバック]({{g.doc('/content/docs/design/responsive_amp/placeholders.md', locale=doc.locale).url.path}})

## 高度な画像読み込み

AMP では、`srcset` 属性と `sizes` 属性の両方がサポートされているため、どの場合にどの画像を読み込むかを細かく制御できます。

参照: 詳しくはこちら: [srcset と sizes による高度な画像読み込み]({{g.doc('/content/docs/design/responsive_amp/art_direction.md', locale=doc.locale).url.path}})

## スタイルとレイアウトを検証する

AMP 検証ツールを使用すると、ページの CSS やレイアウトの値をテストできます。

AMP 検証ツールは、ページの CSS が上限の 50,000 バイトを超えていないか、許可されていないスタイルはないか、ページのレイアウトがサポートされているか、形式は正しいか、などを検証します。チェックできるエラーの一覧については、[スタイルとレイアウトのエラー](/ja/docs/troubleshooting/validation_errors.html#style-and-layout-errors)をご覧ください。

CSS が上限の 50,000 バイトを超えた場合、コンソールには次のように表示されます。

<amp-img src="/static/img/docs/too_much_css.png" width="1404" height="334" layout="responsive"></amp-img>

参照: 詳細はこちら: [AMP ページの検証と修正]({{g.doc('/content/docs/fundamentals/validate.md', locale=doc.locale).url.path}})
