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

### DDL - Linguagem de Definição de Dados

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