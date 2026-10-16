# LeetCode 2 - Add Two Numbers
**Nome:** Otávio Lima Moraes

**Sobre o exercício:** O problema consiste em somar dois números inteiros não negativos representados por listas encadeadas. Cada nó da lista contém um único dígito, e os dígitos estão armazenados em ordem inversa. O objetivo é retornar uma nova lista encadeada contendo o resultado da soma, também em ordem inversa.

Por exemplo (3 testes que funcionam):

**t1:** `l1 = [2, 4, 3]` e `l2 = [5, 6, 4]`. O resultado é `[7, 0, 8]`, pois 342 + 465 = 807.

**t2:** `l1 = [0]` e `l2 = [0]`. O resultado é `[0]`, pois 0 + 0 = 0.

**t3:** `l1 = [9, 9, 9, 9, 9, 9, 9]` e `l2 = [9, 9, 9, 9]`. O resultado é `[8, 9, 9, 9, 0, 0, 0, 1]`, pois 9.999.999 + 9.999 = 10.009.998.

## Minha solução:

Minha ideia foi percorrer as duas listas ao mesmo tempo, somando os valores dos nós correspondentes. Para isso, utilizei um laço `while`, que continua enquanto ainda existir algum nó para processar em uma das listas ou enquanto houver um valor de transporte pendente.

Durante a soma, utilizei duas variáveis principais:

**soma:** guarda o resultado da soma dos dígitos atuais das duas listas, incluindo o transporte da operação anterior.

**carry:** guarda o valor que precisa ser transportado para a próxima soma, quando o resultado é maior ou igual a 10.

A lógica funciona de maneira semelhante a uma soma feita no papel. Por exemplo, quando somamos 4 + 6, obtemos 10. Nesse caso, armazenamos o dígito 0 no nó atual e guardamos o valor 1 em `carry`, para adicioná-lo à próxima soma.

Para construir a lista resultante, utilizei `malloc` para alocar memória para cada novo nó. Também utilizei dois ponteiros, `inicio` e `fim`: o primeiro mantém o endereço do início da lista, enquanto o segundo permite adicionar novos nós ao final sem precisar percorrer toda a lista novamente.

## Dificuldades encontradas:

Uma das partes mais importantes para entender esse problema foi trabalhar com ponteiros e listas encadeadas. Diferentemente de um vetor, em que podemos acessar os elementos por meio de índices, uma lista encadeada utiliza ponteiros para conectar cada nó ao próximo.

Também foi necessário compreender como avançar pelas duas listas sem acessar nós inexistentes, já que elas podem possuir tamanhos diferentes. Por isso, antes de acessar o valor de cada nó, verifico se o ponteiro correspondente é diferente de `NULL`.

Outro ponto importante foi perceber que o transporte precisa ser considerado mesmo quando uma das listas já terminou. Por esse motivo, o laço também verifica se `carry` é diferente de zero, garantindo que nenhum dígito seja perdido no resultado.

## Complexidade:

A solução percorre cada lista uma única vez, realizando uma quantidade constante de operações para cada posição processada.

Por isso, sua complexidade de tempo é **O(max(n, m))**, em que `n` e `m` representam os tamanhos das duas listas.

A complexidade de espaço auxiliar é **O(1)**, pois utilizamos uma quantidade constante de variáveis. Considerando também a memória necessária para construir a lista resultante, o espaço total utilizado é **O(max(n, m))**, pois o resultado pode possuir um dígito a mais devido ao transporte final.

## O que aprendi:

Com esse exercício, consegui compreender melhor como funcionam as listas encadeadas e como os ponteiros permitem percorrer e construir estruturas de dados dinamicamente.

Também aprendi a importância de controlar o transporte durante operações matemáticas e de verificar se ainda existem elementos para processar antes de acessar seus valores.

Além disso, pude perceber como a escolha da estrutura de dados influencia a maneira de resolver um problema. Nesse caso, como os números já estavam representados por listas encadeadas, foi possível realizar a soma diretamente sobre os nós, sem precisar converter as listas para números inteiros convencionais.
