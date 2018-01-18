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

1) Leia do primeiro ao último exercício antes de começar a resolver.  
2) Execute o sqlite criando um banco de dados de nome lista3.sqlite.  
3) Crie uma tabela com o nome de alunos. Deverá conter o campo código (inteiro), nome, telefone e cidade (texto). Vou te ajudar nessa: CREATE TABLE alunos (codigo int, nome text, telefone text, cidade text);  
4) Use o comando .tables para verificar se a tabela foi criada  
5) Crie a tabela funcionários contendo os campos código, nome, endereço, telefone, cidade, estado, cep, rg, cpf e salário. Coloque os tipos de dados necessários.  
6) Saia do sqlite com o comando .exit.  
7) Abra novamente no sqlite o banco lista3.sqlite.  
8) Verifique se as tabelas ainda existem com o comando .tables  
9) Agora iremos trabalhar com o comando insert para inserir um novo registro ao banco de dados. Apenas para você lembrar o funcionamento dele iremos inserir um registro na tabela alunos: insert into alunos (código, nome, telefone, cidade) values (1,’Ana’,’9999-9999’,’Ituiutaba’); - Faça esse comando agora.  
10) Precisamos agora verificar se o registro foi inserido corretamente. Então precisamos selecionar todos os dados da tabela alunos. Use o comando select desse jeito: select * from alunos; (lembre-se que o * aqui nesse caso significa todos os campos, ou seja, irá mostrar nome, endereço, código, etc).  
11) Insira um novo registro na tabela alunos com os seus dados.  
12) Selecione os registros da tabela alunos e veja se o registro foi inserido.  
13) Ligue os cabeçalhos usando o comando .headers on  
14) Selecione novamente para verificar se o cabeçalho foi mostrado corretamente.  
15) Insira na tabela alunos o aluno José Buscapé.  
16) Selecione o conteúdo da tabela e veja se foi inserido corretamente.  
17) Agora você vai aprender um novo recurso do comando select. Você pode escolher os CAMPOS que deseja que sejam exibidos. Por exemplo, se eu quiser exibir somente o código e o nome devo usar o comando assim: select codigo,nome from alunos; - Faça isso agora!  
18) Selecione somente o nome e telefone dos alunos.  
19) Selecione o nome e a cidade dos alunos  
20) Selecione somente o código e o telefone dos alunos  
21) Insira 4 novos alunos;  
22) Selecione todos os campos da tabela alunos  
23) Selecione da tabela alunos os seguintes campos (nessa ordem): cidade, código, nome. Veja que você pode exibir os dados na ordem que quiser.  
24) Insira mais um alunos na tabela alunos.  
25) Saia do sqlite, feche o terminal e abra novamente.  
26) Selecione os dados da tabela a alunos e veja se ainda existem.  
27) Adicione 1 novo funcionário. Lembre-se que é necessário usar aspas para campos TEXTO. Campos numéricos não podem ter aspas. Se o salário tiver centavos, lembre-se que deve separar os centavos com um (.) (ponto) pois a vírgula é usada para separar os valores a serem inseridos.  
28) Selecione os dados da tabela funcionários e veja se foi inserido corretamente.  
29) Cadastre 3 funcionários. Use código na sequência. (1,2,3,4,5 etc).  
30) Selecione somente o código e nome dos funcionários.  

---


1) Leia do primeiro ao último exercício antes de começar a resolver.  

2) Execute o sqlite criando um banco de dados de nome lista3.sqlite.  
```
    sqlite3.exe Lista03.sqlite
```
3) Crie uma tabela com o nome de alunos. Deverá conter o campo código (inteiro), nome, telefone e cidade (texto). Vou te ajudar nessa: CREATE TABLE alunos (codigo int, nome text, telefone text, cidade text);  

```sql
CREATE TABLE Alunos
(
    codigo INT,
    nome TEXT,
    telefone TEXT,
    cidade TEXT
);
```

4) Use o comando .tables para verificar se a tabela foi criada  

```sql
λ sqlite3.exe lista3.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite> .tables
Alunos
sqlite>
```

5) Crie a tabela funcionários contendo os campos código, nome, endereço, telefone, cidade, estado, cep, rg, cpf e salário. Coloque os tipos de dados necessários.  

```
sqlite> Create table funcionario(codigo int, nome text,endereco text,telefone text, cidade text,estado text,cep int, rg int, salario text);
sqlite> .tables
Alunos       funcionario
sqlite> 
```

6) Saia do sqlite com o comando .exit.  
```
.exit
```
7) Abra novamente no sqlite o banco lista3.sqlite.  
```
λ sqlite3.exe lista3.sqlite
SQLite version 3.21.0 2017-10-24 18:55:49
Enter ".help" for usage hints.
sqlite>
```
8) Verifique se as tabelas ainda existem com o comando .tables  
```
sqlite> .tables
Alunos       funcionario
sqlite>
```
9) Agora iremos trabalhar com o comando insert para inserir um novo registro ao banco de dados. Apenas para você lembrar o funcionamento dele iremos inserir um registro na tabela alunos: insert into alunos (código, nome, telefone, cidade) values (1,’Ana’,’9999-9999’,’Ituiutaba’); - Faça esse comando agora.  

```sql
sqlite> .schema Alunos
CREATE TABLE Alunos
(
    codigo INT,
    nome TEXT,
    telefone TEXT,
    cidade TEXT
);
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(1,"Ana","123456789","Belem");
```

10) Precisamos agora verificar se o registro foi inserido corretamente. Então precisamos selecionar todos os dados da tabela alunos. Use o comando select desse jeito: select * from alunos; (lembre-se que o * aqui nesse caso significa todos os campos, ou seja, irá mostrar nome, endereço, código, etc).  

```sql
sqlite> .headers on
sqlite> select * from Alunos;
codigo|nome|telefone|cidade
1|Ana|123456789|Belem
sqlite>
```

11) Insira um novo registro na tabela alunos com os seus dados.  

```sql
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(2,"Ana Maria","987654321","Belem");
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(2,"Ana Carolina","777777665","Belem");
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(4,"Alice","999888765","São Paulo");
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(5,"Alice Govinda","91777777","São Paulo");
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(6,"João","91777777","São Pedro");
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(7,"Jose","91333333","São Carlos");
```

12) Selecione os registros da tabela alunos e veja se o registro foi inserido.  

```sql
sqlite> select * from Alunos;
codigo|nome|telefone|cidade
1|Ana|123456789|Belem
2|Ana Maria|987654321|Belem
2|Ana Carolina|777777665|Belem
4|Alice|999888765|São Paulo
5|Alice Govinda|91777777|São Paulo
6|João|91777777|São Pedro
7|Jose|91333333|São Carlos
sqlite>
```

13) Ligue os cabeçalhos usando o comando .headers on  

```sql
sqlite> .headers on
```

14) Selecione novamente para verificar se o cabeçalho foi mostrado corretamente.  

```sql
sqlite> select * from Alunos;
codigo|nome|telefone|cidade
```

15) Insira na tabela alunos o aluno José Buscapé.  

```sql
7|Jose|91333333|São Carlos
```

16) Selecione o conteúdo da tabela e veja se foi inserido corretamente.  

```sql
sqlite> select * from Alunos;
```

17) Agora você vai aprender um novo recurso do comando select. Você pode escolher os CAMPOS que deseja que sejam exibidos. Por exemplo, se eu quiser exibir somente o código e o nome devo usar o comando assim: select codigo,nome from alunos; - Faça isso agora!  

```sql
sqlite> select codigo, nome from Alunos;
codigo|nome
1|Ana
2|Ana Maria
2|Ana Carolina
4|Alice
5|Alice Govinda
6|João
7|Jose
sqlite>
```

18) Selecione somente o nome e telefone dos alunos.  

```sql
sqlite> select nome,telefone from Alunos;
nome|telefone
Ana|123456789
Ana Maria|987654321
Ana Carolina|777777665
Alice|999888765
Alice Govinda|91777777
João|91777777
Jose|91333333
sqlite>
```

19) Selecione o nome e a cidade dos alunos  

```sql
sqlite> select nome,cidade from Alunos;
nome|cidade
Ana|Belem
Ana Maria|Belem
Ana Carolina|Belem
Alice|São Paulo
Alice Govinda|São Paulo
João|São Pedro
Jose|São Carlos
sqlite>
```

20) Selecione somente o código e o telefone dos alunos  

```sql
sqlite> select codigo,telefone from Alunos;
codigo|telefone
1|123456789
2|987654321
2|777777665
4|999888765
5|91777777
6|91777777
7|91333333
sqlite>
```

21) Insira 4 novos alunos;  

```sql
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(8,"Jose Maria","91111111","São Jose");
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(8,"Jose Arimateia","77111111","RIO");
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(10,"Arlindo Arimateia","7722222","RIO");
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(11,"Arlindo Silva","77333344","RIO");
```

22) Selecione todos os campos da tabela alunos  

```sql
sqlite> select * from Alunos;
codigo|nome|telefone|cidade
1|Ana|123456789|Belem
2|Ana Maria|987654321|Belem
2|Ana Carolina|777777665|Belem
4|Alice|999888765|São Paulo
5|Alice Govinda|91777777|São Paulo
6|João|91777777|São Pedro
7|Jose|91333333|São Carlos
8|Jose Maria|91111111|São Jose
8|Jose Arimateia|77111111|RIO
10|Arlindo Arimateia|7722222|RIO
11|Arlindo Silva|77333344|RIO
sqlite>
```

23) Selecione da tabela alunos os seguintes campos (nessa ordem): cidade, código, nome. Veja que você pode exibir os dados na ordem que quiser.  

```sql
sqlite> select cidade,codigo,nome from Alunos;
cidade|codigo|nome
Belem|1|Ana
Belem|2|Ana Maria
Belem|2|Ana Carolina
São Paulo|4|Alice
São Paulo|5|Alice Govinda
São Pedro|6|João
São Carlos|7|Jose
São Jose|8|Jose Maria
RIO|8|Jose Arimateia
RIO|10|Arlindo Arimateia
RIO|11|Arlindo Silva
sqlite>
```

24) Insira mais um alunos na tabela alunos.  

```sql
sqlite> insert into Alunos (codigo, nome, telefone, cidade) values(12,"Maria Silva","77555555","RIO");
```

25) Saia do sqlite, feche o terminal e abra novamente.  

```sql
.exit
```

26) Selecione os dados da tabela a alunos e veja se ainda existem.  

```sql
sqlite> select * from Alunos;
codigo|nome|telefone|cidade
1|Ana|123456789|Belem
2|Ana Maria|987654321|Belem
2|Ana Carolina|777777665|Belem
4|Alice|999888765|São Paulo
5|Alice Govinda|91777777|São Paulo
6|João|91777777|São Pedro
7|Jose|91333333|São Carlos
8|Jose Maria|91111111|São Jose
8|Jose Arimateia|77111111|RIO
10|Arlindo Arimateia|7722222|RIO
11|Arlindo Silva|77333344|RIO
12|Maria Silva|77555555|RIO
sqlite>
```

27) Adicione 1 novo funcionário. Lembre-se que é necessário usar aspas para campos TEXTO. Campos numéricos não podem ter aspas. Se o salário tiver centavos, lembre-se que deve separar os centavos com um (.) (ponto) pois a vírgula é usada para separar os valores a serem inseridos.  

```sql
sqlite> .schema funcionario
CREATE TABLE funcionario(codigo int, nome text,endereco text,telefone text, cidade text,estado text,cep int, rg int, salario text);
sqlite> insert into funcionario(codigo, nome,endereco,telefone,cidade,estado,cep, rg, salario) values(01,"jose silva","Rua tal","1111111", "Belém","PA",66020000, 1111,"2.000");
sqlite>
```

28) Selecione os dados da tabela funcionários e veja se foi inserido corretamente.  

```sql
sqlite> select * from funcionario;
codigo|nome|endereco|telefone|cidade|estado|cep|rg|salario
1|jose silva|Rua tal|1111111|Belém|PA|66020000|1111|2.000
sqlite>
```

29) Cadastre 3 funcionários. Use código na sequência. (1,2,3,4,5 etc).  

```sql
sqlite> insert into funcionario(codigo, nome,endereco,telefone,cidade,estado,cep, rg, salario) values(02,"jose maria","Rua tal tal","144111", "Belém","PA",66030000, 2211,"1.000");
sqlite> insert into funcionario(codigo, nome,endereco,telefone,cidade,estado,cep, rg, salario) values(03,"maria joaquina","Rua tal Fulado","177111", "Cametá","PA",66040000, 4411,"3.000");
sqlite> insert into funcionario(codigo, nome,endereco,telefone,cidade,estado,cep, rg, salario) values(03,"Gabi joaquina","Rua Fulado Gago","100111", "São Paulo","SP",66090000, 9911,"3.500");
```

30) Selecione somente o código e nome dos funcionários.  

```sql
sqlite> select codigo,nome from funcionario;
codigo|nome
1|jose silva
2|jose maria
3|maria joaquina
3|Gabi joaquina
sqlite>
```



