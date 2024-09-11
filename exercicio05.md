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

### RESOLUÇÃO ###

from abc import ABC, abstractmethod

# Interface PlataformaSocial
class PlataformaSocial(ABC):
    @abstractmethod
    def compartilharPostagem(self, postagem):
        pass

    @abstractmethod
    def compartilharImagem(self, postagem):
        pass

    @abstractmethod
    def compartilharVideo(self, postagem):
        pass

# Classe MyBook
class MyBook(PlataformaSocial):
    def compartilharPostagem(self, postagem):
        print(f"Você compartilhou a postagem '{postagem.titulo}' no MyBook.")

    def compartilharImagem(self, postagem):
        print(f"Você compartilhou a imagem '{postagem.titulo}' no MyBook.")

    def compartilharVideo(self, postagem):
        print(f"Você compartilhou o vídeo '{postagem.titulo}' no MyBook.")

# Classe Fotogram
class Fotogram(PlataformaSocial):
    def compartilharPostagem(self, postagem):
        raise Exception("O Fotogram não suporta o compartilhamento de postagens de texto.")

    def compartilharImagem(self, postagem):
        print(f"Você compartilhou a imagem '{postagem.titulo}' no Fotogram.")

    def compartilharVideo(self, postagem):
        print(f"Você compartilhou o vídeo '{postagem.titulo}' no Fotogram.")

# Classe AnyTube
class AnyTube(PlataformaSocial):
    def compartilharPostagem(self, postagem):
        print(f"Você compartilhou a postagem '{postagem.titulo}' no AnyTube.")

    def compartilharImagem(self, postagem):
        raise Exception("O AnyTube não suporta o compartilhamento de imagens.")

    def compartilharVideo(self, postagem):
        print(f"Você compartilhou o vídeo '{postagem.titulo}' no AnyTube.")

# Classe Postagem
class Postagem:
    def __init__(self, titulo, descricao, tipo):
        self.titulo = titulo
        self.descricao = descricao
        self.tipo = tipo

# Classe Main para testar o programa
def main():
    titulo = input("Digite o título da postagem: ")
    descricao = input("Digite a descrição da postagem: ")
    tipo = input("Digite o tipo da postagem (texto, imagem, video): ")

    postagem = Postagem(titulo, descricao, tipo)

    mybook = MyBook()
    fotogram = Fotogram()
    anytube = AnyTube()

    try:
        if tipo == "texto":
            mybook.compartilharPostagem(postagem)
            fotogram.compartilharPostagem(postagem)
            anytube.compartilharPostagem(postagem)
        elif tipo == "imagem":
            mybook.compartilharImagem(postagem)
            fotogram.compartilharImagem(postagem)
            anytube.compartilharImagem(postagem)
        elif tipo == "video":
            mybook.compartilharVideo(postagem)
            fotogram.compartilharVideo(postagem)
            anytube.compartilharVideo(postagem)
        else:
            print("Tipo de postagem inválido.")
    except Exception as e:
        print(f"Ocorreu um erro ao compartilhar essa postagem: {e}")

# Executa a função principal
main()
