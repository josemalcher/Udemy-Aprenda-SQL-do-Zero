# Resumo Udemy - Aprenda SQL do Zero

https://www.udemy.com/aprenda-sql-do-zero

---

## Lista 03 - Exercício

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

1) Crie no SqliteStudio um banco de dados chamado lista3.sqlite e execute os comandos abaixo.  
2) Crie uma tabela com o nome de livros contendo os campos codigo, titulo, codigo do autor, código da editora, código do estilo, sinopse e isbn. Sugestão  e nome de campo: autor_codigo, editora_codigo  
3) Crie uma tabela com o nome de editoras contendo o codigo, nome, cidade, estado, telefone e e-mail.  
4) Crie uma tabela com o nome de estilos contendo o código e o nome do estilo.  
5) Crie uma tabela com o nome de autores contendo o codigo, nome, cidade, estado, telefone do autor.  
6) Insira um registro na tabela livros (todos os campos)  
7) Insira um registro na tabela editoras (todos os campos).  
8) Insira um registro na tabela estilos (todos os campos).  
9) Insira um registro na tabela autores (todos os campos).  
10) Altere o nome da tabela autores para autor.  
11) Insira na tabela livros um novo registro adicionando somente os campos codigo e nome  
12) Insira 5 estilos de livros (comédia, drama, ficção, suspense, romance).  
13) Selecionar todos os livros do banco de dados.  
14) Insira 2 novos livros.  
15) Altere o nome da tabela livros autores para livro.  
16) DESAFIO: Selecione o nome de todos os estilos em ordem alfabética  
17) DESAFIO: Selecione o nome de todos os autores em ordem alfabética inversa  
18) Selecione o nome e o telefone de todas as editoras.  
19) Selecione o nome de todas as editoras  
20) Selecione o nome de todas as editoras de MG  
21) Selecione os estilos de livros em ordem alfabética.  
22) Selecione agora em ordem alfabética inversa.  
23) Selecione o nome de todos os autores de SP.  
24) Selecione o estilo de código 13  
25) Selecione o autor de código 8  
26) Selecione a editora de código 10  
27) Selecione o nome, a cidade e o estado de todas as editoras.  
28) Adicione 3 editoras.  
29) Selecione o nome de todas as editoras  
30) Exclua a editora de código 1  

---


1) Crie no SqliteStudio um banco de dados chamado lista5.sqlite e execute os comandos abaixo.  

2) Crie uma tabela com o nome de livro contendo os campos id, titulo, codigo do autor, código da editora, código do estilo, sinopse e isbn. Sugestão  e nome de campo: autor_codigo, editora_codigo  
```sql
sqlite> create table livro(id int, titulo text, id_autor int,id_editora int, id_estilo int, sinopse text, isbn int);
sqlite> .schema livro
CREATE TABLE livro(id int, titulo text, id_autor int,id_editora int, id_estilo int, sinopse text, isbn int);
sqlite>
```

3) Crie uma tabela com o nome de editoras contendo o codigo, nome, cidade, estado, telefone e e-mail.  

```sql
sqlite> create table editora(id int, nome text, cidade text, estado text, telefone text, email text);

```

4) Crie uma tabela com o nome de estilos contendo o código e o nome do estilo.  

```sql
sqlite> create table estilo(id int, nome text);
sqlite> .schema estilo
CREATE TABLE estilo(id int, nome text);
sqlite>
```

5) Crie uma tabela com o nome de autores contendo o codigo, nome, cidade, estado, telefone do autor.  

```sql
sqlite> create table autores(id int, nome text, cidade text, estado text, telefone text);
sqlite> .schema autores
CREATE TABLE autores(id int, nome text, cidade text, estado text, telefone text);
sqlite>
```

6) Insira um registro na tabela livros (todos os campos)  

```sql
sqlite> insert into livro(id, titulo,id_autor,id_editora,id_estilo, sinopse,isbn) values(1,"Nome livro qualquer 1",1,1,1,"Sinopse breve..", 123123);
```

7) Insira um registro na tabela editoras (todos os campos).  

```sql
sqlite> insert into editora(id,nome,cidade,estado,telefone,email) values(1,"Editora tal", "Belém", "PA","91 123456789","contato@email.com");
```

8) Insira um registro na tabela estilos (todos os campos).  

```sql
sqlite> insert into estilo(id, nome) values(1, "Estilo Terror");
```

9) Insira um registro na tabela autores (todos os campos).  

```sql
sqlite> insert into autores(id,nome,cidade,estado,telefone) values(1,"Nome Autor 1", "Belém","PA", "91 9889898989");
```

10) Altere o nome da tabela autores para autor.  

```sql
sqlite> alter table autores rename to autor;
sqlite> .table
autor    editora  estilo   livro
sqlite>
```

11) Insira na tabela livros um novo registro adicionando somente os campos codigo e nome  

```sql
sqlite> insert into livro(id, titulo) values(2,"Livro 02");
```

12) Insira 5 estilos de livros (comédia, drama, ficção, suspense, romance).  

```sql
sqlite> insert into estilo(id,nome) values(3,"Estilo Romance");
sqlite> insert into estilo(id,nome) values(2,"Estilo Policial");
sqlite> insert into estilo(id,nome) values(4,"Estilo Concurso");
sqlite> insert into estilo(id,nome) values(5,"Informatica");
sqlite> insert into estilo(id,nome) values(6,"Desenho");
```

13) Selecionar todos os livros do banco de dados.  

```sql
sqlite> .headers on
sqlite> select * from livro;
id|titulo|id_autor|id_editora|id_estilo|sinopse|isbn
1|Nome livro qualquer 1|1|1|1|Sinopse breve..|123123
2|Livro 02|||||
sqlite>
```

14) Insira 2 novos livros.  

```sql
sqlite> insert into livro(id, titulo,id_autor,id_editora,id_estilo, sinopse,isbn) values(2,"Nome livro qualquer 2",1,2,2,"Sinopse breve..tal tal", 144443); sqlite> insert into livro(id, titulo,id_autor,id_editora,id_estilo, sinopse,isbn) values(3,"Nome livro qualquer 3",1,1,2,"Sinopse breve.. tal", 133344);
sqlite> insert into livro(id, titulo,id_autor,id_editora,id_estilo, sinopse,isbn) values(3,"Nome livro qualquer 3",2,1,3,"Sinopse breve.. tal", 1533444);
sqlite> insert into livro(id, titulo,id_autor,id_editora,id_estilo, sinopse,isbn) values(5,"Nome livro qualquer 5",3,2,1,"Sinopse breve.. tal", 1533444);
sqlite> insert into livro(id, titulo,id_autor,id_editora,id_estilo, sinopse,isbn) values(6,"Nome livro qualquer 6",4,3,2,"Sinopse breve.. tal", 1533666);
sqlite> insert into livro(id, titulo,id_autor,id_editora,id_estilo, sinopse,isbn) values(7,"Nome livro qualquer 7",5,2,1,"Sinopse breve.. tal bla", 1533777);
```

15) Altere o nome da tabela livros autores para livro.  

```sql
alter table livros rename to livro;
```

16) DESAFIO: Selecione o nome de todos os estilos em ordem alfabética  

```sql
sqlite> select * from estilo;
id|nome
1|Estilo Terror
3|Estilo Romance
2|Estilo Policial
4|Estilo Concurso
5|Informatica
6|Desenho

sqlite> select * from estilo order by nome;
id|nome
6|Desenho
4|Estilo Concurso
2|Estilo Policial
3|Estilo Romance
1|Estilo Terror
5|Informatica
sqlite>
```

17) DESAFIO: Selecione o nome de todos os autores em ordem alfabética inversa  

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

sqlite> select * from autor order by nome desc;
id|nome|cidade|estado|telefone
7|Xicó Autor 7|Bragança|PA|91 1111143455
1|Nome Autor 1|Belém|PA|91 9889898989
5|Maria Autor 5|São leopoldo|SC|42 333443455
3|Jose Autor 3|São rock|SP|11 33333455
6|Fatima Autor 6|São Caetano O. V|PA|91 399943455
2|Autor 2|SP|SP|11 22334455
4|Ana Maria Autor 4|São Joaquim|SC|41 32223455
sqlite>
```

18) Selecione o nome e o telefone de todas as editoras.  

```sql
sqlite> select nome,telefone from editora;
nome|telefone
Editora tal|91 123456789
PA Editora 2|91 9999999
BA Editora 3|33 9888699
SP Editora|33 1118699
Capanema Editora|91 99938699
sqlite>
```

19) Selecione o nome de todas as editoras  

```sql
sqlite> select nome from editora;
nome
Editora tal
PA Editora 2
BA Editora 3
SP Editora
Capanema Editora
sqlite>
```

20) Selecione o nome de todas as editoras de PA  

```sql
sqlite> select * from editora where estado="PA";
id|nome|cidade|telefone|email|estado
1|Editora tal|Belém|91 123456789|contato@email.com|PA
2|PA Editora 2|Belém|91 9999999|contato@gmail.com|PA
4|Capanema Editora|Capanema|91 99938699|contatopa@gmail.com|PA
sqlite>
```

21) Selecione os estilos de livros em ordem alfabética.  

```sql
sqlite> select * from estilo order by nome;
id|nome
6|Desenho
4|Estilo Concurso
2|Estilo Policial
3|Estilo Romance
1|Estilo Terror
5|Informatica
sqlite>
```

22) Selecione agora em ordem alfabética inversa.  

```sql
sqlite> select * from estilo order by nome desc;
id|nome
5|Informatica
1|Estilo Terror
3|Estilo Romance
2|Estilo Policial
4|Estilo Concurso
6|Desenho
sqlite>
```

23) Selecione o nome de todos os autores de SP.  

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

sqlite> select * from autor where estado="SP";
id|nome|cidade|estado|telefone
2|Autor 2|SP|SP|11 22334455
3|Jose Autor 3|São rock|SP|11 33333455
sqlite>
```

24) Selecione o estilo de código 6  

```sql
sqlite> select * from estilo;
id|nome
1|Estilo Terror
3|Estilo Romance
2|Estilo Policial
4|Estilo Concurso
5|Informatica
6|Desenho

sqlite> select * from estilo where id=6;
id|nome
6|Desenho
sqlite>
```

25) Selecione o autor de código 4  

```sql
sqlite> select * from autor where id=4;
id|nome|cidade|estado|telefone
4|Ana Maria Autor 4|São Joaquim|SC|41 32223455
sqlite>
```

26) Selecione a editora de código 2  

```sql
sqlite> select * from editora where id=2;
id|nome|cidade|telefone|email|estado
2|PA Editora 2|Belém|91 9999999|contato@gmail.com|PA
sqlite>
```

27) Selecione o nome, a cidade e o estado de todas as editoras.  

```sql
sqlite> select nome,estado,cidade from editora;
nome|estado|cidade
Editora tal|PA|Belém
PA Editora 2|PA|Belém
BA Editora 3|BA|Farol Tal
SP Editora|SP|Sao Paulo
Capanema Editora|PA|Capanema
sqlite>
```

28) Adicione 3 editoras.  

```sql
sqlite> insert into editora(id,nome,cidade,telefone,email,estado) values(10,"editora abril","são paulo","11 992233","contato@email.com","SP");
sqlite> insert into editora(id,nome,cidade,telefone,email,estado) values(11,"editora do fulano esquina","são caetano sul","11 552233","contatoEditora@email.com","SP");
sqlite> insert into editora(id,nome,cidade,telefone,email,estado) values(13,"editora Funil","Salinas","91 552233","contatoSalEditora@email.com","PA");
sqlite>
```

29) Selecione o nome de todas as editoras  

```sql
sqlite> select nome from editora;
nome
Editora tal
PA Editora 2
BA Editora 3
SP Editora
Capanema Editora
editora abril
editora do fulano esquina
editora Funil
sqlite>
```

30) Exclua a editora de código 1  

```sql
sqlite> select * from editora;
id|nome|cidade|telefone|email|estado
1|Editora tal|Belém|91 123456789|contato@email.com|PA
2|PA Editora 2|Belém|91 9999999|contato@gmail.com|PA
3|BA Editora 3|Farol Tal|33 9888699|contatoba@gmail.com|BA
4|SP Editora|Sao Paulo|33 1118699|contatosp@gmail.com|SP
4|Capanema Editora|Capanema|91 99938699|contatopa@gmail.com|PA
10|editora abril|são paulo|11 992233|contato@email.com|SP
11|editora do fulano esquina|são caetano sul|11 552233|contatoEditora@email.com|SP
13|editora Funil|Salinas|91 552233|contatoSalEditora@email.com|PA

sqlite> delete from editora where id=1;

sqlite> select * from editora;
id|nome|cidade|telefone|email|estado
2|PA Editora 2|Belém|91 9999999|contato@gmail.com|PA
3|BA Editora 3|Farol Tal|33 9888699|contatoba@gmail.com|BA
4|SP Editora|Sao Paulo|33 1118699|contatosp@gmail.com|SP
4|Capanema Editora|Capanema|91 99938699|contatopa@gmail.com|PA
10|editora abril|são paulo|11 992233|contato@email.com|SP
11|editora do fulano esquina|são caetano sul|11 552233|contatoEditora@email.com|SP
13|editora Funil|Salinas|91 552233|contatoSalEditora@email.com|PA
sqlite>
```
