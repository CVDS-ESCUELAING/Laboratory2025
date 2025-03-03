# LABORATORIO 5 - CI/CD

## PARTE I. DEVOPS / CI-CD
### Creando los Pipelines (CI - Continous Integration)
Usando el mismo código del proyecto realizado en el laboratorio 4 (generar un repositorio nuevo), para hacer lo siguiente:
1) Subir el nuevo repositorio a GitHub
2) Configurar en github actions un **workflow** que contendrá 3 **jobs**, el primer **job** se llamará **build**, el segundo **test** y el tercero **deploy**, además, este workflow se disparará (events/trigger) **on: pull_request**, para esto puede usar como base [este tutorial](https://qaautomation.expert/2023/06/26/how-to-run-springboot-tests-with-github-actions/) o cualquier otro qué considere. Deberás hacer **steps** o **actions** sobre cada **job** para que se pueda obtener los siguiente:
- **build**: únicamente realizar hasta la fase *compile* de *maven*, es prerrequisito de test.
- **test**: realizar la fase de *verify* y responder ¿se puede lograr que se ejecute sin necesidad de compilar el proyecto?, es dependiente (**needs**) de build para ser ejecutada, y a su vez es prerrequisito par hacer deploy.
- **deploy**: por ahora deberá imprimir en consola "En construcción ...", necesita (**needs**) que se haya ejecutado **test** antes de iniciar.
3) Agregar los siguientes tests
- Dado que tengo 1 reserva registrada, Cuando lo consulto a nivel de servicio, Entonces la consulta será exitosa validando el campo id.
- Dado que no hay ninguna reserva registrada, Cuándo la consulto a nivel de servicio, Entonces la consulta no retornará ningún resultado.
- Dado que no hay ninguna reserva registrada, Cuándo lo creo a nivel de servicio, Entonces la creación será exitosa.
- Dado que tengo 1 reserva registrada, Cuándo la elimino a nivel de servicio, Entonces la eliminación será exitosa.
- Dado que tengo 1 reserva registrada, Cuándo la elimino y consulto a nivel de servicio, Entonces el resultado de la consulta no retornará ningún resultado.
4) Verifica que la ejecución del **workflow** es exitosa, si no lo fuera, modifícalo hasta que ocurra
### Desplegando en Azure usando CI/CD (Continous Deployment / Continous Delivery)
5) En Azure crea un servicio de App Service con recursos que facturen 0 dólares <a href="https://youtu.be/Z4LXJG2CVSw?si=xSsNIOEiL2aNfgvK">(TUTORIAL MINUTO 4:34)</a>
6) Configura el **job deploy** que creaste en el paso 2 y usando el *action* **azure/webapps-deploy@v2** despliega el *jar* generado a tu servicio de App Service
7) Verifica qué el endpoint de la aplicación generado en App Service
8) En este punto la aplicación no debería funcionar, ¿Donde puedes ver el mensaje de error de la aplicación o logs?, (probáblemente está fallando debido a que el puerto usado para despliegue no es el esperado (puerto 80), modifícalo en el **application.properties**)
8) En este punto la aplicación no debería funcionar totalmente debido a qué no hay una base de datos preparada, debes verificar esta situación a través de los logs, crea una base de datos MySQL con facturación de 0 dólares
9) Para utilizar la base de datos, configura los datos de conexión como una o varias variables de entorno tanto en App Service como en el archivo **application.properties** de tu proyecto
10) Prueba nuevamente la aplicación, ya debería estar funcionando! :fireworks: :champagne:

## PARTE II. GRÁFICOS
### Generación de datos por procedimientos
Sobre el mismo proyecto:
1) Agrega un nuevo campo, *prioridad de la reserva(de 1 a 5) donde 1 es baja prioridad y 5 alta*.
2) Genera "proceduralmente" nuevas reservas, aleatoriamente serán entre 100 y 1000 (Corresponden a las reservas de los laboratorios). No se necesita crear ningún tipo de interfaz gráfica para poder llenarla, esta parte de la lógica pertenece al dominio de la capa de servicio.
Recuerde la estructura:
![image](https://github.com/PDSW-ECI/labs/assets/4140058/18de025e-cf76-4deb-9fc2-19c763e473d8)
3) Escoje entre algunas de las bibliotecas de gráficos en javascript y sustente su decisión, algunas que podría considerar son: [d3.js](https://d3js.org/), [c3.js](https://c3js.org/), [chart.js](https://www.chartjs.org/), [Google Charts](https://developers.google.com/chart), entre otras, para sustentar apoyese de instrumentos como las tabla T "pros y cons".
4) Realiza una página nueva en la estructura, esta página será la de "analítica" o "insights", en está página se podrá seleccionar entre las siguientes gráficas:
- Histograma de reservas.
- Número de reservas solicitadas en un tiempo determinado claseificadas por laboratorio
- Promedios de reservas por prioridad.
- Lboratorios por nivel de reserva para comprender cuales tienen más demandas.
> Todas estas gráficas deberán ser debidamente rotuladas con su título, leyenda, etiquetas de ejes con sus unidades y tooltip sobre la serie de datos. Puede escoger entre gráficos de barras, líneas, pie, y sustente su elección.

## ENTREGA
-Deben ajustar las nuevas tereas en su planing de Azure DevOps
- CI/CD: La URL pública de la aplicación hasta la parte I, debe ser mostrada en el laboratorio, el profesor dará visto bueno sobre el README.md del repositorio.
- DATA: URL del repositorio en github funcionando con Mongo.
