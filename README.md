
![Inicio Relampago](https://github.com/user-attachments/assets/050dddd9-ce40-4f64-9752-3247aff07764#vitrinedev)

# Diccionario de Variables

## Índice

- [Falabella](#diccionario-de-variables-de-falabella)
- [Mercado Libre](#diccionario-de-variables-de-ventas-de-mercado-libre)
- [París](#diccionario-de-variables-de-ventas-de-parís)
- [Walmart](#diccionario-de-variables-de-ventas-de-walmart)
- [Hites](#diccionario-de-variables-de-ventas-de-hites)
- [Shopify](#diccionario-de-variables-de-ventas-de-shopify)

# Diccionario de Variables de Falabella
<details>
<summary><strong>Diccionario de Variables de Falabella</strong></summary>

| **Atributo** | **Tipo** | **Descripción** | **Valores originales** | **Preprocesado** |
| :--- | :--- | :--- | :--- | :--- |
| **ID del articulo del pedido** | String/Numérico (ID) | Identificador único del artículo dentro del pedido. | **Números enteros grandes** (ej. `124705506`). | Conversión a tipo **`int64`** (entero) o mantenimiento como `string` para evitar errores de precisión. |
| **SKU del vendedor** | String/Numérico (ID) | Stock Keeping Unit (SKU) del producto específico del vendedor. | **Números enteros muy grandes** (ej. `4457798326383`). | Conversión a **`string`** para preservar la integridad del ID. |
| **SKU de Falabella** | String/Numérico (ID) | Stock Keeping Unit (SKU) del producto en el catálogo de Falabella. | **Números enteros** (ej. `137497849`). | Conversión a tipo **`int64`** o mantenimiento como `string`. |
| **Creado el** | Fecha/Timestamp | Fecha y/u hora de creación del pedido. | **String de Fecha/Hora** en formato anglosajón (ej. `"oct 8, 2025 22:35"`). | Conversión a tipo **`datetime`** especificando el formato (`%b %d, %Y %H:%M`). |
| **Numero de pedido** | String/Numérico (ID) | Número de pedido principal. | **Números enteros** (ej. `2994922102`). | Conversión a tipo **`int64`** o mantenimiento como `string`. |
| **ID de pedido** | String/Numérico (ID) | Identificador único del pedido. | **Números enteros** (ej. `1124251233`). | Conversión a tipo **`int64`** o mantenimiento como `string`. |
| **Origen del pedido** | Categórico | Canal de donde proviene el pedido (ej. marketplace, web, app). | **String** con nombre de dominio (ej. `marketplace.falabella.com`). | Si se requiere una variable categórica simple, **extraer solo el dominio principal** (ej. 'falabella.com'). |
| **Moneda del pedido** | Categórico | Tipo de moneda utilizada en el pedido (ej. CLP, USD). | **String** con el código de moneda (ej. `CLP`). | **Mantenimiento como categórico/string.** Verificar si hay múltiples monedas. |
| **Documento requerido** | Categórico | Tipo de documento fiscal requerido (ej. BOLETA, FACTURA). | **String** (ej. `BOLETA`). | **Mantenimiento como categórico/string.** |
| **Nombre del cliente** | String/Geográfico | Nombre completo del cliente. | **String** (ej. `felipe fuentes morales`). | Limpieza de caracteres especiales y **normalización de mayúsculas/minúsculas**. |
| **Correo electronico del cliente** | String/Geográfico | Email del cliente. | **String** (ej. `[correo]@gmail.com`). | **Verificación de formato de email** y estandarización a minúsculas. |
| **Numero de registro nacional** | String/Numérico (ID) | Número de registro o identificación fiscal/nacional del cliente. | **String** que incluye guion y dígito verificador (ej. `17741011-K`). | Para análisis numérico, **eliminar guiones y el dígito verificador**, y convertir a numérico. |
| **Nombre de envio** | String/Geográfico | Nombre de la persona que recibirá el pedido. | **String** (ej. `felipe fuentes morales`). | Limpieza y **normalización**. |
| **Direccion de envio** | String/Geográfico | Línea principal de la dirección de envío. | **String** con nombres de calles/números (ej. `Fray montalva`). | Estandarización de abreviaturas y **detección de nulos**. |
| **Direccion de envio 2** | String/Geográfico | Segunda línea de la dirección de envío (opcional). | **String** o a menudo **vacío**. | Detección y tratamiento de valores nulos (NA). |
| **Direccion de envio 3** | String/Geográfico | Tercera línea de la dirección de envío (opcional). | **String** o a menudo **vacío/numérico** (ej. `211`). | Detección y tratamiento de valores nulos (NA). |
| **Telefono de envio** | String (Identificación) | Número de teléfono principal de contacto para el envío. | **String/Numérico** (no visible en la muestra, se asume formato de dígitos). | Estandarizar a formato numérico (e.g., eliminando prefijos, espacios o guiones). |
| **Telefono de envio 2** | String (Identificación) | Número de teléfono secundario de contacto para el envío. | **String/Numérico** o a menudo **vacío**. | Estandarizar a formato numérico. |
| **Ciudad de envio** | String/Geográfico | Ciudad a donde se enviará el pedido. | **String** (ej. `lo barnechea`). | **Normalización de mayúsculas/minúsculas** y de acentos. |
| **Codigo postal de envio** | String/Numérico (ID) | Código postal de la dirección de envío. | **String/Numérico**. | Conversión a **`string`** si no se requiere para cálculos, o a **`int`** si es un código puramente numérico. |
| **Pais de envio** | String/Geográfico | País de destino del envío. | **String** (ej. `CL`). | **Mantenimiento como categórico/string.** |
| **Barrio de envio** | String/Geográfico | Barrio o comuna de destino del envío. | **String** (ej. `LO BARNECHEA`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Region de envio** | String/Geográfico | Región o estado de destino del envío. | **String** (ej. `METROPOLITANA DE SANTIAGO`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Nombre de facturacion** | String/Geográfico | Nombre de la persona o entidad para la facturación. | **String** (ej. `felipe fuentes morales`). | Limpieza y **normalización**. |
| **Direccion de facturacion** | String/Geográfico | Línea principal de la dirección de facturación. | **String** (ej. `Fray montalva`). | Estandarización de abreviaturas y **detección de nulos**. |
| **Direccion de facturacion 2** | String/Geográfico | Segunda línea de la dirección de facturación (opcional). | **String** o a menudo **vacío**. | Detección y tratamiento de valores nulos (NA). |
| **Direccion de facturacion 3** | String/Geográfico | Tercera línea de la dirección de facturación (opcional). | **String** o a menudo **vacío/numérico** (ej. `211`). | Detección y tratamiento de valores nulos (NA). |
| **Telefono de facturacion** | String (Identificación) | Número de teléfono principal de contacto para la facturación. | **String/Numérico**. | Estandarizar a formato numérico. |
| **Telefono de facturacion 2** | String (Identificación) | Número de teléfono secundario de contacto para la facturación. | **String/Numérico** o a menudo **vacío**. | Estandarizar a formato numérico. |
| **Ciudad de facturacion** | String/Geográfico | Ciudad para la facturación. | **String** (ej. `lo barnechea`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Codigo postal de facturacion** | String/Numérico (ID) | Código postal de la dirección de facturación. | **String/Numérico** (ej. `13115`). | Conversión a **`string`**. |
| **Pais de facturacion** | String/Geográfico | País de la facturación. | **String** (ej. `CL`). | **Mantenimiento como categórico/string.** |
| **Barrio de facturacion** | String/Geográfico | Barrio o comuna para la facturación. | **String** (ej. `LO BARNECHEA`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Region de facturacion** | String/Geográfico | Región o estado de la facturación. | **String** (ej. `METROPOLITANA DE SANTIAGO`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Metodo de pago** | Categórico | Categoría del método de pago utilizado. | **String** (ej. `ecommPay`). | **Mantenimiento como categórico/string.** |
| **Precio pagado** | Numérico (Moneda) | Valor monetario total pagado por el cliente. | **String** con coma como separador de miles y punto decimal (ej. `"176,250.00"`). | **Eliminar comas** y convertir a **tipo `float`** para cálculos. |
| **Precio unitario** | Numérico (Moneda) | Valor monetario del artículo individual. | **String** con coma como separador de miles y punto decimal (ej. `"45,000.00"`). | **Eliminar comas** y convertir a **tipo `float`** para cálculos. |
| **Costo de envio** | Numérico (Moneda) | Valor monetario del costo de envío. | **String** con coma como separador de miles y punto decimal (ej. `"2,990.00"`) o **`0.00`**. | **Eliminar comas** y convertir a **tipo `float`** para cálculos. |
| **Creditos de monedero** | Numérico (Moneda) | Valor monetario de créditos o puntos utilizados. | **String/Numérico** (ej. `0.00`). | Conversión a **tipo `float`**. |
| **Monto de impuestos** | Numérico (Moneda) | Valor monetario de los impuestos aplicados. | **String/Numérico** (ej. `0.00`). | Conversión a **tipo `float`**. |
| **Nombre del articulo** | String/Geográfico | Nombre completo del artículo comprado. | **String** (ej. `Piso Escala Titán Rojo Blanco`). | Limpieza y **normalización**. Puede requerir análisis de texto. |
| **Variacion** | Categórico | Variación del producto (ej. color, talla, modelo). | **String** (ej. `… / …`) o a menudo **vacío**. | Extracción de variaciones si están delimitadas (ej. con `/`) y **detección de nulos**. |
| **Proveedor de envio** | String/Mixto | Nombre del proveedor de envío o paquetería principal. | **String** (ej. `blueexpress`). | **Mantenimiento como categórico/string.** |
| **Tipo de envio** | Categórico | Categoría del tipo de envío (ej. Express, Regular, Dropshipping). | **String** (ej. `Dropshipping`). | **Mantenimiento como categórico/string.** |
| **Tipo de proveedor de envio** | Categórico | Tipo de proveedor de envío. | **String** (ej. `Regular`). | **Mantenimiento como categórico/string.** |
| **Codigo de seguimiento** | String/Numérico (ID) | Código de seguimiento principal del envío. | **Numérico/String** (ej. `9374709503`). | Conversión a **`string`** para evitar la pérdida de ceros a la izquierda. |
| **URL de seguimiento** | String (URL) | Enlace de seguimiento del pedido. | **String** o a menudo **vacío**. | **Detección de nulos** y validación de formato URL. |
| **Proveedor de envio (primer tramo)** | String/Mixto | Proveedor de envío para la primera etapa de la logística. | **Comúnmente vacío** en los registros de la muestra. | **Detección de nulos** y verificación de valores si existen. |
| **Codigo de seguimiento (primer tramo)** | String/Numérico (ID) | Código de seguimiento para el primer tramo. | **Comúnmente vacío** en los registros de la muestra. | **Detección de nulos** y conversión a `string`. |
| **URL de seguimiento (primer tramo)** | String (URL) | Enlace de seguimiento para el primer tramo. | **Comúnmente vacío** en los registros de la muestra. | **Detección de nulos** y validación de formato URL. |
| **Tiempo de envio prometido** | Fecha/Timestamp | Fecha u hora de entrega prometida. | **String de Fecha/Hora** en formato anglosajón (ej. `"oct 6, 2025 22:00"`). | Conversión a tipo **`datetime`** especificando el formato (`%b %d, %Y %H:%M`). |
| **Estado** | Categórico | Estado actual del pedido (ej. `delivered`, `shipped`, `canceled`). | **String** (ej. `delivered`). | **Mantenimiento como categórico/string.** Estandarización de mayúsculas/minúsculas si es necesario. |
| **Canal de cumplimiento** | Categórico | Canal o método de gestión del pedido (ej. Fulfilled by Seller). | **String** (ej. `Fulfilled by Seller`). | **Mantenimiento como categórico/string.** |
| **Motivo de cancelacion** | Categórico | Razón por la cual el pedido fue cancelado (si aplica). | **Comúnmente vacío** en los registros de la muestra. | **Detección de nulos** y creación de una categoría 'No Cancelado' si es necesario. |
| **Nombre Legal** | String/Geográfico | Nombre legal de la entidad o persona asociada a la facturación. | **Comúnmente vacío** en los registros de la muestra. | Limpieza y **normalización**; imputar desde 'Nombre del cliente' si está vacío. |
| **Direccion** | String/Geográfico | Dirección legal o fiscal. | **Comúnmente vacío** en los registros de la muestra. | Estandarización de abreviaturas. |
| **Region** | String/Geográfico | Región o estado legal/fiscal. | **Comúnmente vacío** en los registros de la muestra. | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Ciudad** | String/Geográfico | Ciudad legal/fiscal. | **Comúnmente vacío** en los registros de la muestra. | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Municipalidad** | String/Geográfico | Municipalidad o comuna legal/fiscal. | **Comúnmente vacío** en los registros de la muestra. | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Documento de Identificacion** | String/Numérico (ID) | Tipo de documento de identificación (ej. 'RUT', 'Cédula'). | **Comúnmente vacío** en los registros de la muestra. | **Mantenimiento como categórico/string.** |
| **Numero de Documento** | String/Numérico (ID) | Número de documento de identificación (ej. RUT, Cédula). | **Comúnmente vacío** en los registros de la muestra. | **Mantenimiento como string** para preservar formato. |
| **Actividad Economica** | String/Geográfico | Descripción de la actividad económica (si aplica). | **Comúnmente vacío** en los registros de la muestra. | **Mantenimiento como string.** |
| **Verificador del Documento** | String (Identificación) | Dígito verificador del documento de identificación. | **Comúnmente vacío** en los registros de la muestra. | **Mantenimiento como string.** |
| **Correo Electronico** | String/Geográfico | Correo electrónico de contacto legal/fiscal. | **Comúnmente vacío** en los registros de la muestra. | **Verificación de formato** y estandarización a minúsculas. |
| **Telefono** | String (Identificación) | Teléfono de contacto legal/fiscal. | **Comúnmente vacío** en los registros de la muestra. | Estandarizar a formato numérico. |
</details>

# Diccionario de Variables de Ventas de Mercado Libre

<details>
<summary><strong>Diccionario de Variables de Mercado Libre</strong></summary>

| **Atributo** | **Tipo** | **Descripción** | **Valores originales** | **Preprocesado** |
| :--- | :--- | :--- | :--- | :--- |
| **# de venta** | String/Numérico (ID) | Número de identificación único de la venta/pedido. | **Numérico entero grande** (ej. `2000009404442073`). | Conversión a **`string`** para preservar la integridad del ID. |
| **Fecha de venta** | Fecha/Timestamp | Fecha y hora de la venta. | **String de Fecha/Hora** en formato español (ej. `"30 de septiembre de 2025 19:29 hs."`). | Conversión a **`datetime`** con manejo de la localización y el texto `hs.`. |
| **Estado** | Categórico | Estado actual del pedido (ej. `Entregado`, `Cancelado`). | **String** (ej. `Entregado`). | **Mantenimiento como categórico/string.** Estandarización de mayúsculas/minúsculas. |
| **Descripción del estado** | String/Mixto | Mensaje detallado sobre el estado del pedido. | **String** (ej. `Llegó el 1 de octubre`, `Podrás usar este dinero...`). | **Limpieza de texto** y estandarización; puede ser útil para análisis de sentimiento. |
| **Paquete de varios productos** | Categórico (Booleano) | Indicador de si la venta incluye varios productos en un solo paquete. | **String** (ej. `Sí`, `No`). | Mapear a **Booleano** (`True`/`False`) o **Binario** (`1`/`0`). |
| **Pertenece a un kit** | Categórico (Booleano) | Indicador de si el producto vendido forma parte de un kit o combo. | **String** (ej. `Sí`, `No`). | Mapear a **Booleano** (`True`/`False`) o **Binario** (`1`/`0`). |
| **Unidades** | Numérico (Contador) | Número de unidades vendidas. | **Numérico entero** (ej. `1`, `2`). | Conversión a tipo **`int`**. |
| **Ingresos por productos (CLP)** | Numérico (Moneda) | Ingresos totales de la venta por productos en pesos chilenos. | **Numérico entero** (ej. `68588`, `456576`). | Conversión a tipo **`float`** (moneda). |
| **Cargo por venta e impuestos (CLP)** | Numérico (Moneda) | Total de cargos e impuestos cobrados por la plataforma (valor negativo). | **Numérico entero** (ej. `-11660`, `-74484`). | Conversión a tipo **`float`** (moneda). |
| **Ingresos por envío (CLP)** | Numérico (Moneda) | Ingresos generados por el cobro del envío. | **Numérico entero** o **vacío**. | Conversión a tipo **`float`**; **imputar 0** a valores nulos (NA). |
| **Costos de envío (CLP)** | Numérico (Moneda) | Costos incurridos por el envío. | **Numérico entero** o **vacío**. | Conversión a tipo **`float`**; **imputar 0** a valores nulos (NA). |
| **Anulaciones y reembolsos (CLP)** | Numérico (Moneda) | Monto total de anulaciones y reembolsos. | **Numérico entero** o **vacío**. | Conversión a tipo **`float`**; **imputar 0** a valores nulos (NA). |
| **Total (CLP)** | Numérico (Moneda) | Monto total final después de cargos y costos. | **Numérico entero** o **vacío**. | Conversión a tipo **`float`** (moneda). |
| **Mes de facturación de tus cargos** | Fecha/Timestamp | Mes al que corresponden los cargos de la venta. | **String de mes y año** (ej. `septiembre 2025`). | Conversión a **`datetime`** (primer día del mes) para facilitar el agrupamiento. |
| **Venta por publicidad** | Categórico (Booleano) | Indica si la venta provino de una campaña de publicidad. | **Vacío** o un indicador (ej. `Sí`). | Mapear a **Binario** (`1`/`0`); imputar `0` o `No` a valores nulos. |
| **SKU** | String/Numérico (ID) | Código SKU del producto. | **Alfanumérico/Numérico** (ej. `1007005021254`). | Mantenimiento como **`string`** para preservar ceros a la izquierda. |
| **# de publicación** | String/Numérico (ID) | Identificador de la publicación en Mercado Libre. | **Alfanumérico** (ej. `MLC1084299282`). | **Mantenimiento como string.** |
| **Canal de venta** | Categórico | Plataforma específica donde se realizó la venta. | **String** (ej. `Mercado Libre`, `Mercado Shops`). | **Mantenimiento como categórico/string.** |
| **Título de la publicación** | String/Mixto | Nombre o título del producto. | **String** (ej. `Mesa Auxiliar Plegable Fabricación Nacional Envío Gratis`). | **Limpieza de texto** y normalización. |
| **Variante** | String/Mixto | Características específicas del producto (ej. color, talla). | **String** (ej. `Color : Jerez Negro`). | **Extraer el valor** de la característica (ej. solo `Jerez Negro`). |
| **Precio unitario de venta de la publicación (CLP)** | Numérico (Moneda) | Precio de venta de una unidad del producto publicado. | **Numérico entero** (ej. `25600`). | Conversión a tipo **`float`** (moneda). |
| **Tipo de publicación** | Categórico | Tipo de listado (ej. `Premium`, `Clásica`). | **String** (ej. `Premium`). | **Mantenimiento como categórico/string.** |
| **Factura adjunta** | Categórico (Booleano) | Indica si se adjuntó una factura. | **String** (ej. `Factura adjunta`). | Mapear a **Booleano** (`True`/`False`). |
| **Datos personales o de empresa** | String/Geográfico | Nombre completo del comprador o razón social de la empresa. | **String** (ej. `Ricardo Ulises Castro Serrano`). | Limpieza y **normalización de mayúsculas/minúsculas**. |
| **Tipo y número de documento** | String/Mixto | Tipo y número de identificación fiscal (ej. RUT). | **String** (ej. `RUT 194680848`). | **Separar en dos columnas** (Tipo y Número) si es necesario para análisis fiscal. |
| **Dirección** | String/Geográfico | Dirección fiscal/de facturación. | **String** (ej. `"José Santos Ossa 26, Vallenar, Atacama"`). | **Estandarización** de abreviaturas y limpieza. |
| **Tipo de contribuyente** | Categórico | Categoría del tipo de contribuyente. | **Comúnmente vacío.** | **Detección y tratamiento de nulos** o imputar 'No Aplica'. |
| **Actividad económica** | String/Mixto | Descripción de la actividad económica. | **Comúnmente vacío.** | **Detección y tratamiento de nulos.** |
| **Comprador** | String/Geográfico | Nombre del comprador. | **String** (ej. `Ricardo Ulises Castro Serrano`). | Limpieza y **normalización**. |
| **Negocio** | Categórico (Booleano) | Indica si el comprador es una empresa o persona natural. | **String** (ej. `No`). | Mapear a **Booleano** (`True`/`False`) o **Binario** (`1`/`0`). |
| **Cédula** | String/Numérico (ID) | Número de cédula/identificación del comprador. | **Numérico/String** (ej. `194680848`). | Conversión a **`string`** para preservar el formato. |
| **Domicilio** | String/Geográfico | Dirección de envío del comprador. | **String** (ej. `"José Santos Ossa 26 / Jose Santos Ossa por la subida de la gruta - Vallenar..."`). | **Limpieza de texto adicional** y geocodificación si se necesita alta precisión. |
| **Comuna** | String/Geográfico | Comuna o municipalidad de envío. | **String** (ej. `Vallenar`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Estado.1** | String/Geográfico | Región o estado de envío. | **String** (ej. `Atacama`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Código postal** | String/Numérico (ID) | Código postal de envío. | **Vacío** o un **String/Numérico**. | Conversión a **`string`** si no se requiere para cálculos. |
| **País** | String/Geográfico | País de envío. | **String** (ej. `Chile`). | **Mantenimiento como categórico/string.** |
| **Forma de entrega** | Categórico | Tipo de logística de entrega para el envío. | **String** (ej. `Correo y puntos de despacho`, `Domicilio`). | **Mantenimiento como categórico/string.** |
| **Fecha en camino** | Fecha/Timestamp | Fecha y hora en que el envío salió a ruta. | **String** (ej. `"1 de septiembre \| 23:52"`). | Conversión a **`datetime`** con manejo del separador (`\|`). |
| **Fecha entregado** | Fecha/Timestamp | Fecha y hora de la entrega final. | **String** (ej. `"2 de septiembre \| 18:15"`). | Conversión a **`datetime`**. |
| **Transportista** | Categórico | Nombre del transportista o paquetería. | **String** (ej. `MercadoEnvios`). | **Mantenimiento como categórico/string.** |
| **Número de seguimiento** | String/Numérico (ID) | Código de seguimiento del envío. | **Alfanumérico/UUID** (ej. `23cfd845-e110...`). | **Mantenimiento como string** para preservar el formato. |
| **URL de seguimiento** | String (URL) | Enlace para rastrear el envío. | **URL** o **vacío**. | **Detección de nulos** y validación de formato URL. |
| **Unidades.1** | Numérico (Contador) | Unidades vendidas en caso de devolución. | **Numérico entero** o **vacío** (parece ser parte de la sección Devoluciones). | Conversión a tipo **`int`**; **imputar 0** a valores nulos. |
| **Forma de entrega.1** | Categórico | Forma de entrega asociada a la devolución. | **Vacío** o un **String**. | **Detección de nulos** y **normalización**. |
| **Fecha en camino.1** | Fecha/Timestamp | Fecha en camino asociada a la devolución. | **Vacío** o una **Fecha**. | Conversión a **`datetime`**; **detección de nulos**. |
| **Fecha entregado.1** | Fecha/Timestamp | Fecha de entrega asociada a la devolución. | **Vacío** o una **Fecha**. | Conversión a **`datetime`**; **detección de nulos**. |
| **Transportista.1** | Categórico | Transportista asociado a la devolución. | **Vacío** o un **String**. | **Detección de nulos** y **normalización**. |
| **Número de seguimiento.1** | String/Numérico (ID) | Número de seguimiento asociado a la devolución. | **Vacío** o un **String**. | **Detección de nulos** y **conversión a string**. |
| **URL de seguimiento.1** | String (URL) | URL de seguimiento asociado a la devolución. | **Vacío** o una **URL**. | **Detección de nulos** y validación de URL. |
| **Revisado por Mercado Libre** | Categórico (Booleano) | Indica si la devolución fue revisada por ML. | **String** (ej. `Sí`, `No`) o **vacío**. | Mapear a **Booleano** (`True`/`False`). |
| **Fecha de revisión** | Fecha/Timestamp | Fecha de la revisión de la devolución. | **Vacío** o una **Fecha**. | Conversión a **`datetime`**; **detección de nulos**. |
| **Dinero a favor** | Numérico (Moneda) | Monto de dinero a favor del vendedor por la devolución. | **Numérico** o **vacío**. | Conversión a tipo **`float`**; **imputar 0** a nulos. |
| **Resultado** | Categórico | Resultado final del proceso de devolución. | **String** o **vacío**. | **Mantenimiento como categórico/string.** |
| **Destino** | String/Mixto | Destino de la unidad devuelta. | **String** o **vacío**. | **Mantenimiento como string.** |
| **Motivo del resultado** | String/Mixto | Motivo detallado del resultado de la devolución. | **String** o **vacío**. | **Mantenimiento como string.** |
| **Unidades.2** | Numérico (Contador) | Número de unidades en reclamo. | **Numérico entero** o **vacío** (parece ser parte de la sección Reclamos). | Conversión a tipo **`int`**; **imputar 0** a valores nulos. |
| **Reclamo abierto** | Categórico (Booleano) | Indica si hay un reclamo abierto. | **String** (ej. `Sí`, `No`) o **vacío**. | Mapear a **Booleano** (`True`/`False`) o **Binario** (`1`/`0`). |
| **Reclamo cerrado** | Categórico (Booleano) | Indica si hay un reclamo cerrado. | **String** (ej. `Sí`, `No`) o **vacío**. | Mapear a **Booleano** (`True`/`False`) o **Binario** (`1`/`0`). |
| **Con mediación** | Categórico (Booleano) | Indica si el reclamo requirió la mediación de ML. | **String** (ej. `Sí`, `No`) o **vacío**. | Mapear a **Booleano** (`True`/`False`) o **Binario** (`1`/`0`). |

</details>

# Diccionario de Variables de Ventas de París

| Atributo | Tipo | Descripción | Valores originales | Preprocesado |
| :--- | :--- | :--- | :--- | :--- |
| **Nro_orden** | String/Numérico (ID) | Número de identificación único del pedido/orden. | **Numérico entero** (ej. `3042231950`). | Conversión a **`string`** para evitar pérdida de precisión y tratamiento como identificador. |
| **Nro_Devolucion** | String/Numérico (ID) | Número de identificación de la devolución, si aplica. | **String** (ej. `N/A`) o **vacío**. | **Imputar 0** o **`null`** y **limpiar el string `N/A`**. Mantenimiento como `string`. |
| **Nombre_Cliente** | String/Geográfico | Nombre completo del cliente que realizó la compra. | **String** (ej. `Kevin Alejandro Muñoz Mora`). | Limpieza de caracteres y **normalización de mayúsculas/minúsculas**. |
| **Número de documento** | String/Numérico (ID) | Número de identificación del cliente (ej. RUT). | **Numérico/String** (ej. `183650610`). | Conversión a **`string`** para preservar el formato. |
| **Email_cliente** | String/Geográfico | Correo electrónico de contacto del cliente. | **String** (ej. `kevinalejandro.munozmora@gmail.com`). | **Verificación de formato de email** y estandarización a minúsculas. |
| **Telefono_cliente** | String (Identificación) | Número de teléfono de contacto del cliente. | **String** que incluye prefijo (ej. `+56953375737`). | **Estandarizar a formato numérico** (eliminar `+569` y/o caracteres no numéricos). |
| **Fecha_de_compra** | Fecha/Timestamp | Fecha y hora exactas en que se realizó la compra. | **String de Fecha/Hora** en formato `YYYY-MM-DD HH:MM:SS` (ej. `2025-09-08 16:14:58`). | Conversión a tipo **`datetime`**. |
| **Fecha de entrega al courier** | Fecha/Timestamp | Fecha en que el producto fue entregado al transportista. | **String de Fecha** en formato `YYYY-MM-DD` (ej. `2025-09-09`). | Conversión a tipo **`date`** o **`datetime`** (asumiendo hora 00:00:00). |
| **Fecha de entrega prometida al cliente** | Fecha/Timestamp | Fecha máxima de entrega prometida al cliente. | **String de Fecha** en formato `YYYY-MM-DD` (ej. `2025-09-10`). | Conversión a tipo **`date`** o **`datetime`**. |
| **Nombre_Producto** | String/Mixto | Nombre comercial completo del producto. | **String** (ej. `Bicicleta Artemisa 3 Cambios Shimano Negro`). | **Limpieza de texto** y normalización. |
| **Precio** | Numérico (Moneda) | Precio de lista (sin descuento, si aplica) del producto. | **Numérico con punto decimal** (ej. `159736.0`). | Conversión a tipo **`float`** (moneda). |
| **Precio pago cliente** | Numérico (Moneda) | Precio final pagado por el cliente por el producto. | **Numérico con punto decimal** (ej. `159736.0`). | Conversión a tipo **`float`** (moneda). |
| **Costo_despacho** | Numérico (Moneda) | Monto cobrado al cliente por concepto de envío. | **Numérico con punto decimal** (ej. `9990.0`, `0.0`). | Conversión a tipo **`float`** (moneda). |
| **Comuna** | String/Geográfico | Comuna o municipalidad de destino del envío. | **String** (ej. `La Pintana`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Dirección de envío** | String/Geográfico | Dirección física de entrega. | **String** (ej. `Niebla 12851 Gabriela Mistral`). | **Estandarización** de abreviaturas. |
| **Region** | String/Geográfico | Región o estado de destino del envío. | **String** (ej. `Región Metropolitana`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Sku_marketplace** | String/Numérico (ID) | SKU del producto en la plataforma de venta (marketplace). | **Alfanumérico** (ej. `MK8FJGU07V-1`). | **Mantenimiento como string.** |
| **Sku_seller** | String/Numérico (ID) | SKU del producto proporcionado por el vendedor (seller). | **Numérico/String** (ej. `9626613525477`). | **Mantenimiento como string** para preservar formato. |
| **Estado** | Categórico | Estado actual del pedido (ej. `Entregado`, `Enviado`). | **String** (ej. `Entregado`). | **Mantenimiento como categórico/string.** |
| **Documento** | Categórico | Tipo de documento fiscal emitido para la venta. | **String** (ej. `boleta`). | **Mantenimiento como categórico/string.** |
| **Razón social** | String/Geográfico | Razón social de la empresa de facturación (si aplica). | **Vacío** en la muestra. | **Detección de nulos** y limpieza. |
| **Rut** | String/Numérico (ID) | RUT de la empresa de facturación (si aplica). | **Vacío** en la muestra. | **Detección de nulos** y **conversión a string**. |
| **Giro** | String/Mixto | Giro o actividad económica de la empresa de facturación. | **Vacío** en la muestra. | **Detección de nulos** y limpieza. |
| **Dirección facturación** | String/Geográfico | Dirección de facturación. | **Vacío** en la muestra. | **Detección de nulos** y limpieza. |
| **Comuna.1** | String/Geográfico | Comuna o municipalidad de facturación (columna duplicada/alternativa). | **Vacío** en la muestra. | **Detección de nulos** y **normalización**. |
| **Región** | String/Geográfico | Región o estado de facturación (columna duplicada/alternativa). | **Vacío** en la muestra. | **Detección de nulos** y **normalización**. |
| **Fulfillment** | Categórico (Booleano) | Indica si el pedido fue gestionado por el servicio de Fulfillment. | **String** (ej. `no`). | Mapear a **Booleano** (`True`/`False`) o **Binario** (`1`/`0`). |
| **OPL** | Categórico | Operador Logístico (Courier) asignado. | **String** (ej. `BLUEXPRESS`). | **Mantenimiento como categórico/string.** |




# Diccionario de Variables de Ventas de Walmart

| Atributo | Tipo | Descripción | Valores originales | Preprocesado |
| :--- | :--- | :--- | :--- | :--- |
| **Número de orden de compra** | String/Numérico (ID) | Número de identificación del pedido a nivel de orden de compra. | **Alfanumérico** (ej. `P110476348`). | **Mantenimiento como string** para preservar formato. |
| **Número De Orden** | String/Numérico (ID) | Número de identificación del pedido a nivel de línea o ítem. | **Numérico entero grande** (ej. `8182571000070`). | Conversión a **`string`** para tratar como ID y evitar pérdida de precisión. |
| **Fecha de orden** | Fecha/Timestamp | Fecha en que el cliente realizó el pedido. | **String de Fecha** en formato `YYYY-MM-DD` (ej. `2025-09-09`). | Conversión a tipo **`date`** o **`datetime`**. |
| **Fecha Máxima de entrega a Courier** | Fecha/Timestamp | Fecha límite para que el vendedor entregue el producto al transportista. | **String de Fecha** en formato `YYYY-MM-DD` (ej. `2025-09-10`). | Conversión a tipo **`date`** o **`datetime`**. |
| **Entrega estimada al cliente** | Fecha/Timestamp | Fecha de entrega esperada para el cliente. | **String de Fecha** en formato `YYYY-MM-DD` (ej. `2025-09-15`). | Conversión a tipo **`date`** o **`datetime`**. |
| **Nombre del cliente** | String/Geográfico | Nombre completo del cliente que realizó el pedido. | **String** (ej. `Clienteregistrado Lidercl`). | Limpieza de caracteres y **normalización de mayúsculas/minúsculas**. |
| **Dirección de envío del cliente** | String/Geográfico | Dirección completa de envío, a menudo concatenando todos los campos. | **String largo** que incluye nombre, dirección, comuna, región y teléfono. | **Extraer el número de teléfono** y **dividir** el resto de la dirección en sus componentes si es necesario. |
| **Número de teléfono del cliente** | String (Identificación) | Número de teléfono de contacto del cliente. | **String** que incluye prefijo (ej. `56933327804`). | Estandarizar a formato numérico (eliminar prefijos, espacios o guiones). |
| **Enviar a la dirección 1** | String/Geográfico | Primera línea (calle) de la dirección de envío. | **String** (ej. `PICTON`, `Buenos Aires`). | **Normalización** de nombres de calles. |
| **Enviar a la dirección 2** | String/Geográfico | Segunda línea (número y detalles) de la dirección de envío. | **String** (ej. `3067`, `626,casa`). | **Separar número** de los detalles de la casa/departamento. |
| **Ciudad** | String/Geográfico | Ciudad de destino del envío. | **String** (ej. `Peñaflor`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Estado - Envío** | String/Geográfico | Región o estado de destino del envío. | **String** (ej. `Metropolitana de Santiago`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Código Postal** | String/Numérico (ID) | Código postal de envío. | **Vacío** o un **String/Numérico**. | **Detección de nulos** y mantenimiento como **`string`**. |
| **Nombre de nodo de barco predicho** | String/Geográfico | Nombre predicho para el punto de envío. | **String** (ej. `LEVEM SPA`). | **Mantenimiento como categórico/string.** |
| **ID de nodo de envío previsto** | String/Numérico (ID) | ID del nodo de envío predicho. | **Numérico entero** (ej. `10001496002`). | **Mantenimiento como string** para evitar errores. |
| **Entidad de cumplimiento** | Categórico | Indica quién gestiona la logística (fulfillment). | **String** (ej. `SellerFulfilled`). | **Mantenimiento como categórico/string.** |
| **FLIDs** | String/Numérico (ID) | Identificador logístico (FLIDs). | **Numérico entero** (ej. `1`). | **Mantenimiento como string** o **`int`**. |
| **Número de línea** | Numérico (Contador) | Número de línea dentro de la orden. | **Numérico entero** (ej. `1`). | Conversión a tipo **`int`**. |
| **Número De Línea De Envío** | Numérico (Contador) | Número de línea de envío. | **Numérico entero** (ej. `1`). | Conversión a tipo **`int`**. |
| **UPC** | String/Numérico (ID) | Código Universal de Producto (UPC). | **Numérico/String** (ej. `00800000822446`). | **Mantenimiento como string** para preservar ceros a la izquierda. |
| **Estado** | Categórico | Estado actual del pedido (ej. `Enviado`, `Entregado`). | **String** (ej. `Enviado`). | **Mantenimiento como categórico/string.** |
| **Nombre del producto** | String/Mixto | Nombre del producto. | **String** (ej. `Sábana 2 Plazas 144 Hilos Estampada Trento`). | **Limpieza de texto** y normalización. |
| **Método de envío** | Categórico | Tipo de servicio de envío. | **String** (ej. `STANDARD`). | **Mantenimiento como categórico/string.** |
| **Cantidad** | Numérico (Contador) | Cantidad de unidades de este producto. | **Numérico entero** (ej. `1`). | Conversión a tipo **`int`**. |
| **SKU** | String/Numérico (ID) | SKU del vendedor para el producto. | **Numérico/String** (ej. `8000008224462`). | **Mantenimiento como string** para preservar formato. |
| **Precio** | Numérico (Moneda) | Precio del artículo (antes de descuento, si aplica). | **Numérico con punto decimal** (ej. `2268.0`). | Conversión a tipo **`float`** (moneda). |
| **Costo de envío** | Numérico (Moneda) | Costo de envío asociado a la línea de pedido. | **Numérico con punto decimal** (ej. `699.0`). | Conversión a tipo **`float`** (moneda). |
| **Impuesto** | Numérico (Moneda) | Monto de impuesto cobrado. | **Numérico con punto decimal** (ej. `4124.0`). | Conversión a tipo **`float`** (moneda). |
| **Comisión** | Numérico (Moneda) | Comisión cobrada por la plataforma. | **Numérico con punto decimal** (ej. `3500.0`). | Conversión a tipo **`float`** (moneda). |
| **Descuento** | Numérico (Moneda) | Descuento aplicado al producto. | **Numérico con punto decimal** (ej. `832.0`). | Conversión a tipo **`float`** (moneda). |
| **Portador** | Categórico | Nombre del transportista (carrier). | **String** (ej. `BLUEXPRESS`). | **Mantenimiento como categórico/string.** |
| **Número De Rastreo** | String/Numérico (ID) | Código de seguimiento del envío. | **Numérico/String** (ej. `9348932014`). | **Mantenimiento como string** para evitar la pérdida de ceros a la izquierda. |
| **Rastreo URL** | String (URL) | Enlace para el seguimiento del envío. | **URL** (ej. `https://api.enviame.io/s2/...`). | **Detección de nulos** y validación de formato URL. |
| **Estado de actualización** | String/Mixto | Último estado de actualización del pedido. | **Comúnmente vacío** en la muestra. | **Detección de nulos** y limpieza. |
| **Cantidad de actualización** | Numérico (Contador) | Cantidad de unidades actualizadas (si aplica). | **Comúnmente vacío** en la muestra. | **Detección de nulos** e **imputar 0** si corresponde a una cantidad. |



# Diccionario de Variables de Ventas de Hites

| Atributo | Tipo | Descripción | Valores originales | Preprocesado |
| :--- | :--- | :--- | :--- | :--- |
| **id** | String/Numérico (ID) | Identificador único de la línea de pedido. | Números enteros (ej. `117699`). | Mantenimiento como **`int`** o **`string`**. |
| **orderNumber** | String/Numérico (ID) | Número de la orden de pedido principal. | Números enteros (ej. `2388820101`). | Conversión a **`string`** para tratar como ID. |
| **orderFather** | String/Numérico (ID) | Número de la orden de pedido padre (si es una orden dividida). | Números enteros (ej. `23888201`). | Conversión a **`string`** para tratar como ID. |
| **documentNumber** | String/Numérico (ID) | Número de documento asociado al artículo (si aplica). | String (ej. `No disponible`) o número. | Manejo de la categoría `'No disponible'` como nulo. |
| **sellerOrderNumber** | String/Numérico (ID) | Número de la orden asignado por el vendedor. | Números enteros (ej. `2388820101`). | Conversión a **`string`** para tratar como ID. |
| **creation** | Fecha/Timestamp | Marca de tiempo (timestamp) de la creación del registro/pedido (en formato ISO 8601 con zona horaria). | String de Fecha/Hora (ej. `2025-08-27T16:33:29.000+0000`). | Conversión a tipo **`datetime`** y **normalización a una única zona horaria (UTC)**. |
| **dateSale** | Fecha/Timestamp | Fecha de la venta. | Numérico que representa la fecha (ej. `20250827`). | Conversión a **`datetime`** (formato `YYYYMMDD`). |
| **hourSale** | Fecha/Timestamp | Hora de la venta. | String de hora (ej. `12:33:29`). | Se puede **combinar con `dateSale`** para formar un `datetime` completo. |
| **status** | Categórico/String | Estado principal del pedido. | String en mayúsculas (ej. `ENTREGADA`). | **Estandarización de mayúsculas/minúsculas.** Mantenimiento como categórico. |
| **subStatus** | Categórico/String | Subestado del pedido (estado más detallado). | String en mayúsculas (ej. `ENTREGADA`). | **Estandarización de mayúsculas/minúsculas.** Mantenimiento como categórico. |
| **motive** | Categórico/String | Motivo de la finalización del pedido (ej. `Entregado`, `Cancelado`). | String (ej. `Entregado`). | **Mantenimiento como categórico/string.** |
| **totalProductGrossPrice** | Numérico (Moneda) | Precio total **bruto** de los productos (incluye impuestos). | Numérico entero (ej. `148650`). | Conversión a tipo **`float`** o **`int`** para cálculos. |
| **totalProductNetPrice** | Numérico (Moneda) | Precio total **neto** de los productos (sin impuestos). | Numérico entero (ej. `124916`). | Conversión a tipo **`float`** o **`int`** para cálculos. |
| **totalProductTaxPrice** | Numérico (Moneda) | Monto total de impuestos de los productos. | Numérico entero (ej. `23734`). | Conversión a tipo **`float`** o **`int`** para cálculos. |
| **grossTotalAdjustment** | Numérico (Moneda) | Monto bruto de ajuste total (ej. descuentos/cargos extra a nivel total). | Numérico entero (ej. `0`). | Conversión a tipo **`float`**; **imputar 0** si es un valor de ajuste nulo. |
| **netTotalAdjustment** | Numérico (Moneda) | Monto neto de ajuste total. | Numérico entero (ej. `0`). | Conversión a tipo **`float`**. |
| **taxTotalAdjustment** | Numérico (Moneda) | Monto de impuestos del ajuste total. | Numérico entero (ej. `0`). | Conversión a tipo **`float`**. |
| **grossShippingTotal** | Numérico (Moneda) | Costo total **bruto** del envío. | Numérico entero (ej. `12990`). | Conversión a tipo **`float`** o **`int`**. |
| **netShippingTotal** | Numérico (Moneda) | Costo total **neto** del envío. | Numérico entero (ej. `10916`). | Conversión a tipo **`float`** o **`int`**. |
| **taxShippingTotal** | Numérico (Moneda) | Monto total de impuestos del envío. | Numérico entero (ej. `2074`). | Conversión a tipo **`float`** o **`int`**. |
| **grossTotal** | Numérico (Moneda) | Precio **bruto** total final del pedido (producto + envío + ajustes). | Numérico entero (ej. `161640`). | Conversión a tipo **`float`** o **`int`**. |
| **netTotal** | Numérico (Moneda) | Precio **neto** total final del pedido. | Numérico entero (ej. `135832`). | Conversión a tipo **`float`** o **`int`**. |
| **taxTotal** | Numérico (Moneda) | Monto total de impuestos del pedido. | Numérico entero (ej. `25808`). | Conversión a tipo **`float`** o **`int`**. |
| **grossTotalFather** | Numérico (Moneda) | Precio **bruto** total final del pedido padre. | Numérico entero (ej. `161640`). | Conversión a tipo **`float`** o **`int`**. |
| **netTotalFather** | Numérico (Moneda) | Precio **neto** total final del pedido padre. | Numérico entero (ej. `135832`). | Conversión a tipo **`float`** o **`int`**. |
| **taxTotalFather** | Numérico (Moneda) | Monto total de impuestos del pedido padre. | Numérico entero (ej. `25808`). | Conversión a tipo **`float`** o **`int`**. |
| **type** | Categórico/String | Tipo de registro o transacción. | String (ej. `ORDER`). | **Mantenimiento como categórico/string.** |
| **sellerId** | String/Numérico (ID) | ID del vendedor. | Números enteros (ej. `10156`). | Mantenimiento como **`int`** o **`string`**. |
| **sellerCode** | String/Numérico (ID) | Código del vendedor. | Números enteros (ej. `10156`). | Mantenimiento como **`string`**. |
| **sellerName** | Categórico/String | Nombre comercial del vendedor. | String (ej. `LEVEM SPA`). | Limpieza de texto y **normalización**. |
| **storeId** | String/Numérico (ID) | ID de la tienda asociada (si aplica). | Números enteros (ej. `1`). | Mantenimiento como **`int`** o **`string`**. |
| **storeCode** | String/Numérico (ID) | Código de la tienda. | String (ej. `www.hites.com`). | **Mantenimiento como string.** |
| **storeName** | Categórico/String | Nombre de la tienda/canal de venta. | String (ej. `Hites`). | Limpieza de texto y **normalización**. |
| **originCode** | String/Numérico (ID) | Código de origen de la venta. | String (ej. `003`). | **Mantenimiento como string.** |
| **originName** | Categórico/String | Nombre de origen de la venta. | String (ej. `HITES`). | Limpieza de texto y **normalización**. |
| **customerName** | Categórico/String | Nombre completo del cliente. | String con mezcla de mayúsculas/minúsculas (ej. `Acelimar patty Cardozo medina`). | **Normalización de mayúsculas/minúsculas.** |
| **clientPhone** | Categórico/String | Número de teléfono del cliente. | String con formato de teléfono (ej. `+569 5985...`). | **Estandarizar a formato numérico** (eliminar espacios y `+`). |
| **clientEmail** | Categórico/String | Correo electrónico del cliente. | String de email. | **Estandarización a minúsculas** y validación de formato. |
| **taxation** | Categórico/String | Tipo de régimen tributario/fiscal. | String (ej. `net`). | **Mantenimiento como categórico/string.** |
| **create** | Fecha/Timestamp | Marca de tiempo de creación del registro (alternativo/interno). | String de Fecha/Hora ISO 8601 (ej. `2025-08-27T16:33:29.058+0000`). | Conversión a tipo **`datetime`** y **normalización a una única zona horaria.** |
| **update** | Fecha/Timestamp | Marca de tiempo de la última actualización del registro. | String de Fecha/Hora ISO 8601. | Conversión a tipo **`datetime`** y **normalización a una única zona horaria.** |
| **currency** | Categórico/String | Código de moneda utilizada. | String (ej. `CLP`). | **Mantenimiento como categórico/string.** |
| **errorCode** | Categórico/String | Código de error de la operación. | String (ej. `SUCCESS`) o vacío. | **Manejo de valores nulos/vacíos.** |
| **errorMessage** | Categórico/String | Mensaje de error de la operación. | String (ej. `SUCCESS`) o vacío. | **Manejo de valores nulos/vacíos.** |
| **rutSeller** | String/Numérico (ID) | RUT (Rol Único Tributario) del vendedor. | Numérico entero (ej. `76288540`). | Conversión a **`string`** para preservar formato. |
| **logisticsIntegratorId** | String/Numérico (ID) | ID del integrador logístico. | Números enteros (ej. `1`). | Mantenimiento como **`string`** o **`int`**. |
| **logisticsIntegratorName** | Categórico/String | Nombre del integrador logístico. | String (ej. `Enviame`). | Limpieza de texto y **normalización**. |

# Diccionario de Variables de Ventas de Shopify

| Atributo | Tipo | Descripción | Valores originales | Preprocesado |
| :--- | :--- | :--- | :--- | :--- |
| **Name** | String/Numérico (ID) | Número de identificación de la orden. | String (ej. `#8041`). | Conversión a **`string`** y **extracción del número** (quitar `#`). |
| **Email** | String/Geográfico | Correo electrónico de contacto del cliente. | String (ej. `meli.munoze@gmail.com`). | **Estandarización a minúsculas** y validación de formato. |
| **Financial Status** | Categórico | Estado financiero de la orden (ej. `paid`, `pending`, `refunded`). | String (ej. `paid`). | **Mantenimiento como categórico.** |
| **Paid at** | Fecha/Timestamp | Marca de tiempo de cuándo se pagó la orden. | String de Fecha/Hora con zona horaria (ej. `2025-07-19 15:44:41 -0400`). | Conversión a tipo **`datetime`** y **normalización a UTC**. |
| **Fulfillment Status** | Categórico | Estado de cumplimiento de la orden (ej. `fulfilled`, `unfulfilled`). | String (ej. `fulfilled`). | **Mantenimiento como categórico.** |
| **Fulfilled at** | Fecha/Timestamp | Marca de tiempo de cuándo se completó el cumplimiento. | String de Fecha/Hora con zona horaria (ej. `2025-07-21 12:14:28 -0400`). | Conversión a tipo **`datetime`** y **normalización a UTC**. |
| **Accepts Marketing** | Categórico | Indica si el cliente acepta recibir correos de marketing. | String (ej. `yes`, `no`). | Mapear a **Booleano** (`True`/`False`). |
| **Currency** | Categórico | Código de la moneda de la transacción. | String (ej. `CLP`). | **Mantenimiento como categórico.** |
| **Subtotal** | Numérico (Moneda) | Subtotal de los productos (antes de envío, impuestos o descuentos). | Numérico con decimal (ej. `92000.0`). | Conversión a tipo **`float`** para cálculos. |
| **Shipping** | Numérico (Moneda) | Costo de envío cobrado. | Numérico con decimal (ej. `27822.0`). | Conversión a tipo **`float`** para cálculos. |
| **Taxes** | Numérico (Moneda) | Monto total de impuestos. | Numérico con decimal (ej. `19131.0`). | Conversión a tipo **`float`** para cálculos. |
| **Total** | Numérico (Moneda) | Valor total final de la orden. | Numérico con decimal (ej. `119822.0`). | Conversión a tipo **`float`** para cálculos. |
| **Discount Code** | String/Mixto | Código de descuento utilizado. | String (ej. `OFERTA5000`) o **vacío**. | **Detección de nulos** o imputar `No Discount`. |
| **Discount Amount** | Numérico (Moneda) | Monto del descuento aplicado. | Numérico con decimal (ej. `5000.0`). | Conversión a tipo **`float`** para cálculos. |
| **Shipping Method** | Categórico | Nombre del método de envío utilizado. | String (ej. `FedEx a Domicilio`). | **Mantenimiento como categórico.** |
| **Created at** | Fecha/Timestamp | Marca de tiempo de cuándo se creó la orden. | String de Fecha/Hora con zona horaria. | Conversión a tipo **`datetime`** y **normalización a UTC**. |
| **Lineitem quantity** | Numérico (Contador) | Cantidad de unidades de esta línea de producto. | Numérico entero (ej. `1`). | Conversión a tipo **`int`**. |
| **Lineitem name** | String/Geográfico | Nombre del producto en la línea de pedido. | String (ej. `Red c/ Soportes Repuesto Mesa Ping Pong`). | **Limpieza de texto** y normalización. |
| **Lineitem price** | Numérico (Moneda) | Precio unitario del producto en esta línea. | Numérico con decimal (ej. `12990.0`). | Conversión a tipo **`float`**. |
| **Lineitem compare at price** | Numérico (Moneda) | Precio de comparación (precio de venta original) del producto. | Numérico con decimal o **vacío**. | Conversión a tipo **`float`**. Imputar el `Lineitem price` o `0` a nulos. |
| **Lineitem sku** | String/Mixto | SKU del producto en la línea de pedido. | Alfanumérico (ej. `8000010050020`). | **Mantenimiento como string.** |
| **Lineitem requires shipping** | Categórico | Indica si el artículo requiere envío. | String (ej. `true`, `false`). | Mapear a **Booleano**. |
| **Lineitem taxable** | Categórico | Indica si el artículo está sujeto a impuestos. | String (ej. `true`, `false`). | Mapear a **Booleano**. |
| **Lineitem fulfillment status** | Categórico | Estado de cumplimiento de esta línea de producto. | String (ej. `fulfilled`). | **Mantenimiento como categórico.** |
| **Billing Name** | String/Geográfico | Nombre completo para la facturación. | String (ej. `Melina Muñoz Estevez`). | Limpieza y **normalización**. |
| **Billing Street** | String/Geográfico | Calle de facturación. | String (ej. `Bilbao 1000`). | **Normalización** de nombres de calles. |
| **Billing Address1** | String/Geográfico | Dirección de facturación, línea 1. | String (ej. `8750 DPTO.1203 A`). | **Normalización** de direcciones. |
| **Billing Address2** | String/Geográfico | Dirección de facturación, línea 2 (información adicional). | **Vacío** o String. | **Detección y tratamiento de nulos.** |
| **Billing Company** | String/Geográfico | Nombre de la empresa de facturación (si aplica). | String o **vacío**. | **Detección y tratamiento de nulos.** |
| **Billing City** | String/Geográfico | Ciudad de facturación. | String (ej. `SANTIAGO`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Billing Zip** | String/Geográfico | Código postal de facturación. | String (ej. `8750 DPTO.1203 A`). | **Mantenimiento como string.** |
| **Billing Province** | String/Geográfico | Provincia/Estado de facturación (código corto). | String (ej. `RM`). | **Mantenimiento como categórico.** |
| **Billing Country** | String/Geográfico | País de facturación (código corto). | String (ej. `CL`). | **Mantenimiento como categórico.** |
| **Billing Phone** | String/Geográfico | Teléfono de facturación. | String con prefijo (ej. `+56996302759`). | **Estandarizar a formato numérico** (eliminar espacios y `+`). |
| **Shipping Name** | String/Geográfico | Nombre completo para el envío. | String (ej. `Melina Muñoz Estevez`). | Limpieza y **normalización**. |
| **Shipping Street** | String/Geográfico | Calle de envío. | String (ej. `CLAUDIO ARRAU`). | **Normalización** de nombres de calles. |
| **Shipping Address1** | String/Geográfico | Dirección de envío, línea 1. | String (ej. `8750 DPTO.1203 A`). | **Normalización** de direcciones. |
| **Shipping Address2** | String/Geográfico | Dirección de envío, línea 2. | **Vacío** o String. | **Detección y tratamiento de nulos.** |
| **Shipping Company** | String/Geográfico | Nombre de la empresa de envío (si aplica). | String o **vacío**. | **Detección y tratamiento de nulos.** |
| **Shipping City** | String/Geográfico | Ciudad de envío. | String (ej. `SANTIAGO`). | **Normalización de mayúsculas/minúsculas** y acentos. |
| **Shipping Zip** | String/Geográfico | Código postal de envío. | String (ej. `996302759`). | **Mantenimiento como string.** |
| **Shipping Province** | String/Geográfico | Provincia/Estado de envío (código corto). | String (ej. `RM`). | **Mantenimiento como categórico.** |
| **Shipping Country** | String/Geográfico | País de envío (código corto). | String (ej. `CL`). | **Mantenimiento como categórico.** |
| **Shipping Phone** | String/Geográfico | Teléfono de envío. | String con prefijo (ej. `+56996302759`). | **Estandarizar a formato numérico** (eliminar espacios y `+`). |
| **Notes** | String/Texto Libre | Notas añadidas al pedido por el cliente. | String o **vacío**. | **Limpieza de texto** y tratamiento de nulos. |
| **Note Attributes** | String/Texto Libre | Atributos adicionales del pedido. | String o **vacío**. | **Limpieza de texto** y tratamiento de nulos. |
| **Cancelled at** | Fecha/Timestamp | Marca de tiempo de cuándo se canceló la orden. | String de Fecha/Hora con zona horaria o **vacío**. | Conversión a tipo **`datetime`**. |
| **Payment Method** | Categórico | Método de pago utilizado. | String (ej. `Mercado Pago Checkout Pro`). | **Mantenimiento como categórico.** |
| **Payment Reference** | String/Mixto | Referencia interna del pago. | Alfanumérico (ej. `raXoFNtl7Oauzc1nlOYXChNPw`). | **Mantenimiento como string.** |
| **Refunded Amount** | Numérico (Moneda) | Monto total reembolsado. | Numérico con decimal (ej. `0`). | Conversión a tipo **`float`**. |
| **Vendor** | Categórico | Vendedor/Proveedor del producto (si aplica). | String (ej. `AGM`). | **Mantenimiento como categórico.** |
| **Outstanding Balance** | Numérico (Moneda) | Saldo pendiente (si aplica). | Numérico con decimal (ej. `0`). | Conversión a tipo **`float`**. |
| **Employee** | String/Geográfico | Empleado asociado a la venta. | **Vacío** o Nombre. | **Detección y tratamiento de nulos.** |
| **Location** | String/Geográfico | Ubicación asociada a la venta. | **Vacío** o Nombre. | **Detección y tratamiento de nulos.** |
| **Device ID** | String/Numérico (ID) | ID del dispositivo (si aplica). | **Vacío** o Alfanumérico. | **Mantenimiento como string.** |
| **Id** | String/Numérico (ID) | ID único de la orden (ID interno de Shopify). | Números enteros (ej. `6163980091528`). | **Mantenimiento como string.** |
| **Tags** | Categórico | Etiquetas asignadas al pedido. | String con etiquetas separadas por coma (ej. `etiqueta1,etiqueta2`). | **Separar tags en columnas/filas** para análisis categórico. |
| **Risk Level** | Categórico | Nivel de riesgo de la orden. | String (ej. `Low`). | **Mantenimiento como categórico.** |
| **Source** | Categórico | Fuente o canal de origen del pedido. | String (ej. `web`). | **Mantenimiento como categórico.** |
| **Lineitem discount** | Numérico (Moneda) | Descuento aplicado a la línea de producto. | Numérico con decimal (ej. `0`). | Conversión a tipo **`float`**. |
| **Tax 1 Name** | Categórico | Nombre del impuesto 1 (ej. `VAT 19 %`). | String o **vacío**. | **Mantenimiento como categórico.** |
| **Tax 1 Value** | Numérico (Moneda) | Valor del impuesto 1. | Numérico con decimal (ej. `3829`). | Conversión a tipo **`float`**. |
| **Tax 2 Name** | Categórico | Nombre del impuesto 2. | **Vacío**. | **Mantenimiento como categórico.** |
| **Tax 2 Value** | Numérico (Moneda) | Valor del impuesto 2. | **Vacío**. | Conversión a tipo **`float`**. |
| **Tax 3 Name** | Categórico | Nombre del impuesto 3. | **Vacío**. | **Mantenimiento como categórico.** |
| **Tax 3 Value** | Numérico (Moneda) | Valor del impuesto 3. | **Vacío**. | Conversión a tipo **`float`**. |
| **Tax 4 Name** | Categórico | Nombre del impuesto 4. | **Vacío**. | **Mantenimiento como categórico.** |
| **Tax 4 Value** | Numérico (Moneda) | Valor del impuesto 4. | **Vacío**. | Conversión a tipo **`float`**. |
| **Tax 5 Name** | Categórico | Nombre del impuesto 5. | **Vacío**. | **Mantenimiento como categórico.** |
| **Tax 5 Value** | Numérico (Moneda) | Valor del impuesto 5. | **Vacío**. | Conversión a tipo **`float`**. |
| **Phone** | String/Geográfico | Teléfono del cliente (alternativo/general). | String con prefijo (ej. `+56996302759`). | **Estandarizar a formato numérico.** |
| **Receipt Number** | String/Numérico (ID) | Número de recibo. | Alfanumérico. | **Mantenimiento como string.** |
| **Duties** | String/Mixto | Información sobre aranceles o derechos. | **Vacío**. | **Detección y tratamiento de nulos.** |
| **Billing Province Name** | String/Geográfico | Nombre de la Provincia/Estado de facturación. | String (ej. `Santiago`). | **Normalización de mayúsculas/minúsculas.** |
| **Shipping Province Name** | String/Geográfico | Nombre de la Provincia/Estado de envío. | String (ej. `Santiago`). | **Normalización de mayúsculas/minúsculas.** |
| **Payment ID** | String/Numérico (ID) | ID único del pago. | Alfanumérico. | **Mantenimiento como string.** |
| **Payment Terms Name** | Categórico | Nombre de los términos de pago. | String o **vacío**. | **Mantenimiento como categórico.** |
| **Next Payment Due At** | Fecha/Timestamp | Fecha de próximo pago pendiente. | String de Fecha/Hora con zona horaria o **vacío**. | Conversión a tipo **`datetime`**. |
| **Payment References** | String/Mixto | Referencias de pago adicionales. | Alfanumérico o **vacío**. | **Mantenimiento como string.** |
