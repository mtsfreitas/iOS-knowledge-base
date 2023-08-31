## Introdução aos Closures
Em poucas palavras, Closures são blocos de código que podem ser atribuídos a variáveis, passados como argumentos para funções e armazenados em estruturas de dados. 

A vantagem das closures é a capacidade de encapsular funcionalidades em blocos de código independentes, que podem ser passados como argumentos, capturar seu contexto e promover uma programação mais modular, flexível e legível.

OBS: Toda função é uma closure, mas nem toda closure é uma função.

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


### Exemplo de Closure que soma dois números
A closure 'soma' recebe dois argumentos, a e b, e retorna a soma de a e b.
```swift
let soma = { (a: Int, b: Int) in
  return a + b
}
```

Armazenando o resultado da closure

```swift
let resultado = soma(5, 3) // resultado será 8
```


