# Tablas de verdad v4

Elaborado por: Yael Franco Toledo

De acuerdo con [platzi](https://platzi.com/clases/3221-pensamiento-logico/50676-que-son-las-tablas-de-verdad/), las tablas de verdad son herramientas representadas a través de varios gráficos de filas y columnas que muestran todos los posibles escenarios y condiciones de valores de entrada para una operación lógica y su resultado correspondiente.

Su función base es mostrar cómo funcionan un circuito electrónico y los programas de una computadora, siendo también un pilar de la lógica proposicional.

<img src="https://static.platzi.com/media/user_upload/tablas-verdad-reglas-9ad0f07d-24d4-4a02-aaf5-be8db8711221.jpg" witdh=500>

### Una pequeña introducción sobre variables en python

De acuerdo a un [sitio web](https://tutorialpython.com/variables-en-python/) una variable es un repositorio donde guardamos una determinada información. En función del tipo de información que guardemos (texto, números, booleanas, etc.), la variable será de uno u otro tipo. Por simplicidad sólo vamos a ver las variables de texto y numéricas, ya que son las que se usan en más del 80% de las ocasiones.

Cada variable tiene que tener un nombre con el que referirnos a ella. Python tiene en cuenta si escribimos en mayúsculas o minúsculas la variable (lo que se conoce como case sensitive).


```python
numero = 20
```


```python
print (numero)
```

    20
    


```python
nombre = "Juan"
```


```python
print (nombre)
```

    Juan
    


```python
booleano = True
```


```python
print (booleano)
```

    True
    


```python
nombre = input("Escribe tu nombre: ")
```

    Escribe tu nombre: Pepe
    


```python
print (nombre)
```

    Pepe
    


```python
edad = input("¿Cuántos años tienes? ")
```

    ¿Cuántos años tienes? 18
    


```python
print (edad)
```

    18
    


```python
meses = int(edad) * 12
print (meses)
```

    216
    

## Tablas de verdad 

En python existen muchas bibliotecas con diferentes funcionalidades, casi para todo. Para el caso de las tablas de verdad existe la biblioteca [truth-table-generator](https://pypi.org/project/truth-table-generator/) conocida como *ttg*.

Para instalarla es necesario el comando: pip install truth-table-generator

Despues importarlo con el comando: import ttg


```python
import ttg
```

Una tabla de verdad tiene una columna para cada variable de entrada y una columna final que muestra todos los resultados posibles de la operación lógica que representa la tabla

Por ejemplo, si tenemos dos proposiciones: **p**, **q** podemos escribir el siguiente código:


```python
print(ttg.Truths(['p', 'q']))
```

    +-----+-----+
    |  p  |  q  |
    |-----+-----|
    |  1  |  1  |
    |  1  |  0  |
    |  0  |  1  |
    |  0  |  0  |
    +-----+-----+
    

También podemos agregar tres, cuatro o más proposiciones, por ejemplo:


```python
print(ttg.Truths(['p', 'q', 'r']))
```

    +-----+-----+-----+
    |  p  |  q  |  r  |
    |-----+-----+-----|
    |  1  |  1  |  1  |
    |  1  |  1  |  0  |
    |  1  |  0  |  1  |
    |  1  |  0  |  0  |
    |  0  |  1  |  1  |
    |  0  |  1  |  0  |
    |  0  |  0  |  1  |
    |  0  |  0  |  0  |
    +-----+-----+-----+
    


```python
print(ttg.Truths(['p', 'q', 'r','s']))
```

    +-----+-----+-----+-----+
    |  p  |  q  |  r  |  s  |
    |-----+-----+-----+-----|
    |  1  |  1  |  1  |  1  |
    |  1  |  1  |  1  |  0  |
    |  1  |  1  |  0  |  1  |
    |  1  |  1  |  0  |  0  |
    |  1  |  0  |  1  |  1  |
    |  1  |  0  |  1  |  0  |
    |  1  |  0  |  0  |  1  |
    |  1  |  0  |  0  |  0  |
    |  0  |  1  |  1  |  1  |
    |  0  |  1  |  1  |  0  |
    |  0  |  1  |  0  |  1  |
    |  0  |  1  |  0  |  0  |
    |  0  |  0  |  1  |  1  |
    |  0  |  0  |  1  |  0  |
    |  0  |  0  |  0  |  1  |
    |  0  |  0  |  0  |  0  |
    +-----+-----+-----+-----+
    

## Operators and their representations:
<br>
<li>negation: 'not', '-', '~'
<li>logical disjunction: 'or'
<li>logical nor: 'nor'
<li>exclusive disjunction: 'xor', '!='
<li>logical conjunction: 'and'
<li>logical NAND: 'nand'
<li>material implication: '=>', 'implies'
<li>logical biconditional: '='
<br><br>
    <b>Note:</b> Utiliza parentesis! Especialmente con el operador de negación. Utilice las tablas de arriba y abajo como referencia. Aunque se utilicen reglas de precedencia, a veces la precedencia entre conjunción y disyunción no se especifica y es necesario proporcionarla explicitamente en una fórmula determinada entre parentesis.

### Ejercicios 


```python
import ttg
```

Ejercicio 1


```python
print(ttg.Truths(['p', 'q'], ['p and q']))
```

    +-----+-----+-----------+
    |  p  |  q  |  p and q  |
    |-----+-----+-----------|
    |  1  |  1  |     1     |
    |  1  |  0  |     0     |
    |  0  |  1  |     0     |
    |  0  |  0  |     0     |
    +-----+-----+-----------+
    

Ejercicio 2


```python
print(ttg.Truths(['p', 'q','r'], ['(p and q)','(p and q) and r' ]))
```

    +-----+-----+-----+-------------+-------------------+
    |  p  |  q  |  r  |  (p and q)  |  (p and q) and r  |
    |-----+-----+-----+-------------+-------------------|
    |  1  |  1  |  1  |      1      |         1         |
    |  1  |  1  |  0  |      1      |         0         |
    |  1  |  0  |  1  |      0      |         0         |
    |  1  |  0  |  0  |      0      |         0         |
    |  0  |  1  |  1  |      0      |         0         |
    |  0  |  1  |  0  |      0      |         0         |
    |  0  |  0  |  1  |      0      |         0         |
    |  0  |  0  |  0  |      0      |         0         |
    +-----+-----+-----+-------------+-------------------+
    

Ejercicio 3


```python
print(ttg.Truths(['p', 'q'], ['~(p => ~q) and  (p and ~q)']))
```

    +-----+-----+------------------------------+
    |  p  |  q  |  ~(p => ~q) and  (p and ~q)  |
    |-----+-----+------------------------------|
    |  1  |  1  |              0               |
    |  1  |  0  |              0               |
    |  0  |  1  |              0               |
    |  0  |  0  |              0               |
    +-----+-----+------------------------------+
    

Ejercicio 4


```python
print(ttg.Truths(['p', 'q'], ['(p and q) or (p or ~q)']))
```

    +-----+-----+--------------------------+
    |  p  |  q  |  (p and q) or (p or ~q)  |
    |-----+-----+--------------------------|
    |  1  |  1  |            1             |
    |  1  |  0  |            1             |
    |  0  |  1  |            0             |
    |  0  |  0  |            1             |
    +-----+-----+--------------------------+
    

Ejercicio 5


```python
print(ttg.Truths(['p', 'q', 'r'], ['p and q and r']))
```

    +-----+-----+-----+-----------------+
    |  p  |  q  |  r  |  p and q and r  |
    |-----+-----+-----+-----------------|
    |  1  |  1  |  1  |        1        |
    |  1  |  1  |  0  |        0        |
    |  1  |  0  |  1  |        0        |
    |  1  |  0  |  0  |        0        |
    |  0  |  1  |  1  |        0        |
    |  0  |  1  |  0  |        0        |
    |  0  |  0  |  1  |        0        |
    |  0  |  0  |  0  |        0        |
    +-----+-----+-----+-----------------+
    

Ejercicio 6


```python
print(ttg.Truths(['p', 'q'], ['~(p and ~q) and (p and ~q)']))
```

    +-----+-----+------------------------------+
    |  p  |  q  |  ~(p and ~q) and (p and ~q)  |
    |-----+-----+------------------------------|
    |  1  |  1  |              0               |
    |  1  |  0  |              0               |
    |  0  |  1  |              0               |
    |  0  |  0  |              0               |
    +-----+-----+------------------------------+
    

Ejercicio 7

Expresión original: ~~ (~p and ~q) or (p and ~q)


```python
print(ttg.Truths(['p', 'q'], ['(~p and ~q) or (p and ~q)']))
```

    +-----+-----+-----------------------------+
    |  p  |  q  |  (~p and ~q) or (p and ~q)  |
    |-----+-----+-----------------------------|
    |  1  |  1  |              0              |
    |  1  |  0  |              1              |
    |  0  |  1  |              0              |
    |  0  |  0  |              1              |
    +-----+-----+-----------------------------+
    

Ejercicio 8


```python
print(ttg.Truths(['p', 'q', 'r'], ['p or q and r']))
```

    +-----+-----+-----+----------------+
    |  p  |  q  |  r  |  p or q and r  |
    |-----+-----+-----+----------------|
    |  1  |  1  |  1  |       1        |
    |  1  |  1  |  0  |       1        |
    |  1  |  0  |  1  |       1        |
    |  1  |  0  |  0  |       1        |
    |  0  |  1  |  1  |       1        |
    |  0  |  1  |  0  |       0        |
    |  0  |  0  |  1  |       0        |
    |  0  |  0  |  0  |       0        |
    +-----+-----+-----+----------------+
    

Ejercicio 9


```python
print(ttg.Truths(['p', 'q'], ['~(~p and ~q) and (~p and ~q)']))
```

    +-----+-----+--------------------------------+
    |  p  |  q  |  ~(~p and ~q) and (~p and ~q)  |
    |-----+-----+--------------------------------|
    |  1  |  1  |               0                |
    |  1  |  0  |               0                |
    |  0  |  1  |               0                |
    |  0  |  0  |               0                |
    +-----+-----+--------------------------------+
    

Ejercicio 10


```python
print(ttg.Truths(['p', 'q', 'r'], ['p or q and ~r']))
```

    +-----+-----+-----+-----------------+
    |  p  |  q  |  r  |  p or q and ~r  |
    |-----+-----+-----+-----------------|
    |  1  |  1  |  1  |        1        |
    |  1  |  1  |  0  |        1        |
    |  1  |  0  |  1  |        1        |
    |  1  |  0  |  0  |        1        |
    |  0  |  1  |  1  |        0        |
    |  0  |  1  |  0  |        1        |
    |  0  |  0  |  1  |        0        |
    |  0  |  0  |  0  |        0        |
    +-----+-----+-----+-----------------+
    

Ejercicio 11


```python
print(ttg.Truths(['p', 'q', 'r'], ['p and q => r']))
```

    +-----+-----+-----+----------------+
    |  p  |  q  |  r  |  p and q => r  |
    |-----+-----+-----+----------------|
    |  1  |  1  |  1  |       1        |
    |  1  |  1  |  0  |       0        |
    |  1  |  0  |  1  |       1        |
    |  1  |  0  |  0  |       1        |
    |  0  |  1  |  1  |       1        |
    |  0  |  1  |  0  |       1        |
    |  0  |  0  |  1  |       1        |
    |  0  |  0  |  0  |       1        |
    +-----+-----+-----+----------------+
    

Ejercicio 12


```python
print(ttg.Truths(['p', 'q', 'r'], ['p and q => ~r']))
```

    +-----+-----+-----+-----------------+
    |  p  |  q  |  r  |  p and q => ~r  |
    |-----+-----+-----+-----------------|
    |  1  |  1  |  1  |        0        |
    |  1  |  1  |  0  |        1        |
    |  1  |  0  |  1  |        1        |
    |  1  |  0  |  0  |        1        |
    |  0  |  1  |  1  |        1        |
    |  0  |  1  |  0  |        1        |
    |  0  |  0  |  1  |        1        |
    |  0  |  0  |  0  |        1        |
    +-----+-----+-----+-----------------+
    

Ejercicio 13


```python
print(ttg.Truths(['p'], ['p = ~ p']))
```

    +-----+-----------+
    |  p  |  p = ~ p  |
    |-----+-----------|
    |  1  |     0     |
    |  0  |     0     |
    +-----+-----------+
    

Ejercicio 14


```python
print(ttg.Truths(['p', 'q'], ['~(p and ~ q) and (p and ~q)']))
```

    +-----+-----+-------------------------------+
    |  p  |  q  |  ~(p and ~ q) and (p and ~q)  |
    |-----+-----+-------------------------------|
    |  1  |  1  |               0               |
    |  1  |  0  |               0               |
    |  0  |  1  |               0               |
    |  0  |  0  |               0               |
    +-----+-----+-------------------------------+
    

Ejercicio 15

Expresión original: "~~ p or ~~ q"


```python
print(ttg.Truths(['p', 'q'], ['p or q']))
```

    +-----+-----+----------+
    |  p  |  q  |  p or q  |
    |-----+-----+----------|
    |  1  |  1  |    1     |
    |  1  |  0  |    1     |
    |  0  |  1  |    1     |
    |  0  |  0  |    0     |
    +-----+-----+----------+
    

Ejercicio 16


```python
print(ttg.Truths(['p', 'q'], ['p or q']))
```

    +-----+-----+----------+
    |  p  |  q  |  p or q  |
    |-----+-----+----------|
    |  1  |  1  |    1     |
    |  1  |  0  |    1     |
    |  0  |  1  |    1     |
    |  0  |  0  |    0     |
    +-----+-----+----------+
    

Ejercicio 17


```python
print(ttg.Truths(['p', 'q', 'r'], ['p = q or r']))
```

    +-----+-----+-----+--------------+
    |  p  |  q  |  r  |  p = q or r  |
    |-----+-----+-----+--------------|
    |  1  |  1  |  1  |      1       |
    |  1  |  1  |  0  |      1       |
    |  1  |  0  |  1  |      1       |
    |  1  |  0  |  0  |      0       |
    |  0  |  1  |  1  |      0       |
    |  0  |  1  |  0  |      0       |
    |  0  |  0  |  1  |      0       |
    |  0  |  0  |  0  |      1       |
    +-----+-----+-----+--------------+
    

Ejercicio 18


```python
print(ttg.Truths(['p', 'q'], ['(~p or q) or (p and q) => (~p or q) or ~p']))
```

    +-----+-----+---------------------------------------------+
    |  p  |  q  |  (~p or q) or (p and q) => (~p or q) or ~p  |
    |-----+-----+---------------------------------------------|
    |  1  |  1  |                      1                      |
    |  1  |  0  |                      1                      |
    |  0  |  1  |                      1                      |
    |  0  |  0  |                      1                      |
    +-----+-----+---------------------------------------------+
    

Ejercicio 19


```python
print(ttg.Truths(['p', 'q'], ['(p or ~q) => (p => q)']))
```

    +-----+-----+-------------------------+
    |  p  |  q  |  (p or ~q) => (p => q)  |
    |-----+-----+-------------------------|
    |  1  |  1  |            1            |
    |  1  |  0  |            0            |
    |  0  |  1  |            1            |
    |  0  |  0  |            1            |
    +-----+-----+-------------------------+
    

Ejercicio 20


```python
print(ttg.Truths(['p', 'q'], ['(p = ~q) or (p or ~q)']))
```

    +-----+-----+-------------------------+
    |  p  |  q  |  (p = ~q) or (p or ~q)  |
    |-----+-----+-------------------------|
    |  1  |  1  |            1            |
    |  1  |  0  |            1            |
    |  0  |  1  |            1            |
    |  0  |  0  |            1            |
    +-----+-----+-------------------------+
    

Ejercicio 21


```python
print(ttg.Truths(['p', 'q'], ['(~p and q) or (~p => q)']))
```

    +-----+-----+---------------------------+
    |  p  |  q  |  (~p and q) or (~p => q)  |
    |-----+-----+---------------------------|
    |  1  |  1  |             1             |
    |  1  |  0  |             1             |
    |  0  |  1  |             1             |
    |  0  |  0  |             0             |
    +-----+-----+---------------------------+
    

Ejercicio 22


```python
print(ttg.Truths(['p', 'q'], ['~q or ~p']))
```

    +-----+-----+------------+
    |  p  |  q  |  ~q or ~p  |
    |-----+-----+------------|
    |  1  |  1  |     0      |
    |  1  |  0  |     1      |
    |  0  |  1  |     1      |
    |  0  |  0  |     1      |
    +-----+-----+------------+
    

Ejercicio 23


```python
print(ttg.Truths(['p', 'q', 'r'], ['(p => q and r) = ~(~q or r) or ~r']))
```

    +-----+-----+-----+-------------------------------------+
    |  p  |  q  |  r  |  (p => q and r) = ~(~q or r) or ~r  |
    |-----+-----+-----+-------------------------------------|
    |  1  |  1  |  1  |                  0                  |
    |  1  |  1  |  0  |                  1                  |
    |  1  |  0  |  1  |                  1                  |
    |  1  |  0  |  0  |                  0                  |
    |  0  |  1  |  1  |                  0                  |
    |  0  |  1  |  0  |                  1                  |
    |  0  |  0  |  1  |                  0                  |
    |  0  |  0  |  0  |                  1                  |
    +-----+-----+-----+-------------------------------------+
    

Ejercicio 24


```python
print(ttg.Truths(['p', 'q'], ['~p and q => ~(~p or q) or ~q']))
```

    +-----+-----+--------------------------------+
    |  p  |  q  |  ~p and q => ~(~p or q) or ~q  |
    |-----+-----+--------------------------------|
    |  1  |  1  |               1                |
    |  1  |  0  |               1                |
    |  0  |  1  |               0                |
    |  0  |  0  |               1                |
    +-----+-----+--------------------------------+
    

Ejercicio 25


```python
print(ttg.Truths(['p', 'q', 'r'], ['(p => q) and r => ~(p or r) or ~r']))
```

    +-----+-----+-----+-------------------------------------+
    |  p  |  q  |  r  |  (p => q) and r => ~(p or r) or ~r  |
    |-----+-----+-----+-------------------------------------|
    |  1  |  1  |  1  |                  0                  |
    |  1  |  1  |  0  |                  1                  |
    |  1  |  0  |  1  |                  1                  |
    |  1  |  0  |  0  |                  1                  |
    |  0  |  1  |  1  |                  0                  |
    |  0  |  1  |  0  |                  1                  |
    |  0  |  0  |  1  |                  0                  |
    |  0  |  0  |  0  |                  1                  |
    +-----+-----+-----+-------------------------------------+
    

Ejercicio 26


```python
print(ttg.Truths(['p', 'q', 'r'], ['(p => q) and (q => r) => p and ~r']))
```

    +-----+-----+-----+-------------------------------------+
    |  p  |  q  |  r  |  (p => q) and (q => r) => p and ~r  |
    |-----+-----+-----+-------------------------------------|
    |  1  |  1  |  1  |                  0                  |
    |  1  |  1  |  0  |                  1                  |
    |  1  |  0  |  1  |                  1                  |
    |  1  |  0  |  0  |                  1                  |
    |  0  |  1  |  1  |                  0                  |
    |  0  |  1  |  0  |                  1                  |
    |  0  |  0  |  1  |                  0                  |
    |  0  |  0  |  0  |                  0                  |
    +-----+-----+-----+-------------------------------------+
    

Ejercicio 27


```python
print(ttg.Truths(['p', 'q', 'r'], ['~p = (q and r) v ~(~q or r)']))
```

    +-----+-----+-----+-------------------------------+
    |  p  |  q  |  r  |  ~p = (q and r) v ~(~q or r)  |
    |-----+-----+-----+-------------------------------|
    |  1  |  1  |  1  |               0               |
    |  1  |  1  |  0  |               1               |
    |  1  |  0  |  1  |               1               |
    |  1  |  0  |  0  |               1               |
    |  0  |  1  |  1  |               1               |
    |  0  |  1  |  0  |               0               |
    |  0  |  0  |  1  |               0               |
    |  0  |  0  |  0  |               0               |
    +-----+-----+-----+-------------------------------+
    

Ejercicio 28


```python
print(ttg.Truths(['p', 'q'], ['((p or ~q) => (p => q)) => ((~p => q) or ~p) or ~p']))
```

    +-----+-----+------------------------------------------------------+
    |  p  |  q  |  ((p or ~q) => (p => q)) => ((~p => q) or ~p) or ~p  |
    |-----+-----+------------------------------------------------------|
    |  1  |  1  |                          1                           |
    |  1  |  0  |                          1                           |
    |  0  |  1  |                          1                           |
    |  0  |  0  |                          1                           |
    +-----+-----+------------------------------------------------------+
    

Ejercicio 29


```python
print(ttg.Truths(['p', 'q'], ['~(p or q) or (p => q) => ~p => q v ~p']))
```

    +-----+-----+-----------------------------------------+
    |  p  |  q  |  ~(p or q) or (p => q) => ~p => q v ~p  |
    |-----+-----+-----------------------------------------|
    |  1  |  1  |                    0                    |
    |  1  |  0  |                    1                    |
    |  0  |  1  |                    1                    |
    |  0  |  0  |                    1                    |
    +-----+-----+-----------------------------------------+
    

Ejercicio 30


```python
print(ttg.Truths(['p', 'q', 'r'], ['(p => q) and (q => r) => (p and r)']))
```

    +-----+-----+-----+--------------------------------------+
    |  p  |  q  |  r  |  (p => q) and (q => r) => (p and r)  |
    |-----+-----+-----+--------------------------------------|
    |  1  |  1  |  1  |                  1                   |
    |  1  |  1  |  0  |                  1                   |
    |  1  |  0  |  1  |                  1                   |
    |  1  |  0  |  0  |                  1                   |
    |  0  |  1  |  1  |                  0                   |
    |  0  |  1  |  0  |                  1                   |
    |  0  |  0  |  1  |                  0                   |
    |  0  |  0  |  0  |                  0                   |
    +-----+-----+-----+--------------------------------------+
    

Ejercicio 31


```python
print(ttg.Truths(['p', 'q', 'r'], ['(p and q => r) => (p or r)']))
```

    +-----+-----+-----+------------------------------+
    |  p  |  q  |  r  |  (p and q => r) => (p or r)  |
    |-----+-----+-----+------------------------------|
    |  1  |  1  |  1  |              1               |
    |  1  |  1  |  0  |              1               |
    |  1  |  0  |  1  |              1               |
    |  1  |  0  |  0  |              1               |
    |  0  |  1  |  1  |              1               |
    |  0  |  1  |  0  |              1               |
    |  0  |  0  |  1  |              1               |
    |  0  |  0  |  0  |              1               |
    +-----+-----+-----+------------------------------+
    
