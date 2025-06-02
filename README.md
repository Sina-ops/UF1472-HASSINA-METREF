# UF1472-HASSINA-METREF

Prueba Practica 05/06/2025

Este repositorio contiene una versión modificada de la base de datos **Northwind para PostgreSQL**, desarrollada como proyecto de curso con nuevas funcionalidades y mejoras.

---

## 📋 Descripción del Proyecto

La base de datos Northwind ha sido extendida con las siguientes mejoras:

### ✨ Nuevas Funcionalidades
- **Sistema de Categorías Jerárquicas**: Subcategorías para mejor organización.
- **Control de Stock Avanzado**: Alertas automáticas y stock mínimo.
- **Descuentos por Volumen**: Sistema automatizado de descuentos.
- **Auditoría Completa**: Registro de cambios en productos.
- **Vistas de Análisis**: Reportes de ventas y productos.
- **Triggers Inteligentes**: Automatización de procesos.

- ## 🛠️ Tecnologías

- PostgreSQL 17
- pgAdmin
- SQL Dump

  ## 📁 Estructura del Repositorio

  
  🚀 Instalación Rápida
  
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

postgres=# createdb northwind_curso
postgres-# \q
PS C:\Users\database> createdb -U postgres northwind_curso
Contraseña:
```
---


# 3. Restaurar dump completo

psql -d northwind_curso -f northwind_modificado.sql

```bash
PS C:\Users\database> pg_dump -U postgres -d northwind_curso -f northwind_modificado.sql
Contraseña:

PS C:\Users\database>
```

restaurar

```bash

PS C:\Users\database> psql -U postgres -d northwind_curso -f northwind_modificado.sql
Contraseña para usuario postgres:
```

🔍 Funcionalidades Principales
