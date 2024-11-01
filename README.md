# ⚛︎ GraphQL
<a href="https://graphql.org/"><img src="https://cdn.worldvectorlogo.com/logos/graphql-logo-2.svg" height="77" align="right"></a>

O **GraphQL** é uma especificação para criar e usar APIs que têm sua própria linguagem de query (consulta). O que isso significa então? É que às vezes o <a href="https://dev.elo.com.br/tutoriais/introducao-ao-graphql">Graphql</a> é entendido ou é percebido como sendo uma tecnologia voltada para bancos de dados, ele não é. Ele é uma especificação para APIs, para escrever, criar e utilizar APIs e não está ligado a nenhum tipo de banco, inclusive ele pode ser usado com qualquer base de dados, ou mesmo nenhuma base de dados. O GraphQL é uma linguagem de queries para manipular dados em APIs e não está vinculada a nenhum banco de dados ou linguagem de programação específica. Não importa se os dados vêm de objetos, de tabelas diferentes, de vários endpoints de uma API. A ideia é que o cliente consiga receber os dados da melhor forma possível. GraphQL é uma especificação pensada na forma como clientes utilizarão os dados, não de que forma estão gravados nem de onde vêm. Como o próprio site oficial já diz: "Descreva seus dados", "Pergunte para o que você quer" e "Pegue seus resultados previsíveis", 

O GraphQL é uma ferramenta para construirmos de forma ágil APIs que são rápidas e versáteis. Ou seja, o uso de GraphQL agiliza o desenvolvimento de novas features de um produto. O back-end não precisa desenvolver novos endpoints para cada nova funcionalidade, ao contrário do REST. Isso torna o desenvolvimento de produtos mais ágil. O Graphql fornece um ambiente para executarmos essas queries usando os dados que fornecermos para ele, não importa de onde esses dados venham. Eles podem vir de um banco SQL, de um banco NoSQL, de uma API de terceiros via endpoint REST, ou até mesmo da memória do seu computador. E também de todos esses juntos, para o SQL não faz diferença, isso não é o ponto principal dele. Ou seja, ele pode tanto substituir APIs REST como trabalhar em conjunto dentro de uma mesma aplicação, você pode ter serviços webservices REST trabalhando além de ter uma API GraphQL executando e você pode usar a API GraphQL para direcionar ou encapsular varias aplicações REST em baixo, portanto, tem muitas possibilidades e é um framework extremamente poderoso que traz uma flexibilidade que uma API do tipo REST não vai conseguir de entregar.

O Graphql também normalmente utilizamos o protocolo HTTP para fazer a comunicação, mas na verdade ele é agnóstico com relação a protocolos de comunicação. Os **schemas** (esquemas) do Graphql são baseados em como os dados são usados, e não como estão armazenados. Isso é um conceito chave para entender o Graphql, não importa se os dados vêm de objetos, de APIs, o que acabamos de falar, o que importa é que o cliente consiga utilizar esses dados da melhor forma possível. Quando falo cliente normalmente estou falando do front ou de quem vai consumir nossa API Graphql. Essa é uma questão chave. Os schemas são baseados em como os dados são usados, e não importa de onde eles vêm. Um schema é a peça central que define a estrutura de uma API, especificando quais tipos de dados estão disponíveis e as operações que podem ser realizadas na API, como consultas (queries), <a href="">mutações (mutations)</a> e <a href="">subscrições (subscriptions)</a>. Ele serve como o contrato entre o servidor e os clientes, descrevendo como interagir com os dados e quais dados estão disponíveis.

Por exemplo, se usássemos um banco de tabelas para criar um `usuário`, por exemplo, um usuário de uma escola de inglês, esses usuários têm `nome`, `e-mail`, se eles estão ativos no sistema ou não, e eles podem ser professores, podem ser alunos, podem ser coordenação. Se pensarmos, por exemplo, numa tabela SQL, conseguimos montar um usuário completo a partir de duas tabelas, uma com os dados principais, `nome`, `e-mail`, etc, e outra para definir os possíveis roles, os possíveis papeis desse usuário no sistema. Então você teria uma tabela de `roles` (funções de trabalho) que tem `professor`, `aluno`, `coordenação`, e por aí vai. Com o Graphql pensamos em como esses dados seriam usados pelo lado cliente e o cliente pode montar as queries a partir dessa premissa.

Vamos supor que numa `feature` qualquer desse sistema de escola de cliente, o lado cliente precisa receber somente o nome do usuários da tabela `users` e da tabela `roles` ele só precisa receber uma `string` com o tipo de `role`, `professor`, `aluno`, etc. Ele não precisa receber mais nada. Ele quer fazer uma query que pegue de `users` somente o nome, e do `role` desse `user`, do papel desse usuário, somente a `string` de tipo, ele não quer receber mais nada, somente isso.

> É interessante trabalhar com autenticação e autorização de usuários usando esquemas do GraphQL.

A partir dessa query que o cliente consegue fazer em Graphql ele recebe um JSON somente com o que ele quer no formato agregado de uma forma que para o cliente faz mais sentido, são dados mais concisos e somente com o que o cliente pediu.

O Graphql com isso procura resolver um problema em rest, uma questão do rest que costumamos chamar de **overfitting**, que seria **super requisição**, e também o **underfitting**, que é **sub requisição**. É quando o endpoint ou traz muitos dados que não precisamos numa requisição ou o contrário, precisamos de mais de uma requisição para ter os dados que precisamos. Então, o Graphql vem aí para resolver essa questão e fazer com que nosso cliente peça, em uma requisição só ele receba somente o que ele quer e mais nada. Podemos dizer que o Graphql é uma tecnologia voltada para front? Podemos, porque a ideia é melhorar, otimizar essa relação dos clientes com os dados que ele recebe do back, que é uma tecnologia focada no front, mas claro que vamos desenvolver nosso servidor Graphql no back.

Para o cliente, para a parte de front, ele vai ter menos requisições, vai visualizar os dados de uma forma melhor, os dados agregados de uma forma melhor para ele, mas dados mais enxutos, inclusive, de forma que faça mais sentido para ele, mas também tem bastante benefícios para a parte do back, para o lado do servidor, uma vez que livra o backend de fazer muitas implementações de muitos endpoints.

O desenvolvimento fica mais ágil. Se você tem que desenvolver um novo produto ou uma nova `feature` para o seu produto, evita que o backend caia naquela situação de ter que desenvolver endpoints sem fim para cada coisa nova que pode ou não entrar no sistema.

Fica mais ágil porque o front não fica dependendo tanto do back para criar um endpoint para cada coisa que ele precisa fazer, e o backend fica mais agilizado também sem ter que ficar fazendo todas essas implementações para uma coisa que no final às vezes pode até entrar no sistema ou não.

Vamos testar na prática com alguns testes envolvendo a API GraphQL: Você pode usar o Postman ou <a href="https://app.pipefy.com/graphiql">GraphiQL</a>

Consultar o card do Pipefy:

```gpl
query {
  card(id: [card]) {
    title
    done
    id
    fields {
      date_value
      datetime_value
      filled_at
      float_value
      indexName
      name
      native_value
      report_value
      updated_at
      value
    }
    updated_at
  }
}
```

Como dito anteriormente que poderiamos usar qualquer linguagem de programação com suporte a API GraphQL, vamos ver e comparar as consultas em algumas linguagens de programação:

## [GraphQL] Scalar types
São tipos que refletem alguns dos tipos de dados que já conhecemos. Para o GraphQL, são os tipos que se resolvem em dados concretos (ao contrário de objetos, por exemplo, que são conjuntos de dados). São eles:

- `Int` - inteiro de 32 bits
- `Float` - tipo ponto flutuante
- `String` - sequência de caracteres no formato `UTF-8`
- `Boolean` - `true` ou `false`
- `ID` - identificador único, usado normalmente para localizar dados. É possível criar tipos scalar customizados, estudaremos mais adiante.

## [GraphQL] Object type
Quando trabalhamos com GraphQL, o ideal é pensarmos no uso dos dados, mais do que na forma em que estão armazenados. Pensando nisso, nem sempre queremos retornar um dado concreto, mas sim um conjunto de dados com propriedades específicas — ou seja, um objeto.

Um exemplo de tipo Objeto (Object type) em GraphQL:

```gql
type Livro {
    id: ID!
    titulo: String!
    autoria: String!
    paginas: Int!
    colecoes: [Colecao!]!
}
```

No exemplo acima, estamos definindo o **tipo Objeto** `Livro`.

As propriedades que no GraphQL são chamadas de **campos** retornam **tipos scalar**, como `strings` e `inteiros`, e também podem retornar arrays compostas de outros objetos, como no caso de colecoes: `[Colecao!]!`.

> Note que na definição do objeto não está especificado de qual base de dados virão esses dados, apenas quais dados o GraphQL espera receber, e de que tipos.

Os campos marcados com exclamação `!` são campos que não podem ser nulos. Ou seja, qualquer query que envolva estes campos sempre devem ter algum valor do tipo esperado. No caso de colecoes: `[Colecao!]!` a exclamação após o fechamento da array significa que o campo colecoes sempre vai receber uma array (tendo ou não elementos dentro dela); a exclamação em `Colecao!` significa que qualquer elemento dentro da array sempre vai ser um objeto `Colecao`.

## [GraphQL] Schema & Query type

Os tipos **Query** (consulta) definem os pontos de entrada (entry points) da API; indicam quais dados o cliente pode receber e de que forma, de certa forma, são como requests do tipo `GET` quando trabalhamos com REST, a diferença aqui é que o cliente tem mais liberdade para montar as queries para receber apenas os dados que precisa lembrando que, para o GraphQL e também para o cliente, não importa a origem desses dados. os dados podem vir de diversas fontes: endpoints REST, bancos SQL e NoSQL, outro servidor GraphQL.

Sintaxe: Um exemplo de tipo Query

```gql
type Query {
    livros: [Livro!]!
    livro(id: ID!): Livro!
}
```

Aqui definimos a query `livros`, que retorna uma array composta por **tipos objeto** `Livro`, e a **query** `livro`, que recebe um número de `ID` por parâmetro e retorna um **objeto** `Livro` referente ao `ID` informado.

Uma vez que as queries são os pontos de entrada de uma API GraphQL, toda aplicação vai ter pelo menos uma Query em seu schema.

Para fazer uma requisição de consulta para uma API do GraphQL, nós não utilizamos o método `GET`, mas sim `POST`.

Exemplo:

```http
POST: query {card(id: [ID]) { title done id updated_at }}

Host: https://api.pipefy.com/graphql
```

Em uma API GraphQL, o **payload** refere-se ao conjunto de dados que é enviado ou recebido durante uma requisição. Esse payload contém a estrutura exata da consulta (query) ou mutação (`mutation`) que o cliente deseja realizar, incluindo os campos e filtros específicos que o cliente solicitou ou deseja modificar. O payload em GraphQL é flexível e adaptável, permitindo que o cliente solicite ou envie exatamente os dados necessários, o que reduz o tráfego e otimiza a comunicação entre o cliente e o servidor.

No contexto do GraphQL, o payload inclui:

1. **Query ou Mutation**: A definição da operação que o cliente quer executar. Isso especifica o que deve ser lido (query) ou modificado (mutation).
2. **Campos e Argumentos**: Campos específicos que o cliente deseja acessar ou atualizar. Isso permite a personalização da resposta para incluir apenas os dados necessários.
3. **Variáveis (opcional)**: Valores dinâmicos que podem ser utilizados na query ou mutação, facilitando a reutilização de queries com diferentes parâmetros.
4. **Resposta (Response Payload)**: Os dados que a API GraphQL devolve como resposta, que é estruturada exatamente de acordo com os campos especificados na requisição.

Aqui está um exemplo de payload de uma **requisição** GraphQL:

```graphql
query {
  user(id: "123") {
    id
    name
    email
  }
}
```

Neste caso, o payload enviado para a API inclui uma query que solicita informações do usuário com `id = 123`, com campos específicos (`id`, `name`, `email`).

O payload de **resposta** será estruturado com os dados solicitados:

```json
{
  "data": {
    "user": {
      "id": "123",
      "name": "Alice",
      "email": "alice@example.com"
    }
  }
}
```

O GraphQL usa o código de status HTTP `200 OK` por padrão, mesmo para respostas que incluem erros, pois a estrutura de resposta foi projetada para ser autossuficiente ao incluir um campo específico para erros. Isso ocorre porque, em uma consulta GraphQL, é possível que algumas partes da consulta sejam bem-sucedidas enquanto outras falham. Em GraphQL, mesmo que a resposta retorne com um código HTTP `200` OK, os erros são reportados no campo `errors` do payload de resposta. Isso significa que uma resposta com erros pode coexistir com dados válidos, possibilitando que partes da consulta sejam bem-sucedidas enquanto outras falham.

Aqui estão os principais motivos para essa prática:

1. **Estrutura de Resposta Unificada**: A resposta de uma consulta GraphQL é sempre retornada em um formato JSON padronizado, com um campo `"data"` para os dados solicitados e, se houver erros, um campo `"errors"` descrevendo-os. Isso permite ao cliente diferenciar entre dados bem-sucedidos e falhas dentro de uma mesma resposta.

2. **Suporte a Consultas Parciais**: Em uma única chamada, é possível solicitar dados de várias fontes. Se uma parte da consulta falha, o GraphQL ainda tenta retornar os dados disponíveis, junto com informações sobre o erro.

3. **Abstração de Erros de Transporte**: O foco do GraphQL está na estrutura e integridade dos dados, não no transporte (HTTP). A decisão de usar `200 OK` evita o uso do código HTTP para indicar a presença de erros, permitindo que o cliente trate os erros com base no conteúdo do JSON.

Por isso, ao usar GraphQL, os clientes devem sempre verificar o campo `"errors"` para garantir que a resposta é realmente completa e sem problemas.

Outro padrão do GraphQL, é uma resposta com valores nulos pode tanto indicar sucesso parcial quanto um problema em partes da consulta. Isso depende do contexto dos dados e da presença de um campo de erro.

Aqui estão as principais razões e cenários para esse comportamento:

1. **Sucesso Parcial**: Se uma consulta GraphQL busca múltiplos campos ou tipos de dados, e apenas alguns desses campos não puderem ser resolvidos (por exemplo, por causa de uma falha específica no servidor ou por permissões insuficientes), os campos com erro aparecerão como `null` na resposta. Isso permite que o restante dos dados ainda seja retornado e aproveitado.

2. **Erro Detalhado no Campo `"errors"`**: Mesmo com campos retornando `null`, se a execução da consulta encontrou problemas, eles serão detalhados no campo `"errors"`. Essa estrutura permite que o cliente identifique especificamente o que falhou, sem que a consulta inteira seja considerada um erro total.

3. **Sem Dados Encontrados**: Em alguns casos, um campo `null` pode simplesmente indicar que não há dados correspondentes sem necessariamente representar um erro. Por exemplo, um campo de relacionamento que não possui um registro correspondente ou um dado opcional que não foi preenchido.

Assim, no GraphQL, uma resposta com valores nulos não necessariamente significa erro. É crucial que os clientes analisem o campo `"errors"` e interpretem `null` de acordo com o contexto da consulta e da aplicação.

## [GraphQL] Mutation type

**Mutations** são os tipos GraphQL utilizados para adicionar, alterar e deletar dados, de forma similar às operações de `POST`, `PUT` e `DELETE` nos CRUDs desenvolvidos em REST.

Os tipos <a href="">Query</a> são obrigatórios em qualquer serviço GraphQL, porém Mutations são opcionais. Um exemplo de tipo Mutation para adicionar um novo livro:

```gql
type Mutation {
    adicionaLivro(titulo: String!, autoria: String!, paginas: Int!, colecoes: Colecao!): Livro!
}
```

Neste exemplo, temos somente uma **Mutation**, que chamamos de `adicionaLivro` e recebe por parâmetro os dados necessários. Confira os parâmetros com o tipo `Livro` definido anteriormente!

Além dos tipos acima, o GraphQL ainda tem mais tipos básicos:

- Enum,
- Input,
- Interface,
- Union.

```json
 "Pipefy": {
   "Domain": "https://api.pipefy.com",
   "Endpoint": "graphql",
   "Authorization": "Bearer [Token]",
   "Query": "mutation {                            \nchassi: updateCardField(input: {card_id: {cardId}, field_id: \"chassi\", new_value: \"{chassi}\"}) { success }\nrenavam: updateCardField(input: {card_id: {cardId}, field_id: \"renavam\", new_value: \"{renavam}\"}) { success }\nmotor: updateCardField(input: {card_id: {cardId}, field_id: \"n_mero_do_motor\", new_value: \"{motor}\"})  { success }\nmarca: updateCardField(input: {card_id: {cardId}, field_id: \"marca\", new_value: \"{marca\"}) { success }\nmodelo: updateCardField(input: {card_id: {cardId}, field_id: \"modelo\", new_value: \"{modelo}\"}) { success }\ncor: updateCardField(input: {card_id: {cardId}, field_id: \"cor\", new_value: \"{cor}\"}) { success }\ncombustivel: updateCardField(input: {card_id: {cardId}, field_id: \"combustivel\", new_value: \"{combustivel}\"}) { success }\nveianofabr: updateCardField(input: {card_id: {cardId}, field_id: \"veianofabr\", new_value: \"{veianofabr}\"}) { success }\nveianomodelo: updateCardField(input: {card_id: {cardId}, field_id: \"veianomodelo\", new_value: \"{anodemodelo}\"}) { success }\nmunicipio: updateCardField(input: {card_id: {cardId}, field_id: \"municipio\", new_value: \"{municipio}\"}) { success }\nuf: updateCardField(input: {card_id: {cardId}, field_id: \"uf\", new_value: \"{uf}\"}) { success }\n}}"
 }
```

## [GraphQL] SDL - Schema Definition Language
É importante trabalharmos com essa linguagem SDL, essa linguagem específica do Graphql, porque como o Graphql trabalha com várias linguagens de backend, como por exemplo Python, Node, JavaScript, usar essa linguagem dele garante uma padronização nos esquemas, por isso escrevemos os schemas usando essa linguagem própria do Graphql.

Então, como falamos anteriormente, o GraphQL tem sua própria linguagem, chamada de **SDL - Schema Definition Language**, linguagem de definição de schema. Isso porque é possível implementar o GraphQL em conjunto com qualquer outra linguagem, então a SDL serve para fazer essa integração de forma agnóstica.

Acabamos de criar nosso primeiro tipo, ainda vamos criar vários tipos, vamos falar bastante deles, então vamos em frente continuando para subirmos nosso primeiro servidor Graphql com Apollo. Para entender como essa linguagem funciona, sempre temos que ter em mente que o GraphQL trabalha com tipos, e saber quais tipos são esses.

<details><summary><b title="(click to open)">Node.js</b></summary><br />

Vamos começar com `npm install graphql`, que é a implementação referência para trabalhar **GraphQL com Node**.

[![NPM](https://img.shields.io/badge/-npm_install-fff?style=social&logo=NPM&logoColor=red)](#)

```sh
npm install graphql
```

<a href="https://www.apollographql.com/docs/apollo-server/"><img src="https://cdn.worldvectorlogo.com/logos/apollo-graphql-compact.svg" align="right" height="77"></a>

Como o GraphQL é realmente só uma especificação, usaremos também o pacote de ferramentas **Apollo** para trabalhar com GraphQL. O Apollo é uma implementação bem completa do GraphQL, ele já tem as ferramentas que precisaremos, começando pelo principal: um servidor GraphQL.

Exemplo: Vamos criar o arquivo `index.js` dentro da pasta "api". Este será nosso ponto de entrada da nossa aplicação.

[![NPM](https://img.shields.io/badge/-npm_install-fff?style=social&logo=NPM&logoColor=red)](#)

```sh
npm install apollo-server
```

Já instalamos o Apollo Server, agora vamos importá-lo. Por enquanto, queremos apenas o **ApolloServer** do pacote de ferramentas do Apollo:

[![index.js](https://img.shields.io/badge/-index.js-fff?style=social&logo=javascript&logoColor=ECD53F)](#)

```javascript
// Arquivo index.js

const { ApolloServer } = require('apollo-server')

const server = new ApolloServer()
```

O GraphQL faz uma separação clara entre **estrutura** e **comportamento**.

A estrutura do GraphQL está no schema, no qual especifica-se o que o servidor GraphQL está estruturado para fazer, com seus tipos e objetos.

Essa estrutura precisa ser implementada de alguma forma para que possa funcionar. No GraphQL, isso se dá através do que chamamos de funções `resolver`, ou só `resolvers`. É nos `resolvers` que implementamos o comportamento. Cada campo em um schema GraphQL é implementado através de um resolver.

É aqui que entram ferramentas como Apollo. Elas servem para nos ajudar a implementar a especificação GraphQL em nossa aplicação.

[![index.js](https://img.shields.io/badge/-index.js-fff?style=social&logo=javascript&logoColor=yellow)](#)

```javascript
// Arquivo index.js

const { ApolloServer } = require('apollo-server')

const server = new ApolloServer({ typeDefs, resolvers })
```

Precisamos passar para essa nova instância de `ApolloServer()` como parâmetro um objeto que tem duas propriedades. A primeira é `typeDefs` e a segunda é `resolvers`, como está na documentação. São partes fundamentais para entender o Graphql, então vamos começar vendo só o `typeDefs`, depois passamos para os `resolvers`.

[![index.js](https://img.shields.io/badge/-index.js-fff?style=social&logo=javascript&logoColor=yellow)](#)

```javascript
const { ApolloServer } = require('apollo-server')

const users = [
    {
        nome: "Ana",
        ativo: true
    },
    {
        nome: "Marcia",
        ativo: false
    }
]

const server = new ApolloServer({ typeDefs, resolvers })
```

O que é `typeDefs`, que tipo de definição de tipo é isso? Para entendermos como funcionam os tipos neste primeiro momento, vamos fazer o seguinte. Vou criar uma `const users` e dentro dela uma array com dois objetos. Vou fazer dois usuários bem simplificados, só com duas propriedades, a propriedade **nome**, que vou passar `Ana`, e se está **ativo** ou não, vou passar um booleano `true`.

Mais outro objeto, com **nome** `Marcia` e **ativo** `false`. Como o Graphql não se importa com a origem dos dados, vamos começar pequenos para poder focarmos no que é o `typeDefs`, no que são os tipos e o schema do Graphql.

Se pensarmos, como fazemos para definir uma query baseada nesses dados, quero fazer uma query que pegue usuários de uma base de dados, como vimos nos slides anteriores. Para isso precisamos definir um schema do Graphql. O **schema** é o centro, o core de qualquer servidor Graphql, porque ele define o que pode ser feito no servidor, o que dá para acessar e de que forma.

O **schema** então é composto por tipos, por `types`. Vamos usar a linguagem própria do Graphql para escrever esse schema aqui mesmo no nosso arquivo index, e dentro dele um tipo. 

> Como faríamos para escrever baseado na nossa `const users`, criar um objeto.

[![index.js](https://img.shields.io/badge/-index.js-fff?style=social&logo=javascript&logoColor=yellow)](#)

```javascript
const { ApolloServer } = require('apollo-server')

// Objeto
const users = [
    {
        nome: "Ana",
        ativo: true
    },
    {
        nome: "Marcia",
        ativo: false
    }
]

// Schema
type User {
  nome: String!
  ativo: Boolean!
  email: String
}

const server = new ApolloServer({ typeDefs, resolvers })
```

Ele vai chamar `type`, porque vamos criar o primeiro tipo da nossa definição de tipos `({ typeDefs })` que vai entrar no servidor do `ApolloServer()`. Vai ser um tipo `User`, com letra maiúscula, como é padrão do Graphql.

> Esse tipo `User` que estou criando agora vai ter três campos. O primeiro vai ser nome, como está lá em cima. Nome é um campo do tipo `String`, com letra maiúscula, como é definido pelo Graphql, e uma exclamação `!`. A exclamação significa que o campo não pode ser nulo, ele sempre tem que ter algum dado.

Ele vai ter também ativo, que vai ser um campo do tipo booleano, que também vai ser obrigatório, também vai ter exclamação, e vou colocar um terceiro campo, que vai ser o campo do tipo e-mail, e vai ser um campo do tipo string que não vai ser obrigatório, não vai ter exclamação. Ele pode ser nulo.

Mas tem um problema aqui. Eu criei esse type `User`, só que acabei de falar que íamos usar a linguagem própria do Graphql para isso, a **SDL - Scheme Definition Language**, linguagem de definição de esquemas. Como faço então para o JavaScript entender o que escrevi aqui?

Para isso vamos lá no `ApolloServer()`, na primeira linha onde importamos e vamos importar mais um módulo chamado `gql`. Com esse módulo `gql` consigo fazer o JavaScript interpretar o que está escrito na linguagem do Graphql, faço isso criando uma `const`, vou chamar de `typeDefs`, porque aqui dentro que estou definindo o meu schema, estou passando os tipos que vamos trabalhar nesse servidor, nessa nova instância de `ApolloServer()` que estamos criando aqui.

[![index.js](https://img.shields.io/badge/-index.js-fff?style=social&logo=javascript&logoColor=yellow)](#)

```javascript
const { ApolloServer, gql } = require('apollo-server')

// Objeto
const users = [
    {
        nome: "Ana",
        ativo: true
    },
    {
        nome: "Marcia",
        ativo: false
    }
]

// Primeiro tipo
const typeDefs = gql ` 
  type User {
    nome: String!
    ativo: Boolean!
    email: String
  }
`

// Schema
type User {
  nome: String!
  ativo: Boolean!
  email: String
}

const server = new ApolloServer({ typeDefs, resolvers })
```

Vai ser igual `gql` e vou abrir duas crases, as mesmas crases que usamos para criar templates strings no JavaScript, e entre essas crases vou passar meu `type User`. Agora acabamos de criar nosso primeiro tipo e nossa const `typeDefs` está aguardando o esquema de Graphql que vamos usar nesse nosso servidor que vamos subir daqui a pouco.

</details>

<details><summary><b title="(click to open)">.NET</b></summary><br />

```csharp
 // Query da mutation para atualizar o card no Pipefy - anonymous type
 var updateCardConsult = new
 {
     query = $@"
         mutation {{
             up_1: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""chassi"", new_value: ""{chassi}"" }}) {{ card {{ id }} }},
             up_2: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""renavam"", new_value: ""{renavam}"" }}) {{ card {{ id }} }},
             up_3: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""n_mero_do_motor"", new_value: ""{motor}"" }}) {{ card {{ id }} }},
             up_4: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""marca"", new_value: ""{marca}"" }}) {{ card {{ id }} }},
             up_5: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""modelo_1"", new_value: ""{modelo}"" }}) {{ card {{ id }} }},
             up_6: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""cor"", new_value: ""{cor}"" }}) {{ card {{ id }} }},
             up_7: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""combust_vel"", new_value: ""{combustivel}"" }}) {{ card {{ id }} }},
             up_8: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""ano_fabrica_o"", new_value: ""{veianofabr}"" }}) {{ card {{ id }} }},
             up_9: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""ano_modelo"", new_value: ""{veianomodelo}"" }}) {{ card {{ id }} }},
             up_10: updateCardField(input: {{ card_id: ""{cardId}"", field_id: ""tarjeta_do_munic_pio"", new_value: ""{municipio}"" }}) {{ card {{ id }} }}
         }}"
 };
```

</details>

<details><summary><b title="(click to open)">Python</b></summary><br />

</details>

<details><summary><b title="(click to open)">Java</b></summary><br />

</details>

<details><summary><b title="(click to open)">PHP</b></summary><br />

</details>

<details><summary><b title="(click to open)">Go</b></summary><br />

</details>

<details><summary><b title="(click to open)">Ruby</b></summary><br />

</details>

## [GraphQL] Apollo GraphQL Federation
<img src="https://www.vectorlogo.zone/logos/apollographql/apollographql-icon.svg" align="right" height="77">

**Apollo GraphQL Federation** é um modelo de arquitetura que permite que vários serviços GraphQL, conhecidos como subgráficos ou serviços federados (subgraphs), sejam combinados em um único esquema ou API. Este gráfico de dados unificado permite que os clientes consultem e recebam respostas de vários serviços usando uma única solicitação. A Apollo, uma empresa proeminente no ecossistema GraphQL, foi pioneira neste conceito para facilitar a integração perfeita de vários microsserviços e fontes de dados. Apollo Federation é independente da linguagem de programação. A arquitetura do Apollo Federation foi projetada para possibilitar a composição de múltiplos serviços GraphQL (subgraphs) em uma única "supergraph" unificada, independentemente da linguagem de cada serviço individual. Embora o Apollo Server seja uma implementação popular em JavaScript/TypeScript para serviços federados, você pode implementar subgraphs em qualquer linguagem, desde que eles sigam as especificações GraphQL e estejam em conformidade com os contratos do Apollo Federation.

Os princípios básicos da Federação GraphQL: 

- A Federação GraphQL permite a composição de vários serviços GraphQL implantados independentemente em um único esquema. Esse processo é facilitado pelo **Federation Gateway**, um servidor que se comunica com cada serviço federado, combina seus respectivos esquemas e resolve consultas recebidas. 

- Separação de Preocupações: Cada serviço federado pode ser desenvolvido, implantado e mantido independentemente, o que permite que as equipes trabalhem de forma autônoma e se concentrem em seus domínios específicos. 

- Extensões de Esquema: A Federação permite a extensão de tipos e campos entre serviços, permitindo a junção de dados perfeita e a resolução de dados relacionados de diferentes serviços.
  
- Planejamento de Consulta: Quando uma consulta é recebida, o gateway gera um plano de consulta, determinando o ideal.

<div align="center"><img src="https://github.com/user-attachments/assets/ac25eac7-91c8-4d8c-9e47-3f338b0399c9" height="277"></div>

Usar APIs REST diretamente de seus aplicativos da web, móveis e wearables geralmente resulta em baixo desempenho. No entanto, para desenvolvedores de aplicativos, existe um problema maior: encontrar as APIs REST certas, costurá-las manualmente em cada aplicativo e gerenciar novas versões de API REST que geralmente incluem alterações significativas. A implementação cuidadosa e a coordenação necessárias para evitar alterações significativas na API REST podem ser um grande desperdício de tempo para todas as equipes — tempo que não é gasto na entrega de novas experiências de aplicativo. 

O GraphQL é uma camada sobre seus microsserviços e APIs REST existentes que facilita para os desenvolvedores de aplicativos encontrar os dados de que precisam e criar uma única consulta GraphQL rápida. O GraphQL fornece uma fachada que desacopla as equipes de front-end e back-end para que as APIs REST subjacentes possam ser refatoradas mais facilmente. Uma consulta GraphQL pode recuperar os dados exatos necessários para alimentar uma nova experiência de aplicativo, como listar todos os produtos que um cliente comprou e a data em que os comprou:
