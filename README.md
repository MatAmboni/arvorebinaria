# Árvore binária de busca

Implementação em C++ de uma **árvore binária de busca (BST)** e de uma **lista simplesmente encadeada**, com interface abstrata, tipos genéricos e testes automatizados.

O projeto cobre inserção, busca, remoção (folha, um filho e dois filhos) e os três percursos clássicos. A lista encadeada é a estrutura usada para devolver as chaves visitadas.

## O que o código demonstra

- Estruturas de dados recursivas e ponteiros em C++
- Classes abstratas e implementação concreta (`ArvoreDeBuscaBinaria` / `MinhaArvoreDeBuscaBinaria`, `ListaEncadeadaAbstrata` / `MinhaListaEncadeada`)
- Templates (`template <typename T>`)
- `std::optional` para consultas que podem não ter resultado
- Liberação de memória nos destrutores
- Testes com Google Test

## Exemplo

Inserindo `5, 3, 7, 2, 4, 6, 9`:

```text
        5
       / \
      3   7
     / \ / \
    2  4 6  9
```

| Percurso   | Ordem das chaves        |
|------------|-------------------------|
| Pré-ordem  | 5, 3, 2, 4, 7, 6, 9     |
| Em ordem   | 2, 3, 4, 5, 6, 7, 9     |
| Pós-ordem  | 2, 4, 3, 6, 9, 7, 5     |

A altura de um nó é a maior distância até uma folha da subárvore. A raiz fica com altura 2; as folhas, com altura 0.

## Operações

**Árvore**

| Método | Comportamento |
|--------|----------------|
| `vazia` / `quantidade` | Estado da árvore |
| `contem` | Busca pela chave |
| `inserir` | Insere mantendo a propriedade de busca (menor à esquerda, maior à direita) |
| `remover` | Remove folha, nó com um filho ou nó com dois filhos (substitui pelo menor da subárvore direita) |
| `altura` | Altura da subárvore enraizada na chave, ou `std::nullopt` se a chave não existe |
| `filhoEsquerdaDe` / `filhoDireitaDe` | Chave do filho, ou `std::nullopt` |
| `preOrdem` / `emOrdem` / `posOrdem` | Percurso devolvido em uma lista encadeada |

**Lista**

Inserção e remoção no início, no fim e em uma posição; busca por valor; exceções quando a lista está vazia ou a posição é inválida.

## Estrutura

```text
ArvoreDeBuscaBinaria.hpp        interface da árvore e struct Nodo
MinhaArvoreDeBuscaBinaria.hpp   implementação da BST
ListaEncadeadaAbstrata.hpp      interface da lista e exceções
MinhaListaEncadeada.hpp         implementação da lista
main.cpp                        suíte de testes (Google Test)
```

Os testes cobrem árvore vazia, os três percursos, a forma da árvore após a inserção e a remoção de folha, de raiz, de nó interno e de chave ausente.

## Como executar

Requer um compilador com C++17 e a biblioteca [Google Test](https://github.com/google/googletest).

```bash
g++ -std=c++17 -Wall -Wextra main.cpp -lgtest -pthread -o arvore
./arvore
```

No Windows, com MinGW e o Google Test no caminho do compilador:

```bash
g++ -std=c++17 -Wall -Wextra main.cpp -lgtest -o arvore.exe
arvore.exe
```

## Stack

C++17 · templates · Google Test
