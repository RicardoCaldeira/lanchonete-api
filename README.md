# README - Projeto Spring Boot

Este projeto é um backend desenvolvido em Spring Boot, utilizando a versão 17 do Java. O objetivo do projeto é fornecer uma API que possa ser utilizada por um frontend para realizar operações de CRUD em um banco de dados MySQL.

...

## Pré-requisitos

Antes de executar o projeto, é necessário ter instalado:

- **JDK 17**
- **MySQL Server**

## Configuração do Banco de Dados

Para configurar o banco de dados, é necessário criar um schema chamado "lanchonete" no MySQL Server. Além disso, é necessário configurar o usuário e senha do MySQL no arquivo `application.properties`, que se encontra na pasta `src/main/resources`.

O arquivo `application.properties` deve conter as seguintes linhas:
``` java
spring.datasource.url=jdbc:mysql://localhost/lanchonete?createDatabaseIfNotExist=true&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=root
```

Certifique-se de que o usuário e senha configurados têm permissão para criar e manipular tabelas no schema "lanchonete".

## Execução do Projeto

Para executar o projeto, siga os seguintes passos:

1. Abra o terminal e navegue até a pasta raiz do projeto.
2. Execute o seguinte comando para compilar o projeto: 
```console
$ ./mvnw clean package
```
3. Após a compilação, execute o seguinte comando para iniciar o servidor:
```console
$ ./mvnw spring-boot:run
```
4. O servidor será iniciado na porta 8080. Você pode acessar a API através do seguinte endereço: http://localhost:8080/

## Utilização da API

A API fornece as seguintes operações:

- GET /lanchonete/listarPedidos: retorna todos os pedidos cadastrados no banco de dados.
  Ex de retorno :
![image](https://user-images.githubusercontent.com/34627524/234413619-6f3b0050-09f8-487f-b08f-151f017b7781.png)

- GET /lanchonete/listarPedido/{idPedido}: retorna o pedido com o ID especificado.
  Ex de retorno:
![image](https://user-images.githubusercontent.com/34627524/234413378-b1bde421-f1ad-4226-9cae-f5d98b9ced37.png)


- POST /lanchonete/cadastrarPedido: cria um novo pedido no banco de dados com base na quantidade informada.
  Ex Json a ser enviado:
``` json
{
  "itens": [
    {
        "produto": {
            "id": 1155
        },
        "quantidade": 3
    }
  ]
}
```

- PUT /lanchonete/incrementarPedido/{idPedido}: Adiciona novos produtos à um pedido no banco de dados com base na quantidade informada.
  Ex Json a ser enviado:
```json
{
  "itens": [
    {
      "produto": {
        "id": 1164
      },
      "quantidade": 2
    }
  ]
}
```

- PUT /lanchonete/decrementarPedido/{idPedido}: Retira produtos de um pedido no banco de dados com base na quantidade informada.
  Ex Json a ser enviado:
```json
{
  "itens": [
    {
      "produto": {
        "id": 1155
      },
      "quantidade": 2
    }
  ]
}
```

- PUT /lanchonete/fecharPedido/{idPedido}: Fecha o pedido com o ID especificado se o valor do pagamento for sufuciente para concluir o pedido.
  Ex Json a ser enviado:
```json
{
    "valorPagamento": 30.0
}
```

## Conclusão

Este projeto foi desenvolvido como parte da avaliação do processo seletivo da empresa NetPrecision.

Agradeço à equipe de recrutamento da NetPrecision pela oportunidade de participar do processo seletivo e espero ter a chance de contribuir com a empresa em um futuro próximo.

Caso tenha alguma dúvida ou sugestão para o projeto, sinta-se à vontade para entrar em contato.

...
