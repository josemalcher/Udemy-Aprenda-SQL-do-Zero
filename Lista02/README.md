# Resumo Udemy - Aprenda SQL do Zero

https://www.udemy.com/aprenda-sql-do-zero

---

## Lista 02 - Exercício

Observações:
· Para realização dos exercícios é necessário que você baixe o sqlite e coloque-o em sua área de trabalho. Depois você precisará abrir o cmd para executar com o nome correto do banco de dados conforme pedido.  
· Pode pesquisar a vontade e conversar com seus colegas. O Google é seu amigo.   
· Não reclame que não sabe. Pesquise, tente, teste e refaça! Mude sua postura de “Não sei fazer” para “Vou descobrir como se faz”. Anote a resposta de TODOS os exercícios. Irá te ajudar lá na frente!  
· Não pule nenhum exercício achando que “já sabe”.  
· Nomes de tabelas, campos e banco de dados NÃO devem possuir acentos e cedilha.  
· Lembre-se que o “;” finaliza os comandos.  
· Os tipos de dados basicamente são: int para inteiros, text para texto, real para números com decimais, date para datas e boolean para booleanos. Você também pode usar para campos texto o tipo varchar especificando o tamanho. Para valores monetários você pode usar o tipo real.  
· Sua missão é resolver todas as questões. Não pare antes disso.  

1) Altere o nome da tabela caixa para dinheiro.  
2) Exclua a tabela dinheiro.  
3) Exclua a tabela notas.  
4) Altere o nome da tabela super_alunos para alunos.  
5) Não gostei desse nome. Mude de alunos para estudantes.  
6) Ficou feio mesmo assim. Altere o nome de estudantes para super_estudantes.  
7) Veja se o nome foi alterado usando o comando .tables.  
8) Exclua a tabela super_estudantes.  
9) Agora crie novamente a tabela alunos usando o mesmo comando que usou no exercício 1.  
10) Nós esquecemos que a tabela alunos precisa do campo estado! Precisamos alterar a estrutura da tabela incluindo o campo estado. Para isso iremos usar o comando alter table de novo. Veja como é fácil: ALTER TABLE ALUNOS ADD ESTADO TEXT; - Ou seja, nós informamos o nome da tabela e o novo campo junto com seu tipo! Faça isso agora!  
11) Crie novamente a tabela caixa.  
12) Adicione o campo observação do tipo text na tabela caixa.  
13) Adicione o campo cpf na tabela alunos.  
14) Veja a estrutura da tabela caixa  
15) Adicione o campo saldo na tabela caixa.  
16) Adicione o campo rg na tabela alunos.  
17) Veja a estrutura da tabela alunos.  
18) Altere o nome da tabela caixa para muito_dinheiro  
19) Acrescente o campo cliente na tabela muito_dinheiro.  
20) Adicione o campo fornecedor na tabela muito_dinheiro  
21) Mude o nome da tabela muito_dinheiro para caixa  
22) Saia do sqlite.  
23) Abra novamente o banco de dados lista1 no sqlite.  
24) Veja a lista das tabelas existentes.  
25) Exclua a tabela caixa  
26) Exclua a tabela alunos  
27) Insira o campo gravadora do tipo TEXT na tabela CDs  
28) Mude o nome da tabela CDs para MeusCDs  
29) Mude o nome da tabela MeusCDs para NossosCDs  
30) Veja a estrutura da tabela NossosCDs  

--- 

## Respostas

1) Altere o nome da tabela caixa para dinheiro.  
```sql
λ sqlite3.exe lista02.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite> .tables
caixa         fornecedores  notas         super_alunos
cds           funcionarios  produtos
sqlite> alter table caixa rename to dinheiro;
sqlite> .tables
cds           fornecedores  notas         super_alunos
dinheiro      funcionarios  produtos
sqlite>
```
2) Exclua a tabela dinheiro.  
```sql
sqlite> drop table dinheiro;
```
3) Exclua a tabela notas.  
```sql
sqlite> drop table notas;
sqlite> .table
cds           fornecedores  funcionarios  produtos      super_alunos
sqlite>
```
4) Altere o nome da tabela super_alunos para alunos.  
```sql
sqlite> alter table super_alunos rename to alunos;
sqlite> .tables
alunos        cds           fornecedores  funcionarios  produtos
sqlite>
```
5) Não gostei desse nome. Mude de alunos para estudantes.  
```sql
sqlite> alter table alunos rename to estudantes;
sqlite> .tables
cds           estudantes    fornecedores  funcionarios  produtos
sqlite>
```
6) Ficou feio mesmo assim. Altere o nome de estudantes para super_estudantes.  
```sql
sqlite> alter table estudantes rename to super_estudantes;

```
7) Veja se o nome foi alterado usando o comando .tables.  
```sql
sqlite> .tables
cds               funcionarios      super_estudantes
fornecedores      produtos
sqlite>
```
8) Exclua a tabela super_estudantes.  
```sql
sqlite> drop table super_estudantes;
```
9) Agora crie novamente a tabela alunos usando o mesmo comando que usou no exercício 1.  
```sql
sqlite> CREATE TABLE alunos( cod int, nome varchar(200), telefone varchar(50), cidade varchar(100));
sqlite> .tables
alunos        cds           fornecedores  funcionarios  produtos
sqlite>
```
10) Nós esquecemos que a tabela alunos precisa do campo estado! Precisamos alterar a estrutura da tabela incluindo o campo estado. Para isso iremos usar o comando alter table de novo. Veja como é fácil: ALTER TABLE ALUNOS ADD ESTADO TEXT; - Ou seja, nós informamos o nome da tabela e o novo campo junto com seu tipo! Faça isso agora!  
```sql
sqlite> .schema alunos
CREATE TABLE alunos( cod int, nome varchar(200), telefone varchar(50), cidade varchar(100));
sqlite> alter table alunos add estado text;
sqlite> .schema alunos
CREATE TABLE alunos( cod int, nome varchar(200), telefone varchar(50), cidade varchar(100), estado text);
sqlite>
```
11) Crie novamente a tabela caixa.  
```sql
sqlite> create table caixa(cod int, data Date, descricao text, debito varchar(200), credito varchar(200));
sqlite> .tables
alunos        cds           funcionarios
caixa         fornecedores  produtos
sqlite>
```
12) Adicione o campo observação do tipo text na tabela caixa.  
```sql
sqlite> .schema caixa
CREATE TABLE caixa(cod int, data Date, descricao text, debito varchar(200), credito varchar(200));
sqlite> alter table caixa add observacao text;
sqlite> .schema caixa
CREATE TABLE caixa(cod int, data Date, descricao text, debito varchar(200), credito varchar(200), observacao text);
sqlite>
```
13) Adicione o campo cpf na tabela alunos.  
```sql
sqlite> alter table alunos add cpf int;
sqlite> .schema alunos
CREATE TABLE alunos( cod int, nome varchar(200), telefone varchar(50), cidade varchar(100), estado text, cpf int);
sqlite>
```
14) Veja a estrutura da tabela caixa  
```sql
sqlite> .schema caixa
CREATE TABLE caixa(cod int, data Date, descricao text, debito varchar(200), credito varchar(200), observacao text);
sqlite>
```
15) Adicione o campo saldo na tabela caixa.  
```sql
sqlite> .schema caixa
CREATE TABLE caixa(cod int, data Date, descricao text, debito varchar(200), credito varchar(200), observacao text);
sqlite> alter table caixa add saldo varchar(100);
sqlite> .schema caixa
CREATE TABLE caixa(cod int, data Date, descricao text, debito varchar(200), credito varchar(200), observacao text, saldo varchar(100));
sqlite>
```
16) Adicione o campo rg na tabela alunos.  
```sql
sqlite> alter table alunos add rg int;
```
17) Veja a estrutura da tabela alunos.  
```sql
sqlite> .schema alunos
CREATE TABLE alunos( cod int, nome varchar(200), telefone varchar(50), cidade varchar(100), estado text, cpf int, rg int);
```
18) Altere o nome da tabela caixa para muito_dinheiro  
```sql
sqlite> alter table caixa rename to muito_dinheiro;
sqlite> .tables
alunos          fornecedores    muito_dinheiro
cds             funcionarios    produtos
sqlite>
```
19) Acrescente o campo cliente na tabela muito_dinheiro.  
```sql
sqlite> alter table muito_dinheiro add cliente varchar(200);
sqlite> .schema muito_dinheiro
CREATE TABLE IF NOT EXISTS "muito_dinheiro"(cod int, data Date, descricao text, debito varchar(200), credito varchar(200), observacao text, saldo varchar(100), cliente varchar(200));
sqlite>
```
20) Adicione o campo fornecedor na tabela muito_dinheiro  
```sql
sqlite> alter table muito_dinheiro add fornecedor varchar(200);
sqlite> .schema muito_dinheiro
CREATE TABLE IF NOT EXISTS "muito_dinheiro"(cod int, data Date, descricao text, debito varchar(200), credito varchar(200), observacao text, saldo varchar(100), cliente varchar(200), fornecedor varchar(200));
sqlite>
```
21) Mude o nome da tabela muito_dinheiro para caixa  
```sql
sqlite> alter table muito_dinheiro rename to caixa;
sqlite> .table
alunos        cds           funcionarios
caixa         fornecedores  produtos
sqlite>
```
22) Saia do sqlite.  
```sql
sqlite> .exit
```
23) Abra novamente o banco de dados lista1 no sqlite.  
```sql
λ sqlite3.exe lista02.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite>
```
24) Veja a lista das tabelas existentes.  
```sql
sqlite> .tables
alunos        cds           funcionarios
caixa         fornecedores  produtos
sqlite>
```
25) Exclua a tabela caixa  
```sql
sqlite> drop table caixa;
sqlite> .tables
alunos        cds           fornecedores  funcionarios  produtos
sqlite>
```
26) Exclua a tabela alunos  
```sql
sqlite> drop table alunos;
sqlite> .tables
cds           fornecedores  funcionarios  produtos
sqlite>
```
27) Insira o campo gravadora do tipo TEXT na tabela CDs  
```sql
sqlite> .schema cds
CREATE TABLE cds(cod int, nome vachar(200), cantor varchar(200), ano Date, quantidademusicas int);
sqlite> alter table cds add gravadora text;
sqlite> .schema cds
CREATE TABLE cds(cod int, nome vachar(200), cantor varchar(200), ano Date, quantidademusicas int, gravadora text);
sqlite>
```
28) Mude o nome da tabela CDs para MeusCDs  
```sql
sqlite> alter table cds rename to meuscds;
sqlite> .tables
fornecedores  funcionarios  meuscds       produtos
sqlite>
```
29) Mude o nome da tabela MeusCDs para NossosCDs  
```sql
sqlite> .tables
fornecedores  funcionarios  meuscds       produtos
sqlite> alter table meuscds rename to nossoscds;
sqlite> .tables
fornecedores  funcionarios  nossoscds     produtos
sqlite>
```
30) Veja a estrutura da tabela NossosCDs  
```sql
sqlite> .schema nossoscds
CREATE TABLE IF NOT EXISTS "nossoscds"(cod int, nome vachar(200), cantor varchar(200), ano Date, quantidademusicas int, gravadora text);
sqlite>
```