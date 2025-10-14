
Variables Para Analizar el Resultado:

| Fecha de Venta | Fecha | Producto | Descripción | Precio de Venta Item c/Iva | Cantidad | Descuento | Subtotal | Envío | Tipo de Envío | Comisión | Total | Precio de Venta s/Iva | Iva | P*Q s/ Iva | P*Q s/ Iva - comisión | Pvta s/iva - comisión | Costo Unitario S/ Iva | Costo Total s/ Iva | Margen  Neto | % Margen | Valor Gasto | Margen - Gasto | Ingreso Total | Gasto Total | Costo Asignado | Col27 | Col 28 |
|------|------|------|------|------|------|------|------|------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|-------|
| V1 | V2 | V3 | V4 | V5 | V6 | V7 | V8 | V9 | V10 | V11 | V12 | V13 | V14 | V15 | V16 | V17 | V18 | V19 | V20 | V21 | V22 | V23 | V24 | V25 | V26 | V27 | V28 |
| V1 | V2 | V3 | V4 | V5 | V6 | V7 | V8 | V9 | V10 | V11 | V12 | V13 | V14 | V15 | V16 | V17 | V18 | V19 | V20 | V21 | V22 | V23 | V24 | V25 | V26 | V27 | V28 |

# Diccionario de Variables de Falabella

# Diccionario de Variables (Análisis Específico del Archivo)

| Variable | Tipo | Descripción | Valores originales | Preprocesado |
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










