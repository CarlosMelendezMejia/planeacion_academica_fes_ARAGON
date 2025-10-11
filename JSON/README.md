# 📚 Documentación de cursos.json

## Descripción General

El archivo `cursos.json` contiene la oferta académica del **Departamento de Planeación Académica** de la **FES Aragón UNAM**. Este archivo alimenta dinámicamente la página de cursos (`cursos.html`) y permite gestionar toda la información de los programas de capacitación docente.

## Estructura del Archivo

### Nivel raíz

```json
{
  "programa": "PASD 2025",
  "organiza": {
    "instituciones": [...]
  },
  "cursos": [...]
}
```

| Campo | Tipo | Descripción |
|-------|------|-------------|
| `programa` | `string` | Nombre del programa general (ej: "PASD 2025") |
| `organiza` | `object` | Información de las instituciones organizadoras |
| `cursos` | `array` | Lista de todos los cursos disponibles |

---

## 📋 Estructura de un Curso

Cada objeto dentro del array `cursos` representa un curso individual con la siguiente estructura:

### Campos Obligatorios

#### 1. **Identificación**

```json
{
  "id": "15164",
  "tipo": "Curso",
  "titulo": "Lenguaje incluyente para una docencia con perspectiva de género"
}
```

| Campo | Tipo | Descripción | Ejemplo |
|-------|------|-------------|---------|
| `id` | `string` | Identificador único del curso | `"15164"`, `"PASD-2001"` |
| `tipo` | `string` | Tipo de actividad | `"Curso"`, `"Taller"`, `"Diplomado"` |
| `titulo` | `string` | Nombre completo del curso | `"Herramientas Digitales para Docencia"` |

#### 2. **Estado del Curso** 🎯

```json
{
  "estado": "inscripciones"
}
```

| Campo | Tipo | Valores Permitidos | Color de Badge | Descripción |
|-------|------|--------------------|----------------|-------------|
| `estado` | `string` | `"inscripciones"` | 🟢 Verde (`#10b981`) | Curso con inscripciones abiertas |
| | | `"en-curso"` | 🔵 Azul (`#3b82f6`) | Curso actualmente en desarrollo |
| | | `"lleno"` | 🟠 Naranja (`#f59e0b`) | Curso con cupo completo |
| | | `"cancelado"` | 🔴 Rojo (`#ef4444`) | Curso cancelado o suspendido |

> **Nota:** Los cursos con estado `"cancelado"` se muestran con opacidad reducida (70%) en los cards.

#### 3. **Categoría**

```json
{
  "categoria": {
    "clave": "genero",
    "nombre": "Igualdad de Género"
  }
}
```

**Categorías Disponibles:**

| Clave | Nombre | Color (CSS) |
|-------|--------|-------------|
| `"disciplinar"` | Disciplinar | `#118ab2` |
| `"didactico"` | Apoyo didáctico-pedagógico | `#06d6a0` |
| `"investigacion"` | Apoyo a la investigación | `#3a0ca3` |
| `"docencia"` | Docencia inicial | `#38b000` |
| `"genero"` | Igualdad de Género | `#7b2cbf` |
| `"bienestar"` | Bienestar de la comunidad | `#ff5400` |
| `"tic"` | Conocimiento y Uso de TIC | `#ef476f` |
| `"desarrollo-sostenible"` | Desarrollo sostenible | `#cca43b` |
| `"neurodivergencia"` | Neurodivergencia e inclusión | `#820263` |

#### 4. **Modalidad**

```json
{
  "modalidad": {
    "clave": "en-linea",
    "nombre": "En línea",
    "duracion": "20 horas"
  }
}
```

**Modalidades Disponibles:**

| Clave | Nombre | Icono Bootstrap | Descripción |
|-------|--------|-----------------|-------------|
| `"en-linea"` | En línea | `bi-wifi` | Curso 100% virtual |
| `"presencial"` | Presencial | `bi-geo-alt` | Curso en instalaciones físicas |
| `"mixta"` | Mixta | `bi-arrows-angle-contract` | Combinación de sesiones presenciales y virtuales |

#### 5. **Nivel**

```json
{
  "nivel": {
    "clave": "intermedio",
    "nombre": "Intermedio"
  }
}
```

**Niveles Disponibles:**

| Clave | Nombre |
|-------|--------|
| `"basico"` | Básico |
| `"intermedio"` | Intermedio |
| `"avanzado"` | Avanzado |

#### 6. **Fechas**

```json
{
  "fechas": {
    "inicio": "2025-08-09",
    "fin": "2025-08-30",
    "dias": "Sabatino"
  }
}
```

| Campo | Tipo | Formato | Descripción |
|-------|------|---------|-------------|
| `inicio` | `string` | `YYYY-MM-DD` | Fecha de inicio del curso |
| `fin` | `string` | `YYYY-MM-DD` | Fecha de finalización |
| `dias` | `string` | Texto libre | Días de la semana (ej: "Sabatino", "Lunes y miércoles") |

#### 7. **Horario**

```json
{
  "horario": {
    "inicio": "09:00",
    "fin": "14:00",
    "zona": "Hrs"
  }
}
```

| Campo | Tipo | Formato | Descripción |
|-------|------|---------|-------------|
| `inicio` | `string` | `HH:MM` | Hora de inicio (formato 24h) |
| `fin` | `string` | `HH:MM` | Hora de finalización |
| `zona` | `string` | Texto | Zona horaria o unidad (ej: "Hrs", "CDT") |

#### 8. **Descripción**

```json
{
  "descripcion": "Reflexiona sobre el uso del lenguaje incluyente para transformar la práctica docente con perspectiva de género."
}
```

Texto descriptivo del curso (1-2 líneas recomendadas).

#### 9. **Ponentes**

```json
{
  "ponentes": [
    "Arq. Mónica García Juárez",
    "Mtra. Alejandra Villa Calderón"
  ]
}
```

Array de strings con los nombres completos de los instructores (incluir grado académico).

#### 10. **Enlaces**

```json
{
  "enlaces": {
    "detalles": "https://www.aragon.unam.mx/fes-aragon/#!/portal-docente",
    "registro": "http://zafiro.dgapa.unam.mx/registro/inicio",
    "textoDetalles": "Detalles",
    "textoRegistro": "Me interesa"
  }
}
```

| Campo | Tipo | Descripción | Valor por defecto |
|-------|------|-------------|-------------------|
| `detalles` | `string` (URL) | Enlace a información detallada | - |
| `registro` | `string` (URL) | Enlace al formulario de registro | - |
| `textoDetalles` | `string` (opcional) | Texto del botón de detalles | `"Detalles"` |
| `textoRegistro` | `string` (opcional) | Texto del botón de registro | `"Me interesa"` |

#### 11. **Contacto**

```json
{
  "contacto": {
    "emails": [
      "planeacionacademica@aragon.unam.mx",
      "cursosdgapa@aragon.unam.mx"
    ],
    "whatsapp": "5575169840"
  }
}
```

| Campo | Tipo | Descripción |
|-------|------|-------------|
| `emails` | `array` | Lista de correos electrónicos de contacto |
| `whatsapp` | `string` | Número de WhatsApp (sin espacios ni guiones) |

---

## 🎨 Representación Visual en el Sitio

### Card de Curso

Cada curso se muestra como una tarjeta con:

1. **Badge de categoría** (esquina superior izquierda)
   - Color según la categoría
   - Muestra el nombre de la categoría

2. **Badge de estado** (junto al título)
   - Verde: Inscripciones abiertas
   - Azul: En curso
   - Naranja: Cupo lleno
   - Rojo: Cancelado

3. **Metadatos**
   - Icono de modalidad + nivel
   - Ejemplo: "🌐 En línea · Intermedio"

4. **Fecha de inicio**
   - Formato: "09 ago 2025"

5. **Botones de acción**
   - "Detalles": Abre enlace externo
   - "Me interesa": Abre formulario de registro

---

## 📝 Ejemplo Completo

```json
{
  "id": "15164",
  "tipo": "Curso",
  "titulo": "Lenguaje incluyente para una docencia con perspectiva de género",
  "estado": "en-curso",
  "categoria": {
    "clave": "genero",
    "nombre": "Igualdad de Género"
  },
  "modalidad": {
    "clave": "en-linea",
    "nombre": "En línea",
    "duracion": "20 horas"
  },
  "nivel": {
    "clave": "intermedio",
    "nombre": "Intermedio"
  },
  "fechas": {
    "inicio": "2025-08-09",
    "fin": "2025-08-30",
    "dias": "Sabatino"
  },
  "horario": {
    "inicio": "09:00",
    "fin": "14:00",
    "zona": "Hrs"
  },
  "descripcion": "Reflexiona sobre el uso del lenguaje incluyente para transformar la práctica docente con perspectiva de género.",
  "ponentes": [
    "Arq. Mónica García Juárez",
    "Mtra. Alejandra Villa Calderón"
  ],
  "enlaces": {
    "detalles": "https://www.aragon.unam.mx/fes-aragon/#!/portal-docente",
    "registro": "http://zafiro.dgapa.unam.mx/registro/inicio"
  },
  "contacto": {
    "emails": [
      "planeacionacademica@aragon.unam.mx",
      "cursosdgapa@aragon.unam.mx"
    ],
    "whatsapp": "5575169840"
  }
}
```

---

## 🔧 Cómo Agregar un Nuevo Curso

1. **Abre** `JSON/cursos.json`

2. **Copia** la estructura de un curso existente

3. **Modifica** todos los campos según el nuevo curso:
   - Asigna un `id` único
   - Actualiza `titulo`, `descripcion` y `ponentes`
   - Define el `estado` actual
   - Selecciona `categoria`, `modalidad` y `nivel` de las tablas anteriores
   - Configura `fechas` y `horario`
   - Agrega `enlaces` y `contacto`

4. **Valida** la sintaxis JSON:
   - Verifica comas entre objetos
   - Cierra correctamente llaves y corchetes
   - Usa comillas dobles para strings

5. **Guarda** el archivo

6. **Recarga** la página `cursos.html` para ver el cambio

---

## ⚠️ Errores Comunes

### 1. Sintaxis JSON inválida
```json
// ❌ Incorrecto (coma extra)
{
  "id": "123",
  "titulo": "Mi curso",
}

// ✅ Correcto
{
  "id": "123",
  "titulo": "Mi curso"
}
```

### 2. Estado inválido
```json
// ❌ Incorrecto
"estado": "abierto"

// ✅ Correcto (usa solo valores permitidos)
"estado": "inscripciones"
```

### 3. Formato de fecha incorrecto
```json
// ❌ Incorrecto
"inicio": "09/08/2025"

// ✅ Correcto
"inicio": "2025-08-09"
```

### 4. Categoría no definida
```json
// ❌ Incorrecto (clave no existe)
"categoria": {
  "clave": "matematicas",
  "nombre": "Matemáticas"
}

// ✅ Correcto (usa una clave de la tabla)
"categoria": {
  "clave": "disciplinar",
  "nombre": "Disciplinar"
}
```

---

## 🎯 Filtrado en el Sitio Web

Los usuarios pueden filtrar cursos por:
- **Búsqueda de texto**: Busca en título y descripción
- **Categoría**: Filtra por área temática
- **Modalidad**: Presencial, en línea o mixta
- **Nivel**: Básico, intermedio o avanzado
- **Ordenamiento**: Alfabético (A-Z, Z-A) o por fecha

El estado del curso **NO** filtra automáticamente, pero se muestra visualmente para informar al usuario.

---

## 📊 Variables CSS Relacionadas

Las siguientes variables CSS en `style/main.css` controlan los colores:

```css
/* Categorías */
--disciplinar: #118ab2;
--didactico: #06d6a0;
--investigacion: #3a0ca3;
--docencia: #38b000;
--genero: #7b2cbf;
--bienestar: #ff5400;
--tic: #ef476f;
--desarrollo-sostenible: #cca43b;
--neurodivergencia: #820263;

/* Estados */
--estado-inscripciones: #10b981;
--estado-en-curso: #3b82f6;
--estado-lleno: #f59e0b;
--estado-cancelado: #ef4444;
```

---

## 📞 Soporte

Para dudas o problemas con el archivo JSON:
- **Email**: planeacionacademica@aragon.unam.mx
- **WhatsApp**: 5575169840

---

## 📅 Última Actualización

**Fecha**: Octubre 2025  
**Versión del esquema**: 1.1 (con campo `estado`)

---

## 🔐 Notas de Seguridad

- ⚠️ No incluir información sensible en el JSON
- ✅ Validar URLs antes de publicar
- ✅ Verificar que los enlaces funcionen correctamente
- ✅ Mantener backup del archivo antes de modificaciones grandes
