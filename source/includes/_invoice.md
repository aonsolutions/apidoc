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

## Aceptar factura
Aceptar una factura

```shell

# El servicio 'invoice/accept' es una llamada PUT
curl --request POST "https://aon.solutions/ms/api/invoice/accept"
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
    "status": "pending"
}
```

### HTTP Request

`PUT https://aon.solutions/ms/api/invoice/accept`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id                | number    | Identifcador de la factura    |
| domain            | string    | Identificador del dominio   |
| type              | string    | Tipo de factura   |
| series            | number    | Serie de la factura |
| serie             | number    | Serie de la factura |
| number            | string    | Número de de la factura   |
| reference         | string    | Referencia de la factura  |
| date              | date      | Fecha de la factura |
| transaction       | string    | Transacción    |
| category          | string    | Categoría   |
| total             | number    | Cuantía total   |
| name              | string    | Razón social   |
| sender            | json      | Datos del remitente |
| receiver          | json      | Datos del destinatario    |
| details           | jsonArray | Detalles de la factura    |
| taxes             | jsonArray | Impuestos |
| finances          | jsonArray | Información de los métodos de pago    |
| status            | string    | Estado de la factura  |
| suplidos          | json      | Suplidos  |
| comments          | string    | Comentarios   |
| remarks           | jsonArray | Observaciones |
| selfconta         | boolean   | Selfconta |
| service           | boolean   | Servicio  |
| withholding       | boolean   | Retenciones   |
| investment        | boolean   | Inversión |
| withholdingFarmer | boolean   | Régimen especial agrario  |
| vatAccrualPayment | boolean   | Criterio de caja  |
| surcharge         | boolean   | Recargos  |
| rectified         | boolean   | Rectificada   |
| creation_user     | string    | Usuario que crea la factura   |
| tbai              | boolean   | Ticketbai
| tbaiUrl           | string    | URL de Ticketbai
| file              | json      | Información del fichero   |
| paymethod         | string    | Método de pago    |


### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| date              | date      | Fecha de la factura    |
| withholding       | boolean   | Retenciones  |
| surcharge         | boolean   | Recargo   |
| receiver          | json      | Datos del destinatario   |
| activity          | number    | Identificador de actividad   |
| rectified         | boolean   | Rectificada  |
| investment        | boolean   | Inversión  |
| taxes             | jsonArray | Impuestos  |
| type              | string    | Tipo de factura   |
| reference         | string    | Referencia de la factura  |
| number            | number    | Número de la factura  |
| withholdingFarmer | boolean   | Régimen especial agrario  |
| total             | number    | Cuantía total |
| sender            | json      | Datos del remitente   |
| series            | string    | Serie de la factura    |
| service           | boolean   | Servicio  |
| vatAccrualPayment | boolean   | Criterio de caja  |
| domain            | number    | Identificador del dominio |
| serie             | string    | Serie de la factura   |
| details           | jsonArray | Detalles de la factura    |
| id                | number    | Identificador de la factura   |
| finances          | jsonArray | Datos de los métodos de pago  |
| transaction       | string    | Transacción   |
| status            | string    | Estado de la factura  |

## Eliminar documentos pendientes
Eliminación de documentos pendientes

```shell

# El servicio 'invoice/rawdoc' es una llamada DELETE
curl --request DELETE "https://aon.solutions/ms/api/invoice/rawdoc"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
    "id": [18224, 18225]
}
```

### HTTP Request

`DELETE https://aon.solutions/ms/api/invoice/rawdoc`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id                | array    | Array de ids de las facturas    |

## Eliminar factura
Eliminación de una factura

```shell

# El servicio 'invoice' es una llamada DELETE
curl --request DELETE "https://aon.solutions/ms/api/invoice"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
    "id": [18224, 18225]
}
```

### HTTP Request

`DELETE https://aon.solutions/ms/api/invoice`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id                | number    | Identificador de la factura    |


## Obtener configuración
Obtención de la configuración del usuario de facturas.

```shell

# El servicio 'invoice/configuration' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/invoice/configuration"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

> Ejemplo de JSON de respuesta:

```json
    {
    "tbai": {
        "test": false,
        "administration": "COMMON_TERRITORY",
        "active": false
    },
    "print": {
        "border": 0,
        "contactData": false,
        "footer": 100,
        "active": true,
        "language": "es",
        "detailed": false,
        "adjust": false,
        "background": false,
        "legal": "De conformidad con la Ley Orgánica 15/1999, le informamos que sus datos se hallan incorporados a un fichero titularidad de CAPSULE CORP. con la finalidad de cumplir con nuestra relación comercial. Puede ejercer los derechos de acceso, rectificación, cancelación y oposición en cualquier momento, mediante escrito, acompañado de copia de documento oficial que le identifique, dirigido a CAPSULE CORP., CALLE FALSA, 123",
        "header": 100,
        "logo": false,
        "company": false,
        "theme": {
            "titleTextColor": "#404040",
            "boxBorderColor": "#808080",
            "theme": "BLACK_AND_WHITE",
            "boxTitleBackgroundColor": "#404040",
            "boxTitleTextColor": "#ffffff",
            "boxBodyBackgroundColor": "#ffffff",
            "textColor": "#404040",
            "customerBackgroundColor": "#E7E7E7"
        },
        "recordData": false
    },
    "sii": {
        "test": false,
        "administration": "COMMON_TERRITORY",
        "autosend": false,
        "active": false,
        "includeDate": "2017-07-01",
        "registryDate": "tax"
    },
    "administration": "COMMON_TERRITORY",
    "company": {
        "surcharge": false,
        "withholding": false,
        "documentType": "CIF",
        "document": "B12345678",
        "active": true,
        "eInvoice": false,
        "documentCountry": "ES",
        "nationality": "ES",
        "vatAccrualPayment": false,
        "domain": {
            "owner": "bulma@capsule.es",
            "domainType": "OFFICE",
            "scope": 3195,
            "name": "capsule.aonsolutions.net",
            "enableHeredity": true,
            "description": "CAPSULE CORP.",
            "active": true,
            "id": 7138,
            "domainManagement": false,
            "maxDefinedUsers": 1,
            "parentId": 1
        },
        "legalPerson": true,
        "name": "CAPSULE CORP.",
        "alias": "CAPSULE",
        "id": 100000,
        "confidential": false
    },
    "eInvoice": false
}
```

### HTTP Request

`GET https://aon.solutions/ms/api/invoice/configuration`

### Parámetros

No requiere

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| tbai              | json      | Datos de Ticketbai    |
| print             | json      | Configuración de impresión    |
| sii               | json      | Configuración del SII |
| administration    | string    | Administración    |
| company           | json      | Datos de la empresa |
| eInvoice          | boolean   | Factura electrónica   |


## Guardar configuración
Guardar la configuración del usuario de facturas.

```shell

# El servicio 'invoice/configuration' es una llamada POST
curl --request POST "https://aon.solutions/ms/api/invoice/configuration"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

> Ejemplo de JSON de respuesta:

```json
{
    "tbai": {
        "test": false,
        "administration": "COMMON_TERRITORY",
        "active": false
    },
    "print": {
        "border": 0,
        "contactData": false,
        "footer": 100,
        "active": true,
        "language": "es",
        "detailed": false,
        "adjust": false,
        "background": false,
        "legal": "De conformidad con la Ley Orgánica 15/1999, le informamos que sus datos se hallan incorporados a un fichero titularidad de CAPSULE CORP. con la finalidad de cumplir con nuestra relación comercial. Puede ejercer los derechos de acceso, rectificación, cancelación y oposición en cualquier momento, mediante escrito, acompañado de copia de documento oficial que le identifique, dirigido a CAPSULE CORP., CALLE FALSA, 123",
        "header": 100,
        "logo": false,
        "company": false,
        "theme": {
            "titleTextColor": "#404040",
            "boxBorderColor": "#808080",
            "theme": "BLACK_AND_WHITE",
            "boxTitleBackgroundColor": "#404040",
            "boxTitleTextColor": "#ffffff",
            "boxBodyBackgroundColor": "#ffffff",
            "textColor": "#404040",
            "customerBackgroundColor": "#E7E7E7"
        },
        "recordData": false
    },
    "sii": {
        "test": false,
        "administration": "COMMON_TERRITORY",
        "autosend": false,
        "active": false,
        "includeDate": "2017-07-01",
        "registryDate": "tax"
    },
    "administration": "COMMON_TERRITORY",
    "company": {
        "surcharge": false,
        "withholding": false,
        "documentType": "CIF",
        "document": "B12345678",
        "active": true,
        "eInvoice": false,
        "documentCountry": "ES",
        "nationality": "ES",
        "vatAccrualPayment": false,
        "domain": {
            "owner": "bulma@capsule.es",
            "domainType": "OFFICE",
            "scope": 3195,
            "name": "capsule.aonsolutions.net",
            "enableHeredity": true,
            "description": "CAPSULE CORP.",
            "active": true,
            "id": 7138,
            "domainManagement": false,
            "maxDefinedUsers": 1,
            "parentId": 1
        },
        "legalPerson": true,
        "name": "CAPSULE CORP.",
        "alias": "CAPSULE",
        "id": 804414,
        "confidential": false
    },
    "eInvoice": false
}
```

> Ejemplo de JSON de respuesta:

```json
{
    "tbai": {
        "test": false,
        "administration": "COMMON_TERRITORY",
        "active": false
    },
    "print": {
        "border": 0,
        "contactData": false,
        "footer": 100,
        "active": true,
        "language": "es",
        "detailed": false,
        "adjust": false,
        "background": false,
        "legal": "De conformidad con la Ley Orgánica 15/1999, le informamos que sus datos se hallan incorporados a un fichero titularidad de CAPSULE CORP. con la finalidad de cumplir con nuestra relación comercial. Puede ejercer los derechos de acceso, rectificación, cancelación y oposición en cualquier momento, mediante escrito, acompañado de copia de documento oficial que le identifique, dirigido a CAPSULE CORP., CALLE FALSA, 123",
        "header": 100,
        "logo": false,
        "company": false,
        "theme": {
            "titleTextColor": "#404040",
            "boxBorderColor": "#808080",
            "theme": "BLACK_AND_WHITE",
            "boxTitleBackgroundColor": "#404040",
            "boxTitleTextColor": "#ffffff",
            "boxBodyBackgroundColor": "#ffffff",
            "textColor": "#404040",
            "customerBackgroundColor": "#E7E7E7"
        },
        "recordData": false
    },
    "sii": {
        "test": false,
        "administration": "COMMON_TERRITORY",
        "autosend": false,
        "active": false,
        "includeDate": "2017-07-01",
        "registryDate": "tax"
    },
    "administration": "COMMON_TERRITORY",
    "eInvoice": false
}
```

### HTTP Request

`POST https://aon.solutions/ms/api/invoice/configuration`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| tbai              | json      | Datos de Ticketbai    |
| print             | json      | Configuración de impresión    |
| sii               | json      | Configuración del SII |
| administration    | string    | Administración    |
| company           | json      | Datos de la empresa |
| eInvoice          | boolean   | Factura electrónica   |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| tbai              | json      | Datos de Ticketbai    |
| print             | json      | Configuración de impresión    |
| sii               | json      | Configuración del SII |
| administration    | string    | Administración    |
| eInvoice          | boolean   | Factura electrónica   |


## Obtener configuración de impresión
Obtención de la configuración impresión de facturas del usuario.

```shell

# El servicio 'invoice/print_configuration' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/invoice/print_configuration"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

> Ejemplo de JSON de respuesta:

```json
{
    "border": 0,
    "contactData": false,
    "footer": 100,
    "active": true,
    "language": "es",
    "detailed": false,
    "adjust": false,
    "background": false,
    "legal": "De conformidad con la Ley Orgánica 15/1999, le informamos que sus datos se hallan incorporados a un fichero titularidad de CAPSULE CORP. con la finalidad de cumplir con nuestra relación comercial. Puede ejercer los derechos de acceso, rectificación, cancelación y oposición en cualquier momento, mediante escrito, acompañado de copia de documento oficial que le identifique, dirigido a CAPSULE CORP., CALLE FALSA, 123",
    "header": 100,
    "logo": false,
    "company": false,
    "theme": {
        "titleTextColor": "#404040",
        "boxBorderColor": "#808080",
        "theme": "BLACK_AND_WHITE",
        "boxTitleBackgroundColor": "#404040",
        "boxTitleTextColor": "#ffffff",
        "boxBodyBackgroundColor": "#ffffff",
        "textColor": "#404040",
        "customerBackgroundColor": "#E7E7E7"
    },
    "recordData": false
}
```

### HTTP Request

`GET https://aon.solutions/ms/api/invoice/configuration`

### Parámetros

No requiere

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| border        | number    | Tipo de borde |
| contractData  | boolean   | Datos de contrato |
| footer        | number    | Altura mínima del pie |
| active        | boolean   | Activo    |
| language      | string    | Idioma    |
| detailed      | boolean   | Detallada |
| adjust        | boolean   | Ajustar   |
| background    | boolean   | Fondo |
| legal         | string    | Aviso legal   |
| header        | number    | Altura mínima del encabezado  |
| logo          | boolean   | Logo de empresa   |
| company       | boolean   | Compañía  |
| theme         | json      | Tema  |
| recordData    | boolean   | Datos de registro |


## Guardar configuración de impresión
Guardado de la configuración impresión de facturas del usuario.

```shell

# El servicio 'invoice/print_configuration' es una llamada POST
curl --request POST "https://aon.solutions/ms/api/invoice/print_configuration"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

```json
{
    "border": 0,
    "contactData": false,
    "footer": 100,
    "active": true,
    "language": "es",
    "detailed": false,
    "adjust": false,
    "background": false,
    "legal": "De conformidad con la Ley Orgánica 15/1999, le informamos que sus datos se hallan incorporados a un fichero titularidad de CAPSULE CORP. con la finalidad de cumplir con nuestra relación comercial. Puede ejercer los derechos de acceso, rectificación, cancelación y oposición en cualquier momento, mediante escrito, acompañado de copia de documento oficial que le identifique, dirigido a CAPSULE CORP., CALLE FALSA, 123",
    "header": 100,
    "logo": false,
    "company": false,
    "theme": {
        "titleTextColor": "#404040",
        "boxBorderColor": "#808080",
        "theme": "BLACK_AND_WHITE",
        "boxTitleBackgroundColor": "#404040",
        "boxTitleTextColor": "#ffffff",
        "boxBodyBackgroundColor": "#ffffff",
        "textColor": "#404040",
        "customerBackgroundColor": "#E7E7E7"
    },
    "recordData": false
}
```


> Ejemplo de JSON de respuesta:

```json
{
    "border": 0,
    "contactData": false,
    "footer": 100,
    "active": true,
    "language": "es",
    "detailed": false,
    "adjust": false,
    "background": false,
    "legal": "De conformidad con la Ley Orgánica 15/1999, le informamos que sus datos se hallan incorporados a un fichero titularidad de CAPSULE CORP. con la finalidad de cumplir con nuestra relación comercial. Puede ejercer los derechos de acceso, rectificación, cancelación y oposición en cualquier momento, mediante escrito, acompañado de copia de documento oficial que le identifique, dirigido a CAPSULE CORP., CALLE FALSA, 123",
    "header": 100,
    "logo": false,
    "company": false,
    "theme": {
        "titleTextColor": "#404040",
        "boxBorderColor": "#808080",
        "theme": "BLACK_AND_WHITE",
        "boxTitleBackgroundColor": "#404040",
        "boxTitleTextColor": "#ffffff",
        "boxBodyBackgroundColor": "#ffffff",
        "textColor": "#404040",
        "customerBackgroundColor": "#E7E7E7"
    },
    "recordData": false
}
```

### HTTP Request

`GET https://aon.solutions/ms/api/invoice/configuration`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| border        | number    | Tipo de borde |
| contractData  | boolean   | Datos de contrato |
| footer        | number    | Altura mínima del pie |
| active        | boolean   | Activo    |
| language      | string    | Idioma    |
| detailed      | boolean   | Detallada |
| adjust        | boolean   | Ajustar   |
| background    | boolean   | Fondo |
| legal         | string    | Aviso legal   |
| header        | number    | Altura mínima del encabezado  |
| logo          | boolean   | Logo de empresa   |
| company       | boolean   | Compañía  |
| theme         | json      | Tema  |
| recordData    | boolean   | Datos de registro |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| border        | number    | Tipo de borde |
| contractData  | boolean   | Datos de contrato |
| footer        | number    | Altura mínima del pie |
| active        | boolean   | Activo    |
| language      | string    | Idioma    |
| detailed      | boolean   | Detallada |
| adjust        | boolean   | Ajustar   |
| background    | boolean   | Fondo |
| legal         | string    | Aviso legal   |
| header        | number    | Altura mínima del encabezado  |
| logo          | boolean   | Logo de empresa   |
| company       | boolean   | Compañía  |
| theme         | json      | Tema  |
| recordData    | boolean   | Datos de registro |

La misma que los parámetros en caso de que se haya grabado correctamente.