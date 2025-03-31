# API de Sensores

Este proyecto es una API RESTful diseñada para gestionar sensores y sus lecturas. Además, incluye soporte para protocolos MQTT y CoAP, autenticación de usuarios mediante JWT, y configuración mediante variables de entorno. Está construido con Node.js, Express y MongoDB.

## Características

- **Gestión de Sensores**: Crear, leer, actualizar y eliminar sensores.
- **Gestión de Lecturas**: Crear, leer y eliminar lecturas de sensores.
- **Filtrado por Fecha**: Obtener lecturas de sensores filtradas por un rango de fechas.
- **Conexión a MongoDB**: Utiliza Mongoose para la conexión y manipulación de datos en MongoDB.
- **Soporte para MQTT**: Publicación, suscripción y comunicación en tiempo real mediante WebSocket.
- **Soporte para CoAP**: Interacción con sensores utilizando el protocolo CoAP.
- **Autenticación con JWT**: Login de usuarios y protección de rutas mediante tokens JWT.
- **Variables de Entorno**: Configuración flexible mediante un archivo `.env`.

## Estructura del Proyecto

- **models/reading.js**: Define el esquema y modelo de Mongoose para las lecturas de sensores.
- **models/sensor.js**: Define el esquema y modelo de Mongoose para los sensores.
- **models/user.js**: Define el esquema y modelo de Mongoose para los usuarios.
- **server.js**: Configura y ejecuta el servidor Express, define las rutas de la API.
- **mqtt/**: Contiene la lógica para la integración con MQTT y WebSocket.
- **coap/**: Contiene la lógica para la integración con CoAP.
- **routes/**: Define las rutas de la API REST.
- **middleware/**: Contiene middlewares como la verificación de JWT.
- **.env**: Archivo para configurar variables de entorno como puertos, claves secretas, etc.

## Instalación

1. Clona el repositorio:
    ```sh
    git clone <URL_DEL_REPOSITORIO>
    ```
2. Navega al directorio del proyecto:
    ```sh
    cd API_datos
    ```
3. Crea un archivo `.env` basado en el archivo `.env.example` y configura las variables necesarias:
    ```env
    PORT=9000
    MONGO_URI=mongodb://localhost:27017/sensores
    JWT_SECRET=tu_secreto
    MQTT_BROKER_URL=mqtt://localhost
    ```
4. Instala las dependencias:
    ```sh
    npm install
    ```

## Uso

1. Asegúrate de tener MongoDB corriendo en `localhost:27017`.
2. Configura los brokers MQTT y CoAP si es necesario.
3. Inicia el servidor:
    ```sh
    node server.js
    ```
4. El servidor estará corriendo en `http://localhost:9000`.

## Endpoints

### Autenticación

- **POST /auth/login**: Inicia sesión y devuelve un token JWT.
    - **Body**: `{ "username": "usuario", "password": "contraseña" }`
- **POST /auth/register**: Registra un nuevo usuario.
    - **Body**: `{ "username": "usuario", "password": "contraseña" }`

### Sensores

- **GET /sensors**: Obtiene todos los sensores.
- **GET /sensors/:id**: Obtiene un sensor por su ID.
- **POST /sensors**: Crea un nuevo sensor.
    - **Body**: `{ "name": "Sensor 1", "type": "temperatura" }`
- **PUT /sensors/:id**: Actualiza un sensor por su ID.
    - **Body**: `{ "name": "Nuevo Nombre" }`
- **DELETE /sensors/:id**: Elimina un sensor por su ID.

### Lecturas

- **POST /readings**: Crea una nueva lectura.
    - **Body**: `{ "sensorId": "id_sensor", "value": 25.5 }`
- **GET /readings/:sensorId**: Obtiene todas las lecturas de un sensor por su ID.
- **DELETE /readings/:sensorId**: Elimina todas las lecturas de un sensor por su ID.
- **GET /readingsTime/:sensorId**: Obtiene lecturas de un sensor filtradas por un rango de fechas.
    - **Query Params**: `start=YYYY-MM-DD&end=YYYY-MM-DD`

### MQTT

- **Publicación**: Los sensores publican eventos en un tópico específico.
    - Ejemplo de tópico: `sensors/<sensorId>/data`
- **Suscripción**: Los clientes pueden suscribirse a eventos de sensores.
- **WebSocket**: Comunicación en tiempo real con clientes mediante WebSocket.

### CoAP

- **GET /coap/sensors**: Obtiene todos los sensores utilizando CoAP.
- **POST /coap/sensors**: Crea un nuevo sensor utilizando CoAP.
    - **Payload**: `{ "name": "Sensor CoAP", "type": "humedad" }`

## Dependencias

- **express**: Framework web para Node.js.
- **cors**: Middleware para habilitar CORS.
- **body-parser**: Middleware para parsear cuerpos de solicitudes.
- **mongoose**: ODM para MongoDB.
- **moment**: Biblioteca para manipulación de fechas y horas.
- **mqtt**: Cliente MQTT para Node.js.
- **coap**: Cliente y servidor CoAP para Node.js.
- **jsonwebtoken**: Manejo de tokens JWT para autenticación.
- **dotenv**: Manejo de variables de entorno.

## Contribuciones

Las contribuciones son bienvenidas. Por favor, abre un issue o un pull request para discutir cualquier cambio que desees realizar.

## Licencia

Este proyecto está bajo la Licencia MIT.