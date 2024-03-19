# Checkpoint 8

## **¿Qué tipo de bucles hay en JS?**

Hay varios tipos de bucles en Javascript, aunque quizás sea conveniente explicar en qué consiste un bucle primero. Un bucle es una pieza de código que repite una acción un número de veces determinado. Veámoslo como si fuera un ascensor que sube y baja continuamente. 
![](https://lenguajejs.com/fundamentos/introduccion/conceptos-previos/bucles-iteraciones.png)
Volviendo a la pregunta, los bucles más importantes en JS son los bucles for, for in, for of, for each, while y do while. El bucle for es el estándar, siendo for in/of/ y each variantes más modernas que hhan ido surgiendo con el tiempo.

### Bucle for

El bucle for es el bucle estándar, como ya he dicho. Vamos a ver cómo funciona saltando al código directamente:

```
// for (inicialización; condición; incremento)
for (let i = 0; i < 5; i++) {
  console.log("Valor de i:", i);
}
```
El primer elemento del bucle for, *let i = 0*, es el valor del contador, que normalmente suele empezar en cero. Este valor irá cambiando con cada iteración del bucle, aumentando en uno cada vez. Cuando el valor del contador llegue a la condición especificada por el bucle este se parará. El segundo elemento del bucle for, *i < 5*, viene a decir que el bucle se ejecutará mientras i sea menor que 5 (en otras palabras, que al llegar a 5 se detendrá) y el tercer elemento, *i++*, incrementa el valor del índice en 1 con cada iteración. Esto es lo que hace que el bucle avance (si lo olvidamos el bucle será infinito, lo que puede dar problemas de rendimiento), y si lo imprimimos en consola obtendremos los valores 0, 1, 2, 3 y 4. Empieza en 0 porque es el valor inicial del contador, itera la primera vez y ya pasa a 1, y acaba en 4 porque al llegar a 5 se detiene.

### Bucle for in

El bucle for in es algo más moderno que el bucle for a secas y se usa para iterar sobre las propiedades de un objeto, entre otras cosas. Vamos a ver un ejemplo: 
```
var totn_colors = { primary: 'blue', secondary: 'gray', tertiary: 'white' };

for (var color in totn_colors) {
   console.log(totn_colors[color]);
```

Tenemos un objeto con tres propiedades. El bucle inicia con una key (por convención se usa el singular de la variable a iterar) y a continuación llama a la variable. Finalmente se imprime la variable y la key entre corchetes. Este ejemplo de código imprime *blue*, *gray* y *white*.

### Bucle for of

Este bucle se usa para iterar sobre estructuras de datos, como arrays.
```
const cars = ["BMW", "Volvo", "Mini"];

let text = "";
for (let x of cars) {
  text += x;
}
```

Funciona de forma similar a for in, con una variable/key que luego llama al objeto a iterar. Finalmente termina añadiendo cada iteración (con un operador compuesto) a la variable text, que inicia vacía.

### Bucle for Each

For each también se usa para iterar sobre arrays, pero el bucle requiere que se le pase una función, que es la que funciona como iterador. Vamos a ver código:

```
const fruits = ["apple", "orange", "cherry"];
fruits.forEach(fruit => console.log(fruit));
```
Esto imprime *apple*, *orange* y *cherry*.

### Bucles while y do while

Estos dos bucles son menos utilizados que los bucles for y sus variantes, y también son más antiguos. 

El bucle while se parece al bucle for normal, solo que en vez de poner la condición a secas se pone un while delante. A continuación el contador se incrementa.
```
let i = 0;  // Inicialización de la variable contador

// Condición: Mientras la variable contador sea menor de 5
while (i < 5) {
  console.log("Valor de i:", i);
  
  i = i + 1; // Incrementamos el valor de i
}
```

El bucle do while es parecido al while, pero siempre se ejecuta al menos una vez:
```
let i = 5;
do {
  console.log("Hola a todos");
  i = i + 1;
} while (i < 5);
console.log("Bucle finalizado");
```

En lugar de utilizar un while desde el principio junto a la condición, escribimos do. El while con la condición se traslada al final del bucle.
Lo que ocurre en este caso es que el interior del bucle se realiza siempre, y sólo se analiza la condición al terminar el bucle, por lo que aunque no se cumpla, se va a realizar al menos una vez.

### Break y continue en bucles

Es posible parar un bucle antes de que haya llegado a su final (porque se ha cumplido la condición o llegado al final del objeto). Esto se consigue con la sentencia break:

```
for (i = 0; i < 1000; i++) {
    if (i === 3) { break; }
    connsole.log("Contador: " + i);
}
```

La instrucción continue sirve para saltarse instrucciones específicas, es decir, si llega a esta instrucción el bucle se saltará lo que ponga a continuación y pasará a la siguiente instrucción del bucle.
```
for (i = 0; i < 10; i++) {
    if (i === 4) { continue; }
    connsole.log("Contador: " + i);
}
```
Cuando el contador vale 4 no se ejecuta y pasa al 5.

## **¿Cuáles son las diferencias entre const, let y var?**

var permite reasignar un valor a una variable. Si tengo algo como
```
var edad = 28
```
puedo reasignarlo y decir 
```
var edad = 29
```
Y al imprimir en consola obtendría 29. Esto puede resultar útil en algunos casos, pero suele considerarse una mala práctica porque al reasignar variables estamos reescribiéndolas. Es mejor usar let o const.

Let y const son otra cosa, ya que una vez declaradas no pueden declararse de nuevo y si tecleara el ejemplo anterior me daría error. ¿Cuál es la diferencia entonces? Let puede modificarse dentro de su ámbito. Esto sería correcto,
```let saludar = "dice Hola";
    saludar = "dice Hola tambien";
```
pero esto otro no:
```
let saludar = "dice Hola";
    let saludar = "dice Hola tambien"; // error: Identifier 'saludar' has already been declared
```

En cuanto a const, no puede ni redeclararse ni modificarse. Esto resulta útil cuando hablamos de cosas que no van a cambiar nunca, como por ejemplo:
```
const pi = 3,14
```
Si intento cambiarlo dará error.

## **¿Qué es una función de flecha?**

Una función de flecha es un nuevo tipo de función que hace la lectura de código más sencilla. Básicamente, se trata de reemplazar eliminar la palabra function y añadir => antes de abrir las llaves:
```
const func = function () {
  return "Función tradicional.";
};

const func = () => {
  return "Función flecha.";
};
```

* Si el cuerpo de la función sólo tiene una línea, podemos omitir las llaves ({}). Además, en ese caso, automáticamente se hace un return de esa única línea, por lo que podemos omitir también el return.
* En el caso de que la función no tenga parámetros, se indica como en el ejemplo anterior: () =>.
* En el caso de que la función tenga un solo parámetro, se puede indicar simplemente el nombre del mismo: parametro =>.
* En el caso de que la función tenga 2 ó más parámetros, se indican entre paréntesis: (a, b) =>.
* Si queremos devolver un objeto, que coincide con la sintaxis de las llaves, se puede englobar con paréntesis: ({name: 'John'}).

## **¿Qué es la deconstrucción de variables?**

La deconstrucción de variables permite "desempaquetar" valores de arrays o propiedades de objetos, o cualquier cosa en distintas variables.
```
let frutas = ["Manzana", "Pera" , "Platano"];
let [fruta1, fruta2, fruta3] = introduccion;


console.log(fruta1); // "Manzana"
console.log(fruta2); // "Pera"
console.log(fruta3); // "Platano"
```
Si por ejemplo quiero omitir el segundo elemento, no tengo más que escribir:
```
let frutas = ["Manzana", , "Platano"];
console.log(frutas)
```
Y entonces solamente tendría el primer y el tercer elemento del array.

Es posible hacerlo también con objetos:
```
const obj = { a: 1, b: 2 };
const { a, b } = obj;
```
que es lo mismo que decir 
```
// const a = obj.a;
// const b = obj.b;
```

## **¿Qué hace el operador de extensión en JS?**

El operador de extensión o *spread operator* distribuye los elementos dentro de un iterable (cadena de texto, array o cualquier cosa que se pueda recorrer) dentro de un receptor. La sintaxis de este operador son tres puntos (...) seguidos de la variable que nos interese repartir. Tiene ***muchos*** usos, entre los cuales destacan:

#### Combinar elementos
```
let shoppingCart = [345, 375, 765, 123];
let newItems = [98, 123];

shoppingCart.push(...newItems);
console.log(shoppingCart); // [345, 375, 765, 123, 98, 123]
```

#### Copiar elementos
```
let animales = ['perro', 'caballo', 'gato', 'oso', 'jirafa'];
console.log(animales); // Resultado -> 'perro', 'caballo', 'gato', 'oso', 'jirafa'

let copiaDeAnimales = [...animales];
console.log(copiaDeAnimales); // Resultado -> 'perro', 'caballo', 'gato', 'oso', 'jirafa'
```

### Combinar elementos y añadir nuevos

```
let poblaciones = ['Benicasim', 'Castellón', 'Alcocebre'];
console.log(poblaciones);
// Resultado -> ["Benicasim", "Castellón", "Alcocebre"]

let nuevasPoblaciones = ['Oropesa', ...poblaciones];
console.log(nuevasPoblaciones);
// Resultado -> ["Oropesa", "Benicasim", "Castellón", "Alcocebre"]

let masPoblacionesNuevas = [...poblaciones, 'Madrid'];
console.log(masPoblacionesNuevas);
// Resultado -> ["Benicasim", "Castellón", "Alcocebre", "Madrid"]
```

Todo esto también podemos hacerlo con objetos.

## **¿Qué es la programación orientada a objetos?**

La Programación Orientada a Objetos (POO, o en inglés OOP) es una corriente de programación moderna que trabaja con estructuras de datos. Mediante el uso de ***clases***, que vienen siendo plantillas de objetos, podemos encapsular comportamiento sin repetir tanto código. Si tuviéramos una receta de distintos pasteles, cada uno tendría sus propias características, como por ejemplo sabor, pero tendría elementos comunes. Así, a partir de una 
misma receta podríamos crear distintos pasteles, aunque cambiando 
ingredientes. Los pasteles serían los objetos creados a partir de la receta (clase).

Además de proveernos una forma de agrupar y organizar nuestro código y crear nuevos elementos basados en ellas sin repetirnos, las clases nos ofrecen una forma similar a la vida real de crear estructuras de datos, que de otra forma podría ser mucho más complejo.

Si por ejemplo, necesitáramos añadir una variable que indique la velocidad que tiene el personaje, podríamos añadir una propiedad denominada velocidad que contenga un 5. Luego, podríamos incluir un método denominado correr que cambie esa propiedad velocidad a 10, y un método denominado caminar que la vuelva a cambiar a 5.

## **¿Qué es una promesa en JS?**

Una promesa es un elemento que, como en la vida real, tarda un tiempo en verse ejecutada (o puede que no se ejecute nunca, o se quede a medias, como en la vida real). Esto es útil para cuando se hacen conexiones con APIs, ya que si el servidor falla podemos hacer que vuelva a entregarnos datos cuando esté de nuevo operativo, por ejemplo.
![](https://lenguajejs.com/javascript/asincronia/promesas/promises.png)

La estructura básica para crear una promesa es esta:
```
let greeting = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("hello")
  }, 2000)

  setTimeout(() => {
    reject(Error("greeting not found"))
  }, 2000);
});
```

Utilizamos las palabras reservadas new Promise, que toman dos argumentos: uno para cuando se cumple (resolve) y otro para cuando no (reject). A continuación, con una función flecha, se inicia un contador que indicará cuánto tiempo se tarda en resolver lo que sea (en este caso el string, en dos segundos en cada caso). En el caso de las promesas incumplidas la sintaxis es la misma, aunque cambiando el resolve por el reject(o cualquier otra palabra, el asunto es indicar ambas posibilidades de alguna forma).

Una vez declaradas llega el momento de utlizar las promesas. Para ello se usan las palabras reservadas .then y .catch, que están mapeadas a la promesa cumplida e incumplida respectivamente. A continuación se pasa el elemento que nos interesa ejecutar con la promesa:
```
greeting
  .then(data => {
    console.log(data)
  })
  .catch(err => {
    console.error(err)
  })
  ```
  Existe un método abreviado para escribir promesas, que es el método fetch.
  Suele utlizarse en conexiones con APIs. El método fetch se guarda en una variable, y es una buena práctica indicar que estamos hablando de promesas:
  ```
  const PostPromise = fetch("https://api.dailysmarty.com/topics/python")

PostPromise // sobre esa variable se convierte a json y luego se itera para conseguir los datos
  .then(data => data.json())
  .then(data => {
    data.posts.forEach(item=> {
      console.log(item.title);
    });
  })
  ```
  
  Además, las promesas se pueden agrupar. Para eso solamente hay que usar Promise.all(lista de promesas):
  ```
  const greeting = new Promise((resolve, reject) =>{
  resolve('Hi there');
  reject('Oops, bad greeting');
});

const updateAccount = new Promise((resolve, reject) => {
  resolve('Updating last login...');
  reject('Error updating account with login.');
});

const loginActivities = Promise.all([greeting, updateAccount]);

loginActivities.then(res => {
  res.forEach(activity => {
    console.log(activity);
  })
})
```
  
  ## **¿Qué hacen async y await por nosotros?**
  
![](https://codahosted.io/docs/xE8hEJoQ3Z/blobs/bl-AEAgoEVniW/16b4d6df76c51cd717bc7ee85f69f0136efe776b31d860888c034f2373bb538391ee4c4118d7dae5747044435f3fca61832350d84fdc15e4a822e2b7fbe40454cf5a0f2e50c93e649e2d83b5163d8993e7e2dc59e5a025921e738c0b5128a8a39f3b6919)

Usamos la palabra “async” antes de una función para decir que es asíncrona (este tipo de funciones siempre devuelven una promesa). Una función async puede contener una expresión *await*, la cual pausa la ejecución de la función asíncrona y espera la resolución de la promesa pasada y, a continuación, reanuda la ejecución de la función async y devuelve el valor resuelto. Esto evita que encadenemos promesas (porque tendría que ejecutarse todo antes de poder continuar, y eso sería un caos).
```
async function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (Math.random() < 0.5) {
        resolve("Datos obtenidos con éxito");
      } else {
        reject("Error al obtener los datos");
      }
    }, 1000);
  });
}

async function getData() {
  try {
    const data = await fetchData();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

getData();
```

















  