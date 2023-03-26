# UnaMasRecursividad

# UnaMas

1.

a) La llamada a la función recursiva bisect(0, N) calcula la raíz cuadrada de N usando el método de bisección. La función f(x) devuelve x^2 - N. La función bisect divide el intervalo [0, N] en dos mitades iguales y determina en cuál de las mitades la función cambia de signo. Luego, repite este proceso recursivamente en la mitad que contiene la raíz hasta que la diferencia entre los extremos del intervalo sea menor que la constante PREC. En ese momento, devuelve el valor medio del intervalo como la aproximación de la raíz.

Si cambiamos el valor de N, estaría calculando la raíz cuadrada de ese nuevo valor. 

Si cambiamos la función f(x), resolvería la nueva ecuación que se defina en la nueva función f(x) y devolverá la raíz correspondiente a esa ecuación.


b) static double bisect_iter (double min, double max) {
    double med = (min + max) / 2;
    while (max - min >= PREC) {
        if (f(min) * f(med) < 0) {
            max = med;
        } else {
            min = med;
        }
        med = (min + max) / 2;
    }
    return med;
  }
  En este algoritmo iterativo, la variable med se inicializa como la media de min y max. Después hay un bucle while que se ejecutará mientras la diferencia entre max y min sea mayor o igual que PREC. En cada iteración, se verifica si la función cambia de signo en el intervalo [min, med]. Si es así, se actualiza max a med, de lo contrario se actualiza min a med. Después de cada actualización, se recalcula med como el punto medio del nuevo intervalo [min, max]. El bucle termina cuando la diferencia entre max y min es menor que PREC, y devuelve finalmente med.
