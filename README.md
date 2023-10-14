# これは何
swaggerのお勉強用リポジトリ。APIのページは[こちら](https://yuasalily.github.io/swagger-sample/)。

# 0. 事前準備
このリポジトリではvscodeでswaggerを利用する。環境構築はdevcontainerで行っているので詳細は割愛。

# 1. Hello World
ここではとりあえず動かしてみるところまでやってみる。

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

# メモ
利用しているコマンドなどを列挙する。
- Swagger Viewerの立ち上げ：Shift + Alt + P
- htmlを生成して移動：`npx @redocly/cli build-docs swagger.yaml && mv redoc-static.html docs/index.html`