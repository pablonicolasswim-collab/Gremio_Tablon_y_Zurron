# Memoria · Gremio de Aventureros

**Código de alumno/a:** #141884  (no pongas tu nombre)

## 1. Mi aventurero
- Usuario que he añadido a la tabla: pablo
- Comando o pasos que he usado para generar el hash:

## 2. Parte 1 · match
¿Has puesto `default` en `etiquetaRango()`? Si, añadi default en etiquetaRango() ¿Qué pasa si llega el rango `'Z'`? Devuelve desconocido ¿Por qué lo prefieres así? Porque asi hay una respuesta aunque llegue un rango no esperado

## 3. Parte 2 · Validación de la URL
Escribe a mano en la barra `tablon.php?rango=Z&oro=hola`. ¿Qué ocurre y qué línea de tu código lo evita? Al escribir tablon.php?rango=Z&oro=hola se muestran las 10 misiones porque el rango no es válido y el oro se toma como 0 y lo evita la línea 133 que comprueba el rango y las líneas 147–151 que validan el oro y devuelven 0 si no es un numero válido

## 4. Parte 3 · Sesión frente a cookie
En `$_SESSION` guardo en el servidor los datos necesarios para mantener la sesión del aventurero, como sus datos de usuario, el zurrón, la fecha de entrada y los mensajes temporales. El navegador solo conserva la cookie de sesión con el identificador que permite a PHP reconocer esa sesión. En las cookies propias guardo datos pequeños y no sensibles que quiero conservar en el navegador, como el tema elegido y, si marco la opción, mi nombre de usuario. No guardo la contraseña. Lo hago así porque las cookies están en el navegador y el usuario puede verlas o modificarlas; por eso no guardo allí información sensible ni los datos de autenticación.

## 5. Parte 3 · Seguridad del login
- Si escribo `' OR '1'='1` como usuario, no inicio sesión por ese intento de inyección. La consulta usa una sentencia preparada con el marcador `:usuario`, así que el texto se trata como un valor y no como parte del SQL. Además, la contraseña se comprueba con `password_verify()`.
- `session_regenerate_id(true)` genera un identificador nuevo al iniciar sesión y elimina el identificador anterior. Así reduzco el riesgo de que alguien reutilice un identificador de sesión que ya conocía antes de que yo iniciara sesión.
- Muestro el mismo mensaje, «Usuario o contraseña incorrectos», tanto si no existe el usuario como si la contraseña no coincide. Así no revelo a quien intenta entrar cuál de esos datos era correcto y dificulto que descubra qué usuarios están registrados.

## 6. Pruebas que he hecho
| Prueba | Resultado esperado | Resultado obtenido |
|---|---|---|
| Entrar en tablon.php sin login | | |
| Login con contraseña mala | | |
| Aceptar la misma misión dos veces | | |
| Cerrar sesión y volver al zurrón | | |
| Cambiar el tema y cerrar sesión | | |

## 7. Dificultades y cómo las he resuelto
