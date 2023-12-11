======================================================================
YAML 学習ノート
======================================================================

Jekyll や GitHub Actions など、構成ファイルを YAML 形式で記述する機会が増えてき
ている。人間が書きやすい書式ということだが、私が最初これを編集したときにコレク
ション値の記述法に混乱して当惑した記憶がある。そこでノートを取ろうとしたのだが、
確認すると世の中にすでに良い記事があり、それらをすぐに参照できるようにしておくの
が最善と判断した。

.. contents::

教材
======================================================================

教材が示す YAML コード片を後述の YAML Viewer に与えながら構文の癖を理解すると良
いようだ。YAML のバージョンがそこそこ重要だ。

`YAML Tutorial <https://www.tutorialspoint.com/yaml/index.htm>`__
   Tutorials Point によるチュートリアル。一部、Viewer を通らないコードがあるが、
   少しの修正で整形式になる場合がある。こういう修正が学習になる。

`YAML Tutorial: Everything You Need to Get Started in Minutes | Cloudbees Blog <https://www.cloudbees.com/blog/yaml-tutorial-everything-you-need-get-started>`__
   Python で YAML を扱う方法を述べている。コードが少々壊れているので読者が直す。
   これも学習だ。

   .. code:: python

      #!/usr/bin/env python

      from yaml import load
      try:
          from yaml import CLoader as Loader
      except ImportError:
          from yaml import Loader

      if __name__ == '__main__':
          with open('foo.yaml', 'r') as stream:
              dictionary = load(stream, Loader)
              for key, value in dictionary.items():
                  print(f"{key}: {value}")

   上位互換スクリプトである二つ目の ``load_all`` のほうも同様に修正すれば動作する。

`YAML Tutorial: A Complete Language Guide with Examples <https://spacelift.io/blog/yaml>`__
   叙述がスマートな感じがして安心して読める。スキーマの概念をよく説明できてい
   る。

* `Mastering YAML: A Comprehensive Guide To YAML files <https://saarthakmaini.hashnode.dev/mastering-yaml-a-comprehensive-guide-to-yaml-files>`__
* `Mastering YAML Files: A Step-by-Step Guide <https://www.noobgeek.in/blogs/mastering-yaml-files-a-step-by-step-guide>`__

ツール
======================================================================

* `learn-yaml - Visual Studio Marketplace <https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-yaml>`__
* `YAMLlint - The YAML Validator <https://www.yamllint.com/>`__

`Best YAML Viewer Online <https://jsonformatter.org/yaml-viewer>`__
   左ペインに YAML を入力すると右ペインにツリーを出力するオンラインサービス。き
   わめて有用。
`json2yaml.com <https://www.json2yaml.com/>`__
   左ペインに JSON を入力すると右ペインに等価 YAML を出力するオンラインサービス。

* `Online YAML Parser <https://yaml-online-parser.appspot.com/>`__
* `mikefarah/yq: yq is a portable command-line YAML, JSON, XML, CSV, TOML and properties processor <https://github.com/mikefarah/yq>`__
* `pyyaml.org <https://pyyaml.org/>`__

仕様
======================================================================

* `The Official YAML Web Site <https://yaml.org/>`__
