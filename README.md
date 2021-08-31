# client

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).



Se generó un CRUD en VUE-CLI, con componentes de Bootstrap y utilizando Axios, la idea general de este CRUD es mostrar en tablas un listado de usuarios tomados de la API ubicada en https://github.com/Mondin0/trabajo_node_prueba , generando peticiones HTTP sencillas. Puede ocurrir que al momento de querer realizar un PUT o un POST, se muestre por consola un error de CORS, pero esto es debido a que se utiliza en modo local. Queda atado a cambios y variaciones. Para combinar las dos apis se recomienda correr en VSCODE el comando npm run dev para iniciar la api, y en el cmd el comando npm run serve para prender el front, que se encuentra en el puerto 8080.
