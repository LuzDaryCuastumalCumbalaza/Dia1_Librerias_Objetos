# Dia1_Librerias_Objetos
Exploración de las librerías y sus objetos con los comandos básicos en el entorno IBM/AS400

## 🎯 Objetivo
Comprender la estructura de librerías y objetos en IBM i, explorarlos y documentarlos.

## 📚 Teoría repasada
- Librerías como contenedores de objetos.
- Tipos de objetos: PF, LF, PGM, CLP, MSGQ.
- Comandos principales: WRKLIB, WRKOBJ, DSPLIB, DSPOBJD, CRTLIB.

## 🛠️ Práctica realizada
1. Exploré todas las librerías con el comando WRKLIB
2. Revisé los objetos dentro de **QGPL** y otras librerías del sistema.
3. Consulté la información detallada de librerías con `DSPLIB`.

📸 Evidencias

Comandos para trabajar con las Librerias

1.	Comando WRKLIB: El comando permite trabajar con las librerías mostrando las librerias y sus opciones para su gestión.
   
	![WRKLIB en PUB400](1.WRKLIB.png)
   
1.2 WRKLIB *ALL: Este comando muestra todas las librerías del sistema y con las opciones para su gestion.

 
 
 
1.3 WRKLIB (QGPL): Este comando muestra la librería específica QGPL y con las opciones para su gestión

 

 

WRKLIB LIB(*USRLIBL): Este comando visualiza solo las librerías que están en tu User Library List.
 

 
WRKLIB LIB(*CURLIB): Este comando permite visualizar la librería por defecto o  la librería que te asigna el administrador para trabajar, es decir si no se especifica la librería para crear o buscar un objeto empezará a buscar en esta librería antes de revisar las demás librerías de tu lista de usuario (*USRLIBL)  y con las opciones para su gestión.
 

Patrón con * (comodín): permite buscar librerías por un pedazo de nombre  y con las opciones para su gestion.
 
Parámetros adicionales importantes
Además del parámetro LIB, puedes controlar más cosas:
1.	OUTPUT → Cómo mostrar el resultado.
o	* (pantalla interactiva, por defecto).
o	*PRINT (manda la lista a un spool file).
WRKLIB LIB(*ALL) OUTPUT(*PRINT)
 
*Consultando el Spool
 

•	ASP / ASPDEV → control sobre almacenamiento
🔹 ¿Qué es un ASP?
•	ASP = Auxiliary Storage Pool
Es como una unidad lógica de almacenamiento dentro del sistema IBM i.
•	Piensa que el servidor puede tener varios discos duros organizados en grupos, y cada grupo se llama ASP.
•	El sistema los usa para separar datos: unos para el sistema operativo, otros para usuarios, otros para aplicaciones críticas.
🔹 Tipos comunes
1.	*SYSBAS → El almacenamiento base del sistema (donde están QSYS, QGPL, etc.). Permite ver librerías que están en el almacenamiento base
 
2.	ASP numerados (1, 2, 3, …) → Espacios de almacenamiento adicionales configurados.
   

 
4.	IASP (Independent ASP) → ASPs que se pueden montar/desmontar, parecidos a un disco externo.

Comando DSPLIB
Este comando solo permite visualizar la información de una librería especifica y permite ver qué objetos contiene, sus atributos, y algunos detalles del almacenamiento.
  Este comando muestra la lista de librerías de tu sesión.
 
 Este comando muestra todos los objeto que contiene la librería QGPL en este caso.
 

DSPLIB LIB(*CURLIB): Este comando muestra los objetos que tiene la librería por defecto o actual  en este caso FLDC1
 
 
DSPLIB LIB(*LIBL): Este comentario sirve para ver todas las librerías activas en tu sesión, es decir, el “camino de búsqueda” que tu perfil está usando en ese momento.
 

DSPLIB LIB(MYLIB) OUTPUT(*PRINT): Este comando envia al spool el contenido de la librería FLDC1.

 

TRABAJAR CON OBJETOS
Comando WRKOBJ OBJ(QGPL/*ALL)  muestra todos los objetos para trabajar de la librería QGPL.
 

El comando wrkOBJ OBJ(FLDC1/Q*)  usa un comodín * para mostrar aquellos objetos que inicien con Q y el resto no importa.
 
El comando wrkOBJ OBJ(*all/*all)  muestra todos los objetos de todas las librerías en la lista de librerías.
 

*El comando WRKOBJ OBJ(QGPL/*ALL) OBJTYPE(*FILE): muestra de la librería QGPL todos los objetos que sean de tipo FILE.
 
*El comando WRKOBJ OBJ(QGPL/ALL400SP) muestra el objeto específico ALL400SP de la librería QGPL.
 
*El comando WRKOBJ OBJ(QSYS/*ALL) OBJTYPE(*LIB)  Lista solo las librerías del sistema QSYS.
 
El comando WRKOBJ OBJ(QSYS/*ALL) OBJTYPE(*PGM)  muestra de la librería QSYS todos los programa tipo PGM.
 
El comando DSPOBJD OBJ(FLDC1/EJER01) OBJTYPE(*FILE)   solo permite visualizar mas no trabajar con los objetos, en este caso se muestra de la librería FLDC1 el objeto EJER01 de tipo FILE.
DSPOBJD OBJ(FLDC1/EJER01) OBJTYPE(*FILE)
 
 
* El comando DSPOBJD LIB(QGPL) OBJ(*ALL) OBJTYPE(*ALL) OUTPUT(*PRINT) permite enviar la consulata a un archivo SPOOL con los objetos de FLDC

 


✅ Aprendizajes

Ahora comprendo cómo se organizan los objetos dentro de librerías.

Practiqué los comandos básicos de exploración y creación de librerías.

