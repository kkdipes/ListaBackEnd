# Exercício 05: Compartilhar Postagem

## Objetivo

Crie um programa, utilizando Interfaces, para implementar o compartilhamento em diferentes plataformas de mídia social.

## Instruções

* Crie uma interface chamada `PlataformaSocial` com os métodos `compartilharPostagem()`, `compartilharImagem()`, `compartilharVideo()`.
* Crie uma classe chamada `MyBook` que implementa a interface `PlataformaSocial`.
* Crie uma classe chamada `Fotogram` que implementa a interface `PlataformaSocial`.
* Crie uma classe chamada `AnyTube` que implementa a interface `PlataformaSocial`.
* Crie uma classe chamada `Postagem` que recebe um `titulo`, `descricao` e `tipo` (`texto, imagem, video`).
* O Fotogram deve gerar uma exceção no método `compartilharPostagem`
* O AnyTube deve gerar uma exceção no método `compartilharImagem`
* O MyBook não gera nenhuma exceção e deve imprimir todos os métodos;
* Crie uma classe chamada `Main` para testar o programa.
  * 1. Crie uma instância da classe `Postagem` e peça ao usuário para inserir o título, descrição e tipo da postagem.
  * 2. Crie uma instância da classe `MyBook` e chame o método `compartilharPostagem` passando a instância da classe `Postagem` como parâmetro.
  * 3. Crie uma instância da classe `Fotogram` e chame o método `compartilharImagem` passando a instância da classe `Postagem` como parâmetro.
  * 4. Crie uma instância da classe `AnyTube` e chame o método `compartilharVideo` passando a instância da classe `Postagem` como parâmetro.

## Entradas (inputs)

````txt
Titulo: Minha primeira postagem
Descrição: Esta é uma descrição da minha primeira postagem.
Tipo: imagem
````

## Saídas (outputs)

````txt
Você compartilhou essa postagem no MyBook.
Você compartilhou essa postagem no Fotogram.
Ocorreu um erro ao compartilhar essa postagem no AnyTube.
````