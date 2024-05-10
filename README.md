# Implementação de Busca Binária em C++

## Objetivo
Este repositório tem como objetivo fornecer uma explicação e implementação prática de um algoritmo de busca binária em C++. A busca binária é um algoritmo eficiente para encontrar um elemento específico em um vetor ordenado.

## Conteúdo
- [Motivação](#motivação)
- [Explicação do Algoritmo](#explicação-do-algoritmo)
- [Complexidade do Algoritmo](#complexidade-do-algoritmo)
- [Implementação](#implementação)
- [Como Executar](#como-executar)
- [Referências](#referências)

## Motivação
A busca binária é uma técnica de busca que reduz drasticamente o número de comparações necessárias para encontrar um elemento, comparada à busca linear. Ela é especialmente útil para vetores ordenados, tornando-se uma ferramenta essencial para programadores que buscam eficiência.

## Explicação do Algoritmo
### Passos
1. **Inicialização**: Definimos os índices `ini` (início do vetor) e `fim` (fim do vetor).
2. **Cálculo do Meio**: Calculamos o índice do meio do vetor (`mid = ini + (fim - ini) / 2`).
3. **Comparação**:
   - Se `lista[mid]` for igual ao `alvo`, retornamos `mid`.
   - Se `lista[mid]` for menor que `alvo`, atualizamos `ini` para `mid + 1` (descartando a metade inferior).
   - Se `lista[mid]` for maior que `alvo`, atualizamos `fim` para `mid - 1` (descartando a metade superior).
4. **Repetição**: Repetimos os passos até encontrar o elemento ou `ini` ser maior que `fim`.

### Fluxograma do Processo
```mermaid
graph TD
    A[Inicialização] --> B{ini <= fim?}
    B -- Sim --> C[Calcula mid]
    C --> D{lista[mid] == alvo?}
    D -- Sim --> E[Retorna mid]
    D -- Não --> F{lista[mid] < alvo?}
    F -- Sim --> G[ini = mid + 1]
    F -- Não --> H[fim = mid - 1]
    G --> B
    H --> B
    B -- Não --> I[Retorna -1]
```

## Complexidade do Algoritmo
Tempo:

- Melhor caso: O(1) (quando o elemento é encontrado no meio)
- Pior caso: O(log n) (dividindo o vetor a cada iteração)
- Caso médio: O(log n)
Espaço:

- O(1) (uso de variáveis auxiliares)

### Implementação em C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int search(vector<int> lista, int alvo) {
    int ini = 0;
    int fim = lista.size() - 1;

    while (ini <= fim) {
        int mid = ini + (fim - ini) / 2;
        if (alvo == lista[mid]) {
            return mid;
        }
        if (alvo > lista[mid]) {
            ini = mid + 1;
        } else {
            fim = mid - 1;
        }
    }
    return -1;
}

int main() {
    vector<int> lista = {1, 2, 3, 4, 5, 6, 7, 8};
    int alvo = 5;

    int indice = search(lista, alvo);

    if (indice == -1) {
        cout << "N" << endl;
    } else {
        cout << indice << endl;
    }
    return 0;
}
```
