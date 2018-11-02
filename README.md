# proyecto_cc

[![Status](https://img.shields.io/badge/Status-Documenting-green.svg)](https://github.com/jrtrillo/proyecto_cc/blob/master/README.md)
[![Language](https://img.shields.io/badge/Language-Python-blue.svg)](https://www.python.org/)
[![DBMS](https://img.shields.io/badge/DBMS-MongoDB-orange.svg)](https://www.mongodb.com/es)
[![License](https://img.shields.io/badge/License-GPL-red.svg)](https://github.com/jrtrillo/proyecto_cc/blob/master/LICENSE)

## Alumno:
Jose Ramón Trillo Vílchez

## Asigunatura: 
Cloud Computing

## Master: 
Máster Profesionalizante en Ingeniería Informática desarrollado durante el curso 2018/2019

## Enlace a Web: 
https://jrtrillo.github.io/proyecto_cc/

## Descripción del proyecto:
El ciberbullying es una forma de acoso que está en alza durante los últimos años, para poder prevenirlo a una edad temprana se propone realizar un detector de ciberbullying para redes sociales, con el fin de decidir si un comentario contiene palabras o conjuntos de palabras que se pueden calificar de acoso o no.

La red social elegida para realizar este proyecto es la red social denominada Twitter, debido a que con su API se puede obtener el comentario de un perfil público, esto último es muy importante ya que, si el perfil es privado por la Ley Orgánica 15/1999 de 13 de diciembre de Protección de Datos de Carácter Personal, (LOPD) se prohíbe obtener sus comentarios.

La base de datos que se va a utilizar es la base de datos denominada  [bullyingV3.0](http://research.cs.wisc.edu/bullying/data.html), esta base de datos es pública y contiene más de 7000 comentarios de los cuales a día de hoy solo se puede tener acceso a 4293 comentarios.

Por último, el procedimiento para preprocesar y analizar los comentarios va a estar basado en Natural Lenguaje Processing (NLP).

## Arquitectura: 
Aunque para la resolución de este problema se puede escoger cualquier arquitectura ya sea monolítica, basada en el paso de mensajes o basada en microservicios. Se ha decantado por utilizar la arquitectura basada en microservicios por los siguientes motivos:
		
		- Cada microservicio se puede desplegar de forma independiente.
		- Es fácil de entender.
		- Facilita la gestión de equipos multifuncionales y autónomos.

Por otro lado, se va a contar con una cuenta con un servicio cloud donde se almacenarán los datos obtenidos, la base de datos es una base de datos no relacional [MongoDB](https://www.mongodb.com/es).

El sistema tendrá una página principal donde el usuario podrá poner el ID del comentario **público**, si el comentario es vacío o no existe el ID se volverá a mostrar la página o poner un mensaje de error para que introduzca el ID correcto. 

A continuación, se mostrará una serie de posibilidades para transformar los comentarios en una matriz numérica, ya sea transformar con unigramas+stopped, unigramas, bigramas+stopped, etc.

Una vez que se obtiene la matriz, el usuario puede escoger el método para analizar los datos que prefiera ya sea SVM, BBR, KNN, etc.

Por último, se guardará el resultado del comentario obtenido, se actualizará la base de datos y se mostrará por pantalla. Además, el sistema también cuenta con una API REST para poder consultar los datos y otros resultados. 

En resumen, los microservicios van a ser:

	- Microservicio de conexión con la base de datos NoSQL MongoDB.
	- Microservicio de obtención de comentario.
	- Microservicio de tokenización.
	- Microservicio de análisis del comentario.
	- Microservicio de consulta de datos y resultados.

A parte se estudiará la posibilidad de añadir un **microservicio de gestión de usuarios** para la administración de roles, permisos, login, etc. Como nota final se a de añadir que la comunicación entre los microservicios se va a hacer mediante Brokers a partir de [RabbitMQ](https://www.rabbitmq.com/) 

## Lenguaje a utilizar:
El servicio por lo general va a estar escrito en [Python](https://www.python.org/). Dentro de [Python](https://www.python.org/) se va a utilizar un microframework web denominado [flask](http://flask.pocoo.org/). Como añadido se utilizará la librería [mongoAlchemy](https://pythonhosted.org/Flask-MongoAlchemy/) que se utilizará para establecer conexión con la base de datos no relacional. Por otro lado, también se tendrá en cuenta utilizar Javascript para otros módulos.

## Licencia:
La licencia del software a desarrollar es GNU General Public License v3.0