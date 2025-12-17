# 📝 Práctica: Extensión del CRUD Laravel + React + Inertia.js

## Información General

| Campo | Valor |
|-------|-------|
| **Módulo** | Desarrollo Web en Entorno Servidor / Cliente |
| **Ciclo** | DAW / DAM |
| **Duración** | 2-3 semanas |
| **Modalidad** | Individual o parejas |
| **Entrega** | Repositorio GitHub + Despliegue |

---

## 🎯 Objetivos de Aprendizaje

Al completar esta práctica, el alumno será capaz de:

1. **Comprender** la arquitectura de una aplicación full-stack moderna
2. **Implementar** operaciones CRUD con Laravel y React
3. **Utilizar** Inertia.js como capa de conexión frontend-backend
4. **Aplicar** TypeScript para tipado estático en React
5. **Diseñar** interfaces de usuario con Tailwind CSS
6. **Gestionar** relaciones entre modelos en Eloquent
7. **Implementar** funcionalidades avanzadas (paginación, filtros, búsqueda)

---

## 📋 Contexto

Se te proporciona un proyecto base de gestión de productos desarrollado con:

- **Backend**: Laravel 12 + PHP 8.2
- **Frontend**: React 19 + TypeScript 5
- **Integración**: Inertia.js 2
- **Estilos**: Tailwind CSS 4
- **Autenticación**: Laravel Breeze

**Repositorio base**: https://github.com/maximofernandezriera/laracrud

El proyecto actual incluye:
- ✅ Sistema de autenticación completo
- ✅ CRUD básico de Productos
- ✅ Tabla de listado con acciones
- ✅ Modales para crear/editar

**Tu tarea** es extender este proyecto añadiendo nuevas funcionalidades.

---

## 🚀 Requisitos de la Práctica

### Fase 1: Configuración y Análisis (Obligatorio)

#### 1.1 Fork y Configuración
```bash
# 1. Hacer fork del repositorio base
# 2. Clonar tu fork
git clone https://github.com/TU_USUARIO/laracrud.git
cd laracrud

# 3. Instalar dependencias
composer install
npm install

# 4. Configurar entorno
cp .env.example .env
php artisan key:generate
php artisan migrate

# 5. Verificar funcionamiento
php artisan serve
npm run dev
```

#### 1.2 Análisis del Código Base
Documenta en un archivo `docs/ANALISIS.md`:
- Estructura de carpetas del proyecto
- Flujo de datos entre Laravel y React (Inertia)
- Componentes React existentes y su función
- Rutas definidas y sus controladores

---

### Fase 2: Nuevas Entidades (Obligatorio)

#### 2.1 Modelo: Categorías
Implementa un CRUD completo para **Categorías** de productos.

**Especificaciones de la tabla `categories`:**

| Campo | Tipo | Restricciones |
|-------|------|---------------|
| id | bigint | PK, autoincrement |
| name | string(100) | required, unique |
| description | text | nullable |
| color | string(7) | nullable (hex color) |
| active | boolean | default: true |
| created_at | timestamp | auto |
| updated_at | timestamp | auto |

**Tareas:**
- [ ] Crear migración
- [ ] Crear modelo con `$fillable` y `$casts`
- [ ] Crear controlador con métodos CRUD
- [ ] Crear rutas protegidas
- [ ] Crear tipos TypeScript
- [ ] Crear página de listado
- [ ] Crear componentes de tabla y modal
- [ ] Añadir enlace en navegación

#### 2.2 Relación: Producto-Categoría
Implementa una relación **Many-to-One** entre Productos y Categorías.

**Tareas:**
- [ ] Crear migración para añadir `category_id` a `products`
- [ ] Definir relación `belongsTo` en modelo Product
- [ ] Definir relación `hasMany` en modelo Category
- [ ] Modificar formulario de producto para seleccionar categoría
- [ ] Mostrar categoría en la tabla de productos
- [ ] Actualizar tipos TypeScript

---

### Fase 3: Funcionalidades Avanzadas (Elegir mínimo 3)

#### 3.1 Paginación
Implementa paginación en el listado de productos.

**Requisitos:**
- Mostrar 10 productos por página
- Navegación entre páginas (anterior/siguiente/números)
- Mantener parámetros de URL
- Usar `paginate()` de Laravel

**Ejemplo backend:**
```php
public function index(): Response
{
    return Inertia::render('Products/Index', [
        'products' => Product::with('category')
            ->orderBy('created_at', 'desc')
            ->paginate(10),
    ]);
}
```

#### 3.2 Búsqueda y Filtros
Implementa búsqueda en tiempo real y filtros.

**Requisitos:**
- Campo de búsqueda por nombre/descripción
- Filtro por categoría (dropdown)
- Filtro por estado (activo/inactivo/descontinuado)
- Filtro por rango de precio
- Los filtros deben ser combinables

**Ejemplo de URL con filtros:**
```
/products?search=laptop&category=1&status=active&min_price=100&max_price=500
```

#### 3.3 Ordenación por Columnas
Implementa ordenación clickeable en las columnas de la tabla.

**Requisitos:**
- Click en cabecera ordena por esa columna
- Indicador visual de columna ordenada (↑/↓)
- Toggle entre ASC/DESC
- Persistir ordenación en URL

#### 3.4 Exportación de Datos
Implementa exportación de productos.

**Requisitos:**
- Botón "Exportar CSV"
- Botón "Exportar PDF" (opcional)
- Incluir filtros activos en la exportación
- Nombrar archivo con fecha

#### 3.5 Imágenes de Producto
Añade soporte para imágenes de producto.

**Requisitos:**
- Campo `image` en tabla products
- Upload de imagen en formulario
- Previsualización antes de subir
- Thumbnail en tabla de listado
- Almacenamiento en `storage/app/public`

#### 3.6 Soft Deletes
Implementa eliminación suave (papelera).

**Requisitos:**
- Usar `SoftDeletes` de Laravel
- Vista de "Papelera" con productos eliminados
- Botón "Restaurar" producto
- Botón "Eliminar permanentemente"

#### 3.7 Historial de Cambios (Auditoría)
Registra cambios en los productos.

**Requisitos:**
- Tabla `product_logs` con: product_id, user_id, action, old_values, new_values, created_at
- Registrar CREATE, UPDATE, DELETE
- Vista de historial por producto
- Mostrar qué usuario hizo el cambio

#### 3.8 Dashboard con Estadísticas
Crea un dashboard con métricas.

**Requisitos:**
- Total de productos
- Productos por categoría (gráfico)
- Productos por estado
- Valor total del inventario
- Productos con bajo stock (< 10)
- Últimos productos añadidos

---

### Fase 4: Calidad de Código (Obligatorio)

#### 4.1 TypeScript Estricto
- [ ] Sin errores de TypeScript (`npm run types`)
- [ ] Interfaces para todos los datos
- [ ] Props tipadas en componentes
- [ ] Evitar `any`

#### 4.2 Validación
- [ ] Validación en backend (FormRequest o inline)
- [ ] Mensajes de error en español
- [ ] Validación en frontend (feedback visual)

#### 4.3 Código Limpio
- [ ] Nombres descriptivos de variables/funciones
- [ ] Componentes pequeños y reutilizables
- [ ] Comentarios en código complejo
- [ ] Sin código duplicado

---

### Fase 5: Documentación y Entrega (Obligatorio)

#### 5.1 Documentación
Actualiza/crea los siguientes archivos:

- `README.md` - Instrucciones de instalación y uso
- `docs/ANALISIS.md` - Análisis del código base
- `docs/DESARROLLO.md` - Descripción de funcionalidades implementadas
- `docs/DECISIONES.md` - Decisiones técnicas tomadas y justificación

#### 5.2 Control de Versiones
- [ ] Commits frecuentes y descriptivos
- [ ] Usar conventional commits: `feat:`, `fix:`, `docs:`, `refactor:`
- [ ] Mínimo 10 commits significativos
- [ ] No subir archivos innecesarios (.env, node_modules, vendor)

#### 5.3 Entrega
1. **Repositorio GitHub**: URL de tu fork con todo el código
2. **Despliegue** (opcional +1 punto): Aplicación desplegada en servidor
3. **Vídeo demo** (opcional +0.5 puntos): Vídeo de 3-5 min mostrando funcionalidades

---

## 📊 Criterios de Evaluación

Ver [RUBRICA_EVALUACION.md](./RUBRICA_EVALUACION.md) para el desglose completo.

| Fase | Peso |
|------|------|
| Fase 1: Configuración y Análisis | 10% |
| Fase 2: Nuevas Entidades | 30% |
| Fase 3: Funcionalidades Avanzadas | 30% |
| Fase 4: Calidad de Código | 15% |
| Fase 5: Documentación y Entrega | 15% |
| **Bonus** | +1.5 puntos |

---

## 📅 Fechas Importantes

| Hito | Fecha |
|------|-------|
| Publicación del enunciado | [FECHA] |
| Entrega Fase 1 (checkpoint) | [FECHA + 1 semana] |
| Entrega Final | [FECHA + 3 semanas] |
| Defensa/Demo (si aplica) | [FECHA + 3.5 semanas] |

---

## 🆘 Recursos de Ayuda

### Documentación Oficial
- [Laravel 12 Docs](https://laravel.com/docs/12.x)
- [Inertia.js Docs](https://inertiajs.com/)
- [React Docs](https://react.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Tailwind CSS](https://tailwindcss.com/docs)

### Tutoriales del Proyecto
- [Guía de Desarrollo](./GUIA_DESARROLLO.md)
- [Presentación](./presentacion.html)

### Proyectos de Referencia
- [Ayoub-Gaouet/Crud-Laravel](https://github.com/Ayoub-Gaouet/Crud-Laravel)
- [Laravel Breeze + React](https://github.com/laravel/breeze)

---

## ❓ Preguntas Frecuentes

### ¿Puedo usar librerías adicionales?
Sí, siempre que las documentes en el README y justifiques su uso.

### ¿Puedo cambiar el diseño visual?
Sí, pero mantén Tailwind CSS como framework de estilos.

### ¿Qué hago si encuentro un bug en el código base?
Documéntalo y corrígelo. Suma puntos extra si lo reportas.

### ¿Puedo trabajar en pareja?
Sí, pero ambos deben poder explicar todo el código en la defensa.

---

## 📞 Contacto

- **Profesor**: [Nombre del profesor]
- **Email**: [email@centro.edu]
- **Tutorías**: [Horario y lugar]

---

*Última actualización: Diciembre 2024*
