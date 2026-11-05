# Frontend de Gunfighter

Interfaz React del juego de cartas Gunfighter: cuentas, sala de espera, partidas, amigos, estadísticas y administración.

La descripción del proyecto, arquitectura y requisitos están en el [README principal](../README.md).

## Desarrollo

Con el backend iniciado en el puerto 8080, ejecutar desde esta carpeta:

```sh
npm install
npm start
```

La aplicación se abre en [http://localhost:3000](http://localhost:3000). El proxy de `package.json` dirige las peticiones al backend.

```sh
npm test -- --watchAll=false
npm run build
```

`src/App.js` define las rutas. `src/game/` contiene el juego y `src/matches/` las pantallas de partidas. STOMP y SockJS proporcionan la comunicación con el backend durante el juego.
