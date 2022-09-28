======================================================================
DeepL Translator 利用ノート
======================================================================

本稿では無料版 `DeepL Translator`_ （以下、単に DeepL と記す）の導入例、基本的な
使用例、応用例について記す。後述するように DeepL のインターフェイスは複数存在する。
特に断りのない限り、Windows 版 DeepL の情報を述べる。

.. contents::

機能
======================================================================

注目する機能は次のとおり：

1. 英語から日本語への翻訳
2. 英語以外の外国語から日本語への翻訳
3. 日本語から英語への翻訳

体感では、機能 1. が私の DeepL 使用内訳の 99.9 パーセントを占める。機能 2. は
YouTube のコメント欄、チャット欄のメッセージを処理するのに利用している。機能 3.
は海外からのメールの返信やコミットログなど、どうしても英語を書かなければいかない
場合に現れる。

これらの状況を DeepL 一丁ですべて捌ける。このツールを導入しない理由はない。

インストール
======================================================================

本節では利用する可能性のある DeepL 各種をインストールする手順を簡単に記す。正確
に言うと、インストール手順自体はどれも容易なので、サービス一覧を記録するという目
的意識だ。

* Web ページ版
* Google Chrome 拡張機能版
* Windows 版
* Android 版

Web ページ版
----------------------------------------------------------------------

Web ページなので、インストールというよりはブラウザーのブックマークリストに
`DeepL Translator`_ の URL を追加するだけだ。

人に DeepL の翻訳能力を試させるには、この URL を教えるのが話が早いだろう。

Google Chrome 拡張機能版
----------------------------------------------------------------------

2022 年 5 月頃から Web ブラウザー Google Chrome に拡張機能版を導入するという選択
肢が増えた。インストール手順は次のとおり：

1. `Chrome ウェブストア <https://chrome.google.com/webstore/detail/deepl-translate-reading-w/cofdbpoegempjloogbagkncekinflcnj>`__ を開く。
2. :guilabel:`Chrome に追加` ボタンを押す。

Windows 版
----------------------------------------------------------------------

Windows 版 DeepL をインストールする有望な方法は複数ある。現況に最適な方法を採ることだ。

* 公式ページからインストーラーをダウンロードして展開する。
* Microsoft Store からインストールする。
* Windows Package Manager (:program:`winget`) でコマンド実行によりインストールする。

  .. code:: doscon

     > winget install -e --id DeepL.DeepL

現代の Windows ソフトウェアはインストール方法によってアップグレード方法が変わっ
てくる可能性があるが、どの方法でも更新は手動になりがちだ。最適なインストール方法
の選択をそこまで気にする必要はない。

Android 版
----------------------------------------------------------------------

2022 年 3 月頃から `Android 版 <https://play.google.com/store/apps/details?id=com.deepl.mobiletranslator&referrer=utm_source%3Ddeepl%26utm_campaign%3DpageID408-button%26anid%3Dadmob>`__ が利用可能になっている。
携帯電話の画面を開いて Google Play からインストールする。

アンインストール
======================================================================

本節で述べることは何もない。

DeepL をシステムからアンインストールすることはないだろう。ディスク容量が逼迫し
ているとかであれば、もっと保全優先度の低いアプリケーションを削除するべきだ。

利用
======================================================================

TBW

.. _DeepL: https://www.deepl.com/translator
.. _DeepL Translator: https://www.deepl.com/translator