# 日本語版『TeX Live ガイド』

TeX Live の公式ガイド ([HTML](https://www.tug.org/texlive/doc/texlive-en/texlive-en.html), [PDF](https://www.tug.org/texlive/doc/texlive-en/texlive-en.pdf)) の日本語翻訳プロジェクトです．全編の翻訳・執筆が完了し，TeX Live 2020 収録を目指して現在校正作業中です．プレビュー版 PDF は下記リンクに置いてあります：

* <https://wtsnjp.com/pdf/texlive-ja.pdf>

## 翻訳方針

日本語版『TeX Live ガイド』は，以下のような方針で作成しています．

* 現時点では，日本語ガイドは PDF 版のみをサポートする予定
* 意訳を厭わず，なるべく読みやすい翻訳を目指す
* 原版の翻訳内容に加えて，いくらか日本語 TeX に特有の事情を追加
* 文体は敬体で統一する．ただし，敬語は原則として丁寧語のみを使用

## 本リポジトリに含まれるファイル

* `texlive-ja.tex`: 日本語版『TeX Live ガイド』のソース
* `texlive-ja.sty`: `tex-live.sty` を日本語版用に改造したスタイルファイル
* `feedback.txt`: 英語版へのフィードバック

## ビルド方法

日本語版『TeX Live ガイド』は upLaTeX 文書です．通常の `uplatex` + `dvipdfmx` を用いた手順で PDF を生成できます．著者は拙作ビルドツール [llmk](https://github.com/wtsnjp/llmk) を用いてビルドしています：

```
$ llmk texlive-ja.tex
```

なお，本リポジトリには画像データなど全言語版に共通の素材は含まれていません．ビルドを通すためには，適宜 [texlive-common](https://www.tug.org/texlive/doc/texlive-common/) をダウンロードして  `texlive-ja.tex` と同じ階層に配置してください．

## ライセンス

原版に合わせ，本翻訳ドキュメントもパブリックドメインとします．

---

Takuto ASAKURA ([wtsnjp](https://twitter.com/wtsnjp))
