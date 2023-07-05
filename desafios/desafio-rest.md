## Os testes:

Estes testes devem cobrir o básico para a construção de uma API REST dentro do wordpress,
  
### Desafio 01: Gerar e Classificar Números Aleatórios
  
Seu desafio é criar uma API REST dentro da arquitetura do wordpress com um endpoint `[GET] [...]/rankparity` que gere 50 números aleatórios e os classifique em dois conjuntos: números pares e números ímpares. Ao final, o programa deve exibir dois arrays, um contendo os números pares ordenados em ordem crescente e outro contendo os números ímpares ordenados em ordem decrescente.

Regras do Desafio:
  
    1. Gere 50 números aleatórios inteiros no intervalo de 1 a 200 (inclusive).
    2. Classifique os números em dois conjuntos: pares e ímpares.
    3. Ordene o conjunto de números pares em ordem crescente.
    4. Ordene o conjunto de números ímpares em ordem decrescente.
    5. Exiba os dois conjuntos ordenados em um objeto JSON.
      
Exemplo de Saída: 
```
{
  pairs: [2, 4, 6, 8, 10, …],
  odd: [99, 97, 93, 89, 87, ...]
}
```

Dicas:
    • Considere a utilização de algoritmos de classificação (como bubble sort, insertion sort, quicksort, mergesort, etc.) para ordenar os números.
    • Use estruturas de controle, como loops e condicionais, para separar os números pares e ímpares.
    • Certifique-se de testar (testes unitários) seu programa com diferentes números aleatórios para garantir que ele funcione corretamente.
      
Lembre-se de que este desafio visa testar sua habilidade em gerar números aleatórios, classificar dados em conjuntos diferentes e aplicar algoritmos de classificação para ordenar arrays. Boa sorte e divirta-se resolvendo o desafio!


---
---
---


### Desafio extra: Contando Operações "Leva 1" na Adição

Seu objetivo é criar um endpoint no formato `[POST] /carry` que retornará a quantidade de operações de "leva 1" necessárias ao somar dois números. 

A entrada para esse endpoint será composta por dois números inteiros positivos de até 9 dígitos cada, fornecidos no corpo da requisição (por exemplo: `{ "term1": 15, "term2": 15 }` ).
Ao receber a requisição, seu endpoint deverá calcular a quantidade de operações de "leva 1" necessárias para somar os dois números informados (por exemplo: `{carryOperations: 1}`). 
Em seguida, retorne a quantidade encontrada como resposta da requisição.

#### Exemplo de Requisição: 

Endpoint: `[POST] /carry `
```
{
  "term1":   23456789,
  "term2": 987654321
}
```

Exemplo de Resposta:
```
{
  "carryOperations": 8
}
```


Certifique-se de implementar o endpoint corretamente, recebendo os valores dos termos da adição no corpo da requisição e retornando a quantidade de operações de "leva 1" encontradas como resposta.
