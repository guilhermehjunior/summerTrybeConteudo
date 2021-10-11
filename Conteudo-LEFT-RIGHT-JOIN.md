## LEFT JOIN e RIGHT JOIN

O **LEFT JOIN** tem como resultado todos os dados que estão na tabela da esquerda(a primeira tabela declara na *query*, ligada ao **FROM**) e os dados da tabela da direita (a tabela declarada após o **JOIN**) que são comuns com a tabela da esquerda (ligados pelo **ON**).

A sintaxe é similar a do **INNER JOIN**:

`SELECT t1.coluna1, t1.coluna2, t2.coluna1, t2.coluna2
FROM tabela1 AS t1
LEFT JOIN tabela AS t2
ON t1.coluna2 = t2.coluna2`

Desta forma, teremos as colunas 1 e 2 da tabela 1 inteiras, e as colunas 1 e 2 da tabela 2 quando o dado da coluna 2 da tabela 1 for igual o dado da coluna 2 da tabela 2.

O **RIGHT JOIN** apresenta o resultado praticamente igual ao **LEFT JOIN**, a diferença é que dessa vez os dados apresentados da tabela da esquerda serão só os relacionados, enquanto todos os dados da tabela da direita serão mostrados.

Olhando o mesmo exemplo, mas com **RIGHT JOIN**:

`SELECT t1.coluna1, t1.coluna2, t2.coluna1, t2.coluna2
FROM tabela1 AS t1
RIGHT JOIN tabela AS t2
ON t1.coluna2 = t2.coluna2`

Aqui teremos as colunas 1 e 2 da tabela 1 quando o dado da coluna 2 da tabela 1 for igual ao dado da coluna 2 da tabela 2, e as colunas 1 e 2 da tabela 2 inteiras.

A seguir imagens descritivas do **LEFT JOIN** e **RIGHT JOIN**:


#### LEFT JOIN
![Imagem demonstrativa do LEFT JOIN!](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/images/leftjoin-3bd116be2c7d08ac759c74353260cfea.png)

#### RIGHT JOIN
![Imagem demonstrativa do RIGHT JOIN!](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/images/rightjoin-f8109b9bb4ea1ed927109d1e19a1a262.png)


#### Exercícios de Fixação:

Para os Exercícios, utilize a Base de Dados e tabelas a seguir (cole o código a seguir no seu *Workbench* selecione ele inteiro(ctrl + A) e aperte ctrl + Enter ou clique no ícone do raiozinho para rodá-lo):

```
CREATE DATABASE IF NOT EXISTS joins_exercises;

USE joins_exercises;

DROP TABLE IF EXISTS nome_cidade;

CREATE TABLE nome_idade_2(
  nome VARCHAR(20) PRIMARY KEY,
  idade TINYINT NOT NULL
);

CREATE TABLE nome_cidade(
  nome VARCHAR(20) PRIMARY KEY,
  cidade VARCHAR(30) NOT NULL
);

INSERT INTO nome_idade_2(nome, idade)
VALUES
  ('Carlos', 20),
  ('José', 25),
  ('Sylvia', 21),
  ('Victor', 20);

INSERT INTO nome_cidade(nome, cidade)
VALUES
  ('Carlos', 'Curitiba'),
  ('José', 'Belo Horizonte'),
  ('Julia', 'São Paulo'),
  ('Andressa', 'Salvador');
```

1. Monte uma *Query* com o **LEFT JOIN** que retorne todos os **nomes** da tabela **nome_idade_2** e as **cidades** deles.

2. Monte uma *Query* com o **RIGHT JOIN** que retorne todos os nomes da tabela **nome_cidade** e as **idades** deles, ordene o resultado pela ordem alfabética dos nomes.


#### Gabarito

1. 
```
USE joins_exercises;
SELECT ni2.nome, nc.cidade
FROM nome_idade_2 AS ni2
LEFT JOIN nome_cidade AS nc
ON ni2.nome = nc.nome;
```

2.
```
USE joins_exercises;
SELECT ni2.idade, nc.nome
FROM nome_idade_2 AS ni2
RIGHT JOIN nome_cidade AS nc
ON ni2.nome = nc.nome
ORDER BY nc.nome;
```