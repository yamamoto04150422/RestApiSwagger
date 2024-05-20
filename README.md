
# YAML　とは

**データを記述する**ために使用される形式言語

直列化が容易らしい

形式言語の種類

- Yaml
- Json
- XML

## tool

https://onlineyamltools.com/convert-yaml-to-json

https://www.yamllint.com/

## 比較

| 特徴      | YAML | JSON | XML  |
|-----------|------|------|------|
| フォーマット | インデントベース | キーバリュー形式 | タグベース |
| 読みやすさ | 高い  | 中    | 低い |
| 形式の厳密さ | 柔軟  | 厳密 | 厳密 |
| コメント | 可能  | 不可  | 可能 |
| データ表現 | シンプル | シンプル | リッチ |
| サポート言語 | 多い  | 多い | 多い |
| ファイル拡張子 | .yaml / .yml | .json | .xml |
| メディアタイプ | `application/x-yaml` | `application/json` | `application/xml` |
| ユースケース | 構成ファイル、データ交換 | データ交換、設定ファイル | データ交換、設定ファイル、文書形式 |

### YAML

```yaml
Person:
  Name: John Doe
  Age: 30
  Email: john.doe@example.com
  Address:
    Street: 123 Main St
    City: Anytown
    State: CA
    Zip: 12345
  PhoneNumbers:
    - Type: Home
      Number: 555-555-1234
    - Type: Work
      Number: 555-555-5678
```

### json

```json

{
  "Person": {
    "Name": "John Doe",
    "Age": 30,
    "Email": "john.doe@example.com",
    "Address": {
      "Street": "123 Main St",
      "City": "Anytown",
      "State": "CA",
      "Zip": "12345"
    },
    "PhoneNumbers": [
      {
        "Type": "Home",
        "Number": "555-555-1234"
      },
      {
        "Type": "Work",
        "Number": "555-555-5678"
      }
    ]
  }
}

```

### xml

```xml

<Person>
  <Name>John Doe</Name>
  <Age>30</Age>
  <Email>john.doe@example.com</Email>
  <Address>
    <Street>123 Main St</Street>
    <City>Anytown</City>
    <State>CA</State>
    <Zip>12345</Zip>
  </Address>
  <PhoneNumbers>
    <PhoneNumber>
      <Type>Home</Type>
      <Number>555-555-1234</Number>
    </PhoneNumber>
    <PhoneNumber>
      <Type>Work</Type>
      <Number>555-555-5678</Number>
    </PhoneNumbers>
  </PhoneNumbers>
</Person>


```


## DevOpsツール

- Ansible
- Kubernets
- DockerCompose
- GitHubAction

## 記述単位

1. ドキュメント
1. スカラー
1. コレクション
1. リスト
1. ディクショナリー

拡張子「.yaml」or「.yml」

## 直列化の仕組み

直列化とは、プログラム内でデータを取り扱うための「オブジェクト」のデータ形式を、バイト列に並べる(01)

直列化　プログラムからバイト列への変換

### 直列化の目的は

ファイルやDBへのデータ形式変換やNW経由での送信を行えるようにするため

## memo

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
