# Exercício 00: Gerador de Username

## Objetivo

Criar um programa que gere nomes de usuário (usernames) baseados em dois nomes fornecidos pelo usuário e um número aleatório.

## Instruções

* Crie um programa que solicite ao usuário que insira dois nomes (nome e sobrenome).
* Gere um número aleatório entre 1 e 100.
* Concatene o nome, sobrenome e o número aleatório para formar um nome de usuário.
* Exiba o nome de usuário gerado.

## Especificações

### Entradas (inputs)
O usuário fornecerá um nome e um sobrenome pelo console. Ex.: (`Ronaldo` e `Fenomeno`)

### Saídas (outputs)
O programa exibirá um nome de usuário gerado automaticamente, combinando o nome fornecido com um número aleatório. Ex.: (`RonaldoFenomeno98`)

### RESOLUÇÃO ###
import random

def gerar_username():
    # Solicita ao usuário que insira o nome e o sobrenome
    nome = input("Digite o seu nome: ")
    sobrenome = input("Digite o seu sobrenome: ")
    
    # Gera um número aleatório entre 1 e 100
    numero_aleatorio = random.randint(1, 100)
    
    # Concatena o nome, sobrenome e o número aleatório
    username = f"{nome}{sobrenome}{numero_aleatorio}"
    
    # Exibe o nome de usuário gerado
    print(f"Nome de usuário gerado: {username}")

# Executa a função para gerar o username
gerar_username()
