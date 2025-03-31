# API de Sensores

Este proyecto es una API RESTful de la asignatura segurdad de datos en red para gestionar sensores y sus lecturas. Está construido con Node.js, Express y MongoDB.

## Características

- **Gestión de Sensores**: Crear, leer, actualizar y eliminar sensores.
- **Gestión de Lecturas**: Crear, leer y eliminar lecturas de sensores.
- **Filtrado por Fecha**: Obtener lecturas de sensores filtradas por un rango de fechas.
- **Conexión a MongoDB**: Utiliza Mongoose para la conexión y manipulación de datos en MongoDB.
- **Soporte para MQTT**: Publicación y suscripción a eventos de sensores mediante MQTT.
- **Soporte para CoAP**: Interacción con sensores utilizando el protocolo CoAP.

## Estructura del Proyecto

- **models/reading.js**: Define el esquema y modelo de Mongoose para las lecturas de sensores.
- **models/sensor.js**: Define el esquema y modelo de Mongoose para los sensores.
- **server.js**: Configura y ejecuta el servidor Express, define las rutas de la API.
- **testCallback.js**: Contiene un ejemplo de uso de promesas y funciones asíncronas en JavaScript.
- **sensors.json**: Archivo JSON con datos de ejemplo de un sensor.
- **package.json**: Define las dependencias del proyecto.
- **mqtt/**: Contiene la lógica para la integración con MQTT.
- **coap/**: Contiene la lógica para la integración con CoAP.

## Instalación

1. Clona el repositorio:
    ```sh
    git clone <URL_DEL_REPOSITORIO>
    ```
2. Navega al directorio del proyecto:
    ```sh
    cd API_datos
    ```
3. Instala las dependencias:
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

### Sensores

- **GET /sensors**: Obtiene todos los sensores.
- **GET /sensors/:id**: Obtiene un sensor por su ID.
- **POST /sensors**: Crea un nuevo sensor.
- **PUT /sensors/:id**: Actualiza un sensor por su ID.
- **DELETE /sensors/:id**: Elimina un sensor por su ID.

### Lecturas

- **POST /readings**: Crea una nueva lectura.
- **GET /readings/:sensorId**: Obtiene todas las lecturas de un sensor por su ID.
- **DELETE /readings/:sensorId**: Elimina todas las lecturas de un sensor por su ID.
- **GET /readingsTime/:sensorId**: Obtiene lecturas de un sensor filtradas por un rango de fechas.

### MQTT

- **Publicación**: Los sensores publican eventos en un tópico específico.
- **Suscripción**: Los clientes pueden suscribirse a eventos de sensores.

### CoAP

- **GET /coap/sensors**: Obtiene todos los sensores utilizando CoAP.
- **POST /coap/sensors**: Crea un nuevo sensor utilizando CoAP.

## Dependencias

- **express**: Framework web para Node.js.
- **cors**: Middleware para habilitar CORS.
- **body-parser**: Middleware para parsear cuerpos de solicitudes.
- **mongoose**: ODM para MongoDB.
- **moment**: Biblioteca para manipulación de fechas y horas.
- **mqtt**: Cliente MQTT para Node.js.
- **coap**: Cliente y servidor CoAP para Node.js.

## Contribuciones

Las contribuciones son bienvenidas. Por favor, abre un issue o un pull request para discutir cualquier cambio que desees realizar.

## Licencia

Este proyecto está bajo la Licencia MIT.