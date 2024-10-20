# Base de datos por servicio

- Queremos que cada servicio se ejecute de forma independiente respecto a los otros servicios.
- El esquema de la base de datos podría cambiar inesperadamente.
- Algunos servicios podrían funcionar de forma más eficiente con diferentes tipos de bases de datos (SQL vs NoSQL).


# Comunicación entre servicios

Hay 2 opciones que debemos tener en cuenta para la comunicación entre nuestros servicios:

- **Sync:** Los servicios se comunican con cada uno de los otros usando requests directas.
- **Async:** Los servicios se comunican con los otros usando eventos.


## Comunicación Sync

> [!TIP]
> Ventajas

- Conceptualmente fácil de entender.
- Un servicio que sólo utiliza los otros no necesita una base de datos.

> [!WARNING]
> Desventajas

- Introduce una dependencia entre servicios.
- Si alguna de las solicitudes entre servicios falla, todas las demás solicitudes fallarán.
- La solicitud entera es sólo tan rápida como la solicitud más lenta.
- Puede introducir fácilmente webs de solicitudes.


## Comunicación Async

Aquí siempre tendremos un Event Bus, el cual se encarga de detectar notificaciones o eventos desde los servicios para realizar diferentes acciones.

> [!TIP]
> Ventajas

- Un servicio que sólo utiliza los demás tendrá 0 dependencias.
- El servicio que llama a los demás será extremadamente rápido.

> [!WARNING]
> Desventajas

- Duplicación de datos. Pago por almacenamiento extra + base de datos extra.
- Más difícil de entender.
