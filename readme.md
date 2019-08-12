# Documentación Tarea 2-3 SA## Descripción de la tareaRealizar una aplicación SOA para simular los siguientes servicios de carros tipo Uber:* Solicitud del servicio por parte del cliente+ Recepción de solicitud y aviso al piloto- Solicitud de ubicación (rastreo) desde la administración de servicio de carros.Realizado con servicios orquestados por medio de un ESB.## Solución implementadaSe crearon 4 API's diferentes, 3 de ellas son los servicios de cliente, piloto y rastreo, la otra se encarga de orquestar estos 3 servicios funcionando como un ESB.La lógica de la aplicación se desarrolló de la siguiente manera:1. El cliente solicita el servicio de Uber por medio de una interfaz gráfica, en este caso al no ser necesario se utiliza postman como cliente.2. La solicitud del cliente es enviada al ESB que recibe como parámetro el id del cliente que hace la solicitud del servicio.3. El ESB se encarga de enviar esta información al servicio de clientes, que responde al ESB con la información del cliente incluida la ubicación del mismo.4. El ESB tiene ahora la información del cliente que solicitó el servicio, ahora se encargará de enviar la ubicación del cliente al servicio de rastreos para buscar el vehículo más cercano que pueda prestar este servicio.5. El servicio de rastreos recibe la ubicación del cliente y localiza el vehículo más cercano, responde al ESB la ubicación del vehículo y la placa del vehículo que será el encargado de prestar el servicio.6. Ahora el ESB tiene la información del vehículo encargado, por lo que se debe de notificar al piloto que está a cargo de este vehículo, por lo tanto se hace la comunicación con el servicio de Pilotos enviando la placa del vehículo que prestará el servicio para localizar al piloto.7. El servicio de pilotos identifica al piloto que está a cargo del vehículo seleccionado y responde al ESB que piloto ha sido asignado para prestar el servicio.8. El ESB responde al usuario que piloto está a cargo del servicio que solicitó y envía la información del vehículo con su ubicación actual.## Documentación técnica###Herramientas utilizadas* **Lenguaje utilizado:** JavaScript NodeJs 8.12* **Framework:** Express* **S.O:** Windows 10 Pro* **Editor:** Visual Studio Code* **Cliente:** Postam* **Sistema de control de versiones:** GitHub* **Módulos utilizados:** Express, BodyParser, Sync-Request###Instalación:Para la ejecución de las API REST, se debe de hacer en un entorno de ejecución de Node, por lo que es necesario tener instalado *NodeJs*, en cualquier sistema operativo. Como ya se aclaró, se utilizaron diferentes módulos para el funcionamiento del software, por lo que se deben de instalar de la siguiente manera sobre el entorno: `npm install express body-parser sync-request`.###Git:Se utilizó Git como sistema de control de versiones, se puede verificar el código utilizado en el repositorio https://github.com/DanielGarcia097/SA-TareaESB. Se utilizó una sola rama Master, donde se hicieron todos los commit correspondientes versionados.Para obtener el código realizado basta con clonar el repositorio de la siguiente forma:`git clone https://github.com/DanielGarcia097/SA-TareaESB`.###Estándar de código utilizado:El estándar de código utilizado es **JavaScript Standard Style** es una guía de estilos JavaScript, con linter y corrección automática de código. Para la instalación de esta herramienta bastan con `npm install standard --save-dev`.Documentación de la herramienta: https://standardjs.com/readme-esla.html.La belleza de JavaScript Standard Style es qué es simple. Algunas características del estándar de código.* 2 espacios como sangría.* Usar comillas simples en cadenas de texto con la excepción de escapado de texto* No dejar variables sin usar – esta captura toneladas de bugs!* Sin punto y coma