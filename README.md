# Array combinations
https://www.codewars.com/kata/59e66e48fc3c499ec5000103

## ¿Qué nos piden?

Nos piden contar cuántas combinaciones únicas de arrays podemos formar al escoger un elemento de cada subarray, teniendo muy en cuenta que los elementos duplicados no cuentan como nuevas combinaciones.

# Por ejemplo:

## Si tenemos [[1,2],[4,4],[5,6,6]], el resultado debe dar 4 porque:

* Podemos elegir 1 o 2 del primer subarray.
* Del segundo subarray solo podríamos elegir una opción el 4.
* Y del último subarray podemos tomar dos opciones: el 5 o el 6.

## Así que las combinaciones únicas son: [1, 4, 5], [1, 4, 6], [2, 4, 5], [2, 4, 6].

# Pseudocódigo

    function contar_combinaciones_unicas(arrays)
      cantidad_total = 1 
      Para cada subarray de los arrays
        cont_opciones = 0
        array_opciones = nuevo array vacío
        Para cada elemento del subarray
          Si elemento no está en array_opciones entonces
            agregar elemento a array_opciones
            cont_opciones++
          Fin si
        cantidad_total *= cont_opciones
      return cantidad_total

# java

public static int contar_combinaciones_unicas(int[][] arrays) {
    int cantidad_total = 1;
    for (int idx = 0; idx < arrays.length; idx++) {
        int[] subarray = arrays[idx];
        int cont_opciones = 0;
        int[] array_opciones = new int[subarray.length];
        int opciones_size = 0;
        for (int j = 0; j < subarray.length; j++) {
            int elemento = subarray[j];
            boolean existe = false;
            for (int i = 0; i < opciones_size; i++) {
                if (array_opciones[i] == elemento) {
                    existe = true;
                    break;
                }
            }
            if (!existe) {
                array_opciones[opciones_size++] = elemento;
                cont_opciones++;
            }
        }
        cantidad_total *= cont_opciones;
    }
    return cantidad_total;
}
