# php-sandbox
DockerでのPHPの実行環境です。

PHPのバージョンは8.0としていますが、`./docker/php/Dockerfile`を編集すれば変更できます。

`./punlic`フォルダがドキュメントルートです。

## 使い方
docker-compose.ymlがあるディレクトリで実行してください。

コンテナ起動(初回)
```
docker compose up -d --build
```

コンテナ起動(2回目以降)
```
docker compose up -d
```

コンテナ終了
```
docker compose down
```
