# Contabilidad
Aon Solutions dispone de diferentes métodos para obtener datos sobre la contabilidad de la empresa:

## Obtener los períodos contables
Obtención de todos los períodos contables disponibles para la empresa.

```shell

# El servicio 'periods' es una llamada POST
curl --request POST "https://aon.solutions/ms/api/accounting/periods"
 -H "session_id:YOURSESSIONID" --data
```
```json
{
    "domain" : 1,
    "domainName": "empresa.aonsolutions.net",
    "user": "admin"
}
```

> Ejemplo de JSON de respuesta:

```json
[
    {
        "initiationDate": "01/01/2022",
        "domain": 1,
        "name": "2022",
        "id": 11090,
        "deadline": "31/12/2022",
        "status": 2
    },
    {
        "initiationDate": "01/01/2021",
        "domain": 1,
        "name": "2021",
        "id": 5518,
        "deadline": "31/12/2021",
        "status": 4
    }
]  
```

### HTTP Request

`POST https://aon.solutions/ms/api/accounting/periods`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| domain      | number | Identificador del dominio de la empresa  |
| domainName  | string | Nombre del dominio de la empreasa        |
| user        | string | Nombre de usuario                        |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| initiationDate | date   | Fecha de inicio del período (dd/MM/yyyy) |
| domain         | number | Identificador del dominio de la empresa  |
| name           | string | Nombre del período                       |
| id             | number | Identificador del período                |
| deadLine       | date   | Fecha de fin del período (dd/MM/yyyy)    |
| status         | number | Estado del período:<br/>&nbsp;0: Activo<br/>&nbsp;1: Inactivo<br/>&nbsp;2: Apertura<br/>&nbsp;3: Explotación<br/>&nbsp;4: Cerrado|

## Obtener las cuentas contables
Obtención de todos los períodos contables de la contabilidad de la empresa en un período determinado.

```shell

# El servicio 'pyg' es una llamada POST
curl --request POST "https://aon.solutions/ms/api/accounting/pyg"
 -H "session_id:YOURSESSIONID" --data
```

```json
{
    "domain": 7138,
    "domainName": "empresa.aonsolutions.net",
    "user": "admin",
    "level": 5,
    "byMonth": true,
    "period": 11090,
    "fromDate": "01/01/2022",
    "toDate": "31/12/2022"
}
```

> Ejemplo de JSON de respuesta:

```json
{
    "intervals": [
        {
            "interval": {
                "fromDate": "01/01/2022",
                "toDate": "31/01/2022",
                "name": "01/2022"
            },
            "statements": [
                {
                    "salesRatio": 0,
                    "expensesRatio": 0,
                    "month": "20221",
                    "increasePercent": 0,
                    "debit": 13191.809999999983,
                    "credit": 466639.59000006545,
                    "account": {
                        "code": "7050",
                        "description": "Prestación de servicios.",
                        "id": 816,
                        "type": "SALES"
                    },
                    "purchasesRatio": 0
                },
                {
                    "salesRatio": 0,
                    "expensesRatio": 0,
                    "month": "20221",
                    "increasePercent": 0,
                    "debit": 0,
                    "credit": 1504.9500000000003,
                    "account": {
                        "code": "7053",
                        "description": "Empresas del grupo",
                        "id": 50951,
                        "type": "SALES"
                    },
                    "purchasesRatio": 0
                }
            ]
        },
        {
            "interval": {
                "fromDate": "01/02/2022",
                "toDate": "28/02/2022",
                "name": "02/2022"
            },
            "statements": [
                {
                    "salesRatio": 0,
                    "expensesRatio": 0,
                    "month": "20222",
                    "increasePercent": 0,
                    "debit": 9207.289999999997,
                    "credit": 447784.50000006164,
                    "account": {
                        "code": "7050",
                        "description": "Prestación de servicios.",
                        "id": 816,
                        "type": "SALES"
                    },
                    "purchasesRatio": 0
                }
            ]
        }
    ],
    "accounts": [
        {
            "code": "7050",
            "description": "Prestación de servicios.",
            "id": 816,
            "type": "SALES"
        },
        {
            "code": "7053",
            "description": "Empresas del grupo",
            "id": 50951,
            "type": "SALES"
        }
    ],
    "params": {
        "surcharge": false,
        "ledgerUnpaidBalance": 0,
        "reverseOrder": false,
        "hideDateTimeOnFooter": false,
        "selectedPeriod": {
            "initiationDate": "01/01/2022",
            "domain": 7138,
            "name": "2022",
            "id": 11090,
            "deadline": "31/12/2022",
            "status": 2
        },
        "noActivityAccountVisible": false,
        "output": false,
        "percentsEnabled": false,
        "operatingEntriesExcluded": false,
        "ledgerDebitBalance": 0,
        "pageOffset": 0,
        "accrualRegime": false,
        "closingEntriesExcluded": false,
        "breakdownEnabled": false,
        "lowLevelAccountVisible": false,
        "openingEntriesExcluded": false,
        "farmerRegime": false,
        "period": 11090,
        "level": 5,
        "toDate": "31/12/2022",
        "byMonth": true,
        "investment": false,
        "noBalanceAccountExcluded": false,
        "consolidation": false,
        "fromDate": "01/01/2022",
        "previousPeriods": 0,
        "service": false,
        "domain": 7138,
        "domainName": "b72384936-ayudat.aonsolutions.net",
        "showCover": false,
        "hideFilter": false,
        "user": ""
    }
}
```

### HTTP Request

`POST https://aon.solutions/ms/api/accounting/pyg`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| domain      | number  | Identificador del dominio de la empresa   |
| domainName  | string  | Nombre del dominio de la empreasa         |
| user        | string  | Nombre de usuario                         |
| level       | number  | Nivel de detalle (posibles:[1,2,3,4,5,9]) |
| byMonth     | boolean | Agrupado por meses                        |
| period      | number  | Identificador del período                 |
| fromDate    | date    | Fecha desde (dd/MM/yyyy)                  |
| toDate      | date    | Fecha hasta (dd/MM/yyyy)                  |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| intervals      | jsonArray | Array de objetos que contienen el intervalo y un array con todos los movimientos correspondientes |
| accounts       | jsonArray | Array de las cuentas contables del período seleccionado |
| params         | json      | Los parámetros con los que se ha llamado a la función |