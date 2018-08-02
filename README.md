# AX4B Code Challenge

## Sobre o desafio

#### Propósito do nosso desafio
Queremos entender qual a sua capacidade de resolver problemas, a forma como você pensa para resolvê-los e como você organiza o seu código.

#### Modo de avaliação
A equipe técnica considera primordiais os seguintes critérios:

* **Legibilidade e manutenibilidade:**
    * O código é legível e de fácil manutenção?
    * O código está acoplado ou desacoplado?
    * Como foi feito o tratamento de erro?

* **Organização:**
    * Como estão divididas as responsabilidades?
    * Qual abordagem de desenvolvimento foi utilizada?
* **Qualidade:**
    * O código segue as boas práticas da linguagem?
    * Tem testes? Qual é a cobertura dos testes?
    * Como foram utilizados os recursos da linguagem?
* **Desempenho:**
    * Escreveu um código com performance adequada? 
* **Documentação:**
    * É suficiente para entender como a solução funciona? 
    * Contempla a instalação da solução?

## Desafio

Consiste em disponibilizar, através de uma API REST, as funções básicas para o gerenciamento de um cadastro de clientes.

As regras abaixo devem ser aplicadas ao cadastro:

* Todos os clientes devem possuir um ID, único e sequencial, definido pelo sistema.
* Todos os clientes devem ter em seu cadastro as informações: Nome, Email e Endereço.
* Para cada cliente deve ser designado uma entidade legal, que será responsável pelo seu atendimento.

Como designar uma entidade legal para atender o cliente: O cliente deve ser atendido pela entidade legal mais próxima de acordo com as coordenadas geográficas de seus respectivos endereços.

Utilize a fórmula abaixo para calcular a distancia entre as coordenadas:

```
a = sin²(Δφ/2) + cos φ1 ⋅ cos φ2 ⋅ sin²(Δλ/2)
c = 2 ⋅ atan2( √a, √(1−a) )
d = R ⋅ c

where	φ is latitude, λ is longitude, R is earth’s radius (mean radius = 6,371km);
note that angles need to be in radians to pass to trig functions!
```

Uma lista de entidades legais está disponível nesse arquivo [legalEntity.json](seed/legalEntity.json) e devem ser carregasdas no seu sistema.

#### Funções

#### Crie um cliente
A partir da estrutura abaixo em `Request` e `Body` permita a criação de um cliente

Request:
```
POST /cust
```

Body:
```json
{
    "name" : "Frank Castle",
    "email" : "f.castle@email.com",
    "address" : "R. Flórida, 1738 - Cidade Monções, São Paulo - SP, 04565-001"
}
```

Response: 

Em caso de erro, você deve definir uma estrutura de retorno e em caso de sucesso esperamos a segunte estrutura:
```json
{
    "id": 1,
    "name": "Frank Castle",
    "email": "f.castle@email.com",
    "address": "R. Flórida, 1738 - Cidade Monções, São Paulo - SP, 04565-001",
    "location": {
        "lat": -23.6071357,
        "lng": -46.6946085
    }
}
```
#### Mostre um cliente
Busque um cliente a partir de um `id`

Request:
```
GET /cust/{id}
```

Response: 
```json
{
    "id": 1,
    "name": "Frank Castle",
    "email": "f.castle@email.com",
    "address": "R. Flórida, 1738 - Cidade Monções, São Paulo - SP, 04565-001",
    "location": {
        "lat": -23.6071357,
        "lng": -46.6946085
    },
    "legalEntityId": "AXSP"
}
```

## Orientações gerais

Capriche no código.

Crie uma documentação de como rodar o seu projeto!

#### Banco de dados
Caso você decida persistir os dados em banco de dados garanta que todos os arquivos para configuração do banco estejam disponíveis e limite-se as seguintes versões de banco de dados:
* mongoDB
* SQL Server
* Oracle 11g

#### Deploy do desafio

A forma como você disponibiliza o seu código faz parte do teste.


Só começar!!!
