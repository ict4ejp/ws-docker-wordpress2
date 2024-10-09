# CLI 利用ができるコンテナ紹介


## Web 開発

### cURL 

* 概要: HTTPやFTPなどのプロトコルをサポートするデータ送受信用のコマンドラインツールです。
* 利用シーン: APIのテストやウェブサービスとの通信確認に役立つ。
* コマンド: `docker run --rm curlimages/curl <URL>`


### wget

* 概要: インターネット上のファイルをダウンロードするためのコマンドラインツール。HTTP、HTTPS、FTPなどのプロトコルをサポートし、再帰的なダウンロードも可能。
* 利用シーン: ウェブからのファイルダウンロード、ミラーリング、バックアップを自動化したいときに使用。ファイルを直接取得するのに便利。
* コマンド: `docker run --rm -it appropriate/curl wget <URL>`
* 公式：


### Httpie

* 概要: 人間に優しいHTTPクライアントツールで、REST APIのテストに役立つ。
* 利用シーン: APIのデバッグや確認作業を簡単に行いたいときに使用。
* コマンド: `docker run --rm alpine/httpie <API_URL>`
* 公式：https://httpie.io/


### jq

* 概要: JSONデータを整形・フィルタリングするためのコマンドラインツール。
* 利用シーン: APIのレスポンスやログファイルなど、JSONデータを解析したい場合に便利。
* コマンド: `docker run --rm ghcr.io/jqlang/jq:latest <JSON_FILE>`
* 公式：https://jqlang.github.io/jq/


## プラットフォーム管理

### AWS CLI

* 概要: AWSの各種サービス（EC2、S3、Lambdaなど）をコマンドラインから操作できる公式CLIツール
* 利用シーン: クラウドリソースの管理や自動化スクリプトの実行、AWSサービス間の操作、デプロイやデータの操作などを効率的に行いたい場合に最適。
* コマンド： `docker run --rm -it amazon/aws-cli <AWS_CLI_COMMAND>`
* TIPS：AWS認証情報を、ローカルファイルとして準備しておく必要あり


### MySQL Client (mysqlclient)

* 概要: MySQLデータベースに対してクエリを実行するためのコマンドラインクライアント
* 利用シーン: MySQLデータベースに接続してクエリを実行、データの取得・挿入・更新、データベースの管理操作（バックアップ・リストアなど）を行う際に便利。
* コマンド: `docker run --rm -it mysql mysql -h <host> -u <user> -p`


### PostgreSQL

* 概要: PostgreSQLデータベースサーバーに対してクエリを実行するためのCLIツール。
* 利用シーン: PostgreSQLデータベースのクエリ実行やバックアップ、データの確認作業に最適。
* コマンド: `docker run -it --rm postgres psql -h <host> -U <user>`


## TIPS

### alias コマンドで、ショートカット利用

httpieコンテナを httpie コマンドとして登録する

```
$ alias httpie='docker run --rm alpine/httpie'
$ httpie --help
$ httpie <API_URL>
```

AWS CLIコンテナ を awstest コマンドとして登録する

```
$ alias awstest='docker run --rm -ti -v ~/.aws:/root/.aws -v $(pwd):/aws amazon/aws-cli'
$ awstest --version
```

※alias 設定を永続化したい場合は、.bashrc などへの追記を検索ください

