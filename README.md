# Examples of Fortran OSS for efficiency improvement of desktop development environment

[第6回並列Fortranシンポジウム](https://site.hpfpc.org/home/events/parallel_fortran_sympo6)での発表「Fortran向けOSSを活用したデスクトップ開発環境効率化」([pdf](https://github.com/degawa/hpfpc_fortran_oss/blob/main/Fortran_OSS_for_efficiency_improvement_of_desktop_development_environment.pdf))で紹介したFortran OSSの使用例．

発表内では，下記のOSSの使用例を紹介した．
- Fortran stdlib
- JSON-Fortran
- VTKFortran
- fypp
- fprettify

応用例として，JSON-Fortranから設定ファイルを読み込み，距離関数を計算し，VTKFortranを用いてvtr形式で出力するプログラムも紹介した．ロギングやエラーチェックにはstdlibを用いている．

## リポジトリ内容の取得
`--recursive`オプションを付けてクローンする．
```console
git clone --recursive https://github.com/degawa/hpfpc_fortran_oss
```

`--recursive`オプションを付けずにクローンした場合は，`git submodule`コマンドを利用して，参照するリポジトリの内容も取得する．

```
git clone https://github.com/degawa/hpfpc_fortran_oss
cd hpfpc_fortran_oss
git submodule update --init --recursive
```

このリポジトリ内でまとめてクローンする必要はなく，使用例を個別にクローンしてもよい．

## 要求ソフトウェア
- [fpm](https://github.com/fortran-lang/fpm)
- [Fortran-stdlib](https://github.com/fortran-lang/stdlib)
- [JSON-Fortran](https://github.com/jacobwilliams/json-fortran)
- [VTKFortran](https://github.com/szaghi/VTKFortran)
- [fypp](https://github.com/aradi/fypp)
- [fprettify](https://github.com/pseewald/fprettify)

## fpmの学習について
発表の中ではfpmの利用方法について，その利用方法の詳細な導入は行わなかった．しかし，fpmの学習についても考慮しており，使用例の中で様々な機能を活用している．

下記の順番で作業をしていくと，fpmに躓くことなく一定の使い方を学習できると考えている．ただし，fpmが標準コンパイラとして参照するgfortranを利用する場合であり，Intel Fortranを用いる場合はいくつか手順が省略される．

1. `fpm new`で新しくプロジェクトを作り, `fpm build`, `fpm run`, `fpm test`を実行する．
1. stdlibの使用例（[ex_stdlib](https://github.com/degawa/ex_stdlib)）あるいはJSON-Fortranの使用例（[ex_jsonfortran](https://github.com/degawa/ex_jsonfortran)）を実行する．
    - 依存プロジェクトの参照方法
1. VTKFortranの使用例（[ex_vtkfortran](https://github.com/degawa/ex_vtkfortran)）
    - ビルドの際に，コンパイラにオプションを渡す方法
    - 依存プロジェクトがさらに別のプロジェクトを参照している際の挙動
    - ビルドだけでなく，実行の際にもコンパイル時と同じオプションが必要であること
1. [ex_io](https://github.com/degawa/ex_io)
    - 複数の依存リポジトリの参照方法
1. fyppの使用例（[ex_fypp](https://github.com/degawa/ex_fypp)）
    - exampleの使用方法
    - 複数の実行ファイルのビルド
    - 実行可能な実行ファイルの確認方法，選択して実行する方法

## 言及したOSS
使用例を紹介する時間はなかったが，下記OSSに言及した．
- [FORD](https://github.com/Fortran-FOSS-Programmers/ford)
    - ドキュメント生成ツール
- [TOML-Fortran](https://github.com/toml-f/toml-f)
    - FortranでTOMLファイルを取り扱うためのAPIを提供
- [M_CLI2](https://github.com/urbanjost/M_CLI2)
    - コマンドラインオプションの取り扱いを改善
- [vegetables](https://gitlab.com/everythingfunctional/vegetables)
    - BDDスタイルのテストフレームワーク
- [GTK-Fortran](https://github.com/vmagnin/gtk-fortran)
    - GIMP ToolkitのFortranバインディング
- [Quickstart Fortran on Windows](https://github.com/LKedward/quickstart-fortran)
    - Windows用のFortran環境のインストーラ
        - gfortran, fpm OpenBLAS, make
        - intelコンパイラの環境変数を設定するためのバッチファイル
        - stdlibをインストールするためのバッチファイル
