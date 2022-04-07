# Facturación
Métodos para la obtención de datos de facturas.

## Obtener facturas
Obtención de facturas resumidas

```shell

# El servicio 'invoice' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/invoice"
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

`GET https://aon.solutions/ms/api/invoice`

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
| date      | date   | Fecha de la factura          |
| reference | string | Referencia de la factura     |
| total     | number | Cuantía total                |
| name      | string | Nombre del titular           |
| id        | number | Identificador de la factura  |
| status    | string | Estado de la factura         |

## Obtener factura
Obtención del una factura

```shell

# El servicio 'invoice' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/invoice"
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
            "amount": 322.68,
            "paymethod": 3,
            "domain": 7138,
            "due_date": "2022-03-28",
            "id": 1302213
        }
    ],
    "category": "705012200",
    "transaction": "NAC",
    "status": "scored"
}
```

### HTTP Request

`GET https://aon.solutions/ms/api/invoice`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id   | number | Identificador de la factura  |



### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| date              | date      | Fecha de la factura  |
| withholding       | boolean   | Retenciones |
| surcharge         | boolean   | Recargos |
| receiver          | json      | Datos del receptor |
| activity          | number    | Identificador de actividad |
| rectified         | boolean   | Rectificada |
| investment        | number    | Inversión |
| taxes             | jsonArray | Impuestos |
| type              | string    | Tipo |
| reference         | string    | Referencia |
| number            | number    | Número de factura |
| withholdingFarmer | boolean   | Régimen especial agrario |
| total             | number    | Total de la factura |
| sender            | json      | Datos del remitente |
| service           | boolean   | Servicio |
| vatAccrualPayment | boolean   | Criterio de caja |
| domain            | number    | Identificador del dominio |
| details           | jsonArray | Detalles de la factura |
| id                | number    | Identificador de la factura |
| finances          | jsonArray | Datos bancarios |
| category          | string    | Categoría de la factura |
| transaction       | string    | Tipo de transacción |
| status            | string    | Estado de la factura |


## Subir factura
Subir una factura

```shell

# El servicio 'invoice' es una llamada POST
curl --request POST "https://aon.solutions/ms/api/invoice"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
    "file": {
        "domain": {
            "id": "1234",
            "name": "empresa.aonsolutions.net"
        },
        "name": "1424.pdf",
        "size": 21610,
        "date": "2022-04-07T07:49:38.546Z",
        "content": "/*el archivo en base64*/",
        "contentType": "application/pdf",
        "contentName": "1424.pdf",
        "contentEncoding": "base64",
        "contentSize": 21610
    },
    "invoice": {
        "domain": "7138",
        "type": "recibida",
        "series": 2022,
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

`POST https://aon.solutions/ms/api/invoice`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| file   | json | Datos del fichero a subir  |
| invoice   | json | Datos de la nueva factura |



### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| date           | date      | Fecha de la factura    |
| withholding    | false     | Retenciones    |
| creation_user  | string    | Usuario que crea la factura    |
| selfconta      | boolean   | SelfConta  |
| taxes          | jsonArray | Impuestos |
| type           | string    | Tipo de factura  |
| reference      | string    | Referencia de la factura    |
| number         | string    | Número de la factura |
| total          | Number    | Total de la factura  |
| file           | json      | Fichero de la factura    |
| details        | jsonArray | Detalles de la factura  |
| id             | number    | Identificador de la factura   |
| tbai           | boolean   | false   |
| comments       | string    | Comentarios  |
| receiver       | json      | Datos del destinatario   |
| tbaiUrl        | string    | URL de Ticketbai
| insight        | json      | Datos parseados del fichero  |
| sender         | json      | Datos del remitente |
| series         | number    | Serie de la factura |
| domain         | string    | Identificador del dominio   |
| serie          | number    | Serie de la factura |
| category       | string    | Categoría de la factura   |
| finances       | jsonArray | Métodos de pago   |
| transaction    | string    | Transacción    |
| remarks        | jsonArray |    |
| status         | string    | Estado de la factura  |
| suplidos       | json      | Suplidos |

