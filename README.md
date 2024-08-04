# SISTEMA-DE-UNA-CL-NICA

## Descripción

El sistema es una interfaz que, dependiendo de los roles asignados dentro de una base de datos MySQL, permite acceder a ciertas áreas del sistema. Los roles incluyen:

- **Recepcionista**: Agenda citas y registra pacientes.
- **Doctor**: Registra la medicación y actualiza el historial.
- **Administrador**: Controla todas las cuentas de usuario y puede observar el historial de usuarios y pacientes.

## Usos

- **Gestión de Pacientes**: Permite registrar y actualizar información de pacientes, como historial médico, datos de contacto y programación de citas.
- **Programación de Citas**: Facilita la reserva, modificación y cancelación de citas médicas. Incluye una vista de calendario y recordatorios automáticos.
- **Historial Médico**: Proporciona acceso a registros médicos electrónicos, incluyendo diagnósticos previos, tratamientos realizados y resultados de pruebas.

## Requisitos

- Base de datos MySQL
- JDK 22
- Coherencia entre el programa y su base de datos
  
# API

## LOGIN

## Validación de Correo

### Descripción

El siguiente código en Java valida si una dirección de correo electrónico cumple con un conjunto específico de criterios. El método verifica si el correo electrónico pertenece a uno de los dominios permitidos (gmail.com, hotmail.com, yahoo.com, itoaxaca.edu.mx) y sigue el formato adecuado.
### Campos
Definición del método: public boolean validarCorreo(String correo) {
public: El método es accesible desde cualquier lugar.
boolean: El método devuelve un valor booleano (true o false).
validarCorreo: Nombre del método, que indica que se utiliza para validar correos electrónicos.
String correo: Parámetro de entrada que representa la dirección de correo electrónico a validar.
Expresión regular (regex): String regex = "^[a-zA-Z0-9._%+-]+@(gmail\\.com|hotmail\\.com|yahoo\\.com|itoaxaca\\.edu\\.mx)$";
La variable regex contiene una expresión regular que define el formato válido de las direcciones de correo electrónico aceptadas.
^[a-zA-Z0-9._%+-]+: La parte anterior al símbolo @ puede contener letras mayúsculas y minúsculas (a-zA-Z), dígitos (0-9), y ciertos caracteres especiales (._%+-), y debe haber al menos un carácter.
@(gmail\\.com|hotmail\\.com|yahoo\\.com|itoaxaca\\.edu\\.mx)$: La parte después del símbolo @ debe ser uno de los dominios especificados (gmail.com, hotmail.com, yahoo.com, o itoaxaca.edu.mx). El símbolo | se utiliza para denotar opciones alternativas, y el símbolo \\ se usa para escapar el punto (.) que tiene un significado especial en las expresiones regulares.
Compilación de la expresión regular: Pattern pattern = Pattern.compile(regex);
Se crea un objeto Pattern utilizando la expresión regular definida, lo que permite utilizarla para realizar coincidencias.
Creación de un matcher: Matcher matcher = pattern.matcher(correo);
Se crea un objeto Matcher utilizando el patrón compilado y la cadena de correo electrónico proporcionada como argumento. Este objeto se utiliza para verificar si la cadena de correo coincide con el patrón.
Retorno del resultado: return matcher.matches();
El método matches() del objeto Matcher se utiliza para comprobar si la cadena de correo cumple con el patrón definido por la expresión regular. Si coincide, devuelve true; de lo contrario, devuelve false.

### Código

```java
import java.util.regex.Pattern;
import java.util.regex.Matcher;

public class Main {
    
    public static void main(String[] args) {
        // Ejemplo de uso
        System.out.println(validarCorreo("ejemplo@gmail.com"));  // true
        System.out.println(validarCorreo("ejemplo@otro.com"));   // false
    }

    public static boolean validarCorreo(String correo) {
        String regex = "^[a-zA-Z0-9._%+-]+@(gmail\\.com|hotmail\\.com|yahoo\\.com|itoaxaca\\.edu\\.mx)$";
        Pattern pattern = Pattern.compile(regex);
        Matcher matcher = pattern.matcher(correo);
        return matcher.matches();
    }
}
