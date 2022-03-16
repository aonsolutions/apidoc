# Autenticación

> Para autenticarse, debes hacerlo con la siguiente llamada al servicio web:

```shell

# El servicio Login es una llamada POST
curl --request POST "https://aon.solutions/ms/api/login"
  --data
```
```json
{
  "email":"xxx@xxx.xxx",
  "password":"xxx"
}
```

> La respuesta devolverá la session_id que deberás utilizar en cada petición a los servicios de Aon Solutions:

```json
{
  "session_id": "234QWEREWRewfq23ehjHF456..."
}  
```

Aon Solutions utiliza un sistema de identificadores de sesión para autorizar a un usuario a realizar llamadas a cualquier servicio web.

### HTTP Request

`POST https://aon.solutions/ms/api/login`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| email | string | Cuenta de correo registrada en Aon Solutions |
| password | string | Contraseña utilizada en el registro de Aon Solutions |

Si el usuario no utiliza este identificador, el servicio devolverá el error “Unauthorized” y se deberá volver a identificar para seguir haciendo uso de los servicios.

<aside class="notice">Se necesita el valor de session_id para cualquier otra llamada a la API de Aon Solutions.</aside>
