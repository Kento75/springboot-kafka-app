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

### Apache kafka の起動

Zookeeper はそのままで、別端末を開く。

```
# ダウンロードしたKafkaの中に移動
$ cd ./<Kafkaディレクトリ>

# Kafkaの起動
$ ./bin/kafka-server-start.sh config/server.properties
```
