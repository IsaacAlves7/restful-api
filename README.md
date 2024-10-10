# ⚛︎ GraphQL
<a href="https://graphql.org/"><img src="https://cdn.worldvectorlogo.com/logos/graphql-logo-2.svg" height="77" align="right"></a>

O **GraphQL** é uma especificação para criar e usar APIs que têm sua própria linguagem de query. O que isso significa então? É que às vezes o Graphql é entendido ou é percebido como sendo uma tecnologia voltada para bancos de dados, ele não é. Ele é uma especificação para APIs, para escrever, criar e utilizar APIs e não está ligado a nenhum tipo de banco, inclusive ele pode ser usado com qualquer base de dados, ou mesmo nenhuma base de dados. O GraphQL é uma linguagem de queries para manipular dados em APIs e não está vinculada a nenhum banco de dados ou linguagem de programação específica. Não importa se os dados vêm de objetos, de tabelas diferentes, de vários endpoints de uma API. A ideia é que o cliente consiga receber os dados da melhor forma possível. GraphQL é uma especificação pensada na forma como clientes utilizarão os dados, não de que forma estão gravados nem de onde vêm. Não importa se os dados vêm de objetos, de tabelas diferentes, de vários endpoints de uma API. A ideia é que o cliente consiga receber os dados da melhor forma possível.

O GraphQL é uma ferramenta para construirmos de forma ágil APIs que são rápidas e versáteis. Ou seja, o uso de GraphQL agiliza o desenvolvimento de novas features de um produto. O back-end não precisa desenvolver novos endpoints para cada nova funcionalidade, ao contrário do REST. Isso torna o desenvolvimento de produtos mais ágil.

O Graphql fornece um ambiente para executarmos essas queries usando os dados que fornecermos para ele, não importa de onde esses dados venham. Eles podem vir de um banco SQL, de um banco NoSQL, de uma API de terceiros via endpoint REST, ou até mesmo da memória do seu computador. E também de todos esses juntos, para o SQL não faz diferença, isso não é o ponto principal dele.

O Graphql também normalmente utilizamos o protocolo HTTP para fazer a comunicação, mas na verdade ele é agnóstico com relação a protocolos de comunicação. Os **schemas** (esquemas) do Graphql são baseados em como os dados são usados, e não como estão armazenados. Isso é um conceito chave para entender o Graphql, não importa se os dados vêm de objetos, de APIs, o que acabamos de falar, o que importa é que o cliente consiga utilizar esses dados da melhor forma possível.

Quando falo cliente normalmente estou falando do front ou de quem vai consumir nossa API Graphql. Essa é uma questão chave. Os schemas são baseados em como os dados são usados, e não importa de onde eles vêm.

Por exemplo, se usássemos um banco de tabelas para criar um usuário, por exemplo, um usuário de uma escola de inglês, esses usuários têm nome, e-mail, se eles estão ativos no sistema ou não, e eles podem ser professores, podem ser alunos, podem ser coordenação. Se pensarmos, por exemplo, numa tabela SQL, conseguimos montar um usuário completo a partir de duas tabelas, uma com os dados principais, nome, e-mail, etc, e outra para definir os possíveis roles, os possíveis papeis desse usuário no sistema.

Então você teria uma tabela de roles que tem professor, aluno, coordenação, e por aí vai. Com o Graphql pensamos em como esses dados seriam usados pelo lado cliente e o cliente pode montar as queries a partir dessa premissa.

Vamos supor que numa `feature` qualquer desse sistema de escola de cliente, o lado cliente precisa receber somente o nome do usuários da tabela `users` e da tabela `roles` ele só precisa receber uma `string` com o tipo de role, professor, aluno, etc. Ele não precisa receber mais nada.

Ele quer fazer uma query que pegue de `users` somente o nome, e do `role` desse user, do papel desse usuário, somente a string de tipo, ele não quer receber mais nada, somente isso.

A partir dessa query que o cliente consegue fazer em Graphql ele recebe um JSON somente com o que ele quer no formato agregado de uma forma que para o cliente faz mais sentido, são dados mais concisos e somente com o que o cliente pediu.

O Graphql com isso procura resolver um problema em rest, uma questão do rest que costumamos chamar de **overfitting**, que seria **super requisição**, e também o **underfitting**, que é **sub requisição**. É quando o endpoint ou traz muitos dados que não precisamos numa requisição ou o contrário, precisamos de mais de uma requisição para ter os dados que precisamos. Então, o Graphql vem aí para resolver essa questão e fazer com que nosso cliente peça, em uma requisição só ele receba somente o que ele quer e mais nada. Podemos dizer que o Graphql é uma tecnologia voltada para front? Podemos, porque a ideia é melhorar, otimizar essa relação dos clientes com os dados que ele recebe do back, que é uma tecnologia focada no front, mas claro que vamos desenvolver nosso servidor Graphql no back.

Para o cliente, para a parte de front, ele vai ter menos requisições, vai visualizar os dados de uma forma melhor, os dados agregados de uma forma melhor para ele, mas dados mais enxutos, inclusive, de forma que faça mais sentido para ele, mas também tem bastante benefícios para a parte do back, para o lado do servidor, uma vez que livra o backend de fazer muitas implementações de muitos endpoints.

O desenvolvimento fica mais ágil. Se você tem que desenvolver um novo produto ou uma nova `feature` para o seu produto, evita que o backend caia naquela situação de ter que desenvolver endpoints sem fim para cada coisa nova que pode ou não entrar no sistema.

Fica mais ágil porque o front não fica dependendo tanto do back para criar um endpoint para cada coisa que ele precisa fazer, e o backend fica mais agilizado também sem ter que ficar fazendo todas essas implementações para uma coisa que no final às vezes pode até entrar no sistema ou não.

Vamos começar com `npm install graphql`, que é a implementação referência para trabalhar **GraphQL com Node**.

[![NPM](https://img.shields.io/badge/-npm_install-fff?style=social&logo=NPM&logoColor=red)](#)

```sh
npm install graphql
```

Como o GraphQL é realmente só uma especificação, usaremos também o pacote de ferramentas **Apollo** para trabalhar com GraphQL:

[![NPM](https://img.shields.io/badge/-npm_install-fff?style=social&logo=NPM&logoColor=red)](#)

```sh
npm install apollo-server
```

O Apollo é uma implementação bem completa do GraphQL, ele já tem as ferramentas que precisaremos, começando pelo principal: um servidor GraphQL.

Vamos criar o arquivo `index.js` dentro da pasta "api". Este será nosso ponto de entrada da nossa aplicação.

Já instalamos o Apollo Server, agora vamos importá-lo. Por enquanto, queremos apenas o **ApolloServer** do pacote de ferramentas do Apollo:

[![index.js](https://img.shields.io/badge/-index.js-fff?style=social&logo=javascript&logoColor=ECD53F)](#)

```javascript
// Arquivo index.js

const { ApolloServer } = require('apollo-server')

const server = new ApolloServer()
```

<a href="https://www.apollographql.com/docs/apollo-server/"><img src="https://cdn.worldvectorlogo.com/logos/apollo-graphql-compact.svg" align="right" height="77"></a>

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

> É importante trabalharmos com essa linguagem SDL, essa linguagem específica do Graphql, porque como o Graphql trabalha com várias linguagens de backend, como por exemplo Python, Node, JavaScript, usar essa linguagem dele garante uma padronização nos esquemas, por isso escrevemos os schemas usando essa linguagem própria do Graphql.

Acabamos de criar nosso primeiro tipo, ainda vamos criar vários tipos, vamos falar bastante deles, então vamos em frente continuando para subirmos nosso primeiro servidor Graphql com Apollo.

Então, como falamos anteriormente, o GraphQL tem sua própria linguagem, chamada de SDL, ou Schema Definition Language, linguagem de definição de schema. Isso porque é possível implementar o GraphQL em conjunto com qualquer outra linguagem, então a SDL serve para fazer essa integração de forma agnóstica.

Para entender como essa linguagem funciona, sempre temos que ter em mente que o GraphQL trabalha com tipos, e saber quais tipos são esses.

**[GraphQL] SCALAR TYPES**

São tipos que refletem alguns dos tipos de dados que já conhecemos. Para o GraphQL, são os tipos que se resolvem em dados concretos (ao contrário de objetos, por exemplo, que são conjuntos de dados). São eles:

- `Int` - inteiro de 32 bits
- `Float` - tipo ponto flutuante
- `String` - sequência de caracteres no formato `UTF-8`
- `Boolean` - `true` ou `false`
- `ID` - identificador único, usado normalmente para localizar dados. É possível criar tipos scalar customizados, estudaremos mais adiante.

**[GraphQL] OBJECT TYPE**

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

**[GraphQL] QUERY TYPE**

Os **tipos Query** definem os pontos de entrada (entry points) da API; indicam quais dados o cliente pode receber e de que forma, de certa forma, são como queries do tipo `GET` quando trabalhamos com REST, a diferença aqui é que o cliente tem mais liberdade para montar as queries para receber apenas os dados que precisa lembrando que, para o GraphQL e também para o cliente, não importa a origem desses dados. os dados podem vir de diversas fontes: endpoints REST, bancos SQL e NoSQL, outro servidor GraphQL.

Um exemplo de tipo Query:

```gql
type Query {
    livros: [Livro!]!
    livro(id: ID!): Livro!
}
```

Aqui definimos a query `livros`, que retorna uma array composta por **tipos objeto** `Livro`, e a **query** `livro`, que recebe um número de `ID` por parâmetro e retorna um **objeto** `Livro` referente ao `ID` informado.

Uma vez que as queries são os pontos de entrada de uma API GraphQL, toda aplicação vai ter pelo menos uma Query em seu schema.

**[GraphQL] MUTATION TYPE**

**Mutations** são os tipos GraphQL utilizados para adicionar, alterar e deletar dados, de forma similar às operações de `POST`, `PUT` e `DELETE` nos CRUDs desenvolvidos em REST.

Os **tipos Query** são obrigatórios em qualquer serviço GraphQL, porém Mutations são opcionais. Um exemplo de tipo Mutation para adicionar um novo livro:

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
