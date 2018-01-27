# Resumo Udemy - Aprenda SQL do Zero

https://www.udemy.com/aprenda-sql-do-zero

---

## <a name="indice">Índice</a>

- [Preparação do ambiente de desenvolvimento](#parte1)  
- [Esquentando os motores](#parte2)  
- [Criando tabelas e inserindo informações](#parte3)  
- [Selecionando e Extraindo informações](#parte4)  
- [Tabelas também se relacionam](#parte5)  
- [Aprendendo COUNT, MIN, MAX, AVG](#parte6)  
- [Vamos aprender umas coisas legais](#parte7)  
- [Isso tá muio fácil! Quero recursos avançados!](#parte8)  
- [Fechamento](#parte9)  

---

## <a name="parte1">Preparação do ambiente de desenvolvimento</a>

"Structured Query Language, ou Linguagem de Consulta Estruturada ou SQL, é a linguagem de pesquisa declarativa padrão para banco de dados relacional (base de dados relacional). Muitas das características originais do SQL foram inspiradas na álgebra relacional." (https://pt.wikipedia.org/wiki/SQL)



[Voltar ao Índice](#indice)

---

## <a name="parte2">Esquentando os motores</a>

https://www.sqlite.org/index.html

https://sqlitestudio.pl/index.rvt

[Voltar ao Índice](#indice)

---

## <a name="parte3">Criando tabelas e inserindo informações</a>

### 10. Criando uma tabela

```
λ sqlite3.exe aula01.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite> create table agenda(nome text, telefone text);
sqlite> .tables
agenda
sqlite> create table alunos(matricula integer, nome text, telefone text, cidade text);

sqlite> .tables
agenda  alunos
sqlite> create table produtos (codigo integer, nome text, qtd integer);
sqlite> .tables
agenda    alunos    produtos
sqlite> .exit
```
#### DDL - Linguagem de Definição de Dados

O segundo grupo é a DDL (Data Definition Language - Linguagem de Definição de Dados). Uma DDL permite ao utilizador definir tabelas novas e elementos associados. A maioria dos bancos de dados de SQL comerciais tem extensões proprietárias no DDL.

Os comandos básicos da DDL são poucos:

- CREATE: cria um objeto (uma Tabela, por exemplo) dentro da base de dados.  
- DROP: apaga um objeto do banco de dados.  

Alguns sistemas de banco de dados usam o comando ALTER, que permite ao usuário alterar um objeto, por exemplo, adicionando uma coluna a uma tabela existente.

Outros comandos DDL:

- CREATE TABLE  
- CREATE INDEX  
- CREATE VIEW  
- ALTER TABLE  
- ALTER INDEX  
- DROP INDEX  
- DROP VIEW  

### 11. Inserindo informações

```
λ sqlite3.exe aula01.sqlite             SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite> .schema
CREATE TABLE agenda(nome text, telefone text);
CREATE TABLE alunos(matricula integer, nome text, telefone text, cidade text);
CREATE TABLE produtos (codigo integer, nome text, qtd integer);
sqlite>
sqlite> insert into agenda(nome, telefone) values ("Jose", "988889900");
sqlite> insert into agenda(nome, telefone) values ("Beta", "111111111");

sqlite> select * from agenda;
Jose|988889900
Beta|111111111

sqlite> .headers on

sqlite> select * from agenda;
nome|telefone
Jose|988889900
Beta|111111111
sqlite>
```
### 12. Entendendo os tipos de dados

https://www.devmedia.com.br/tipos-de-dados-no-postgresql-e-sql-server/23362

### 14. Excluindo uma tabela

```
sqlite> .exit
C:\Users\josemalcher\Documents\09-Workspaces\workspace-Udemy-SQL-aprenda-sql-do-zero\03-CriandoTabelaseInserindoInformacoes (master)
λ sqlite3.exe aula01.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite> .tables
agenda    alunos    produtos
sqlite> drop table produtos;
sqlite> .tables
agenda  alunos
sqlite>
```

### 15. Mudando o nome da tabela

```
sqlite> .tables
agenda  alunos

sqlite> alter table alunos rename to estudantes;
sqlite> .tables
agenda      estudantes

sqlite> alter table agenda rename to cadernos;
sqlite> .tables
cadernos    estudantes
```

### 16. Vamos adicionar um campo na tabela
```
sqlite> .tables
estudantes

sqlite> .schema
CREATE TABLE IF NOT EXISTS "estudantes"(matricula integer, nome text, telefone text, cidade text);

sqlite> alter table estudantes add estado text;
sqlite> .schema
CREATE TABLE IF NOT EXISTS "estudantes"(matricula integer, nome text, telefone text, cidade text, estado text);

sqlite> alter table estudantes add condigo integer;
sqlite> .schema
CREATE TABLE IF NOT EXISTS "estudantes"(matricula integer, nome text, telefone text, cidade text, estado text, condigo integer);
```


[[MÃO NA MASSA] Exercícios - Lista 1](https://github.com/josemalcher/Udemy-Aprenda-SQL-do-Zero/tree/master/Lista01)

[[MÃO NA MASSA] Exercícios - Lista 2](https://github.com/josemalcher/Udemy-Aprenda-SQL-do-Zero/tree/master/Lista02)




[Voltar ao Índice](#indice)

---

## <a name="parte4">Selecionando e Extraindo informações</a>

### 22. Inserindo informações
```sql
sqlite> insert into funcionarios(nome, endereco, telefone,cidade, cep, rg, salaro) values("jose", "rua ttal tal",  "999999","Belem", 66020000, "44433221","2000");
sqlite> select * from funcionarios;
|jose|rua ttal tal|999999|Belem|66020000|44433221|2000

sqlite> .headers on

sqlite> select * from funcionarios;
cod|nome|endereco|telefone|cidade|cep|rg|salaro
|jose|rua ttal tal|999999|Belem|66020000|44433221|2000
sqlite>
```

[Voltar ao Índice](#indice)

---

### 23. O comando mais badalado do SQL

```sql
sqlite> select * from funcionarios;
codigo|nome|telefone|cpf
1|jose stelio|3241-2233|78911122233
2|Nome funcionario 2|3222-3123|11122233344
3|funcionario 3|3333-3123|2223334411
4|funcionario 4|4444-3123|4443334411
5|Ana|3111-3123|1113333344

sqlite> select * from funcionarios where nome="Ana";
codigo|nome|telefone|cpf
5|Ana|3111-3123|1113333344
sqlite>
```

---

### 24. Mostrando só alguns campos mesmo

```sql
sqlite> select * from funcionarios where telefone="3111-3123";
codigo|nome|telefone|cpf
5|Ana|3111-3123|1113333344

sqlite> select nome from funcionarios where telefone="3111-3123";
nome
Ana

sqlite> select nome,cpf from funcionarios where telefone="3111-3123";
nome|cpf
Ana|1113333344

sqlite> select nome from funcionarios;
nome
jose stelio
Nome funcionario 2
funcionario 3
funcionario 4
Ana
sqlite>
```

### 25. Apagando coisas que não preciso

```sql
sqlite> select * from funcionarios;
codigo|nome|telefone|cpf
1|jose stelio|3241-2233|78911122233
2|Nome funcionario 2|3222-3123|11122233344
3|funcionario 3|3333-3123|2223334411
4|funcionario 4|4444-3123|4443334411
5|Ana|3111-3123|1113333344

sqlite> delete from funcionarios where nome="Ana";

sqlite> select * from funcionarios;
codigo|nome|telefone|cpf
1|jose stelio|3241-2233|78911122233
2|Nome funcionario 2|3222-3123|11122233344
3|funcionario 3|3333-3123|2223334411
4|funcionario 4|4444-3123|4443334411
sqlite>
```

---

### 26. O que é esse tal de Like?

```sql
sqlite> select * from funcionarios;
codigo|nome|telefone|cpf
1|jose stelio|3241-2233|78911122233
2|Nome funcionario 2|3222-3123|11122233344
3|funcionario 3|3333-3123|2223334411
4|funcionario 4|4444-3123|4443334411
6|Ana Maria|3111-3123|1113444344
7|Ana Souza|3111-2222|1223444344
8|Ana Beatriz|3111-5555|9999444344
9|Ana Vinagre|3111-1111|9444344
10|Ana Carolina|3111-7777|7779444344

sqlite> select * from funcionarios where nome like "A%";
codigo|nome|telefone|cpf
6|Ana Maria|3111-3123|1113444344
7|Ana Souza|3111-2222|1223444344
8|Ana Beatriz|3111-5555|9999444344
9|Ana Vinagre|3111-1111|9444344
10|Ana Carolina|3111-7777|7779444344

sqlite> select nome,telefone from funcionarios where nome like "A%";
nome|telefone
Ana Maria|3111-3123
Ana Souza|3111-2222
Ana Beatriz|3111-5555
Ana Vinagre|3111-1111
Ana Carolina|3111-7777

sqlite> select nome,telefone from funcionarios where telefone like "31%";
nome|telefone
Ana Maria|3111-3123
Ana Souza|3111-2222
Ana Beatriz|3111-5555
Ana Vinagre|3111-1111
Ana Carolina|3111-7777
sqlite>
```

---

### 27. Conhecendo o SQLite Studio

https://sqlitestudio.pl/index.rvt

---

28. [MÃO NA MASSA] Exercícios - Lista 3

[Lista 3 Resolvida](https://github.com/josemalcher/Udemy-Aprenda-SQL-do-Zero/tree/master/Lista03)

30. [MÃO NA MASSA] Exercícios - Lista 4

[Lista 4 Resolvida](https://github.com/josemalcher/Udemy-Aprenda-SQL-do-Zero/tree/master/Lista04)

--- 

### 32. Colocando em ordem alfabética

```sql
sqlite> select nome from funcionarios;
nome
jose stelio
Nome funcionario 2
funcionario 3
funcionario 4
Ana Maria
Ana Souza
Ana Beatriz
Ana Vinagre
Ana Carolina

sqlite> select nome from funcionarios order by nome;
nome
Ana Beatriz
Ana Carolina
Ana Maria
Ana Souza
Ana Vinagre
Nome funcionario 2
funcionario 3
funcionario 4
jose stelio

sqlite> select nome from funcionarios order by nome DESC;
nome
jose stelio
funcionario 4
funcionario 3
Nome funcionario 2
Ana Vinagre
Ana Souza
Ana Maria
Ana Carolina
Ana Beatriz

sqlite> select nome,telefone from funcionarios order by telefone;
nome|telefone
Ana Vinagre|3111-1111
Ana Souza|3111-2222
Ana Maria|3111-3123
Ana Beatriz|3111-5555
Ana Carolina|3111-7777
Nome funcionario 2|3222-3123
jose stelio|3241-2233
funcionario 3|3333-3123
funcionario 4|4444-3123
sqlite>
```

---

### 33. Buscando intervalos de valores

```sql
sqlite> select * from funcionarios;
codigo|nome|telefone|cpf
1|jose stelio|3241-2233|78911122233
2|Nome funcionario 2|3222-3123|11122233344
3|funcionario 3|3333-3123|2223334411
4|funcionario 4|4444-3123|4443334411
6|Ana Maria|3111-3123|1113444344
7|Ana Souza|3111-2222|1223444344
8|Ana Beatriz|3111-5555|9999444344
9|Ana Vinagre|3111-1111|9444344
10|Ana Carolina|3111-7777|7779444344

sqlite> select * from funcionarios where codigo>=5;
codigo|nome|telefone|cpf
6|Ana Maria|3111-3123|1113444344
7|Ana Souza|3111-2222|1223444344
8|Ana Beatriz|3111-5555|9999444344
9|Ana Vinagre|3111-1111|9444344
10|Ana Carolina|3111-7777|7779444344

sqlite> select * from funcionarios where codigo>5;
codigo|nome|telefone|cpf
6|Ana Maria|3111-3123|1113444344
7|Ana Souza|3111-2222|1223444344
8|Ana Beatriz|3111-5555|9999444344
9|Ana Vinagre|3111-1111|9444344
10|Ana Carolina|3111-7777|7779444344

sqlite> select * from funcionarios where codigo=6 or codigo=10;
codigo|nome|telefone|cpf
6|Ana Maria|3111-3123|1113444344
10|Ana Carolina|3111-7777|7779444344

sqlite> select * from funcionarios where codigo=6 or codigo=10 or codigo = 5;
codigo|nome|telefone|cpf
6|Ana Maria|3111-3123|1113444344
10|Ana Carolina|3111-7777|7779444344

sqlite> select * from funcionarios where codigo in (1,5,6,10);
codigo|nome|telefone|cpf
1|jose stelio|3241-2233|78911122233
6|Ana Maria|3111-3123|1113444344
10|Ana Carolina|3111-7777|7779444344
sqlite>
```

---

35. [MÃO NA MASSA] Exercícios - Lista 5

https://github.com/josemalcher/Udemy-Aprenda-SQL-do-Zero/tree/master/Lista05


---

### 37. Atualizando informações na tabela

```sql
sqlite> select * from funcionarios;
codigo|nome|telefone|cpf
1|jose stelio|3241-2233|78911122233
2|Nome funcionario 2|3222-3123|11122233344
3|funcionario 3|3333-3123|2223334411
4|funcionario 4|4444-3123|4443334411
6|Ana Maria|3111-3123|1113444344
7|Ana Souza|3111-2222|1223444344
8|Ana Beatriz|3111-5555|9999444344
9|Ana Vinagre|3111-1111|9444344
10|Ana Carolina|3111-7777|7779444344

sqlite> update funcionarios set nome="José Malcher Jr." where codigo=1;

sqlite> select * from funcionarios;
codigo|nome|telefone|cpf
1|José Malcher Jr.|3241-2233|78911122233
2|Nome funcionario 2|3222-3123|11122233344
3|funcionario 3|3333-3123|2223334411
4|funcionario 4|4444-3123|4443334411
6|Ana Maria|3111-3123|1113444344
7|Ana Souza|3111-2222|1223444344
8|Ana Beatriz|3111-5555|9999444344
9|Ana Vinagre|3111-1111|9444344
10|Ana Carolina|3111-7777|7779444344
sqlite>
```

## <a name="parte5">Tabelas também se relacionam</a>

### 38. Vamos fazer nosso primeiro JOIN

```sql
sqlite> select * from livro;
id|titulo|id_autor|id_editora|id_estilo|sinopse|isbn
1|Nome livro qualquer 1|1|1|1|Sinopse breve..|123123
2|Livro 02|||||
2|Nome livro qualquer 2|1|2|2|Sinopse breve..tal tal|144443
3|Nome livro qualquer 3|1|1|2|Sinopse breve.. tal|133344
3|Nome livro qualquer 3|2|1|3|Sinopse breve.. tal|1533444
5|Nome livro qualquer 5|3|2|1|Sinopse breve.. tal|1533444
6|Nome livro qualquer 6|4|3|2|Sinopse breve.. tal|1533666
7|Nome livro qualquer 7|5|2|1|Sinopse breve.. tal bla|1533777
-- usando "apelidos nas tabelas"
sqlite> select l.titulo, a.nome from livro l, autor a where a.id = l.id_autor;
titulo|nome
Nome livro qualquer 1|Nome Autor 1
Nome livro qualquer 2|Nome Autor 1
Nome livro qualquer 3|Nome Autor 1
Nome livro qualquer 3|Autor 2
Nome livro qualquer 5|Jose Autor 3
Nome livro qualquer 6|Ana Maria Autor 4
Nome livro qualquer 7|Maria Autor 5
sqlite>
```

---

### 39. Mais um JOIN para você entender

```sql
sqlite> select livro.titulo, editora.nome 
        from livro, editora 
        where editora.id = livro.id_editora;
titulo|nome
Nome livro qualquer 2|PA Editora 2
Nome livro qualquer 5|PA Editora 2
Nome livro qualquer 6|BA Editora 3
Nome livro qualquer 7|PA Editora 2
sqlite>
```
---

### 40. Que tal ligarmos agora 3 tabelas?

```sql
sqlite> select livro.titulo, autor.nome, editora.nome from livro, autor, editora where autor.id = livro.id_editora AND editora.id = livro.id_editora;
titulo|nome|nome
Nome livro qualquer 2|Autor 2|PA Editora 2
Nome livro qualquer 5|Autor 2|PA Editora 2
Nome livro qualquer 6|Jose Autor 3|BA Editora 3
Nome livro qualquer 7|Autor 2|PA Editora 2
sqlite>
```

---

### 41. Além do JOIN vamos restringir um pouco mais?

```sql
sqlite> select l.titulo, a.nome, e.nome, e.telefone 
        from livro l, autor a, editora e 
        where a.id = l.id_autor 
        and   e.id = l.id_editora 
        and   e.telefone like "91%";
titulo|nome|nome|telefone
Nome livro qualquer 2|Nome Autor 1|PA Editora 2|91 9999999
Nome livro qualquer 5|Jose Autor 3|PA Editora 2|91 9999999
Nome livro qualquer 7|Maria Autor 5|PA Editora 2|91 9999999
sqlite>
```

---

42. [MÃO NA MASSA] Exercícios - Lista 6

https://github.com/josemalcher/Udemy-Aprenda-SQL-do-Zero/tree/master/Lista06


---

[Voltar ao Índice](#indice)

---

## <a name="parte6">Aprendendo COUNT, MIN, MAX, AVG</a>

### 44. Vamos contar

```sql
sqlite> select count(*) from editora;
101

sqlite> select count(*) from editora where estado="MG";
44

sqlite> select count(*) as "Total" from editora where estado="MG";
44

sqlite> .headers on

sqlite> select count(*) as "Total" from editora where estado="MG";
Total
44
sqlite>
```

---

### 45. Tirando a média

```sql
sqlite> select * from livro;
id|titulo|autor_id|editora_id|estilo_id|sinopse|isbn|precovenda
1|Anjos e Demônios|2|1|1|Livro excelente com uma historia legal|7878787878|87.580035
2|A Arte da Guerra||4||||30.315
2|Código da Vinci|1|2|1|Outro livro excelente com uma historia legal|555544448888|20.21
3|SQL de A a Z||||||

sqlite> select avg(precovenda) from livro;
avg(precovenda)
46.0350116666667

sqlite> select avg(precovenda) as "Preço Médio" from livro;
Preço Médio
46.0350116666667

sqlite> select avg(precovenda) "Preço Médio" from livro;
Preço Médio
46.0350116666667

```

---
### 46. Encontrando valores maiores e menores

```sql
sqlite> select * from livro;
id|titulo|autor_id|editora_id|estilo_id|sinopse|isbn|precovenda
1|Anjos e Demônios|2|1|1|Livro excelente com uma historia legal|7878787878|87.580035
2|A Arte da Guerra||4||||30.315
2|Código da Vinci|1|2|1|Outro livro excelente com uma historia legal|555544448888|20.21
3|SQL de A a Z||||||
sqlite> select max(precovenda) as "Maior Valor" from livro;
Maior Valor
87.580035
sqlite> select min(precovenda) as "Menor Valor" from livro;
Menor Valor
20.21
sqlite> select max(id) as "Maior ID" from editora;
Maior ID
109

```

---

### 47. A cláusula group by e having

```sql
sqlite> select count(*) "Total" from editora;
Total
101

sqlite> select estado, count(*) "Total" from editora where estado="MG";
estado|Total
MG|44

sqlite> select estado, count(*) "Total" from editora group by estado;
estado|Total
|2
GO|20
MG|44
N.|1
SP|34

sqlite> select estado, count(*) "Total" from editora group by estado having count(*) < 30;
estado|Total
|2
GO|20
N.|1

sqlite> select estado, count(*) "Total" from editora group by estado having count(*) >= 30;
estado|Total
MG|44
SP|34
sqlite>

```

---

### 48. [MÃO NA MASSA] Exercícios - Lista 7 (Assista aqui! PORCENTAGEM)

https://github.com/josemalcher/Udemy-Aprenda-SQL-do-Zero/tree/master/Lista07


[Voltar ao Índice](#indice)

---

## <a name="parte7">Vamos Aprender umas coisas legais</a>

### 50. Criando uma view

```sql
CREATE VIEW GO AS
select a.nome, e.nome, es.nome, l.titulo, e.estado
from livro l, autor a, editora e, estilo es
where a.id = l.autor_id
and e.id = l.editora_id
and es.id = l.estilo_id
and e.estado = "GO";

SELECT * from GO;

CREATE VIEW Livro_e_Editora AS
SELECT l.titulo, e.nome
  FROM editora e, livro l
  WHERE e.id = l.editora_id;

SELECT * FROM Livro_e_Editora;
SELECT * FROM Livro_e_Editora WHERE nome="ABC";
```

---

### 51. Excluindo uma view

```sql
sqlite> .table
GO               auditoria        dados_fake       estilo
Livro_e_Editora  autor            editora          livro

sqlite> select * from GO;
nome|nome:1|nome:2|titulo|estado
Dan Brown|ABC|Policial|Código da Vinci|GO

sqlite> drop view GO;

sqlite> .table
Livro_e_Editora  autor            editora          livro
auditoria        dados_fake       estilo
sqlite>
```

---

### 52. O comando create INDEX

```sql
--- SEM INDEX
select count(*) 
from fakenames 
where estado = "MG";
--- 1 row retrieved starting from 1 in 252ms (execution: 242ms, fetching: 10ms)

SELECT estado, count(*)
from fakenames
GROUP BY estado;
--- 27 rows retrieved starting from 1 in 741ms (execution: 554ms, fetching: 187ms)

--- COM INDEX CRIADO
CREATE INDEX idx_fakenames ON fakenames(estado);

SELECT estado, count(*)
from fakenames
GROUP BY estado;
--- 27 rows retrieved starting from 1 in 200ms (execution: 6ms, fetching: 194ms)

```

---

### 54. Excluindo um índex

```sql
        drop INDEX idx_fakenames2;
```

---

### 55. A cláusula DISTINCT

```sql
sqlite> select distinct estado from fakenames;
AC
AL
AM
AP
BA
CE
DF
ES
GO
MA
MG
MS
MT
PA
PB
PE
PI
PR
RJ
RN
RO
RR
RS
SC
SE
SP
TO

sqlite> select distinct cidade from fakenames;
```

---

### 56. Usando o LIMIT

```sql
sqlite> select distinct cidade from fakenames limit 10;
Santa Maria
Jacareí
Rio de Janeiro
Várzea Grande
São Paulo
Brasília
Porto Alegre
Maringá
Canoas
Cabo Frio
sqlite>

select * from livro
order by precovenda DESC
limit 2;

```





[Voltar ao Índice](#indice)

---

## <a name="parte8">Isso tá muio fácil! Quero recursos avançados!</a>

[Voltar ao Índice](#indice)

---

## <a name="parte9">Fechamento</a>

[Voltar ao Índice](#indice)

---