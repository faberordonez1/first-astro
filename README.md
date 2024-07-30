# Instalacion

Antes de iniciar la creacion del proyecto, es importante tener en cuenta que astro, genera una carpeta nuevo con todo lo necesario, por lo que se debe ejecutar el comando en la carpeta padre (Workspace), que va a contener todos los proyectos de astro.

1. Comando iniciar proyecto 
```sh
npm create astro@latest
```

2. Seleccionar opciones deseadas
3. Indicar nombre del proyecto
4. Probando redireccion otra pagina

    Se crea el componente o pagina [about.astro](/first-astro/src/pages/about.astro) y para acceder, en la url unicamente se agrega /about, con esto se accede a la nueva pagina

5. Creando componentes 
 - Se crea el componente [Card.astro](/first-astro/src/components/Card.astro)
 - Se importa en el index.astro de la sigte forma

``` astro
---
import Card from '../components/Card.astro';
---
```
  - En el html del index.astro se usa el nuevo componente Card

```html
<h1>Astro Faber</h1>
<Card />
<Card />
<Card />
```

  - Pasando valores dinamicos al componente Card, 
    1.  En el Card se agrega la sigte linea para recibir las props y se imprime su valor
    2.  En index.astro se le pasa un valor a la propiedad title
```html
---
const { title } = Astro.props
---

<h1>{title ?? 'Sin Title'}</h1>
```

```html
<Card title="Card 1"/>
```

- Se estiliza el componente card dentro del mismo componente con la etiqueta style
```html
<style>
   .card{
     padding: 20px;
     border: 1px solid #ccc;
     border-radius: 5px;
     margin: 10px;
     box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1,)
   }
</style>
```

# Habilitar frameworks

Astro por defecto esta creado para sitios web estaticos, pero tambien se puede habilitar para trabajar con react y otros frameworks, para esto se deben agregar los paquetes necesarios.

## React

Se crea el componente [HelloComponent.jsx](/first-astro/src/components/HelloComponent.jsx)

Se importa el componente en index.astro y se intenta renderizar, pero falla, porque no estan instalados los paquetes del framework react, para usarlo de forma correcta se deben instalar con el sigte comando y luego y, segun corresponda.

```sh
npx astro add react
```

Con esto ya se pueden importar componentes de react

### Habilitando Interactive components
En el componente de react agregamos un boton para disparar una alert de js, pero por defecto no funciona, esto ocurre porque astro por defecto crea web estaticas, entonces se le debe indicar a astro que debe renderizar el componente como cliente, es decir interactivo o con lógica js (componentes hidratados).
```jsx
<button onClick={() => {
        alert('Hello World')
    }}>Click Me</button>
```
Para habilitar esto se debe agregar la propiedad client cuando se usa el componente, junto al estado de la pagina donde se va a cargar el js

```html
<HelloComponent client:visible/>
```

#  🔵🔵🔵🔵🔵🔵 Readme Oficial 🔵🔵🔵🔵🔵🔵

# Astro Starter Kit: Minimal

```sh
npm create astro@latest -- --template minimal
```

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/astro/tree/latest/examples/minimal)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/p/sandbox/github/withastro/astro/tree/latest/examples/minimal)
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/withastro/astro?devcontainer_path=.devcontainer/minimal/devcontainer.json)

> 🧑‍🚀 **Seasoned astronaut?** Delete this file. Have fun!

## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```text
/
├── public/
├── src/
│   └── pages/
│       └── index.astro
└── package.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Feel free to check [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).
