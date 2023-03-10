## Aplicacion Web en AWS

Dentro de nuestra AWS Cloud, lo primero que necesitamos es un servicio de DNS que resuelva las peticiones que los usuarios realizan a nuestro dominio, en este caso el servicio de AWS es Route 53.
\
Luego utilizamos CloudFront, para mostrar nuestro contenido y tiene muchas ventajas, como baja latencia y alto rendimiento, ademas de generarnos el certificado SSL para nuestra webapp. Para nuestro contenido estatico (.jpgs, .js, etc) seteamos un bucket S3, de manera que CloudFront pueda acceder a esos archivos. Lo implementamos de esta manera ya que S3 tiene alta disponibilidad, es altamente escalable, y reduce los costos en comparacion con tener nuestros archivos en CloudFront. 
\
El ALB (Application Load Balancer) se encarga de distribuir uniformemente el trafico entrante, ya que para lograr una alta disponibilidad implementamos Zonas de Disponibilidad. De esta manera si tenemos problemas con alguna de las zonas, tendriamos otras 2 disponibles.
Dentro de nuestras zonas tenemos la aplicacion web deployada en contenedores, haciendo uso del servicio Fargate que nos permite correr contenedores sin manejar los servidores, junto con ECS que es el servicio de AWS para correr contenedores. No utilizamos EKS (clusters de k8s), ya que no le veo la necesidad, ni tampoco optamos por una instancia EC2 (en vez de Fargate) porque es mas dificil de configurar, no escala tan facil y hay que pagar por las instancias.
\
En nuestras instancias Fargate/ECS habilitamos el Auto-Scaling, para ajustar la capacidad y recursos, asegurandonos que nuestra aplicacion no se caiga cuando tengamos periodos de mucho trafico. Esto es fundamental para asegurarse la Alta Disponibilidad.
\
Luego para las bases de datos tenemos el servicio Amazon RDS la base de datos relacional, y Amazon DynamoDB para bases no-relacionales.
