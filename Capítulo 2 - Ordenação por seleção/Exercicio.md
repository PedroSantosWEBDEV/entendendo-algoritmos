# Exercícios do Livro "Entendendo Algoritmos" - Aditya Bhargava

## Capítulo 2: Ordenação por Seleção

### Ordenação por Seleção

A ordenação por seleção é um algoritmo de ordenação que divide a lista em duas partes: uma parte ordenada e uma parte não ordenada. A cada passo, o algoritmo encontra o menor elemento da parte não ordenada e o move para o final da parte ordenada.

**Características:**

- **Entrada:** Lista de elementos comparáveis
- **Objetivo:** Ordenar a lista em ordem crescente
- **Complexidade:**
  - Ordenação por seleção: O(n²)
  - Ordenação eficiente (ex: quicksort): O(n log n)

**Lógica do algoritmo:**

1. Inicialmente, a parte ordenada está vazia e a não ordenada é toda a lista
2. Para cada posição i de 0 a n-1:
   - Encontre o menor elemento na parte não ordenada (de i a n-1)
   - Troque o menor elemento com o elemento na posição i
   - Aumente a parte ordenada em um elemento

**Implementação em Python:**

```python
def ordenacao_selecao(lista):
    n = len(lista)
    for i in range(n):
        indice_minimo = i
        for j in range(i+1, n):
            if lista[j] < lista[indice_minimo]:
                indice_minimo = j
        lista[i], lista[indice_minimo] = lista[indice_minimo], lista[i]
    return lista

# Exemplo de uso
minha_lista = [64, 25, 12, 22, 11]
print(ordenacao_selecao(minha_lista))  # Retorna [11, 12, 22, 25, 64]
```

### **2.1)** Suponha que você esteja criando um aplicativo para acompanhar as suas finanças. Todos os dias você anotará tudo o que gastou e onde gastou. No final do mês, você deverá revisar os seus gastos e resumir o quanto gastou. Logo, você terá um monte de inserções e poucas leituras. Você deverá usar um array ou uma lista para implementar este aplicativo?

**Resposta:** Uma lista (lista encadeada) será melhor que um array. Visto que as listas são mais flexíveis para inserções, permitindo adicionar elementos em tempo constante (O(1)) no final, enquanto arrays podem requerer redimensionamento, tornando algumas inserções O(n).

### **2.2)** Suponha que você esteja criando um aplicativo para anotar os pedidos dos clientes em um restaurante. Seu aplicativo precisa de uma lista de pedidos. Os garçons adicionam os pedidos a essa lista e os chefes retiram os pedidos da lista. Funciona como uma fila. Os garçons colocam os pedidos no final da fila e os chefes retiram os pedidos do começo dela para cozinhá-los. Você usaria um array ou uma lista encadeada para implementar essa lista?

**Resposta:** Uma lista encadeada. Tendo em vista que não sei a quantidade de pedidos simultâneos na lista e que as listas são boas para inserção e deleção em qualquer posição. Em uma lista encadeada, as operações de enfileiramento (inserção no final) e desenfileiramento (remoção no início) podem ser feitas em O(1) se tivermos ponteiros para o início e o final. Já em um array, a remoção no início requer deslocamento de todos os elementos, sendo O(n).

### **2.3)** Vamos analisar um experimento. Imagine que o Facebook guarda uma lista de usuários. Quando alguém tenta acessar o Facebook, uma busca é feita pelo nome de usuário. Se o nome da pessoa está na lista, ela pode continuar o acesso. As pessoas acessam o Facebook com muita frequência, então existem muitas buscas nessa lista. Presuma que o Facebook usa a pesquisa binária para procurar um nome na lista. A pesquisa binária requer acesso aleatório - você precisa ser capaz de acessar o meio da lista de nomes instantaneamente. Sabendo disso, você implementaria essa lista como um array ou uma lista encadeada?

**Resposta:** Um array. Tendo em vista que com uma lista encadeada não seria possível acessar qualquer posição instantaneamente, pois requer percorrer os elementos até a posição desejada. A pesquisa binária requer acesso aleatório em O(1) para qualquer índice, o que é fornecido por arrays, mas não por listas encadeadas.

### **2.4)** As pessoas se inscrevem no Facebook com muita frequência também. Suponha que você decida usar um array para armazenar a lista de usuários. Quais as desvantagens de um array em relação às inserções? Em particular, imagine que você está usando a pesquisa binária para buscar os logins. O que acontece quando você adiciona novos usuários em um array?

**Resposta:** Inserções em arrays dependem de memória previamente alocada. No caso citado, como é usada uma pesquisa binária, a lista deve estar ordenada. Para inserir um novo usuário, é necessário encontrar a posição correta (o que pode ser feito em O(log n) com busca binária), mas inserir naquela posição requer deslocar todos os elementos à direita para abrir espaço, o que leva O(n). Além disso, se o array estiver cheio, será necessário redimensioná-lo, o que também é uma operação custosa.

### **2.5)** Na verdade, o Facebook não usa nem array nem listas encadeadas para armazenar informações. Vamos considerar uma estrutura de dados híbrida: um array de listas encadeadas. Você tem um array com 26 slots. Cada slot aponta para uma lista encadeada. Por exemplo, o primeiro slot aponta para uma lista que possui os nomes que começam com *A*, o segundo para uma lista com nomes que começam com *B*, e assim por diante. Suponha que o **Adit B** se inscreva no Facebook e você queira adicioná-lo à lista. Você vai do slot 1 do array, a seguir para a lista encadeada do slot 1, e adiciona **Adit B** no final. Agora, suponha que você queira procurar o **Zakhir H**. Você vai ao slot 26. Então, procura pela lista até encontrar o **Zakhir H**. Compare esta estrutura híbrida com arrays e listas encadeadas. É mais lento ou mais rápido fazer inserções e eliminações nesse caso?

**Resposta:**

- **Inserções:** A estrutura híbrida é mais rápida que um array (que leva O(n) para inserir) e tão rápida quanto uma lista encadeada (O(1) para inserção no final, assumindo que temos o ponteiro para o final).
- **Buscas:** A estrutura híbrida é mais lenta que um array (que permite busca binária em O(log n)) mas mais rápida que uma lista encadeada (que requer busca linear em O(n)). No híbrido, a busca é O(k/26) em média, onde k é o número de elementos na lista da letra, o que é melhor que O(n) da lista encadeada, mas pior que O(log n) do array.

Portanto, a estrutura híbrida oferece um equilíbrio: inserções rápidas (como listas encadeadas) e buscas mais rápidas que listas encadeadas (mas mais lentas que arrays).
