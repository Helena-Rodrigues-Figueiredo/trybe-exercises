# Exercícios do dia 20.4

Para realizar as tarefas do 1 ao 7, restaure o seguinte banco de dados: <br />

```
DROP SCHEMA IF EXISTS Pixar;
CREATE SCHEMA Pixar;
USE Pixar;

CREATE TABLE Movies (
  id INTEGER auto_increment PRIMARY KEY NOT NULL,
  title VARCHAR(30) NOT NULL,
  director VARCHAR(30) NULL,
  year INT NOT NULL,
  length_minutes INT NOT NULL
);

CREATE TABLE BoxOffice (
  movie_id INTEGER,
  FOREIGN KEY (movie_id) REFERENCES Movies (id),
  rating DECIMAL(2,1) NOT NULL,
  domestic_sales INT NOT NULL,
  international_sales INT NOT NULL
);

INSERT INTO Movies(title, director, year, length_minutes)
  VALUES ('Toy Story', 'John Lasseter', 1995, 81),
         ('Vida de inseto', 'Andrew Staton', 1998, 95),
         ('ratatui', 'Brad Bird', 2010, 115),
         ('UP', 'Pete Docter', 2009, 101),
         ('Carros', 'John Lasseter', 2006, 117),
         ('Toy Story 2', 'John Lasseter', 1999, 93),
         ('Valente', 'Brenda Chapman', 2012, 98);


INSERT INTO BoxOffice(movie_id, rating, domestic_sales, international_sales)
  VALUES (1, 8.3, 190000000, 170000000),
         (2, 7.2, 160000000, 200600000),
         (3, 7.9, 245000000, 239000000),
         (4, 6.1, 330000000, 540000000),
         (5, 7.8, 140000000, 310000000),
         (6, 5.8, 540000000, 600000000),
         (7, 7.5, 250000000, 190000000);
```

## Exercícios

1 - Insira as produções da Pixar na tabela Movies: 
* Monstros SA, de Pete Docter, lançado em 2001, com 92 minutos de duração.
* Procurando Nemo, de John Lasseter, lançado em 2003, com 107 minutos de duração.
* Os Incríveis, de Brad Bird, lançado em 2004, com 116 minutos de duração.
* WALL-E, de Pete Docter, lançada em 2008, com 104 minutos de duração.

`INSERT INTO Movies (title, director, year, length_minute) VALUES` <br />
 `('Monstros SA', 'Pete Docter', 2001, 92),` <br />
 `('Procurando Nemo', 'John Lasseter', 2003, 107),` <br />
 `('Os Incríveis', 'Brad Bird', 2004, 116),` <br />
 `('WALL-E', 'Pete Docter', 2008, 104);`

2 - O filme Procurando Nemo foi classificado em 6.8, fez 450 milhões no mercado interno e 370 milhões no mercado internacional. Insira as informações à tabela BoxOffice. <br />

`INSERT INTO BoxOffice(movie_id, rating, domestic_sales, international_sales)` <br />
 `VALUE (9, 6.8, 450000000, 370000000);`
  
3 - O nome do diretor do filme "Procurando Nemo" está incorreto, ele foi dirigido por Andrew Staton. Corrija esse dado utilizando o comando UPDATE.<br />

`UPDATE Pixar.Movies` <br />
`SET director = 'Andrew Staton'` <br />
`WHERE title = 'Procurando Nemo';`

4 - O título do filme "Ratatouille" está incorreto na tabela Movies. Além disso, o filme foi lançado em 2007 e não em 2010. Corrija esses dados utilizando o comando UPDATE. <br />

`UPDATE Movies` <br />
`SET title = 'Ratatouille', year = 2007` <br />
`WHERE title = 'ratatui';`

5 - Insira as novas classificações abaixo na tabela BoxOffice, lembre-se que a coluna movie_id é uma foreign key referente a coluna id da tabela Movies: <br />
* Monsters SA, classificado em 8.5, lucrou 300 milhões no mercado interno e 250 milhões no mercado internacional.
* Os Incríveis, classificado em 7.4, lucrou 460 milhões no mercado interno e 510 milhões no mercado internacional.
* WALL-E, classificado em 9.9, lucrou 290 milhões no mercado interno e 280 milhões no mercado internacional.

`INSERT INTO BoxOffice(movie_id, rating, domestic_sales, international_sales)` <br />
  `VALUES (8, 8.5, 300000000, 250000000),` <br />
         `(10, 7.4, 460000000, 510000000),` <br />
         `(11, 9.9, 290000000, 280000000);`

6 - Exclua da tabela Movies o filme "WALL-E". <br />

`DELETE FROM BoxOffice` <br />
`WHERE movie_id = 11;` <br />

`DELETE FROM Movies` <br />
`WHERE title = 'WALL-E';`

7 - Exclua da tabela Movies todos os filmes dirigidos por "Andrew Staton".<br />

`DELETE FROM BoxOffice` <br />
`WHERE movie_id IN (2, 9);` <br />

`DELETE FROM Movies` <br />
`WHERE director = 'Andrew Staton';`
