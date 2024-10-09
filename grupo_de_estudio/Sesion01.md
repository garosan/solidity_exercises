# Grupo de Estudio de Solidity. Sesión 01. 08-OCT-2024

Shoutout a Elba por ayudarnos a navegar las fallas técnicas con su cuenta de Google!

Estaremos siguiendo [estas notas](https://docs.hektorprofe.net/python/).

Puedes usar [Google Colab](https://colab.research.google.com/) para seguir los ejercicios en Python sin necesidad de instalar nada en tu computadora.

También puedes usar [Repl.it](https://replit.com/@replit/Python) solo necesitas usar tu cuenta de Google o similar.

O incluso [ésta herramienta todavía más sencilla](https://www.pythonmorsels.com/repl/).

## ¿Qué es un lenguaje de programación?

Un lenguaje de programación es una manera de decirle a las computadoras qué hacer. Así como los humanos usamos palabras para comunicarnos entre nosotros, como programadores usamos palabras especiales y reglas en estos lenguajes para escribir instrucciones que la computadora puede entender y seguir. Cada lenguaje tiene sus propias reglas y maneras de escribir esas instrucciones, pero el objetivo siempre es el mismo: hacer que la computadora haga cosas, como mostrar una página web, hacer cálculos, o controlar un juego.

## Tipos de datos

¿Qué son los tipos de datos?

En Python, estos son los tipos de datos más importantes para empezar:

Números: Flotantes o Enteros

Cadenas.

## Comentarios

## Operaciones con números

En Python, como en casi cualquier lenguaje de programación podemos hacer operaciones matemáticas de manera muy sencilla.

Podemos sumar:

`3 + 2`

Resultado:

`5`

Podemos restar:

`10 - 2`

Resultado:

`8`

Podemos dividir:

`10 / 2`

Resultado:

`5`

Podemos multiplicar:

`3 * 5`

Resultado:

`15`

También podemos hacer exponenciación:

`3 ** 3`

Resultado:

`81`

O encontrar el módulo o residuo de una operación:

`10 % 2`

Resultado:

`0`

Esto nos podría ayudar por ejemplo a saber si un número es par o impar.

## Cadenas o strings

## Variables

Podemos pensar en una variable como una cajita donde podemos almacenar un dato como un número o una cadena que más adelante podemos necesitar para hacer una operación, como saber a qué wallets queremos darles un airdrop por poner un ejemplo.

Por ejemplo, para crear una variable número que sea igual al número 3:

`n = 3`

Hay ciertas reglas para nombrar nuestras variables, como por ejemplo nuestra variable no puede tener espacios, esto estaría mal:

`mi variable = 'Hola'`

Pero esto estaría bien:

`mi_variable = 'Hola'`

## Listas o arreglos

Las listas se tratan de un tipo compuesto de dato que puede almacenar distintos valores (llamados ítems o elementos) ordenados entre [ ] y separados con comas:

`numeros = [1,2,3,4]`

O por ejemplo podríamos tener una lista de wallets a las que queremos darles un airdrop:

`wallets = ['vitalik.eth', 'satoshi.eth', 'solana.eth']`

Hay qué recordar que los arreglos son '0-index', esto quiere decir que empezaremos a contar desde 0 y no desde 1.

Si quisieramos saber cual es la 1era wallet de nuestro arreglo, accedemos a ella de ésta manera:

`wallets[0]`

## Diccionarios o mappings

En cada lenguaje tienen un nombre diferente, lo importante es que son de las estructuras más utilizadas y se basan en una estructura mapeada donde cada elemento de la colección se encuentra identificado con una clave única

Para cada elemento se define la estructura clave:valor:

`colores = {'amarillo':'yellow','azul':'blue'}`

Esta sesión fue llevada por [albertou_eth](https://x.com/albertou_eth) y estas notas se generaron con lo comentado en la sesión + [estas notas](https://docs.hektorprofe.net/python/).
