# Pedidos de venta

API de pedidos de venta

## Búsqueda de pedidos de venta

Búsqueda de pedidos de venta

```shell

# El servicio 'sales' es una llamada GET y POST
curl --request GET "https://aon.solutions/ms/api/sales"
curl --request POST "https://aon.solutions/ms/api/sales"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

```json
    {
    "series": "",
    "number": 1,
    "status": "PENDING",
    "from": "2022-01-01'T'00:00:00'Z'",
    "to": "2022-05-09'T'00:00:00'Z'"
    }
```

> Ejemplo de JSON de respuesta:

```json
[
    {
    "id": 1,
    "domain": 1,

    "project": {
        "id": 1,
        "domain": 1,
        "alias": "",
        "type": {
        "id": 1,
        "domain": 1,
        "description": "",
        "active": true,
        "dirty": false
        },
        "name": "",
        "date": "2022-05-09T00:00:00Z",
        "registry": 1,
        "active": true,
        "dirty": false
    },
    "series": "",
    "number": 1,
    "purchaseReference": "",
    "seller": {
        "id": 1,
        "domain": { "id": 1 },
        "document": "",
        "documentCountry": "",
        "documentType": "",
        "name": "",
        "alias": "",
        "legalPerson": true,
        "nationality": "",
        "confidential": false,
        "global": false,
        "dirty": false,
        "commissionType": {
        "id": 1,
        "domain": 1,
        "name": "",
        "rate": 10.0
        },
        "scope": {
        "id": 1,
        "domain": 1,
        "description": ""
        },
        "active": true
    },
    "customer": {
        "id": 1,
        "domain": { "id": 1 },
        "document": "",
        "documentCountry": "",
        "documentType": "",
        "name": "",
        "alias": "",
        "legalPerson": true,
        "nationality": "",
        "confidential": false,
        "global": false,
        "dirty": false,
        "account": 1,
        "deliveryGrouped": false,
        "deliveryValuated": false,
        "eInvoice": false,
        "invoicingGroup": 1,
        "projectGrouped": false,
        "surcharge": false,
        "tariff": 1,
        "transaction": "NATIONAL",
        "withholding": false,
        "scope": {
        "id": 1,
        "domain": 1,
        "description": ""
        },
        "status": "ACTIVE"
    },
    "address": {
        "id": 1,
        "domain": 1,
        "registry": 1,
        "main": true,
        "streetType": "",
        "address": "",
        "number": 2,
        "address2": "",
        "city": "",

        "province": "",
        "country": "",
        "zip": "",
        "dirty": false,
        "removed": false,
        "global": false
    },
    "date": "2022-05-09T00:00:00Z",
    "payMethod": {
        "id": 1,
        "domain": 1,
        "type": "CASH_BASIS",
        "name": ""
    },
    "confidential": false,
    "status": "PENDING",
    "type": "NORMAL",
    "comments": "",
    "remarks": "",
    "workplace": {
        "id": 1,
        "domain": 1,
        "name": "",
        "active": true,
        "address": 1,
        "customer": 1,
        "economicAgreement": 1,
        "scope": {
        "id": 1,
        "domain": 1,
        "description": ""
        }
    },
    "scope": {
        "id": 1,
        "domain": 1,
        "description": ""
    },
    "deliveryDate": "2022-05-09'T'00:00:00'Z'",
    "numberOfPymnts": 1,
    "daysToFirstPymnt": 0,
    "daysBetweenPymnts": 0,
    "pymntDays": 1,

    "discount": "0.0",
    "bankAccount": "",
    "bankAlias": "",
    "bic": "",
    "carrier": {
        "id": 1,
        "domain": { "id": 1 },
        "document": "",
        "documentCountry": "",
        "documentType": "",
        "name": "",
        "alias": "",
        "legalPerson": true,
        "nationality": "",
        "confidential": false,
        "global": false,
        "dirty": false,
        "scope": {
        "id": 1,
        "domain": 1,
        "description": ""
        },
        "status": "ACTIVE"
    },
    "shippingAlternativeAddress": "",
    "shippingAlternativeAddress2": "",
    "shippingAlternativeZip": "",
    "shippingAlternativeCity": "",
    "shippingAlternativePhone": "",
    "shippingAlternativeRecipient": "",
    "shippingContact": "",
    "shippingPeriod": "",
    "details": [
        {
        "id": 1,
        "domain": 1,
        "sales": 1,
        "line": 1,
        "item": {
            "id": 1,
            "domain": 1,
            "detail": "",
            "detail2": "",

            "detail3": "",
            "description": "",
            "serialNumber": "",
            "serialDate": "2022-05-09'T'00:00:00'Z'",
            "barcode": "",
            "status": "ACTIVE",
            "product": {
            "id": 1,
            "domain": { "id": 1 },
            "code": "",
            "name": "",
            "brand": {
                "id": 1,
                "domain": 1,
                "name": ""
            },
            "category": {
                "id": 1,
                "domain": 1,
                "name": "",
                "detail": "",
                "detail2": "",
                "detail3": ""
            },
            "type": "LABOUR",
            "kind": "SALE_PURCHASE",
            "status": "ACTIVE",
            "vat": 21.0,
            "retention": 15.0,
            "inventoriable": true,
            "serializable": true,
            "lotable": true,
            "manufactured": true,
            "composition": true,
            "compositionPrice": true,
            "packaged": true,
            "salesAccount": {
                "id": 1,
                "domain": 1,
                "code": "",
                "description": "",
                "alias": "",
                "entryEnabled": true,

                "level": 1,
                "active": true,
                "costCenter": ""
            },
            "purchaseAccount": {
                "id": 1,
                "domain": 1,
                "code": "",
                "description": "",
                "alias": "",
                "entryEnabled": true,
                "level": 1,
                "active": true,
                "costCenter": ""
            }
            },
            "price": 0.0,
            "expensesPercent": 0.0,
            "profitPercent": 0.0,
            "purchasePrice": 0.0,
            "expensesFixed": 0.0,
            "internet": false,
            "packFormatTag": 1,
            "packUnits": 2,
            "packUnitsTag": 3,
            "packMeasurement": 0.0,
            "packMeasurementTag": 4,
            "stockUnitTag": 5
        },
        "description": "",
        "quantity": 0.0,
        "price": 0.0,
        "discount": "0.0",
        "taxes": 0.0,
        "status": "PENDING",
        "offerDetail": 1,
        "delivered": 0.0,
        "carrier": {},
        "carrierPacking": 1
        }
    ]
    }
]
```

### HTTP Request

`GET https://aon.solutions/ms/api/sales`
<br/>
`POST https://aon.solutions/ms/api/sales`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| series    | string    | Serie del pedido  |
| number    | int       | Número del pedido |
| status    | string    | Estado del pedido de venta.<br/>Valores permitidos:<ul><li>PENDING (Pendiente)</li><li>BLOCKED (Bloqueado)</li><li>SERVED (Servido)</li><li>CLOSED (Cerrado)</li><li>INVOICED(Facturado)</li></ul>|
| from      | date      | Fecha desde       |
| to        | date      | Fecha hasta       |
### Respuesta

Devuelve un arreglo con los pedidos de venta que ha encontrado

#### Estructura Pedido de Venta (sales)
| Name |  Type  | Description |
|------|--------|-------------|
| id                            | int       | Identificador del pedido de venta.    |
| domain                        | int       | Identificador del dominio al que pertenece el pedido de venta. |
| project                       | object    | Proyecto al que pertenece el pedido de venta.|
| series                        | string    | Serie del pedido de venta.|
| number                        | int       | Número del pedido de venta.|
| purchaseReference             | string    | Referencia de compra.|
| seller                        | [object](#estructura-comercial-seller)    | Datos del comercial.|
| customer                      | [object](#estructura-cliente-customer)    | Datos del cliente.|
| address                       | [object](#estructura-direccion-postal-address)    | Dirección postal del cliente.|
| date                          | date      | Fecha del pedido de venta.|
| payMethod                     | [object](#estructura-forma-de-pago-paymethod)    | Método de Pago.|
| confidential                  | boolean   | Cierto si el pedido de venta es confidencial.|
| status                        | string    | Estado del pedido de venta.<br/>Valores permitidos:<ul><li>PENDING (Pendiente)</li><li>BLOCKED (Bloqueado)</li><li>SERVED (Servido)</li><li>CLOSED (Cerrado)</li><li>INVOICED (Facturado)</li></ul>|
| type                          | string    | Type del pedido de venta.<br/>Valores permitidos:<ul><li>NORMAL</li><li>SAMPLE</li><li>INTERNET</li><li>DEVOLUTION</li></ul>|
| comments                      | string    | Comentarios del pedido de venta.|
| remarks                       | string    | Observaciones del pedido de venta|
| workplace                     | [object](#estructura-centro-de-trabajo-workplace)    | Centro de trabajo al que pertenece el pedido de venta.|
| scope                         | [object](#estructura-ambito-scope)    | Ámbito del pedido de venta.|
| deliveryDate                  | date      | Fecha de entrega.|
| numberOfPymnts                | int       | Número de Vencimientos.|
| daysToFirstPymnt              | int       | Días al primer vencimiento.|
| daysBetweenPymnts             | int       | Días entre vencimientos.|
| pymntDays                     | int       | Días de pago.|
| discount                      | string    | Descuento.|
| bankAccount                   | string    | Número de cuenta bancaria.|
| bankAlias                     | string    | Alias del Banco.|
| bic                           | string    | Bic del banco.|
| carrier                       | [object](#estructura-empresa-de-transporte-carrier)    | Empresa de Transporte.|
| shippingAlternativeAddress    | string    | Primera parte de la dirección de entrega alternativa.|
| shippingAlternativeAddress2   | string    | Segunda parte de la dirección de entrega alternativa.|
| shippingAlternativeZip        | string    | Código Postal de la dirección de entrega alternativa.|
| shippingAlternativeCity       | string    | Ciudad de la dirección de entrega alternativa.|
| shippingAlternativePhone      | string    | Teléfono de la dirección de entrega alternativa.|
| shippingAlternativeRecipient  | string    | Destinatario de la dirección de entrega alternativa.|
| shippingContact               | string    | Nombre del contacto para la entrega.|
| shippingPeriod                | string    | Periodo de entrega.<br/>Valores permitidos:<ul><li>IN_COMMENTS</li><li>MORNING</li><li>NOON</li><li>AFTERNOON</li><li>BEFORE_10</li><li>BEFORE_12</li><li>OFFICE_HOURS</li><li>AFTER_19</li></ul>|
| details                       | array     | Detalles del pedido de venta.|

#### Estructura Detalle Pedido de Venta (salesDetail)

| Name |  Type  | Description |
|------|--------|-------------|
| id                | int       | Identificador del proyecto.|
| domain            | int       | Identificador del dominio al que pertenece el detalle del pedido de venta.|
| sales             | int       | Identificador del pedido de venta|
| line              | int       | Número de línea de detalle.|
| item              | [object](#estructura-de-articulo-item)    | Datos del artículo.|
| description       | string    | Descripción del detalle.|
| quantity          | double    | Cantidad.|
| price             | double    | Precio unitario.|
| discount          | string    | descuento|
| taxes             | double    | impuestos|
| status            | string    | Estado del detalle del pedido de venta.<br/>Valores permitidos:<ul><li>PENDING</li><li>PARTIAL_SETTLED</li><li>SETTLED</li></ul>|
| offerDetail       | int       | Identificador del detalle de presupuesto relacionado.|
| delivered         | double    | Cantidad que ya está enviada.|
| carrier           | [object](#estructura-empresa-de-transporte-carrier)    | Empresa de Transporte.|
| carrierPacking    | int       | Identificador del packing list.|

#### Estructura Proyecto (project)

| Name |  Type  | Description |
|------|--------|-------------|
| id        | int       | Identificador del proyecto.|
| domain    | int       | Identificador del dominio al que pertenece el proyecto.|
| alias     | string    | Alias del proyecto|
| type      | [object](#estructura-tipo-de-proyecto-projecttype)    | Tipo del proyecto.|
| name      | string    | Nombre del proyecto.|
| date      | date      | Fecha del proyecto.|
| registry  | [object](#estructura-cliente-customer)    | Identificador del cliente.|
| active    | boolean   | Cierto si está activo.|
| dirty     | boolean   | Cierto si hay que modificar el proyecto..|

#### Estructura Tipo de Proyecto (projectType)
| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del proyecto.|
| domain        | int       | Identificador del dominio al que pertenece el proyecto.|
| description   | string    | Descripción del tipo de proyecto.|
| active        | boolean   | Cierto si el tipo de proyecto está activo.|
| dirty         | boolean   | Cierto si hay que modificar el tipo.|

#### Estructura Cliente (customer)
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

#### Estructura Comercial (seller)

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
| commissionType    | [object](#estructura-tipo-de-comision-commissiontype)    | Tipo de Comisión.|
| scope             | [object](#estructura-ambito-scope)    | Ámbito del comercial.|
| active            | boolean   | Cierto si está activo.|

#### Estructura Empresa de Transporte (carrier)


| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del pedido de venta.|
| domain        | object    | Dominio al que pertenece el cliente|
| document      | string    | NIF del cliente|
| documentType  | string    | Tipo de documento.<br/>Valores permitidos:<ul><li>NIF</li><li>CIF</li><li>NIE</li><li>PASSPORT</li><li>WORK_PERMIT</li><li>COMMUNITY_CARD</li><li>OTHER</li></ul>|
| name          | string    | Nombre / Razón social del cliente.|
| alias         | string    | Alias del cliente.|
| legalPerson   | boolean   | Cierto si es persona juridica.|
| nationality   | string    | Nacionalidad del cliente.|
| confidential  | boolean   | Cierto si el cliente es confidencial.|
| global        | boolean   | Cierto si el cliente es de global.|
| dirty         | boolean   | Cierto si hay que modificar el cliente.|
| scope         | [object](#estructura-ambito-scope)    | Ámbito de la empresa de transporte.|
| status        | string    | Estado de la empresa de transporte.<br/>Valores permitidos:<ul><li>ACTIVE</li><li>INACTIVE</li><li>BLOCKED</li></ul>|

#### Estructura Dirección Postal (address)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del pedido de venta.|
| domain        | int       | Identificador del dominio al que pertenece el proyecto.|
| registry      | int       | registry|
| main          | boolean   | Indica si es la dirección principal o no.|
| streetType    | string    | Tipo de vía.|
| address       | string    | Primera parte de la dirección.|
| number        | string    | Número de la dirección.|
| address2      | string    | Segunda parte de la dirección.|
| city          | string    | Ciudad de la dirección.|
| province      | string    | Provincia de la dirección.|
| country       | string    | País de la dirección.|
| zip           | string    | Código postal de la dirección.|
| dirty         | boolean   | Indica si hay que modificar o no la dirección.|
| removed       | boolean   | Indica si hay que borrar o no la dirección.|
| global        | boolean   | Indica si la dirección es global o no.|

#### Estructura Forma de Pago (payMethod)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del pedido de venta.|
| domain        | int       | Identificador del dominio al que pertenece el proyecto.|
| type          | string    | Tipo de Forma de Pago.<br/>Valores permitidos:<ul><li>CASH_BASIS</li><li>NEGOTIABLE_DOCUMENT</li><li>DEBIT_CARD</li><li>CREDIT_CARD</li><li>CHEQUE</li><li>BANK_TRANSFER</li><li>OTHER</li></ul>|
| name          | string    | Nombre Forma de pago.|

#### Estructura Centro de Trabajo (workplace)

| Name |  Type  | Description |
|------|--------|-------------|
| id                | int       | Identificador del pedido de venta.|
| domain            | int       | Identificador del dominio al que pertenece el centro de trabajo.|
| description       | string    | Descripción del centro de trabajo.|
| active            | boolean   | Indica si el centro de trabajo está activo o no.|
| address           | int       | Identificador de la dirección.|
| customer          | int       | Identificador de cliente.|
| economicAgreement | int       | Concierto Económico del Centro de Trabajo.|
| scope             | [object](#estructura-ambito-scope)    | Ámbito del centro de trabajo.|

#### Estructura Ámbito (scope)

| Name |  Type  | Description |
|------|--------|-------------|
| id                | int       | Identificador del pedido de venta.|
| domain            | int       | Identificador del dominio al que pertenece el proyecto.|
| description       | string    | Descripción del ámbito.|

#### Estructura Tipo de comisión (commissionType)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del tipo de comisión.|
| domain        | int       | Identificador del dominio al que pertenece el tipo de comisión.|
| name          | string    | Nombre del tipo de comisión.|
| rate          | double    | Porcentaje de comisión.|

#### Estructura de Artículo (item)

| Name |  Type  | Description |
|------|--------|-------------|
| id                    | int       | Identificador del pedido de venta.|
| domain                | object    | dominio al que pertenece el artículo.|
| detail                | string    | Detalle del artículo.|
| detail2               | string    | Detalle 2 del artículo.|
| detail3               | string    | Detalle 3 del artículo.|
| description           | string    | Descripción del artículo.|
| serialNumber          | string    | Número de serie del artículo.|
| serialDate            | date      | Fecha de serie del artículo.|
| barcode               | string    | Código de barras del artículo.|
| status                | string    | Estado del artículo.<br/>Valores permitidos:<ul><li>ACTIVE</li><li>DISCONTINUED</li></ul>|
| product               | [object](#estructura-de-producto-product)    | Datos del Producto.|
| price                 | double    | Precio del artículo.|
| expensesPercent       | double    | Gastos porcentuales del Artículo.|
| profitPercent         | double    | Porcentaje de beneficio del Artículo.|
| purchasePrice         | double    | Precio de compra del artículo.|
| expensesFixed         | double    | Gastos fijos del Artículo.|
| internet              | boolean   | Visible en internet|
| packFormatTag         | int       | Identificador de la Etiqueta de formato|
| packUnits             | int       | Número de unidades por formato|
| packUnitsTag          | int       | Identificador de la Etiqueta de unidad de envase|
| packMeasurement       | double    | Medida envasada|
| packMeasurementTag    | int       | Identificador de la Etiqueta de unidad de medida|
| stockUnitTag          | int       | Identificador de la Etiqueta de unidad de Stock|

#### Estructura de Producto (product)

| Name |  Type  | Description |
|------|--------|-------------|
| id                    | int       | Identificador del pedido de venta.|
| domain                | object    | dominio al que pertenece el producto.|
| code                  | string    | Código del Producto.|
| name                  | string    | Nombre del Producto.|
| brand                 | [object](#estructura-de-marca-brand)    | Marca del producto.|
| type                  | string    | Tipo de Producto.<br/>Valores permitidos:<ul><li>LABOUR (Mano de Obra)</li><li>SERVICE (Servicio)</li><li>COMMERCIAL_PRODUCT (Product Comercial)</li><li>EXTERNAL_WORK (Trabajo Externo)</li><li>EXPENSE (Gasto)</li><li>PREPAYMENT (Suplidos)</li><li>INCREASE (Recargo)</li><li>AUXILIARY (Auxiliar)</li></ul>|
| kind                  | string    | Valores permitidos:<br/><ul><li>SALE_PURCHASE</li><li>PURCHASE</li><li>SALE</li></ul>|
| status                | string    | Valores permitidos:<br/><ul><li>ACTIVE</li><li>DISCONTINUED</li></ul>|
| vat                   | double    | porcentaje de iva.|
| retention             | double    | porcentaje de retención|
| inventoriable         | boolean   | Indica si el Producto es inventariable|
| serializable          | boolean   | Indica si el Producto es serializable|
| lotable               | boolean   | Indica si el Producto es loteable|
| manufactured          | boolean   | Indica si el Producto es elaborado|
| composition           | boolean   | Indica si el Producto es una Composición|
| compositionPrice      | boolean   | Indica si el Precio lo determina la composición|
| packaged              | boolean   | Indica si el Producto es envasado|
| salesAccount          | [object](#estructura-de-cuenta-contable-account)    | Cuenta contable de ventas|
| purchaseAccount       | [object](#estructura-de-cuenta-contable-account)    | Cuenta contable de compras.|

#### Estructura de Marca (brand)

| Name |  Type  | Description |
|------|--------|-------------|
| id        | int       | Identificador de la marca.|
| domain    | int       | dominio al que pertenece la marca.|
| name      | string    | Nombre de la marca.|

#### Estructura de Categoría (category)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador de la categoría.|
| domain        | int       | dominio al que pertenece la categoría.|
| name          | string    | Nombre de la categoría.|
| detail        | string    | Detalle de la categoría.|
| detail2       | string    | Detalle 2 de la categoría.|
| detail3       | string    | Detalle 3 de la categoría.|
| id            | int       | Identificador de la cuenta contable.|
| domain        | int       | Dominio al que pertenece la cuenta contable.|
| code          | string    | Código de la cuenta contable.|
| description   | string    | Descripción de la cuenta contable.|
| alias         | string    | Alias de la cuenta contable.|
| entryEnabled  | boolean   | Indica si la cuenta contable permite o no apuntes.|
| level         | int       | Nivel de la cuenta contable.|
| active        | boolean   | Indica si la cuenta contable está activa o no.|
| costCenter    | string    | Centro de costo.|

#### Estructura de Cuenta Contable (account)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador de la cuenta contable.|
| domain        | int       | Dominio al que pertenece la cuenta contable.|
| code          | string    | Código de la cuenta contable.|
| description   | string    | Descripción de la cuenta contable.|
| alias         | string    | Alias de la cuenta contable.|
| entryEnabled  | boolean   | Indica si la cuenta contable permite o no apuntes.|
| level         | int       | Nivel de la cuenta contable.|
| active        | boolean   | Indica si la cuenta contable está activa o no.|
| costCenter    | string    | Centro de costo.|

## Guardado de pedidos de venta

Guardar pedido de venta

```shell

# El servicio 'sales' es una llamada PUT
curl --request PUT "https://aon.solutions/ms/api/sales"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```
```json
{
"id": 1,
"domain": 1,

"project": {
    "id": 1,
    "domain": 1,
    "alias": "",
    "type": {
    "id": 1,
    "domain": 1,
    "description": "",
    "active": true,
    "dirty": false
    },
    "name": "",
    "date": "2022-05-09T00:00:00Z",
    "registry": 1,
    "active": true,
    "dirty": false
},
"series": "",
"number": 1,
"purchaseReference": "",
"seller": {
    "id": 1,
    "domain": { "id": 1 },
    "document": "",
    "documentCountry": "",
    "documentType": "",
    "name": "",
    "alias": "",
    "legalPerson": true,
    "nationality": "",
    "confidential": false,
    "global": false,
    "dirty": false,
    "commissionType": {
    "id": 1,
    "domain": 1,
    "name": "",
    "rate": 10.0
    },
    "scope": {
    "id": 1,
    "domain": 1,
    "description": ""
    },
    "active": true
},
"customer": {
    "id": 1,
    "domain": { "id": 1 },
    "document": "",
    "documentCountry": "",
    "documentType": "",
    "name": "",
    "alias": "",
    "legalPerson": true,
    "nationality": "",
    "confidential": false,
    "global": false,
    "dirty": false,
    "account": 1,
    "deliveryGrouped": false,
    "deliveryValuated": false,
    "eInvoice": false,
    "invoicingGroup": 1,
    "projectGrouped": false,
    "surcharge": false,
    "tariff": 1,
    "transaction": "NATIONAL",
    "withholding": false,
    "scope": {
    "id": 1,
    "domain": 1,
    "description": ""
    },
    "status": "ACTIVE"
},
"address": {
    "id": 1,
    "domain": 1,
    "registry": 1,
    "main": true,
    "streetType": "",
    "address": "",
    "number": 2,
    "address2": "",
    "city": "",

    "province": "",
    "country": "",
    "zip": "",
    "dirty": false,
    "removed": false,
    "global": false
},
"date": "2022-05-09T00:00:00Z",
"payMethod": {
    "id": 1,
    "domain": 1,
    "type": "CASH_BASIS",
    "name": ""
},
"confidential": false,
"status": "PENDING",
"type": "NORMAL",
"comments": "",
"remarks": "",
"workplace": {
    "id": 1,
    "domain": 1,
    "name": "",
    "active": true,
    "address": 1,
    "customer": 1,
    "economicAgreement": 1,
    "scope": {
    "id": 1,
    "domain": 1,
    "description": ""
    }
},
"scope": {
    "id": 1,
    "domain": 1,
    "description": ""
},
"deliveryDate": "2022-05-09'T'00:00:00'Z'",
"numberOfPymnts": 1,
"daysToFirstPymnt": 0,
"daysBetweenPymnts": 0,
"pymntDays": 1,

"discount": "0.0",
"bankAccount": "",
"bankAlias": "",
"bic": "",
"carrier": {
    "id": 1,
    "domain": { "id": 1 },
    "document": "",
    "documentCountry": "",
    "documentType": "",
    "name": "",
    "alias": "",
    "legalPerson": true,
    "nationality": "",
    "confidential": false,
    "global": false,
    "dirty": false,
    "scope": {
    "id": 1,
    "domain": 1,
    "description": ""
    },
    "status": "ACTIVE"
},
"shippingAlternativeAddress": "",
"shippingAlternativeAddress2": "",
"shippingAlternativeZip": "",
"shippingAlternativeCity": "",
"shippingAlternativePhone": "",
"shippingAlternativeRecipient": "",
"shippingContact": "",
"shippingPeriod": "",
"details": [
    {
    "id": 1,
    "domain": 1,
    "sales": 1,
    "line": 1,
    "item": {
        "id": 1,
        "domain": 1,
        "detail": "",
        "detail2": "",

        "detail3": "",
        "description": "",
        "serialNumber": "",
        "serialDate": "2022-05-09'T'00:00:00'Z'",
        "barcode": "",
        "status": "ACTIVE",
        "product": {
        "id": 1,
        "domain": { "id": 1 },
        "code": "",
        "name": "",
        "brand": {
            "id": 1,
            "domain": 1,
            "name": ""
        },
        "category": {
            "id": 1,
            "domain": 1,
            "name": "",
            "detail": "",
            "detail2": "",
            "detail3": ""
        },
        "type": "LABOUR",
        "kind": "SALE_PURCHASE",
        "status": "ACTIVE",
        "vat": 21.0,
        "retention": 15.0,
        "inventoriable": true,
        "serializable": true,
        "lotable": true,
        "manufactured": true,
        "composition": true,
        "compositionPrice": true,
        "packaged": true,
        "salesAccount": {
            "id": 1,
            "domain": 1,
            "code": "",
            "description": "",
            "alias": "",
            "entryEnabled": true,

            "level": 1,
            "active": true,
            "costCenter": ""
        },
        "purchaseAccount": {
            "id": 1,
            "domain": 1,
            "code": "",
            "description": "",
            "alias": "",
            "entryEnabled": true,
            "level": 1,
            "active": true,
            "costCenter": ""
        }
        },
        "price": 0.0,
        "expensesPercent": 0.0,
        "profitPercent": 0.0,
        "purchasePrice": 0.0,
        "expensesFixed": 0.0,
        "internet": false,
        "packFormatTag": 1,
        "packUnits": 2,
        "packUnitsTag": 3,
        "packMeasurement": 0.0,
        "packMeasurementTag": 4,
        "stockUnitTag": 5
    },
    "description": "",
    "quantity": 0.0,
    "price": 0.0,
    "discount": "0.0",
    "taxes": 0.0,
    "status": "PENDING",
    "offerDetail": 1,
    "delivered": 0.0,
    "carrier": {},
    "carrierPacking": 1
    }
]
}
```

### HTTP Request

`PUT https://aon.solutions/ms/api/sales`

### Parámetros

#### Estructura Pedido de Venta (sales)
| Name |  Type  | Description |
|------|--------|-------------|
| id                            | int       | Identificador del pedido de venta.    |
| domain                        | int       | Identificador del dominio al que pertenece el pedido de venta. |
| project                       | object    | Proyecto al que pertenece el pedido de venta.|
| series                        | string    | Serie del pedido de venta.|
| number                        | int       | Número del pedido de venta.|
| purchaseReference             | string    | Referencia de compra.|
| seller                        | [object](#estructura-comercial-seller-2)    | Datos del comercial.|
| customer                      | [object](#estructura-cliente-customer-2)    | Datos del cliente.|
| address                       | [object](#estructura-direccion-postal-address-2)    | Dirección postal del cliente.|
| date                          | date      | Fecha del pedido de venta.|
| payMethod                     | [object](#estructura-forma-de-pago-paymethod-2)    | Método de Pago.|
| confidential                  | boolean   | Cierto si el pedido de venta es confidencial.|
| status                        | string    | Estado del pedido de venta.<br/>Valores permitidos:<ul><li>PENDING (Pendiente)</li><li>BLOCKED (Bloqueado)</li><li>SERVED (Servido)</li><li>CLOSED (Cerrado)</li><li>INVOICED (Facturado)</li></ul>|
| type                          | string    | Type del pedido de venta.<br/>Valores permitidos:<ul><li>NORMAL</li><li>SAMPLE</li><li>INTERNET</li><li>DEVOLUTION</li></ul>|
| comments                      | string    | Comentarios del pedido de venta.|
| remarks                       | string    | Observaciones del pedido de venta|
| workplace                     | [object](#estructura-centro-de-trabajo-workplace-2)    | Centro de trabajo al que pertenece el pedido de venta.|
| scope                         | [object](#estructura-ambito-scope-2)    | Ámbito del pedido de venta.|
| deliveryDate                  | date      | Fecha de entrega.|
| numberOfPymnts                | int       | Número de Vencimientos.|
| daysToFirstPymnt              | int       | Días al primer vencimiento.|
| daysBetweenPymnts             | int       | Días entre vencimientos.|
| pymntDays                     | int       | Días de pago.|
| discount                      | string    | Descuento.|
| bankAccount                   | string    | Número de cuenta bancaria.|
| bankAlias                     | string    | Alias del Banco.|
| bic                           | string    | Bic del banco.|
| carrier                       | [object](#estructura-empresa-de-transporte-carrier-2)    | Empresa de Transporte.|
| shippingAlternativeAddress    | string    | Primera parte de la dirección de entrega alternativa.|
| shippingAlternativeAddress2   | string    | Segunda parte de la dirección de entrega alternativa.|
| shippingAlternativeZip        | string    | Código Postal de la dirección de entrega alternativa.|
| shippingAlternativeCity       | string    | Ciudad de la dirección de entrega alternativa.|
| shippingAlternativePhone      | string    | Teléfono de la dirección de entrega alternativa.|
| shippingAlternativeRecipient  | string    | Destinatario de la dirección de entrega alternativa.|
| shippingContact               | string    | Nombre del contacto para la entrega.|
| shippingPeriod                | string    | Periodo de entrega.<br/>Valores permitidos:<ul><li>IN_COMMENTS</li><li>MORNING</li><li>NOON</li><li>AFTERNOON</li><li>BEFORE_10</li><li>BEFORE_12</li><li>OFFICE_HOURS</li><li>AFTER_19</li></ul>|
| details                       | array     | Detalles del pedido de venta.|

#### Estructura Detalle Pedido de Venta (salesDetail)

| Name |  Type  | Description |
|------|--------|-------------|
| id                | int       | Identificador del proyecto.|
| domain            | int       | Identificador del dominio al que pertenece el detalle del pedido de venta.|
| sales             | int       | Identificador del pedido de venta|
| line              | int       | Número de línea de detalle.|
| item              | [object](#estructura-de-articulo-item-2)    | Datos del artículo.|
| description       | string    | Descripción del detalle.|
| quantity          | double    | Cantidad.|
| price             | double    | Precio unitario.|
| discount          | string    | descuento|
| taxes             | double    | impuestos|
| status            | string    | Estado del detalle del pedido de venta.<br/>Valores permitidos:<ul><li>PENDING</li><li>PARTIAL_SETTLED</li><li>SETTLED</li></ul>|
| offerDetail       | int       | Identificador del detalle de presupuesto relacionado.|
| delivered         | double    | Cantidad que ya está enviada.|
| carrier           | [object](#estructura-empresa-de-transporte-carrier-2)    | Empresa de Transporte.|
| carrierPacking    | int       | Identificador del packing list.|

#### Estructura Proyecto (project)

| Name |  Type  | Description |
|------|--------|-------------|
| id        | int       | Identificador del proyecto.|
| domain    | int       | Identificador del dominio al que pertenece el proyecto.|
| alias     | string    | Alias del proyecto|
| type      | [object](#estructura-tipo-de-proyecto-projecttype-2)    | Tipo del proyecto.|
| name      | string    | Nombre del proyecto.|
| date      | date      | Fecha del proyecto.|
| registry  | [object](#estructura-cliente-customer-2)    | Identificador del cliente.|
| active    | boolean   | Cierto si está activo.|
| dirty     | boolean   | Cierto si hay que modificar el proyecto..|

#### Estructura Tipo de Proyecto (projectType)
| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del proyecto.|
| domain        | int       | Identificador del dominio al que pertenece el proyecto.|
| description   | string    | Descripción del tipo de proyecto.|
| active        | boolean   | Cierto si el tipo de proyecto está activo.|
| dirty         | boolean   | Cierto si hay que modificar el tipo.|

#### Estructura Cliente (customer)
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

#### Estructura Comercial (seller)

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
| commissionType    | [object](#estructura-tipo-de-comision-commissiontype-2)    | Tipo de Comisión.|
| scope             | [object](#estructura-ambito-scope-2)    | Ámbito del comercial.|
| active            | boolean   | Cierto si está activo.|

#### Estructura Empresa de Transporte (carrier)


| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del pedido de venta.|
| domain        | object    | Dominio al que pertenece el cliente|
| document      | string    | NIF del cliente|
| documentType  | string    | Tipo de documento.<br/>Valores permitidos:<ul><li>NIF</li><li>CIF</li><li>NIE</li><li>PASSPORT</li><li>WORK_PERMIT</li><li>COMMUNITY_CARD</li><li>OTHER</li></ul>|
| name          | string    | Nombre / Razón social del cliente.|
| alias         | string    | Alias del cliente.|
| legalPerson   | boolean   | Cierto si es persona juridica.|
| nationality   | string    | Nacionalidad del cliente.|
| confidential  | boolean   | Cierto si el cliente es confidencial.|
| global        | boolean   | Cierto si el cliente es de global.|
| dirty         | boolean   | Cierto si hay que modificar el cliente.|
| scope         | [object](#estructura-ambito-scope-2)    | Ámbito de la empresa de transporte.|
| status        | string    | Estado de la empresa de transporte.<br/>Valores permitidos:<ul><li>ACTIVE</li><li>INACTIVE</li><li>BLOCKED</li></ul>|

#### Estructura Dirección Postal (address)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del pedido de venta.|
| domain        | int       | Identificador del dominio al que pertenece el proyecto.|
| registry      | int       | registry|
| main          | boolean   | Indica si es la dirección principal o no.|
| streetType    | string    | Tipo de vía.|
| address       | string    | Primera parte de la dirección.|
| number        | string    | Número de la dirección.|
| address2      | string    | Segunda parte de la dirección.|
| city          | string    | Ciudad de la dirección.|
| province      | string    | Provincia de la dirección.|
| country       | string    | País de la dirección.|
| zip           | string    | Código postal de la dirección.|
| dirty         | boolean   | Indica si hay que modificar o no la dirección.|
| removed       | boolean   | Indica si hay que borrar o no la dirección.|
| global        | boolean   | Indica si la dirección es global o no.|

#### Estructura Forma de Pago (payMethod)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del pedido de venta.|
| domain        | int       | Identificador del dominio al que pertenece el proyecto.|
| type          | string    | Tipo de Forma de Pago.<br/>Valores permitidos:<ul><li>CASH_BASIS</li><li>NEGOTIABLE_DOCUMENT</li><li>DEBIT_CARD</li><li>CREDIT_CARD</li><li>CHEQUE</li><li>BANK_TRANSFER</li><li>OTHER</li></ul>|
| name          | string    | Nombre Forma de pago.|

#### Estructura Centro de Trabajo (workplace)

| Name |  Type  | Description |
|------|--------|-------------|
| id                | int       | Identificador del pedido de venta.|
| domain            | int       | Identificador del dominio al que pertenece el centro de trabajo.|
| description       | string    | Descripción del centro de trabajo.|
| active            | boolean   | Indica si el centro de trabajo está activo o no.|
| address           | int       | Identificador de la dirección.|
| customer          | int       | Identificador de cliente.|
| economicAgreement | int       | Concierto Económico del Centro de Trabajo.|
| scope             | [object](#estructura-ambito-scope-2)    | Ámbito del centro de trabajo.|

#### Estructura Ámbito (scope)

| Name |  Type  | Description |
|------|--------|-------------|
| id                | int       | Identificador del pedido de venta.|
| domain            | int       | Identificador del dominio al que pertenece el proyecto.|
| description       | string    | Descripción del ámbito.|

#### Estructura Tipo de comisión (commissionType)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador del tipo de comisión.|
| domain        | int       | Identificador del dominio al que pertenece el tipo de comisión.|
| name          | string    | Nombre del tipo de comisión.|
| rate          | double    | Porcentaje de comisión.|

#### Estructura de Artículo (item)

| Name |  Type  | Description |
|------|--------|-------------|
| id                    | int       | Identificador del pedido de venta.|
| domain                | object    | dominio al que pertenece el artículo.|
| detail                | string    | Detalle del artículo.|
| detail2               | string    | Detalle 2 del artículo.|
| detail3               | string    | Detalle 3 del artículo.|
| description           | string    | Descripción del artículo.|
| serialNumber          | string    | Número de serie del artículo.|
| serialDate            | date      | Fecha de serie del artículo.|
| barcode               | string    | Código de barras del artículo.|
| status                | string    | Estado del artículo.<br/>Valores permitidos:<ul><li>ACTIVE</li><li>DISCONTINUED</li></ul>|
| product               | [object](#estructura-de-producto-product-2)    | Datos del Producto.|
| price                 | double    | Precio del artículo.|
| expensesPercent       | double    | Gastos porcentuales del Artículo.|
| profitPercent         | double    | Porcentaje de beneficio del Artículo.|
| purchasePrice         | double    | Precio de compra del artículo.|
| expensesFixed         | double    | Gastos fijos del Artículo.|
| internet              | boolean   | Visible en internet|
| packFormatTag         | int       | Identificador de la Etiqueta de formato|
| packUnits             | int       | Número de unidades por formato|
| packUnitsTag          | int       | Identificador de la Etiqueta de unidad de envase|
| packMeasurement       | double    | Medida envasada|
| packMeasurementTag    | int       | Identificador de la Etiqueta de unidad de medida|
| stockUnitTag          | int       | Identificador de la Etiqueta de unidad de Stock|

#### Estructura de Producto (product)

| Name |  Type  | Description |
|------|--------|-------------|
| id                    | int       | Identificador del pedido de venta.|
| domain                | object    | dominio al que pertenece el producto.|
| code                  | string    | Código del Producto.|
| name                  | string    | Nombre del Producto.|
| brand                 | [object](#estructura-de-marca-brand-2)    | Marca del producto.|
| type                  | string    | Tipo de Producto.<br/>Valores permitidos:<ul><li>LABOUR (Mano de Obra)</li><li>SERVICE (Servicio)</li><li>COMMERCIAL_PRODUCT (Product Comercial)</li><li>EXTERNAL_WORK (Trabajo Externo)</li><li>EXPENSE (Gasto)</li><li>PREPAYMENT (Suplidos)</li><li>INCREASE (Recargo)</li><li>AUXILIARY (Auxiliar)</li></ul>|
| kind                  | string    | Valores permitidos:<br/><ul><li>SALE_PURCHASE</li><li>PURCHASE</li><li>SALE</li></ul>|
| status                | string    | Valores permitidos:<br/><ul><li>ACTIVE</li><li>DISCONTINUED</li></ul>|
| vat                   | double    | porcentaje de iva.|
| retention             | double    | porcentaje de retención|
| inventoriable         | boolean   | Indica si el Producto es inventariable|
| serializable          | boolean   | Indica si el Producto es serializable|
| lotable               | boolean   | Indica si el Producto es loteable|
| manufactured          | boolean   | Indica si el Producto es elaborado|
| composition           | boolean   | Indica si el Producto es una Composición|
| compositionPrice      | boolean   | Indica si el Precio lo determina la composición|
| packaged              | boolean   | Indica si el Producto es envasado|
| salesAccount          | [object](#estructura-de-cuenta-contable-account-2)    | Cuenta contable de ventas|
| purchaseAccount       | [object](#estructura-de-cuenta-contable-account-2)    | Cuenta contable de compras.|

#### Estructura de Marca (brand)

| Name |  Type  | Description |
|------|--------|-------------|
| id        | int       | Identificador de la marca.|
| domain    | int       | dominio al que pertenece la marca.|
| name      | string    | Nombre de la marca.|

#### Estructura de Categoría (category)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador de la categoría.|
| domain        | int       | dominio al que pertenece la categoría.|
| name          | string    | Nombre de la categoría.|
| detail        | string    | Detalle de la categoría.|
| detail2       | string    | Detalle 2 de la categoría.|
| detail3       | string    | Detalle 3 de la categoría.|
| id            | int       | Identificador de la cuenta contable.|
| domain        | int       | Dominio al que pertenece la cuenta contable.|
| code          | string    | Código de la cuenta contable.|
| description   | string    | Descripción de la cuenta contable.|
| alias         | string    | Alias de la cuenta contable.|
| entryEnabled  | boolean   | Indica si la cuenta contable permite o no apuntes.|
| level         | int       | Nivel de la cuenta contable.|
| active        | boolean   | Indica si la cuenta contable está activa o no.|
| costCenter    | string    | Centro de costo.|

#### Estructura de Cuenta Contable (account)

| Name |  Type  | Description |
|------|--------|-------------|
| id            | int       | Identificador de la cuenta contable.|
| domain        | int       | Dominio al que pertenece la cuenta contable.|
| code          | string    | Código de la cuenta contable.|
| description   | string    | Descripción de la cuenta contable.|
| alias         | string    | Alias de la cuenta contable.|
| entryEnabled  | boolean   | Indica si la cuenta contable permite o no apuntes.|
| level         | int       | Nivel de la cuenta contable.|
| active        | boolean   | Indica si la cuenta contable está activa o no.|
| costCenter    | string    | Centro de costo.|

### Respuesta
El mismo json pasado como parámetro

## Borrado de pedidos de venta

Borrar pedidos de venta

```shell

# El servicio 'sales' es una llamada DELETE
curl --request DELETE "https://aon.solutions/ms/api/sales"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

```json
    {
    "id": 1
    }
```

### HTTP Request

`DELETE https://aon.solutions/ms/api/sales`

### Parámetros

| Name |  Type  | Description |
|------|--------|-------------|
| id   | int    | Identificador del pedido  |