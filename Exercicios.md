## Exercícios

Para os exercícios, utilizaremos o banco de dados [sakila](https://s3.us-east-2.amazonaws.com/assets.app.betrybe.com/back-end/sakila-1ae15ae82697888c35bf1f1c8acbf755.sql). Para utilizá-lo, faça o download do arquivo, após isso, abra o arquivo em um editor de texto, copie todo seu conteúdo, cole no seu *workbench*, selecine tudo (ctrl + A) e execute com ctrl + Enter ou clicando no raiozinho. (Você também pode abrir o arquivo diretamente no seu *worknech* com **Shift+Ctrl+O**)

1. Monte uma *Query* que mostre a **cidade(city)** da tabela *city* e o nome dos **países(country)** ao qual essas cidades pertencem.

2. Monte uma *Query* que mostre o **endereço(address)** e o **distrito(district)** da tabela *address* e o nome das **cidades** desses endereços, ordene pelo nome das cidades em ordem alfabética.

3. Monte uma *Query* que mostre o **titulo do filme(title)**, a sua **descrição(description)**, a **duração(length)**, o **ano de lançamento(release year)** de todos os filmes com **mais de 90 minutos de duração**  tabela *film* e a **língua(language)** deles, ordene pelo título do filme em ordem alfabética.

4. Monte uma *Query* que mostre o **título** do filme e a **nome de sua categoria**(use o *Alias* **categoria**), ordene pelo título em ordem alfabética. (Utilize a tabela **film_category**)

5. Monte uma *Query* que mostre o **nome completo do ator(actor)**, utilize o *Alias* **nome**, e os **títulos dos filmes** em que esse ator apareceu. Ordene pelo nome do ator, no caso do mesmo nome, ordene pelo título do filme em ordem alfabética.

6. Monte uma *Query* com o **LEFT JOIN** mostrando o **nome completo** de todos os **atores** e o **nome completo** de quais clientes(customers) possuem o **PRIMEIRO nome** igual ao ator, ordene pelos nomes do atores em ordem alfabética.

7. Realize uma *Query* semelhante a anterior, só que use o **RIGHT JOIN** para mostrar o **nome completo** de todos os clientes, e o **nome completo** dos atores que possuem o **SOBRENOME** igual aos clientes, ordene pelo nome do cliente em ordem alfabética e mostre apenas **10** resultados a partir do resultado **51**.

8. Monte uma *Query* na tabela **film** exibindo o **título** e a **duração** de todos os filmes que possuem a mesma duração.

9. Monte uma *Query* que mostre o **título dos filmes** e seus **recursos adicionais(special_features)** para os filmes com a mesma **classificação etária(rating)**.

10. Monte uma *Query* que mostre as **cidades** que estão no mesmo país e o **código do país**(id), retire a própria cidade(já que com certeza ela estará no mesmo país que ela mesma :D) e ordene pelo código **decrescente** do país e depois pelo nome da cidade.

#### Bônus

11. Monte uma *Query* que mostre o **primeiro nome do ator(actor)**, os **títulos**, a **duração** e a **classificação etária** dos filmes, em que esse ator apareceu e o filme teve **mais de 85 minutos** e uma classificação etária **PG** . Ordene pelo nome do ator, no caso do mesmo nome, ordene pelo título do filme em ordem alfabética.

12. Monte uma *Query* que mostre o **título do filme** e a sua **categoria**, para todos os filmes que começarem com a **letra C** e tenham a categoria **ação(Action)**, ordene pelo título do filme em ordem alfabética.

13. Monte uma *Query* que mostre o **nome completo do ator** (com *Alias* nome), os **títulos dos filmes** em que participou e a **categoria**(com *Alias* categoria) desses filmes;

#### Gabaritos

1. 
```
USE sakila;
SELECT ci.city, co.country
FROM city AS ci
INNER JOIN country as co
ON ci.country_id = co.country_id;
```

2. 
```
USE sakila;
SELECT a.address, a.district, c.city
FROM address AS a
INNER JOIN city as c
ON a.city_id = c.city_id
ORDER BY c.city;
```
3. 
```
USE sakila;
SELECT f.title, f.description, f.release_year, f.length, l.name AS `language`
FROM film AS f
INNER JOIN `language` AS l
ON f.language_id = l.language_id
WHERE f.length > 90
ORDER BY f.title
```

4.
```
USE sakila;
SELECT f.title, c.name AS categoria
FROM film_category AS fc
INNER JOIN film AS f
ON f.film_id = fc.film_id
INNER JOIN category AS c
ON c.category_id = fc.category_id
ORDER BY f.title;
```

5. 
```
USE sakila;
SELECT CONCAT(a.FIRST_NAME, ' ', a.LAST_NAME) AS `nome` , f.title
FROM film_actor AS fa
INNER JOIN actor AS a
ON a.actor_id = fa.actor_id
INNER JOIN film AS f
ON f.film_id = fa.film_id
ORDER BY `nome`, f.title;
```

6.
```
USE sakila;
SELECT CONCAT(a.FIRST_NAME, ' ', a.LAST_NAME) AS actor_name, CONCAT(c.FIRST_NAME, ' ', c.LAST_NAME) AS customer_name
FROM actor AS a
LEFT JOIN customer as c
ON a.FIRST_NAME = c.FIRST_NAME
ORDER BY actor_name;
```

7.
```
USE sakila;
SELECT CONCAT(a.FIRST_NAME, ' ', a.LAST_NAME) AS actor_name, CONCAT(c.FIRST_NAME, ' ', c.LAST_NAME) AS customer_name
FROM actor AS a
RIGHT JOIN customer as c
ON a.LAST_NAME = c.LAST_NAME
ORDER BY customer_name
LIMIT 10
OFFSET 50;
```

8.
```
USE sakila;
SELECT t1.title, t1.length, t2.title
FROM film AS t1, film AS t2
WHERE t1.length = t2.length;
```

9.
```
USE sakila;
SELECT t1.title, t1.special_features, t2.title, t2.special_features
FROM film AS t1, film AS t2
WHERE t1.rating = t2.rating;
```

10.
```
USE sakila;
SELECT t1.city, t2.city, t1.country_id
FROM city AS t1, city AS t2
WHERE t1.country_id = t2.country_id
AND t1.city <> t2.city
ORDER BY t1.country_id, t1.city;
```

11. 
```
USE sakila;
SELECT a.FIRST_NAME, f.title, f.length, f.rating
FROM film_actor AS fa
INNER JOIN actor AS a
ON a.actor_id = fa.actor_id
INNER JOIN film AS f
ON f.film_id = fa.film_id
WHERE f.length > 85
AND f.rating = 'PG'
ORDER BY a.FIRST_NAME, f.title;
```

12.
```
USE sakila;
SELECT f.title, c.name AS categoria
FROM film_category AS fc
INNER JOIN film AS f
ON f.film_id = fc.film_id
INNER JOIN category AS c
ON c.category_id = fc.category_id
WHERE f.title LIKE 'C%'
AND c.name = 'Action'
ORDER BY f.title;
```

13.
```
USE sakila;
SELECT CONCAT(a.FIRST_NAME, ' ', a.LAST_NAME) AS `nome` , f.title, c.name AS categoria
FROM film_actor AS fa
INNER JOIN actor AS a
ON a.actor_id = fa.actor_id
INNER JOIN film AS f
ON f.film_id = fa.film_id
INNER JOIN film_category AS fc
ON f.film_id = fc.film_id
INNER JOIN category AS c
ON c.category_id = fc.category_id
ORDER BY `nome`, f.title;
```