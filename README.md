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

---

## 📁 Estructura del Repositorio

# 1. Clonar repositorio
git clone https://github.com/tu-usuario/northwind-postgres-modificado.git
cd northwind-postgres-modificado

# 2. Crear base de datos
createdb northwind_curso

# 3. Restaurar dump completo
psql -d northwind_curso -f northwind_modificado.sql
