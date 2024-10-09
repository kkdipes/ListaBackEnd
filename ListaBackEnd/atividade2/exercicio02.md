# Exercício 02: Gerador de Personagem


## Objetivo

Criar um programa que gere e manipule personagens de jogo usando classes.

## Instruções

* Crie uma classe chamada `Personagem` que implemente os atributos `nome`, `vida` e `ataque`, além de dos métodos `receberDano` e `atacar`;
* O método `receberDano` recebe um parâmetro do tipo `int` que subtrai da `vida` do objeto. Se o valor da `vida` for menor ou igual a zero, o método deve imprimir uma mensagem informando que o personagem foi derrotado;
* O método `atacar` recebe um parâmetro do tipo `Personagem` chamado `alvo` e chama o método `receberDano`, passando o ataque do personagem atacante como parâmetro. Caso a vida do `alvo` seja igual a zero, o método deve imprimir uma mensagem informando que o `ataque falhou`;
* No método `main` da classe principal, crie crie uma lista de `Personagem` chamada de `inimigos` e adicione pelo menos três personagens diferentes;
* Crie um `Personagem` chamado `jogador` e use o método `atacar` passando como parâmetro aleatoriamente um dos personagens da lista `inimigos`. O jogador não deve atacar inimigos com vida igual a 0;
* Após o ataque do jogador, crie um loop que percorre a lista de `inimigos` e chama o método `atacar` de cada um deles passando como parâmetro o `jogador`;
* Repita os dois últimos passos até que o `jogador` ou todos os `inimigos` tenham a vida zerada e imprima o resultado final.

## Entradas (inputs)

````txt
Orc / Vida: 100 / Ataque: 10
Goblin / Vida: 50 / Ataque: 5
Lobo / Vida: 75 / Ataque: 15
Cavaleiro / Vida: 200 / Ataque: 20
Dragão / Vida: 500 / Ataque: 50

Steve / Vida: 100 / Ataque: 20
````

## Saídas (outputs)

````txt
Orc foi derrotado!
Goblin foi derrotado!
Steve foi derrotado!
````

### RESOLUÇÃO ###

import random

class Personagem:
    def __init__(self, nome, vida, ataque):
        self.nome = nome
        self.vida = vida
        self.ataque = ataque

    def receberDano(self, dano):
        self.vida -= dano
        if self.vida <= 0:
            self.vida = 0
            print(f"{self.nome} foi derrotado!")
    
    def atacar(self, alvo):
        if self.vida > 0:
            if alvo.vida > 0:
                alvo.receberDano(self.ataque)
            else:
                print(f"O ataque falhou! {alvo.nome} já está derrotado.")
        else:
            print(f"{self.nome} não pode atacar porque foi derrotado.")

def main():
    # Criando uma lista de inimigos
    inimigos = [
        Personagem("Orc", 100, 10),
        Personagem("Goblin", 50, 5),
        Personagem("Lobo", 75, 15),
        Personagem("Cavaleiro", 200, 20),
        Personagem("Dragão", 500, 50)
    ]

    # Criando o personagem jogador
    jogador = Personagem("Steve", 100, 20)

    # Loop da batalha
    while jogador.vida > 0 and any(inimigo.vida > 0 for inimigo in inimigos):
        # Jogador ataca um inimigo aleatório
        inimigo_vivo = [inimigo for inimigo in inimigos if inimigo.vida > 0]
        alvo = random.choice(inimigo_vivo)
        print(f"\n{jogador.nome} está atacando {alvo.nome}!")
        jogador.atacar(alvo)
        
        # Inimigos atacam o jogador
        for inimigo in inimigos:
            if inimigo.vida > 0:
                print(f"\n{inimigo.nome} está atacando {jogador.nome}!")
                inimigo.atacar(jogador)
            if jogador.vida <= 0:
                break
    
    # Resultado final
    if jogador.vida > 0:
        print("\nSteve venceu a batalha!")
    else:
        print("\nSteve foi derrotado!")

# Executa a função principal
main()
