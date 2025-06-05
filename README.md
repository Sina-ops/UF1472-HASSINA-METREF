# UF1472-HASSINA-METREF

Prueba Practica 05/06/2025

Este repositorio contiene una versión modificada de la base de datos **Northwind para PostgreSQL**, desarrollada como proyecto de curso con nuevas funcionalidades y mejoras.

---

## 📋 Descripción del Proyecto
---

La base de datos Northwind ha sido extendida con las siguientes mejoras:

### ✨ Nuevas Funcionalidades
- **Sistema de Categorías Jerárquicas**: Subcategorías para mejor organización.
- **Control de Stock Avanzado**: Alertas automáticas y stock mínimo.
- **Descuentos por Volumen**: Sistema automatizado de descuentos.
- **Auditoría Completa**: Registro de cambios en productos.
- **Vistas de Análisis**: Reportes de ventas y productos.
- **Triggers Inteligentes**: Automatización de procesos.

- ## 🛠️ Tecnologías
- ---

- PostgreSQL 17
- pgAdmin
- SQL Dump
##📁 Estructura del Repositorio
---

añadir una subcarpeta

``` bash
PS C:\Users\database\UF1472-HASSINA-METREF> mkdir -p UF1472-HASSINA-METREF/northwind_modificado
````
``` bash
PS C:\Users\database> cd UF1472-HASSINA-METREF
PS C:\Users\database\UF1472-HASSINA-METREF> tree /f
Listado de rutas de carpetas para el volumen OS
El número de serie del volumen es 3840-5A98
C:.
│   README.md
│
└───UF1472-HASSINA-METREF
    └───northwind_modificado
PS C:\Users\database\UF1472-HASSINA-METREF> dir


    Directorio: C:\Users\database\UF1472-HASSINA-METREF


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        05/06/2025     12:11                UF1472-HASSINA-METREF
-a----        02/06/2025     13:57           1778 README.md


PS C:\Users\database\UF1472-HASSINA-METREF>
```

```BASH
 PS C:\Users\database> git clone https://github.com/Sina-ops/UF1472-HASSINA-METREF.git
```
clonar 
 ``` bash
PS C:\Users\database> git clone https://github.com/Sina-ops/UF1472-HASSINA-METREF.git
``` 

  ##🚀 Instalación Rápida
  ---

 # 1. Clonar repositorio
  
```bash

PS C:\Users\database> git clone https://github.com/Sina-ops/UF1472-HASSINA-METREF
Cloning into 'UF1472-HASSINA-METREF'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (1/1), done.
PS C:\Users\database> cd UF1472-HASSINA-METREF
```

# 2. Crear base de datos
createdb northwind_curso

``` bash
PS C:\Users\database> psql -U postgres -d postgres
Contraseña para usuario postgres:

psql (17.5)
ADVERTENCIA: El código de página de la consola (850) difiere del código
            de página de Windows (1252).
            Los caracteres de 8 bits pueden funcionar incorrectamente.
            Vea la página de referencia de psql «Notes for Windows users»
            para obtener más detalles.
Digite «help» para obtener ayuda.

postgres=# createdb northwind_modificado
postgres-# \q
PS C:\Users\database> createdb -U postgres northwind_modificado
Contraseña:
```
``` bash

C:\Users\database>pg_dump -U postgres -d northwind -F c -f northwind.backup
Contraseña:

```
``` bash

C:\Users\database>pg_dump -U postgres -d northwind --inserts -f northwind_inserts.sql
Contraseña:

```


# 3. Restaurar dump completo



``` bash
C:\Users\database>psql -U postgres -d northwind_modificado -f northwind_inserts.sql
```


##🔍 Funcionalidades Principales
---

1.Modificación de la tabla Products

Voy a modificar la tabla Products para agregar una nueva columna llamada caracteristicas_json. Esta columna servirá para guardar información adicional de cada producto, como su categoría, subcategoría y detalles técnicos, usando el formato JSON.

Añadir columna JSON a la tabla Products

``` SQL
ALTER TABLE Products
ADD COLUMN caracteristicas_json JSONB;
```

Actualizar registros con ejemplos de datos JSON, Aquí añadimos valores para las columnas caracteristicas_json con atributos como "categoria" y "subcategoria".

``` SQL
elect * from products;
UPDATE Products
SET caracteristicas_json = '{
  "categoria": "Agricultura",
  "subcategoria": "Maquinaria",
  "especificaciones": {
    "potencia": "2000",
    "zona": "Seca"
  }
}'
WHERE product_id = 1;

UPDATE Products
SET caracteristicas_json = '{
  "categoria": "Agricultura",
  "subcategoria": "phytoproducto",
  "especificaciones": {
    "NPK": "Cargado",
    "PH": "basico"
  }
}'
WHERE product_id = 2;

UPDATE Products
SET caracteristicas_json = '{
  "categoria": "Agricultura",
  "subcategoria": "zoologia",
  "especificaciones": {
    "material": "vacuna",
    "tipo": "obligatorio"
  }
}'
WHERE product_id = 3;


UPDATE Products
SET caracteristicas_json = '{
  "categoria": "Agricultura",
  "subcategoria": "Fertilizantes",
  "especificaciones": {
    "tipo": "Orgánico",
    "contenido_npk": "10-5-5",
    "presentacion": "Sólido"
  }
}'
WHERE product_id = 10;


UPDATE Products
SET caracteristicas_json = '{
  "categoria": "Agricultura",
  "subcategoria": "Maquinaria",
  "especificaciones": {
    "potencia_hp": "150",
    "tipo": "Tractor de ruedas",
    "marca": "John Deere"
  }
}'
WHERE product_id = 11;


UPDATE Products
SET caracteristicas_json = '{
  "categoria": "Agricultura",
  "subcategoria": "Riego",
  "especificaciones": {
    "tipo": "Goteo",
    "longitud": "500m",
    "presion_agua": "1.5 bar"
  }
}'
WHERE product_id = 12;


UPDATE Products
SET caracteristicas_json = '{
  "categoria": "Agricultura",
  "subcategoria": "Semillas",
  "especificaciones": {
    "variedad": "Híbrido 321",
    "rendimiento_estimado": "10t/ha",
    "resistencia": "Alta a sequía"
  }
}'
WHERE product_id = 13;


UPDATE Products
SET caracteristicas_json = '{
  "categoria": "Agricultura",
  "subcategoria": "Fitosanitarios",
  "especificaciones": {
    "tipo": "Biológico",
    "ingrediente_activo": "Bacillus thuringiensis",
    "aplicacion": "Fumigación foliar"
  }
}'
WHERE product_id = 14;
```


Ejecutar consultas sobre los datos JSON Obtener productos de una categoría específica:

``` SQL
SELECT product_id, Product_Name, caracteristicas_json
FROM Products
WHERE caracteristicas_json ->> 'categoria' = 'Agricultura';
```

Filtrar productos según una subcategoría dentro del JSON:

``` SQL
select product_id, product_Name, caracteristicas_json
from Products
where caracteristicas_json ->> 'subcategoria'='Maquinaria';
```

2. Propuesta Practica

La idea es añadir una columna JSON a la tabla Products para guardar información como tipo de uso, características técnicas o clasificaciones. Así se pueden hacer búsquedas más detalladas sin depender solo de las columnas fijas.
Por ejemplo, podré buscar productos agrícolas que sean “orgánicos” o equipos ambientales con cierta potencia, directamente dentro del campo JSON.
Tendremos como ebjetivo:
Poder filtrar productos según detalles específicos (como subcategoría, potencia, resistencia al clima, etc.) sin modificar el diseño original de la base de datos.

Ejemplo 01: Buscar productos agrícolas que sean orgánicos
```SQL
SELECT product_id, product_name, caracteristicas_json
FROM Products
WHERE caracteristicas_json -> 'especificaciones' ->> 'tipo' = 'Orgánico';
```

Ejemplo 02 r productos ambientales con potencia mayor a 100
``` SQL
SELECT product_id, product_Name, caracteristicas_json
FROM Products
WHERE (caracteristicas_json -> 'especificaciones' ->> 'potencia')::int > 100;
```


##📊 Nuevas Tablas Añadidas

---

subcategories - Categorías jerárquicas

``` SQL
CREATE TABLE subcategories (
    subcategory_id SERIAL PRIMARY KEY,
    category_id INTEGER REFERENCES categories(category_id),
    subcategory_name VARCHAR(100) NOT NULL,
    description TEXT
);
---Ejemplo de insercion
INSERT INTO subcategories (category_id, subcategory_name, description)
VALUES
(3, 'Frutas Orgánicas', 'Frutas cultivadas sin pesticidas ni químicos'),
(3, 'Verduras de Hoja', 'Lechugas, espinacas y otras verduras frescas'),
(3, 'Cereales Integrales', 'Arroz, avena y trigo sin procesar'),
(3, 'Legumbres', 'Lentejas, garbanzos y porotos'),
(3, 'Tubérculos', 'Papa, yuca y otros cultivos subterráneos');
```

volume_discounts - Descuentos por cantidad

``` SQL
CREATE TABLE discounts (
    discount_id SERIAL PRIMARY KEY,
    product_id INTEGER REFERENCES products(product_id),
    min_quantity INTEGER NOT NULL,
    discount_percent NUMERIC(5,2) NOT NULL CHECK (discount_percent BETWEEN 0 AND 100)
);

-- Ejemplo de inserción
INSERT INTO discounts (product_id, min_quantity, discount_percent)
VALUES
(1, 50, 10.00),
(2, 100, 15.00);
```

product_audit - Auditoría de cambios

``` SQL
CREATE TABLE product_audit (
    audit_id SERIAL PRIMARY KEY,
    product_id INTEGER REFERENCES products(product_id),
    changed_by VARCHAR(50),
    change_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    field_changed VARCHAR(50),
    old_value TEXT,
    new_value TEXT
);

-- Ejemplo de inserción
INSERT INTO product_audit (product_id, changed_by, field_changed, old_value, new_value)
VALUES
(1, 'admin', 'unit_price', '20.00', '18.50'),
(2, 'maria.p', 'units_in_stock', '100', '80');
```
stock_alerts - Alertas de inventario

```SQL
CREATE TABLE stock_alerts (
    alert_id SERIAL PRIMARY KEY,
    product_id INTEGER REFERENCES products(product_id),
    alert_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    stock_level INTEGER,
    alert_message TEXT
);

-- Ejemplo de inserción
INSERT INTO stock_alerts (product_id, stock_level, alert_message)
VALUES
(1, 5, 'Critico: quedan menos de 15 unidades'),
(3, 0, 'agotado');
```

##📈 Vistas Creadas

---

---vw_analisis_clientes - Segmentación y comportamiento de clientes

```SQL

create or replace view vw_analisis_cliente as
select cd.customer_desc as comportamiento,
      COUNT(c.customer_id) as cantidad_clientes
from customers c
join customer_customer_demo cc on c.customer_id = cc.customer_id
join customer_demographics cd on cc.customer_type_id = cd.customer_type_id
group  by cd.customer_desc
order by cantidad_clientes desc;
```

-vw_ventas_mensuales - Tendencias de ventas por período

```SQL
create or replace view vw_ventas_mensuales as
select DATE_TRUNC('month', o.order_date)as fecha,
       round(SUM(od.unit_price * od.quantity * (1 - od.discount))::numeric, 2)  as ventas
from orders o
join order_details od on o.order_id = od.order_id
group by date_trunc('month', o.order_date)
order by fecha;
```

-vw_performance_proveedores - Evaluación de proveedores

```SQL
create or replace view vw_performance_proveedores as 
select s.company_name as company,
       p.product_name as product,
       round(SUM(od.unit_price * od.quantity * ( 1 - od.discount))::numeric, 2) as ventas
from suppliers s 
join products p on p.supplier_id = s.supplier_id
join order_details od on p.product_id=od.product_id
group by company, product
order by ventas;

```

##🧪 Validar Instalación

Validado
```SQL

SELECT count(*) FROM subcategories;        -- he puesto 10 ejemplos 
SELECT count(*) FROM discounts;     -- Debe mostrar 8
SELECT count(*) FROM stock_alerts;        -- Debe mostrar varias

-- Probar vistas
SELECT count(*) FROM vw_ventas_mensuales;
SELECT count(*) FROM vw_performance_proveedores;
```

