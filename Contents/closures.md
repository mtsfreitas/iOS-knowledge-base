<link rel="stylesheet" href="highlight.css">

## Introdução aos Closures
Em poucas palavras, Closures são blocos de código que podem ser atribuídos a variáveis, passados como argumentos para funções e armazenados em estruturas de dados. 

A vantagem das closures é a capacidade de encapsular funcionalidades em blocos de código independentes, que podem ser passados como argumentos, capturar seu contexto e promover uma programação mais modular, flexível e legível.


<span style="background-color: #FFFF00; color: black">OBS: Toda função é uma closure, mas nem toda closure é uma função.</span>


## Sintaxe Básica 

A sintaxe da expressão de uma closure tem a seguinte forma geral:

```swift
{ (parameters) -> ReturnType in
   // statements
}
```
Também pode ser escrito assim: 

```swift
{ (parameters) -> ReturnType = {
     // statements
}
```

* parameters - qualquer valor passado para o closure
* ReturnType - especifica o tipo de valor retornado pelo closure
* in (opcional) - usado para separar parâmetros/tipoRetorno do corpo do closure


## Exemplo de Closue em constantes
### Soma dois números
A closure 'soma' recebe dois argumentos, a e b, e retorna a soma de a e b.
```swift
let soma = { (a: Int, b: Int) in
  return a + b
}
```

Chamando a closure através da constante

```swift
let resultado = soma(5, 3) // resultado será 8
```

### Exibir texto
Armazena uma closure que não aceita nenhum argumento e retorna uma string de saudação.


```swift
let greetClosure: () -> String = {
    return "Olá, mundo!"
}
```
Chamando a closure através da constante
```swift
let greeting = greetClosure()
print(greeting) // Saída: "Olá, mundo!"
```

## Closures como argumentos de função

Neste exemplo, temos uma função chamada <mark class = "red">applyOperation</mark> que aceita dois valores inteiros (a e b) e uma closure chamada  <mark class = "red">operation</mark> como argumento. Essa closure espera duas entradas inteiras e retorna um valor inteiro.

```swift
func applyOperation(_ a: Int, _ b: Int, operation: (Int, Int) -> Int) -> Int {
    return operation(a, b)
}
```

A função applyOperation é usada para executar operações aritméticas, sendo que você pode passar a closure add ou subtract como argumento para determinar qual operação será realizada.


```swift
let add: (Int, Int) -> Int = { a, b in
    return a + b
}
```

```swift
let subtract: (Int, Int) -> Int = { a, b in
    return a - b
}
```
Foram definidas duas closures: <mark class = "purple">add</mark> e <mark class = "purple">subtract</mark>. A closure add simplesmente retorna a soma de seus dois argumentos, enquanto a closure subtract retorna a diferença entre seus dois argumentos.

```swift
let result1 = applyOperation(5, 3, operation: add) // Resultado: 8
let result2 = applyOperation(10, 4, operation: subtract) // Resultado: 6
```

## Closures como valores de retorno
A função <mark class = "red">makeIncrementer</mark> aceita um valor inteiro incrementAmount e retorna uma closure que, quando chamada, incrementa o valor interno total pelo valor de incrementAmount e retorna o novo valor de total.

```swift
func makeIncrementer(incrementAmount: Int) -> () -> Int {
    var total = 0
    
    let incrementer: () -> Int = {
        total += incrementAmount
        return total
    }
    
    return incrementer
}
```
As closures retornadas por makeIncrementer capturam a variável total e o incrementAmount do escopo da função. Isso permite criar "contadores" independentes, cada um com seu próprio estado interno.

```swift
let incrementByTwo = makeIncrementer(incrementAmount: 2)
print(incrementByTwo()) // Resultado: 2
print(incrementByTwo()) // Resultado: 4

let incrementByFive = makeIncrementer(incrementAmount: 5)
print(incrementByFive()) // Resultado: 5
```

## Capturando variáveis externas
A função <mark class = "red">makeCounter</mark> retorna uma closure que atua como um contador. Cada vez que a closure é chamada, ela incrementa uma variável count definida no escopo da função.

```swift
func makeCounter() -> () -> Int {
    var count = 0
    
    let counter: () -> Int = {
        count += 1
        return count
    }
    
    return counter
}
```

Essa closure mantém uma referência à variável count mesmo após a função makeCounter ter concluído sua execução. Isso é um exemplo de como as closures podem capturar e manter referências a variáveis do escopo em que foram definidas.

```swift
let counter = makeCounter()
print(counter()) // Resultado: 1
print(counter()) // Resultado: 2
print(counter()) // Resultado: 3
```