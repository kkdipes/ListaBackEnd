# Exercício 06: Ticket do Cinema

## Objetivo

Crie um programa, utilizando Exceções e Collections, que permita realizar a compra de tickets para assistir filmes no cinema.

## Instruções

* Crie uma classe chamada `Cliente`, `Cinema`, `Filme` e `Ingresso`.
* Na classe cliente, implemente um POJO contendo os atributos `nome` e 'idade'.
* Na classe `Cinema`, adicione uma collection (sugestão: `ArrayList`) com `filmesDisponiveis` e insira pelo menos 5 filmes.
* Na classe `Cinema`, adicione uma lista com `ingressosVendidos`.
* Na classe `Filme`, adicione os atributos `nome`, `preco`, `idadeMinima`.
* Na classe `Ingresso`, adicione os atributos `cliente`, `filme` e `assento`.
* Crie uma classe `Main` para testar o programa.
  * 1. Crie uma instância da classe `Cinema` e adicione os filmes disponíveis.
  * 2. Crie uma instância da classe `Ingresso` e peça ao usuário para inserir o nome do cliente, o nome do filme e o assento desejado (de A1 a F5).
  * 2.1. O programa deve retornar uma Exception caso o assento não esteja mais disponível ou a idade do cliente não seja compatível com a idade mínima do filme.
  * 3. Adicione o ingresso à lista de ingressos vendidos.
  * 4. Imprima uma mensagem informando que o ingresso foi vendido com sucesso.
  * 5. Repita os passos 2 ao 4 novamente.


## Entradas (inputs)

````txt
Que filme você deseja assistir?
Homen Aranha
Qual assento você deseja?
A1
Qual o seu nome?
Rivelino
Qual a sua idade?
16
````

## Saídas (outputs)

````txt
O ingresso não pode ser vendido pois sua idade não permite!
O ingresso não pode ser vendido pois seu assento não está mais disponível!
Ingresso vendido com sucesso! Homen Aranha - A1 - Rivelino
````