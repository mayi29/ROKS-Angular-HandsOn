# ROKS-Angular-HandsOns

# GUIA DE INSTALACIÓN Y DESPLIEGUE DE APP ANGULAR EN OPENSHIFT

_Para el desarrollo de este proyecto se tiene como base el desarrollo de una aplicación basada en el lenguaje de programación angular y su posterior despliegue en un **Cluster de OpenShift** que se encuentra alojado en **IBM Cloud**._

## Despliegue en OpenShift desde IBM Cloud shell: 🚀

_Iniciualmente debe acceder al shell de IBM Cloud desde el siguinete link:_
```
https://cloud.ibm.com/shell
```
_1.	Inicie sesión desde la consola de IBM Cloud Shell, para hacerlo utilizamos el siguiente comando:_
```
ibmcloud login
```
_Si se rechazan sus credenciales, puede que esté utilizando un ID federado. Para iniciar sesión con un ID federado, utilice el distintivo --sso. Consulte Inicio de sesión con un ID federado para obtener más detalles. Una vez instalado, puede acceder a IBM Cloud desde su línea de comandos con el prefijo bx._
```
ibmcloud login --sso
```
_2.	Configure el entorno de trabajo. Para esto debe colocar el siguiente comando en la terminal._
```
ibmcloud target
```
_Si se ve que faltan faltan algunos campos por configurar,  para hacerlo se debe digitar los siguientes comandos._
```
ibmcloud target -r us-east -g openshift-workshop
```
_y por ultimo digitar el siguiente comando:_
```
ibmcloud target --cf
```
_De este modo damos por terminada la configuración inicial para el despliegue de la aplicación._

_3.	Inicie sesión e ingrese desde la CLI de OpenShift al clúster en el que se va a trabajar._

_Este paso se realiza por medio del siguiente comando:_
```
oc login https://c100-e.us-east.containers.cloud.ibm.com:31320 --token=xn9VJ1NhrWktYArWnBH_e25e6ra3uYCuEQ0ZrFrQ-vA
```
_**NOTA: Este comando es único para acceder al cluster que lleva por nombre openshift3.11 el cual se dispuso para el desarrollo de este laboratorio.**_

_Si se desea acceder a otro clúster que tengamos aprovisionado en nuestra cuenta de IBM Cloud se deben realizar los siguientes pasos:_

_•	Ingresar a la plataforma de IBM cloud con sus credenciales de inicio de sesión._

_•	Diríjase al resource list._

_•	Diríjase a la sección de clústers y dar clic en el que se desea acceder._

_•	Se da clic en el botón OpenShift web console._

_•	Ahora en la parte superior derecha se da clic sobre el ID del correo con el que ingresamos y luego en la sección que dice Copy Login Command._


<img width="144" alt="1" src="https://user-images.githubusercontent.com/60987042/76917049-53479180-6890-11ea-91a1-b2c2c9213729.PNG">

_•	Y por último volvemos a la terminal que se estaba utilizando pegamos y damos enter._

_4.	Cree un nuevo proyecto en el cluster de la siguiente manera:_
```
oc new-project <projectname>
```
_**Nota:** Para el **projectname** coloque **openshift + las iniciales de su nombre y apellido.**_

_5.	Acceda al proyecto que acabo de crear de la siguiente manera:_

```
oc project <projectname>
```

_6.	Clone el repositorio de la aplicación que se desea desplegar._

_**App de hello Word en angular:** https://github.com/emeloibmco/AngularHelloWorld_

_**App de listas en angular:** https://github.com/emeloibmco/AngularWebList_

_7.	Desde el Shell de IBM cloud digitar el comando:_

```
Git clone <url_repositorio>
```
_8.	Dirigirse desde a esta carpeta con el comando:_

_•	Para la carpeta del proyecto Hello word:_
```
cd AngularHelloWorld
```
•	Para la carpeta del proyecto listas.
```
cd AngularWebList
```
_9.	Para desplegar la aplicación en OpenShift es necesario escribir el siguiente comando:_
```
npx nodeshift --strictSSL=false --dockerImage=nodeshift/ubi8-s2i-web-app --imageTag=10.x --build.env OUTPUT_DIR=dist/angular-web-app --expose
```

_El resultado de este comando va a ser una respuesta de este tipo, que nos indica que 
la aplicación se desplego correctamente._

<img width="865" alt="2" src="https://user-images.githubusercontent.com/60987042/76918560-9441a500-6894-11ea-954f-62c8076b8903.PNG">

_10.	Para poder acceder al la URL de la aplicación y realizar la verificación de la misma debemos:_

_•Acceder a IBM cloud._

_•Dirigirse al resource list._

_•Dirigirse a la sección de clusters._

_•Ingresar al cluster que lleva por nombre openshift.311._

_•Ingrese a la sección de openshift web console._

_•Buscar el proyecto que creo con sus iniciales y buscar la aplicación que se desplego._

<img width="789" alt="3" src="https://user-images.githubusercontent.com/60987042/76919117-f222bc80-6895-11ea-835e-cb689f2b61bb.PNG">

_Y por último solo faltaría dar clic en el link que lo llevara a la aplicación desplegada._

<img width="688" alt="4" src="https://user-images.githubusercontent.com/60987042/76919471-074c1b00-6897-11ea-95c7-e8675b91ec80.PNG">

_De esta forma se daría por terminado el despliegue de la aplicación angular en openshift._

# _ANEXOS._

_Si se desea realizar el mismo despliegue, pero desde la maquina local se deberían seguir los siguientes pasos:_

### Pre-requisitos 📋

_Paso 1: Instale IBM Cloud CLI._

_Instale la interfaz de la línea de comandos de IBM Cloud así:_

_**Para Mac y Linux ™**_
_Ejecute el siguiente comando en la terminal:_
```
curl -sL https://ibm.biz/idt-installer | bash
```
_**Para Windows™ 10 Pro**_
_Pulse con el botón derecho del ratón el icono de Windows™ PowerShell y seleccione **Ejecutar como administrador**, efectué el siguiente comando:_

```
[Net.ServicePointManager]::SecurityProtocol="Tls12";iex(New-Object Net.WebClient).DownloadString('https://ibm.biz/idt-win-installer')
```

_Paso 2: Verificar la instalación._
_Para verificar que las herramientas de desarrollador y la CLI se han instalado correctamente, ejecute el comando **help**:_

```
ibmcloud dev help
```
### Instalación 🔧

_Una serie de ejemplos paso a paso que te dice lo que debes ejecutar para tener un entorno de desarrollo ejecutandose_

_Dí cómo será ese paso_

```
Da un ejemplo
```

_Y repite_

```
hasta finalizar
```

_Finaliza con un ejemplo de cómo obtener datos del sistema o como usarlos para una pequeña demo_

## Ejecutando las pruebas ⚙️

_Explica como ejecutar las pruebas automatizadas para este sistema_

### Analice las pruebas end-to-end 🔩

_Explica que verifican estas pruebas y por qué_

```
Da un ejemplo
```

### Y las pruebas de estilo de codificación ⌨️

_Explica que verifican estas pruebas y por qué_

```
Da un ejemplo
```

## Despliegue 📦

_Agrega notas adicionales sobre como hacer deploy_

## Construido con 🛠️

_Menciona las herramientas que utilizaste para crear tu proyecto_

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - El framework web usado
* [Maven](https://maven.apache.org/) - Manejador de dependencias
* [ROME](https://rometools.github.io/rome/) - Usado para generar RSS

## Contribuyendo 🖇️

Por favor lee el [CONTRIBUTING.md](https://gist.github.com/villanuevand/xxxxxx) para detalles de nuestro código de conducta, y el proceso para enviarnos pull requests.

## Wiki 📖

Puedes encontrar mucho más de cómo utilizar este proyecto en nuestra [Wiki](https://github.com/tu/proyecto/wiki)

## Versionado 📌

Usamos [SemVer](http://semver.org/) para el versionado. Para todas las versiones disponibles, mira los [tags en este repositorio](https://github.com/tu/proyecto/tags).

## Autores ✒️

_Menciona a todos aquellos que ayudaron a levantar el proyecto desde sus inicios_

* **Andrés Villanueva** - *Trabajo Inicial* - [villanuevand](https://github.com/villanuevand)
* **Fulanito Detal** - *Documentación* - [fulanitodetal](#fulanito-de-tal)

También puedes mirar la lista de todos los [contribuyentes](https://github.com/your/project/contributors) quíenes han participado en este proyecto. 
<img width="144" alt="1" src="https://user-images.githubusercontent.com/60987042/76917049-53479180-6890-11ea-91a1-b2c2c9213729.PNG">
