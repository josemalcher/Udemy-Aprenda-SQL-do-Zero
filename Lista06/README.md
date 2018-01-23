# Resumo Udemy - Aprenda SQL do Zero

https://www.udemy.com/aprenda-sql-do-zero

---

## Lista 06 - Exercício

Observações:  
· Para realização dos exercícios é necessário que você baixe o sqlite e coloque-o em sua área de trabalho. Depois você precisará abrir o cmd para executar com o nome correto do banco de dados conforme pedido.  
· Pode pesquisar a vontade e conversar com seus colegas. O Google é seu amigo.  
· Não reclame que não sabe. Pesquise, tente, teste e refaça! Mude sua postura de “Não sei fazer” para “Vou descobrir como se faz”. Anote a resposta de TODOS os exercícios. Irá te ajudar lá na frente!  
· Não pule nenhum exercício achando que “já sabe”.  
· Nomes de tabelas, campos e banco de dados NÃO devem possuir acentos e cedilha.  
· Lembre-se que o “;” finaliza os comandos.  
· Os tipos de dados basicamente são: int para inteiros, text para texto, real para números com decimais, date para datas e boolean para booleanos. Você também pode usar para campos texto o tipo varchar especificando o tamanho. Para valores monetários você pode usar o tipo real.  
· Sua missão é resolver todas as questões. Não pare antes disso.  

---

1) Abra no SQLite Studio o banco de dados com o controle de livros que desenvolvemos.  
2) Selecione o nome e o estilo de todos os livros  
3) Selecione o nome e a editora de todos os livros  
4) Selecione o nome e o autor de todos os livros  
5) Selecione o nome e o estilo de todos os livros que começam por “A”  
6) Selecione o nome e o estilo de todos os livros que cujo estilo comece por “R”  
7) Selecione o nome do autor, da editora, do estilo e do livro de todos os livros de autores cujo  nome  comece por D.  
8) Selecione o nome do autor, da editora, do estilo e do livro de todos os livros de editoras paulistas.  
9) Atualize o autor do livro de id 1 para autor_id 2.  
10) Atualize o telefone da editora de id 3 para 44 6666-6666  
11) Atualize o nome do autor 8 para “Graciliano Ramos”  
12) Atualize o estilo 5 para Fantasia.  
13) Selecione o nome do livro e do estilo de todas as editoras de SP.  
14) Selecione o nome do livro e da Editora de todas as editoras de SP.  
15) Selecione o nome do livro e do autor de em ordem alfabética por autor.  

---

1) Abra no SQLite Studio o banco de dados com o controle de livros que desenvolvemos.  

```sql
λ sqlite3.exe lista6.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite>
```

2) Selecione o nome e o estilo de todos os livros  

```sql
sqlite> select  l.titulo, e.nome 
        from livro l, estilo e 
        where e.id = l.id_estilo;
titulo|nome
Nome livro qualquer 1|Estilo Terror
Nome livro qualquer 2|Estilo Policial
Nome livro qualquer 3|Estilo Policial
Nome livro qualquer 3|Estilo Romance
Nome livro qualquer 5|Estilo Terror
Nome livro qualquer 6|Estilo Policial
Nome livro qualquer 7|Estilo Terror
sqlite>
```

3) Selecione o nome e a editora de todos os livros  

```sql
sqlite> SELECT l.titulo, e.nome 
        from livro l, editora e 
        where e.id = l.id_editora;
titulo|nome
Nome livro qualquer 2|PA Editora 2
Nome livro qualquer 5|PA Editora 2
Nome livro qualquer 6|BA Editora 3
Nome livro qualquer 7|PA Editora 2
sqlite>
```

4) Selecione o nome e o autor de todos os livros  

```sql
sqlite> select a.nome, l.titulo 
        from autor a, livro l 
        where a.id = l.id_autor;
nome|titulo
Nome Autor 1|Nome livro qualquer 1
Nome Autor 1|Nome livro qualquer 2
Nome Autor 1|Nome livro qualquer 3
Autor 2|Nome livro qualquer 3
Jose Autor 3|Nome livro qualquer 5
Ana Maria Autor 4|Nome livro qualquer 6
Maria Autor 5|Nome livro qualquer 7
sqlite>
```

5) Selecione o nome e o estilo de todos os livros que começam por “Terror”  

```sql
sqlite> select l.titulo, e.nome 
        from livro l, estilo e 
        where e.id = l.id_estilo 
        and e.nome like "%Terror";
titulo|nome
Nome livro qualquer 1|Estilo Terror
Nome livro qualquer 5|Estilo Terror
Nome livro qualquer 7|Estilo Terror
sqlite>
```

6) Selecione o nome e o estilo de todos os livros que cujo estilo comece por “Policial”  

```sql
sqlite> select livro.titulo, estilo.nome 
        from livro, estilo 
        where estilo.id = livro.id_estilo 
        and estilo.nome like "%Policial";
titulo|nome
Nome livro qualquer 2|Estilo Policial
Nome livro qualquer 3|Estilo Policial
Nome livro qualquer 6|Estilo Policial
sqlite>
```

7) Selecione o nome do autor, da editora, do estilo e do livro de todos os livros de autores cujo  nome  comece por "Ana".  

```sql
sqlite> select a.nome, e.nome, est.nome, l.titulo 
        from autor a, editora e, estilo est, livro l 
        where a.id = l.id_autor 
        and e.id = l.id_estilo 
        and est.id = l.id_estilo 
        and a.nome like "Ana%";
nome|nome|nome|titulo
Ana Maria Autor 4|PA Editora 2|Estilo Policial|Nome livro qualquer 6
sqlite>
```

8) Selecione o nome do autor, da editora, do estilo e do livro de todos os livros de editoras paraenses(PA).  

```sql
sqlite> select a.nome, e.nome, est.nome, l.titulo, e.estado 
        from autor a, editora e, estilo est, livro l 
        where a.id = l.id_autor 
        and e.id = l.id_editora 
        and est.id = l.id_estilo 
        and e.estado like "PA";
nome|nome|nome|titulo|estado
Nome Autor 1|PA Editora 2|Estilo Policial|Nome livro qualquer 2|PA
Jose Autor 3|PA Editora 2|Estilo Terror|Nome livro qualquer 5|PA
Maria Autor 5|PA Editora 2|Estilo Terror|Nome livro qualquer 7|PA
sqlite>
```

9) Atualize o autor do livro de id 1 para autor_id 2.  

```sql
sqlite> UPDATE livro set id_autor = 2 WHERE id = 1;
```

10) Atualize o telefone da editora de id 3 para 44 6666-6666  

```sql
sqlite> select * from editora;
id|nome|cidade|telefone|email|estado
2|PA Editora 2|Belém|91 9999999|contato@gmail.com|PA
3|BA Editora 3|Farol Tal|33 9888699|contatoba@gmail.com|BA
4|SP Editora|Sao Paulo|33 1118699|contatosp@gmail.com|SP
4|Capanema Editora|Capanema|91 99938699|contatopa@gmail.com|PA
10|editora abril|são paulo|11 992233|contato@email.com|SP
11|editora do fulano esquina|são caetano sul|11 552233|contatoEditora@email.com|SP
13|editora Funil|Salinas|91 552233|contatoSalEditora@email.com|PA

sqlite> update editora set telefone = "6666-6666" where id=3;

sqlite> select * from editora;
id|nome|cidade|telefone|email|estado
2|PA Editora 2|Belém|91 9999999|contato@gmail.com|PA
3|BA Editora 3|Farol Tal|6666-6666|contatoba@gmail.com|BA
4|SP Editora|Sao Paulo|33 1118699|contatosp@gmail.com|SP
4|Capanema Editora|Capanema|91 99938699|contatopa@gmail.com|PA
10|editora abril|são paulo|11 992233|contato@email.com|SP
11|editora do fulano esquina|são caetano sul|11 552233|contatoEditora@email.com|SP
13|editora Funil|Salinas|91 552233|contatoSalEditora@email.com|PA
sqlite>
```

11) Atualize o nome do autor 2 para “Graciliano Ramos”  

```sql
sqlite> select * from autor;
id|nome|cidade|estado|telefone
1|Nome Autor 1|Belém|PA|91 9889898989
2|Autor 2|SP|SP|11 22334455
3|Jose Autor 3|São rock|SP|11 33333455
4|Ana Maria Autor 4|São Joaquim|SC|41 32223455
5|Maria Autor 5|São leopoldo|SC|42 333443455
6|Fatima Autor 6|São Caetano O. V|PA|91 399943455
7|Xicó Autor 7|Bragança|PA|91 1111143455

sqlite> update autor set nome= "Graciliano Ramos" where id=2;

sqlite> select * from autor;
id|nome|cidade|estado|telefone
1|Nome Autor 1|Belém|PA|91 9889898989
2|Graciliano Ramos|SP|SP|11 22334455
3|Jose Autor 3|São rock|SP|11 33333455
4|Ana Maria Autor 4|São Joaquim|SC|41 32223455
5|Maria Autor 5|São leopoldo|SC|42 333443455
6|Fatima Autor 6|São Caetano O. V|PA|91 399943455
7|Xicó Autor 7|Bragança|PA|91 1111143455
sqlite>
```

12) Atualize o estilo 5 para Fantasia.  

```sql
sqlite> select * from estilo;
id|nome
1|Estilo Terror
3|Estilo Romance
2|Estilo Policial
4|Estilo Concurso
5|Informatica
6|Desenho

sqlite> update estilo set nome="Fantasia" where id=5;

sqlite> select * from estilo;
id|nome
1|Estilo Terror
3|Estilo Romance
2|Estilo Policial
4|Estilo Concurso
5|Fantasia
6|Desenho
sqlite>
```
13) Selecione o nome do livro e do estilo de todas as editoras de BA.  

```sql
sqlite> select l.titulo, e.nome, ed.estado from livro l, estilo e, editora ed where e.id = l.id_estilo and ed.id = l.id_editora and ed.estado like "BA";
titulo|nome|estado
Nome livro qualquer 6|Estilo Policial|BA
sqlite>
```

14) Selecione o nome do livro e da Editora de todas as editoras de BA.  

```sql
sqlite> select l.titulo, e.nome, e.estado from livro l, editora e where e.id = l.id_editora and e.estado like "BA";

titulo|nome|estado
Nome livro qualquer 6|BA Editora 3|BA
sqlite>
```

15) Selecione o nome do livro e do autor de em ordem alfabética por autor.  


```sql
sqlite> select l.titulo, a.nome from livro l, autor a where a.id = l.id_autor ORDER BY a.nome ;
titulo|nome
Nome livro qualquer 6|Ana Maria Autor 4
Nome livro qualquer 3|Graciliano Ramos
Nome livro qualquer 5|Jose Autor 3
Nome livro qualquer 7|Maria Autor 5
Nome livro qualquer 1|Nome Autor 1
Nome livro qualquer 2|Nome Autor 1
Nome livro qualquer 3|Nome Autor 1
sqlite>
```
