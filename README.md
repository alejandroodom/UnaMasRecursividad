# UnaMasRecursividad

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


 2.
  
  a) La llamada a la función recursiva f(x, 2) muestra por pantalla todos los factores primos de x.

  Un nombre más adecuado para la función f sería print_factores_primos_x.
  
  
  b) Implementación iterativa:
      static void mostrar_factores_primos_iter(int num) {
          int div = 2;
          while (num > 1) {
            if (num % div == 0) {
              System.out.println(div);
              num /= div;
            } else {
              div++;
            }
          }
      }
      
      En esta implementación iterativa, se inicializa div en 2 y se entra en un bucle while que se ejecuta mientras num sea mayor que 1. En cada iteración, se comprueba si div es un divisor de num. Si se cumple esto, se muestra div por pantalla y se divide num por div. Si div no es un divisor de num, se incrementa div. El bucle termina cuando num es menor que 2.
      
      Implementación mediante expresiones lambda:
      static IntConsumer mostrar_factores_primos_lambda = num -> {
          IntStream.rangeClosed(2, num).filter(div -> num % div == 0).findFirst().ifPresent(div -> {
            System.out.println(div);
            mostrar_factores_primos_lambda.accept(num / div);
          });
      };
      
      En esta implementación, se utiliza una expresión lambda IntConsumer para representar la función mostrar_factores_primos. La expresión lambda toma un argumento         num y utiliza IntStream.rangeClosed para generar una secuencia de enteros desde 2 hasta num. Luego, utiliza filter para filtrar los números de la secuencia que         son divisores de num y findFirst para obtener el primer divisor. Si se encuentra un divisor, se muestra por pantalla y se llama recursivamente a la expresión           lambda con el cociente de num y el divisor como argumento.

      La llamada a la función mostrar_factores_primos_lambda.accept(x) muestra por pantalla todos los factores primos de x.
      
      
      3.
      
      public static String decimalAHexadecimal(int decimal) {
          if (decimal == 0) {
            return "0";
          }
          StringBuilder resultado = new StringBuilder();
          while (decimal > 0) {
            int residuo = decimal % 16;
            if (residuo < 10) {
              resultado.insert(0, residuo);
            } else {
              resultado.insert(0, (char) (residuo - 10 + 'A'));
         }
            decimal = decimal / 16;
         }
         return resultado.toString();
    }
    
    La función utiliza un StringBuilder para ir construyendo la cadena resultado, que se va formando de derecha a izquierda utilizando el método insert(0, valor).
    
    
     4.
    
    Recursiva:
    public static boolean esPalindromoRecursivo(String s) {
        if (s.length() <= 1) {
          return true;
        } else {
        char primer = s.charAt(0);
        char ultimo = s.charAt(s.length() - 1);
            if (primer != ultimo) {
              return false;
            } else {
              String subcadena = s.substring(1, s.length() - 1);
              return esPalindromoRecursivo(subcadena);
            }
      }
  }
  La función esPalindromoRecursivo recibe una cadena s y devuelve true si es un palíndromo, y false en caso contrario. Si la longitud de la cadena es menor o igual a     1, la función devuelve true. En caso contrario, se comparan el primer y el último carácter de la cadena, y si no son iguales, la   función devuelve false. Si son iguales, se llama recursivamente a la función con la subcadena que resulta de eliminar estos dos caracteres.
  
  Iterativa:
  public static boolean esPalindromoIterativo(String s) {
      int i = 0;
      int j = s.length() - 1;
      while (i < j) {
          if (s.charAt(i) != s.charAt(j)) {
              return false;
          }
          i++;
          j--;
      }
      return true;
  }
  La función esPalindromoIterativo recibe una cadena s y devuelve true si es un palíndromo, y false en caso contrario. La función utiliza dos índices, i y j, que apuntan   al primer y al último carácter de la cadena, respectivamente. En cada iteración del bucle, se comparan los caracteres apuntados por i y j, y si no son iguales, la función devuelve false. Si son iguales, se actualizan los índices para apuntar al siguiente par de caracteres, hasta que i sea mayor o igual que j, en cuyo caso la función devuelve true.


 5.
  
  Recursivo:
  public static int mcdRecursivo(int m, int n) {
    if (n == 0) {
        return m;
    } else {
        return mcdRecursivo(n, m % n);
    }
  }
  
  Iterativo:
  public static int mcdIterativo(int m, int n) {
    while (n != 0) {
        int r = m % n;
        m = n;
        n = r;
    }
    return m;
  }
  
  Expresiones lambda:
  BiFunction<Integer, Integer, Integer> mcdLambda = (m, n) ->
    (n == 0) ? m : mcdLambda.apply(n, m % n);
  
 
    
   
