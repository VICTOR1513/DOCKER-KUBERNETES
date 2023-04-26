# DOCKER-KUBERNETES
DOCKER KUBERNETES

# PUEBAS-UNITARIAS
Pruebas unitarias con Mokito y Junit


-----------------------------------
Desacargamos Docker Desktop
-----------------------------------
Intall
------------------------------------
powershell administrador:
https://docs.docker.com/desktop/install/windows-install/
wsl --install


Paso 1: Habilitación del Subsistema de Windows para Linux
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart


Paso 3: Habilitación de la característica Máquina virtual
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

Paso 4: Descarga del paquete de actualización del kernel de Linux

Paso 5: Definición de WSL 2 como versión predeterminada
wsl --set-default-version 2
wsl -l -v
--------------------------------------------------------

En windows 10 home gabilitar caracteristicas de virtualizacio: https://docs.docker.com/desktop/troubleshoot/topics/#virtualization

--------------------------------------------------------
CREADENCIALES DOCKER
--------------------------------------------------------

	USER DOCKER:
	User: victor
	pass: Vsc151315

	DDOCKER HUB:
	victorsalazarcruz8@gmail.com
	Vsc151315

--------------------------------------------------------
EMPAQUETAMOS EL MICROSERVICIO A JAR
--------------------------------------------------------

	ENTRAR AL LA CARPETA RAIZ DEL MICROSERVICIO
	cd .\msvc-cursos\
	ls

	EMPAQUETAMOS JAR:
	.\mvnw.cmd clean package

	EMPAQUETAMOS JAR Y SALTA LAS PRUEVAS TEST:
	.\mvnw.cmd clean package -DskipTests

	RUN JAR:
	java -jar nombreApp

--------------------------------------------------------
DOKERIZAMOS MICROSERVICIO
--------------------------------------------------------
	CONFIG DOCKERFILE PRUEBA:
			FROM openjdk:17.0.2
		#CARPETA DE TRABAJO SE LLAMA AP
			WORKDIR /app
		#COPIAMOS A LA CARPETA DE TRABAJO EL JAR
			COPY ./target/msvc-usuarios-0.0.1-SNAPSHOT.jar .
		#EPONEMOS EL PUERTO A UTILIZAR
			EXPOSE 8001
		#EJECUTAR UN COMANDO PARA CORRER EL MICROSERVICIO ESTO NO ES PARTE DE LA IMAGEN SI NO SE EJECUTA CUNSO SE CORRE LA IMAGEN
			ENTRYPOINT ["java", "-jar", "msvc-usuarios-0.0.1-SNAPSHOT.jar"]



IMAGENES

	CREAMOS LA IMAGEN DE DOCKER:
		docker build .
		docker build -t nombreImagen .
		docker build -t nombreImagen . -f .\msvc-usuarios\Dockerfile
 

	VER IMAGENS:
		docker images

	CORRER IMAGEN POR ID, PUERTO EXTERIOR(puerto expuesto para el consumo) y INTERIOR(pueto asignado en dokerfile):
		docker run -p 8000:8001 idImagen




CONTENEDORES

	LISTAR CONTENEDORES:
		docker ps

	LISTAR CONTENEDORES DETENIDOS O PARADOS:
		docker ps -a

	DETENER O PARAR CONTENEDOR:
		docker stop idContenedor

	CORRER CONTENEDOR YA CREADO:
		docker start name

	ELIMINAR CONTENEDOR (Debe estar detenido stop el contenedor):
		docker rm name

	ELIMINAR TODOS LOS CONTENEDOR:
		docker cointaner prune






