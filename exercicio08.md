### Exercício 08: Tabela FIPE

Objetivo
Utilizando o framework Spring Web, implemente um controlador e um método que receba um objeto JSON no corpo da requisição contendo uma marca, modelo e ano de um carro e retorne o valor de tabela FIPE para esse carro. Utilize esta API como referência: https://deividfortuna.github.io/fipe/

Instruções

Crie um novo projeto Spring Boot usando o Spring Initializr.
Defina uma classe de controlador com a anotação @RestController.
Crie um método que receba um objeto JSON no corpo da requisição contendo uma marca, modelo e ano de um carro e retorne o valor de tabela FIPE para esse carro.
Use o RestClient para fazer a requisição à API da Tabela FIPE.


### Entradas (inputs)

{
  "marca": "Fiat",
  "modelo": "Uno",
  "ano": 2023
}



Saídas (outputs)

{
  "valor": 50000.0
  "mes": "Setembro de 2024"
}


## RESOLUÇÃO ##


    
