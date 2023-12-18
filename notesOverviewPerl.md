# Ventajas
- Fácil manipular números y texto, archivos y directorios, computadoras y redes.
- Fácil ejecutar programas externos y escanear su salida
- Fácil enviar estos datos a otros programas
- Fácil desarrollar, modificar y depurar
- Fácil de ejecutar el programa en cualquier sistema operativo.

*Perl es sencillo de aprender y de usar, ese siempre ha sido y será su objetivo*

```perl
# Hola mundo en Perl!
print "Hello World!\n";
```

# Variables
- Strings y números son piezas de datos únicas, son llamados *escalares*
- Listas y arreglos son plurales(con varios elementos, son llamados *arrays*
````perl
# Inicializar Variable
$phrase = "Hello Peaches!\n";
# Imprimir variable
print $phrase;
````
- No es necesario definir el tipo de variable
- EL símbolo *$* le indica a Perl que es una variable escalar, es decir, de una valor único
- En constraste, el símbolo *@* indica que es un array, una variable de valor plural, múltipe, de varios valores contenidos en ella

Type          | Character     | Example       | Is a name for
------------- | ------------- | ------------- | -------------
Escalar       | $             | $num          | Un valor individual
Arreglo       | @             | @nums         | Lista de valores, indexados por números
Hash          | %             | %dictionary   | Una lista de valores, indexados por Strings
Subrutina     | &             | &function     | Como un método
Typeglob      | *             | *global       | Todos los llamados global

- Recordar que los *verbs* son funciones, acciones llamadas con verbos, como **print**, **open**, etc.
- En Perl, los *nouns* (nombres de variables, sustantivos) destacan de los *verbs* (funciones que realizan acciones), lo que hace que sea fácil leer el código de Perl
- Esto es algo importante, ya que se puede añadir nuevos *verbs* sin romper los ćodigos viejos, se dice que Perl **fue hecho para evolucionar**

## Singularidades

- Se pueden utilizar diferentes mecanismos para inicializar tipos de valores.
  - Comillas dobles: Para una variable de interpolación, permite llamar a variables dentro del mismo, además, que identifica los backslach
  - Comillas simples: COn estas se suprime la interpolación
  - Comillas invertidas: Capturará la salida de un programa externo, como *pwd*

````perl
$answer   = 42;                 # un entero
$pi       = 3.14159265;         # un número real
$avocados = 6.02e23;            # notación científica
$pet      = "Camel";            # string
$sign     = "I love my $pet";   # string con interpolación
$cost     = 'It costs $100';    # string sin interpolación
$thence   = $whence;            # el valor de otra variable
$salsa    = $moles * $avocados; # una expresión gastroquímica, en notación científica
$exit     = system("vi $file"); # estado numérico de un comando
$cwd      = `pwd`;              # salida en string de un comando
````
- También podemos hacer referencias en Perl

````perl
$ary  = \@myarray;              # referencia a un arreglo identificado
$hsh  = \%myhash;               # referencia a un hash identificado
$sub  = \&mysub;                # referencia a una subrutina identificada
$ary  = [1,2,3,4,5];            # referencia a un arreglo no identificado
$hsh  = {'Na' = > 19, 'Cl' = > 35}; # referencia a un hash no identificado
$sub  = sub { print $state };   # reference a una subrutina no identificada
$fido = new Camel "Amelia";     # referencia a un objeto
````

- Si se usa una variable cuyo valor no ha sido asignado, su valor surge según sea necesario
- Dependiendo donde sea utilizada puede tomar valor "" o 0, incluso true y false
- Algunos operadores proporcionan un contexto escalar, es decir, ayudan al intérprete a manejar los datos de acuerdo a la situación, esto es automático, por ejemplo:
````perl
$camels = '123';
print $camels + 1, "\n";
````
- El valor original de camels es un string, pero se convierte a número para sumarle 1, luego se convertido nuevamente a string para imprimir el valor 124.
- Si colocamos '\n', no se obtendrá el salto de línea, serán leídos como dos caracteres

````perl
fido = new Camel "Amelia";
if (not $fido) { die "dead camel"; }
$fido -> saddle();
````
- En este ejemplo se inicializa una referencia a un objeto Camello y se coloca en la variable $fido. Dentro del if, esta variable se comporta como booleano.
- *true*: si logró construir el objeto, *false* si falló, por lo tanto, se captura la excepción
- **Nota**: En mi salida, el programa mostró: 
  - Can't locate object method "new" via package "Camel" (perhaps you forgot to load "Camel"?) at -e line 1.
  - Can't modify constant item in scalar assignment at test.pl line 1, near ""Amelia";"
Execution of test.pl aborted due to compilation errors.
- Lo más importante que se debe tener en cuenta es que en Perl, el contexto es importante, ya que Perl conoce que quieres sin decirlo explícitamente (o al menos eso intenta)

## Pluralidades

- Perl tiene dos tipos de variables multivalor: arreglos y hashes, de muchas maneras, estos se comportan como escalares
- Surgen sin nada en ellos cuando es necesario, sin embargo, surgen con un contexto de lista, a diferencia de los escalares, que surgen con un contexto escalar 
- Hashes y arreglos con complementarios, unos transforma de números a strings, y el otro de strings a números.

### Array

- Es una lista ordenada a la que se accede por la posición escalar.
- Puede contener números, strings, referencias a objetos, subarreglos, subhashes, o una mixtura de todo.

````perl
@home = ("couch", 1, $hello, "table");
````

- Usaremos la @home en un contexto de lista, por ejemplo, podemos asignar sus valores a variables de la siguiente manera:

````perl
($home1, $home2, $home3, $home4) = @home;
````

- Son llamados asignación de listas y suceden en paralelo, por lo que podemos intercambiar dos valores de la siguiente manera:

````perl
($alpha, $omega) = ($omega, $alpha);
````

- Para seleccionar elementos del arreglo, se utilizan corchetes `$home[n]` donde n es la posición en el arreglo, de esta manera se puede utilizar los elementos de un arreglo. Asimismo, se puede asignar nuevos valores a los elementos de un arreglo.
- Con los arreglos se pueden hacer operaciones de pila como *push* y *pop*. ya que, la pila al fin y al cabo es una lista ordenada.

### Hashes

- El bash es un hash, una configuración desordenada de escalares, a los que se accede a través de un valor de string.
