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
## API

## LOGIN

## Validación de Correo

### Descripción

El siguiente código en Java valida si una dirección de correo electrónico cumple con un conjunto específico de criterios. El método verifica si el correo electrónico pertenece a uno de los dominios permitidos (gmail.com, hotmail.com, yahoo.com, itoaxaca.edu.mx) y sigue el formato adecuado.

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
