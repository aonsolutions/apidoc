# Usuario

<!-- 
    ////////////////////////////////////////////////////////////////////////////
    /
    / Obtener datos del usuario
    /
    ////////////////////////////////////////////////////////////////////////////
-->
## Obtener datos del usuario

> Ejemplo: "auth"

```shell
curl --request GET "https://aon.solutions/ms/api/auth"
 -H "session_id:YOURSESSIONID"
```
```json
// Parámetros
{

}
```

> Ejemplo de JSON de respuesta:

```json
// Respuesta
{
  "email"   : "aaaa@aaaa.aa",
  "uuid"    : "xxx",
  "name"    : "aaaa",
  "surname" : "bbbb",
  "document": "XXXXXXXX",
  "phone"   : "666666666",
  "avatar"  : "image url"
}
```

Con este método, obtendremos los datos básicos del usuario.

### HTTP Request

`GET https://aon.solutions/ms/api/auth`

### HTTP Request Header
Parámetros que enviamos en la cabecera

| Name |  Type  | Description |
|------|--------|-------------|
| session_id | string | Token de autenticación del usuario. |


### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
|      |        |             |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| email    | string | Cuenta de correo |
| uuid     | string | "xxx" |
| name     | string | Nombre del usuario |
| surname  | string | Apellido del usuario |
| document | ??? | "XXXXXXXX" |
| phone    | number | Número de teléfono|
| avatar   | string  | Ruta url de la imagen del avatar del usuario |


<!-- 
    ////////////////////////////////////////////////////////////////////////////
    /
    / Cambiar contraseña del usuario autenticado
    /
    ////////////////////////////////////////////////////////////////////////////
-->

## Cambiar contraseña del usuario

> Ejemplo: "password"

```shell
curl --request PUT "https://aon.solutions/ms/api/auth/password"
 -H "session_id:YOURSESSIONID" --data
```
```json
// Parámetros
{
  "oldPassword":"xxxxx",
  "newPassword":"yyyyy"
}
```
> Ejemplo de JSON de respuesta:

```json
// Respuesta
{

}
```

Con este método, se podrá modificar la contraseña del usuario por una nueva.

### HTTP Request

`PUT https://aon.solutions/ms/api/auth/password`

### HTTP Request Header
Parámetros que enviamos en la cabecera

| Name |  Type  | Description |
|------|--------|-------------|
| session_id | string | Token de autenticación del usuario. |

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| oldPassword | string | Contraseña actual utilizada en el registro de Aon Solutions |
| newPassword | string | Nueva contraseña que se utilizará en el registro de Aon Solutions |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
|      |        |             |


<!-- 
    ////////////////////////////////////////////////////////////////////////////
    /
    / Subir avatar del usuario
    /
    ////////////////////////////////////////////////////////////////////////////
-->

## Subir avatar del usuario

> Ejemplo: avatar

```shell
curl --request PUT "https://aon.solutions/ms/api/auth/avatar"
 -H "session_id:YOURSESSIONID" --data
```
```json
// Parámetros
{
  "content"     :"xxxxx", // base64
  "contentType" :"Tipo de archivo"
}
```
> Ejemplo de JSON de respuesta:

```json
// Respuesta
{

}
```
Con este método, subiremos o editaremos la imagen que tiene de avatar el usuario 

### HTTP Request

`PUT https://aon.solutions/ms/api/auth/avatar`

### HTTP Request Header
Parámetros que enviamos en la cabecera

| Name |  Type  | Description |
|------|--------|-------------|
| session_id | string | Token de autenticación del usuario. |

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| content | string | Imagen que se utilizará como avatar del usuario en formato **base64**. |
| contentType | string | Tipo de archivo. [MIME type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types#structure_of_a_mime_type "MIME type") de la [imagen](https://www.iana.org/assignments/media-types/media-types.xhtml#image "MIME type en las imagenes"). |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
|      |        |             |

<aside class="warning">Entiendo que editara y creara la imagen.</aside>
