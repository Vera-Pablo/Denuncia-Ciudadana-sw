# 🖥️ DenunciaCiudadana Client

## 📋 ¿Qué hace el proyecto?

DenunciaCiudadana Client es la aplicación web frontend del sistema de gestión de denuncias ciudadanas. Ofrece una interfaz moderna e intuitiva que permite a los ciudadanos registrar denuncias sobre problemáticas urbanas, dar seguimiento a sus casos y comunicarse directamente con las autoridades a través de un chat bidireccional. Las autoridades cuentan con un panel de administración para gestionar denuncias, actualizar estados, visualizar estadísticas y responder a los ciudadanos.

## 💡 ¿Por qué el proyecto es útil?

- **Experiencia de usuario moderna**: Interfaz construida con una paleta de colores Material-You terrosa y cálida, tipografía Inter, animaciones suaves y diseño responsivo que se adapta a cualquier dispositivo.
- **Accesibilidad para el ciudadano**: Cualquier persona puede registrarse, crear una denuncia con evidencia fotográfica, y darle seguimiento sin necesidad de conocimientos técnicos.
- **Comunicación en tiempo real**: El chat bidireccional con actualizaciones optimistas permite una comunicación fluida e instantánea entre ciudadanos y autoridades sin necesidad de recargar la página.
- **Panel de administración completo**: Las autoridades disponen de un dashboard con gráficos estadísticos (barras y tortas), tablas de denuncias filtrables y la capacidad de actualizar estados y emitir respuestas oficiales.

## ✨ Características Principales

- **Autenticación completa**: Registro, inicio de sesión, recuperación de contraseña vía email y rutas protegidas por rol (Ciudadano / Autoridad).
- **Creación de denuncias**: Formulario con validación en tiempo real, selección de tipo de denuncia, ubicación (calle y número) y carga de evidencia fotográfica vía Cloudinary.
- **Mis denuncias**: Listado de denuncias propias del ciudadano con tarjetas informativas, badges de estado y acceso al detalle completo.
- **Detalle de denuncia (Ciudadano)**: Modal con información completa, panel de respuestas oficiales y acceso directo al chat bidireccional.
- **Chat bidireccional**: Sistema de mensajería con burbujas diferenciadas por rol, actualizaciones optimistas (el mensaje aparece al instante), y modal responsivo (pantalla completa en mobile, modal centrado en desktop).
- **Botón flotante de chat (FAB)**: Acceso rápido a las conversaciones de todas las denuncias desde cualquier pantalla, con menú popup desplegable.
- **Panel de administración**: Tabla de denuncias con filtros por estado, tipo y fecha. Detalle completo con capacidad de cambiar estado y agregar resolución.
- **Dashboard de estadísticas**: Gráficos interactivos con Nivo (barras y tortas) para visualizar la distribución de denuncias por estado y tipo.
- **Gestión de perfil**: Visualización y edición de datos personales del usuario autenticado.
- **Página de contactos**: Directorio de contactos relevantes para la ciudadanía.
- **Notificaciones toast**: Feedback visual inmediato de acciones con Sonner.
- **Diseño responsivo**: Layouts adaptados a mobile, tablet y desktop con sidebars colapsables.

## 🛠️ Tecnologías Utilizadas

| Tecnología | Uso |
|---|---|
| **React 19** | Librería de UI para construir la interfaz |
| **TypeScript** | Tipado estático y seguridad en el código |
| **Vite 8** | Bundler y servidor de desarrollo ultrarrápido |
| **React Router DOM 7** | Enrutamiento SPA con rutas protegidas y layouts anidados |
| **TanStack React Query 5** | Gestión de estado del servidor, caché y actualizaciones optimistas |
| **Zustand** | Gestión de estado global ligero (autenticación) |
| **Tailwind CSS 4** | Framework de utilidades CSS con sistema de diseño personalizado (Material-You) |
| **React Hook Form + Zod** | Formularios con validación de esquemas declarativa |
| **Axios** | Cliente HTTP para la comunicación con la API |
| **Nivo** | Gráficos interactivos (barras y tortas) para el dashboard |
| **React Icons** | Iconografía con Material Design Icons |
| **Sonner** | Notificaciones toast elegantes |
| **Cloudinary** | Servicio de almacenamiento y optimización de imágenes |
| **ESLint** | Linting y calidad de código |

## 🚀 ¿Cómo empezar con el proyecto? (Instalación)

### Prerrequisitos

- [Node.js](https://nodejs.org/) (v18 o superior)
- [npm](https://www.npmjs.com/) (incluido con Node.js)
- El backend [DenunciaCiudadanaAPI](https://github.com/Vera-Pablo/DenunciaCiudadanaAPI) corriendo en `http://localhost:3000`

### Pasos de instalación

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/Vera-Pablo/DenunciaCiudadanaClient.git
   cd DenunciaCiudadanaClient
   ```

2. **Instalar dependencias**
   ```bash
   npm install
   ```

3. **Configurar las variables de entorno**

   Crea un archivo `.env` en la raíz del proyecto con las siguientes variables:
   ```env
   # URL base de la API backend
   VITE_API_URL=http://localhost:3000/api/v1

   # Cloudinary (para la carga de imágenes)
   VITE_CLOUDINARY_CLOUD_NAME=tu_cloud_name
   VITE_CLOUDINARY_UPLOAD_PRESET=tu_upload_preset
   ```

4. **Iniciar el servidor de desarrollo**
   ```bash
   npm run dev
   ```
   La aplicación estará disponible en `http://localhost:5173`.

### Scripts disponibles

| Comando | Descripción |
|---|---|
| `npm run dev` | Inicia el servidor de desarrollo con hot-reload |
| `npm run build` | Compila TypeScript y genera el bundle de producción |
| `npm run preview` | Previsualiza el build de producción localmente |
| `npm run lint` | Ejecuta ESLint para analizar la calidad del código |

## 📁 Estructura Principal del Proyecto

```
DenunciaCiudadanaClient/
├── public/                         # Archivos estáticos públicos (favicon, etc.)
├── src/
│   ├── api/
│   │   └── axios.ts                # Instancia de Axios configurada con interceptores
│   ├── assets/                     # Recursos estáticos (imágenes, SVGs)
│   ├── components/
│   │   ├── layout/                 # Componentes de layout
│   │   │   ├── MainLayout.tsx      # Layout principal para ciudadanos
│   │   │   ├── AuthorityLayout.tsx # Layout para el panel de autoridades
│   │   │   ├── SimpleLayout.tsx    # Layout sin navegación (login, register)
│   │   │   └── Sidebar.tsx         # Barra lateral de navegación
│   │   ├── ui/                     # Componentes UI reutilizables
│   │   │   ├── Badge.tsx           # Badges de estado
│   │   │   ├── Button.tsx          # Botón con variantes
│   │   │   ├── Input.tsx           # Campo de texto
│   │   │   ├── Select.tsx          # Selector desplegable
│   │   │   ├── ErrorMessage.tsx    # Mensaje de error
│   │   │   └── LoadingSpinner.tsx  # Indicador de carga
│   │   ├── ProtectedRoute.tsx      # HOC de rutas protegidas por autenticación y rol
│   │   └── PublicRoute.tsx         # HOC de rutas públicas (redirige si autenticado)
│   ├── features/
│   │   ├── auth/                   # Feature de autenticación
│   │   │   ├── api/                # Llamadas a la API de auth
│   │   │   ├── components/         # Formularios de login, registro, etc.
│   │   │   ├── context/            # AuthProvider y contexto de autenticación
│   │   │   ├── hooks/              # useAuth y hooks de autenticación
│   │   │   ├── schemas/            # Esquemas Zod de validación
│   │   │   ├── types/              # Tipos TypeScript (User, Role, etc.)
│   │   │   └── index.ts            # Barrel export
│   │   └── reports/                # Feature de denuncias
│   │       ├── api/
│   │       │   └── upload.service.ts   # Servicio de carga de imágenes a Cloudinary
│   │       ├── components/
│   │       │   ├── ReportForm.tsx           # Formulario de creación de denuncia
│   │       │   ├── ReportCard.tsx           # Tarjeta de denuncia (ciudadano)
│   │       │   ├── AdminReportCard.tsx      # Tarjeta de denuncia (autoridad)
│   │       │   ├── AdminReportTable.tsx     # Tabla de denuncias (autoridad)
│   │       │   ├── CitizenReportDetailModal.tsx  # Modal de detalle (ciudadano)
│   │       │   ├── ReportDetailModal.tsx    # Modal de detalle (autoridad)
│   │       │   ├── ReportChat.tsx           # Componente de chat con burbujas
│   │       │   ├── ChatModal.tsx            # Modal responsivo del chat
│   │       │   └── FloatingChatButton.tsx   # Botón flotante (FAB) para acceder al chat
│   │       ├── hooks/
│   │       │   ├── useMyReports.ts          # Obtener denuncias del ciudadano
│   │       │   ├── useAdminReports.ts       # Obtener todas las denuncias (autoridad)
│   │       │   ├── useCreateReport.ts       # Crear nueva denuncia
│   │       │   ├── useUpdateReportStatus.ts # Actualizar estado de denuncia
│   │       │   ├── useAddComment.ts         # Agregar comentario (con actualización optimista)
│   │       │   ├── useReportTypes.ts        # Obtener tipos de denuncia
│   │       │   ├── useStatuses.ts           # Obtener estados disponibles
│   │       │   └── useDashboardStats.ts     # Obtener estadísticas para el dashboard
│   │       ├── schemas/            # Esquemas Zod de validación de reportes
│   │       ├── types/              # Tipos TypeScript (Report, Comment, etc.)
│   │       ├── utils/
│   │       │   └── statusHelpers.ts    # Helpers para labels y variantes de estado
│   │       └── index.ts            # Barrel export
│   ├── pages/
│   │   ├── Login.tsx               # Página de inicio de sesión
│   │   ├── Register.tsx            # Página de registro
│   │   ├── ResetPassword.tsx       # Página de recuperación de contraseña
│   │   ├── Dashboard.tsx           # Página principal del ciudadano
│   │   ├── CreateReport.tsx        # Página de creación de denuncia
│   │   ├── MyReports.tsx           # Página de mis denuncias (ciudadano)
│   │   ├── Profile.tsx             # Página de perfil de usuario
│   │   ├── AdminDashboard.tsx      # Panel de administración (autoridad)
│   │   ├── DashboardView.tsx       # Dashboard de estadísticas con gráficos
│   │   └── Contacts.tsx            # Página de contactos
│   ├── App.tsx                     # Componente raíz con enrutamiento
│   ├── main.tsx                    # Punto de entrada de React
│   └── index.css                   # Sistema de diseño (tokens de color, tipografía, sombras)
├── .env                            # Variables de entorno (no incluido en el repo)
├── .gitignore
├── index.html                      # HTML base con Google Fonts y Material Symbols
├── package.json
├── tsconfig.json
├── tsconfig.app.json
├── tsconfig.node.json
├── eslint.config.js
└── vite.config.ts
```

> La arquitectura sigue un patrón **Feature-Based** donde cada dominio funcional (`auth`, `reports`) encapsula sus propios componentes, hooks, tipos, esquemas de validación y llamadas a la API, promoviendo la cohesión y la separación de responsabilidades.
