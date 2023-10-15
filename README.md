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


# メモ
利用しているコマンドなどを列挙する。
- Swagger Viewerの立ち上げ：Shift + Alt + P
- htmlを生成して移動：`npx @redocly/cli build-docs swagger.yaml && mv redoc-static.html docs/index.html`