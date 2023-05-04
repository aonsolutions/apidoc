# Autenticación

<!-- 
    ////////////////////////////////////////////////////////////////////////////
    /
    / Login
    /
    ////////////////////////////////////////////////////////////////////////////
-->
## Login
<!-- 
    Shell - Estos datos aparecen a la izquierda 
    - Comentario
    - Ejemplo de como llamar al metodo
        - Comentario
        - Llamada curl
            -- Agregar parámetros que se pasan por cabecera: - H "session_id:YOURSESSIONID"
            -- Agregar que se pasan parámetros: --data
    - Parámetros necesarios
    - Respuesta
-->
> Ejemplo: "login"

```shell
# Usamos una llamada POST
curl --request POST "https://aon.solutions/ms/api/login"
  --data
```

```json
// Parámetros
{
  "usermane":"xxx@xxx.xxx",
  "password":"xxx"
}
```

> La respuesta devolverá la session_id que deberás utilizar en cada petición se enviara en la cabecera:

```json
// Respuesta
{
  "session_id": "234QWEREWRewfq23ehjHF456..."
}  
```
<!-- Descripción del método -->
Método usado para iniciar sesión, usando **nombre** y **contraseña**.

La API de Aon Solutions utiliza un sistema de identificadores de sesión para autorizar a un usuario a realizar llamadas a cualquier servicio web.

<!-- Descripción de la llamada -->
### HTTP Request

`POST https://aon.solutions/ms/api/login`

<!-- Descripción de parámetros en la cabecera -->
### HTTP Request Header
Parámetros que enviamos en la cabecera

| Name |  Type  | Description |
|------|--------|-------------|
|      |        |             |

<!-- Descripción de parámetros en el cuerpo -->
### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| username | string | Cuenta de correo registrada en Aon Solutions |
| password | string | Contraseña utilizada en el registro de Aon Solutions |

<!-- Descripción de la respuesta -->
### Respuesta
Si el usuario no utiliza este identificador, el servicio devolverá el error “Unauthorized” y se deberá volver a identificar para seguir haciendo uso de los servicios.

| Name |  Type  | Description |
|------|--------|-------------|
| session_id | string | Token que deberás utilizar en cada petición se enviara en la cabecera. |
<!-- 
    Comentario
-->
<aside class="notice">
Se necesita el valor de session_id para cualquier otra llamada a la API de Aon Solutions.
La session_id se enviara en la cabecera.
</aside>

<!-- 
    ////////////////////////////////////////////////////////////////////////////
    /
    / Login - Magic link
    /
    ////////////////////////////////////////////////////////////////////////////
-->
## Login - Magic link

> Ejemplo: "magicLink"

```shell

# El servicio Login es una llamada ????
curl --request ???? "https://aon.solutions/ms/api/magicLink"
  --data
```

```json
// Parámetros
{
  "usermane":"xxx@xxx.xxx"
}
```

> Ejemplo de JSON de respuesta:

```json
// Respuesta
{

}
```

Este método lo que hace es enviar un mail con un link para iniciar sesión en la aplicación.

### HTTP Request

`POST https://aon.solutions/ms/api/magicLink`

### HTTP Request Header
Parámetros que enviamos en la cabecera

| Name |  Type  | Description |
|------|--------|-------------|
|      |        |             |

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| username | string | Cuenta de correo registrada en Aon Solutions |


### Respuesta


| Name |  Type  | Description |
|------|--------|-------------|
| ??? | string | ??? |

<aside class="warning">No esta claro el funcionamiento real de este metodo.</aside>
<aside class="notice">Se necesita el valor de session_id para cualquier otra llamada a la API de Aon Solutions.</aside>

<!-- 
    ////////////////////////////////////////////////////////////////////////////
    /
    / Listado de empresas
    /
    ////////////////////////////////////////////////////////////////////////////
-->
## Listado de empresas

> Ejemplo: "company"

```shell

# El servicio Login es una llamada GET o POST
curl --request GET "https://aon.solutions/ms/api/company"
curl --request POST "https://aon.solutions/ms/api/company"
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
[
    {
        "withholding"       : false,
        "surcharge"         : false,
        "registry"          : 702378,
        "parent"            : false,
        "shared"            : false,
        "administration"    : "ALAVA",
        "document"          : "A54212356",
        "active"            : true,
        "type"              : "ENTERPRISE",
        "parentId"          : 343,
        "vatAccrualPayment" : false,
        "domain"            : "a54212356-cau.aonsolutions.org",
        "name"              : "PRUEBA BIDOQ 1",
        "id"                : 545
    }
]
```

Este método devuelve el listado de empresas del usuario.

### HTTP Request

`GET https://aon.solutions/ms/api/company`

`POST https://aon.solutions/ms/api/company`

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
| withholding       | ???    | ??? |
| surcharge         | ???    | ??? |
| registry          | number | ??? |
| parent            | ???    | ??? |
| shared            | ???    | ??? |
| administration    | string | ??? |
| document          | string | Documento identificativo de la empresa |
| active            | ???    | ??? |
| type              | string | ??? |
| parentId          | number | ??? |
| vatAccrualPayment | ???    | ??? |
| domain            | string | ??? |
| name              | string | Nombre de la empresa |
| id                | number | ??? |


<aside class="warning">No esta claro el funcionamiento real de este metodo.</aside>
<aside class="info">Valores que se usara en el resto de llamadas.</aside>

<!-- 
    ////////////////////////////////////////////////////////////////////////////
    /
    / Permisos del usuario
    /
    ////////////////////////////////////////////////////////////////////////////
-->
## Permisos del usuario

> Ejemplo: "approles"

```shell

# El servicio Login es una llamada ????
curl --request ???? "https://aon.solutions/ms/api/approles"
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

}
```

Permisos que tiene el usuario.

### HTTP Request

`???? https://aon.solutions/ms/api/approles`

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
| ??? | string | ??? |

<aside class="warning">No esta claro el funcionamiento real de este metodo.</aside>
