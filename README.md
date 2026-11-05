# Gunfighter

Aplicación web para jugar duelos de cartas entre dos jugadores, con ambientación del Oeste. Permite crear una partida, esperar a otro jugador y compartir el estado del juego en tiempo real, además de consultar estadísticas, rankings y logros.

![Java](https://img.shields.io/badge/Java-17-ED8B00?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1.1-6DB33F?logo=springboot&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=white)
![H2](https://img.shields.io/badge/H2-Database-09476B)
![WebSocket](https://img.shields.io/badge/WebSocket-Tiempo%20real-4A6FA5)
![JWT](https://img.shields.io/badge/JWT-Auth-8E44AD?logo=jsonwebtokens&logoColor=white)

Proyecto académico desarrollado en equipo en el contexto de Diseño y Pruebas 1 de la Universidad de Sevilla. Parte de la base docente React Petclinic y adapta su arquitectura a un juego multijugador.

## Funcionalidades

- Registro, inicio de sesión y perfiles de jugadores.
- Creación de partidas y sala de espera para dos participantes.
- Juego con cartas, mazos y personajes, con mensajes y actualizaciones mediante WebSocket.
- Historial de partidas, victorias y estadísticas de tiempo de juego.
- Rankings, logros y consulta de perfiles públicos.
- Solicitudes de amistad y consulta de amigos conectados.
- Administración de usuarios, jugadores, partidas y logros.

## Tecnologías y arquitectura

| Capa | Tecnologías |
| --- | --- |
| Interfaz | React 18, React Router, Bootstrap y Reactstrap |
| API | Java 17, Spring Boot 3.1.1 y Bean Validation |
| Seguridad | Spring Security y JWT |
| Datos | Spring Data JPA y H2 en memoria |
| Tiempo real | Spring WebSocket, STOMP y SockJS |
| Pruebas | Spring Boot Test, Spring Security Test, Jest y Testing Library |
| Construcción | Maven Wrapper y npm |

Las operaciones de cuentas y partidas usan una API REST. La comunicación durante las partidas utiliza WebSocket. El backend separa controladores, servicios y repositorios; el frontend agrupa pantallas por funcionalidad.

El paquete Java conserva el nombre `org.springframework.samples.petclinic` por su origen docente; el dominio implementado es Gunfighter.

## Ejecutar en local

Requisitos: JDK 17, Node.js y npm. El `pom.xml` toma Node 18.12.1 como referencia del entorno original. El repositorio incluye Maven Wrapper.

```sh
git clone https://github.com/carlosmdpb/Gunfighter.git
cd Gunfighter
```

En una terminal, iniciar el backend desde la raíz:

```powershell
# Windows / PowerShell
.\mvnw.cmd spring-boot:run
```

```sh
# Linux / macOS
./mvnw spring-boot:run
```

En otra terminal, desde la raíz:

```sh
cd frontend
npm install
npm start
```

- Aplicación: [http://localhost:3000](http://localhost:3000).
- API y Swagger: [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html).

El proxy de React dirige las llamadas al puerto 8080. La base H2 se inicializa al arrancar con los datos definidos en el proyecto.

### Cómo jugar

1. Registrar dos jugadores y abrir sus sesiones en navegadores o perfiles separados.
2. Crear una partida desde una sesión y unirse desde la otra.
3. Recorrer la sala de espera y el juego; consultar después el historial y las estadísticas.

## Estructura

```text
frontend/src/        Juego, partidas, amigos y administración
src/main/java/       API, dominio, seguridad y WebSocket
src/main/resources/  Configuración y datos iniciales
src/test/            Pruebas Java y plan JMeter
pom.xml              Dependencias y construcción
```

Puntos de entrada: [rutas del frontend](frontend/src/App.js), [modelo de partida](src/main/java/org/springframework/samples/petclinic/match/Match.java) y [controlador de partidas y mensajes](src/main/java/org/springframework/samples/petclinic/match/MatchRestController.java).

## Pruebas y construcción

Desde la raíz, `./mvnw test` ejecuta las pruebas Java y `./mvnw package` construye el backend. En Windows, usar `.\mvnw.cmd`.

Desde `frontend/`:

```sh
npm test -- --watchAll=false
npm run build
```

Para incluir la interfaz en el paquete, ejecutar primero `npm run build` en `frontend/` y después el empaquetado con Maven.

## Origen del proyecto

La base procede de React Petclinic de la Universidad de Sevilla, derivada de [Spring Petclinic](https://github.com/spring-projects/spring-petclinic). El `pom.xml` conserva la referencia a Apache License 2.0 del proyecto base.
