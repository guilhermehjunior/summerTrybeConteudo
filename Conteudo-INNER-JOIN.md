## INNER JOIN

O **INNER JOIN** permite juntar os dados relacionados de duas ou mais tabelas. A sintaxe é a seguinte:

`SELECT t1.coluna, t2.coluna 
FROM tabela1 AS t1
INNER JOIN tabela AS t2
ON t1.coluna_em_comum = t2.coluna_em_comum`

A **tabela1** e a **tabela2** são as que possuem os dados relacionados e o **ON** é a condição para conectar essas tabelas (o dado relacionado).

Uma representação gráfica do INNER JOIN:

![Imagem demonstrativa do INNER JOIN!](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sql/images/innerjoin-dcdd0d7b81d1843386871875fc408dd4.png)

Como você viu no exemplo, utilizamos o *Alias*(**AS**) na hora de declarar as tabelas que desejamos unir. O objetivo dele é apelidar uma parte da query, isso evita que ocorram erros de ambiguidade com nomes de coluna e para que fique mais fácil identificá-la (tanto quem está lendo o código, como para o próprio banco de dados). Suas *querys* ficam mais legíveis e bem estruturadas também.

Agora, qual *Alias* usar?

A principal importância dele é ajudar na identificação de uma parte da query, então o nome deve remeter e ser menor que o nome original, por exemplo, uma tabela chamada pagamentos, bom *alias* seriam p, pa, pag. No entanto, para *querys* mais complexas e com muitas linhas, o mais importante é que o *alias* seja descritivo, para facilitar na leitura.


#### Exercícios de Fixação: