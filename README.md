# react-demo
- reactの基礎を学ぶレポジトリになっている。
- [reactを学ぶ](https://ja.react.dev/learn)における以下の項目全てやる
1. クイックスタート
2. チュートリアル: 三目並べ
3. Reactの流儀
4. UIの記述
5. インタラクティビティの追加
6. stateの管理
7. 避難ハッチ

## 環境構築
参考: 
- https://www.docker.com/ja-jp/blog/how-to-dockerize-react-app/
- https://qiita.com/tsuyuni/items/95551eb3d71be4ae79c8#%E3%83%95%E3%83%AD%E3%83%B3%E3%83%88%E3%82%A8%E3%83%B3%E3%83%89%E3%81%AE%E7%92%B0%E5%A2%83%E6%A7%8B%E7%AF%89
- https://zenn.dev/web_tips/articles/abad1a544f3643

### ローカルを汚さずにreactプロジェクトを作成する
docker/Dockerfile
```Dockerfile
FROM node:22.12.0-alpine
WORKDIR /app
RUN apk add bash
```

docker-compose.yml
```yml
services:
  app:
    build:
      context: .
      dockerfile: ./docker/Dockerfile
    ports:
      - 3000:3000
    volumes:
      - ./app:/app
```

```bash
docker compose build 
docker compose run --rm app bash
```

/app#
```bash
npx create-react-app .
```

### docker/Dockerfileを編集

```Dockerfile
FROM node:22.12.0-alpine
WORKDIR /app
RUN apk add bash
COPY ./app .
RUN npm install
CMD ["npm", "start"]
```

この状態で以下にアクセスすれば立ち上がる
http://localhost:3000/

## クイックスタート
題材: https://ja.react.dev/learn
>React ドキュメントへようこそ！ このページでは、日々の開発で使用する React のコンセプトのうち 80％ の部分を紹介します。

### オンラインコンバータ
HTMLとJSXは若干違うので、変換してくれるツール: https://transform.tools/html-to-jsx
