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