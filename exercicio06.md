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

### RESOLUÇÃO ###

class Cliente:
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

class Filme:
    def __init__(self, nome, preco, idadeMinima):
        self.nome = nome
        self.preco = preco
        self.idadeMinima = idadeMinima

class Ingresso:
    def __init__(self, cliente, filme, assento):
        self.cliente = cliente
        self.filme = filme
        self.assento = assento

class Cinema:
    def __init__(self):
        self.filmesDisponiveis = []
        self.ingressosVendidos = []
        self.assentosDisponiveis = [f"{linha}{coluna}" for linha in "ABCDEF" for coluna in range(1, 6)]

    def adicionarFilme(self, filme):
        self.filmesDisponiveis.append(filme)

    def venderIngresso(self, cliente, nomeFilme, assento):
        try:
            filmeEscolhido = next(filme for filme in self.filmesDisponiveis if filme.nome == nomeFilme)
        except StopIteration:
            raise Exception("O filme não está disponível.")

        if cliente.idade < filmeEscolhido.idadeMinima:
            raise Exception("O ingresso não pode ser vendido pois sua idade não permite!")

        if assento not in self.assentosDisponiveis:
            raise Exception("O ingresso não pode ser vendido pois seu assento não está mais disponível!")

        ingresso = Ingresso(cliente, filmeEscolhido, assento)
        self.ingressosVendidos.append(ingresso)
        self.assentosDisponiveis.remove(assento)

        print(f"Ingresso vendido com sucesso! {filmeEscolhido.nome} - {assento} - {cliente.nome}")

def main():
    cinema = Cinema()

    # Adicionando filmes disponíveis
    cinema.adicionarFilme(Filme("Homem Aranha", 15.00, 12))
    cinema.adicionarFilme(Filme("A Origem", 20.00, 16))
    cinema.adicionarFilme(Filme("Toy Story", 10.00, 0))
    cinema.adicionarFilme(Filme("O Senhor dos Anéis", 25.00, 14))
    cinema.adicionarFilme(Filme("Coringa", 30.00, 18))

    while True:
        try:
            nomeFilme = input("Que filme você deseja assistir? ")
            assento = input("Qual assento você deseja? ")
            nomeCliente = input("Qual o seu nome? ")
            idadeCliente = int(input("Qual a sua idade? "))

            cliente = Cliente(nomeCliente, idadeCliente)
            cinema.venderIngresso(cliente, nomeFilme, assento)

            repetir = input("Deseja comprar outro ingresso? (s/n): ").strip().lower()
            if repetir != 's':
                break
        except Exception as e:
            print(e)
            repetir = input("Deseja tentar novamente? (s/n): ").strip().lower()
            if repetir != 's':
                break

if __name__ == "__main__":
    main()


````txt
O ingresso não pode ser vendido pois sua idade não permite!
O ingresso não pode ser vendido pois seu assento não está mais disponível!
Ingresso vendido com sucesso! Homen Aranha - A1 - Rivelino
````
