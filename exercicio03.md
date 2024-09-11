# Exercício 03: Barcos e Portos


## Objetivo

Criar um programa que gere e manipule barcos e portos usando classes e herança.

## Instruções

* Crie uma classe chamada `Barco` contendo os atributos `nome` e `tamanho`;
* Crie uma classe chamada `BasePorto` contendo os atributos `nome`, um array de `barcosAtracados` e dois métodos método chamados `atracarBarco` e `desatracarBarco`;
* O método `atracarBarco` recebe um objeto `Barco` e adiciona o barco ao array de `barcosAtracados`;
* O método `desatracarBarco` recebe um objeto `Barco` e remove o barco do array de `barcosAtracados`;
* Crie uma classe  chamada `PortoPequeno` que herda da classe `BasePorto`. Sobreescreva o método `atracarBarcos` para que ele permita apenas a atracagem de barcos com tamanho menor ou igual a 10;
* Crie uma classe  chamada `PortoGrande que herda da classe `BasePorto`. Sobreescreva o método `atracarBarcos` para que ele permita apenas a atracagem de barcos com tamanho maior ou igual a 10;
* No método `main`:
  * Crie uma lista contendo 5 barcos com diferentes tamanhos e dois portos (um pequeno e um grande);
  * Percorra a lista de barcos e use o método `atracarBarco` para atracar cada barco em um dos portos;
  * Os barcos devem tentar ser atracados primeiramente no porto pequeno e, se não puderem, devem ser atracados no porto grande.

## Entradas (inputs)

````txt
Barco 1: Tamanho 2
Barco 2: Tamanho 5
Barco 3: Tamanho 7
Barco 4: Tamanho 12
Barco 5: Tamanho 20
````

## Saídas (outputs)

````txt
Barco 1 atracado no porto pequeno
Barco 2 atracado no porto pequeno
Barco 3 atracado no porto pequeno
Barco 4 atracado no porto grande
Barco 5 atracado no porto grande
````



### RESOLUÇÃO ###

class Barco:
    def __init__(self, nome, tamanho):
        self.nome = nome
        self.tamanho = tamanho

class BasePorto:
    def __init__(self, nome):
        self.nome = nome
        self.barcosAtracados = []

    def atracarBarco(self, barco):
        self.barcosAtracados.append(barco)
        print(f"{barco.nome} atracado no {self.nome}")

    def desatracarBarco(self, barco):
        if barco in self.barcosAtracados:
            self.barcosAtracados.remove(barco)
            print(f"{barco.nome} desatracado do {self.nome}")
        else:
            print(f"{barco.nome} não está atracado no {self.nome}")

class PortoPequeno(BasePorto):
    def atracarBarco(self, barco):
        if barco.tamanho <= 10:
            super().atracarBarco(barco)
        else:
            print(f"{barco.nome} é muito grande para o {self.nome}")

class PortoGrande(BasePorto):
    def atracarBarco(self, barco):
        if barco.tamanho >= 10:
            super().atracarBarco(barco)
        else:
            print(f"{barco.nome} é muito pequeno para o {self.nome}")

def main():
    # Criando uma lista de barcos
    barcos = [
        Barco("Barco 1", 2),
        Barco("Barco 2", 5),
        Barco("Barco 3", 7),
        Barco("Barco 4", 12),
        Barco("Barco 5", 20)
    ]

    # Criando os portos
    porto_pequeno = PortoPequeno("Porto Pequeno")
    porto_grande = PortoGrande("Porto Grande")

    # Tentando atracar cada barco
    for barco in barcos:
        if barco.tamanho <= 10:
            porto_pequeno.atracarBarco(barco)
        else:
            porto_grande.atracarBarco(barco)

# Executa a função principal
main()
