# Exercícios do Livro "Entendendo Algoritmos" - Aditya Bhargava

## Capítulo 1: Introdução a Algoritmos

### Pesquisa Binária

A pesquisa binária é um algoritmo eficiente para encontrar um elemento em uma **lista ordenada**. Ela funciona dividindo repetidamente a lista pela metade até encontrar o elemento desejado.

**Características:**

- **Entrada:** Lista ordenada de elementos
- **Objetivo:** Eliminar metade da busca a cada tentativa
- **Complexidade:**
  - Pesquisa binária: O(log n)
  - Pesquisa simples: O(n)

**Lógica do algoritmo:**

1. Define-se os limites inferior (`baixo`) e superior (`alto`) da lista
2. Enquanto `baixo <= alto`:
   - Calcula o elemento do `meio` (arredondado para baixo)
   - Compara o elemento do meio com o valor buscado
   - Se for igual: retorna a posição
   - Se for maior: ajusta `alto = meio - 1`
   - Se for menor: ajusta `baixo = meio + 1`

**Implementação em Python:**

```python
def pesquisa_binaria(lista, item):
    baixo = 0
    alto = len(lista) - 1
    
    while baixo <= alto:
        meio = (baixo + alto) // 2
        chute = lista[meio]
        
        if chute == item:
            return meio
        if chute > item:
            alto = meio - 1
        else:
            baixo = meio + 1
    return None

# Exemplo de uso
minha_lista = [1, 3, 5, 7, 9]
print(pesquisa_binaria(minha_lista, 3))  # Retorna 1
print(pesquisa_binaria(minha_lista, -1)) # Retorna None
```

### **1.1)** Suponha que você tenha uma lista com 128 nomes e esteja fazendo uma pesquisa binária. Qual seria o número máximo de etapas que você levaria para encontrar o nome desejado ?

 A pesquisa binária precisa de log₂ n para retornar o valor buscado.
 Logo, seriam necessarios log₂ 128 operações, ou, máximo de 7 etapas para encontrar o nome desejado.

### **1.2)** Suponha que você duplique o tamanho da lista. Qual seria o número máximo de etapas agora ?

 Como "duplicar a lista" aumenta apenas uma única operação na pesquisa binária, o número de etapas agora será 8.
 Veja: 128 x 2 = 256; e log₂ 256 = 8.

### **1.3)** Você tem um nome e deseja encontrar o número de telefone para esse nome em uma agenda telefônica. Forneça o tempo de execução na notação Big O

 O(log n).

### **1.4)** Você tem um número de telefone e deseja encontrar o dono dele em uma agenda telefônica. (Dica: Deve procurar pela agenda inteira!)

 O(n).

### **1.5)** Você quer ler o número de cada pessoa da agenda telefônica

 O(n).

### **1.6)** Você quer ler os números apenas dos nomes que começam com *A*

 O(n).

### Notação Big O

A notação Big O descreve como o tempo de execução de um algoritmo cresce à medida que o tamanho da entrada aumenta.

**Tempos de execução comuns:**

- O(log n): Crescimento logarítmico (ex: pesquisa binária)
- O(n): Crescimento linear (ex: pesquisa simples)
- O(n log n): Crescimento linearítmico (ex: algoritmos de ordenação eficientes)
- O(n²): Crescimento quadrático (ex: algoritmos de ordenação lentos)
- O(n!): Crescimento fatorial (ex: problema do caixeiro viajante)

**Exercícios:**

1. Encontrar número telefônico pelo nome: O(log n)
2. Encontrar dono de número telefônico: O(n)
3. Ler todos os números da agenda: O(n)
4. Ler números de nomes com A: O(n) (necessário percorrer toda a lista no pior caso)

### O Problema do Caixeiro Viajante

Problema de otimização combinatorial que busca encontrar o caminho mais curto possível visitando múltiplas cidades exatamente uma vez e retornando à cidade de origem.

**Complexidade:** O(n!) - Crescimento fatorial que se torna computacionalmente inviável para grandes valores de n.
