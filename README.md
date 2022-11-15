# Код для исследования

В Metaspace ClassLoading подгружается класс JvmComprehension
### `public class JvmComprehension {`
- - -
В момент вызова метода main() создаётся фрейм 1 в стеке
### `public static void main(String[] args) {`
- - -
1) В фрейм-1 создается переменная i, примитивное значение 1 сохраняется в стеке
### `int i = 1;`
- - -
2) В Heap создается объект Object, в фрейм 1 в переменную o сохраняется ссылка на Object в Heap
### `Object o = new Object();`
- - -
3) В Heap создается объект-обертка Integer содержащая 2, в фрейм 1 создается переменная ii со ссылкой на объект*
### `Integer ii = 2`;
- - -
4) В момент вызова метода printAll создаётся фрейм 2 в стеке. Примитив i=1 будет сохранен в фрейм 2, ссылочные переменные o, ii указывают на объекты в Heap
### `printAll(o, i, ii);`
- - -
7) В метод будет передано значение находящееся в String pool
### `System.out.println("finished");`
### `}`
### `private static void printAll(Object o, int i, Integer ii) {`
- - -
5) В фрейм 2 создается ссылочная переменная uselessVar, значение "700" сохраняется в Heap, потом будет удален GC
### ` Integer uselessVar = 700;`
- - -
6) В метод println члена класса System передастся ссылка на объект типа String находящегося в Heap
### `System.out.println(o.toString() + i + ii);`
### `}`
### `}`
