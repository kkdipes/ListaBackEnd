# Exercício 07: Controladores Web

## Objetivo

Utilizando o framework Spring Web, implemente um controlador que receba uma entrada por query strings e retorne uma resposta. Utilize um dos exercícios propostos anteriores como base.

> Exemplo: Um controlador que recebe duas query strings com genero e ambientação e retorna uma sugestão de filme (como no [exercício 01](./exercicio01.md)).

## Instruções

* Crie um novo projeto Spring Boot usando o Spring Initializr.
* Defina uma classe de controlador com a anotação `@RestController`.
* Crie um método que receba uma entrada por query strings e retorne uma resposta.


## Entradas (inputs)

````txt
http://localhost:8080/recomendar?genero=acao&ambiente=futurista
``

## Saídas (outputs)

````txt
Homens de Preto
````

## RESOLUÇÃO

package com.exemplo.recomendacao;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class FilmeController {

    @GetMapping("/recomendar")
    public String recomendarFilme(
            @RequestParam String genero,
            @RequestParam String ambiente) {
        
        if ("acao".equalsIgnoreCase(genero) && "futurista".equalsIgnoreCase(ambiente)) {
            return "Homens de Preto";
        }
        // Adicione outras combinações de gênero e ambiente conforme necessário
        return "Nenhuma recomendação disponível";
    }
}

./mvnw spring-boot:run

http://localhost:8080/recomendar?genero=acao&ambiente=futurista

Homens de Preto

@GetMapping("/recomendar")
public String recomendarFilme(
        @RequestParam String genero,
        @RequestParam String ambiente) {
    
    if ("acao".equalsIgnoreCase(genero) && "futurista".equalsIgnoreCase(ambiente)) {
        return "Homens de Preto";
    } else if ("acao".equalsIgnoreCase(genero) && "histórico".equalsIgnoreCase(ambiente)) {
        return "Gladiador";
    } else if ("comedia".equalsIgnoreCase(genero) && "moderno".equalsIgnoreCase(ambiente)) {
        return "A Morte lhe Cai Bem";
    }
    return "Nenhuma recomendação disponível";
}


