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
## Login - Magic Link

> Ejemplo: "magicLink"

```shell
# El servicio Login es una llamada POST
curl --request POST "https://aon.solutions/ms/api/magicLink"
  --data
```

```json
// Parámetros
{
  "email":"xxx@xxx.xxx"
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

| Name  |  Type  | Description                                  |
|-------|--------|----------------------------------------------|
| email | string | Cuenta de correo registrada en Aon Solutions |


### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
|      |        |             |

<aside class="notice">Enviara un correo al email, si este email esta registrado en Aon Solutions. Con el link que le permite el acceso.</aside>
<aside class="warning">No esta claro el funcionamiento de tratar el valor con el token que llega.</aside>

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
    --data
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
        "registry"          : 66666,
        "parent"            : false,
        "shared"            : false,
        "administration"    : "ALAVA",
        "document"          : "Axxxxxx",
        "active"            : true,
        "type"              : "ENTERPRISE",
        "parentId"          : 666,
        "vatAccrualPayment" : false,
        "domain"            : "Axxxxxx-cau.aonsolutions.org",
        "name"              : "PRUEBA 1",
        "id"                : 666
    }
]
```

Este método devuelve el listado de empresas del usuario.

### HTTP Request

`GET https://aon.solutions/ms/api/company`

`POST https://aon.solutions/ms/api/company`

### HTTP Request Header
Parámetros que enviamos en la cabecera

| Name       |  Type  | Description                         |
|------------|--------|-------------------------------------|
| session_id | string | Token de autenticación del usuario. |

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
|      |        |             |

### Respuesta

| Name              |  Type  | Description                              |
|-------------------|--------|------------------------------------------|
| withholding       | ???    | ??? |
| surcharge         | ???    | ??? |
| registry          | number | ??? |
| parent            | ???    | ??? |
| shared            | ???    | ??? |
| administration    | string | ??? |
| document          | string | Documento identificativo de la empresa   |
| active            | ???    | ??? |
| type              | string | ??? |
| parentId          | number | ??? |
| vatAccrualPayment | ???    | ??? |
| domain            | string | Nombre del dominio de la empresa         |
| name              | string | Nombre de la empresa                     |
| id                | number | ??? |


<aside class="warning">No esta claro los valores que devuelve el metodo.</aside>
<aside class="info">Se necesita el valor de domain para cualquier otra llamada a la API de Aon Solutions. El domain se enviara en la cabecera, como domain_name.</aside>

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
# El servicio Login es una llamada GET o POST
curl --request GET "https://aon.solutions/ms/api/company/approles"
curl --request POST "https://aon.solutions/ms/api/company/approles"
 -H "session_id:YOURSESSIONID"
 -H "domain_name:NOMBRE_DEL_DOMINIO"
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
    "parentDomainApps": [
        "OCR",
        "CONVENIOS",
        "ALMA",
        "AIO",
        "PACK_SUITE"
    ],
    "domainUserRoles": [
        "ADMIN"
    ],
    "domainApps": [
        "OCR",
        "BIDOQ",
        "SELFCONTA",
        "API_SERVICE",
        "PROFESSIONAL_MANAGEMENT",
        "ACCOUNTING",
        "FISCAL",
        "PAYROLL",
        "DOCUMENTAL",
        "COMUNICA",
        "TIMECONTROL",
        "MESSENGER",
        "INVOICE",
        "COMMERCIAL",
        "MARKETING",
        "TREASURY",
        "GROUPWARE",
        "WAREHOUSE"
    ],
    "oldParentDomainModules": [
        "FINANCE_PORTAL",
        "SUITE_PORTAL",
        "DOCUMENT",
        "ACCOUNTING",
        "FISCAL",
        "PAYROLL",
        "PAYROLL_PORTAL"
    ],
    "domainPayer": false,
    "oldUserRoles": [
        "CONFIG",
        "PRODUCT",
        "SALE",
        "PURCHASE",
        "FINANCE",
        "STATISTICS",
        "E_SIGNATURE",
        "FISCAL"
    ],
    "definedUsers": 2,
    "parentDomain": {
        "owner": "aaaa@aaaa.aa",
        "lastAccessUser": "sruesgas",
        "modification_user": "bbbb",
        "aonStatus": "BILLABLE",
        "disableDomainManagement": false,
        "domainType": "CONSULTANCY",
        "creation_user": "bbbb",
        "enableHeredity": false,
        "description": "ASESORIA (DEMOS)",
        "active": true,
        "creation_date": "2015-01-12T10:17:04Z",
        "maxTotalDocumentSize": 100,
        "lastAccessDate": "2023-02-24T10:17:52Z",
        "modification_date": "2021-04-20T11:36:03Z",
        "name": "cau.aonsolutions.org",
        "id": 666,
        "domainManagement": true,
        "maxDocumentSize": 16,
        "maxDefinedUsers": 6
    },
    "oldDomainModules": [
        "ACCOUNTING",
        "FISCAL",
        "PAYROLL",
        "DOCUMENT",
        "CALL_CENTER",
        "CRM",
        "MARKETING",
        "TREASURY",
        "GROUPWARE",
        "WAREHOUSE"
    ],
    "domain": {
        "owner": "aaaa@aaaa.aa",
        "lastAccessUser": "666666",
        "modification_user": "bbbb",
        "aonStatus": "BILLABLE",
        "disableDomainManagement": false,
        "domainType": "ENTERPRISE",
        "creation_user": "",
        "enableHeredity": false,
        "description": "PRUEBA 1",
        "active": true,
        "creation_date": "2021-11-10T09:43:54Z",
        "definedUsers": 2,
        "parentId": 666,
        "maxTotalDocumentSize": 100,
        "lastAccessDate": "2021-11-10T13:40:01Z",
        "modification_date": "2021-11-10T09:57:59Z",
        "name": "Axxxxxx-cau.aonsolutions.org",
        "id": 666,
        "domainManagement": false,
        "maxDocumentSize": 1,
        "maxDefinedUsers": 3
    },
    "parentDomainUserRoles": [],
    "user": {
        "shared": true,
        "phone": "",
        "surname": "",
        "document": "",
        "domain": 666,
        "name": "PRUEBAS",
        "taskHolders": [
            {
                "documentType": "CIF",
                "document": "Axxxxxx",
                "active": true,
                "workgroups": [],
                "documentCountry": "ES",
                "nationality": "ES",
                "domain": {
                    "disableDomainManagement": false,
                    "enableHeredity": false,
                    "active": false,
                    "id": 545,
                    "domainManagement": false
                },
                "legalPerson": true,
                "name": "PRUEBA 1",
                "alias": "",
                "id": 66666,
                "user": 666,
                "confidential": false,
                "status": "ACTIVE"
            }
        ],
        "id": 66666,
        "type": "SHARED",
        "portal": false,
        "login": "66666"
    },
    "maxDefinedUsers": 3,
    "parentUser": false
}
```

Permisos que tiene el usuario.

### HTTP Request

`GET https://aon.solutions/ms/api/company/approles`

`POST https://aon.solutions/ms/api/company/approles`

### HTTP Request Header
Parámetros que enviamos en la cabecera

| Name       |  Type  | Description                         |
|------------|--------|-------------------------------------|
| session_id | string | Token de autenticación del usuario. |
| domainName | string | Nombre del dominio de la empresa    |

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
|      |        |             |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| ??? | string | ??? |

<aside class="warning">No esta claro el funcionamiento real de este metodo.</aside>
