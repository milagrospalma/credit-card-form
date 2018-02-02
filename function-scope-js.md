# Functions and scope

## Objetivo
Leer código javascript e identificar las funciones globales, locales, funciones de callback, expresions, statement, clousure, scope, contextos de ejecucion, que funciones forman parte de la pila de ejecucion (stack execution) y que funciones forman parte de la cola de eventos (event queue).

> Las funciones de nombre `longitud` y `soloNumeros` pasaron a ser `cardNumberLength` y `onlyNumbers`, respectivamente.

## Funciones globales
Son las que no están dentro de ninguna función, en este caso, es la función anónima que se ejecuta cuando el DOM se carga completamente.
```js
    $(document).ready(function() {});
```

## Funciones Locales
Son aquellas que se encuentran dentro de otra función. En este ejemplo, se observan 7 funciones locales:
```js
    function() {} // Función anónima relacionada al evento input -> línea 14
    function activeButton() {}
    function desactiveButton() {}
    function cardNumberLength(input) {}
    function onlyNumbers(input) {}
    function isValidCreditCard(numberCard) {}
    creditCardNumber // Está dentro de la función isValidCreditCard -> línea 45
```

## Callback
Funciones que son llamadas por otra función, es decir, una función *`a`* que recibe como argumento a la función *`b`*, ejecutará la función *`b`* cuando la función *`a`* sea invocada.
```js
    onlyNumbers(cardNumberLength(numberCard));
```

## Expressions
Son aquellas funciones que se pueden asignar a una variable (primero se declaran, luego se invocan) y producen un valor.
```js
    var creditCardNumber = onlyNumbers(cardNumberLength(numberCard));
```

## Statement
Funciones creadas directamente y se pueden invocar en cualquier parte del Lexical Enviroment (ambiente lexical).
```js
    function activeButton() {}
    function desactiveButton() {}
    function cardNumberLength(input) {}
    function onlyNumbers(input) {}
    function isValidCreditCard(numberCard) {}
```

## Clousure
Funciones que tienen la capacidad de recordar el contexto en donde fueron creadas.
```js
    function activeButton() {}
    function desactiveButton() {}
    function cardNumberLength(input) {}
    function onlyNumbers(input) {}
    function isValidCreditCard(numberCard) {}
```

## Scope
El alcance de las funciones anteriormente mencionadas es la función anónima global ya que se podrá acceder a ellas estando dentro de la función global, pero no fuera de ella.
```js
    $(document).ready(function() {}); // Función global
```

## Contextos de ejecución
Se crean cada vez que se invoca una función.

## Stack execution
La pila de ejecución indica el orden en el que se ejecutan las funciones. (El orden es de abajo hacia arriba)
```js
    console.log('Probar con el número válido 4544164785372342');      
    $(document).ready(function() {}); // Función global
    Contexto Global
```

## Event queue
Una vez que la pila de ejecución esté vacía, se invocan a las funciones que estén en la cola de eventos.
```js
    $inputCard.on('input', function() { // -> función anónima
      isValidCreditCard($(this).val().trim());
    });
```