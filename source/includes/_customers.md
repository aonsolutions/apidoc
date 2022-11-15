# Clientes

Métodos para la obtención de clientes

## Obtener clientes 

Obtención de los clientes.

```shell

# El servicio 'customers' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/customers"
curl --request POST "https://aon.solutions/ms/api/customers"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

> Ejemplo de JSON de respuesta:

```json
[
 {
    "surcharge": false,
    "withholding": false,
    "isRelationship": false,
    "documentType": "NIF",
    "creation_user": "userName",
    "document": "9999999V",
    "deliveryGrouped": true,
    "deliveryValuated": true,
    "legalPerson": false,
    "scope": {
      "id": 11
    },
    "modification_date": 1579349214000,
    "alias": "test.aonsolutions.ne",
    "tariff": 3,
    "id": 661721,
    "confidential": false,
    "modification_user": "userName",
    "ProjectGrouped": true,
    "creation_date": 1556201144000,
    "eInvoice": false,
    "documentCountry": "ES",
    "nationality": "ES",
    "domain": {
      "owner": "test@test.es",
      "lastAccessUser": "jgarcia",
      "modification_user": "jgarcia",
      "disableDomainManagement": false,
      "domainType": "OFFICE",
      "enableHeredity": false,
      "description": " EMPRESA SL",
      "active": true,
      "parentId": 3,
      "maxTotalDocumentSize": 10240,
      "lastAccessDate": "2022-11-11T13:32:01Z",
      "scope": 9,
      "modification_date": "2022-03-14T08:45:05Z",
      "name": "name.domain.net",
      "id": 5,
    },
    "name": " TEST TEST",
    "account": 3246531,
    "transaction": "NAC",
    "status": "INACTIVE"
  },
]
```

### HTTP Request

`GET or POST https://aon.solutions/ms/api/customers`

#### Obtener un registro

`GET https://aon.solutions/ms/api/customers/{$id}`

### Parámetros (Opcionales)

| Name   | Type   | Description                                                                                                            |
| ------ | ------ | ---------------------------------------------------------------------------------------------------------------------- |
| id     | number    |  Identificador del cliente                                                                                          |
| status | array  | Estados.<br/>Valores permitidos:<ul><li>ACTIVE (Activo)</li><li>INACTIVE (Inactivo)</li><li>CLOSED (Cerrado)</li></ul> |
| value  | string | Filtrar por (Documento, Nombre, Alias)                                                                                 |
| additional_info | array | Información adicional. <br/>Valores permitidos:<ul><li>ADDRESSES (Direcciones)</li><li>MEDIA (Correos, Teléfonos)</li><li>BANKS (Bancos)</li><li>PAYMETHOD (Métodos de pagos)</li><li>RSEGMENT (Segmentos)</li></ul> |

## Guardado clientes 

Guardar cliente

```shell

# El servicio 'customers' es una llamada PUT
curl --request PUT "https://aon.solutions/ms/api/customers"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

```json
{
  "deliveryGrouped": false,
  "deliveryValuated": false,
  "eInvoice": false,
  "projectGrouped": false,
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

`PUT https://aon.solutions/ms/api/customers`

#### Actualizar registro

`PUT https://aon.solutions/ms/api/customers/${id}`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id                | int       | Identificador del pedido de venta.|
| domain            | object    | dominio al que pertenece el cliente|
| document          | string    | NIF del cliente|
| documentCountry   | string    | País del documento.|
| documentType      | string    | Tipo de documento.<br/>Valores permitidos:<ul><li>NIF</li><li>CIF</li><li>NIE</li><li>PASSPORT</li><li>WORK_PERMIT</li><li>COMMUNITY_CARD</li><li>OTHER</li></ul>|
| name              | string    | Nombre / Razón social del cliente.|
| alias             | string    | Alias del cliente.|
| legalPerson       | boolean   | Cierto si es persona jurídica.|
| nationality       | string    | Nacionalidad del cliente.|
| confidential      | boolean   | Cierto si el cliente es confidencial.|
| global            | boolean   | Cierto si el cliente es de global.|
| dirty             | boolean   | Cierto si hay que modificar el cliente.|
| account           | int       | Identificador de la cuenta contable asignada al cliente.|
| deliveryGrouped   | boolean   | Indica si el Cliente desea agrupar albaranes en una sola Factura.|
| deliveryValuated  | boolean   | Indica si el Cliente desea imprimir el albarán valorado.|
| eInvoice          | boolean   | Indica si el Cliente desea recibir Facturas electrónicas.|
| invoicingGroup    | int       | Identificador de Grupo de Facturación.|
| projectGrouped    | boolean   | Indica si el Cliente desea agrupar proyectos en una sola Factura.|
| scope             | int       | Identificador del ámbito.|
| surcharge         | boolean   | Indica si el Cliente tiene recargo de equivalencia.|
| tariff            | int       | Tarifa asociada al Cliente.|
| transaction       | string    | Tipo de transacciones del cliente.<br/>Valores permitidos:<ul><li>NATIONAL</li><li>INTRACOMMUNITY</li><li>EXTRACOMMUNITY</li><li>CAN_CEU_MEL</li><li>OTHER_ISP</li></ul>|
| withholding       | boolean   | Indica si el Cliente aplica retención de impuestos.|
| status            | string    | Estado del cliente.<br/>Valores permitidos:<ul><li>ACTIVE</li><li>INACTIVE</li><li>BLOCKED</li></ul>|
| tariff            | int(optional) |Tarifa asociada al Cliente.|
