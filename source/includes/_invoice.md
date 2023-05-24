# Facturación
Métodos para la obtención de datos de facturas.

## Obtener facturas
Obtención de facturas resumidas

```shell

# El servicio 'invoice' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/invoices"
 -H "session_id:YOURSESSIONID" --data
```
```json
{
    "status": "accounting",
    "type": "purchase,expenses",
    "page": 1,
    "per_page": 50
}
```

> Ejemplo de JSON de respuesta:

```json
[
    {
        "date": "2022-03-31",
        "reference": "A-345",
        "total": 2041,
        "name": "TOFU FUJIWARA",
        "id": 1294902,
        "status": "SCORED"
    },
    {
        "date": "2022-03-25",
        "reference": "2/22",
        "total": 5445,
        "name": "RAYSON CO LTD.",
        "id": 1289504,
        "status": "SCORED"
    }
]  
```

### HTTP Request

`GET https://aon.solutions/ms/api/invoices`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| status    | string    | Estado de la factura  |
| type      | string    | Tipos (separados por coma) de facturas |
| page      | number    | Página de los resultados |
| per_page  | number    | Número máximo de resultados por página |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| id        | number | Identificador de la factura  |
| reference | string | Referencia de la factura     |
| date      | date   | Fecha de la factura          |
| name      | string | Nombre del titular           |
| status    | string | Estado de la factura         |
| total     | number | Importe total de la factura  |

## Obtener factura
Obtención de una factura

```shell

# El servicio 'invoice' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/invoices/:id"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
    "id": 288
}
```

> Ejemplo de JSON de respuesta:

```json
{
    "date": "2022-03-28T00:00:00.000Z",
    "withholding": false,
    "surcharge": false,
    "receiver": {
        "address": {},
        "nationality": "ES",
        "documentType": "NIF",
        "domain": {
            "enableHeredity": false,
            "active": false,
            "id": 7138,
            "domainManagement": false
        },
        "document": "B12345678",
        "legalPerson": false,
        "name": "NERV",
        "id": 807851,
        "documentCountry": "JP",
        "confidential": false
    },
    "activity": 4717,
    "rectified": false,
    "investment": false,
    "taxes": [
        {
            "surcharge": 0,
            "surcharge_quota": 0,
            "percentage": 21,
            "quota": 56,
            "tax": "IVA",
            "type": "IVA",
            "base": 266.68
        }
    ],
    "type": "emitida",
    "reference": "EVA01-0000288",
    "number": 181975,
    "withholdingFarmer": false,
    "total": 322.68,
    "sender": {
        "nationality": "ES",
        "documentType": "NIF",
        "domain": {
            "enableHeredity": false,
            "active": false,
            "id": 7138,
            "domainManagement": false
        },
        "document": "B12345678",
        "legalPerson": false,
        "name": "NERV",
        "id": 807851,
        "documentCountry": "ES",
        "confidential": false
    },
    "service": false,
    "vatAccrualPayment": false,
    "domain": 7138,
    "details": [
        {
            "surcharge": 0,
            "amount": 266.68,
            "quantity": 1,
            "surcharge_quota": 0,
            "price": 266.68,
            "percentage": 21,
            "quota": 56,
            "description": "Servicios de mantenimiento",
            "discount": "0.0",
            "id": 1681110,
            "category": "705012200"
        }
    ],
    "id": 1295807,
    "finances": [
        {
            "id"            : 1302213,
            "domain"        : 7138,
            "amount"        : 322.68,
            "due_date"      : "2022-03-28",
            "paymethod"     : 3,
            "paymethodName" : "TARJETA",
            "paymethodType" : "CREDIT_CARD",
            "bank_account"  : "ES7320386623844751152119"
        }
    ],
    "category"   : "705012200",
    "transaction": "NAC",
    "status"     : "scored",
    "file"       : {
        "content_type" : "application/pdf",
        "url"          : "https://aon.solutions/ms/api/file/eyJkb21haW5faWQiOjc...",
        "path"         : "ms/api/file/eyJkb21haW5faWQiOjc..."
    }
}
```

### HTTP Request

`GET https://aon.solutions/ms/api/invoices/:id`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id   | number | Identificador de la factura  |

### Respuesta

| Name                  | Type                                                  | Description                                                                       |
|-----------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------|
| id                    | number                                                | Identificador de la factura. |
| domain                | number                                                | Identificador del dominio al que pertenece la factura. |
| type                  | string                                                | Tipo de la factura. valores permitidos: emitida, recibida, ticket. |
| serie                 | string                                                | Serie de la factura. |
| number                | number                                                | Número de factura. |
| reference             | string                                                | Referencia de la factura. |
| date                  | date                                                  | Fecha de emisión la factura. |
| transaction           | string                                                | Tipo de transacción de la factura. valores permitidos: NAC, INTR, EXTR, CCM, ISP. |
| category              | string                                                | Categoría de la factura. (Cuenta Contable de la factura). |
| total                 | number                                                | Importe total de la factura. |
| sender                | object                                                | Información del emisor de la factura. |
| receiver              | object                                                | Información del emisor de la factura. |
| investment            | boolean                                               | Indica si es una factura de inversión. |
| service               | boolean                                               | Indica si es una factura de servicio. |
| withholding           | boolean                                               | Indica si la factura tiene Retención. |
| withholdingFarmer     | boolean                                               | Indica si la factura tiene régimen especial de agricultura, ganaderia y pesca. |
| vatAccrualPayment     | boolean                                               | Indica si la factura tiene régimen especial de criterio de caja. |
| surcharge             | boolean                                               | Indica si la factura tiene Recargo de equivalencia. |
| rectified             | boolean                                               | Indica si es una factura rectificada. |
| rectifier             | boolean                                               | Indica si es una factura rectificativa. |
| rectificationInvoice  | number                                                | Identificador de la factura rectificada o de la factura rectificativa. |
| comments              | string                                                | Comentarios de la factura. |
| remarks               | string                                                | Observaciones de la factura. |
| activity              | object                                                | Actividad de la factura. |
| workplace             | string                                                | Centro de trabajo de la factura. |
| status                | string                                                | Estado de la factura. valores permitidos: inbox, rejected, draft, pending, scored |
| taxes                 | array                                                 | Resumen de los impuestos de la factura. |
| details               | array                                                 | Detalles de la factura. |
| finances              | [array](#estructura-respuesta-de-vencimiento-finance) | Vencimientos de la factura. |
| file                  | [JSON](#estructura-respuesta-file)                    | Contiene el tipo de fichero y la url para descargar el fichero. |

## Crear factura
Crear una factura

```shell

# El servicio 'invoice' es una llamada POST
curl --request POST "https://aon.solutions/ms/api/invoices"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
    "domain": "7138",
    "type": "recibida",
    "serie": 2022,
    "number": "",
    "reference": "",
    "date": "2022-04-07T07:49:38.546Z",
    "transaction": "NAC",
    "category": "",
    "total": 0,
    "sender": {
        "document": "",
        "name": "",
        "address": {
            "country": "ES",
            "address": "",
            "zip": "",
            "city": "",
            "province": ""
        }
    },
    "receiver": {
        "document": "",
        "name": "",
        "address": {
            "country": "ES",
            "address": "",
            "zip": "",
            "city": "",
            "province": ""
        }
    },
    "details": [],
    "taxes": [],
    "finances": [],
    "status": "inbox",
    "suplidos": {
        "active": false,
        "description": "",
        "total": 0
    },
    "comments": "",
    "remarks": [],
    "selfconta": false,
    "withholding": false,
    "creation_user": "aon",
    "tbai": false,
    "tbaiUrl": ""
}
```

> Ejemplo de JSON de respuesta:

```json
{
    "date": "2020-06-29T00:00:00.000Z",
    "withholding": false,
    "creation_user": "aon",
    "selfconta": false,
    "taxes": [
        {
            "percentage": 0,
            "quota": 0,
            "tax": "IVA",
            "base": 143.41
        }
    ],
    "type": "recibida",
    "reference": "",
    "number": "",
    "total": 143.41,
    "file": {
        "content_type": "application/pdf",
        "url": "ms/api/file/eyJkb21haW5faWQiOjcxMzgsImF0dGFjaF90eXBlIjo..."
    },
    "details": [],
    "id": 18223,
    "tbai": false,
    "comments": "",
    "receiver": {
        "address": {
            "zip": "",
            "country": "ES",
            "address": "",
            "province": "",
            "city": ""
        },
        "document": "",
        "name": ""
    },
    "tbaiUrl": "",
    "insight": {
        "total": 143.41,
        "amounts": [
            143.41,
            116.41,
            99.42
        ],
        "issue_date": "2020-06-29T00:00:00.000Z",
        "dates": [
            "Mon Jun 29 00:00:00 CEST 2020",
            "Tue Jun 30 00:00:00 CEST 2020"
        ],
        "nifs": [
            {
                "str": "Y1234567M",
                "type": "NIE"
            },
            {
                "str": "B12345678",
                "type": "CIF"
            }
        ]
    },
    "sender": {
        "address": {
            "zip": "",
            "country": "ES",
            "address": "",
            "province": "",
            "city": ""
        },
        "document": "",
        "name": ""
    },
    "series": 2022,
    "domain": "1234",
    "serie": 2022,
    "category": "",
    "finances": [],
    "transaction": "NAC",
    "remarks": [],
    "status": "inbox",
    "suplidos": {
        "total": 0,
        "active": false,
        "description": ""
    }
}
```

### HTTP Request

`POST https://aon.solutions/ms/api/invoices`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| domain            | number    | Identificador del dominio al que pertenece la factura. |
| type              | string    | Tipo de la factura. valores permitidos: emitida, recibida, ticket. |
| serie             | string    | Serie de la factura. |
| number            | number    | Número de factura. |
| reference         | string    | Referencia de la factura. |
| date              | date      | Fecha de emisión la factura. |
| transaction       | string    | Tipo de transacción de la factura. valores permitidos: NAC, INTR, EXTR, CCM, ISP. |
| category          | string    | Categoría de la factura. (Cuenta Contable de la factura). |
| total             | number    | Importe total de la factura. |
| sender            | object    | Información del emisor de la factura. |
| receiver          | object    | Información del emisor de la factura. |
| investment        | boolean   | Indica si es una factura de inversión. |
| service           | boolean   | Indica si es una factura de servicio. |
| withholding       | boolean   | Indica si la factura tiene Retención. |
| withholdingFarmer | boolean   | Indica si la factura tiene régimen especial de agricultura, ganaderia y pesca. |
| vatAccrualPayment | boolean   | Indica si la factura tiene régimen especial de criterio de caja. |
| surcharge         | boolean   | Indica si la factura tiene Recargo de equivalencia. |
| rectified         | boolean   | Indica si es una factura rectificada. |
| rectifier         | boolean   | Indica si es una factura rectificativa. |
| rectificationInvoice | number | Identificador de la factura rectificada o de la factura rectificativa. |
| comments          | string    | Comentarios de la factura. |
| remarks           | string    | Observaciones de la factura. |
| activity          | object    | Actividad de la factura. |
| workplace         | string    | Centro de trabajo de la factura. |
| status            | string    | Estado de la factura. valores permitidos: inbox, rejected, draft, pending, scored |
| taxes             | array     | Resumen de los impuestos de la factura. |
| details           | array     | Detalles de la factura. |
| finances          | array     | Vencimientos de la factura. |


### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| id                | number    | Identificador de la factura. |
| domain            | number    | Identificador del dominio al que pertenece la factura. |
| type              | string    | Tipo de la factura. valores permitidos: emitida, recibida, ticket. |
| serie             | string    | Serie de la factura. |
| number            | number    | Número de factura. |
| reference         | string    | Referencia de la factura. |
| date              | date      | Fecha de emisión la factura. |
| transaction       | string    | Tipo de transacción de la factura. valores permitidos: NAC, INTR, EXTR, CCM, ISP. |
| category          | string    | Categoría de la factura. (Cuenta Contable de la factura). |
| total             | number    | Importe total de la factura. |
| sender            | object    | Información del emisor de la factura. |
| receiver          | object    | Información del emisor de la factura. |
| investment        | boolean   | Indica si es una factura de inversión. |
| service           | boolean   | Indica si es una factura de servicio. |
| withholding       | boolean   | Indica si la factura tiene Retención. |
| withholdingFarmer | boolean   | Indica si la factura tiene régimen especial de agricultura, ganaderia y pesca. |
| vatAccrualPayment | boolean   | Indica si la factura tiene régimen especial de criterio de caja. |
| surcharge         | boolean   | Indica si la factura tiene Recargo de equivalencia. |
| rectified         | boolean   | Indica si es una factura rectificada. |
| rectifier         | boolean   | Indica si es una factura rectificativa. |
| rectificationInvoice | number | Identificador de la factura rectificada o de la factura rectificativa. |
| comments          | string    | Comentarios de la factura. |
| remarks           | string    | Observaciones de la factura. |
| activity          | object    | Actividad de la factura. |
| workplace         | string    | Centro de trabajo de la factura. |
| status            | string    | Estado de la factura. valores permitidos: inbox, rejected, draft, pending, scored |
| taxes             | array     | Resumen de los impuestos de la factura. |
| details           | array     | Detalles de la factura. |
| finances          | array     | Vencimientos de la factura. |

## Modificar factura
Modificar una factura

```shell

# El servicio 'invoice' es una llamada PUT
curl --request PUT "https://aon.solutions/ms/api/invoices/:id"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
    "domain": "7138",
    "type": "recibida",
    "serie": 2022,
    "number": "",
    "reference": "",
    "date": "2022-04-07T07:49:38.546Z",
    "transaction": "NAC",
    "category": "",
    "total": 0,
    "sender": {
        "document": "",
        "name": "",
        "address": {
            "country": "ES",
            "address": "",
            "zip": "",
            "city": "",
            "province": ""
        }
    },
    "receiver": {
        "document": "",
        "name": "",
        "address": {
            "country": "ES",
            "address": "",
            "zip": "",
            "city": "",
            "province": ""
        }
    },
    "details": [],
    "taxes": [],
    "finances": [],
    "status": "inbox",
    "suplidos": {
        "active": false,
        "description": "",
        "total": 0
    },
    "comments": "",
    "remarks": [],
    "selfconta": false,
    "withholding": false,
    "creation_user": "aon",
    "tbai": false,
    "tbaiUrl": ""
}
```

> Ejemplo de JSON de respuesta:

```json
{
    "date": "2020-06-29T00:00:00.000Z",
    "withholding": false,
    "creation_user": "aon",
    "selfconta": false,
    "taxes": [
        {
            "percentage": 0,
            "quota": 0,
            "tax": "IVA",
            "base": 143.41
        }
    ],
    "type": "recibida",
    "reference": "",
    "number": "",
    "total": 143.41,
    "file": {
        "content_type": "application/pdf",
        "url": "ms/api/file/eyJkb21haW5faWQiOjcxMzgsImF0dGFjaF90eXBlIjo..."
    },
    "details": [],
    "id": 18223,
    "tbai": false,
    "comments": "",
    "receiver": {
        "address": {
            "zip": "",
            "country": "ES",
            "address": "",
            "province": "",
            "city": ""
        },
        "document": "",
        "name": ""
    },
    "tbaiUrl": "",
    "insight": {
        "total": 143.41,
        "amounts": [
            143.41,
            116.41,
            99.42
        ],
        "issue_date": "2020-06-29T00:00:00.000Z",
        "dates": [
            "Mon Jun 29 00:00:00 CEST 2020",
            "Tue Jun 30 00:00:00 CEST 2020"
        ],
        "nifs": [
            {
                "str": "Y1234567M",
                "type": "NIE"
            },
            {
                "str": "B12345678",
                "type": "CIF"
            }
        ]
    },
    "sender": {
        "address": {
            "zip": "",
            "country": "ES",
            "address": "",
            "province": "",
            "city": ""
        },
        "document": "",
        "name": ""
    },
    "series": 2022,
    "domain": "1234",
    "serie": 2022,
    "category": "",
    "finances": [],
    "transaction": "NAC",
    "remarks": [],
    "status": "inbox",
    "suplidos": {
        "total": 0,
        "active": false,
        "description": ""
    }
}
```

### HTTP Request

`PUT https://aon.solutions/ms/api/invoices/:id`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id                | number    | Identificador de la factura. |
| domain            | number    | Identificador del dominio al que pertenece la factura. |
| type              | string    | Tipo de la factura. valores permitidos: emitida, recibida, ticket. |
| serie             | string    | Serie de la factura. |
| number            | number    | Número de factura. |
| reference         | string    | Referencia de la factura. |
| date              | date      | Fecha de emisión la factura. |
| transaction       | string    | Tipo de transacción de la factura. valores permitidos: NAC, INTR, EXTR, CCM, ISP. |
| category          | string    | Categoría de la factura. (Cuenta Contable de la factura). |
| total             | number    | Importe total de la factura. |
| sender            | object    | Información del emisor de la factura. |
| receiver          | object    | Información del emisor de la factura. |
| investment        | boolean   | Indica si es una factura de inversión. |
| service           | boolean   | Indica si es una factura de servicio. |
| withholding       | boolean   | Indica si la factura tiene Retención. |
| withholdingFarmer | boolean   | Indica si la factura tiene régimen especial de agricultura, ganaderia y pesca. |
| vatAccrualPayment | boolean   | Indica si la factura tiene régimen especial de criterio de caja. |
| surcharge         | boolean   | Indica si la factura tiene Recargo de equivalencia. |
| rectified         | boolean   | Indica si es una factura rectificada. |
| rectifier         | boolean   | Indica si es una factura rectificativa. |
| rectificationInvoice | number | Identificador de la factura rectificada o de la factura rectificativa. |
| comments          | string    | Comentarios de la factura. |
| remarks           | string    | Observaciones de la factura. |
| activity          | object    | Actividad de la factura. |
| workplace         | string    | Centro de trabajo de la factura. |
| status            | string    | Estado de la factura. valores permitidos: inbox, rejected, draft, pending, scored |
| taxes             | array     | Resumen de los impuestos de la factura. |
| details           | array     | Detalles de la factura. |
| finances          | array     | Vencimientos de la factura. |


### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| id                | number    | Identificador de la factura. |
| domain            | number    | Identificador del dominio al que pertenece la factura. |
| type              | string    | Tipo de la factura. valores permitidos: emitida, recibida, ticket. |
| serie             | string    | Serie de la factura. |
| number            | number    | Número de factura. |
| reference         | string    | Referencia de la factura. |
| date              | date      | Fecha de emisión la factura. |
| transaction       | string    | Tipo de transacción de la factura. valores permitidos: NAC, INTR, EXTR, CCM, ISP. |
| category          | string    | Categoría de la factura. (Cuenta Contable de la factura). |
| total             | number    | Importe total de la factura. |
| sender            | object    | Información del emisor de la factura. |
| receiver          | object    | Información del emisor de la factura. |
| investment        | boolean   | Indica si es una factura de inversión. |
| service           | boolean   | Indica si es una factura de servicio. |
| withholding       | boolean   | Indica si la factura tiene Retención. |
| withholdingFarmer | boolean   | Indica si la factura tiene régimen especial de agricultura, ganaderia y pesca. |
| vatAccrualPayment | boolean   | Indica si la factura tiene régimen especial de criterio de caja. |
| surcharge         | boolean   | Indica si la factura tiene Recargo de equivalencia. |
| rectified         | boolean   | Indica si es una factura rectificada. |
| rectifier         | boolean   | Indica si es una factura rectificativa. |
| rectificationInvoice | number | Identificador de la factura rectificada o de la factura rectificativa. |
| comments          | string    | Comentarios de la factura. |
| remarks           | string    | Observaciones de la factura. |
| activity          | object    | Actividad de la factura. |
| workplace         | string    | Centro de trabajo de la factura. |
| status            | string    | Estado de la factura. valores permitidos: inbox, rejected, draft, pending, scored |
| taxes             | array     | Resumen de los impuestos de la factura. |
| details           | array     | Detalles de la factura. |
| finances          | array     | Vencimientos de la factura. |


## Aceptar factura
Aceptar una factura

```shell

# El servicio 'invoice/accept' es una llamada PUT
curl --request POST "https://aon.solutions/ms/api/invoices/accept"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
    "id": 18224,
    "domain": "7138",
    "type": "recibida",
    "series": 2022,
    "serie": 2022,
    "number": "",
    "reference": "2022/",
    "date": "2022-04-07",
    "transaction": "NAC",
    "category": "",
    "total": 143.41,
    "name": "MUGIWARA, SL",
    "sender": {
        "documentType": "CIF",
        "document": "B12345678",
        "legalPerson": false,
        "name": "MUGIWARA, SL",
        "global": false,
        "id": 1000000,
        "documentCountry": "ES",
        "confidential": false,
        "address": {
            "zip": "01001",
            "dirty": false,
            "registry": 1251249,
            "country": "ES",
            "streetType": "AV   ",
            "address": "AVENIDA KAIDO 123",
            "address2": " ",
            "city": "ONIGASHIMA",
            "main": true,
            "number": "",
            "province": "WANO",
            "removed": false,
            "domain": 7138,
            "id": 1155976,
            "postal_code": "01001",
            "global": false
        }
    },
    "receiver": {
        "address": {
            "zip": "",
            "country": "ES",
            "address": "",
            "province": "",
            "city": ""
        },
        "document": "",
        "name": ""
    },
    "details": [],
    "taxes": [
        {
            "percentage": 0,
            "quota": 0,
            "tax": "IVA",
            "base": 143.41,
            "type": "IVA"
        }
    ],
    "finances": [
        {
            "due_date": "2020-06-29T00:00:00.000Z",
            "paymethod": "CASH",
            "amount": 143.41,
            "iban": "",
            "bank_account": "ES"
        }
    ],
    "status": "inbox",
    "suplidos": {
        "total": 0,
        "active": false,
        "description": ""
    },
    "comments": "",
    "remarks": [],
    "selfconta": false,
    "service": false,
    "withholding": false,
    "investment": false,
    "withholdingFarmer": false,
    "vatAccrualPayment": false,
    "surcharge": false,
    "rectified": false,
    "creation_user": "aon",
    "tbai": false,
    "tbaiUrl": "",
    "file": {
        "content_type": "application/pdf",
        "url": "ms/api/file/eyJkb21haW5faWQiOjc..."
    },
    "paymethod": "CASH"
}
```

> Ejemplo de JSON de respuesta:

```json
{
    "date": "2022-04-07T00:00:00.000Z",
    "withholding": false,
    "surcharge": false,
    "receiver": {
        "documentType": "CIF",
        "document": "B12345678",
        "legalPerson": false,
        "name": "MUGIWARA, SL",
        "alias": "",
        "id": 1000000,
        "documentCountry": "ES",
        "confidential": false
    },
    "activity": 4717,
    "rectified": false,
    "investment": false,
    "taxes": [
        {
            "surcharge": 0,
            "surcharge_quota": 0,
            "percentage": 0,
            "quota": 0,
            "tax": "IVA",
            "type": "IVA",
            "base": 143.41
        }
    ],
    "type": "recibida",
    "reference": "2022/",
    "number": 375,
    "withholdingFarmer": false,
    "total": 143.41,
    "sender": {
        "address": {
            "zip": "01001",
            "dirty": false,
            "registry": 1251249,
            "country": "ES",
            "streetType": "AV   ",
            "address": "AVENIDA KAIDO 123",
            "address2": "  ",
            "city": "ONIGASHIMA",
            "main": true,
            "number": "",
            "province": "",
            "removed": false,
            "domain": 7138,
            "id": 1155976,
            "postal_code": "06200"
        },
        "documentType": "CIF",
        "document": "B12345678",
        "legalPerson": false,
        "name": "MUGIWARA, SL",
        "alias": "",
        "id": 1251249,
        "documentCountry": "ES",
        "confidential": false
    },
    "series": "2022",
    "service": false,
    "vatAccrualPayment": false,
    "domain": 7138,
    "serie": "2022",
    "details": [
        {
            "surcharge": 0,
            "amount": 143.41,
            "quantity": 1,
            "surcharge_quota": 0,
            "price": 143.41,
            "domain": 7138,
            "percentage": 0,
            "quota": 0,
            "description": "IVA 0.0",
            "discount": "0.0",
            "id": 1708563
        }
    ],
    "id": 1312850,
    "finances": [
        {
            "amount": 143.41,
            "paymethod": 1,
            "domain": 7138,
            "due_date": "2020-06-29"
        }
    ],
    "transaction": "NAC",
    "status": "pending",
    "file"       : {
        "content_type" : "application/pdf",
        "url"          : "https://aon.solutions/ms/api/file/eyJkb21haW5faWQiOjc...",
        "path"         : "ms/api/file/eyJkb21haW5faWQiOjc..."
    }
}
```

### HTTP Request

`POST https://aon.solutions/ms/api/invoices/accept`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id                | number    | Identificador de la factura. |
| domain            | number    | Identificador del dominio al que pertenece la factura. |
| type              | string    | Tipo de la factura. valores permitidos: emitida, recibida, ticket. |
| serie             | string    | Serie de la factura. |
| number            | number    | Número de factura. |
| reference         | string    | Referencia de la factura. |
| date              | date      | Fecha de emisión la factura. |
| transaction       | string    | Tipo de transacción de la factura. valores permitidos: NAC, INTR, EXTR, CCM, ISP. |
| category          | string    | Categoría de la factura. (Cuenta Contable de la factura). |
| total             | number    | Importe total de la factura. |
| sender            | object    | Información del emisor de la factura. |
| receiver          | object    | Información del emisor de la factura. |
| investment        | boolean   | Indica si es una factura de inversión. |
| service           | boolean   | Indica si es una factura de servicio. |
| withholding       | boolean   | Indica si la factura tiene Retención. |
| withholdingFarmer | boolean   | Indica si la factura tiene régimen especial de agricultura, ganaderia y pesca. |
| vatAccrualPayment | boolean   | Indica si la factura tiene régimen especial de criterio de caja. |
| surcharge         | boolean   | Indica si la factura tiene Recargo de equivalencia. |
| rectified         | boolean   | Indica si es una factura rectificada. |
| rectifier         | boolean   | Indica si es una factura rectificativa. |
| rectificationInvoice | number | Identificador de la factura rectificada o de la factura rectificativa. |
| comments          | string    | Comentarios de la factura. |
| remarks           | string    | Observaciones de la factura. |
| activity          | object    | Actividad de la factura. |
| workplace         | string    | Centro de trabajo de la factura. |
| status            | string    | Estado de la factura. valores permitidos: inbox, rejected, draft, pending, scored |
| taxes             | array     | Resumen de los impuestos de la factura. |
| details           | array     | Detalles de la factura. |
| finances          | array     | Vencimientos de la factura. |


### Respuesta

| Name                  |  Type                                     | Description                                                                       |
|-----------------------|-------------------------------------------|-----------------------------------------------------------------------------------|
| id                    | number                                    | Identificador de la factura. |
| domain                | number                                    | Identificador del dominio al que pertenece la factura. |
| type                  | string                                    | Tipo de la factura. valores permitidos: emitida, recibida, ticket. |
| serie                 | string                                    | Serie de la factura. |
| number                | number                                    | Número de factura. |
| reference             | string                                    | Referencia de la factura. |
| date                  | date                                      | Fecha de emisión la factura. |
| transaction           | string                                    | Tipo de transacción de la factura. valores permitidos: NAC, INTR, EXTR, CCM, ISP. |
| category              | string                                    | Categoría de la factura. (Cuenta Contable de la factura). |
| total                 | number                                    | Importe total de la factura. |
| sender                | object                                    | Información del emisor de la factura. |
| receiver              | object                                    | Información del emisor de la factura. |
| investment            | boolean                                   | Indica si es una factura de inversión. |
| service               | boolean                                   | Indica si es una factura de servicio. |
| withholding           | boolean                                   | Indica si la factura tiene Retención. |
| withholdingFarmer     | boolean                                   | Indica si la factura tiene régimen especial de agricultura, ganaderia y pesca. |
| vatAccrualPayment     | boolean                                   | Indica si la factura tiene régimen especial de criterio de caja. |
| surcharge             | boolean                                   | Indica si la factura tiene Recargo de equivalencia. |
| rectified             | boolean                                   | Indica si es una factura rectificada. |
| rectifier             | boolean                                   | Indica si es una factura rectificativa. |
| rectificationInvoice  | number                                    | Identificador de la factura rectificada o de la factura rectificativa. |
| comments              | string                                    | Comentarios de la factura. |
| remarks               | string                                    | Observaciones de la factura. |
| activity              | object                                    | Actividad de la factura. |
| workplace             | string                                    | Centro de trabajo de la factura. |
| status                | string                                    | Estado de la factura. valores permitidos: inbox, rejected, draft, pending, scored |
| taxes                 | array                                     | Resumen de los impuestos de la factura. |
| details               | array                                     | Detalles de la factura. |
| finances              | array                                     | Vencimientos de la factura. |
| file                  | [JSON](#estructura-respuesta-file)        | Contiene el tipo de fichero y la url para descargar el fichero. |

## Eliminar factura
Eliminación de una factura

```shell

# El servicio 'invoice' es una llamada DELETE
curl --request DELETE "https://aon.solutions/ms/api/invoices/:id"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
    "id": [18224, 18225]
}
```

### HTTP Request

`DELETE https://aon.solutions/ms/api/invoices/:id`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id                | number    | Identificador de la factura    |
