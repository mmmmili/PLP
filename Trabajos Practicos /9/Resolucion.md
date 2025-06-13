# Trabajo Practico 9 - Equivalencia de Tipo de Dato

## 1. ¿Cual es la diferencia entre equivalencia de tipo de dato y compatibilidad de tipo de dato?
- Equivalencia de tipo: dos tipos son equivalentes si son exactamente del mismo tipo, segun las reglas del lenguaje.

- Dos tipos son compatibles si se pueden usar juntos sin error, aunque no sean equivalentes. Es una relación más flexible que la equivalencia.

## 2. 
(a) Sobre Registros
1. type algoA = record a, b: integer end;
2. type algoB = record
            a, b: integer
          end;
3. type algoC = record
      a: integer;
      b: integer
        end;
4. type algoD = record
      b, a: integer
      end;
5. type algoE = record
    b: integer;
    a: integer
  end;

| Comparación        | ¿Misma definición? | ¿Misma estructura? | ¿Mismo nombre? |
|--------------------|--------------------|---------------------|----------------|
| algoA vs algoB     | ✔ Sí               | ✔ Sí                | ✖ No           |
| algoA vs algoC     | ✖ No               | ✔ Sí                | ✖ No           |
| algoA vs algoD     | ✖ No               | ✖ No                | ✖ No           |
| algoA vs algoE     | ✖ No               | ✖ No                | ✖ No           |
| algoD vs algoE     | ✖ No               | ✔ Sí                | ✖ No           |
| algoD vs algoC     | ✖ No               | ✖ No                | ✖ No           |

(b) Sobre Arreglos:
1. type Arreglo1 = array [1..10] of char;
2. type Arreglo2 = array [0..9] of char;

| Comparación              | ¿Misma definición? | ¿Misma estructura?  | ¿Mismo nombre? |
|--------------------------|--------------------|---------------------|----------------|
| Arreglo1 vs Arreglo2     | ✔ No               | ✔ No                | ✖ No           |

## 3. 
1. type T = array [1..10] of integer
2. S = T
3. A : T
4. B : T
5. C : S
6. D : array [1..10] of integer

por estructura: 
- A,B,C,D,S,T
por nominal: 
- T,D
- A,B

## 4. Considere la declaracion con punteros e indique los tipos de equivalencias de tipos encontrados:
TA = pointer to TA ; 1
TB = pointer to TB ; 2
TC = record 3
Dato : Integer ; 4
   Siguiente : pointer to TC ; 5
end; 6
TD = record 7
Dato : Integer ; 8

| Comparación   | ¿Equivalencia nominal? | ¿Equivalencia estructural? | Justificación                                             |
|---------------|------------------------|-----------------------------|----------------------------------------------------------|
| TA vs TB      | ✖ No                   | ✔ Sí                        | Mismo tipo (punteros autoref), distinto nombre           |
| TA vs TC      | ✖ No                   | ✖ No                        | Uno es puntero, otro es record                           |
| TC vs TD      | ✖ No                   | ✖ No                        | TC tiene puntero interno, TD no                          |


## 5. Considere la siguiente declaraci´on y analice las equivalencias de tipos posibles:

1. type cell // (una declaración cualquiera, no detallada)
2. type cell_ptr = pointer to cell
3. x : cell
4. type cell2 = record
5.   val : integer;
6.   next : cell_ptr
7. y : cell2


| Comparación          | ¿Equivalencia nominal? | ¿Equivalencia estructural? | Justificación                                                       |
|----------------------|------------------------|-----------------------------|---------------------------------------------------------------------|
| `cell` vs `cell_ptr` | ✖ No                   | ✖ No                        | Uno es un tipo , el otro es un puntero al tipo                     |
| `cell_ptr` vs `next` | ✔ Sí                   | ✔ Sí                        | `next` usa el tipo `cell_ptr` directamente.                        |??
| `x` vs `y`           | ✖ No                   | ✖ No                        | `x` es de tipo `cell`, `y` es de tipo `cell2`, estructuras dist    |
| `x` vs `next`        | ✖ No                   | ✖ No                        | `x` es `cell`, `next` es `pointer to cell`.                        |

            
## 6. Para el siguiente codigo de programa escrito en el Lenguaje de Programacion C, indique que variables son equivalentes en tipo segun: Equivalencia Estructural, Equivalencia por Definicion y Equivalencia de Nombres:
typedef struct { 
            char * cara ; 
            char * palo ; 
} TipoCarta1 , TipoCarta2 ; 
TipoCarta1 carta1 , carta2 ; 
TipoCarta2 carta3 ; 
TipoCarta2 carta4 ; 

| Comparación          |        Nombre          | Estructura                  | Definicion                                                     |
|----------------------|------------------------|-----------------------------|-----------------------------------------------------------------|
| TipoCarta1 vs TipoCarta2 | ✔ Sí               | ✔ Sí                        | Ambos son alias del mismo `struct` anónimo                     |
| carta1 vs carta3     | ✔ Sí                   | ✔ Sí                        | Tipos distintos por nombre, pero son el mismo tipo en C        |??
| carta3 vs carta4     | ✔ Sí                   | ✔ Sí                        | Mismo tipo (`TipoCarta2`), misma estructura                    |

## 7. 
type 1
T1 , T2 , T3 = array [1..10] of real ; 2
T4 = array [1..10] of real ; 3
Flotante = real ; 4
T5 = array [1..10] of Flotante 5
var V11 , V12 : T1 ; 6
V2 : T2 ;

| Comparación        | ¿ Nombre? | ¿Estructura? | ¿Compatibles? | Justificación                                                                 |
|--------------------|----------------------|--------------------------|---------------|--------------------------------------------------------------------------------|
| T1 vs T2           | ✔ Sí                 | ✔ Sí                     | ✔ Sí          | Definidos juntos en la misma línea                                            |
| T1 vs T3           | ✔ Sí                 | ✔ Sí                     | ✔ Sí          | Definidos juntos en la misma línea                                            |
| T1 vs T4           | ✖ No                 | ✔ Sí                     | ✔ Sí          | Misma estructura (`array[1..10] of real`), pero definidos por separado        |
| T1 vs T5           | ✖ No                 | ✔ Sí                     | ✔ Sí          | `T5` es `array[1..10] of Flotante`, y `Flotante = real`                       |
| T4 vs T5           | ✖ No                 | ✔ Sí                     | ✔ Sí          | Misma estructura, distintos nombres                                            |
| V11 vs V12         | ✔ Sí                 | ✔ Sí                     | ✔ Sí          | Mismo tipo: `T1`                                                              |
| V11 vs V2          | ✔ ?                 | ✔ ?                     | ✔ ?          |                                 |


