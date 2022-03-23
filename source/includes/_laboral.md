# Laboral
Métodos para la obtención de documentos de carácter laboral como recibos salariales.

## Obtener nómina
Obtención del una nómina en PDF.

```shell

# El servicio 'contract/salary/pdf' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/contract/salary/pdf"
  --data
```
```json
{
    "salaryId" : 100,
    "enterpriseId": 1234,
    "type": "SETTLE"
}
```

### HTTP Request

`GET https://aon.solutions/ms/api/contract/salary/pdf`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| salaryId      | number | Identificador del recibo salarial  |
| enterpriseId  | number | Identificador de la empresa        |
| type          | string | Tipo de nómina                     |

### Respuesta

El PDF de la nómina pasada por parámetros

## Obtener empleados por centro de trabajo
Obtención del una nómina en PDF.

```shell

# El servicio 'contract/employee/workplace' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/contract/employee/workplace"
  --data
```
```json
{
    "workplace" : 100,
    "allEmployees": true
}
```

> Ejemplo de JSON de respuesta:

```json
[
    {
        "nationality": "ES",
        "surName": "DÍAZ",
        "documentType": 0,
        "document": "12345678J",
        "domain": 7138,
        "secondSurName": "DE VIVAR",
        "contractId": 110,
        "name": "RODRIGO",
        "ssNumber": "111088888888",
        "employeeId": 288,
        "payMethodTypeB": 0
    },
    {
        "nationality": "PE",
        "surName": "DAIMAOH",
        "documentType": 0,
        "document": "87654321Z",
        "domain": 7138,
        "secondSurName": "VÁSQUEZ",
        "contractId": 111,
        "name": "PICCOLO",
        "ssNumber": "111077777777",
        "employeeId": 289,
        "payMethodTypeB": 0
    }
]  
```

### HTTP Request

`GET https://aon.solutions/ms/api/contract/employee/workplace`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| workplace     | number  | Identificador del centro de trabajo  |
| allEmployees  | boolean | Obtener todos los empleados (true) o solo aquellos cuyo contrato no haya acabado o lo haya hecho en los últimos dos meses |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| nationality    | string | Nacionalidad del empleado       |
| surName        | string | Primer apellido                 |
| documentType   | number | Tipo de documento               |
| document       | string | Número de documento             |
| domain         | number | Identificador del dominio       |
| secondSurName  | string | Segundo apellido                |
| contractId     | number | Identificador del contrato      |
| name           | string | Nombre del empleado             |
| ssNumber       | string | Número de la Seguridad Social   |
| employeeId     | number | Identificador del empleado      |
| payMethodTypeB | number | Método de pago                  |

## Obtener nóminas por fecha
Obtención de nóminas por fecha de fin de las mismas.

```shell

# El servicio 'contract/enterprise/salaries' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/contract/enterprise/salaries"
  --data
```
```json
{
    "startDate" : "2022-01-01",
    "endDate": "2022-12-31"
}
```

> Ejemplo de JSON de respuesta:

```json
[
    {
        "employeeName": "DE LEZO Y OLAVARRIETA, BLAS",
        "endDate": "2022-02-24",
        "contract": 12345,
        "workplaceName": "NAVAL",
        "type": "SETTLE",
        "totalPayment": 199.18,
        "totalDeduction": 16.63,
        "domain": 7138,
        "workplaceId": 1123,
        "enterpriseId": 804414,
        "id": 200000,
        "totalLiquid": 182.55,
        "enterpriseName": "EMPRESA S.L.",
        "startDate": "2020-09-18"
    },
    {
        "employeeName": "BOLSÓN, FRODO",
        "endDate": "2022-03-16",
        "contract": 11111,
        "workplaceName": "MORDOR",
        "type": "SALARY",
        "totalPayment": 750.85,
        "totalDeduction": 62.7,
        "domain": 7138,
        "workplaceId": 2222,
        "enterpriseId": 33333,
        "id": 200001,
        "totalLiquid": 688.15,
        "enterpriseName": "COMPAÑÍA DEL ANILLO S.L.",
        "startDate": "2022-03-01"
    }
]  
```

### HTTP Request

`GET https://aon.solutions/ms/api/contract/enterprise/salaries`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| startDate     | date  | Fecha desde (dd-MM-yyyy)  |
| endDate       | date  | Fecha hasta (dd-MM-yyyy)  |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| employeeName   | string | Nombre completo del empleado                |
| endDate        | date   | Fecha de fin de la nómina (dd-MM-yyyy)      |
| contract       | number | Identificador del contrato                  |
| workplaceName  | string | Nombre del centro de trabajo                |
| type           | string | Tipo de nómina                              |
| totalPayment   | number | Total devengado                             |
| totalDeduction | number | Total a deducir                             |
| domain         | number | Identificador del dominio                   |
| workplaceId    | number | Identificador del centro de trabajo         |
| enterpriseId   | number | Identificador de la empresa                 |
| id             | number | Identificador de la nómina                  |
| totalLiquid    | number | Líquido total                               |
| enterpriseName | string | Nombre de la empresa                        |
| startDate      | date   | Fecha de inicio de la nómina (dd-MM-yyyy)   |