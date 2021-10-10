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


### FULL OUTER JOIN

O **FULL OUTER JOIN** tem um comportamento parecido com o **RIGHT JOIN** e o **LEFT JOIN**, só que os dados apresentados são os dados inteiros de ambas as tabelas conectadas.

A sintaxe é a seguinte:

`SELECT t1.coluna1, t1.coluna2, t2.coluna1, t2.coluna2
FROM tabela1 AS t1
FULL OUTER JOIN tabela AS t2
ON t1.coluna2 = t2.coluna2`

Desta forma, teremos as colunas 1 e 2 da tabela 1 inteiras e as colunas 1 e 2 da tabela 2 inteiras e elas se interpondo onde a coluna 2 da tabela 1 for igual a coluna 2 da tabela 2.

A seguir uma imagem demonstrativa do **FULL OUTER JOIN**

![Imagem demonstrativa do FULL OUTER JOIN!](https://arquivo.devmedia.com.br/artigos/Fernanda_sallai/sql_join/image008.jpg)

#### Exercícios de Fixação: