# Exercício 01: Recomendador de Filmes


## Objetivo

Criar um programa recomende uma série, livro ou filme com base nas respostas fornecidas pelo usuário.

## Instruções

* Crie um programa que imprima ao usuário duas perguntas;
* Cada pergunta deve ser respondida com um número inteiro `1` ou `2`;
* Caso o número não seja `1` ou `2`, o programa deve ser encerrado sem erros;
* Ao final, o programa deve exibir uma recomendação com base nas respostas fornecidas pelo usuário;
* O programa deverá fornecer pelo menos quatro recomendações diferentes com base nas respostas fornecidas pelo usuário.

## Conjunto de dados (dataset) [opcional]
````
Homens de Preto, Arrival, Shrek, Gladiador
````

````
Pergunta 1: Que ambientação você prefere?
  1. Sci-fi
  2. Medieval

Pergunta 2: Que gênero você prefere?
  1. Comédia
  2. Drama
````

## Entradas (inputs)
O usuário responderá a cada pergunta digitando os números 1 ou 2 pelo console. Caso o número não esteja entre 1 e 2, o programa deve ser encerrado sem erros. Ex.: (`1` e `1`)

## Saídas (outputs)
O programa exibirá o nome de uma série, livro ou filme recomendado com base nas respostas. Ex.: (`Homens de Preto`)


### RESOLUÇÃO ###

def recomendador_filmes():
    # Pergunta 1: Que ambientação você prefere?
    print("Pergunta 1: Que ambientação você prefere?")
    print("  1. Sci-fi")
    print("  2. Medieval")
    resposta1 = input("Digite 1 ou 2: ")
    
    # Verifica se a resposta é válida
    if resposta1 not in ['1', '2']:
        return
    
    # Pergunta 2: Que gênero você prefere?
    print("\nPergunta 2: Que gênero você prefere?")
    print("  1. Comédia")
    print("  2. Drama")
    resposta2 = input("Digite 1 ou 2: ")
    
    # Verifica se a resposta é válida
    if resposta2 not in ['1', '2']:
        return
    
    # Recomendação com base nas respostas
    if resposta1 == '1' and resposta2 == '1':
        recomendacao = "Homens de Preto"
    elif resposta1 == '1' and resposta2 == '2':
        recomendacao = "Arrival"
    elif resposta1 == '2' and resposta2 == '1':
        recomendacao = "Shrek"
    elif resposta1 == '2' and resposta2 == '2':
        recomendacao = "Gladiador"
    
    # Exibe a recomendação
    print(f"\nRecomendação: {recomendacao}")

# Executa a função recomendador de filmes
recomendador_filmes()
