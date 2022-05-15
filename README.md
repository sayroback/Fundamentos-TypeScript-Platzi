# Curso de Fundamentos de TypeScript

Descripción por Platzi:
[¡Aprende TypeScript](https://platzi.com/cursos/typescript/), el superset de Microsoft para agregar tipado fuerte a tu código JavaScript! Conoce los datos primitivos y especiales del lenguaje para programar aplicaciones web, agilizar su mantenimiento y evitar la mayoría de errores. Descubre los fundamentos de TypeScript con tu profesor Nicolas Molina.

- Trabaja con números, strings, objetos, arrays y funciones en TypeScript.
- Protege tu código con tipado estático fuerte.
- Integra librerías con o sin soporte de TypeScript a tu aplicación.
- Reflexiona: ¿ahora eres TypeScript Developer o JavaScript "Pro" Developer?.

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
