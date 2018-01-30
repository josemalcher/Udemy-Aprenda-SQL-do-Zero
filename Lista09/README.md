# Resumo Udemy - Aprenda SQL do Zero

https://www.udemy.com/aprenda-sql-do-zero

---

## Lista 09 - Exercício

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

1) Crie uma tabela de auditoria contendo os campos editora_id, data e observação  
2) Crie uma trigger para que toda vez que seja inserido um novo registro na tabela editora seja gravado um registro na tabela auditoria com a informação “Registro inserido”  
3) Crie uma trigger para que toda vez que seja excluído um registro na tabela editora seja gravado um registro na tabela auditoria com a informação “Registro excluído”  
4) Faça um join na tabela de livros com autores mostrando o título do livro e do autor.  
5) Faça um join na tabela de livros com autores mostrando o título do livro e do autor usando agora um LEFT OUTER JOIN para mostrar inclusive os livros que não tenham autor definido.  
6) Escreva um bloco de transação que exclua o livro de código 1 e insira um novo livro de código 50. Mas dê um rollback na transação.  
7) Escreva um bloco de transação que exclua o livro de código 3 e insira um novo livro de código 3. Feche a transação com Commit.  
8) Fazer um select no Banco e retornar os seguintes campos:  
· Nome do autor em letras maiúsculas  
· Nome do estilo em letras minúsculas  
· As 10 primeiras letras do nome do livro  
· Valor do Livro  
· Valor do Livro com desconto de 7%  
Atenção: Trata-se de UM ÚNICO COMANDO SELECT para retornar todos os campos acima.  

9) Faça um select trazendo o nome do livro, código do estilo, código do autor e código da editora. Caso algum campo desse esteja NULL mostre a mensagem SEM CADASTRO.  
10) Mostre o nome das 6 primeiras editoras em ordem alfabética e em letras maiúsculas.  
11) Faça um select mostrando o nome do livro e o tamanho em caracteres do nome  
12) Exiba a data atual  
13) Exiba a versão do SQLite  
14) Exiba o nome das editoras substituindo a letra a por X  
15) Grite bem alto “TERMINEI TODOS OS EXERCÍCIOS!!!!!!!” ;-)  

---

1) Crie uma tabela de auditoria contendo os campos editora_id, data e observação  

```sql
  CREATE TABLE auditoria_exer (editora_id, data date, obs tex);
```

2) Crie uma trigger para que toda vez que seja inserido um novo registro na tabela editora seja gravado um registro na tabela auditoria com a informação “Registro inserido”  

```sql

CREATE TRIGGER auditoria_exer AFTER INSERT ON editora
  BEGIN
  INSERT INTO auditoria_exer(editora_id, data, obs)
      VALUES (new.id, datetime('now'), "Registro inserido");
END;

--teste
INSERT INTO editora(id, nome, cidade, estado, telefone, email)
    VALUES (10,"NOVATEC Editora", "São Paulo", "SP", "011 99999", "contato@gmail.co");
```

3) Crie uma trigger para que toda vez que seja excluído um registro na tabela editora seja gravado um registro na tabela auditoria com a informação “Registro excluído”  

```sql
INSERT INTO editora(id, nome, cidade, estado, telefone, email)
    VALUES (10,"NOVATEC Editora", "São Paulo", "SP", "011 99999", "contato@gmail.co");

CREATE TRIGGER auditoria_exer_del AFTER DELETE ON editora
  BEGIN
  INSERT INTO auditoria_exer(editora_id, data, obs)
      VALUES (old.id, datetime('now'), "Registro Deletado");
END;

--teste
DELETE from editora WHERE id = 2;
DELETE from editora WHERE id = 3;
DELETE from editora WHERE id = 4;


```

4) Faça um join na tabela de livros com autores mostrando o título do livro e do autor.  

```sql

SELECT l.titulo, a.nome
FROM livro l, autor a
WHERE a.id = l.autor_id;

SELECT titulo, nome
from autor INNER JOIN livro
ON autor.id = livro.autor_id;
```

5) Faça um join na tabela de livros com autores mostrando o título do livro e do autor usando agora um LEFT OUTER JOIN para mostrar inclusive os livros que não tenham autor definido.  

```sql

SELECT titulo,nome
FROM livro LEFT OUTER JOIN autor
ON autor.id = livro.autor_id;

```

6) Escreva um bloco de transação que exclua o livro de código 1 e insira um novo livro de código 50. Mas dê um rollback na transação.  

```sql

BEGIN TRANSACTION ;
DELETE from livro WHERE id=1;
INSERT INTO livro(id,titulo) VALUES (11, "So o nome");
ROLLBACK;


```

7) Escreva um bloco de transação que exclua o livro de código 3 e insira um novo livro de código 3. Feche a transação com Commit.  

```sql
BEGIN TRANSACTION ;
DELETE from livro WHERE id=3;
INSERT INTO livro(id,titulo) VALUES (11, "So o nome");
COMMIT ;
```

8) Fazer um select no Banco e retornar os seguintes campos:  
· Nome do autor em letras maiúsculas  
· Nome do estilo em letras minúsculas  
· As 10 primeiras letras do nome do livro  
· Valor do Livro  
· Valor do Livro com desconto de 7%  
Atenção: Trata-se de UM ÚNICO COMANDO SELECT para retornar todos os campos acima.  

```sql
SELECT
  upper(a.nome),
  lower(e.nome),
  substr(l.titulo,1,10),
  l.precovenda,
  l.precovenda * 0.93
FROM livro l, autor a, estilo e
WHERE a.id = l.autor_id
AND e.id = l.estilo_id;
```

9) Faça um select trazendo o nome do livro, código do estilo, código do autor e código da editora. Caso algum campo desse esteja NULL mostre a mensagem SEM CADASTRO.  

```sql
SELECT titulo,
  ifnull(estilo_id, "SEM CADASTRO"),
  ifnull(autor_id, "SEM CADASTRO"),
  ifnull(editora_id, "SEM CADASTRO")
FROM livro;
```

10) Mostre o nome das 6 primeiras editoras em ordem alfabética e em letras maiúsculas.  

```sql
SELECT upper(nome)
FROM editora
ORDER BY nome
LIMIT 6;
```

11) Faça um select mostrando o nome do livro e o tamanho em caracteres do nome  

```sql
SELECT titulo, length(titulo) FROM livro;
```

12) Exiba a data atual  

```sql
SELECT date('now');
```

13) Exiba a versão do SQLite  

```sql
SELECT sqlite_version();
```

14) Exiba o nome das editoras substituindo a letra a por X  

```sql
SELECT replace(nome, "a","x") FROM editora;
```

15) Grite bem alto “TERMINEI TODOS OS EXERCÍCIOS!!!!!!!” ;-)  


```sql
          --    \o/
```
