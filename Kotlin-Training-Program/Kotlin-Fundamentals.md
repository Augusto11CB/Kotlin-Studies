# Kotlin Fundamentals -  PagSeguro Training Program

## Useful Links 
- https://play.kotlinlang.org/
- https://kotlinlang.org/

## Kotlin
- Home page is https://kotlinlang.org
- JetBrains criou e mantém a linguagem
- Oficialmente endossado pelo Google como uma linguagem de desenvolvimento Android
- Fornece `null safety` no nível do compilador
- **Estaticamente tipado**  por padrão
    - Significa que o tipo de cada expressão em um programa é conhecido em tempo de compilação
    - O compilador valida se os métodos e campos que você está tentando acessar existem nos objetos que você está usando.
    - TODO - Adicionar Link para "Vantagens de Linguagens Estaticamente Tipadas"
- Executa na JVM `-->` Interoperabilidade com Java

## Instalando e Rodando Kotlin
### SDKMAN
- `sdk install kotlin`

### Rodando Kotlin
1. Crie um aplicativo simples em Kotlin que exiba "Hello, World!". Em seu editor favorito, crie um novo arquivo chamado `hello.kt` com as seguintes linhas:

```kt
fun main() {
    println("Hello, World!")
}
```

2. Compile a aplicação usando o comando: `$ kotlinc hello.kt -include-runtime -d hello.jar`

A opção `-d` indica o caminho de saída para arquivos de classe gerados, que podem ser um diretório ou um arquivo .jar. A opção `-include-runtime` torna o arquivo .jar resultante independente e executável, incluindo Kotlin runtime library.

3. Rodando a aplicação: `java -jar hello.jar`


Para mais informações conferir: [Kotlin command-line compiler](https://kotlinlang.org/docs/command-line.html#install-the-compiler)

## Kotlin Basics
### Functions e Variables
#### Variables
- Declarando uma variavel: `val s: String`
- `val` vs `var`
    - `var` é uma variavel (mutable)
        - O valor de variáveis declaradas com `var` pode ser alterado.
    - `val` é um valor (immutable)
        - `val` não pode ser reatribuído depois de inicializado
    - Por padrão, você deve se esforçar para declarar todas as variáveis em Kotlin com a palavra-chave val.
    - **[WARNING!!]** Embora variaveis declaradas com `var`  permitam que seu valor seja alterado, seu tipo é fixo.
        - O exemplo abaixo **não irá compilar**
            ```kt
            var answer = 42
            answer = "no answer"
            ```

- Variáveis em kotlin são **non-null** por padrão
- Para declarar uma variavel que pode assumir `null` é decessário declara-lá como nullable utilizando `?`
    - Ex: `val name: String?`

- **The `!!` operator**
    - O operador de asserção não nulo (`!!`) converte qualquer valor em um tipo não nulo e **lança uma exceção se o valor for nulo**. Você pode escrever b!!, e isso retornará um valor não nulo de b (por exemplo, uma String em nosso exemplo) ou lançará um NPE se b for nulo:
    ```
    val l = b!!.length
    ```

#### Functions

```kt
fun main(args: Array<String>) {
    println("Hello, world!")
}
```

- `fun` keyword é usada para declarar uma função
- tipo de parâmetro é escrito após seu nome (ex: `args: Array<String>`)

```kt
fun max(a: Int, b: Int): Int {
    return if (a > b) a else b
}
```
- A declaração da função começa com a keyword `fun`, seguida pelo nome da função (no caso do exemplo é `max`). Depois, é seguido pela lista de parâmetros entre parênteses. O **tipo de retorno** vem após a lista de parâmetros, separado dela por dois pontos (`:`).


- Default parameter Values
    - Em Kotlin, você pode especificar valores padrão para parâmetros em uma declaração de função.
        ```
        TODO Pegar exemplo
        ```

#### Verificando Tipos 

TODO

```kt
val age: Int = 25
printnl("Is age String?{age is String}")
```

### Expressions - `if else` 

```kt
fun max(a: Int, b: Int): Int = if (a > b) a else b
```

```kt
fun max(a: Int, b: Int): Int {

    if(a > b) {
        return a
    } else {
        return b
    }

} 
```

#### Elvis Operator
- Quando você tem uma referência anulável, b, você pode dizer "se b não for nulo, use-o, caso contrário, use algum valor não nulo":
    ```kt
    val l: Int = if (b != null) b.length else -1
    ```
- Uma alternativa ao `if else` para verificar `null` é a utilização do **Elvis Operator** 
    ```kt
    val l = b?.length ?: -1
    ```
    - se a expressão à esquerda de `?:` não for nula, o operador Elvis a devolve, caso contrário devolve a expressão à direita.

## Enums e `when`
https://kotlinlang.org/docs/control-flow.html#when-expression
https://www.geeksforgeeks.org/enum-classes-in-kotlin/?ref=lbp

## Loops - `while` e `for`
TODO
https://kotlinlang.org/docs/control-flow.html#while-loops
https://kotlinlang.org/docs/control-flow.html#for-loops

## Pacotes (*Packages*)
- Usados pacotes para agrupar classes relacionadas
- Pacotes são declarados com a palavra-chave package
- https://kotlinlang.org/docs/packages.html

![](./resources/project-structure-packages.png)
![](./resources/package-structure.png)

## Classes, Objects, Interface e Properties

### Classes
As classes em Kotlin são declaradas usando a keyword `class`:

```kt
class Person { /*...*/ }
```

#### Construtor 
Uma classe em Kotlin pode ter um construtor primário e um ou mais construtores secundários.

- **Primary Constructor**
    - O construtor primário não pode conter nenhum código.
        ```kt
        class Person(firstName: String) { /*...*/ }

        class Person(val firstName: String, val lastName: String, var age: Int)
        ```

- **Exercício: Ler sobre o bloco `init` ([Init Blocks Kotlin Constructors](https://kotlinlang.org/docs/classes.html#constructors))**


- **Secondary Constructor**
    - Uma classe também pode declarar construtores secundários, que são prefixados com `construtor`
    - Construtores secundários permitem a inicialização de variáveis e também fornecem alguma lógica para a classe
        ```kt
        class Pet {
            constructor(owner: Person) {
                owner.pets.add(this) 
            }
        }

        class Add {
            constructor(a: Int, b:Int) {
                var c = a + b
                println("The sum of numbers 5 and 6 is: ${c}")
            }
        }
        ```
- **Exercício: Ler sobre algumas formas de se utilizar `Secondary Constructor` ([Init Blocks Kotlin Constructors](https://www.geeksforgeeks.org/kotlin-constructor/?ref=lbp))**

#### Criando instâncias de classes
```kt
val invoice = Invoice()

val customer = Customer("Joe Smith")
```

### Companion objects
TODO

### Herança
TODO
https://www.geeksforgeeks.org/kotlin-inheritance/?ref=lbp

### Interface

- Declarando uma interface:
    ```kt
    interface Clickable {
        fun click()
    }
    ```

- Implementando uma interface
    ```kt
    class Button : Clickable {
        override fun click() = println("I was clicked")
    }
    ```

### Open, final, e abstract modifiers


**Estudo recomendado:** Ler o Cap 4. Classes, objects, and interfaces de JEMEROV, Dmitry and ISAKAVA, Svetlana. Kotlin in Action, 2017

## Exceptions
- Uma função pode ser concluída de maneira normal ou lançar uma exceção se ocorrer um erro. O chamador da função pode capturar essa exceção e processá-la.

```kt
if (percentage !in 0..100) {
    throw IllegalArgumentException(
        "A percentage value must be between 0 and 100: $percentage")
}
```

### `try`, `catch` e `finally`
TODO

#### `finally`
- **Exercício: Busquem na internet os casos de uso do block `finally`**


## Collections and Arrays
```
val set = hashSetOf(1, 7, 53)
val list = arrayListOf(1, 7, 53)
val map = hashMapOf(1 to "one", 7 to "seven", 53 to "fifty-three")
```

- **Exercício: Qual a diferença entre as estruturas set, list e map em Kotlin?**


## Data classes
TODO

## Exercises

1. Criar uma função que verifica se uma palavra é palíndromo
```
fun String.isPalindrome()=

```


2. Converter uma frase em seu acrônimo.

Converta um nome longo como Portable Network Graphics em seu acrônimo (PNG).

Ex: Federal Bureau of Investigation => FBI

## Vantagens de Linguagens Estaticamente Tipadas
A seguir estão alguns dos benefícios da tipagem estática:

- Desempenho— Chamar métodos é mais rápido porque não há necessidade de descobrir em tempo de execução qual método precisa ser chamado.
- Confiabilidade— O compilador verifica a exatidão do programa, portanto, há menos chances de travamentos em tempo de execução.
- Manutenibilidade— Trabalhar com código desconhecido é mais fácil porque você pode ver com que tipo de objetos o código está trabalhando.
- Suporte a ferramentas— A tipagem estática permite refatorações confiáveis, preenchimento de código preciso e outros recursos do IDE.

## Conceitos de Programação Funcional
- First-class functions— Você trabalha com funções (partes de comportamento) como valores. Você pode armazená-los em variáveis, passá-los como parâmetros ou retorná-los de outras funções.
- Immutability— Você trabalha com objetos imutáveis, o que garante que seu estado não possa mudar após sua criação.
- No side effects— Você usa funções puras que retornam o mesmo resultado com as mesmas entradas e não modificam o estado de outros objetos ou interagem com o mundo exterior.