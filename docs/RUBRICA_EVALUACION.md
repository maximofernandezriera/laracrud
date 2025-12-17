# 📊 Rúbrica de Evaluación: Práctica CRUD Laravel + React

## Información General

| Campo | Valor |
|-------|-------|
| **Puntuación máxima** | 10 puntos (+1.5 bonus) |
| **Puntuación mínima para aprobar** | 5 puntos |
| **Modalidad** | Individual o parejas |

---

## Fase 1: Configuración y Análisis (10% - 1 punto)

### 1.1 Fork y Configuración del Entorno (0.4 puntos)

| Nivel | Puntos | Descripción |
|-------|--------|-------------|
| **Excelente** | 0.4 | Proyecto funciona sin errores. Todas las dependencias instaladas. Base de datos configurada y migraciones ejecutadas. |
| **Bien** | 0.3 | Proyecto funciona con mínimas intervenciones. Faltan algunos detalles de configuración. |
| **Suficiente** | 0.2 | Proyecto funciona pero requiere ajustes manuales para arrancar. |
| **Insuficiente** | 0-0.1 | El proyecto no arranca o tiene errores graves de configuración. |

### 1.2 Análisis del Código Base (0.6 puntos)

| Nivel | Puntos | Descripción |
|-------|--------|-------------|
| **Excelente** | 0.6 | Documento `ANALISIS.md` completo con: estructura de carpetas detallada, flujo de datos Inertia explicado, diagrama de componentes, análisis de rutas y controladores. |
| **Bien** | 0.45 | Análisis completo pero con algunas secciones poco desarrolladas. |
| **Suficiente** | 0.3 | Análisis básico que cubre los puntos principales sin profundidad. |
| **Insuficiente** | 0-0.15 | Análisis incompleto o ausente. |

---

## Fase 2: Nuevas Entidades (30% - 3 puntos)

### 2.1 CRUD de Categorías (1.5 puntos)

#### Backend (0.75 puntos)

| Componente | Puntos | Criterios |
|------------|--------|-----------|
| **Migración** | 0.15 | Tabla creada correctamente con todos los campos especificados, tipos correctos, restricciones aplicadas. |
| **Modelo** | 0.15 | `$fillable` configurado, `$casts` para boolean, relaciones definidas. |
| **Controlador** | 0.30 | Métodos index, store, update, destroy implementados. Validación de datos. Respuestas correctas (Inertia/JSON). |
| **Rutas** | 0.15 | Rutas RESTful definidas, middleware de autenticación aplicado, nombres de ruta asignados. |

#### Frontend (0.75 puntos)

| Componente | Puntos | Criterios |
|------------|--------|-----------|
| **Tipos TypeScript** | 0.15 | Interface `Category` definida correctamente, props tipadas. |
| **Página Index** | 0.25 | Listado de categorías, integración con layout, manejo de estado. |
| **Componentes** | 0.25 | Tabla y modal reutilizables, formulario funcional, validación visual. |
| **Navegación** | 0.10 | Enlace añadido en menú, navegación funcional. |

### 2.2 Relación Producto-Categoría (1.5 puntos)

| Componente | Puntos | Criterios |
|------------|--------|-----------|
| **Migración** | 0.25 | Foreign key `category_id` añadida a products, constraint configurada. |
| **Relaciones Eloquent** | 0.35 | `belongsTo` en Product, `hasMany` en Category, eager loading implementado. |
| **Formulario actualizado** | 0.40 | Selector de categoría en crear/editar producto, categorías cargadas desde backend. |
| **Visualización** | 0.30 | Categoría mostrada en tabla de productos, badge o texto con nombre/color. |
| **Tipos TypeScript** | 0.20 | Interface Product actualizada con category opcional. |

---

## Fase 3: Funcionalidades Avanzadas (30% - 3 puntos)

*El alumno debe implementar mínimo 3 funcionalidades de las siguientes (1 punto cada una):*

### 3.1 Paginación (1 punto)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **Backend** | 0.30 | Uso de `paginate()`, número configurable de items. |
| **Frontend** | 0.40 | Componente de paginación, navegación funcional, estado sincronizado. |
| **UX** | 0.15 | Indicador de página actual, total de páginas/items. |
| **URL** | 0.15 | Parámetro `page` en URL, navegación con botones actualiza URL. |

### 3.2 Búsqueda y Filtros (1 punto)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **Búsqueda** | 0.30 | Campo de búsqueda funcional, búsqueda en múltiples campos. |
| **Filtros** | 0.35 | Mínimo 2 filtros implementados (categoría, estado, precio). |
| **Combinación** | 0.20 | Filtros combinables entre sí y con búsqueda. |
| **UX** | 0.15 | Botón limpiar filtros, feedback visual de filtros activos. |

### 3.3 Ordenación por Columnas (1 punto)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **Funcionalidad** | 0.40 | Click en cabecera ordena, toggle ASC/DESC. |
| **Visual** | 0.25 | Indicador de dirección (flechas), columna activa destacada. |
| **Backend** | 0.20 | Query ordenada según parámetros. |
| **URL** | 0.15 | Parámetros `sort` y `direction` en URL. |

### 3.4 Exportación de Datos (1 punto)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **CSV** | 0.50 | Exportación funcional, todos los campos incluidos, encoding correcto. |
| **Filtros** | 0.25 | Exporta datos filtrados, no todos. |
| **Nombre archivo** | 0.10 | Incluye fecha en nombre. |
| **PDF** (bonus) | 0.15 | Exportación PDF con formato legible. |

### 3.5 Imágenes de Producto (1 punto)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **Upload** | 0.35 | Formulario acepta imágenes, validación de tipo/tamaño. |
| **Almacenamiento** | 0.25 | Imagen guardada en storage, path en BD. |
| **Visualización** | 0.25 | Thumbnail en tabla, imagen completa en detalle/modal. |
| **Preview** | 0.15 | Previsualización antes de subir. |

### 3.6 Soft Deletes (1 punto)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **Implementación** | 0.30 | Trait `SoftDeletes` aplicado, migración con `deleted_at`. |
| **Vista papelera** | 0.35 | Listado de productos eliminados, acceso desde menú. |
| **Restaurar** | 0.20 | Botón restaurar funcional. |
| **Eliminar permanente** | 0.15 | Botón eliminar definitivo con confirmación. |

### 3.7 Historial de Cambios (1 punto)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **Tabla logs** | 0.25 | Migración con campos correctos. |
| **Registro automático** | 0.35 | Eventos CREATE/UPDATE/DELETE capturados. |
| **Vista historial** | 0.25 | Listado de cambios por producto. |
| **Detalle** | 0.15 | Muestra valores anteriores/nuevos, usuario, fecha. |

### 3.8 Dashboard con Estadísticas (1 punto)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **Métricas básicas** | 0.30 | Total productos, por categoría, por estado. |
| **Gráficos** | 0.30 | Mínimo 1 gráfico (Chart.js, Recharts, etc.). |
| **Inventario** | 0.20 | Valor total, productos bajo stock. |
| **Últimos productos** | 0.20 | Listado de últimas adiciones. |

---

## Fase 4: Calidad de Código (15% - 1.5 puntos)

### 4.1 TypeScript (0.5 puntos)

| Nivel | Puntos | Descripción |
|-------|--------|-------------|
| **Excelente** | 0.5 | Sin errores TS, interfaces completas, sin `any`, props tipadas. |
| **Bien** | 0.4 | Pocos errores menores, la mayoría de código tipado. |
| **Suficiente** | 0.25 | Tipado básico, algunos `any` o errores tolerados. |
| **Insuficiente** | 0-0.15 | Muchos errores TS, uso extensivo de `any`. |

### 4.2 Validación (0.5 puntos)

| Nivel | Puntos | Descripción |
|-------|--------|-------------|
| **Excelente** | 0.5 | Validación completa backend y frontend, mensajes en español, feedback visual claro. |
| **Bien** | 0.4 | Validación backend completa, frontend básico. |
| **Suficiente** | 0.25 | Solo validación backend o solo frontend. |
| **Insuficiente** | 0-0.15 | Validación ausente o muy incompleta. |

### 4.3 Código Limpio (0.5 puntos)

| Nivel | Puntos | Descripción |
|-------|--------|-------------|
| **Excelente** | 0.5 | Código legible, bien estructurado, sin duplicación, comentarios útiles, componentes reutilizables. |
| **Bien** | 0.4 | Código organizado con pequeñas mejoras posibles. |
| **Suficiente** | 0.25 | Código funcional pero con problemas de organización o duplicación. |
| **Insuficiente** | 0-0.15 | Código desordenado, difícil de leer o mantener. |

---

## Fase 5: Documentación y Entrega (15% - 1.5 puntos)

### 5.1 Documentación (0.75 puntos)

| Documento | Puntos | Criterios |
|-----------|--------|-----------|
| **README.md** | 0.25 | Instrucciones claras de instalación, descripción del proyecto, screenshots. |
| **DESARROLLO.md** | 0.25 | Descripción de funcionalidades implementadas, decisiones tomadas. |
| **Comentarios código** | 0.25 | Funciones complejas documentadas, JSDoc/PHPDoc donde corresponda. |

### 5.2 Control de Versiones (0.5 puntos)

| Nivel | Puntos | Descripción |
|-------|--------|-------------|
| **Excelente** | 0.5 | +15 commits descriptivos, conventional commits, historial limpio. |
| **Bien** | 0.4 | 10-15 commits, mensajes claros. |
| **Suficiente** | 0.25 | 5-10 commits, algunos mensajes poco descriptivos. |
| **Insuficiente** | 0-0.15 | <5 commits o mensajes tipo "update", "fix". |

### 5.3 Entrega (0.25 puntos)

| Aspecto | Puntos | Criterios |
|---------|--------|-----------|
| **Repositorio** | 0.15 | URL correcta, código accesible, .gitignore correcto. |
| **Puntualidad** | 0.10 | Entregado antes de la fecha límite. |

---

## Bonus (hasta +1.5 puntos)

| Bonus | Puntos | Criterios |
|-------|--------|-----------|
| **Despliegue** | +1.0 | Aplicación desplegada y funcional (Railway, Render, VPS, etc.) |
| **Vídeo demo** | +0.5 | Vídeo de 3-5 min explicando funcionalidades implementadas |
| **+4 funcionalidades** | +0.5 | Implementar más de 3 funcionalidades de la Fase 3 |
| **Tests** | +0.5 | Tests unitarios o de integración (Pest/PHPUnit, Jest) |
| **CI/CD** | +0.25 | GitHub Actions para tests o despliegue automático |
| **Bug fix reportado** | +0.25 | Issue abierta en repo original con bug encontrado y solución |

*Nota: El bonus no puede superar +1.5 puntos adicionales.*

---

## Penalizaciones

| Penalización | Puntos | Motivo |
|--------------|--------|--------|
| **Plagio** | -10 | Código copiado de compañero sin atribución |
| **Sin funcionamiento** | -2 | La aplicación no arranca |
| **Entrega tardía** | -0.5/día | Por cada día de retraso (máx -2) |
| **Sin .gitignore** | -0.25 | Subir node_modules, vendor, .env |
| **Archivos sensibles** | -0.5 | Subir credenciales, API keys, etc. |

---

## Escala de Calificación

| Nota | Rango | Descripción |
|------|-------|-------------|
| **Sobresaliente** | 9-10+ | Todas las fases completas, código excelente, bonus |
| **Notable** | 7-8.9 | Fases obligatorias completas, buen código |
| **Bien** | 6-6.9 | Fases obligatorias con algunos fallos menores |
| **Suficiente** | 5-5.9 | Requisitos mínimos cumplidos |
| **Insuficiente** | <5 | No cumple requisitos mínimos |

---

## Checklist de Autoevaluación

Antes de entregar, verifica:

### Fase 1
- [ ] El proyecto arranca sin errores
- [ ] Documento `ANALISIS.md` completo

### Fase 2
- [ ] CRUD de Categorías funcional
- [ ] Relación Producto-Categoría implementada
- [ ] Selector de categoría en formulario de producto

### Fase 3
- [ ] Mínimo 3 funcionalidades avanzadas implementadas
- [ ] Cada funcionalidad probada y funcional

### Fase 4
- [ ] `npm run types` sin errores
- [ ] Validación en backend y frontend
- [ ] Código limpio y organizado

### Fase 5
- [ ] README.md actualizado
- [ ] Mínimo 10 commits significativos
- [ ] Repositorio GitHub accesible

### Bonus (opcional)
- [ ] Aplicación desplegada
- [ ] Vídeo demo grabado
- [ ] Tests implementados

---

## Ejemplo de Evaluación

### Alumno: Juan Pérez
### Fecha: DD/MM/YYYY

| Fase | Puntos Obtenidos | Puntos Máximos | Comentarios |
|------|------------------|----------------|-------------|
| 1.1 Fork y Config | 0.4 | 0.4 | Correcto |
| 1.2 Análisis | 0.5 | 0.6 | Falta diagrama de componentes |
| 2.1 CRUD Categorías | 1.3 | 1.5 | Modal con pequeño bug visual |
| 2.2 Relación | 1.5 | 1.5 | Correcto |
| 3.1 Paginación | 0.9 | 1.0 | Falta total de items |
| 3.2 Búsqueda | 1.0 | 1.0 | Excelente |
| 3.3 Ordenación | 0.8 | 1.0 | No persiste en URL |
| 4.1 TypeScript | 0.4 | 0.5 | 2 errores menores |
| 4.2 Validación | 0.5 | 0.5 | Completa |
| 4.3 Código limpio | 0.4 | 0.5 | Algo de duplicación |
| 5.1 Documentación | 0.6 | 0.75 | README incompleto |
| 5.2 Git | 0.5 | 0.5 | 18 commits |
| 5.3 Entrega | 0.25 | 0.25 | Puntual |
| **SUBTOTAL** | **9.05** | **10** | |
| Bonus: Despliegue | +0.5 | +1.0 | Desplegado en Railway |
| **TOTAL** | **9.55** | **11.5** | **Sobresaliente** |

---

*Rúbrica v1.0 - Diciembre 2024*
