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

´´´sql

´´´

2) Crie uma trigger para que toda vez que seja inserido um novo registro na tabela editora seja gravado um registro na tabela auditoria com a informação “Registro inserido”  

´´´sql

´´´

3) Crie uma trigger para que toda vez que seja excluído um registro na tabela editora seja gravado um registro na tabela auditoria com a informação “Registro excluído”  

´´´sql

´´´

4) Faça um join na tabela de livros com autores mostrando o título do livro e do autor.  

´´´sql

´´´

5) Faça um join na tabela de livros com autores mostrando o título do livro e do autor usando agora um LEFT OUTER JOIN para mostrar inclusive os livros que não tenham autor definido.  

´´´sql

´´´

6) Escreva um bloco de transação que exclua o livro de código 1 e insira um novo livro de código 50. Mas dê um rollback na transação.  

´´´sql

´´´

7) Escreva um bloco de transação que exclua o livro de código 3 e insira um novo livro de código 3. Feche a transação com Commit.  

´´´sql

´´´

8) Fazer um select no Banco e retornar os seguintes campos:  
· Nome do autor em letras maiúsculas  
· Nome do estilo em letras minúsculas  
· As 10 primeiras letras do nome do livro  
· Valor do Livro  
· Valor do Livro com desconto de 7%  
Atenção: Trata-se de UM ÚNICO COMANDO SELECT para retornar todos os campos acima.  

´´´sql

´´´

9) Faça um select trazendo o nome do livro, código do estilo, código do autor e código da editora. Caso algum campo desse esteja NULL mostre a mensagem SEM CADASTRO.  

´´´sql

´´´

10) Mostre o nome das 6 primeiras editoras em ordem alfabética e em letras maiúsculas.  

´´´sql

´´´

11) Faça um select mostrando o nome do livro e o tamanho em caracteres do nome  

´´´sql

´´´

12) Exiba a data atual  

´´´sql

´´´

13) Exiba a versão do SQLite  

´´´sql

´´´

14) Exiba o nome das editoras substituindo a letra a por X  

´´´sql

´´´

15) Grite bem alto “TERMINEI TODOS OS EXERCÍCIOS!!!!!!!” ;-)  


´´´sql

´´´
