# 日本語版『TeX Liveガイド』

TeX Live の公式ガイド（[HTML](https://www.tug.org/texlive/doc/texlive-en/texlive-en.html), [PDF](https://www.tug.org/texlive/doc/texlive-en/texlive-en.pdf)）の日本語版制作プロジェクトです。ビルド済みPDFは下記リンクに置いてあります：

* TeX Live版：<https://tug.org/texlive/doc/texlive-ja/texlive-ja.pdf>
* プレビュー版：<https://wtsnjp.com/pdf/texlive-ja.pdf>

## 翻訳方針

日本語版『TeX Liveガイド』は、以下のような方針で作成されています。

* このプロジェクトではPDF版のみをサポートする
* 意訳を厭わず、なるべく読みやすい翻訳を目指す
* 原版の翻訳内容に加えて、いくらか日本語 TeX に特有の事情を追加
* 文体は敬体で統一する。ただし、敬語は原則として丁寧語のみを使用

## 本リポジトリに含まれるファイル

* `texlive-ja.tex`: 日本語版『TeX Liveガイド』のソース
* `texlive-ja.sty`: `tex-live.sty`を日本語版用に改造したスタイルファイル

## ビルド方法

日本語版『TeX Liveガイド』はupLaTeX文書です。通常の`uplatex` + `dvipdfmx`を用いた手順でPDFを生成できます。著者は拙作ビルドツール[llmk](https://github.com/wtsnjp/llmk)を用いてビルドしています：

```
$ llmk texlive-ja.tex
```

なお、本リポジトリには一部の画像データなど他言語版と共通の素材は含まれていません。ビルドを通すためには、[texlive-common](https://www.tug.org/texlive/doc/texlive-common/), [texlive-en](https://www.tug.org/texlive/doc/texlive-en/)ディレクトリが TeX から見えるようになっている必要があります（例えば`texlive-ja.tex`と同じ階層に配置すればOKです）。

## ライセンス

原版に合わせ、本翻訳ドキュメントもパブリックドメインとします。

---

Takuto Asakura ([wtsnjp](https://twitter.com/wtsnjp))
