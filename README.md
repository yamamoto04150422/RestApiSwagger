OpenAPIを利用するにあたり「YAML」を自由に記載できる必要があります。

ここではざっと「YAML」の記述方法について「JSONと比較しながら」まとめておきますので、今後の学習ベースとして一通り使えるよう読み込んでおきましょう。



◆ハッシュ

キーとバリューは「":"(コロン)」でつなぎます。また、キーとバリューの間には半角スペースを1つ以上入れます。

YAML

key: value
JSON

{ key: value }


◆配列

配列は「"-"(ハイフン)」で表現します。「"-"(ハイフン)」1つが1要素になります。

YAML

key:
  - value1
  - value2
  …
JSON

key: [value1, value2, ...]


◆ハッシュのネスト

インデント数とオブジェクトの兄弟が同じ意味を持ちます。ネストする場合、インデント数に注意してください。

YAML

parent_key:
  child_key1: child_value1
  child_key2: child_value2
JSON

parent_key: {
  child_key1: child_value1,
  child_key2: child_value2
}


◆配列のネスト

配列が「"-"(ハイフン)」で表現されること、兄弟が同じ数の半角スペースインデントで表現されることを組み合わせて表現します。

YAML

parent_key:
  -
    - value1
    - value2
  -
    - valueA
    - valueB
JSON

parent_key: [
  [ value1, value2 ],
  [ valueA, valueB ]
]


◆配列内のハッシュ

配列は「"-"(ハイフン)」で表現されますが、その要素としてオブジェクトをとる場合、配列要素となるオブジェクトのプロパティ位置および「"-"(ハイフン)」の有無に注意します。

YAML

parent_key:
  - child_key1: child_value1
    child_key2: child_value2
JSON

parent_key: [{
    child_key1: child_value1,
    child_key2: child_value2
  }]


◆長文（コードのような改行付きの長い文字列を入れたい場合）

バリューに改行ありの長文を入れたいケース（コマンド群やソースコードなどを入れるような―ケース）の場合、「"|"(パイプ)」に続けてデータを記載します。

YAML

key: |
  hobe
  foo
  bar
JSON

{
  key: `hoge
foo
bar`
}


◆複数YAMLの結合（1ファイルに複数のYAMLを含めたい場合）

YAMLは1ファイルに複数定義を入れることができます。複数の定義を行いたい場合、その境界は「"---"(ハイフン3つ)」で仕切ります。

YAML

key1: value1
---
key2: value2
JSON

{ key1: value1 }
{ key2: value2 }