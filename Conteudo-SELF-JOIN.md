## SELF JOIN

O **SELF JOIN** é utilizado quando precisamos fazer uma análise dos dados presentes em uma mesma tabela, como por exemplo uma comparação. Logo, diferente dos outros JOINS vistos, não é necessário mais de uma tabela para realizá-lo.

Exemplo: 

Temos uma tabela com informações de filmes que saíram no cinema no último ano e queremos saber quais filmes que possuem a mesma classificação etária.

A sintaxe dele pode ser a seguinte:

```
SELECT t1.nome, t1.duracao, t2.nome
FROM filme AS t1, filme AS t2
WHERE t1.duracao = t2.duracao
```

Neste exemplo, teremos uma comparação do nome dos filmes que têm a mesma duração.

A sintaxe dele é bem flexível, podendo utilizar as dos exemplos dos outros JOINS.

#### Exercícios de Fixação:

Para os Exercícios, utilize a Base de Dados e tabelas a seguir (cole o código a seguir no seu *Workbench* selecione ele inteiro(ctrl + A) e aperte ctrl + Enter ou clique no ícone do raiozinho para rodá-lo):

```
CREATE DATABASE IF NOT EXISTS joins_exercises;

USE joins_exercises;

CREATE TABLE filmes(
  id INT PRIMARY KEY AUTO_INCREMENT,
  titulo VARCHAR(20) NOT NULL,
  duracao TINYINT NOT NULL,
  lingua VARCHAR(20) NOT NULL,
  ano_lancamento INT NOT NULL,
);


INSERT INTO filmes(titulo, duracao, lingua, ano_lancamento)
VALUES
  ('O auto da compadecida', 104, 'Português', 2000),
  ('O lado bom da vida', 122, 'Inglês', 2012),
  ('As panteras', 98, 'Inglês', 2000),
  ('Filme imaginário', 104, 'Inglês', 2003);
```

1. Monte uma *Query* que mostre o **título** e a **língua** dos filmes que possuem a mesma língua.

2. Monte uma *Query* que mostre o **título** e a **duração** dos filmes que possuem a mesma duração.

#### Gabarito

1. 
```
USE joins_exercises;
SELECT t1.titulo, t1.lingua, t2.titulo
FROM filmes AS t1, filmes AS t2
WHERE t1.lingua = t2.lingua
AND t1.titulo <> t2.titulo;
```

2. 
```
USE joins_exercises;
SELECT t1.titulo, t1.duracao, t2.titulo
FROM filmes AS t1, filmes AS t2
WHERE t1.duracao = t2.duracao
AND t1.titulo <> t2.titulo;
```