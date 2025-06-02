# minibook

[![CI][badge]](https://github.com/showa-yojyo/minibook/actions/workflows/ci.yml)

公に見られる場所に置く文書ではあるが、個人的な用途で書いたものなのでこの
`README` も日本語で書く。

## 概要

このリポジトリーの目的は次の二つ：

1. [別プロジェクト][note]の Sphinx 文書のビルドを簡易的に再現する。
2. GitHub の動作各種 (Actions, Pages, etc.) を施行する。

## プロジェクトサイト

GitHub に置いてある次のページが当リポジトリーを含むプロジェクト拠点の URL だ：

* 当プロジェクト
  * [showa-yojyo/minibook](https://github.com/showa-yojyo/minibook/): 本プロジェクト。
  * [GitHub Pages](https://showa-yojyo.github.io/minibook/): ビルド成果物。
* [読書ノート][note]: 親プロジェクト。

## ビルド

ビルド環境や手法など、随時更新。

## リポジトリー構造

[親プロジェクト][note]のリポジトリー構造を規模を縮小して模倣する。

```raw
.
├── .git
├── .github
│   ├── ISSUE_TEMPLATE
│   └── workflows
├── .vscode
├── build
│   ├── doctrees
│   │   ├── (subdir1)
│   │   ├── (subdir2)
│   │   └── (...)
│   └── html
│       ├── _images
│       ├── _static
│       ├── (subdir1)
│       ├── (subdir2)
│       └── (...)
└── source
    ├── _extension
    ├── _images
    ├── _include
    ├── _static
    ├── _templates
    ├── (subdir1)
    ├── (subdir2)
    └── (...)
```

ルート直下には `Makefile` を含むプロジェクト管理に関係するファイルを置く。

ディレクトリー `.github` には GitHub 固有の管理ファイルを置く。

* `.github/ISSUE_TEMPLATE` には Issues 画面で課題を報告するときの文面の雛形を与える
* `.github/workflows` には GitHub Actions ワークフロー定義ファイルを置く。

ディレクトリー `build` 以下は `.gitignore` によりバージョン管理外だが、
`build/html` 以下は成果物であり重要だ。

ディレクトリー `source` 以下は親プロジェクトから採取した Sphinx 文書原稿ファイルを置く場だ。
アセットは画像を除いてすべて流用する方針だ。

## 協力者

協力募集およびクレジットは[親プロジェクト][note]で行う。

## 告知

動作試行を中心とするという当プロジェクトの性質上、行わない。

## メーリングリスト

当プロジェクトの性質上、設けない。

[badge]: <https://github.com/showa-yojyo/minibook/actions/workflows/ci.yml/badge.svg>
[MkDocs]: <https://www.mkdocs.org/>
[note]: <https://showa-yojyo.github.io/notebook/>
