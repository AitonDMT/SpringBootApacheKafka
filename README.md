# Exemplo de Configuração e utilização do Apache Kafka com Spring Boot

1 - Clonar o projeto Maven.

2 - Baixar 1 dos exemplos de container kafka em: https://github.com/confluentinc/cp-docker-images/tree/5.3.3-post/examples ou utilizar o já existente no projeto:
"/SpringKafka/src/main/resources/docker-compose.yml"

Aqui está o kafka-single-node, mas também podem ser utilizas outra imagens de exemplo.

3 - Em uma janela do terminal, executar o comando "docker-compose up -d"
Aguardar baixar os arquivos.

4 - Digitar o comando "docker-compose ps " para exibir os nodes em execução.

5 - Entrar no container digitando o comando abaixo:
"docker exec -it kafka-single-node_kafka_1 bash"

6 - Com o comando abaixo, criar um tópico (aqui o nome do topic é "dmt_topic", o mesmo configurado no Field TOPIC da classe producer:
"kafka-topics --create --bootstrap-server localhost:29092 --replication-factor 1 --partitions 2 --topic dmt_topic"

7 - Listar os tópicos existentes:
"kafka-topics --list --bootstrap-server localhost:29092"

8 - Executar o projeto SpringKafka como uma Spring Boot Application.

9 - Utilizando o Postman ou qualquer outro similar, realizar a chamada POST ao RestController disponibilizado pela classe TestController.java
POST http://localhost:8080/publish?message=Ola Mundo

10 - a mensagem recebida via POST será exibida no console da Spring Boot Application




