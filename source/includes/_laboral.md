# Laboral
Métodos para la obtención de documentos de carácter laboral como recibos salariales.

## Obtener nómina
Obtención del una nómina en PDF.

```shell

# El servicio 'contract/salary/pdf' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/contract/salary/pdf"
 -H "session_id:YOURSESSIONID" --data
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
Obtención de empleados por su centro de trabajo.

```shell

# El servicio 'contract/employee/workplace' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/contract/employee/workplace"
 -H "session_id:YOURSESSIONID" --data
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
 -H "session_id:YOURSESSIONID" --data
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

## Obtener costes
Obtención de costes por fecha.

```shell

# El servicio 'contract/company/costs' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/contract/company/costs"
 -H "session_id:YOURSESSIONID" --data
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
        "endDate": "2022-03-31",
        "employee": "AGATSUMA, ZENITSU",
        "cgp": 0,
        "employeeSS": 52.99,
        "jobTraining": 0.83,
        "noEstruct": 0,
        "bonuses": 0,
        "estruc": 0,
        "noEstructEnterprise": 0,
        "cgpEnterprise": 12.42,
        "otherDeductions": 0,
        "fogasaEnterprise": 1.66,
        "salaryType": "SALARY",
        "embargos": 0,
        "enterpriseSS": 296.46,
        "jobTrainingEnterprise": 4.97,
        "raw": 1000,
        "estrucEnterprise": 0,
        "irpfBase": 1000,
        "cgcBase": 827.88,
        "irpf": 20,
        "advancedPayment": 0,
        "liquid": 927.01,
        "unemployment": 13.25,
        "unemploymentEnterprise": 55.46,
        "workplace": "CAZADEMONIOS",
        "startDate": "2022-03-01",
        "cgc": 38.91,
        "totalCost": 1296.46
    },
    {
        "endDate": "2022-03-31",
        "employee": "DE MAGALLANES, FERNANDO",
        "cgp": 0,
        "employeeSS": 12.65,
        "jobTraining": 0.2,
        "noEstruct": 0,
        "bonuses": 0,
        "estruc": 0,
        "noEstructEnterprise": 0,
        "cgpEnterprise": 2.98,
        "otherDeductions": 0,
        "fogasaEnterprise": 0.4,
        "salaryType": "SETTLE",
        "embargos": 0,
        "enterpriseSS": 62.53,
        "jobTrainingEnterprise": 1.19,
        "raw": 199.18,
        "estrucEnterprise": 0,
        "irpfBase": 199.18,
        "cgcBase": 199.18,
        "irpf": 3.98,
        "advancedPayment": 0,
        "liquid": 182.55,
        "unemployment": 3.09,
        "unemploymentEnterprise": 10.95,
        "workplace": "EXPLORACIÓN",
        "startDate": "2022-03-01",
        "cgc": 9.36,
        "totalCost": 261.71000000000004
    }
]
```

### HTTP Request

`GET https://aon.solutions/ms/api/contract/company/costs`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| startDate     | date  | Fecha desde (dd-MM-yyyy)  |
| endDate       | date  | Fecha hasta (dd-MM-yyyy)  |

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| endDate                   | date   | Fecha de fin de la nómina (dd-MM-yyyy)       |
| employee                  | string | Nombre completo del empleado                 |
| cgp                       | number | Contingencias profesionales                  |
| employeeSS                | number | Total contribuciones del empleado            |
| jobTraining               | number | Formación profesional                        |
| noEstruct                 | number | Horas extras de fuerza mayor                 |
| bonuses                   | number | Bonificaciones                               |
| estruc                    | number | Horas extras estructurales                   |
| noEstructEnterprise       | number | Horas extras de fuerza mayor (empresa)       |
| cgpEnterprise             | number | Contingencias profesionales (empresa)        |
| otherDeductions           | number | Otras deducciones                            |
| fogasaEnterprise          | number | FOGASA                                       |
| salaryType                | string | Tipo de nómina                               |
| embargos                  | number | Embargos                                     |
| enterpriseSS              | number | Total contribuciones de la empresa           |
| jobTrainingEnterprise     | number | Formación profesional (empresa)              |
| raw                       | number | Bruto                                        |
| estrucEnterprise          | number | Horas extras estructurales (empresa)         |
| irpfBase                  | number | Base IRPF                                    |
| cgcBase                   | number | Base de contingencias comunes                |
| irpf                      | number | IRPF                                         |
| advancedPayment           | number | Anticipos                                    |
| unemployment              | number | Desempleo                                    |
| unemploymentEnterprise    | number | Desempleo (empresa)                          |
| workplace                 | string | Nombre del centro de trabajo                 |
| startDate                 | date   | Fecha de inicio de la nómina                 |
| cgc                       | number | Contingencias comunes                        |
| totalCost                 | number | Coste total de empresa                       |

## Obtener hoja de cálculo de costes
Obtención de la hoja de cálculo de costes.

```shell

# El servicio 'contract/company/costs/excel' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/contract/company/costs/excel"
 -H "session_id:YOURSESSIONID" --data
```
```json
{
    "startDate" : "2022-01-01",
    "endDate": "2022-12-31"
}
```

### HTTP Request

`GET https://aon.solutions/ms/api/contract/company/costs/excel`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| startDate     | date  | Fecha desde (dd-MM-yyyy)  |
| endDate       | date  | Fecha hasta (dd-MM-yyyy)  |

### Respuesta

El PDF con los costes.