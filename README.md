# これは何
swaggerのお勉強用リポジトリ。APIのページは[こちら](https://yuasalily.github.io/swagger-sample/)。

# 0. 事前準備
このリポジトリではvscodeでswaggerを利用する。環境構築はdevcontainerで行っているので詳細は割愛。

# 1. Hello World
ここではとりあえず動かしてみるところまでやってみる。完成品は[ここ](https://yuasalily.github.io/swagger-sample/1HelloWorld/)で見られる。

yamlファイルを作成する。名前はなんでもいいのでとりあえずswagger.yamlとする。出来たファイルに下記の内容を保存する。ここでは動かしてみるだけなので各要素の詳細は割愛する。保存出来たらShift + Alt + Pを押すことでSwagger Previewが表示される。
```
openapi: "3.0.3"

info:
  title: "Swagger Sample Api"
  version: "1.0.0"

paths:
  "/hello":
    get:
      summary: "Hello World API"
      description: "Get Hello World"
      responses:
        "200":
          description: "Success"
          content:
            application/json:
              schema:
                type: string
                example: "Hello World"

```
せっかく作ったのでhtmlに変換してGithub Pagesで見られるようにする。htmlへの変換は[redocly](https://github.com/Redocly/redoc)を用いる。Swagger Viewerと見た目は異なるけれどかっこいいので気にしない。下記コマンドでhtmlを生成して移動させる。Github Pagesの設定ができていれば見られるようになる。
```
npx @redocly/cli build-docs swagger.yaml && mv redoc-static.html docs/index.html
```
今回作ったものを`docs/1HelloWorld`にコピーしておく。

# 2. OpenAPIオブジェクト
APIの記述形式をOpenAPI Specificationと呼び、上で作ったswagger.yamlのような形式で記述していく（[参考](https://swagger.io/docs/specification/about/)）。これのルートオブジェクトをOpenAPIオブジェクトと呼ぶ。記述できるフィールドは[このページ](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.3.md)に記載しているのでまとめていく。

# 3. openapi
必須項目。どのOpenAPI Specificationのバージョンを利用するかを`openapi`というフィールドに記述する。各バージョンのドキュメントは[ここ](https://github.com/OAI/OpenAPI-Specification/tree/main/versions)にある。

# 4. info
必須項目。API仕様のメタデータを記述する。設定できる項目の詳細は[公式ページ](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.3.md#fixed-fields-1)を見たほうが早いのでそちらを参照。ここでは各項目の説明を簡単にしながらサンプルのswagger.yamlを作成していく。完成品は[ここ](https://yuasalily.github.io/swagger-sample/4info/)で見られる。

## 4.1 title
必須項目。APIのタイトルを記述する。今回は下記の通り記述した。
```
titile: "Swagger Sample API"
```

## 4.2 description
APIの詳細を記述する。Markdownでの記述が可能。今回は下記の通り記述した。
```
description: |
    # Features
    - Get Hello World
    - Other Brilliant API
```

## 4.3 termsOfService
サービスの利用規約へのURLを記載する。今回は下記の通り記述した。
```
termsOfService: "https://www.example.com/sample-terms-of-service"
```

## 4.4 contact
連作先の情報を記載する。今回は下記の通り記述した。
```
contact:
    name: "Sample API team"
    url: "https://www.example.com/sample-support"
    email: "sample-support@example.com"
```

## 4.5 lisence
ライセンスの情報を記載する。今回は存在しないライセンスを適当に記載しているが、実際に記述する際は[SPDX](https://spdx.org/licenses/)などを参照するとよい。今回は下記の通り記述した。
```
license:
    name: "Sample License"
    url: "https://www.example.com/sample-license"
```

## 4.6 version
APIのバージョンを記載する。今回は下記の通り記述した。
```
version: "1.0.0"
```
以上で作成したものを`docs/4info`に保存しておく。


# メモ
利用しているコマンドなどを列挙する。
- Swagger Viewerの立ち上げ：Shift + Alt + P
- htmlを生成して移動：`npx @redocly/cli build-docs swagger.yaml && mv redoc-static.html docs/index.html`