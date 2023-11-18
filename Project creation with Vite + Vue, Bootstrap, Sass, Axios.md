# Creazione progetto con Vite + Vue, Bootstrap, Sass, Axios.
# Project creation with Vite + Vue, Bootstrap, Sass, Axios.


## Crea il template di un progetto all'interno della cartella un cui ci troviamo se usiamo il ".", 
## Create the template of a project inside the folder we are in if we use the ".",
```bash
npm create vite@latest . -- --template vue
```


### In alternativa scriviamo il nome della directory e questa verrà creata nella posizione attuale
### Alternatively, we write the name of the directory and it will be created in the current location
```bash
npm create vite@latest name_project -- --template vue
```


## Questo comando installerà tutte le dipendenze necessarie al progetto elencate nel file package.json.
## This command will install all the necessary dependencies for the project listed in the package.json file.
```bash
npm install
```


## Installazione Bootstrap e Popper.js
- Installazione file di Bootstrap nel progetto e di Popper.js che spesso è utilizzata insieme a librerie come Bootstrap per gestire il posizionamento dinamico di popover, dropdown, tooltip e altri componenti che richiedono una precisione nel posizionamento.
## Installing Bootstrap and Popper.js
- Install Bootstrap files in the project and Popper.js which is often used in conjunction with libraries such as Bootstrap to handle the dynamic placement of popovers, dropdowns, tooltips, and other components that require precision in placement.
```bash
npm install bootstrap @popperjs/core
```
- Comando dalla versione npm 5 in poi
- Control from npm version 5 onwards
```bash
npm i --save bootstrap @popperjs/core
```
- Comando precedente alla versione npm 5
- Command prior to npm version 5


## Installazione dipendenza (Sass) per importare e raggruppare correttamente il CSS di Bootstrap.
## Dependency Installation (Sass) to properly import and group Bootstrap CSS.
```bash
npm i --save-dev sass
```

## Installazione Axios
## Install Axios
```bash
npm install axios
```

# Settaggi struttura base e importazioni app
# Basic structure settings and app imports

### Spostare 'style.css' in 'src/assets/scss' e modificare l'estenzione in '.scss'
### Move 'style.css' to 'src/assets/scss' and change the extension to '.scss'

## Modificare l'imporatazione in main.js
## Changing the settings in main.js
```js
import './assets/scss/style.scss'
```


## Importare bootstrap in style.scss
## Import bootstrap to style.scss

```js
@use 'bootstrap'
```


## Importare axios prima dell'export
## Import axios before 'export'
```js
import axios from 'axios';
```

# Esempi:
# Examples:

## Aggiungere la struttura base dell'esportazione dei metodi di Vue dentro il tag <script></script> in 'app.vue'
## Add the basic structure of Vue's method export inside the tag <script></script> in 'app.vue'
```js
export default {
    name: 'App',
    data() {

        return {

        }

    },

    methods: {

    },

    mounted() {

    }

}
```


## Definire le variabili necessaie
## Define the required variables
```js
data() {

        return {
            baseurl: 'http://127.0.0.1:8000/', // URL BASE DI laravel_api
            portfolioApi: 'api/projects',
            projects: [],
        }

    },
```


## Aggiungi la chiamata Axios sul 'mounted' dell'app
## Add the Axios call on the 'mounted' of the app
```js
mounted() {
        // CHIAMATA AXIOS QUANDO App E' MOUNTED
        axios.get(this.baseurl + this.portfolioApi)
            .then(response => {
                console.log(response);
                this.projects = response.data.result.data
            }).catch(err => {
                console.error(err);
            })
    }
```