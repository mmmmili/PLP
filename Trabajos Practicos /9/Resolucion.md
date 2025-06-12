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
| Arreglo1 vs Arreglo2     | ✔ No               | ✔ Sí                | ✖ No           |





