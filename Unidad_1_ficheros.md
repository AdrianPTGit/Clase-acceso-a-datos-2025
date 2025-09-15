# 1. Introducción a los ficheros  

> Un **fichero** es una secuencia de datos almacenados en un dispositivo (disco duro, USB, etc.) para guardar información de forma no volátil.  
  - Puede contener **texto, imágenes, audio, vídeo u otros formatos**.  
  - Generalmente tiene **nombre, extensión y directorio**.  
  - Está formado por **registros**, y estos a su vez por **campos** de distintos tipos.  

---

## 1.1. Tipos de ficheros según su contenido  

- **Texto (caracteres)**  
  - Contienen solo caracteres (ASCII/Unicode).  
  - Legibles y editables con cualquier editor de texto.  
  - Ocupan más espacio que los binarios para la misma información.  

- **Binarios (bytes)**  
  - Contienen datos en forma de bytes (imágenes, música, vídeo).  
  - Requieren programas específicos para abrirse.  

---

## 1.2. Tipos de ficheros según su acceso  

- **Secuenciales**  
  - Los registros se leen y escriben en orden.  
  - No permiten inserciones intermedias.  

- **Directos o aleatorios**  
  - Acceso directo a un registro mediante su dirección lógica.  
  - Requieren registros de tamaño fijo.  

- **Indexados**  
  - Combinan acceso secuencial y directo.  
  - Incluyen:  
    - **Área de índices** → clave + dirección del registro.  
    - **Área de datos** → registros organizados secuencialmente.  
## 1.3. Comparaciones  

### Ficheros Secuenciales  
- **Ventajas**  
  - Rápidos en acceso secuencial.  
  - Mejor aprovechamiento del espacio.  
- **Inconvenientes**  
  - No permiten acceso directo.  
  - La actualización de un registro requiere reescribir todo el fichero.  

### Ficheros Aleatorios  
- **Ventajas**  
  - Acceso rápido a registros concretos.  
- **Inconvenientes**  
  - Relacionar posición y contenido puede ser complejo.  
  - Posible desperdicio de espacio (huecos entre registros).  
# 2. Clase File en Java  

La clase `File` proporciona utilidades para manejar ficheros y directorios:  
- Obtener información (nombre, atributos, rutas).  
- Representar ficheros individuales o conjuntos en un directorio.  
- Crear directorios o rutas completas si no existen.  

> ⚠️ No permite acceder ni modificar el contenido del fichero, solo gestionarlo a nivel de sistema.  

---

## 2.1. Proceso para trabajar con ficheros  

1. **Importar** los paquetes necesarios.  
2. **Crear** un objeto `File` con la ruta del fichero.  
3. **Abrir** el fichero (previo a lectura/escritura).  
4. **Leer y/o escribir** datos.  
5. **Cerrar** el fichero para liberar recursos.  

## 2.2. Métodos importantes

- Para crear un objeto `File`, se puede usar cualquiera de los siguientes constructores: 

| Método                                | Descripción                                                                                                                                                                     |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `File(String directorio/Fichero)`     | Recibe la ruta completa donde está el fichero junto con el nombre. Por defecto, si no se indica, lo busca en la carpeta del proyecto. Puede ser también la ruta a un directorio. |
| `File(String directorio, String nombreFichero)` | Recibe la ruta completa donde está el fichero y el nombre del fichero.                                                                                       |
| `File(File directorio, String fichero)` | Recibe un objeto de tipo File, que hace referencia a un directorio y el nombre del fichero.                                                                  |

- La clase `File` tiene los siguientes métodos que sirven para ficheros y directorios:

| Método                 | Descripción                                                                 |
|-------------------------|------------------------------------------------------------------------------|
| `boolean canRead()`     | Devuelve `true` si el fichero se puede leer.                                |
| `boolean canWrite()`    | Devuelve `true` si el fichero se puede escribir.                            |
| `boolean exists()`      | Devuelve `true` si el fichero/directorio existe.                            |
| `boolean isFile()`      | Devuelve `true` si el objeto `File` corresponde a un fichero normal.         |
| `boolean isDirectory()` | Devuelve `true` si el objeto `File` corresponde a un directorio.             |
| `long lastModified()`   | Devuelve la fecha de la última modificación.                                |
| `String getName()`      | Devuelve el nombre del fichero/directorio.                                  |
| `String getPath()`      | Devuelve la ruta relativa.                                                  |
| `String getAbsolutePath()` | Devuelve la ruta absoluta del fichero/directorio.                        |
| `String getParent()`    | Devuelve el nombre del directorio padre o `null` si no existe.              |


- La clase `File` dispone de los siguientes métodos para el manejo de ficheros:

| Método              | Descripción                                                                                                      |
|----------------------|------------------------------------------------------------------------------------------------------------------|
| `boolean mkdir()`    | Crea un directorio con el nombre indicado en la instanciación del objeto `File`. Solo se crea si no existe.      |
| `String[] list()`    | Devuelve un vector de cadenas de caracteres con los nombres de ficheros y directorios asociados al objeto `File`.|
| `File[] listFiles()` | Devuelve un vector de objetos `File` conteniendo los ficheros que estén dentro del directorio representado.       |

- Hay que tener en cuenta que se puede:
  - indicar el nombre de un fichero **sin la ruta**: se buscará el fichero en el directorio actual.
  - indicar el nombre de un fichero **con la ruta relativa**.
  - indicar el nombre de un fichero **con la ruta absoluta**.

## 2.3. Ejemplos
- Para crear un objeto File existen diferentes constructores según cómo se desee especificar la ruta del archivo:
```java
// Crear un objeto File utilizando una cadena que representa la ruta
File archivo1 = new File("ruta/al/archivo.txt");``
```
```java
// Crear un objeto File utilizando otro objeto File como base y una cadena
// que representa el nombre del archivo o directorio
File directorio = new File("ruta/al/directorio");
File archivo2 = new File(directorio, "archivo.txt");
```
```java
// Supongamos que tenemos la siguiente estructura de carpetas: 
File carpetaActual = new File("."); // carpeta actual
File carpetaPadre = new File(".."); // carpeta superior
File carpetaRaiz = new File("C:/"); // carpeta raíz de la unidad C: en Windows
File carpeta1 = new File("C:/Users"); // carpeta Users unidad C: en Windows
File carpeta2 = new File("../.."); // Superior de la superior
File archivo1 = new File("../img1.png"); // C:/Users/VIRUS/Desktop/img1.png
```
