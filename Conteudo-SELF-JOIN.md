## SELF JOIN

O **SELF JOIN** é utilizado quando precisamos fazer uma análise dos dados presentes em uma mesma tabela, como por exemplo uma comparação. Logo, diferente dos outros JOINS vistos, não é necessário mais de uma tabela para realizá-lo.

Exemplo: 

Temos uma tabela com informações de filmes que saíram no cinema no último ano e queremos saber quais filmes que possuem a mesma classificação etária.

A sintaxe dele pode ser a seguinte:

`SELECT t1.nome, t1.duracao, t2.nome
FROM filme AS t1, filme AS t2
WHERE t1.duracao = t2.duracao`

Neste exemplo, teremos uma comparação do nome dos filmes que têm a mesma duração.

A sintaxe dele é bem flexível, podendo utilizar as dos exemplos dos outros JOINS.

#### Exercícios de Fixação: