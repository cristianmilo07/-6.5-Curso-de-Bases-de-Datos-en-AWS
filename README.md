# -6.5-Curso-de-Bases-de-Datos-en-AWS

_____________________________________________________________________
![](https://static.platzi.com/media/courses/og-aws-database.png)
_____________________________________________________________________
### Introducción al documento
_____________________________________________________________________
El contenido de este documento esta basado en el curso del mismo nombre dictado por Mauro Parra Miranda en Platzi.

**Table of Contents**

[TOCM]

[TOC]

# 1. Qué aprenderás sobre bases de datos en AWS

Bienvenido al Curso de Bases de Datos en AWS de Platzi. Vamos a aprender sobre los servicios de bases de datos relacionales en AWS, principalmente el servicio de RDS, y sobre el servicio de bases de datos no relacionales en AWS: DynamoDB.

Esta vez nuestro profesor será Carlos Andrés Zambrano, que tiene más de 4 años de experiencia trabajando con AWS.

# 2. Características de Relational Database Service (RDS)

RDS (Relational Database Service) es un servicio de AWS enfocado a bases de datos relacionales con compatibilidad a 6 motores de bases de datos: Amazon Aurora, MySQL, MariaDB, PostgreSQL, Oracle y Microsoft SQL Server, cada uno con sus características, integraciones y limitaciones.

Entre sus características principales podemos destacar los backups automáticos con un tiempo de retención de hasta 35 días, es decir, si encontramos algún problema con nuestras bases de datos podemos restablecerlas a la hora, minuto y segundo que necesitemos dentro del periodo de retención. Recuerda que por defecto este periodo es de 7 días. También tenemos la opción de hacer backups manuales, podemos tomar snapshots manuales en cualquier momento si nuestra aplicación lo necesita. Además, AWS por defecto tomará un snapshot final de nuestras bases de datos antes de eliminarlas, así podremos restablecerla si tenemos algún inconveniente.

Todas las bases de datos relacionales utilizan un sistema de almacenamiento, si la carga de lectura y escritura son constantes, el sistema General Purpose funciona muy bien, sin embargo, podemos utilizar el sistema Provisioned Storage cuando requerimos de altas cantidades de consumo y operaciones de disco.

RDS es un sistema completamente administrado, esto quiere decir que AWS reduce nuestra carga operativa automatizando muchas tareas de nuestra base de datos, por ejemplo, las actualizaciones. A nivel de seguridad contamos con muchas opciones, una de ellas es la posibilidad de encriptar nuestra base de datos para que solo nosotros y las personas o roles que especifiquemos tengan acceso.

También tenemos integración con otros servicios de AWS, por ejemplo, IAM para administrar a los usuarios, roles, grupos y políticas de conexión a la base de datos por medio de tokens con máximo 20 conexiones por segundo (recomendado para escenarios de prueba), o la integración de Enhanced monitoring para hacer monitoreo en tiempo real nuestras bases de datos (recuerda que además de subir el precio, no está disponible para instancias small).

Lecturas recomendadas

https://docs.aws.amazon.com/rds/index.html

# 3. Desplegando nuestra primer base de datos

No me gusta Amazon, le da la espalda a estudiantes que quieren aprender y no tienen tarjeta de credito.

Si eres de Colombia, crea una cuenta de Daviplata (Por el celular lo puedes hacer), es facil de hacer. Cuando la crees, habrá una opción de crear una tarjeta virtual, no me acuerdo si debes meter dinero, pero no es demasiado, con 5000 o 10000 funciona. Cuando tengas la tarjeta, podras hacer el proceso de inscripción de AMAZON. Daviplata y la tarjeta virtual son cuentas aparte, eso creo.
Es posible que hallan actividades que necesiten hacer cosas de pago, pero trata de hacer todo con los servicios gratuitos. Lo importante es hacer lo que mas se pueda.

Todo lo contrario, sumado al comentario anterior se puede hacer esto para tener un mayor acceso
https://aws.amazon.com/education/awseducate/

# 4. Conexión gráfica a nuestra base de datos

En esta clase vamos a conectarnos a la base de datos que creamos en la clase anterior usando la herramienta MySQL Workbench, que nos permite ejecutar y visualizar nuestros comandos muy fácilmente.

Cuando utilizamos el servicio RDS con el motor de MySQL podemos crear multiples bases de datos con un solo endpoint (una sola conexión), ya que entre las características de este motor encontramos la cantidad de bases de datos ilimitada. Obviamente, debemos tener en cuenta que nuestras instancias deberían soportar la cantidad de bases de datos que vamos a utilizar, y las herramientas de monitoreo nos pueden ayudar a medir esta relación de tamaño y rendimiento.

Recuerda que si necesitamos un permiso de usuarios diferente para cada base de datos vamos a necesitar configuraciones diferentes en las keys (llaves de acceso) de nuestra instancia.

Lecturas recomendadas

MySQL :: MySQL Workbench

https://www.mysql.com/products/workbench/

# 5. Creación de una tabla

Tengan mucho cuidado con el presupuesto y especialmente con servicios como Glue, Kinesis y Managed Streaming for Apache Kafka. Yo estuve activa en la plataforma por 14 días mientras desarrollaba las actividades del curso y, al finalizar el mes, me generaron una factura por 785 dólares, por lo que me tocó abrir una disputa en AWS.

# 6. Conexión por consola a nuestra base de datos

En esta clase vamos a conectarnos a nuestra base de datos por medio del bash de Linux. Para esto, debemos crear la instancia de un servidor de AWS con un grupo de seguridad que posteriormente vamos a configurar para que la base de datos y el servidor sean accesibles entre ellos.

El desafió de esta clase es identificar al menos 2 características de RDS que actualmente no tenemos en otros sistemas bases de datos.
