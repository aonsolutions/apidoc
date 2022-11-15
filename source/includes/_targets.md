# Clientes potenciales

Métodos para la obtención de clientes potenciales

## Obtener clientes potenciales

Obtención de los clientes potenciales.

```shell

# El servicio 'targets' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/target"
curl --request POST "https://aon.solutions/ms/api/target"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

> Ejemplo de JSON de respuesta:

```json
[
  {
    "surcharge": false,
    "withholding": false,
    "modification_user": "admin",
    "documentType": "CIF",
    "creation_user": "admin",
    "document": "B12345678",
    "advertising": "ALLOWED",
    "creation_date": 1487584437000,
    "documentCountry": "ES",
    "nationality": "ES",
    "domain": {
      "disableDomainManagement": false,
      "enableHeredity": false,
      "active": false,
      "id": 5,
      "domainManagement": false
    },
    "legalPerson": true,
    "scope": {
      "domain": 5,
      "name": "aon /CENTRAL",
      "description": "aon /CENTRAL",
      "id": 51
    },
    "modification_date": 1652975243000,
    "name": "NAME CUSTOMER",
    "alias": "test.aonsolutions.net",
    "tariff": {
      "purchase": false,
      "discount": 0,
      "active": false
    },
    "id": 660234,
    "transaction": "NATIONAL",
    "confidential": false,
    "status": "ACTIVE"
  }
]
```

### HTTP Request

`GET https://aon.solutions/ms/api/target`

### Parámetros (Opcionales)

| Name   | Type   | Description                                                                                                            |
| ------ | ------ | ---------------------------------------------------------------------------------------------------------------------- |
| status | array  | Estados.<br/>Valores permitidos:<ul><li>ACTIVE (Activo)</li><li>INACTIVE (Inactivo)</li><li>CLOSED (Cerrado)</li></ul> |
| value  | string | Filtrar por (Documento, Nombre, Alias)          

### Obtener un registro

`GET https://aon.solutions/ms/api/target/{$id}`


### Parámetros para obtener un registro (Opcionales)

| Name   | Type   | Description                                                                                                            |
| ------ | ------ | ---------------------------------------------------------------------------------------------------------------------- |
| id     | number    |  Identificador del cliente                                                                                          |
| document  | string | Filtrar por Documento, Nombre                                                                           |
| additional_info | array | Información adicional. <br/>Valores permitidos:<ul><li>ADDRESSES (Direcciones)</li><li>MEDIA (Correos, Teléfonos)</li><li>BANKS (Bancos)</li><li>PAYMETHOD (Métodos de pagos)</li><li>RSEGMENT (Segmentos)</li></ul> |  

### Respuesta

| Name            | Type    | Description               |
| --------------- | ------- | ------------------------- |
| surcharge       | boolean | Recargos                  |
| withholding     | boolean | Retenciones               |
| documentType    | string  | Tipo de documento         |
| document        | string  | NIF                       |
| documentCountry | string  | País del documento        |
| advertising     | string  | Tipo de publicidad        |
| nationality     | string  | Nacionalidad              |
| domain          | object  | Dominio                   |
| name            | string  | Nombre                    |
| alias           | string  | Alias                     |
| id              | number  | Identificador del cliente |
| confidential    | boolean | Confidencial              |
| transaction     | string  | Tipo de transacción       |
| status          | string  | Estado del cliente        |

## Guardado clientes potenciales

Guardar cliente potencial

```shell

# El servicio 'target' es una llamada POST
curl --request POST "https://aon.solutions/ms/api/target"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

```json
{
  "surcharge": false,
  "withholding": false,
  "documentType": "CIF",
  "document": "B12345678",
  "advertising": "ALLOWED",
  "documentCountry": "ES",
  "nationality": "ES",
  "domain": {
    "id": 5
  },
  "legalPerson": true,
  "scope": {
    "id": 51
  },
  "name": "NAME CUSTOMER",
  "alias": "test.aonsolutions.net",
  "transaction": "NATIONAL",
  "confidential": false,
  "status": "ACTIVE"
}
```

### HTTP Request

`POST https://aon.solutions/ms/api/target`

#### Actualizar registro

`PUT https://aon.solutions/ms/api/target/${id}`

### Parámetros

| Name            | Type                                            | Description                                                                                                                                                              |
| --------------- | ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id              | int                                             | Identificador .                                                                                                                                                          |
| domain          | object                                          | dominio al que pertenece el cliente                                                                                                                                      |
| document        | string                                          | NIF del cliente                                                                                                                                                          |
| documentCountry | string                                          | País del documento.                                                                                                                                                      |
| documentType    | string                                          | Tipo de documento.<br/>Valores permitidos:<ul><li>NIF</li><li>CIF</li><li>NIE</li><li>PASSPORT</li><li>WORK_PERMIT</li><li>COMMUNITY_CARD</li><li>OTHER</li></ul>        |
| name            | string                                          | Nombre / Razón social del cliente.                                                                                                                                       |
| alias           | string                                          | Alias del cliente.                                                                                                                                                       |
| legalPerson     | boolean                                         | Cierto si es persona jurídica.                                                                                                                                           |
| nationality     | string                                          | Nacionalidad del cliente.                                                                                                                                                |
| confidential    | boolean                                         | Cierto si el cliente es confidencial.                                                                                                                                    |
| global          | boolean                                         | Cierto si el cliente es de global.                                                                                                                                       |
| dirty           | boolean                                         | Cierto si hay que modificar el cliente.                                                                                                                                  |
| scope           | [object](#estructura-ambito-del-cliente-scope)  | Identificador del ámbito.                                                                                                                                                |
| surcharge       | boolean                                         | Indica si el Cliente tiene recargo de equivalencia.                                                                                                                      |
| tariff          | [object](#estructura-tarifa-del-cliente-tariff)(optional) | Tarifa asociada al Cliente.                                                                                                                                              |
| transaction     | string                                          | Tipo de transacciones del cliente.<br/>Valores permitidos:<ul><li>NATIONAL</li><li>INTRACOMMUNITY</li><li>EXTRACOMMUNITY</li><li>CAN_CEU_MEL</li><li>OTHER_ISP</li></ul> |
| withholding     | boolean                                         | Indica si el Cliente aplica retención de impuestos.                                                                                                                      |
| status          | string                                          | Estado del cliente.<br/>Valores permitidos:<ul><li>ACTIVE</li><li>INACTIVE</ul>          |


#### Estructura Ámbito del cliente (scope)

| Name   | Type | Description                |
| ------ | ---- | -------------------------- |
| id     | int  | Identificador del ambito.  |
| domain | int  | Identificador del dominio. |

#### Estructura Tarifa del cliente (tariff)

| Name     | Type    | Description                        |
| -------- | ------- | ---------------------------------- |
| id       | int     | Identificador del pedido de venta. |
| domain   | object  | Identificador del dominio.         |
| code     | string  | Code.                              |
| name     | string  | Nombre.                            |
| purchase | boolean | Es de compra.                      |
| discount | boolean | Descuento.                         |
| active   | boolean | Activo                             |
