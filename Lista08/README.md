# Resumo Udemy - Aprenda SQL do Zero

https://www.udemy.com/aprenda-sql-do-zero

---

## Lista 08 - Exercício

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

1) Faça um select somente de 10 editoras de GO  
2) Exiba o nome das editoras em ordem inversa e retorne as 3 primeiras  
3) Exiba todos os estados que temos editoras cadastradas  
4) Crie uma view para o select que você fez no exercício 1 com o nome de GOIAS.  
5) Crie uma view para o select que você fez no exercício 3 com o nome de ESTADOS.  
6) Crie um índice para o estado na tabela Editora  
7) Crie um índice para o nome do autor.  
8) Utilize subselect e exclua todos os livros da editora XPTO  
9) Utilize subselect e exclua todos os livros do autor José Buscapé  
10) Exclua a view GOIAS  
11) Exclua o índice da tabela Editora  
12) Exclua a view Estados  
13) Exiba em ordem alfabética as editoras e mostre as 7 primeiras (somente o nome).  
14) Exclua o índice da tabela autor  
15) Crie um índice para o nome do livro  

--- 

1) Faça um select somente de 10 ou 2 editoras de GO/SP  

```sql
SELECT editora.nome, estado
from editora
where estado="SP" LIMIT 2;
```

2) Exiba o nome das editoras em ordem inversa e retorne as 3 primeiras  

```sql
SELECT nome
from editora
ORDER BY nome DESC
LIMIT 4;
```

3) Exiba todos os estados que temos editoras cadastradas  

```sql
SELECT DISTINCT estado
from editora;
```

4) Crie uma view para o select que você fez no exercício 1 com o nome de GOIAS.  

```sql

CREATE VIEW GOIAIS2 AS
SELECT DISTINCT cidade, estado
  FROM fakenames
  WHERE estado="GO";


SELECT * from GOIAIS2;
```

5) Crie uma view para o select que você fez no exercício 3 com o nome de ESTADOS.  

```sql

CREATE VIEW ESTADOS AS
SELECT DISTINCT estado
  FROM fakenames;

SELECT * FROM ESTADOS;
```

6) Crie um índice para o estado na tabela Editora(ou em outra)  

```sql
CREATE INDEX idx_estado ON fakenames(estado); 
```

7) Crie um índice para o nome do autor.  

```sql
Create INDEX idx_cidade on fakenames(cidade);
```

8) Utilize subselect e exclua todos os livros da editora XPTO  

```sql
DELETE from livro
where id=(
    SELECT id
    FROM editora
    WHERE id=3
);
```

9) Utilize subselect e exclua todos os livros do autor José Buscapé  

```sql
DELETE from livro
WHERE id=(
    SELECT id 
    from autor
    WHERE nome="José"
);
```

10) Exclua a view GOIAS  

```sql
DROP VIEW ESTADOS;
DROP VIEW GOIAS;

```

11) Exclua o índice da tabela Editora  

```sql
drop INDEX idx_editora;
```

12) Exclua a view Estados  

```sql
drop INDEX idx_estado;
```

13) Exiba em ordem alfabética as editoras e mostre as 7 primeiras (somente o nome).  

```sql
SELECT DISTINCT cidade, estado
FROM fakenames
  ORDER BY cidade
LIMIT 10;
```

14) Exclua o índice da tabela autor  

```sql
drop INDEX idx_autor;
```

15) Crie um índice para o nome do livro  


```sql
CREATE INDEX idx_cidades ON fakenames(cidade);
```
