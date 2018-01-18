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