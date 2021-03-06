# Resumo Udemy - Aprenda SQL do Zero

https://www.udemy.com/aprenda-sql-do-zero

---

## Lista 01 - Exercício

Observações:
· Para realização dos exercícios é necessário que você baixe o sqlite e coloque-o em sua área de trabalho. Depois você precisará abrir o cmd para executar com o nome correto do banco de dados conforme pedido.  
· Pode pesquisar a vontade e conversar com seus colegas. O Google é seu amigo.   
· Não reclame que não sabe. Pesquise, tente, teste e refaça! Mude sua postura de “Não sei fazer” para “Vou descobrir como se faz”. Anote a resposta de TODOS os exercícios. Irá te ajudar lá na frente!  
· Não pule nenhum exercício achando que “já sabe”.  
· Nomes de tabelas, campos e banco de dados NÃO devem possuir acentos e cedilha.  
· Lembre-se que o “;” finaliza os comandos.  
· Os tipos de dados basicamente são: int para inteiros, text para texto, real para números com decimais, date para datas e boolean para booleanos. Você também pode usar para campos texto o tipo varchar especificando o tamanho. Para valores monetários você pode usar o tipo real.  
· Sua missão é resolver todas as questõsqlitees. Não pare antes disso.  

1) Execute o sqlite criando um banco de dados de nome lista1.sqlite.  
2) Crie uma tabela com o nome de alunos. Deverá conter o campo código (inteiro), nome, telefone e cidade (texto). Vou te ajudar nessa: CREATE TABLE alunos (codigo int, nome text, telefone text, cidade text);  
3) Use o comando .tables para verificar se a tabela foi criada  
4) Crie uma tabela com o nome de alunos2. Deverá conter o campo código (inteiro), nome (varchar de tamanho 200), telefone (varchar de tamanho 50)e cidade (varchar de tamanho 100). Vou te ajudar nessa também. O comando ficará assim: CREATE TABLE alunos2 (codigo int, nome varchar(200), telefone varchar(50), cidade varchar(100) );  
5) Crie a tabela funcionários contendo os campos nome, endereço, telefone, cidade, estado, cep, rg, cpf e salário. Coloque os tipos de dados necessários.  
6) Saia do sqlite com o comando .exit.  
7) Abra novamente no sqlite o banco lista1.sqlite.  
8) Verifique se as tabelas ainda existem com o comando .tables  
9) Crie a tabela fornecedores contendo os campos nome, endereço, telefone, cidade, estado, cep, cnpj e email. Coloque os tipos de dados necessários.  
10) Crie a tabela livros contendo o campo código, nome, categoria, resumo, precocusto, precovenda.  
11) Existe uma maneira de verificar o ESQUEMA da tabela, ou seja, sua estrutura. É o comando .SCHEMA.  
12) Crie a tabela estoque contendo o campo código, nomedoproduto, categoria, quantidade e fornecedor.  
13) Crie a tabela notas contendo os campos código, nomedoaluno, 1bim, 2bim, 3bim e 4bim.  
14) Crie a tabela caixa contendo os campos código, data, descrição, debito e credito.  
15) Crie a tabela contasAPagar contendo os campos código, data_conta, descrição, valor e data_pagamento.  
16) Crie a tabela contasAReceber contendo os campos código, data_conta, descrição, valor e data_recebimento.  
17) Crie a tabela filmes contendo os campos código, nome, sinopse, categoria e diretor.  
18) Crie a tabela CDs contendo os campos código, nome, cantor, ano e quantidademusicas.  
19) Agora iremos aprender a excluir tabelas. É muito fácil. Basta usar o comando DROP TABLE. Se quero excluir a tabela alunos o comando fica assim: Drop table alunos;. Faça isso então, exclua a tabela alunos.  
20) Use o comando .tables e veja se a tabela realmente foi excluída  
21) Exclua a tabela livros.  
22) Exclua a tabela contasAPagar.  
23) Exclua também a tabela contasAReceber.  
24) Agora apague a tabela filmes.  
25) Liste as tabelas e veja se a tabela alunos2 ainda existe.  
26) Agora iremos aprender como MUDAR O NOME das tabelas. É fácil, basta usar o comando ALTER TABLE. Por exemplo se quisermos mudar o nome da tabela NOMEFEIO para NOMEBONITO o comando ficará assim: ALTER TABLE NOMEFEIO RENAME TO NOMEBONITO; - Agora que você sabe disse renomeie a tabela alunos para super_alunos  
27) Use o comando .tables e veja se foi alterado o nome.  
28) Altere o nome da tabela estoque para produtos.  
29) Altere o nome da tabela notas para aprovados.  
30) Altere o nome da tabela aprovados para notas.  

## Resposta

1) Execute o sqlite criando um banco de dados de nome lista1.sqlite.  
```sql
λ sqlite3 lista01.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite>
```
2) Crie uma tabela com o nome de alunos. Deverá conter o campo código (inteiro), nome, telefone e cidade (texto). Vou te ajudar nessa: CREATE TABLE alunos (codigo int, nome text, telefone text, cidade text);  
```sql
sqlite> create table alunos(codigo int, nome text, telefone text, cidade text);
```
3) Use o comando .tables para verificar se a tabela foi criada  
```sql
sqlite> .tables
alunos
```
4) Crie uma tabela com o nome de alunos2. Deverá conter o campo código (inteiro), nome (varchar de tamanho 200), telefone (varchar de tamanho 50)e cidade (varchar de tamanho 100). Vou te ajudar nessa também. O comando ficará assim: CREATE TABLE alunos2 (codigo int, nome varchar(200), telefone varchar(50), cidade varchar(100) );  
```sql
sqlite> create table alunos2( cod int, nome varchar(200), telefone varchar(50), cidade varchar(100));
sqlite> .tables
alunos   alunos2
sqlite>

```
5) Crie a tabela funcionários contendo os campos nome, endereço, telefone, cidade, estado, cep, rg, cpf e salário. Coloque os tipos de dados necessários.  
```sql
sqlite> create table funcionarios(cod int, nome varchar(200), endereco varchar(200), telefone varchar(20), cidade varchar(200), cep int, rg varchar(10), salaro varchar(200));
sqlite> .tables
alunos        alunos2       funcionarios
sqlite>
```
6) Saia do sqlite com o comando .exit.  
```sql
sqlite> .exit

C:\Users\josemalcher\Documents\09-Workspaces\workspace-Udemy-SQL-aprenda-sql-do-zero\Lista01 (master)
λ

```
7) Abra novamente no sqlite o banco lista1.sqlite.  
```sql
C:\Users\josemalcher\Documents\09-Workspaces\workspace-Udemy-SQL-aprenda-sql-do-zero\Lista01 (master)
λ sqlite3 lista01.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite>

```
8) Verifique se as tabelas ainda existem com o comando .tables  
```sql
sqlite> .tables
alunos        alunos2       funcionarios
sqlite>
```
9) Crie a tabela fornecedores contendo os campos nome, endereço, telefone, cidade, estado, cep, cnpj e email. Coloque os tipos de dados necessários.  
```sql
sqlite> create table fornecedores(cod int, nome varchar(200), end varchar(200), telefone varchar(20), cidade varchar(100), cnpj varchar(100), email varchar(200));
sqlite>
```
10) Crie a tabela livros contendo o campo código, nome, categoria, resumo, precocusto, precovenda.  
```sql
sqlite> create table livros(cod int, nome varchar(200), cat varchar(200), resumo text, precocusto varchar(200), precovenda varchar(200));
sqlite> .tables
alunos        alunos2       fornecedores  funcionarios  livros
sqlite>
```
11) Existe uma maneira de verificar o ESQUEMA da tabela, ou seja, sua estrutura. É o comando .SCHEMA.  
```sql
sqlite> .schema
CREATE TABLE alunos(codigo int, nome text, telefone text, cidade text);
CREATE TABLE alunos2( cod int, nome varchar(200), telefone varchar(50), cidade varchar(100));
CREATE TABLE funcionarios(cod int, nome varchar(200), endereco varchar(200), telefone varchar(20), cidade varchar(200), cep int, rg varchar(10), salaro varchar(200));
CREATE TABLE fornecedores(cod int, nome varchar(200), end varchar(200), telefone varchar(20), cidade varchar(100), cnpj varchar(100), email varchar(200));
CREATE TABLE livros(cod int, nome varchar(200), cat varchar(200), resumo text, precocusto varchar(200), precovenda varchar(200));
sqlite>
```
12) Crie a tabela estoque contendo o campo código, nomedoproduto, categoria, quantidade e fornecedor.  
```sql
sqlite> create table estoque(cod int, nomeproduto varchar(200), cat varchar(200), quantidade int, fornecedor varchar(200));
sqlite>
```
13) Crie a tabela notas contendo os campos código, nomedoaluno, 1bim, 2bim, 3bim e 4bim.  
```sql
sqlite> create table notas(cod int, nomedoaluno varchar(200), bim1 varchar(10), bim2 varchar(10), bim3 varchar(10), bim4 varchar(10));
sqlite> .tables
alunos        estoque       funcionarios  notas
alunos2       fornecedores  livros
sqlite>
```
14) Crie a tabela caixa contendo os campos código, data, descrição, debito e credito.  
```sql
sqlite> create table caixa(cod int, data Date, descricao text, debito varchar(200), credito varchar(200));
sqlite>
```
15) Crie a tabela contasAPagar contendo os campos código, data_conta, descrição, valor e data_pagamento.  
```sql
sqlite> create table contasapagar(cod int, data_conta Date, descricao text, valor varchar(200), data_pagamento Date);

sqlite>
```
16) Crie a tabela contasAReceber contendo os campos código, data_conta, descrição, valor e data_recebimento.  
```sql
sqlite> create table contasreceber(cod int, data_conta Date, descricao text, valor varchar(200), data_recebimento Date);
```
17) Crie a tabela filmes contendo os campos código, nome, sinopse, categoria e diretor.  
```sql
sqlite> create table fimes(cod int, nome varchar(200), sinopse text, categoria varchar(200), diretor varchar(200));
sqlite>
```
18) Crie a tabela CDs contendo os campos código, nome, cantor, ano e quantidademusicas.  
```sql
sqlite> create table cds(cod int, nome vachar(200), cantor varchar(200), ano Date, quantidademusicas int);
sqlite>
```
19) Agora iremos aprender a excluir tabelas. É muito fácil. Basta usar o comando DROP TABLE. Se quero excluir a tabela alunos o comando fica assim: Drop table alunos;. Faça isso então, exclua a tabela alunos.  
```sql
e> .tables
alunos         cds            estoque        funcionarios
alunos2        contasapagar   fimes          livros
caixa          contasreceber  fornecedores   notas
sqlite> drop table alunos;

```
20) Use o comando .tables e veja se a tabela realmente foi excluída  
```sql
sqlite> .tables
alunos2        contasapagar   fimes          livros
caixa          contasreceber  fornecedores   notas
cds            estoque        funcionarios
sqlite>
```
21) Exclua a tabela livros.  
```sq
sqlite> drop table livros
```
22) Exclua a tabela contasAPagar.  
```sql
sqlite> drop table contasapagar;
```
23) Exclua também a tabela contasAReceber.  
```sql
sqlite> drop table contasreceber;
```
24) Agora apague a tabela filmes.  
```sql
sqlite> drop table filmes;
```
25) Liste as tabelas e veja se a tabela alunos2 ainda existe.  
```sql
sqlite> .tables
alunos2       cds           fornecedores  notas
caixa         estoque       funcionarios
sqlite>
```
26) Agora iremos aprender como MUDAR O NOME das tabelas. É fácil, basta usar o comando ALTER TABLE. Por exemplo se quisermos mudar o nome da tabela NOMEFEIO para NOMEBONITO o comando ficará assim: ALTER TABLE NOMEFEIO RENAME TO NOMEBONITO; - Agora que você sabe disse renomeie a tabela alunos para super_alunos  
```sql
sqlite> .tables
alunos2       cds           fornecedores  notas
caixa         estoque       funcionarios
sqlite> alter table alunos2 rename to super_alunos;
```
27) Use o comando .tables e veja se foi alterado o nome.  
```sql
sqlite> .tables
caixa         estoque       funcionarios  super_alunos
cds           fornecedores  notas
sqlite>
```
28) Altere o nome da tabela estoque para produtos.  
```sql
sqlite> alter table estoque rename to produtos;
```
29) Altere o nome da tabela notas para aprovados.  
```sql
sqlite> alter table notas rename to aprovados;
```
30) Altere o nome da tabela aprovados para notas.  
```sql
sqlite> alter table aprovados rename to notas;

sqlite> .table
caixa         fornecedores  notas         super_alunos
cds           funcionarios  produtos
```

