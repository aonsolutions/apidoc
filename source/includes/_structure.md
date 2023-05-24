# Estructuras
Se especifica la estructura de array y object enlazados en los métodos. 

## Estructura respuesta file
```json
"file" : {
    "content_type" : "application/pdf",
    "url"          : "https://aon.solutions/ms/api/file/eyJkb21haW5faWQiOjc...",
    "path"         : "ms/api/file/eyJkb21haW5faWQiOjc..."
}
```

JSON que nos llega en la **respuesta** que contiene el tipo de fichero y la url para descargar el fichero.

### Formato 
| Name          |  Type         | Description                       |
|---------------|---------------|-----------------------------------|
| contentType   | string        | Tipo de archivo.                  |
| url           | string        | URL para descargar el fichero.    |
| path          | string        | URL que no contiene el dominio.   |

<aside class="notice">
    Ahora mismo solo hace referencia a <a href="#obtener-factura">obtener factura</a> y <a href="#aceptar-factura">aceptar factura</a> del apartado <a href="#facturacion">facturación</a>.
</aside>

## Estructura respuesta de vencimiento (finance)
```json
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
]
```

JSON que nos llega en la **respuesta** que contiene los datos de vencimientos de la factura.

### Formato 
| Name          |  Type         | Description                           |
|---------------|---------------|---------------------------------------|
| id            | int           | Identificador del vencimiento.             |
| domain        | int           | Identificador del dominio.            |
| due_date      | date          | Fecha de vencimiento. `yyyy-mm-dd`    |
| amount        | float         | Cantidad.                             |
| paymethod     | int           | Identificador de la forma de pago.    |
| paymethodName | string        | Nombre de la forma de pago.           |
| paymethodType | string        | Tipo de la forma de pago: <ul> <li>CASH_BASIS (Metálico)</li> <li>NEGOTIABLE_DOCUMENT (Negociable)</li> <li>DEBIT_CARD (Tarjeta de Débito)</li> <li>CREDIT_CARD (Tarjeta de Crédito)</li> <li>CHEQUE (Cheque)</li> <li>BANK_TRANSFER (Transferencia) </li> <li>OTHER (Otros)</li></ul> |
| bank_account  | string        | IBAN de la cuenta bancaria.           |

<aside class="notice">
    Ahora mismo solo hace referencia a <a href="#obtener-factura">obtener factura</a> del apartado <a href="#facturacion">facturación</a>.
</aside>
