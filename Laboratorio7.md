# LABORATORIO 7 - Seguridad

## PARTE I. Spring Security

1. Modifique su proyecto de reservas para incluir protección de seguridad.
   - Puede seguir el tutorial disponible en el siguiente enlace: [Spring Security]([https://spring.io/guides/gs/securing-web](https://www.geeksforgeeks.org/securing-rest-apis-with-springsecurity/)).

2. El tutorial utiliza una base de datos en memoria. Como su proyecto ya cuenta con una base de datos en MongoDB, ajuste las configuraciones necesarias para integrarlo.

3. Aplique mecanismos de cifrado para garantizar que las credenciales de inicio de sesión de los usuarios se almacenen de forma encriptada en la base de datos.

4. Defina roles que permitan visualizar diferentes vistas dentro de la aplicación. Para el sistema de reserva contamos con 2 Administrador y profesor:

## PARTE II. SSL

1. Modifique su proyecto de reservas para incluir certificados SSL, asegurando que las peticiones HTTP sean seguras. Aplique estos certificados a los Endpoints definidos.
   - Puede seguir el tutorial disponible en el siguiente enlace: [Certificado HTTPS autofirmado en Spring Boot](https://www.baeldung.com/spring-boot-https-self-signed-certificate).

## Requisitos de entrega

1. Actualice el plan del proyecto en Azure DevOps.

2. Distribuya las tareas entre los miembros del equipo para asegurar una cobertura completa.

3. Actualice el archivo `README.md` con los cambios necesarios a nivel de diseño, teniendo en cuenta que el diagrama de arquitectura también debe ser actualizado.
