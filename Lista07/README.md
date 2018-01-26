# Resumo Udemy - Aprenda SQL do Zero

https://www.udemy.com/aprenda-sql-do-zero

---

## Lista 07 - Exercício

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

1) Conte o número de editoras cadastradas  
2) Calcule a média do preço de venda dos livros  
3) Atualize o preço de venda do livro 1 aumentando seu valor em 7%  
4) Conte a quantidade de editoras de MG.  
5) Conte o número de editoras agrupando por estado.  
6) Diminua o preço de todos os livros da editora 1 em 19%.  
7) Qual o maior código de autor cadastrado?  
8) Qual o menor código de autor cadastrado?  
9) Conte o número de editoras, agrupando por estado e somente para estados que tenham 40 ou mais editoras.  
10) Aumente o preço de todos os livros em 7,5%  
11) Exclua todas as editoras do estado DF.  
12) Os livros podem ser vendidos em 3 parcelas sendo a primeira parcela 30% do valor do livro e a segunda e terceira sendo 35% cada. Faça um select que mostre o nome do livro juntamente com o preço dele e os valor das parcelas.  
13) Todas as editoras do DF mudaram para GO. Atualize no banco de dados por favor!  
14) Quantas editoras temos em cidades que começam pela letra M?  
15) Altere o preço de todos os livros dando um desconto de 6%  

---

1) Conte o número de editoras cadastradas  

```sql
sqlite> select count(*) "total editoras" from editora;
total editoras
101
```

2) Calcule a média do preço de venda dos livros  

```sql
sqlite> select * from livro;
id|titulo|autor_id|editora_id|estilo_id|sinopse|isbn|precovenda
1|Anjos e Demônios|2|1|1|Livro excelente com uma historia legal|7878787878|87.580035
2|A Arte da Guerra||4||||30.315
2|Código da Vinci|1|2|1|Outro livro excelente com uma historia legal|555544448888|20.21
3|SQL de A a Z||||||

sqlite> select avg(precovenda) "Preço Médio" from livro;
Preço Médio
46.0350116666667

```

3) Atualize o preço de venda do livro 1 aumentando seu valor em 7%  

```sql
sqlite> select id,titulo, precovenda from livro;
id|titulo|precovenda
1|Anjos e Demônios|87.580035
2|A Arte da Guerra|30.315
2|Código da Vinci|20.21
3|SQL de A a Z|

sqlite> update livro set precovenda = precovenda + (precovenda * 0.07) where id=1;

sqlite> select id,titulo, precovenda from livro;
id|titulo|precovenda
1|Anjos e Demônios|93.71063745
2|A Arte da Guerra|30.315
2|Código da Vinci|20.21
3|SQL de A a Z|

```

4) Conte a quantidade de editoras de MG.  

```sql
sqlite> select estado, count(*) as "Total" from editora where estado="MG";
estado|Total
MG|44
```

5) Conte o número de editoras agrupando por estado.  

```sql
sqlite> select estado, count(*) "Total" from editora group by estado;
estado|Total
|2
GO|20
MG|44
N.|1
SP|34

```

6) Diminua o preço de todos os livros da editora 1 em 19%.  

```sql
sqlite> select id, titulo,precovenda, editora_id from livro;
id|titulo|precovenda|editora_id
1|Anjos e Demônios|93.71063745|1
2|A Arte da Guerra|30.315|4
2|Código da Vinci|20.21|2
3|SQL de A a Z||

sqlite> update livro set precovenda = precovenda - (precovenda * 0.19) where editora_id=1;

sqlite> select id, titulo,precovenda, editora_id from livro;
id|titulo|precovenda|editora_id
1|Anjos e Demônios|75.9056163345|1
2|A Arte da Guerra|30.315|4
2|Código da Vinci|20.21|2
3|SQL de A a Z||
```

7) Qual o maior código de autor cadastrado?  

```sql
sqlite> select max(id) from autor;
max(id)
8
```

8) Qual o menor código de autor cadastrado?  

```sql
sqlite> select min(id) from autor;
min(id)
1

```

9) Conte o número de editoras, agrupando por estado e somente para estados que tenham 40 ou mais editoras.  

```sql
sqlite> select estado, count(*) "Total" from editora group by estado;
estado|Total
|2
GO|20
MG|44
N.|1
SP|34

sqlite> select estado, count(*) "Total" from editora group by estado having count(*) >= 20;
estado|Total
GO|20
MG|44
SP|34
```

10) Aumente o preço de todos os livros em 7,5%  

```sql
sqlite> select id,titulo,precovenda from livro;
id|titulo|precovenda
1|Anjos e Demônios|75.9056163345
2|A Arte da Guerra|30.315
2|Código da Vinci|20.21
3|SQL de A a Z|

sqlite> update livro set precovenda = precovenda + (precovenda * 0.075);

sqlite> select id,titulo,precovenda from livro;
id|titulo|precovenda
1|Anjos e Demônios|81.5985375595875
2|A Arte da Guerra|32.588625
2|Código da Vinci|21.72575
3|SQL de A a Z|
sqlite>
```

11) Exclua todas as editoras do estado DF.  

```sql
sqlite> delete from editora where estado="DF";
```

12) Os livros podem ser vendidos em 3 parcelas sendo a primeira parcela 30% do valor do livro e a segunda e terceira sendo 35% cada. Faça um select que mostre o nome do livro juntamente com o preço dele e os valor das parcelas.  

```sql
sqlite> select id,titulo,precovenda from livro;
id|titulo|precovenda
1|Anjos e Demônios|81.5985375595875
2|A Arte da Guerra|32.588625
2|Código da Vinci|21.72575
3|SQL de A a Z|

sqlite> select titulo,precovenda, precovenda * 0.3 as "Parcela 1", precovenda * 0.35 as "Parcela 2", precovenda * 0.35 as "Parcela 3" from livro;
titulo|precovenda|Parcela 1|Parcela 2|Parcela 3
Anjos e Demônios|81.5985375595875|24.4795612678762|28.5594881458556|28.5594881458556
A Arte da Guerra|32.588625|9.7765875|11.40601875|11.40601875
Código da Vinci|21.72575|6.517725|7.6040125|7.6040125
SQL de A a Z||||

```

13) Todas as editoras do DF mudaram para GO. Atualize no banco de dados por favor!  

```sql
id|estado|count(*)
89|GO|20
109|MG|43
10|PR|4
107|SP|34

sqlite> update editora set estado="GO" where estado="PR";

sqlite> select id,estado, count(*) from editora editora group by estado;
id|estado|count(*)
10|GO|24
109|MG|43
107|SP|34

```

14) Quantas editoras temos em cidades que começam pela letra M?  

```sql
sqlite> select count(*) "Total Editora" from editora;
Total Editora
101

sqlite> select count(*) "Total Editora Que começa com M" from editora where nome like "M%";
Total Editora Que começa com M
8
sqlite>
```


15) Altere o preço de todos os livros dando um desconto de 6%  


```sql
sqlite> select id, titulo, precovenda from livro;
id|titulo|precovenda
1|Anjos e Demônios|81.5985375595875
2|A Arte da Guerra|32.588625
2|Código da Vinci|21.72575
3|SQL de A a Z|

sqlite> update livro set precovenda = precovenda - (precovenda * 0.06);

sqlite> select id, titulo, precovenda from livro;
id|titulo|precovenda
1|Anjos e Demônios|76.7026253060123
2|A Arte da Guerra|30.6333075
2|Código da Vinci|20.422205
3|SQL de A a Z|

sqlite> update livro set precovenda = precovenda * 0.94 where id=1;

sqlite> select id, titulo, precovenda from livro;
id|titulo|precovenda
1|Anjos e Demônios|72.1004677876515
2|A Arte da Guerra|30.6333075
2|Código da Vinci|20.422205
3|SQL de A a Z|

```
