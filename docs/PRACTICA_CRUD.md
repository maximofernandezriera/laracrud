# 📝 Práctica: CRUD de Categorías con Laravel + React + Inertia.js

## Información General

| Campo | Valor |
|-------|-------|
| **Módulo** | Desarrollo Web en Entorno Servidor / Cliente |
| **Ciclo** | DAW / DAM |
| **Duración** | 1 semana |
| **Modalidad** | Individual o parejas |
| **Entrega** | Repositorio GitHub |

---

## 🎯 Objetivos de Aprendizaje

Al completar esta práctica, el alumno será capaz de:

1. **Comprender** la arquitectura de una aplicación full-stack moderna
2. **Implementar** operaciones CRUD completas con Laravel y React
3. **Utilizar** Inertia.js como capa de conexión frontend-backend
4. **Aplicar** TypeScript para tipado estático en React
5. **Gestionar** relaciones entre modelos en Eloquent
6. **Diseñar** interfaces de usuario con Tailwind CSS

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

**Tu tarea** es extender este proyecto añadiendo el CRUD de Categorías y relacionándolo con Productos.

---

## 🚀 Requisitos de la Práctica

### Paso 0: Configuración Inicial

```bash
# 1. Hacer fork del repositorio base en GitHub
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

Accede a `http://localhost:8000`, regístrate y comprueba que el CRUD de Productos funciona correctamente.

---

### Tarea 1: CRUD de Categorías (5 puntos)

Implementa un CRUD completo para **Categorías** de productos, siguiendo la misma arquitectura que el CRUD de Productos existente.

#### 1.1 Especificaciones de la tabla `categories`

| Campo | Tipo | Restricciones |
|-------|------|---------------|
| id | bigint | PK, autoincrement |
| name | string(100) | required, unique |
| description | text | nullable |
| color | string(7) | nullable (código hex, ej: #FF5733) |
| active | boolean | default: true |
| created_at | timestamp | auto |
| updated_at | timestamp | auto |

#### 1.2 Backend - Checklist

- [ ] **Migración**: Crear archivo en `database/migrations/`
- [ ] **Modelo**: Crear `app/Models/Category.php` con `$fillable` y `$casts`
- [ ] **Controlador**: Crear `app/Http/Controllers/CategoryController.php` con métodos:
  - `index()` - Listar categorías con Inertia
  - `store()` - Crear categoría (validación + JSON response)
  - `update()` - Actualizar categoría (validación + JSON response)
  - `destroy()` - Eliminar categoría (redirect)
- [ ] **Rutas**: Añadir en `routes/web.php` dentro del grupo autenticado

#### 1.3 Frontend - Checklist

- [ ] **Tipos TypeScript**: Añadir interface `Category` en `resources/js/types/index.d.ts`
- [ ] **Página**: Crear `resources/js/Pages/Categories/Index.tsx`
- [ ] **Componentes**: Crear en `resources/js/Components/Categories/`:
  - `CategoryTable.tsx` - Tabla con listado y acciones
  - `CategoryModal.tsx` - Modal para crear/editar
- [ ] **Navegación**: Añadir enlace "Categorías" en `AuthenticatedLayout.tsx`

---

### Tarea 2: Relación Producto-Categoría (3 puntos)

Implementa una relación **Many-to-One** (muchos productos pertenecen a una categoría).

#### 2.1 Backend - Checklist

- [ ] **Migración**: Crear migración para añadir columna `category_id` a tabla `products`
  ```php
  $table->foreignId('category_id')->nullable()->constrained()->nullOnDelete();
  ```
- [ ] **Modelo Product**: Añadir relación `belongsTo`
  ```php
  public function category(): BelongsTo
  {
      return $this->belongsTo(Category::class);
  }
  ```
- [ ] **Modelo Category**: Añadir relación `hasMany`
  ```php
  public function products(): HasMany
  {
      return $this->hasMany(Product::class);
  }
  ```
- [ ] **Controlador Product**: Modificar `index()` para incluir categorías
  ```php
  'products' => Product::with('category')->orderBy('created_at', 'desc')->get(),
  'categories' => Category::where('active', true)->get(),
  ```

#### 2.2 Frontend - Checklist

- [ ] **Tipos TypeScript**: Actualizar interface `Product` para incluir `category_id` y `category`
- [ ] **Formulario Producto**: Añadir selector de categoría en `ProductModal.tsx`
- [ ] **Tabla Productos**: Mostrar nombre de categoría en `ProductTable.tsx`

---

### Tarea 3: Documentación y Entrega (2 puntos)

#### 3.1 Control de Versiones
- [ ] Commits frecuentes y descriptivos (mínimo 5 commits)
- [ ] Usar formato: `feat:`, `fix:`, `docs:`
- [ ] No subir archivos innecesarios (.env, node_modules, vendor)

#### 3.2 README.md
Actualiza el README con:
- [ ] Tu nombre y fecha
- [ ] Descripción de las funcionalidades añadidas
- [ ] Capturas de pantalla del CRUD de categorías

#### 3.3 Entrega
- [ ] Subir código a tu fork en GitHub
- [ ] Enviar URL del repositorio

---

## 📊 Criterios de Evaluación

Ver [RUBRICA_EVALUACION.md](./RUBRICA_EVALUACION.md) para el desglose completo.

| Tarea | Puntos |
|-------|--------|
| Tarea 1: CRUD de Categorías | 5 |
| Tarea 2: Relación Producto-Categoría | 3 |
| Tarea 3: Documentación y Entrega | 2 |
| **Total** | **10** |

---

## 📅 Fechas

| Hito | Fecha |
|------|-------|
| Publicación del enunciado | [FECHA] |
| Entrega Final | [FECHA + 1 semana] |

---

## 🆘 Recursos de Ayuda

### Documentación Oficial
- [Laravel 12 Docs](https://laravel.com/docs/12.x)
- [Inertia.js Docs](https://inertiajs.com/)
- [React Docs](https://react.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)

### Tutoriales del Proyecto
- [Guía de Desarrollo](./GUIA_DESARROLLO.md) - Tutorial paso a paso
- [Presentación](https://maximofernandezriera.github.io/laracrud/) - Slides explicativas

### Código de Referencia
Estudia el CRUD de Productos existente:
- `app/Http/Controllers/ProductController.php`
- `resources/js/Pages/Products/Index.tsx`
- `resources/js/Components/Products/ProductTable.tsx`
- `resources/js/Components/Products/ProductModal.tsx`

---

## ❓ Preguntas Frecuentes

### ¿Puedo cambiar el diseño visual?
Sí, pero mantén Tailwind CSS como framework de estilos.

### ¿Qué hago si encuentro un bug en el código base?
Documéntalo y corrígelo. ¡Puntos extra si lo reportas!

### ¿Puedo trabajar en pareja?
Sí, pero ambos deben poder explicar todo el código.

---

## 📞 Contacto

- **Profesor**: [Nombre del profesor]
- **Email**: [email@centro.edu]
- **Tutorías**: [Horario y lugar]

---

*Última actualización: Diciembre 2024*
