## INNER JOIN

O **INNER JOIN** permite juntar os dados relacionados de duas ou mais tabelas. A sintaxe é a seguinte:

```
SELECT t1.coluna, t2.coluna 
FROM tabela1 AS t1
INNER JOIN tabela AS t2
ON t1.coluna_em_comum = t2.coluna_em_comum
```

A **tabela1** e a **tabela2** são as que possuem os dados relacionados e o **ON** é a condição para conectar essas tabelas (o dado relacionado).

Uma representação gráfica do INNER JOIN:

![Imagem demonstrativa do INNER JOIN!](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/images/innerjoin-dcdd0d7b81d1843386871875fc408dd4.png)

Como você viu no exemplo, utilizamos o *Alias*(**AS**) na hora de declarar as tabelas que desejamos unir. O objetivo dele é apelidar uma parte da query, isso evita que ocorram erros de ambiguidade com nomes de coluna e para que fique mais fácil identificá-la (tanto quem está lendo o código, como para o próprio banco de dados). Suas *querys* ficam mais legíveis e bem estruturadas também.

Agora, qual *Alias* usar?

A principal importância dele é ajudar na identificação de uma parte da query, então o nome deve remeter e ser menor que o nome original, por exemplo, uma tabela chamada pagamentos, bom *alias* seriam p, pa, pag. No entanto, para *querys* mais complexas e com muitas linhas, o mais importante é que o *alias* seja descritivo, para facilitar na leitura.


#### Exercícios de Fixação:

Para os Exercícios, utilize a Base de Dados e tabelas a seguir (cole o código a seguir no seu *Workbench* selecione ele inteiro(ctrl + A) e aperte ctrl + Enter ou clique no ícone do raiozinho para rodá-lo):

```
CREATE DATABASE IF NOT EXISTS joins_exercises;

USE joins_exercises;

CREATE TABLE nome_idade(
  nome VARCHAR(20) NOT NULL,
  idade TINYINT NOT NULL,
);

CREATE TABLE nome_cidade(
  nome VARCHAR(20) NOT NULL,
  cidade VARCHAR(30) NOT NULL,
);

CREATE TABLE cidade_estado(
  cidade VARCHAR(20) NOT NULL,
  estado VARCHAR(20) NOT NULL,
);

INSERT INTO nome_idade(nome, idade)
VALUES
  ('Carlos', 20),
  ('José', 25),
  ('Julia', 21),
  ('Andressa', 20);

INSERT INTO nome_cidade(nome, idade)
VALUES
  ('Carlos', 'Curitiba'),
  ('José', 'Belo Horizonte'),
  ('Julia', 'São Paulo'),
  ('Andressa', 'Salvador');

INSERT INTO cidade_estado(nome, idade)
VALUES
  ('Curitiba', 'PR'),
  ('Belo Horizonte', 'MG'),
  ('São Paulo', 'SP'),
  ('Salvador', 'BA');
```

1. Monte uma *Query* que exiba o **nome**, a **cidade** e a **idade** de todas as pessoas na tabela nome_idade.

2. Monte uma *Query* que exiba o **nome** e o **estado** de todas as pessoas na tabela nome_cidade.

3. Monte uma *Query* que exiba o **nome**, a **cidade**, a **idade** e o **estado** das pessoas com **menos de 23 anos** na tabela nome_idade.

#### Gabarito

1. 
```
USE joins_exercises;
SELECT ni.nome, nc.cidade, ni.idade 
FROM nome_idade AS ni
INNER JOIN nome_cidade AS nc
ON ni.nome = nc.nome
```

2. 
```
USE joins_exercises;
SELECT nc.nome, ce.estado
FROM nome_cidade AS nc
INNER JOIN cidade_estado AS ce
ON nc.cidade = ce.cidade
```

3. 
```
USE joins_exercises;
SELECT ni.nome, nc.cidade, ni.idade, ce.estado
FROM nome_idade AS ni
INNER JOIN nome_cidade AS nc
ON ni.nome = nc.nome
INNER JOIN cidade_estado AS ce
ON nc.cidade = ce.cidade
WHERE ni.idade < 23
```