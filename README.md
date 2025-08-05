# -SS2_S22025_201902259

# Diseño de Modelo Dimensional

## Esquema Estrella

- Es más sencillo de implementar.  
- Es rápido para consultas OLAP.  
- Se adapta bien a ventas y compras históricas.

---

## Tablas de Hechos

### HechosVentas

- `IdTiempo` (FK)  
- `IdProducto` (FK)  
- `IdSucursal` (FK)  
- `IdCliente` (FK)  
- `CantidadVendida`  
- `PrecioVenta`  
- `TotalVenta`  

### HechosCompras

- `IdTiempo` (FK)  
- `IdProducto` (FK)  
- `IdSucursal` (FK)  
- `IdProveedor` (FK)  
- `CantidadComprada`  
- `CostoCompra`  
- `TotalCompra`  

---

## Tablas de Dimensiones

### DimTiempo

- `IdTiempo` (PK)  
- `Año`  
- `Mes`  
- `Día`  
- `Trimestre`  

### DimProducto

- `IdProducto` (PK)  
- `NombreProducto`  
- `Categoría`  
- `SubCategoría`  
- `Marca`  

### DimSucursal

- `IdSucursal` (PK)  
- `NombreSucursal`  
- `Región`  
- `Ciudad`  

### DimCliente

- `IdCliente` (PK)  
- `NombreCliente`  
- `Segmento`  

### DimProveedor

- `IdProveedor` (PK)  
- `NombreProveedor`  
- `TipoProveedor`  
- `País`  

---

## Justificación del Diseño

Se utiliza un modelo estrella debido a que las tablas de hechos se conectan directamente a las dimensiones, lo que facilita la consulta y optimiza el rendimiento OLAP.  
Las dimensiones representan los ejes de análisis solicitados en el enunciado: **tiempo, producto, sucursal, cliente y proveedor**.  

Las medidas son los valores numéricos relevantes para el negocio: **ventas, compras, cantidades, costos**.  
Las jerarquías permiten análisis agregados por:  
- `Año → Mes → Día`  
- `Región → Ciudad`
