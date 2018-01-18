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

1) Selecione somente o nome e salário dos funcionários.  
2) Selecione somente o nome e telefone dos funcionários.  
3) Selecione somente o nome, rg e cpf dos funcionários.  
4) Selecione somente o nome e a cidade dos funcionários.  
5) Insira mais um funcionário.  
6) Exiba todos os dados dos funcionários.  
7) Crie a tabela fornecedores contendo os campos nome, endereço, telefone, cidade, estado, cep, cnpj e email. Coloque os tipos de dados necessários.  
8) Insira 2 fornecedores. Código 1 e Código 2  
9) Selecione o nome e o telefone dos fornecedores.  
10) Agora iremos aprender uma opção do comando select. Nós podemos restringir o que vai ser exibido na tela. É moleza. Por exemplo se eu quiser listar somente o aluno de código 2 o comando fica assim: select * from alunos where codigo = 2; - Nós apenas adicionamos o WHERE e a CONDIÇÃO. Veja que mantivemos o * para exibir todos os campos, mas poderíamos também exibir somente o nome do aluno 2 assim: select nome from alunos where codigo = 2; - EXPERIMENTE AGORA ESSES 2 COMANDOS.  
11) Selecione o funcionário de código 3.  
12) Selecione o fornecedor de código 1.  
13) Selecione o aluno de código 2.  
14) Selecione o funcionário de código 1.  
15) Selecione somente o nome e salário do funcionário de código 2.  
16) Selecione somente o nome a cidade do aluno de código 1.  
17) Selecione todos os funcionários de MG. É assim: select * from funcionários where estado=’MG’; - Como estado é texto eu usei aspas! – Faça isso agora!  
18) Selecione todos os funcionários de GO.  
19) Selecione todos os funcionários de SP.  
20) Insira um funcionário para SP.  
21) Selecione todos os funcionários de SP.  
22) Crie a tabela livros contendo o campo código, nome, categoria, resumo, precocusto, precovenda.  
23) Verifique o esquema .schema da tabela livros.  
24) Liste as tabelas existentes.  
25) Insira 1 livro.  
26) Selecione o nome e a categoria do livro de código 1.  
27) Selecione o nome e a categoria do livro de código 3.  
28) Exclua a tabela livros.  
29) Altere o nome da tabela aluno para estudantes.  
30) Altere a tabela alunos inserindo o campo estado. Se estiver com dúvidas consulte a primeira lista de exercícios.  

---

1) Selecione somente o nome e salário dos funcionários.  

```sql
sqlite> select * from funcionario;
1|jose silva|Rua tal|1111111|Belém|PA|66020000|1111|2.000
2|jose maria|Rua tal tal|144111|Belém|PA|66030000|2211|1.000
3|maria joaquina|Rua tal Fulado|177111|Cametá|PA|66040000|4411|3.000
3|Gabi joaquina|Rua Fulado Gago|100111|São Paulo|SP|66090000|9911|3.500
sqlite> .schema funcionario
CREATE TABLE funcionario(codigo int, nome text,endereco text,telefone text, cidade text,estado text,cep int, rg int, salario text);

sqlite> select nome,salario from funcionario;
jose silva|2.000
jose maria|1.000
maria joaquina|3.000
Gabi joaquina|3.500
sqlite>
```

2) Selecione somente o nome e telefone dos funcionários.  

```sql
sqlite> select nome,telefone from funcionario;
nome|telefone
jose silva|1111111
jose maria|144111
maria joaquina|177111
Gabi joaquina|100111
sqlite>
```

3) Selecione somente o nome, rg e cpf dos funcionários.  

```sql
sqlite> select nome, rg, cpf from funcionario;
Error: no such column: cpf
```

4) Selecione somente o nome e a cidade dos funcionários.  

```sql
sqlite> select nome, cidade from funcionario;
nome|cidade
jose silva|Belém
jose maria|Belém
maria joaquina|Cametá
Gabi joaquina|São Paulo
sqlite>
```

5) Insira mais um funcionário.  

```sql
sqlite> insert into funcionario(codigo, nome,endereco,telefone,cidade,estado,cep, rg, salario) values(04,"Gabi Maria","Rua Fulado Esquina","100222", "São CARLOS","SP",66022000, 9911,"5.500");
```

6) Exiba todos os dados dos funcionários.  

```sql
sqlite> select * from funcionario;
codigo|nome|endereco|telefone|cidade|estado|cep|rg|salario
1|jose silva|Rua tal|1111111|Belém|PA|66020000|1111|2.000
2|jose maria|Rua tal tal|144111|Belém|PA|66030000|2211|1.000
3|maria joaquina|Rua tal Fulado|177111|Cametá|PA|66040000|4411|3.000
3|Gabi joaquina|Rua Fulado Gago|100111|São Paulo|SP|66090000|9911|3.500
4|Gabi Maria|Rua Fulado Esquina|100222|São CARLOS|SP|66022000|9911|5.500
sqlite>
```

7) Crie a tabela fornecedores contendo os campos nome, endereço, telefone, cidade, estado, cep, cnpj e email. Coloque os tipos de dados necessários.  

```sql
sqlite> create table fornecedores(nome text, telefone text, cidade text, estado text, cep text, cnpj int, email text);
sqlite> .tables
Alunos        fornecedores  funcionario
sqlite>
```

8) Insira 2 fornecedores. Código 1 e Código 2  

```sql
sqlite> .schema fornecedores
CREATE TABLE fornecedores(nome text, telefone text, cidade text, estado text, cep text, cnpj int, email text);
sqlite> alter table fornecedores add codigo int;
sqlite> .schema fornecedores
CREATE TABLE fornecedores(nome text, telefone text, cidade text, estado text, cep text, cnpj int, email text, codigo int);
sqlite>

sqlite> insert into fornecedores(nome, telefone, cidade, estado, cep, cnpj, email, codigo) values ("Empresa Tal 1", "9132224422", "Belém", "PA", "66020-000", 123456789,"email@gmail.com", 01);
sqlite> insert into fornecedores(nome, telefone, cidade, estado, cep, cnpj, email, codigo) values ("Empresa Tal 2", "9132222222", "Belém", "PA", "66020-222", 222456789,"email2@gmail.com", 02);
sqlite> insert into fornecedores(nome, telefone, cidade, estado, cep, cnpj, email, codigo) values ("Empresa Tal 3", "9132223332", "Cametá", "PA", "66020-333", 222456333,"email3@gmail.com", 03);
```

9) Selecione o nome e o telefone dos fornecedores.  

```sql
sqlite> select * from fornecedores;
nome|telefone|cidade|estado|cep|cnpj|email|codigo
Empresa Tal 1|9132224422|Belém|PA|66020-000|123456789|email@gmail.com|1
Empresa Tal 2|9132222222|Belém|PA|66020-222|222456789|email2@gmail.com|2
Empresa Tal 3|9132223332|Cametá|PA|66020-333|222456333|email3@gmail.com|3
sqlite>
```

10) Agora iremos aprender uma opção do comando select. Nós podemos restringir o que vai ser exibido na tela. É moleza. Por exemplo se eu quiser listar somente o aluno de código 2 o comando fica assim: select * from alunos where codigo = 2; - Nós apenas adicionamos o WHERE e a CONDIÇÃO. Veja que mantivemos o * para exibir todos os campos, mas poderíamos também exibir somente o nome do aluno 2 assim: select nome from alunos where codigo = 2; - EXPERIMENTE AGORA ESSES 2 COMANDOS.  

```sql
sqlite> .tables
Alunos        fornecedores  funcionario

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

sqlite> select * from Alunos where codigo=2;
codigo|nome|telefone|cidade
2|Ana Maria|987654321|Belem
2|Ana Carolina|777777665|Belem

sqlite> select * from Alunos where cidade="Belem";
codigo|nome|telefone|cidade
1|Ana|123456789|Belem
2|Ana Maria|987654321|Belem
2|Ana Carolina|777777665|Belem
sqlite>
```

11) Selecione o funcionário de código 3.  

```sql
sqlite> select * from funcionario where codigo=3;
codigo|nome|endereco|telefone|cidade|estado|cep|rg|salario
3|maria joaquina|Rua tal Fulado|177111|Cametá|PA|66040000|4411|3.000
3|Gabi joaquina|Rua Fulado Gago|100111|São Paulo|SP|66090000|9911|3.500
sqlite>
```

12) Selecione o fornecedor de código 1.  

```sql
sqlite> select * from fornecedores where codigo=1;
nome|telefone|cidade|estado|cep|cnpj|email|codigo
Empresa Tal 1|9132224422|Belém|PA|66020-000|123456789|email@gmail.com|1
sqlite>
```

13) Selecione o aluno de código 2.  

```sql
sqlite> select * from Alunos where codigo = 2;
codigo|nome|telefone|cidade
2|Ana Maria|987654321|Belem
2|Ana Carolina|777777665|Belem
sqlite>
```

14) Selecione o funcionário de código 1.  

```sql
sqlite> select * from funcionario where codigo = 1;
codigo|nome|endereco|telefone|cidade|estado|cep|rg|salario
1|jose silva|Rua tal|1111111|Belém|PA|66020000|1111|2.000
sqlite>
```

15) Selecione somente o nome e salário do funcionário de código 2.  

```sql
sqlite> select nome,salario from funcionario where codigo =1 ;
nome|salario
jose silva|2.000
sqlite>
```

16) Selecione somente o nome a cidade do aluno de código 1.  

```sql
sqlite> select nome, cidade from Alunos where codigo = 1;
nome|cidade
Ana|Belem
sqlite>
```

17) Selecione todos os funcionários de MG. É assim: select * from funcionários where estado=’MG’; - Como estado é texto eu usei aspas! – Faça isso agora!  

```sql
sqlite> select * from funcionario;
codigo|nome|endereco|telefone|cidade|estado|cep|rg|salario
1|jose silva|Rua tal|1111111|Belém|PA|66020000|1111|2.000
2|jose maria|Rua tal tal|144111|Belém|PA|66030000|2211|1.000
3|maria joaquina|Rua tal Fulado|177111|Cametá|PA|66040000|4411|3.000
3|Gabi joaquina|Rua Fulado Gago|100111|São Paulo|SP|66090000|9911|3.500
4|Gabi Maria|Rua Fulado Esquina|100222|São CARLOS|SP|66022000|9911|5.500

sqlite> select * from funcionario where estado = "PA";
codigo|nome|endereco|telefone|cidade|estado|cep|rg|salario
1|jose silva|Rua tal|1111111|Belém|PA|66020000|1111|2.000
2|jose maria|Rua tal tal|144111|Belém|PA|66030000|2211|1.000
3|maria joaquina|Rua tal Fulado|177111|Cametá|PA|66040000|4411|3.000
sqlite>
```

18) Selecione todos os funcionários de SP.  

```sql
sqlite> select * from funcionario where estado = "SP";
codigo|nome|endereco|telefone|cidade|estado|cep|rg|salario
3|Gabi joaquina|Rua Fulado Gago|100111|São Paulo|SP|66090000|9911|3.500
4|Gabi Maria|Rua Fulado Esquina|100222|São CARLOS|SP|66022000|9911|5.500
sqlite>
```

19) Selecione todos os funcionários de GO.  

```sql
sqlite> select * from funcionario where estado = "GO";
sqlite>
```

20) Insira um funcionário para GO.  

```sql
sqlite> insert into funcionario(codigo, nome,endereco,telefone,cidade,estado,cep, rg, salario) values(06,"Graziela Maria","Tv Esquina","400222", "Cidade Tal","GO",66022000, 9911,"5.500");
sqlite> insert into funcionario(codigo, nome,endereco,telefone,cidade,estado,cep, rg, salario) values(06,"Maria Marta","Tv Esquina Rui","444222", "Cidade Maguito","GO",66332000, 3311,"4.500");
```

21) Selecione todos os funcionários de GO.  

```sql
sqlite> select * from funcionario where estado = "GO";
codigo|nome|endereco|telefone|cidade|estado|cep|rg|salario
6|Graziela Maria|Tv Esquina|400222|Cidade Tal|GO|66022000|9911|5.500
6|Maria Marta|Tv Esquina Rui|444222|Cidade Maguito|GO|66332000|3311|4.500
sqlite>
```

22) Crie a tabela livros contendo o campo código, nome, categoria, resumo, precocusto, precovenda.  

```sql
sqlite> create table livros (codigo int, nome text, categoria text, resumo text, precocusto text, precovenda text);
```

23) Verifique o esquema .schema da tabela livros.  

```sql
sqlite> .schema livros
CREATE TABLE livros (codigo int, nome text, categoria text, resumo text, precocusto text, precovenda text);
sqlite>
```

24) Liste as tabelas existentes.  

```sql
sqlite> .tables
Alunos        fornecedores  funcionario   livros
sqlite>
```

25) Insira 1 livro.  

```sql
sqlite> insert into livros(codigo, nome, categoria, resumo, precocusto, precovenda) values(01, "Livro tal", "Suspence", "livro sobre tal tal ", "20,00", "30,00");
sqlite> insert into livros(codigo, nome, categoria, resumo, precocusto, precovenda) values(02, "Livro tal 2", "Suspence", "livro sobre tal tal tal ", "30,00", "35,00");
sqlite> insert into livros(codigo, nome, categoria, resumo, precocusto, precovenda) values(03, "Livro tal 4", "Romance", "livro tal tal tal ", "50,00", "55,00");
sqlite> insert into livros(codigo, nome, categoria, resumo, precocusto, precovenda) values(05, "Livro tal 5", "Romance", "livro tal tal ", "40,00", "55,00");
sqlite> insert into livros(codigo, nome, categoria, resumo, precocusto, precovenda) values(06, "Livro tal 6", "Romance", "livro tal ", "70,00", "75,00");
sqlite> insert into livros(codigo, nome, categoria, resumo, precocusto, precovenda) values(07, "Livro tal 7", "Comedia", "livro tal tal ", "10,00", "15,00");
sqlite> insert into livros(codigo, nome, categoria, resumo, precocusto, precovenda) values(08, "Livro tal 8", "Comedia", "livro tal tal ta ", "20,00", "25,00");
```

26) Selecione o nome e a categoria do livro de código 1.  

```sql
sqlite> select nome, categoria from livros where codigo = 1;
nome|categoria
Livro tal|Suspence
sqlite>
```

27) Selecione o nome e a categoria do livro de código 3.  

```sql
sqlite> select nome, categoria from livros where codigo = 3;
nome|categoria
Livro tal 4|Romance
sqlite>
```

28) Exclua a tabela livros.  

```sql
sqlite> drop table livros;
sqlite> .tables
Alunos        fornecedores  funcionario
sqlite>
```

29) Altere o nome da tabela aluno para estudantes.  

```sql
sqlite> .tables
Alunos        fornecedores  funcionario
sqlite> alter table Alunos rename to estudantes;
sqlite> .tables
estudantes    fornecedores  funcionario
sqlite>
```

30) Altere a tabela alunos inserindo o campo estado. Se estiver com dúvidas consulte a primeira lista de exercícios.  

```sql
sqlite> .schema estudantes
CREATE TABLE IF NOT EXISTS "estudantes"
(
    codigo INT,
    nome TEXT,
    telefone TEXT,
    cidade TEXT
);

sqlite> alter table estudantes add estado text;

sqlite> .schema estudantes
CREATE TABLE IF NOT EXISTS "estudantes"
(
    codigo INT,
    nome TEXT,
    telefone TEXT,
    cidade TEXT
, estado text);
sqlite>
```
