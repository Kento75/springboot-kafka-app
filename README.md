# springboot-kafka-app

### Apache Kafka の準備

```
$ curl https://www-us.apache.org/dist/kafka/2.3.0/kafka_2.12-2.3.0.tgz | tar zx -C ./
```

### Zookeeper の起動

Zookeeper は分散アプリケーションを構築する上で必要となる。
同期、設定管理、グルーピング、名前管理などの機能を提供するサービスである。

```
# ダウンロードしたKafkaの中に移動
$ cd ./<Kafkaディレクトリ>

# Zookeeperの起動
$ ./bin/zookeeper-server-start.sh config/zookeeper.properties
```

### Apache Kafka の起動

Zookeeper はそのままで、別端末を開く。

```
# ダウンロードしたKafkaの中に移動
$ cd ./<Kafkaディレクトリ>

# Kafkaの起動
$ ./bin/kafka-server-start.sh config/server.properties
```

## kafka_prod_cons の使用例

Zookeeper と Kafka の起動、SpringBootApp の起動後に以下のプロセスを立ち上げる。

```
# コンシューマーの起動
$ <Kafkaをダウンロードしたディレクトリ>/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic myTopic
```

プロセス立ち上げ後、Postman で以下の送信を実行

API1
| リクエスト種別 | POST |
| -------------- | --------------------------------------------- |
| URL | http://localhost:8080/api/kafka |
| Request Body | { "field1" : "field1", "field2" : "field2" } |

API2
| リクエスト種別 | POST |
| -------------- | ------------------------------------------------------------- |
| URL | http://localhost:8080/api/kafka/v2 |
| Request Body | { "title" : "new title", "description" : "new description" } |
