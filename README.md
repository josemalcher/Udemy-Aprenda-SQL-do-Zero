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

[Voltar ao Índice](#indice)

---

## <a name="parte5">Tabelas também se relacionam</a>

[Voltar ao Índice](#indice)

---

## <a name="parte6">Aprendendo COUNT, MIN, MAX, AVG</a>

[Voltar ao Índice](#indice)

---

## <a name="parte7">Aprendendo COUNT, MIN, MAX, AVG</a>

[Voltar ao Índice](#indice)

---

## <a name="parte8">Isso tá muio fácil! Quero recursos avançados!</a>

[Voltar ao Índice](#indice)

---

## <a name="parte9">Fechamento</a>

[Voltar ao Índice](#indice)

---