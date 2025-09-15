# Introducción a los ficheros  

Un **fichero** es una secuencia de datos almacenados en un dispositivo (disco duro, USB, etc.) para guardar información de forma no volátil.  
Puede contener **texto, imágenes, audio, vídeo u otros formatos**.  
Generalmente tiene **nombre, extensión y directorio**.  
Está formado por **registros**, y estos a su vez por **campos** de distintos tipos.  

---

## Tipos de ficheros según su contenido  

- **Texto (caracteres)**  
  - Contienen solo caracteres (ASCII/Unicode).  
  - Legibles y editables con cualquier editor de texto.  
  - Ocupan más espacio que los binarios para la misma información.  

- **Binarios (bytes)**  
  - Contienen datos en forma de bytes (imágenes, música, vídeo).  
  - Requieren programas específicos para abrirse.  

---

## Tipos de ficheros según su acceso  

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
## 1.3 Comparaciones  

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
