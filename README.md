# JPICUSB 1.1.1

Interface JAVA con API Usb de Microchip

**Autor:** Angel Gonzalez Mejia  
**Versión:** 1.1.1  
**Fecha:** 31 de Octubre de 2025

## Documentación

Información sobre los métodos disponibles en `javadoc/index.html`

## Ejemplo de uso

```java
/*MainClass.java*/
package jpicusbtest;
import jPicUsb.*;

public class MainClass {
    public static void main(String[] args) {
        try {
            iface.load();
        } catch(Exception e) {
        }
        
        try {
            System.out.println("Presione una tecla cuando desee conectarse con el dispositivo.");
            System.in.read();
        } catch (Exception ex) {
            System.out.println(ex.getMessage());
        }
        
        byte[] out = new byte[64];
        out[0] = 99;
        
        try {
            // byte[] QWriteRead(byte[] salida, int writeout, int readin, long timeoutmsec)
            String data_in = new String(iface.QWriteRead(out, 1, 6, 1000), "utf-8");
            if (data_in.length() == 0) {
                System.out.println("No se recibieron datos");
            } else {
                System.out.println("Datos recibidos:" + data_in);
            }
        } catch(Exception ex) {
            System.out.println("ERROR:" + ex.getMessage());
        }
        
        return;
    }
}
```

## Nota

Todos los archivos deben ubicarse en el mismo directorio que el programa principal.
