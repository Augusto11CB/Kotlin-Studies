# Exercícios

## Exercício - Palíndromo
Criar uma função que verifica se uma palavra é palíndromo
```
fun String.isPalindrome()=

```

## Exercício - Acrônimo
Converter uma frase em seu acrônimo.

Converta um nome longo como Portable Network Graphics em seu acrônimo (PNG).

Ex: Federal Bureau of Investigation => FBI

## Exercício - Valor de Palavras
Dada uma palavra, calcule o valor de cala palavra levado em conta a tabela de valor de letras do alfabeto abaixo

### Tabela Valor das Letras
```
Letras                           Valor
A, E, I, O, U, L, N, R, S, T       1
D, G                               2
B, C, M, P                         3
F, H, V, W, Y                      4
K                                  5
J, X                               8
Q, Z                               10
```

Carro -> C=3, a=1, r=1, r=1, o=1
3 + 1 + 1 + 1 + 1 = 7

## Exercício - Pangrama
Determine se uma frase é um pangrama. Um pangrama (em grego: παν γράμμα, pan gramma, "cada letra") é uma frase que usa cada letra do alfabeto pelo menos uma vez. O pangrama inglês mais conhecido é:

`The quick brown fox jumps over the lazy dog.`

O alfabeto usado consiste em letras ASCII de a a z, inclusive, e não diferencia maiúsculas de minúsculas. A entrada não conterá símbolos não ASCII.

### Outros exemplos de Pangram

- Two driven jocks help fax my big quiz.
- The jay, pig, fox, zebra and my wolves quack!
- Watch "Jeopardy!", Alex Trebek's fun TV quiz game.
- The five boxing wizards jump quickly.

### Exercício - Mutações Genéticas
Calcule a diferença no [código de Hamming](https://pt.wikipedia.org/wiki/C%C3%B3digo_de_Hamming) entre duas fitas de DNA.

Uma mutação é simplesmente um erro que ocorre durante a criação ou cópia de um ácido nucleico, em particular o DNA. Como os ácidos nucleicos são vitais para as funções celulares, as mutações tendem a causar um efeito cascata em toda a célula. Embora as mutações sejam tecnicamente erros, uma mutação muito rara pode equipar a célula com um atributo benéfico. De fato, os macroefeitos da evolução são atribuíveis ao resultado acumulado de mutações microscópicas benéficas ao longo de muitas gerações.

O tipo mais simples e comum de mutação de ácido nucleico é uma mutação pontual, que substitui uma base por outra em um único nucleotídeo.

Ao contar o número de diferenças entre duas fitas de DNA homólogas retiradas de genomas diferentes com um ancestral comum, obtemos uma medida do número mínimo de mutações pontuais que poderiam ter ocorrido no caminho evolutivo entre as duas fitas.

Isso é chamado de 'distância de Hamming'.

Ele é encontrado comparando duas fitas de DNA e contando quantos dos nucleotídeos são diferentes de seu equivalente na outra seqüência.

```
GAGCCTACTAACGGGAT
CATCGTAATGACGGCCT
^ ^ ^  ^ ^    ^^
```

- **A distância de Hamming entre essas duas fitas de DNA é 7.**

## Exercício - Números Perfeitos

Determine se um número é perfeito, abundante ou deficiente com base no esquema de classificação de Nicômaco (60 - 120 CE) para números naturais.

O matemático grego Nicômaco elaborou um esquema de classificação para os números naturais, identificando cada um como pertencente exclusivamente às categorias de perfeito, abundante ou deficiente com base em sua soma alíquota. A soma alíquota é definida como a soma de todos os divisores de um número sem incluir o próprio número. Por exemplo, a soma alíquota de 15 é (1 + 3 + 5) = 9

- Perfeito: soma alíquota = número
    - 6 é um número perfeito porque (1 + 2 + 3) = 6
    - 28 é um número perfeito porque (1 + 2 + 4 + 7 + 14) = 28
- Abundante: soma alíquota > número
    - 12 é um número abundante porque (1 + 2 + 3 + 4 + 6) = 16
    - 24 é um número abundante porque (1 + 2 + 3 + 4 + 6 + 8 + 12) = 36
- Deficiente: soma alíquota < número
    - 8 é um número deficiente porque (1 + 2 + 4) = 7
    - Os números primos são deficientes

Implemente uma maneira de determinar se um determinado número é **perfeito**. Dependendo da sua faixa de idioma, você também pode precisar implementar uma maneira de determinar se um determinado número é **abundante** ou **deficiente**.

## Exercício - RNA
Dada uma fita de DNA, retorne seu complemento de RNA (por transcrição de RNA).

As fitas de DNA e RNA são uma sequência de nucleotídeos.

Os quatro nucleotídeos encontrados no DNA são adenina (A), citosina (C), guanina (G) e timina (T).

Os quatro nucleotídeos encontrados no RNA são adenina (A), citosina (C), guanina (G) e uracila (U).

Dada uma fita de DNA, sua fita de RNA transcrita é formada pela substituição de cada nucleotídeo por seu complemento:

```
G -> C
C -> G
T -> A
A -> U
```

![](./resources/dna-to-rna.png)