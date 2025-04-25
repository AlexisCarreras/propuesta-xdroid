# **Proyecto XDroid**

---

## 📚 **Tabla de Contenidos**

1. [📁 Estructura del Proyecto](#estructura-del-proyecto)
2. [⚙️ Decisiones Técnicas](#decisiones-técnicas)
3. [🌿 Git Flow](#git-flow)
4. [📦 Conventional Commits](#conventional-commits)

---

## 📁 Estructura del Proyecto

```
.
├── 📁 public
│   └── 📄 CAT.svg  
├── 📁 src  
│   ├── 📁 app
│   │   ├── 📁 router
│   │   │   ├── 📄 AppRouter.tsx
│   │   │   ├── 📄 PrivateRoute.tsx
│   │   │   ├── 📄 PublicRoute.tsx
│   │   └── 📄 App.tsx
│   ├── 📁 assets
│   ├── 📁 components 
│   │   ├── 📁 dashboard
│   │   ├── 📁 home
│   │   ├── 📁 notifications
│   │   ├── 📁 processed-batches
│   │   ├── 📁 reporting
│   │   ├── 📁 shared
│   │   │   ├── 📁 loading
│   │   │   │   └── 📄 LoadingBackdrop.tsx
│   │   │   ├── 📁 modal
│   │   │   │   └── 📄 ModalConfirm.tsx
│   │   │   ├── 📁 error
│   │   │   │   ├── 📄 ErrorMessage.tsx
│   │   │   │   ├── 📄 errorMessage.module.css
│   │   │   │   └── 📄 ErrorMessage.test.tsx
│   │   ├── 📁 tab-management
│   ├── 📁 containers 
│   │   ├── 📁 dashboard
│   │   ├── 📁 home
│   │   ├── 📁 notifications
│   │   ├── 📁 processed-batches
│   │   ├── 📁 reporting
│   │   └── 📁 tab-management
│   ├── 📁 contexts 
│   │   └── 📄 useThemeStore.ts
│   ├── 📁 hooks
│   │   └── 📁 utils
│   │       └── 📄 useResponsive.ts
│   ├── 📁 layouts
│   │   ├── 📄 MainLayout.tsx
│   │   ├── 📄 layoutUtils.ts
│   │   └── 📄 type.ts
│   ├── 📁 services 
│   │   └── 📁 abm-example
│   │       ├── 📄 getExampleService.ts
│   │       ├── 📄 postExampleService.ts
│   │       ├── 📄 putExampleService.ts
│   │       └── 📄 deleteExampleService.ts
│   ├── 📁 tests 
│   ├── 📁 themes 
│   │   └── 📄 theme.ts
│   ├── 📁 types 
│   ├── 📁 utils 
│   ├── 📄 index.css
│   ├── 📄 main.tsx
│   ├── 📄 queryClient.ts
├── 📄 .eslintrc.cjs
├── 📄 .gitignore
├── 📄 README.md
├── 📄 index.html
├── 📄 package.json
├── 📄 tsconfig.app.json
└── 📄 tsconfig.json
```

## 🧹 Nomenclaturas

- 📁 Carpetas: `kebab-case` → `/processed-batches`  
- 📄 Componentes: `PascalCase` → `ModalConfirm.tsx`  
- 🪝 Hooks/funciones: `camelCase` → `useResponsive.ts`  
- 🌐 Rutas: `kebab-case` → `/user-profile`  
- 🔒 Constantes: `SCREAMING_SNAKE_CASE` → `API_URL`

---

## ⚙️ Decisiones Técnicas

### 1. 📦 Separación de Capas

- Modularización entre componentes, contenedores, ruteos y proveedores.  
- Lazy loading y suspense para optimizar carga inicial.

### 2. 🧠 TypeScript (OPCIONAL)

- Todo el código podría estar tipado con `interface`, `type`, `enum`, dando más claridad y facilitando el mantenimiento.

### 3. 🎨 Material UI

- Uso de componentes MUI y configuración de temas customizados según el look and feel propuesto.

### 4. 🧪 Testing

- RTL, Mocha y Chai para tests. Posibilidad de agregar NYC para coverage(asegurarnos de tener el 100% de test cubiertos).

### 5. 🧼 Prettier + ESLint

- Para tener un formato estándar del código, evitaría conflictos a la hora de mergear. Herramienta de Linteo para configurar un orden (junto a Prettier) en todos los archivos. Orden de importaciones, tabulaciones, etc. Además, al ejecutar nos muestra errores o advertencias a corregir, para poder dejar el código 100% limpio..

### 6. ✅ Zod (OPCIONAL)

- Validación de formularios con esquemas tipados.

### 7. 🧭 React Router Dom

- Soporte para rutas públicas/privadas, redirects, etc.

### 8. 🔗 Peticiones a Servicios (Fetch, Axios ó React Query)

- Fetch para soluciones más directas en los componentes.
- Axios si hay esquemas de servicios.
- React Query serviría para esquemas de servicios con hooks, además de manejar mejor el caché, reintentos y sincronización con query keys.

### 9. 🌍 Estados Globales (Context API ó Zustand)

- Para contextos globales que no requieran mucha configuración, podemos utilizar Context API.
- Si los contextos crecen mucho, podríamos optar por algo más potente como Zustand donde además podemos persistir en storage desde el mismo store.

### 10. ✉️ Conventional Commits (Husky)

- Commitlint + Husky para mantener el formato correcto de los mensajes.

---

## 🌿 Git Flow

```
🌿 main                 → Rama principal de producción (siempre estable)
│
├── 📥 develop          → Rama de integración o pre-producción (estable con últimos cambios)
│   │
│   ├── ✨ feature/xxx  → Nuevas funcionalidades en desarrollo
│   ├── 🐛 bug/xxx      → Correcciones de errores
│   ├── 🧪 test/xxx     → Implementación o mejora de pruebas
│   └── 🛠️ chore/xxx    → Refactor, configuración, ajustes menores
```
Ej. `feature/login-form`, `bugfix/fix-button-color

---

## 📦 Conventional Commits

Los mensajes deben seguir el formato:

```
tipo(scope): descripción
```

Ejemplo:

```
feat(dashboard): consume e implementa datos del servicio
```

| Tipo    | Descripción              |
|---------|--------------------------|
| feat    | Nueva funcionalidad      |
| fix     | Corrección de errores    |
| docs    | Cambios en documentación |
| chore   | Tareas de mantenimiento  |
| test    | Agregado/modificación de tests |
| style   | Cambios de estilos (no funcionales) |

> `scope`: módulo afectado (ej. `dashboard`, `auth`)

- https://www.conventionalcommits.org/en/v1.0.0/

---
