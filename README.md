# Curso de TypeScript - Platzi

Descripción por Platzi: </br>
[¡Aprende TypeScript,](https://platzi.com/cursos/typescript/) el superset de Microsoft para agregar tipado fuerte a tu código JavaScript! Conoce los datos primitivos y especiales del lenguaje para programar aplicaciones web, agilizar su mantenimiento y evitar la mayoría de errores. Descubre los fundamentos de TypeScript con tu profesor Nicolas Molina.

- Trabaja con números, strings, objetos, arrays y funciones en TypeScript.
- Protege tu código con tipado estático fuerte.
- Integra librerías con o sin soporte de TypeScript a tu aplicación.
- Reflexiona: ¿ahora eres TypeScript Developer o JavaScript "Pro" Developer?.

# Mis notas:

## Introducción a TypeScript

### Atrapando bugs clase (4/24)

Agregar: //@ts-checka en la primer línea de los .js para que TypeScript lo muestre los posibles errores.

### El compilador de TypeScript (5/24)

Ni los navegadores asi como Node pueden leer archivos TypeScrip, debemos hacer un proceso de transpilación para traducir a JavaScript.

En node con el comando:
`npx tsc ruta/archivo.ts` devolverá un archivo .js.
Por defecto este comando transpila ES3, por lo que muchas funcionalidades de ES5/ES6 generaran errores. Para elegir la version de ES solo debemos agregar `--target es5`.

Si queremos agregar un destino a los archivos que genera lo agregamos con `--outDir ruta/`.
También podemos transpilar usando expresiones regulares como `ruta/*.ts`.

Con todo esto podríamos transpilar todos los archivos y enviarlos a una carpeta especifica:
`npx tsc ruta/*.ts --target es6 --outDir outRuta`

### Veamos el TSConfig.json (6/25)

Para generar un archivo TSConfig.json usamos el comando `npx tsc --init`.

## Tipos de datos primitivos

### Qué es el tipado en TypeScript (7/24)

Se agrega el type annotation con `: number` siendo number el tipo de dato que establecemos.
Sintaxis: `const product: number = 12;`
Es recomendado declarar el tipo siembre con minúsculas, aunque se puede hacer con la primer letra mayúscula, esto puede generar errores.

### Tipos inferidos (8/24)

TypeScript también puede inferir tipos de datos.
Ademas reconoce cuando declaras la misma variable aun cuando este en diferentes archivos, si quieres trabajar con el mismo nombre puedes envolver el código en una función anónima que se ejecuta justo después.
`(()=> {})();`

### Numbers (9/24)

Si no inicializas la variable al declararla si debes declarar el tipo de dato, de lo contrario TS no puede inferir. Haciendo esto TS podría alertarnos si es que estamos llamando una variable sin inicializar.

### Booleans (10/24)

No se puede inicializar un booleano como null.
El alcance de la inferencia de TS en en toda asignación no solo en la declaración o inicialización.

### Strings (11/24)

Es recomendable envolver los strings con comillas dobles para evitar un error en el cual el dato asignado posea una comilla simple por ejemplo: I'm.

Back tick’s:
Son muy útiles para guardar bloques de texto y concatenar variables.

### Arrays (12/24)

TS infiere el tipo de datos que se encuentran inicializados en el array, pero si después agregaras otro tipo de dato debes declararlo.

`let mixed: (number | string | boolean | Object)[];`

## Tipos de datos especiales

### Any (13/24)

Con any declarar que pude ser cualquier tipo de dato, quitas la inferencia de las variables. Esto no es recomendado pero es util si es que estas migrando un proyecto en el cuan aun no implementas por completo TS y surgen errores difíciles de complicados de corregir.
Si al traer una variable any ahora queremos asignar un tipo lo declaramos asi:
<code>let myDynamicVar: any;
myDynamicVar = 'Hola';
const rta = (myDynamicVar as string).toLowerCase();</code>

También se puede declarar:
`const rta2 = (<number>myDynamicVar).toFixed();`

### Union Types (14/24)

Añade flexibilidad al tipo de dato. Por ejemplo:
`let userId: string | number;`
Si creamos un condicional que compruebe el tipo de dato que se asigno al escribir nosotros la condición de un tipo de dato TS reconoce que en ese momento deberá ser uno de esos tipo y recomendara según el tipo.

### Alias y tipos literales (15/24)

Podemos crear nuestros propios tipos:
`type UserID = string | number;`

También podemos crear conjuntos de datos permitidos.
<code>
type Sizes = 'S' | 'M' | 'L' | 'XL';
let shirtSize: Sizes;
</code>

### Null y Undefined (16/24)

Podemos forzar que una variable se inicialice en alguno de esos datos y que después acepte otro tipo de dato. Por ejemplo:
`let myNumber: number | null = null;`
Podemos validar muy fácil una variable que puede o no ser nula o indefinida.
`hello += name?.toLowerCase() || 'nobody';`

### Funciones (17/24)

La fecha de puede definir como de tipo Date (con la primer letra mayúscula).
Si queremos volver opcional el que una función reciba un dato se declara con un signo de interrogación antes de los dos puntos. Por ejemplo:
`size?: Sizes`

### Retorno de funciones (18/24)
