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