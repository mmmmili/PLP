# 📚 Trabajo Practico 8 - Prolog 💻
## 📌 Ejercicio 1

## 📌 Ejercicio 2

## 📌 Ejercicio 3
### Suma 
```
suma(0,Y,Y).

suma(X,Y,R):-
    succ(X1,X),
    suma(X1,Y,R1),
    succ(R1,R).
```
### Resta
```
resta(X,0,X).

resta(X,Y,R):-
    succ(Y1,Y),
    resta(X,Y1,R1),
    succ(R,R1).
```

### Multiplicacion
```
multiplicacion(0,_,0).

multiplicacion(X,Y,R):-
    succ(X1,X),
    multiplicacion(X1,X,R1),
    suma(R1,Y,R).
```
### Division
```
menor(0,Y):-
    succ(_,Y).

menor(X,Y):-
    succ(X1,X),
    succ(Y1,Y),
    menor(X1,Y1).
    
division(X,Y,0):-
    menor(X,Y).
    
division(X,Y,R):-
	resta(X,Y,X1),
	division(X1,Y,Q1),
	succ(Q1,R).
```

## 📌 Ejercicio 4
‼️ ATOMO: un atomo es una costante. puede ser una cadena de caracteres de letras mayúsculas, minúsculas, dígitos o guión bajo, que comienza
con una letra minúscula ej `panadero` . O una cadena encerrada entre comillas simples `'Panadero'`. O una cadena de caracteres especiales como `====>`.

‼️ Variables: Una cadena de caracteres de letras mayúsculas, minúsculas, dígitos o guión bajo, que comienza
con una letra mayúscula o con un guión bajo. Por ejemplo: `X`, `Y`, `_etiqueta`.

✅ Dos términos unifican si hay una manera de hacerlos idénticos mediante sustitución de variables.

| Término 1                        | Término 2                        | Unifican? |
|----------------------------------|----------------------------------|------------|
| point(A,B)                       | point(1,s(2))                    |     S     |
| pre(A,B)                         | pre(X,Y,Z)                       |     N     |
| 6                                | 4                                |     N      |
| esquina(X+Y)                     | esquina(corrientes+cordoba)     |      S     |
| Diana                            | 'Diana'                          |     N      |
| 'Diana'                          | 'Diana'                          |     S      |
| _                                | diana                            |     S       |
| X+1-Y*2                          | (X+1)-(Y*2)                      |     S      |
| long(X, punto(A,2))             | long(Y, punto(2+1, )))          |       N     |
| plus(2,2)                        | 3+3                              |     N      |
| admira(X, padre(X))             | admira(padre(U), V)             |       S     |
| p(q(-1,0),P2,P3)                | p(P1, q(1,0), q(0,Y))           |       N     |



