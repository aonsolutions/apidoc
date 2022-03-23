# Autenticación

## Login

> Para autenticarse, debes hacerlo con la siguiente llamada al servicio web:

```shell

# El servicio Login es una llamada POST
curl --request POST "https://aon.solutions/ms/api/login"
  --data
```
```json
{
  "usermane":"xxx@xxx.xxx",
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
| username | string | Cuenta de correo registrada en Aon Solutions |
| password | string | Contraseña utilizada en el registro de Aon Solutions |

Si el usuario no utiliza este identificador, el servicio devolverá el error “Unauthorized” y se deberá volver a identificar para seguir haciendo uso de los servicios.

<aside class="notice">Se necesita el valor de session_id para cualquier otra llamada a la API de Aon Solutions.</aside>

## Obtener datos del usuario autenticado

> Ejemplo de llamada al servicio “Obtener datos del usuario autenticado”:

```shell
curl --request GET "https://aon.solutions/ms/api/auth"
 -H "session_id:YOURSESSIONID"
```

> Ejemplo de JSON de respuesta:

```json
{
  "email":"aaaa@aaaa.aa",
  "uuid": "xxx",
  "name":"aaaa",
  "surname":"bbbb",
  "document": "XXXXXXXX",
  "phone": "666666666",
  "avatar": "image url"
}
```

### HTTP Request

`GET https://aon.solutions/ms/api/auth`

### HTTP Request Header

| Name |  Type  | Description |
|------|--------|-------------|
| session_id | string | Token de autenticación del usuario. |

## Cambiar contraseña del usuario autenticado

> Ejemplo de llamada al servicio “Cambiar contraseña del usuario autenticado”:

```shell
curl --request PUT "https://aon.solutions/ms/api/auth/password"
 -H "session_id:YOURSESSIONID" --data
```
```json
{
  "oldPassword":"xxxxx",
  "newPassword":"yyyyy"
}
```

### HTTP Request

`PUT https://aon.solutions/ms/api/auth/password`

### HTTP Request Header

| Name |  Type  | Description |
|------|--------|-------------|
| session_id | string | Token de autenticación del usuario. |

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| oldPassword | string | Contraseña actual utilizada en el registro de Aon Solutions |
| newPassword | string | Nueva contraseña que se utilizará en el registro de Aon Solutions |

## Subir una imagen como avatar del usuario autenticado

> Ejemplo de llamada al servicio “Subir una imagen como avatar del usuario autenticado”:

```shell
curl --request PUT "https://aon.solutions/ms/api/auth/avatar"
 -H "session_id:YOURSESSIONID" --data
```
```json
{
  "content":"xxxxx", // base64
  "contentType":"Tipo de archivo"
}
```

### HTTP Request

`PUT https://aon.solutions/ms/api/auth/avatar`

### HTTP Request Header

| Name |  Type  | Description |
|------|--------|-------------|
| session_id | string | Token de autenticación del usuario. |

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| content | string | Imagen que se utilizará como avatar del usuario en formato base64. |
| contentType | string | Tipo de archivo. |
