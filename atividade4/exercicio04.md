# Exercício 04: Buscador de Músicas


## Objetivo

Crie um programa, utilizando Collections e Exceptions, que seja capaz de armazenar uma lista de músicas e permita o usuário criar playlists.

## Instruções

* Crie uma classe chamada `Musica` com os atributos `titulo` e `artista`.
* Crie uma classe chamada `Playlist` com os atributos `nome` e `musicas`.
* Crie uma classe chamada `MusicCloud` com os atributos `musicasDisponiveis`.
  * 1. Insira diferentes nomes de músicas na lista `musicasDisponiveis`.
  * 2. Crie um método para pesquisar as músicas disponíveis.
* Crie uma classe chamada `Main` para testar o programa.
  * 1. Peça ao usuário para inserir o nome da playlist.
  * 2. Peça ao usuário para inserir o nome da música.
  * 3. Se a música existir, adicione na playlist
  * 4. Se a música não existir, retorne uma mensagem de erro
  * 5. Repita os passos 2 ao 4 até que o usuário decida parar.
  * 6. Imprima a playlist.

## Entradas (inputs)

````txt
Digite o nome da música:
Hino do Real Paulista
````

## Saídas (outputs)

````txt
Você adicionou a música Hino do Real Paulista na playlist.
Você adicionou a música Macarena na playlist.
Você adicionou a música Evidências na playlist.
A música Hino do Real Paulista não foi encontrada no sistema.

Playlist:
- Hino do Real Paulista
- Macarena
- Evidências
````

###  RESOLUÇÃO ###

class Musica:
    def __init__(self, titulo, artista):
        self.titulo = titulo
        self.artista = artista

    def __str__(self):
        return f"{self.titulo} - {self.artista}"

class Playlist:
    def __init__(self, nome):
        self.nome = nome
        self.musicas = []

    def adicionar_musica(self, musica):
        self.musicas.append(musica)
        print(f"Você adicionou a música {musica.titulo} na playlist.")

    def mostrar_playlist(self):
        print(f"\nPlaylist: {self.nome}")
        for musica in self.musicas:
            print(f"- {musica.titulo}")

class MusicCloud:
    def __init__(self):
        self.musicasDisponiveis = [
            Musica("Hino do Real Paulista", "Artista Desconhecido"),
            Musica("Macarena", "Los Del Rio"),
            Musica("Evidências", "Chitãozinho & Xororó"),
            Musica("Thriller", "Michael Jackson"),
            Musica("Bohemian Rhapsody", "Queen")
        ]

    def pesquisar_musica(self, titulo):
        for musica in self.musicasDisponiveis:
            if musica.titulo.lower() == titulo.lower():
                return musica
        return None

def main():
    music_cloud = MusicCloud()
    
    playlist_nome = input("Digite o nome da playlist: ")
    playlist = Playlist(playlist_nome)
    
    while True:
        titulo_musica = input("\nDigite o nome da música (ou 'sair' para finalizar): ")
        if titulo_musica.lower() == 'sair':
            break
        
        musica_encontrada = music_cloud.pesquisar_musica(titulo_musica)
        if musica_encontrada:
            playlist.adicionar_musica(musica_encontrada)
        else:
            print(f"A música {titulo_musica} não foi encontrada no sistema.")
    
    playlist.mostrar_playlist()

# Executa a função principal
main()
