```python
import urllib.request
import requests
from bs4 import BeautifulSoup
import sys
import os
import re
import pandas as pd
import random
import time
from datetime import date, timedelta
```


```python
webpage_response = requests.get('https://ja.wikipedia.org/wiki/python')
webpage = webpage_response.content
soup = BeautifulSoup(webpage, "html.parser")
```


```python
text = soup.get_text()
```


```python
for script in soup(["script", "style"]):
    script.decompose()
```


```python
lines= [line.strip() for line in text.splitlines()]
```


```python
text="\n".join(line for line in lines if line)
```


```python
print(text)
```

    Python - Wikipedia
    Python
    出典: フリー百科事典『ウィキペディア（Wikipedia）』
    ナビゲーションに移動
    検索に移動
    この項目では、プログラミング言語について説明しています。その他の用法については「パイソン (曖昧さ回避)」をご覧ください。
    Python
    Pythonのロゴパラダイム
    関数型プログラミング、オブジェクト指向プログラミング、動的計画法、命令型プログラミング、マルチパラダイムプログラミング 登場時期
    1991年 (30年前) (1991)開発者
    Pythonソフトウェア財団、グイド・ヴァンロッサム 最新リリース
    3.9.5  - 2021年5月3日 (2か月前) (2021-05-03)[1] [±]型付け
    強い型付け 動的型付け主な処理系
    CPython, PyPy, IronPython, Jython方言
    Cython, RPython, Stackless Python影響を受けた言語
    ALGOL 68、ABC、Modula-3、C言語、C++、Perl、Java、LISP、Haskell、APL、CLU、Dylan、Icon、Standard ML 影響を与えた言語
    Boo, Cobra, D, F#, Falcon, Go, Groovy, JavaScript[2], Ruby[3], Perl, Swiftプラットフォーム
    クロスプラットフォーム ライセンス
    Python Software Foundation License ウェブサイト
    www.python.org 拡張子
    py、pyc、pyd、pyo、pyw、pyz、pyi テンプレートを表示
    Python（パイソン）はインタープリタ型の高水準汎用プログラミング言語である。グイド・ヴァン・ロッサムにより創り出され、1991年に最初にリリースされたPythonの設計哲学は、有意なホワイトスペース(オフサイドルール)の顕著な使用によってコードの可読性を重視している。その言語構成とオブジェクト指向のアプローチは、プログラマが小規模なプロジェクトから大規模なプロジェクトまで、明確で論理的なコードを書くのを支援することを目的としている。
    Pythonは動的に型付けされていて、ガベージコレクションされている。構造化（特に手続き型）、オブジェクト指向、関数型プログラミングを含む複数のプログラミングパラダイムをサポートしている。Pythonは、その包括的な標準ライブラリのため、しばしば「バッテリーを含む」言語と表現される[† 1]。
    Pythonは1980年代後半にABC言語の後継として考案された。2000年にリリースされたPython 2.0では、リスト内包表記や参照カウントによるガベージコレクションシステムなどの機能が導入された。
    2008年にリリースされたPython 3.0は、完全な下位互換性を持たない言語の大規模な改訂であり、Python 2のコードの多くはPython 3では変更なしには動作しない。
    Python 2言語は2020年に正式に廃止され（当初は2015年予定）、"Python 2.7.18はPython 2.7の最後のリリースであり、したがってPython 2の最後のリリースである "[4]とされている。これ以上のセキュリティパッチやその他の改善はリリースされない[† 2]。Python 2が終了したことで、サポートされるのはPython 3.5.x以降[5]のみとなる。
    Pythonのインタプリタは多くのOSに対応している。プログラマーのグローバルコミュニティは、無料のオープンソース [† 3] リファレンス実装であるCPythonを開発および保守している 。非営利団体であるPythonソフトウェア財団は、PythonとCPythonの開発のためのリソースを管理・指導している。
    目次
    1 概要
    1.1 特徴
    1.2 動作する計算機環境 (platform)
    1.3 実装
    1.4 ライセンス
    2 言語の機能
    2.1 構文
    2.2 データ型
    2.3 オブジェクト指向プログラミング
    2.4 ライブラリ
    2.5 多言語の扱い
    3 エコシステム
    3.1 パッケージ
    4 利用
    4.1 データサイエンスおよび数値計算用途
    4.2 Webアプリケーション用途
    4.3 システム管理およびグルー言語用途
    4.4 教育用
    5 歴史
    5.1 0.9x
    5.2 1.x
    5.3 2.x
    5.4 3.x
    5.5 Python の時系列
    5.6 Pythonに影響を与えた言語
    6 Webアプリケーションフレームワーク
    7 パッケージ管理システムおよびディストリビューション
    8 注釈
    9 出典
    9.1 一次文献
    10 関連項目
    11 学習用図書の例
    12 外部リンク
    概要[編集]
    特徴[編集]
    Pythonはインタプリタ上で実行することを前提に設計している。以下の特徴をもっている:
    動的な型付け
    ガベージコレクション
    マルチパラダイム
    モジュール・クラス・オブジェクト等の言語の要素が内部からアクセス可能であり、リフレクションを利用した記述が可能。
    動作する計算機環境 (platform)[編集]
    Pythonの最初のバージョンはAmoeba上で開発された。のちに多くの計算機環境上で動作するようになった。
    Windows[6], Windows CE（9x系およびNT系は最新版、Windows 3.1およびMS-DOSは旧版のみ）
    Macintosh (Classic Mac OSおよびmacOSともに)
    iOS Pythonista for iOS (omz:software)
    Android Pydroid3 for Android (IIEC)
    各種UNIX
    Linux (Linux Standard Base3.2で標準仕様となった)
    Plan 9 (Python 3.xは未移植)
    PalmOS
    S60
    Javaプラットフォーム (Jython)
    .NET Frameworkプラットフォーム (IronPython)
    実装[編集]
    Pythonには複数の実装が存在する。
    CPython - 作者によってC言語で書かれたバージョン。通常「Python」といえばこのCPythonを指す。
    Stackless Python - Cスタックを使わずに独自のスタック（Pythonスタック）で実装したもの。
    Unladen Swallow - GoogleのチームによるPythonの実装
    Jython - Java仮想マシン上に移植したもの。PythonからJavaのライブラリを使うことができる。
    IronPython - .NET Framework/Monoで動作するPython。C#で実装されている。.NET Frameworkのライブラリを使うことができる。動的言語ランタイム上に構築されているため、既存の.NETアプリケーションへマクロ言語として搭載することも可能となっている。
    PyPy - Python (RPython) によるPythonの実装
    Psyco - CPython向けのJITコンパイラ
    PyMite - 組み込み向けの実装、AVRなどに対応。
    tinypy - 同じく組み込み向けの実装。ソースコードが 64 kB未満と非常に軽量なことが謳われている。
    MicroPython - 組み込み向けの実装。256 kB以上のフラッシュを推奨。
    Pyodide - WebAssembly向けの実装[※ 1]
    ライセンス[編集]
    Python のリリースは全てオープンソースであり、PSF (Python Software Foundationライセンス)として配布されている。これはGPL互換であるが、GPLと異なり、変更したバージョンを配布する際に変更をオープンソースにしなくてもよい。
    言語の機能[編集]
    Pythonには、読みやすく、それでいて効率もよいコードをなるべく簡単に書けるようにするという思想が浸透しており、Pythonコミュニティでも単純で簡潔なコードをよしとする傾向が強い[† 4]。
    Pythonの本体は、ユーザがいつも必要とする最小限の機能のみを提供する。基本機能以外の専門機能や拡張プログラムはインターネット上にライブラリとして提供されており、別途ダウンロードして保存し、必要なツールはこのツールキットからその都度呼び出して使用する[† 5]。
    またPythonでは、Perlの「やり方は一つじゃない」という哲学[7]とは逆に、ある動作をさせる方法は、基本的に1通りしかないように作られている。そのためPythonのプログラムは、誰が書いてもだいたいどれも同じようなコードになり、作成者以外が見ても動作を把握しやすい。また、Pythonではプログラムの文書化（ソフトウェアドキュメンテーション）が重視されており、言語の基本機能の一部となっている。
    機械学習やAI開発、自動化ツールの作成やスクレイピングも可能な言語である。
    構文[編集]
    インデントが意味を持つ「オフサイドルール」が特徴的である。
    以下に、階乗 (関数名: factorial)を題材にC言語と比較した例を示す。
    Pythonのコード:
    def factorial(x):
    if x == 0:
    return 1
    else:
    return x * factorial(x - 1)
    わかりやすく整形されたC言語のコード:
    int factorial(int x) {
    if (x == 0) {
    return 1;
    } else {
    return x * factorial(x - 1);
    }
    }
    この例では、Pythonと整形されたC言語とでは、プログラムコードの間に違いがほとんど見られない。しかし、C言語のインデントは構文規則上のルールではなく、単なる読みやすさを向上させるコーディングスタイルでしかない。そのためC言語では全く同じプログラムを以下のように書くこともできる。
    わかりにくいC:
    int factorial(int x) {
    if(x == 0) {return 1;} else
    {return x * factorial(x - 1); } }
    Pythonではインデントは構文規則として決められているため、こうした書き方は不可能である。Pythonではこのように強制することによって、ソースコードのスタイルがその書き手にかかわらずほぼ統一したものになり、その結果読みやすくなるという考え方が取り入れられている。これについては賛否両論があり、批判的立場の人々からは、これはプログラマがスタイルを選ぶ自由を制限するものだ、という意見も出されている。
    インデントによる整形は、単に「見かけ」だけではなく品質そのものにも関係する。例として次のコードを示す。
    間違えたC:
    if (x > 10)
    x = 10;
    y = 0;
    このコードはC言語の構文規則上は問題無いが、インデントによる見かけのifの範囲と、言語仕様によるifの実際の範囲とが異なっているため、プログラマの意図が曖昧になる。(前者は"y = 0;"がif文に包含され、後者は"{}"がないため"y = 0;"がif文に包含されない)この曖昧さは、検知しにくいバグを生む原因になる。例としてはApple goto failが挙げられる。
    ソースコードを読む際、多くの人はインデントのような空白を元に整列されたコードを読み、コンパイラのように構文解析しながらソースを読むものではない。その結果、一見しただけでは原因を見つけられないバグを作成する危険がある。
    Pythonではインデントをルールとすることにより、人間が目視するソースコードの理解とコンパイラの構文解析の間の差を少なくすることで、より正確に意図した通りにコーディングすることができると主張されている。
    データ型[編集]
    Pythonのデータは動的に型付けされる。値自身が型を持っており、変数はすべて値への参照である。
    基本的なデータ型として、整数型・多倍長整数型・浮動小数点数型・複素数型・文字列型・Unicode文字列型・論理型、そして関数型がある。多倍長整数型は（メモリの許す限り）無制限の桁数で整数計算が可能である。浮動小数点数型を整数型にキャストすると、小数点以下が切り捨てられる。
    さらに組み込みのコンテナ型として、リスト型、タプル型、辞書型（連想配列）のほか、値の重複を許さない集合型（Python 2.3以降）がある。
    Python 3.x以降では、整数型が多倍長整数型と統合され、従来の文字列型とUnicode文字列型に代わり、バイト列型と文字列型が導入された。
    リスト型および辞書型は内部の値をあとから変えられる（mutable、変更可能）が、タプル型は一度構築したら内部の値は変わらない（immutable、変更不能）。タプル型とリスト型は、多くのプログラミング言語では配列と呼ばれるものに類似している。しかし、Pythonではタプル型は辞書のキーとして使うことができるが、リスト型は内容が変わるため辞書のキーとして使うことはできないという理由から、これら2つの型を区別している。集合型には変更可能なものと変更不能なものの2種類がある。
    多くのオブジェクト指向プログラミング言語と同様、Pythonではユーザが新しく自分の型を定義することも可能である。この場合、組み込み型を含む既存の型を継承して新たな型（クラス）を定義する事も、ゼロから全く新しい型を作り出す事も出来る。
    Pythonは基本的にメソッドや関数の引数に型を指定する必要がない。そのため、ダック・タイピングという、内部で必要とする演算子やメソッドに対応していれば、関数やオブジェクトの設計時点で意図していなかったオブジェクトを引き渡すことも可能である。
    Pythonはガベージコレクションを内蔵しており、参照されなくなったオブジェクトは自動的にメモリから破棄される。CPythonでは、ガベージコレクションの方式として参照カウント方式とマーク・アンド・スイープ方式を併用している。マーク・アンド・スイープ方式のみに頼っている言語では、オブジェクトがいつ回収されるか保証されないので、ファイルのクローズなどをデストラクタに任せることができない。CPythonは参照カウント方式を併用することで、循環参照が発生しない限り、オブジェクトはスコープアウトした時点で必ずデストラクトされることを保証している。なおJythonおよびIronPythonではマーク・アンド・スイープ方式を採用しているため、スコープアウトした時点で必ずデストラクトされることが前提のコードだとJythonやIronPythonでは正しく動かない。
    イテレータを実装するためのジェネレータが言語仕様に組み込まれており、Pythonでは多くの場面でイテレータを使うように設計されている。イテレータの使用はPython全体に普及していて、プログラミングスタイルの統一性をもたらしている。
    オブジェクト指向プログラミング[編集]
    Pythonでは扱えるデータの全てがオブジェクトである。単純な数値といった基本的なデータ型をはじめ、組み込みのコンテナ型、組み込み関数など、これらは全て統一的な継承関係をもつオブジェクトであり「型」をもっている。これらの組み込み型とユーザ定義型は区別されず、組み込み型を継承したクラスを定義できる。上の「データ型」の項で述べたように Pythonは静的な型チェックを持たないため、Javaのようなインターフェイスという言語上の仕組みは必要とされない。
    クラスの継承 (inheritance) メカニズムでは、複数の基底クラスを持つことができ（多重継承）、導出されたクラスでは基底クラスの任意のメソッドをオーバライド（override; 上書き）することが可能である。
    また、オブジェクトには任意のデータを入れることができる。これらのメソッドやデータは、基本的に、すべてpublicであり、virtual（仮想）である。ただし、先頭にアンダースコアをもつメンバをprivateとすることができる。これは単なるマナーであるが、アンダースコアを2つもつ場合は、クラスの外部からメンバの名前を隠された状態（mangle; 難号化）とすることでカプセル化を実現できる。また、利用者定義演算子が機能として用意されておりほとんどの組み込み演算子（算術演算子（arithmetic operator）や添字表記）はクラスインスタンスで使うために再定義することが可能となっている。
    ライブラリ[編集]
    Pythonには「電池付属 ("Battery Included")」という思想があり、プログラマがすぐに使えるようなライブラリや統合環境をあらかじめディストリビューションに含めるようにしている。このため標準ライブラリは非常に充実している。
    正規表現
    OSのシステムコール
    XML処理系
    シリアライゼーション
    HTTP, FTP等の各種通信プロトコル
    電子メールやCSVファイルの処理
    データベース接続 (SQLiteを標準で扱える)
    GUIフレームワーク (Tkinter)
    HTMLのパーサー
    Python自身のコードの構文解析ツール
    サードパーティによるライブラリも豊富に存在する。
    行列演算パッケージの NumPy
    プログラミング数学、科学、工学のための数値解析 SciPy
    データ解析ソフト pandas
    データ処理インタフェース IPython
    グラフ表示ソフト Matplotlib
    描画ソフト  Seaborn
    数式処理機能 SymPy
    データ処理の高速化  PyPy
    Pythonアプリのコンパイルによる高速化 Numba
    機械学習ライブラリ scikit-learn
    深層学習ライブラリ  TensorFlow
    深層学習ライブラリ  PyTorch
    画像処理のための Python Imaging Library
    SDLのラッパである Pygame
    スクレイピングライブラリ Beautiful Soup
    クローリング、スクレイピング用のpythonフレームワーク Scrapy
    離散事象シミュレーション SimPy
    OpenCLへのインタフェース pyOpenCL
    OpenGLへのインタフェース pyOpenGL
    OpenCVへのインタフェース pyOpenCV
    CUDAへのインタフェース   pyCUDA
    3Dグラフィックスやアニメーション VPyyhon
    PyODE
    Cython
    Python(x,y)
    マイナーなものまで含めると多すぎて収拾がつかない。
    Python Package Index (PyPI) と呼ぶ公式のパッケージリポジトリを導入した。
    多言語の扱い[編集]
    当初Pythonでは1バイト単位での文字列型のみ扱い、ひらがな・(全角) カタカナおよび漢字のようなマルチバイト文字をサポートしていなかったが、Python 2.0からはUnicode文字型が新たに導入された[† 6]。
    Python 3.0では、文字列型がバイト列型に、Unicode文字列型が文字列型に変更された。これにより、文字列をPython 3.0で扱う際には後述の変換処理を必ず行う必要がある。ファイル入出力などエンコードを明示しなければ、標準エンコードを用いて暗黙に行われる場合も多い。これにより多言語の扱いを一貫したものにしている。
    Pythonでは文字のエンコードとUnicodeの内部表現を明確に区別している。Unicode文字はメモリ中に保持される抽象的なオブジェクトであり、画面表示やファイルへの入出力の際には変換ルーチン（コーデック）を介して特定のエンコーディングのバイト列表現との間で相互に変換する。また、ソースコード中の文字コードを認識する機能があり、これによって異なる文字コードで書かれたプログラムの動きが異なるという危険を解消している。
    Pythonでは変換ルーチンをモジュールとして追加することで、さまざまなエンコーディングに対応できるようになっている。日本語の文字コード (EUC-JP, Shift_JIS, MS932, ISO-2022-JP) に対応したコーデックも作成されている。Python 2.4からは、日中韓国語用のコーデックが標準でディストリビューションに含まれるようになったため[† 7]、現在では日本語の処理に問題はほとんどなくなった。ただしGUIライブラリであるTkinterや統合開発環境のIDLEは、プラットフォームにもよるが、まだ日本語にきちんと対応していないものもある。
    ソースコードの文字コードは、ASCIIと互換性があり、Pythonが対応しているものを使用する。ソースコードのデフォルトエンコーディングは、Python 3.xではUTF-8[† 8]（ソースコード以外のPython 3のデフォルトエンコーディングは複雑になっている[† 9][† 10]）、Python 2.xではASCIIであるが、デフォルトエンコーディング以外の文字コードを使う場合は、ソースファイルの1行目か2行目に一定の書式でコメントとして記述することになっており[† 11]、しばしば以下のようにEmacsやVimなどのテキストエディタにも認識可能な書式で記述される（次の例は Emacs が認識できる書式）。
    #! /usr/bin/python2
    # -*- coding: utf-8 -*-
    s = '日本語の文字列'
    エコシステム[編集]
    Pythonはパッケージ管理ソフト・レポジトリなどからなるエコシステムを形成している。
    パッケージ[編集]
    ビルドシステム/wheel/インストーラ
    Pythonのパッケージ管理はpip・pipenv・poetryなどのパッケージ管理システムによっておこなわれる。バイナリパッケージのフォーマットにはwheelがあり、これをインタフェースとしてビルドシステムとパッケージ管理システムの分離が可能になっている[† 12]。
    利用[編集]
    「Pythonを使っている製品あるいはソフトウェアの一覧」も参照
    Pythonは全世界で使われているが、欧米の企業でもよく使われている。大企業ではマイクロソフトやAppleなどのパッケージソフトウェア企業をはじめ、Google, Yahoo!, YouTube などの企業も利用している[† 13]。また携帯電話メーカーのノキアでは、S60シリーズでPythonアプリケーションが動く[8]。研究機関では、NASA[† 13]や日本の高エネルギー加速器研究機構[9]でPythonが使われている。
    適応範囲はデータサイエンス、Webプログラミング、GUIベースのアプリケーション、CAD、3Dモデリング、数式処理など幅広い分野に及ぶ。
    データサイエンスおよび数値計算用途[編集]
    NumPy, SciPyなどの高速な数値計算ライブラリの存在により、データサイエンスや科学技術コンピューティングにもよく用いられる。NumPy, SciPyの内部はC言語で書かれているので、動的スクリプト言語の欠点の一つである動作速度の遅さを補っている[10]。Numba を使うと、Python のコードが LLVM に JITコンパイルして利用可能であり、非常に高速な計算ができる。TensorFlow などのライブラリにより GPU 上で高速に計算するライブラリも充実している。
    JetBrains とPythonソフトウェア財団による共同調査によると、2017年10月現在、最も主要な用途は何かというアンケートで、用途の27%がデータサイエンス（そのうち18%がデータ解析、9%が機械学習）である[11]。
    Webアプリケーション用途[編集]
    Django や Flask といったWebアプリケーションフレームワークが充実しているため、Webアプリケーション開発用途にも多く使われている。JetBrains とPythonソフトウェア財団による共同調査によると、2017年10月現在、26%の人が最も主要な用途としてWeb開発を選んだ[11]。
    システム管理およびグルー言語用途[編集]
    スクリプト言語としての特性から、従来Perlやシェルスクリプトが用いられることの多かったシステム管理用のスクリプトとして採用しているOSも複数ある。また、多くの異なる言語で書かれたモジュールをまとめるグルー言語としての利用例も多い。実際、多くの商用アプリケーションで Python は組み込みのスクリプト言語として採用されている。
    JetBrains とPythonソフトウェア財団による共同調査によると、2017年10月現在、9%の人が最も主要な用途としてDevOps, システム管理, 自動化スクリプトを上げた[11]。
    教育用[編集]
    Pythonは教育用の目的で設計されたわけではないが[12]、その単純さから子供が最初に学ぶプログラミングにおける教育用の言語としても利用が増えている。グイド・ヴァンロッサムはPython設計以前に教育用言語であるABCの開発にかかわり、教育用としての利用について期待感を示したこともあり、方針として非技術者向けといった利用を視野に入れているとされることもある[13]。
    私の大好きなPython利用法は、騒ぎ立てずに、言語教育でプログラミングの原理を教えること。それを考えてくれ――次の世代の話だね。-- スラッシュドット・ジャパン『 Guido van Rossum へのインタビュー』
    情報処理推進機構 (IPA) は国家試験の基本情報技術者試験で2020年の春期試験より COBOL を廃止して Python を追加した[14]。
    日本の高等学校情報科「情報Ⅰ」の教員向け研修教材の中で、プログラミング用言語としてPythonが使われている[15]。
    歴史[編集]
    元々はAmoebaの使用言語であるABC言語に例外処理やオブジェクト指向を対応させるために作られた言語である[16]。
    0.9x[編集]
    1991年にヴァンロッサムがPython 0.90のソースコードを公開した。この時点ですでにオブジェクト指向言語の特徴である継承、クラス、例外処理、メソッドやさらに抽象データ型である文字列、リストの概念を利用している。これはModula-3のモジュールを参考にしていた。
    1.x[編集]
    1994年1月、Python 1.0を公開した。主な特徴として関数型言語の基本であるラムダ計算を実装、map関数・reduce関数などを組み込んだ。
    バージョン1.4ではCommon Lispにある機能とよく似たキーワード引数を導入した。また簡易ながら名前修飾を用いたカプセル化も実装した。
    2.x[編集]
    2000年に公開。ガベージコレクションやUnicode、リストを導入した。一躍メジャーな言語となった。多くの機能はHaskellを参考にして導入している。
    2.6以降のバージョンには、2.xから3.xへの移植を助ける「2to3 ツール」と「lib2to3 モジュール」を含んでいる[† 14]。2.7が2.xの最後のバージョンで、2.7のサポートは2020年1月1日までである[† 15]。ただし、サポート終了後に 2.7.18 を2020年4月にリリースし、これが最後の 2.7.x になる。
    バージョン
    リリース日[17]
    サポート期限[18]
    2.0
    2000年10月16日
    2.1
    2001年4月15日
    2.2
    2001年12月21日
    2.3
    2003年7月29日
    2.4
    2004年11月30日
    2.5
    2006年9月19日
    2.6
    2008年10月1日
    2013年10月29日
    2.7
    2010年7月4日
    2020年1月1日
    3.x[編集]
    2008年、長い試験期間を経てPython 3.0が公開された。
    開発初期には、西暦3000年に公開予定の理想のPythonとして、Python 3000と呼んでいた。Py3Kと略すこともある。
    しかし2.xとの後方互換性が損なわれている。当初は2.xに比べて3.xが利用できるライブラリ等が著しく少ないという問題点があったが、Djangoなど徐々に3.xに対応したフレームワークやライブラリなどが増えていったこともあり、2016年時点においては新規のプロジェクトについて3.xで開発することが多くなっている[19][信頼性要検証]。JetBrains とPythonソフトウェア財団による共同調査では、Python の 2 と 3 がどっちがメインであるかというアンケートで、Python 3 がメインであると答えた人が、2016年1月は40%だったが、2017年10月は75%になった[11][20]。
    2015年11月にリリースされたFedora 23[21]や2016年4月にリリースされたUbuntu 16.04 LTS[22]では、デフォルトでインストールされるPythonのバージョンが2.xから3.xに変更されている。Red Hat Enterprise Linuxでは7.5をもってPython 2が廃止予定（deprecated）となった[23]。
    バージョン
    リリース日[17]
    サポート期限[18]
    3.0
    2008年12月3日
    2009年1月13日
    3.1
    2009年6月27日
    2012年4月9日
    3.2
    2011年2月20日
    2016年2月20日
    3.3
    2012年9月29日
    2017年9月29日
    3.4
    2014年3月16日
    2019年3月18日
    3.5
    2015年9月13日
    2020年9月30日
    3.6
    2016年12月23日
    2021年12月
    3.7
    2018年6月27日
    2023年6月
    3.8
    2019年10月14日
    2024年10月
    3.9
    2020年10月5日
    2025年10月
    3.0[24]
    print命令をprint関数へ変更
    Unicodeを全面採用
    整数をint型に一本化
    3.1[25][26]
    順序付き辞書
    単体テストフレームワーク「unittest」への機能追加
    TkinterでのTile対応
    import文のリファレンス実装となる、Pythonで実装したimportlibモジュール
    ネストしたwith文に対する新たな文法
    3.2[27]
    単体テストモジュールのアップデートや拡張モジュール向け stable ABI
    pyc レポジトリディレクトリのサポート
    E-mail パッケージや SSL モジュールの改善
    pdb (Python debugger) の改良
    3.3
    3.1リリースから2年間、言語仕様を凍結し変更を行わない「モラトリアム期間」を解除した[28]。
    新しい文法として、ジェネレータ関数内で別のジェネレータ関数を利用する「yield from」を追加。
    「u」や「U」といったプレフィックスを用いたUnicodeリテラルシンタックスを復活
    UCS-4文字列にも対応し、文字列表現の柔軟性を強化
    仮想化Python実行環境を導入するためのvirtualenvパッケージの機能を「venv」機能としてコアに取り込んだ。
    3.4[29][30]
    オブジェクト指向ファイルシステムパスを提供する「pathlib」モジュールの提供
    列挙型を扱うためのenumモジュールの標準化
    統計関数を提供するstatisticsモジュールの導入
    Pythonが割り当てたメモリブロックを追跡するためのデバッグツールのtracemallocモジュールの導入
    非同期I/Oを扱うためのフレームワークとなるasyncioモジュールの導入
    Pythonの組み込み関数に関する分析情報を得るため機構の実装
    3.5[31][32]
    zipアプリケーションサポートの改良
    byte/bytearrayオブジェクトのための「%」フォーマット対応の追加
    行列乗算演算子@の導入
    高速ディレクトリトラバーサル機能os.scandir()の導入
    割込がかかったシステムコールのオートリトライ機能追加
    近似値であるかどうかをテストする機能の導入
    .pyoファイルの削除
    拡張モジュールをロードするための新しい仕組みの導入
    3.6[33]
    文字列中に式を埋め込める「Formatted string literals」の導入
    変数に対して型に関する情報（型ヒント）を与える「Syntax for variable annotations」の導入
    「async」および「await」文法 (async/await)でコルーチンを利用可能にする「Asynchronous generators」の導入
    標準ライブラリにsecretsモジュールを追加
    DTraceおよびSystemTapプローブのサポートを追加
    3.7[34][† 16]
    使用時点では宣言されていない型を使った型アノーテーション表記が可能となる
    レガシーな C ロケールの抑圧、強制 UTF-8 実行モード
    breakpoint() 関数の追加
    dict の挿入順の保存
    ナノ秒 (10-9 s) 単位の分解能を持つ新しい時間関数の追加
    コンテキスト変数
    データクラス
    3.8[† 17]
    代入式 :=
    位置のみのパラメータ
    f文字列で f'{expr=}' の形式のサポート
    pickle プロトコル5
    dict での reversed のサポート
    Python の時系列[編集]
    1990年代始め - オランダにあるStichting Mathematisch Centrum (CWI)で、グイド・ヴァンロッサムによってPythonの初期バージョンが作成される。
    1995年 - ヴァンロッサムは米国ヴァージニア州レストンにあるCorporation for National Research Initiatives (CNRI) に移動。ここでPythonの開発に携わり、いくつかのバージョンを公開する。
    2000年3月 - ヴァンロッサムとPythonのコア開発チームは BeOpen.com に移り、BeOpen PythonLabs チームを結成する。同年10月、PythonLabsチームはDigital Creations (現在のZope Corporation) に移る。
    2001年 - Pythonに関する知的財産を保有するための非営利組織Pythonソフトウェア財団 (PSF) が立ち上がる。このときZope CorporationはPSFの賛助会員となる。
    Pythonに影響を与えた言語[編集]
    ABC（インデントによる構文）
    Modula-2, -3（モジュール機能、オブジェクト指向）
    Icon（辞書、スライス演算子など）
    SETL（リストの内包表現）
    C, C++（基本的な構文）
    Smalltalk（仮想マシン機構、動的性）
    Lisp, Scheme（関数型言語の機能）
    Webアプリケーションフレームワーク[編集]
    Bottle（ボトル） - https://bottlepy.org/docs/dev/
    CherryPy（チェリーパイ） - https://cherrypy.org/
    Django（ジャンゴ） - https://www.djangoproject.com/
    Flask（フラスク） - http://flask.pocoo.org/
    Pyramid（ピラミッド） - https://pylonsproject.org/projects/pyramid/
    Plone（プローン） - https://plone.org/
    Tornado (Webサーバ)（トルネード） - https://sites.google.com/site/tornadowebja/
    Cyclone（C10K問題対応)（サイクロン） - http://cyclone.io/
    パッケージ管理システムおよびディストリビューション[編集]
    pip
    Anaconda (Pythonディストリビューション)
    EasyInstall
    注釈[編集]
    ^ GitHub - pyodide/pyodide: Python with the scientific stack, compiled to WebAssembly.
    出典[編集]
    ^ “Python Release Python 3.9.5”.   Python.org (2021年5月3日). 2021年5月13日閲覧。
    ^ Chapter 3. The Nature of JavaScript - Speaking JavaScript、2019年4月19日閲覧
    ^ Bini, Ola (2007). Practical JRuby on Rails Web 2.0 Projects: bringing Ruby on Rails to the Java platform. Berkeley: APress. p. 3. ISBN 978-1-59059-881-8
    ^ Peterson, Benjamin (2020年4月20日). “Python Insider: Python 2.7.18, the last release of Python 2”. Python Insider. 2020年4月27日閲覧。
    ^ “Python Developer’s Guide — Python Developer's Guide”. devguide.python.org. 2019年12月17日閲覧。
    ^ Windows (MS)にPython (Anaconda)を導入する（6つの罠） https://qiita.com/kaizen_nagoya/items/7bfd7ecdc4e8edcbd679
    ^ TIMTOWTDI。there's more than one way to do it
    ^ “Python for S60”. 2007年1月17日閲覧。
    ^ “KEKB: An Asymmetric Electron-Positron Collider for B-Factory in KEK”. 2007年1月17日閲覧。
    ^ “Python for Scientists and Engineers”. 2015年8月9日閲覧。
    ^ a b c d Python Developers Survey 2017 - Results
    ^ TSpython 発言
    ^ “EDU-SIG: Python in Education”. 2011年5月16日閲覧。
    ^ プレス発表 基本情報技術者試験における出題を見直し：IPA 独立行政法人 情報処理推進機構
    ^ 文部科学省初等中等教育局情報教育・外国語教育課 高等学校情報科「情報Ⅰ」教員研修用教材（本編）「第3章 コンピューターとプログラミング」(2019年5月)
    ^ “Why was Python created in the first place?”. General Python FAQ.   Python Software Foundation. 2007年3月22日閲覧。
    ^ a b “Python Documentation by Version”.   Python Software Foundation. 2014年3月20日閲覧。
    ^ a b 17. Development Cycle — Python Developer's Guide
    ^ 佐野裕史. “【入門者必見】Python2と3、どっちを学習すべき？違いを徹底解説！”.   株式会社 侍. 2016年9月21日閲覧。
    ^ By the numbers: Python community trends in 2017/2018 | Opensource.com
    ^ “【Changes/Python 3 as Default”.   Fedora Project. 2016年9月21日閲覧。
    ^ kuromabo. “Ja”.   Ubuntu.com. 2016年9月21日閲覧。
    ^ Red Hat Enterprise Linux 7 Chapter 53. Deprecated Functionality - Red Hat Customer Portal
    ^ “登場! Python 3.0 - 2系との違いを比較”.   マイナビ (2009年1月1日). 2014年3月13日閲覧。
    ^ “「Python 3.1」正式版リリース”.   OSDN Corporation (2009年7月1日). 2014年3月13日閲覧。
    ^ “Python 3.1リリース”.   OSDN Corporation (2009年6月30日). 2014年3月13日閲覧。
    ^ “Python 3.2リリース”.   OSDN Corporation (2011年2月22日). 2014年3月13日閲覧。
    ^ 末岡洋子 (2012年10月1日). “仕様変更凍結が解除され新機能が追加された「Python 3.3」、ついにリリース”.   SourceForge.JP. 2014年3月13日閲覧。
    ^ 後藤大地 (2014年3月18日). “Python 3.4登場”.   マイナビニュース. 2014年3月20日閲覧。
    ^ 末岡洋子 (2014年3月18日). “「Python 3.4」リリース、標準ライブラリを強化”.   SourceForge.JP. 2014年3月20日閲覧。
    ^ 後藤大地 (2015年9月13日). “Python 3.5.0登場”.   マイナビニュース. 2015年11月5日閲覧。
    ^ “「Python 3.5」正式版がリリース – 新機能が多数追加”.   ソフトアンテナブログ (2015年9月14日). 2015年11月5日閲覧。
    ^ 末岡洋子 (2016年12月26日). “「Python 3.6」がリリース”.   OSDN. 2017年5月26日閲覧。
    ^ 末岡洋子 (2018年6月29日). “「Python 3.7」リリース、型アノーテーションの強化などさまざまな機能が追加される”.   OSDN. 2018年7月11日閲覧。
    一次文献[編集]
    ^ “Welcome to Python.org” (英語). Python.org. 2020年8月10日閲覧。
    ^ “Sunsetting Python 2” (英語). Python.org. 2019年9月22日閲覧。
    ^ “History and License”. 2016年12月5日閲覧。 "All Python releases are Open Source"
    ^ Peters, Tim (2004年8月19日). “PEP 20 – The Zen of Python”. Python Enhancement Proposals.   Python Software Foundation. 2008年11月24日閲覧。
    ^ “About Python”.   Python Software Foundation. 2012年4月24日閲覧。, second section "Fans of Python use the phrase "batteries included" to describe the standard library, which covers everything from asynchronous processing to zip files."
    ^ Lemburg, Marc-André (2000年3月10日). “PEP 100 -- Python Unicode Integration”. Python Enhancement Proposals.   Python Software Foundation. 2014年2月12日閲覧。
    ^ What’s New in Python 2.4
    ^ PEP 3120 -- Using UTF-8 as the default source encoding | Python.org
    ^ PEP 538 -- Coercing the legacy C locale to a UTF-8 based locale | Python.org
    ^ PEP 540 -- Add a new UTF-8 Mode | Python.org
    ^ “PEP 0263 -- Defining Python Source Code Encodings”. Python Enhancement Proposals.   Python Software Foundation (2001年6月6日). 2014年2月12日閲覧。
    ^ "Wheel attempts to remedy these problems by providing a simpler interface between the build system and the installer." PEP 427 -- The Wheel Binary Package Format 1.0
    ^ a b “Quotes about Python”. 2007年1月15日閲覧。
    ^ “Python 2 から Python 3 への移植”.   Python Software Foundation. 2014年3月13日閲覧。
    ^ PEP 373 -- Python 2.7 Release Schedule | Python.org
    ^ What's New In Python 3.7 — Python 3.7.5 ドキュメント
    ^ What's New In Python 3.8 — Python 3.8.0 ドキュメント
    関連項目[編集]
    ポータル FLOSS
    IPython - Pythonのスニペットを実行できるノートパッド
    MyHDL - Python言語ベースのハードウェア記述言語
    Julia (プログラミング言語) - PythonのライブラリやC言語、Fortranのコードを呼び出せるプログラミング言語
    Pythonとよりは高速とされる
    スクリプト言語
    オブジェクト指向プログラミング
    学習用図書の例[編集]
    柴田望洋：「新・明解Python入門」 、SBクリエイティブ 、 ISBN 978-4815601522 (2019年5月)。
    外部リンク[編集]
    ウィキメディア・コモンズには、Pythonに関連するカテゴリがあります。
    ウィキブックスにPython関連の解説書・教科書があります。
    Welcome to Python.org Python公式サイト （英語）
    日本Pythonユーザ会 - マニュアル日本語訳の配布
    Python awesome
    Allen Downey、相川利樹(訳):「Think Python：コンピュータサイエンティストのように考えてみよう」
    喜多一, 「プログラミング演習 Python 2019」 2020年 p.1-200
    Pythonプログラミング入門 東京大学
    ゼロからのPython入門講座
    1. 科学技術計算のために Python を始めよう。
    Python による科学技術計算の概要 神嶌敏弘（2020年4月21日）。
    表話編歴Python実装
    ChinesePython
    CLPython
    CPython
    Cython
    MicroPython
    Numba
    IronPython
    Jython
    Psyco
    PyPy
    Python for S60（英語版）
    Shed Skin
    Stackless Python
    Unladen Swallow
    ウィジェット・ツールキット
    Tkinter
    PyGTK
    PyQt
    PySide
    wxPython
    フレームワーク
    CherryPy
    Django
    Flask
    PIDA（英語版）
    PyDev（英語版）
    Pylons
    Quixote（英語版）
    Spyder
    TurboGears
    Web2py
    Wing IDE（英語版）
    統合開発環境（専用）
    Boa
    IDLE
    Stani's Python Editor（英語版）
    PyCharm
    総合開発環境（汎用）
    Visual Python IDE
    PIDA（英語版）
    PyDev（英語版）
    Spyder
    Wing IDE（英語版）
    Eric Python IDE
    Geany
    ActiveState（英語版）
    omodo
    MonoDevelop
    NetBeans
    wxGlade（英語版）
    ライブラリ
    Kivy
    NumPy
    Pandas
    Requests
    SciPy
    カテゴリ
    Python
    ライブラリ
    コモンズ
    ウィキブックス
    Portal:コンピュータ
    表話編歴コンピュータ・プログラミング言語低水準言語
    機械語
    アセンブリ言語
    高水準言語
    1950年代
    FORTRAN
    LISP
    ALGOL
    RPG
    COBOL
    1960年代
    CPL
    BASIC
    PL/I
    APL
    BCPL
    Simula
    LOGO
    B
    1970年代
    Forth
    Pascal
    C
    Prolog
    Smalltalk
    Scheme
    ML
    AWK
    Ada
    1980年代
    C++
    Objective-C
    Common Lisp
    Eiffel
    Erlang
    Perl
    Mathematica
    J
    1990年代
    Python
    Tcl
    Haskell
    Visual Basic
    Ruby
    Lua
    Delphi
    Java
    ECMAScript (JavaScript)
    PHP
    OCaml
    SuperCollider
    R
    2000年代
    C#
    VB.NET
    Scala
    Clojure
    D
    F#
    Go
    Nim
    2010年代
    Dart
    Ceylon
    Elixir
    Crystal
    Hack
    Swift
    Rust
    Raku
    Elm
    Julia
    Kotlin
    Zig
    架空の言語
    擬似言語
    CASL
    CAP-X
    年表
    パラダイム
    一覧
    典拠管理
    BNF: cb13560465c (データ)
    FAST: 1084736
    GND: 4434275-5
    LCCN: sh96008834
    MA: 519991488
    SUDOC: 051626225
    「https://ja.wikipedia.org/w/index.php?title=Python&oldid=83976499」から取得
    カテゴリ: オブジェクト指向言語スクリプト言語オープンソースソフトウェアPython基本情報技術者試験隠しカテゴリ: 無効な出典が含まれている記事/2018年BNF識別子が指定されている記事FAST識別子が指定されている記事GND識別子が指定されている記事LCCN識別子が指定されている記事MA識別子が指定されている記事SUDOC識別子が指定されている記事ISBNマジックリンクを使用しているページ
    案内メニュー
    個人用ツール
    ログインしていませんトーク投稿記録アカウント作成ログイン
    名前空間
    ページノート
    変種
    表示
    閲覧編集履歴表示
    その他
    検索
    案内
    メインページコミュニティ・ポータル最近の出来事新しいページ最近の更新おまかせ表示練習用ページアップロード (ウィキメディア・コモンズ)
    ヘルプ
    ヘルプ井戸端お知らせバグの報告寄付ウィキペディアに関するお問い合わせ
    ツール
    リンク元関連ページの更新状況ファイルをアップロード特別ページこの版への固定リンクページ情報このページを引用ウィキデータ項目
    印刷/書き出し
    ブックの新規作成PDF 形式でダウンロード印刷用バージョン
    他のプロジェクト
    コモンズウィキブックスウィキバーシティ
    他言語版
    AfrikaansAlemannischAragonésالعربيةঅসমীয়াAsturianuAzərbaycancaتۆرکجهBasa BaliБеларускаяБългарскиभोजपुरीবাংলাBosanskiᨅᨔ ᨕᨘᨁᨗCatalàCebuanoکوردیČeštinaCymraegDanskDeutschΕλληνικάEnglishEsperantoEspañolEestiEuskaraفارسیSuomiNa Vosa VakavitiFrançaisGalegoગુજરાતીעבריתहिन्दीHrvatskiMagyarՀայերենInterlinguaBahasa IndonesiaÍslenskaItalianoLa .lojban.ქართულიҚазақшаភាសាខ្មែរ한국어KurdîКыргызчаLatinaLombardLietuviųLatviešuМакедонскиമലയാളംМонголमराठीBahasa Melayuမြန်မာဘာသာPlattdüütschNederlandsNorsk nynorskNorsk bokmålߒߞߏଓଡ଼ିଆਪੰਜਾਬੀPolskiپنجابیPortuguêsRomânăРусскийСаха тылаᱥᱟᱱᱛᱟᱲᱤScotsSrpskohrvatski / српскохрватскиၽႃႇသႃႇတႆး සිංහලSimple EnglishSlovenčinaSlovenščinaShqipСрпски / srpskiSvenskaKiswahiliதமிழ்తెలుగుТоҷикӣไทยTagalogTürkçeТатарча/tatarçaئۇيغۇرچە / UyghurcheУкраїнськаاردوOʻzbekcha/ўзбекчаTiếng ViệtWalonWinaray吴语中文Bân-lâm-gú粵語
    リンクを編集
    最終更新 2021年6月11日 (金) 17:10 （日時は個人設定で未設定ならばUTC）。
    テキストはクリエイティブ・コモンズ 表示-継承ライセンスの下で利用可能です。追加の条件が適用される場合があります。詳細は利用規約を参照してください。
    プライバシー・ポリシー
    ウィキペディアについて
    免責事項
    モバイルビュー
    開発者
    統計
    Cookieに関する声明
    
