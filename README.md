# SISTEMA DE UNA CLINICA

## DESCRIPCIÓN

El sistema es una interfaz que, dependiendo de los roles asignados dentro de una base de datos MySQL, permite acceder a ciertas áreas del sistema. Los roles incluyen:

- **Recepcionista**: Agenda citas y registra pacientes.
- **Doctor**: Registra la medicación y actualiza el historial.
- **Administrador**: Controla todas las cuentas de usuario y puede observar el historial de usuarios y pacientes.

## USOS

- **Gestión de Pacientes**: Permite registrar y actualizar información de pacientes, como historial médico, datos de contacto y programación de citas.
- **Programación de Citas**: Facilita la reserva, modificación y cancelación de citas médicas. Incluye una vista de calendario y recordatorios automáticos.
- **Historial Médico**: Proporciona acceso a registros médicos electrónicos, incluyendo diagnósticos previos, tratamientos realizados y resultados de pruebas.

## REQUISITOS

- Base de datos MySQL
- JDK 22
- Coherencia entre el programa y su base de datos
  
# API

## LOGIN

## VALIDACIÓN CORREO

### DESCRIPCIÓN

El siguiente código en Java valida si una dirección de correo electrónico cumple con un conjunto específico de criterios. El método verifica si el correo electrónico pertenece a uno de los dominios permitidos (gmail.com, hotmail.com, yahoo.com, itoaxaca.edu.mx) y sigue el formato adecuado.

### CAMPOS

- **Definición del método**: public boolean validarCorreo(String correo)
- **public**: El método es accesible desde cualquier lugar.
- **boolean**: El método devuelve un valor booleano (true o false).
- **validarCorreo**: Nombre del método, que indica que se utiliza para validar correos electrónicos.
- **String correo**: Parámetro de entrada que representa la dirección de correo electrónico a validar.
- **Expresión regular (regex)**: String regex = "^[a-zA-Z0-9._%+-]+@(gmail\\.com|hotmail\\.com|yahoo\\.com|itoaxaca\\.edu\\.mx)$"
La variable regex contiene una expresión regular que define el formato válido de las direcciones de correo electrónico aceptadas.
- **^[a-zA-Z0-9._%+-]+**: La parte anterior al símbolo @ puede contener letras mayúsculas y minúsculas (a-zA-Z), dígitos (0-9), y ciertos caracteres especiales (._%+-), y debe haber al menos un carácter.
- **@(gmail\\.com|hotmail\\.com|yahoo\\.com|itoaxaca\\.edu\\.mx)$**: La parte después del símbolo @ debe ser uno de los dominios especificados (gmail.com, hotmail.com, yahoo.com o itoaxaca.edu.mx). El símbolo | se utiliza para denotar opciones alternativas, y el símbolo \\ se usa para escapar el punto (.) que tiene un significado especial en las expresiones regulares.
- **Compilación de la expresión regular**: Pattern pattern = Pattern.compile(regex);
Se crea un objeto Pattern utilizando la expresión regular definida, lo que permite utilizarla para realizar coincidencias.
- **Creación de un matcher**: Matcher matcher = pattern.matcher(correo);
Se crea un objeto Matcher utilizando el patrón compilado y la cadena de correo electrónico proporcionada como argumento. Este objeto se utiliza para verificar si la cadena de correo coincide con el patrón.
- **Retorno del resultado**: return matcher.matches();
El método matches() del objeto Matcher se utiliza para comprobar si la cadena de correo cumple con el patrón definido por la expresión regular. Si coincide, devuelve true; de lo contrario, devuelve false.

### CÓDIGO

```java
    public boolean validarCorreo(String correo) {
        String regex = "^[a-zA-Z0-9._%+-]+@(gmail\\.com|hotmail\\.com|yahoo\\.com|itoaxaca\\.edu\\.mx)$";
        Pattern pattern = Pattern.compile(regex);
        Matcher matcher = pattern.matcher(correo);
        return matcher.matches();
    }}
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-33-12-PM.jpg](https://i.postimg.cc/mgHSmWW5/Whats-App-Image-2024-08-03-at-9-33-12-PM.jpg)](https://postimg.cc/JsRJhgnN)
[![Whats-App-Image-2024-08-03-at-9-35-06-PM.jpg](https://i.postimg.cc/x8QKpXYx/Whats-App-Image-2024-08-03-at-9-35-06-PM.jpg)](https://postimg.cc/G8M8Hh4G)

## VALIDACIÓN CONTRASEÑA

### DESCRIPCIÓN

El código proporcionado es un método en Java llamado validarContrasena, que se utiliza para validar si una contraseña cumple con ciertos criterios de seguridad. este método se utiliza para verificar si una contraseña es lo suficientemente fuerte según ciertos criterios de seguridad, como incluir una combinación de letras, números y caracteres especiales, y tener una longitud mínima.

### CAMPOS

- **public**: El método es público, lo que significa que puede ser accedido desde cualquier parte del código.
- **static**: El método pertenece a la clase en lugar de a una instancia de la clase. Esto significa que puede ser llamado sin crear un objeto de la clase.
- **boolean**: El método devuelve un valor de tipo booleano, que puede ser true o false.
- **String contrasena**: El método acepta un argumento de tipo String que representa la contraseña que se desea validar.
- **Expresión Regular (Regex)**:
String regex = "^(?=.*[0-9])(?=.*[a-z])(?=.*[A-Z])(?=.*[@#$%^&+=!]).{8,}$";: Se define una cadena de texto que contiene una expresión regular (regex) utilizada para validar la contraseña. Esta expresión regular tiene los siguientes requisitos:
- **^(?=.*[0-9])**: La contraseña debe contener al menos un dígito (0-9).
- **(?=.*[a-z])**: La contraseña debe contener al menos una letra minúscula (a-z).
- **(?=.*[A-Z])**: La contraseña debe contener al menos una letra mayúscula (A-Z).
- **(?=.*[@#$%^&+=!]): La contraseña debe contener al menos uno de los caracteres especiales mencionados: @#$%^&+=!.
- **.{8,}$**: La contraseña debe tener al menos 8 caracteres de longitud.
- **Compilación y Coincidencia de Patrón**:
Pattern pattern = Pattern.compile(regex);: Se compila la expresión regular en un patrón que puede ser usado para realizar comparaciones.
- **Matcher matcher = pattern.matcher(contrasena);**: Se crea un objeto Matcher para comparar la contraseña proporcionada con el patrón definido.
- **Retorno del Resultado**:
return matcher.matches();: Se devuelve true si la contraseña cumple con todos los criterios definidos en la expresión regular, y false en caso contrario.

### CÓDIGO

```java
public static boolean validarContrasena(String contrasena) {
    String regex = "^(?=.*[0-9])(?=.*[a-z])(?=.*[A-Z])(?=.*[@#$%^&+=!]).{8,}$";
    Pattern pattern = Pattern.compile(regex);
    Matcher matcher = pattern.matcher(contrasena);
    return matcher.matches();
}
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-34-16-PM.jpg](https://i.postimg.cc/mgng2KcB/Whats-App-Image-2024-08-03-at-9-34-16-PM.jpg)](https://postimg.cc/9DGhL8tn)
[![Whats-App-Image-2024-08-03-at-9-34-40-PM.jpg](https://i.postimg.cc/c48DbnQh/Whats-App-Image-2024-08-03-at-9-34-40-PM.jpg)](https://postimg.cc/3dYCyWf0)

## COMPONENTE VER CONTRASEÑA

### DESCRIPCIÓN

Este código es un manejador de eventos en una aplicación Java Swing, donde se controla el comportamiento de un botón para mostrar u ocultar la contraseña en un campo de texto. En resumen, este código permite alternar entre mostrar y ocultar la contraseña en un campo de texto cuando el usuario hace clic en el botón.

### CAMPOS

- **private void btnVerActionPerformed(java.awt.event.ActionEvent evt)**: Es el método que se ejecuta cuando se hace clic en el botón btnVer. El parámetro evt contiene la información del evento.
- **if (textContraseña.getEchoChar() == (char)0)**: Comprueba si el carácter de eco (que oculta el texto en el campo de contraseña) es 0. Si es así, significa que el texto de la contraseña es visible.
- **textContraseña.setEchoChar('●');**: Si el texto es visible, se establece el carácter de eco a ●, lo que oculta el texto de la contraseña.
- **btnVer.setText("Mostrar");**: Cambia el texto del botón a "Mostrar" para indicar que el usuario puede hacer clic en él para ver la contraseña.
- **else**: Si el carácter de eco no es 0, significa que el texto está oculto.
- **textContraseña.setEchoChar((char)0);**: Se establece el carácter de eco a 0, lo que hace que el texto de la contraseña sea visible.
- **btnVer.setText("Ocultar");**: Cambia el texto del botón a "Ocultar" para indicar que el usuario puede hacer clic en él para ocultar la contraseña.

### CÓDIGO

```java
private void btnVerActionPerformed(java.awt.event.ActionEvent evt) {                                       
     if (textContraseña.getEchoChar() == (char)0) {
        textContraseña.setEchoChar('●');
        btnVer.setText("Mostrar"); 
    } else {
        textContraseña.setEchoChar((char)0);
        btnVer.setText("Ocultar"); 
    } 
    }  
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-34-16-PM.jpg](https://i.postimg.cc/mgng2KcB/Whats-App-Image-2024-08-03-at-9-34-16-PM.jpg)](https://postimg.cc/9DGhL8tn)
[![Whats-App-Image-2024-08-03-at-9-34-40-PM.jpg](https://i.postimg.cc/c48DbnQh/Whats-App-Image-2024-08-03-at-9-34-40-PM.jpg)](https://postimg.cc/3dYCyWf0)

## ACTUALIZAR

### DESCRIPCIÓN

Este código Java actualiza un registro en la base de datos de medicaciones usando JDBC. Este método se encarga de asegurar que la información de medicación se actualice adecuadamente y proporciona retroalimentación al usuario en caso de éxito o error.

### CAMPOS

- **Método**: actualizarHistorialMedico
- **Parámetros**:
  int idMedicacion: Identificador único de la medicación a actualizar.
  int idPaciente: Identificador del paciente al que se le ha administrado la medicación.
- **String descripcion**: Descripción de la medicación.
- **String tratamiento**: Detalles del tratamiento asociado.
- **String observaciones**: Observaciones adicionales sobre la medicación.
- **java.sql.Date fechaMedicacion**: Fecha en que se administró la medicación.
SQL:
La consulta SQL utilizada es un UPDATE para modificar un registro en la tabla Medicacion.
- **Conexión**: Se establece una conexión a la base de datos mediante el método getConnection().
- **Preparación de la sentencia**: Se crea un PreparedStatement con la consulta SQL.
- **Asignación de parámetros**: Se establecen los valores de los parámetros en la consulta SQL utilizando los métodos setInt(), setString(), y setDate().
- **Ejecución de la consulta**: Se ejecuta la actualización mediante pstmt.executeUpdate(), que devuelve el número de filas afectadas.
- **Manejo de resultados**:
Si la actualización afecta a al menos una fila, se muestra un mensaje de éxito.
Si no se afecta ninguna fila, se muestra un mensaje de error indicando que no se encontró la medicación con el ID proporcionado.
- **Manejo de excepciones**:
En caso de excepción SQL, se muestra un mensaje de error con la descripción del problema.

### CÓDIGO

```java
    public void actualizarHistorialMedico(int idMedicacion, int idPaciente, String descripcion, String tratamiento, String observaciones, java.sql.Date fechaMedicacion) {
        String sql = "UPDATE Medicacion SET Id_Paciente = ?, Descripcion = ?, Tratamiento = ?, Observaciones = ?, Fecha_Medicacion = ? WHERE Id_Medicacion = ?";
                try (Connection conn = getConnection();
             PreparedStatement pstmt = conn.prepareStatement(sql)) {
             pstmt.setInt(1, idPaciente);
            pstmt.setString(2, descripcion);
            pstmt.setString(3, tratamiento);
            pstmt.setString(4, observaciones);
            pstmt.setDate(5, fechaMedicacion);
            pstmt.setInt(6, idMedicacion);
            int rowsAffected = pstmt.executeUpdate();
            if (rowsAffected > 0) {
                JOptionPane.showMessageDialog(null, "Medicación actualizada con éxito.", "Éxito", JOptionPane.INFORMATION_MESSAGE);
            } else {
                JOptionPane.showMessageDialog(null, "No se encontró la medicación con el ID proporcionado.", "Error", JOptionPane.ERROR_MESSAGE);
            }
            } catch (SQLException e) {
            JOptionPane.showMessageDialog(null, "Error al actualizar la medicación: " + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-36-55-PM.jpg](https://i.postimg.cc/L84Btg6N/Whats-App-Image-2024-08-03-at-9-36-55-PM.jpg)](https://postimg.cc/WhKkj3Zk)
[![Whats-App-Image-2024-08-03-at-9-37-26-PM.jpg](https://i.postimg.cc/nzWw5YMF/Whats-App-Image-2024-08-03-at-9-37-26-PM.jpg)](https://postimg.cc/62d04Zdg)

## ELIMINAR

### DESCRIPCIÓN

El código proporcionado es un método en Java que elimina un registro de medicación de una base de datos utilizando JDBC (Java Database Connectivity). Este método proporciona una manera segura de interactuar con la base de datos y manejar posibles errores o excepciones que puedan ocurrir durante la operación de eliminación.

### CAMPOS

- **Confirmación del usuario**:
El método recibe un parámetro idMedicacion, que representa el ID de la medicación que se quiere eliminar.
Se muestra un cuadro de diálogo de confirmación al usuario con JOptionPane.showConfirmDialog, preguntando si está seguro de que desea eliminar la medicación con el ID especificado. El usuario puede seleccionar "Sí" o "No".
- **Eliminación de la medicación**:
Si el usuario confirma la eliminación (es decir, selecciona "Sí"), se procede a eliminar el registro de la base de datos.
Se define una cadena SQL para eliminar la fila correspondiente de la tabla Medicacion donde Id_Medicacion coincide con el ID proporcionado.
Se utiliza una conexión a la base de datos (Connection) y una declaración preparada (PreparedStatement) para evitar ataques de inyección SQL y manejar de manera segura los parámetros de entrada.
Se establece el valor del parámetro en la declaración preparada con pst.setInt(1, idMedicacion).
Se ejecuta la declaración SQL con pst.executeUpdate(), que devuelve el número de filas afectadas por la operación.
- **Mensajes de resultado**:
Si el número de filas afectadas es mayor que cero, se muestra un mensaje de éxito indicando que la medicación fue eliminada exitosamente.
Si no se afecta ninguna fila (lo que significa que no se encontró una medicación con ese ID), se muestra un mensaje de error indicando que no se encontró la medicación.
Si ocurre una excepción SQL (SQLException) durante el proceso, se muestra un mensaje de error con la descripción del problema.

### CÓDIGO

```java
    public void eliminarHistorialMedico(int idMedicacion) {
        int confirm = JOptionPane.showConfirmDialog(null, "¿Estás seguro de que deseas eliminar la medicación con ID " + idMedicacion + "?", "Confirmación", JOptionPane.YES_NO_OPTION);
            if (confirm == JOptionPane.YES_OPTION) {
            String sql = "DELETE FROM Medicacion WHERE Id_Medicacion = ?";
            try (Connection con = getConnection();
                 PreparedStatement pst = con.prepareStatement(sql)) {
                pst.setInt(1, idMedicacion);
                int rowsAffected = pst.executeUpdate();
                   if (rowsAffected > 0) {
                    JOptionPane.showMessageDialog(null, "Medicación eliminada exitosamente.", "Éxito", JOptionPane.INFORMATION_MESSAGE);
                } else {
                    JOptionPane.showMessageDialog(null, "No se encontró la medicación.", "Error", JOptionPane.ERROR_MESSAGE);
                }
            } catch (SQLException e) {
                JOptionPane.showMessageDialog(null, "Error al eliminar la medicación: " + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
            }
        }
    }
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-37-40-PM.jpg](https://i.postimg.cc/NG4x5xQ5/Whats-App-Image-2024-08-03-at-9-37-40-PM.jpg)](https://postimg.cc/6T8ZPn2X)
[![Whats-App-Image-2024-08-03-at-9-38-15-PM.jpg](https://i.postimg.cc/MZCjZMQv/Whats-App-Image-2024-08-03-at-9-38-15-PM.jpg)](https://postimg.cc/kDy5f5wm)

## MOSTRAR

### DESCRIPCIÓN

Este código Java es un método llamado mostrarDatosHistorialMedico, que se utiliza para mostrar los detalles de un registro de medicación específico en una interfaz gráfica de usuario, probablemente en un componente de tipo JTextArea. Este método es útil en aplicaciones de escritorio que manejan registros médicos, permitiendo a los usuarios visualizar detalles específicos de la medicación almacenados en una base de datos.

### CAMPOS

- **Parámetros del método**:
idMedicacion: un número entero que representa el identificador único de la medicación que se quiere consultar.
textDescripcion: un objeto de tipo JTextArea donde se mostrarán los detalles de la medicación.
- **Consulta SQL**:
La consulta SQL selecciona los campos Id_Paciente, Descripcion, Tratamiento, Observaciones, y Fecha_Medicacion de la tabla Medicacion donde el Id_Medicacion coincida con el valor proporcionado como parámetro.
- **Bloque try con recursos**:
Se establece una conexión con la base de datos usando getConnection().
Se prepara la consulta SQL usando un PreparedStatement para evitar inyecciones SQL.
Se establece el valor del parámetro de la consulta con pst.setInt(1, idMedicacion).
- **Ejecutar la consulta y procesar los resultados**:
La consulta se ejecuta con pst.executeQuery() y se obtiene un ResultSet que contiene los resultados.
Si se encuentra un registro, se extraen los datos del ResultSet y se formatean como un texto, que se establece en el JTextArea (textDescripcion).
Si no se encuentra ningún registro, se muestra un mensaje de error indicando que no se encontró la medicación con el ID proporcionado.
- **Manejo de excepciones**:
Si ocurre una excepción SQLException durante la conexión, preparación de la declaración, ejecución de la consulta o cualquier otra operación relacionada, se captura y se muestra un mensaje de error al usuario usando JOptionPane.

### CÓDIGO

```java
    public void mostrarDatosHistorialMedico(int idMedicacion, javax.swing.JTextArea textDescripcion) {
        String sql = "SELECT Id_Paciente, Descripcion, Tratamiento, Observaciones, Fecha_Medicacion FROM Medicacion WHERE Id_Medicacion = ?";
           try (Connection con = getConnection();
             PreparedStatement pst = con.prepareStatement(sql)) {
            pst.setInt(1, idMedicacion);
            try (ResultSet rs = pst.executeQuery()) {
                if (rs.next()) {
                    textDescripcion.setText(
                        "ID Paciente: " + rs.getInt("Id_Paciente") + "\n" +
                        "Descripción: " + rs.getString("Descripcion") + "\n" +
                        "Tratamiento: " + rs.getString("Tratamiento") + "\n" +
                        "Observaciones: " + rs.getString("Observaciones") + "\n" +
                        "Fecha Medicación: " + rs.getDate("Fecha_Medicacion")
                    );
                } else {
                    JOptionPane.showMessageDialog(null, "No se encontró la medicación con el ID proporcionado.", "Error", JOptionPane.ERROR_MESSAGE);
                }
            }
        } catch (SQLException e) {
            JOptionPane.showMessageDialog(null, "Error al mostrar los datos de la medicación: " + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-40-09-PM.jpg](https://i.postimg.cc/1tcDVDNm/Whats-App-Image-2024-08-03-at-9-40-09-PM.jpg)](https://postimg.cc/qhqN9hLS)

## VALIDACIÓN TEXTO

### DESCRIPCIÓN

Este código es un método en Java que se usa en un componente de interfaz gráfica, como un campo de texto, para restringir la entrada del usuario. 
El propósito de este código es restringir la entrada en el campo de texto textnombrep para que solo se puedan ingresar letras. Cualquier otro carácter, como números o símbolos, será ignorado y no aparecerá en el campo de texto.

### CAMPOS

- **Método textnombrepKeyTyped**: Este es un manejador de eventos que se ejecuta cada vez que se escribe una tecla en un componente de texto (textnombrep). El evento KeyEvent se pasa como argumento.
- **evt.getKeyChar()**: Obtiene el carácter que el usuario está intentando ingresar.
Character.isLetter(char): Verifica si el carácter es una letra (es decir, una letra del alfabeto).
- **evt.consume()**: Si el carácter no es una letra, este método detiene el procesamiento del evento, lo que significa que el carácter no se ingresará en el campo de texto.

### CÓDIGO

```java
private void textnombrepKeyTyped(java.awt.event.KeyEvent evt) {                                     
        if(!Character.isLetter(evt.getKeyChar()))
        evt.consume();
    }    
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-41-35-PM.jpg](https://i.postimg.cc/Gt63c5hH/Whats-App-Image-2024-08-03-at-9-41-35-PM.jpg)](https://postimg.cc/K3rhfQT2)

## VALIDACION NUMERO

### DESCRIPCIÓN

Este código en Java está diseñado para manejar el evento de tipeo (es decir, cuando el usuario presiona una tecla) en un componente gráfico, específicamente un JLabel con el identificador lblNoSeguridadSocial. La función se llama lblNoSeguridadSocialKeyTyped, y su propósito es asegurarse de que solo se puedan ingresar caracteres numéricos en el JLabel. 

### CAMPOS

- **private void lblNoSeguridadSocialKeyTyped(java.awt.event.KeyEvent evt)**: Define un método privado que recibe un evento de teclado (KeyEvent) como argumento. Este evento proporciona información sobre la tecla que se ha presionado.
- **if(!Character.isDigit(evt.getKeyChar()))**: Verifica si el carácter ingresado no es un dígito. evt.getKeyChar() obtiene el carácter que se ha presionado, y Character.isDigit() comprueba si ese carácter es un dígito del 0 al 9.
- **evt.consume();**: Si el carácter no es un dígito, este método consume el evento, lo que significa que el carácter no se procesará ni se mostrará en el componente. Esto efectivamente previene que caracteres no numéricos sean ingresados.

### CÓDIGO

```java
private void lblNoSeguridadSocialKeyTyped(java.awt.event.KeyEvent evt) {                                              
       if(!Character.isDigit(evt.getKeyChar()))
         evt.consume();
    } 
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-42-02-PM.jpg](https://i.postimg.cc/8P3wSBR9/Whats-App-Image-2024-08-03-at-9-42-02-PM.jpg)](https://postimg.cc/7f3S1zQn)

## ENCRIPTACIÓN CONTRASEÑA

### DESCRIPCIÓN

Este método convierte una contraseña en un hash SHA-256 y devuelve el hash en formato hexadecimal, que es una práctica común para almacenar contraseñas de manera segura. Sin embargo, es importante notar que SHA-256 es una función de hash criptográfico y no un método de cifrado reversible. Es decir, no se puede obtener la contraseña original a partir del hash generado. Además, para mayor seguridad, generalmente se recomienda usar un valor "salt" junto con la contraseña antes de hashearla para proteger contra ataques de fuerza bruta y tablas de búsqueda inversa.

### CAMPOS

- **String contrasena**: Es el parámetro de entrada al método, que representa la contraseña en texto plano que se desea cifrar.
- **MessageDigest md**: Es una instancia de la clase MessageDigest, utilizada para calcular el hash de la contraseña utilizando el algoritmo SHA-256.
- **byte[] hash**: Es un arreglo de bytes que almacena el resultado del cálculo del hash de la contraseña.
- **StringBuilder sb**: Es una instancia de StringBuilder utilizada para construir la cadena de texto que representa el hash en formato hexadecimal.

### CÓDIGO

```java
    private String encriptarContrasena(String contrasena) {
        try {
            MessageDigest md = MessageDigest.getInstance("SHA-256");
            byte[] hash = md.digest(contrasena.getBytes());
            StringBuilder sb = new StringBuilder();
            for (byte b : hash) {
                sb.append(String.format("%02x", b));
            }
            return sb.toString();
        } catch (NoSuchAlgorithmException e) {
            throw new RuntimeException("Error al encriptar la contraseña", e);
        }
    }
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-42-40-PM.jpg](https://i.postimg.cc/Kctgz7hC/Whats-App-Image-2024-08-03-at-9-42-40-PM.jpg)](https://postimg.cc/hhPGZdj0)

## ENVIAR CORREO

### DESCRIPCIÓN

Este código es un método privado llamado sendEmail() en Java, que se utiliza para enviar un correo electrónico utilizando el protocolo SMTP (Simple Mail Transfer Protocol). 

### CAMPOS

- **Obtener el transporte SMTP**:
Se obtiene un objeto Transport de la sesión de correo (mSession) utilizando el protocolo "smtp". El objeto Transport es responsable de enviar el mensaje a través del protocolo especificado.
- **Conexión al servidor SMTP**:
El método connect establece una conexión con el servidor SMTP utilizando las credenciales de correo electrónico (emailFrom y passwordFrom). Estos datos representan el correo electrónico del remitente y su contraseña.
- **Enviar el mensaje**:
Se envía el mensaje mCorreo a los destinatarios especificados (mCorreo.getRecipients(Message.RecipientType.TO)). mCorreo es un objeto de tipo Message que contiene la información del correo electrónico, incluyendo los destinatarios, asunto, contenido, etc.
- **Cerrar la conexión**:
Después de enviar el correo, se cierra la conexión con el servidor SMTP.
- **Notificación de éxito**:
Si el correo se envía correctamente, se muestra un cuadro de diálogo informando al usuario que el correo fue enviado con éxito. Además, se limpian algunas variables relacionadas con los archivos adjuntos (lblAdjuntos.setText("") y nombres_archivos = "").
- **Manejo de excepciones**:
El código maneja dos posibles excepciones:
NoSuchProviderException: Se lanza si no se encuentra el proveedor de transporte especificado.
MessagingException: Se lanza si ocurre algún problema con la mensajería (por ejemplo, problemas de autenticación o de red).

### CÓDIGO

```java
    private void sendEmail() {
        try {
            Transport mTransport = mSession.getTransport("smtp");
            mTransport.connect(emailFrom, passwordFrom);
            mTransport.sendMessage(mCorreo, mCorreo.getRecipients(Message.RecipientType.TO));
            mTransport.close();
            JOptionPane.showMessageDialog(null, "Correo enviado");
            lblAdjuntos.setText("");
            nombres_archivos = "";
        } catch (NoSuchProviderException ex) {
            Logger.getLogger(EnvioCorreos.class.getName()).log(Level.SEVERE, null, ex);
        } catch (MessagingException ex) {
            Logger.getLogger(EnvioCorreos.class.getName()).log(Level.SEVERE, null, ex);
        }
    }
```

### EJEMPLO

[![Whats-App-Image-2024-08-03-at-9-44-08-PM.jpg](https://i.postimg.cc/RhxdtMFm/Whats-App-Image-2024-08-03-at-9-44-08-PM.jpg)](https://postimg.cc/Vr4XQPnZ)
[![Whats-App-Image-2024-08-03-at-9-44-31-PM.jpg](https://i.postimg.cc/j52014Q2/Whats-App-Image-2024-08-03-at-9-44-31-PM.jpg)](https://postimg.cc/nsyPj7Wf)

## EJEMPLO DEL FUNCIONAMIENTO COMPLETO
https://youtu.be/5aFZsFDihoI

# AUTORES

* [Sanjuan Vasquez Liz](https://github.com/Liz3456)
* [Sánchez Pérez Carlos Raúl](https://github.com/Carlosprogramacion12)
