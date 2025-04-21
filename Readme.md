# Laboratorio propiedades de un componente y map

Este laboratorio tiene el objetivo demostrar como cargar hacer un map dinámico de compnentes
## Requisitos Previos

1. Vite
2. Crear una cuenta en [GitHub](https://github.com/).
3. Utilizar un codespace de git hub o un dev container con docker en tu computadora de forma local

---

## Instrucciones Paso a Paso

### 1. Cargando el proyecto

1.1  Instalar los paquetes del proyecto y tailwind

``` bash
npm install
npm install tailwindcss @tailwindcss/vite
```

1.2 Ejecuta react en modo de desarrollo

```
npm run dev -- --host
```

> [!IMPORTANT]
> Se desplegará un pop up en la parte inferior derecha con el mensaje: La aplicación que se ejecuta en el puerto 5173 está disponible. 
> [Ver todos los puertos reenviados] (command:~remote.forwardedPorts.focus) [Abrir en el navegador] [Hacer público] Debes dar click en hacer público

> [!NOTE]
>Si no lograste darle click o no te apareció el pop up en la cinta de terminal, ve a la opción puertos, busca el puerto 5173, da click derecho, selecciona visibilidad de puerto y selecciona público

Abre el proyecto en el navegador web

### 2. Validación

2.1 Agrega un poco de contenido del tailwindcss
Abre el archivo ```my-app/src/Nav.jsx``` y descomenta las linead que tinene el arreglo navigation

Analiza el contenido del div con el id  ```navbar-default```

cambia el contenido por lo siguiente:

```jsx
<ul className="font-medium flex flex-col p-4 md:p-0 mt-4 border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700">
  {navigation.map(e=>
    <li>
      <a href={e.href} className={e.available?"block py-2 px-3 text-white bg-blue-700 rounded-sm md:bg-transparent md:text-blue-700 md:p-0 dark:text-white md:dark:text-blue-500":"block py-2 px-3 text-gray-900 rounded-sm hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent"} aria-current="page">{e.title}</a>
    </li>
  )}     
</ul>

```
2.2 agrega un comentario en el archivo Nav explicando como funciona map en este caso.

### 3. Propiedades de un componente

3.1 Abre el archivo ```Card.jsx``` y agrega el parametro ```props``` a la función
```jsx
function Card({props}){
  //...
}
```
Revisa la siguiente documentación:  [props react doc](https://react.dev/learn/passing-props-to-a-component)

3.2 Implementa las siguientes propiedades: ```image``` en la imagen de la crad, ```title``` para la etiqueta h5, ```paragraph``` para la etiqueta p y ```productRef``` para la referencia del botón

> [!IMPORTANT]
> Pon el valor que está actualmente como ek valor por default

```jsx
import imgDefault from './assets/react.svg'
function Card(props){
return (

<div className="max-w-sm bg-white border border-gray-200 rounded-lg shadow-sm dark:bg-gray-800 dark:border-gray-700">
    <a href="#">
        <img className="rounded-t-lg" src={props.image?props.image:imgDefault} alt="" />
    </a>
    <div className="p-5">
        <a href="#">
            <h5 className="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{props.title?props.title:'Title'}</h5>
        </a>
        <p className="mb-3 font-normal text-gray-700 dark:text-gray-400">{props.paragraph?props.paragraph:'Body description'}</p>
        <a href={props.productRef?props.productRef:'#'} className="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
            View Product
             <svg className="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
            </svg>
        </a>
    </div>
</div>

);
}
export default Card;
```

3.3 Revisa ```App.jsx``` y cambia las propiedades de title, paragraph y carga la url de una imagen del producto que tu quieras

### 4. Reto

Descomenta el arreglo de productos en ```App.jsx``` y haz un map para imprimirlos en cards.

### 5. Guarda los cambios y subelos al repositorio

Guarda los cambios en el historial del repositorio con un commit:

```bash
cd ..
git add my-app
git commit -m "propiedades de los componentes"
git push origin main
```
 > [!TIP]
 > Documentación instalación tailwind: https://tailwindcss.com/docs/installation/using-vite

 > [!TIP]
 > Documentación ejemplos tailwind react: https://tailwindcss.com/plus/ui-blocks/preview