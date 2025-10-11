# 📚 Documentación de cursos.json

## Descripción General

El archivo `cursos.json` contiene la oferta académica del **Departamento de Planeación Académica** de la **FES Aragón UNAM**. Este archivo alimenta dinámicamente la página de cursos (`cursos.html`) y permite gestionar toda la información de los programas de capacitación docente.

## Estructura del Archivo

### Nivel raíz

```json
{
  "metadata": {
    "total_cursos": 95,
    "fecha_generacion": "2025-10-11 17:21:19",
    "fuente": "Panel de Monitoreo Depto. Planeación Académica"
  },
  "cursos": [...]
}
```

| Campo | Tipo | Descripción |
|-------|------|-------------|
| `metadata` | `object` | Metadatos del archivo (total de cursos, fecha de generación, fuente) |
| `cursos` | `array` | Lista de todos los cursos disponibles |

---

## 📋 Estructura de un Curso

Cada objeto dentro del array `cursos` representa un curso individual con la siguiente estructura:

### Campos Obligatorios

#### 1. **Identificación**

```json
{
  "id": "14321",
  "programa": "DGAPA",
  "nombre": "Fundamentos de Automatización de Procesos",
  "tipo": "CURSO",
  "año": 2025
}
```

| Campo | Tipo | Descripción | Ejemplo |
|-------|------|-------------|---------|
| `id` | `string` | Identificador único del curso | `"14321"`, `"14325"` |
| `programa` | `string` | Programa al que pertenece | `"DGAPA"`, `"FES ARAGÓN"` |
| `nombre` | `string` | Nombre completo del curso | `"Fundamentos de Automatización de Procesos"` |
| `tipo` | `string` | Tipo de actividad | `"CURSO"`, `"TALLER"`, `"DIPLOMADO"` |
| `año` | `number` | Año de impartición | `2025` |

#### 2. **Programa** 🎯

```json
{
  "programa": "DGAPA"
}
```

| Valor | Badge Color | Descripción |
|-------|-------------|-------------|
| `"DGAPA"` | 🔵 Azul | Dirección General de Asuntos del Personal Académico |
| `"FES ARAGÓN"` | 🟢 Verde | Facultad de Estudios Superiores Aragón |

#### 3. **Estado del Curso** 🎯

```json
{
  "estado": "FINALIZADO"
}
```

| Campo | Tipo | Valores Permitidos | Color de Badge | Descripción |
|-------|------|--------------------|----------------|-------------|
| `estado` | `string` | `"INSCRIPCIONES"` | 🟢 Verde | Curso con inscripciones abiertas |
| | | `"EN CURSO"` | 🔵 Azul | Curso actualmente en desarrollo |
| | | `"FINALIZADO"` | ⚫ Gris | Curso ya finalizado |
| | | `"CANCELADO"` | 🔴 Rojo | Curso cancelado o suspendido |

> **Nota:** Los cursos con estado `"CANCELADO"` se muestran con opacidad reducida (75%) en los cards.

#### 4. **Categoría**

```json
{
  "categoria": "DISCIPLINAR"
}
```

**Categorías Disponibles:**

| Valor | Nombre Completo | Color (CSS) |
|-------|-----------------|-------------|
| `"DISCIPLINAR"` | Disciplinar | `#118ab2` |
| `"APOYO DIDÁCTICO-PEDAGÓGICO"` | Apoyo didáctico-pedagógico | `#06d6a0` |
| `"APOYO A LA INVESTIGACIÓN"` | Apoyo a la investigación | `#3a0ca3` |
| `"DOCENCIA INICIAL"` | Docencia inicial | `#38b000` |
| `"IGUALDAD DE GÉNERO"` | Igualdad de Género | `#7b2cbf` |
| `"BIENESTAR DE LA COMUNIDAD DESDE LA PRÁCTICA DOCENTE"` | Bienestar de la comunidad | `#ff5400` |
| `"CONOCIMIENTO Y USO DE TIC"` | Conocimiento y Uso de TIC | `#ef476f` |
| `"DESARROLLO SOSTENIBLE"` | Desarrollo sostenible | `#cca43b` |
| `"NEURODIVERGENCIA E INCLUSIÓN"` | Neurodivergencia e inclusión | `#820263` |

#### 5. **Nivel**

```json
{
  "nivel": "LICENCIATURA"
}
```

**Niveles Disponibles:**

| Valor | Descripción |
|-------|-------------|
| `"LICENCIATURA"` | Dirigido a profesores de licenciatura |
| `"POSGRADO"` | Dirigido a profesores de posgrado |

#### 6. **Fechas**

```json
{
  "fechas": {
    "inicio": "2025-01-20",
    "termino": "2025-01-24"
  }
}
```

| Campo | Tipo | Formato | Descripción |
|-------|------|---------|-------------|
| `inicio` | `string` | `YYYY-MM-DD` | Fecha de inicio del curso |
| `termino` | `string` | `YYYY-MM-DD` | Fecha de finalización |

#### 7. **Horario**

```json
{
  "horario": {
    "dias": "Lunes a viernes",
    "horario": "11:00 a 15:00"
  }
}
```

| Campo | Tipo | Descripción |
|-------|------|-------------|
| `dias` | `string` | Días de la semana en que se imparte |
| `horario` | `string` | Horario de impartición |

#### 8. **Ponentes**

```json
{
  "ponentes": [
    "JOSE DANIEL CASTRO DIAZ",
    "HUMBERTO MANCILLA ALONSO",
    "-",
    "-",
    "-",
    "-"
  ]
}
```

Array de strings con los nombres completos de los instructores. Los valores `"-"` se filtran automáticamente en el frontend.

---

## 🎨 Representación Visual en el Sitio

### Card de Curso

Cada curso se muestra como una tarjeta con:

1. **Badge de programa** (esquina superior izquierda)
   - Azul: DGAPA
   - Verde: FES ARAGÓN

2. **Badge de categoría** (esquina superior derecha)
   - Color según la categoría
   - Muestra el nombre de la categoría

3. **Título del curso**
   - En color primario
   - Hover effect

4. **Badge de estado** (junto al título)
   - Verde: Inscripciones abiertas
   - Azul: En curso
   - Gris: Finalizado
   - Rojo: Cancelado

5. **Metadatos**
   - Nivel (Licenciatura/Posgrado)
   - Tipo (Curso/Taller/Diplomado)
   - Horario (días y horas)

6. **Ponentes**
   - Muestra hasta 2 ponentes
   - Si hay más, muestra "+N más"

7. **Fechas**
   - Formato: "20 ene 2025 - 24 ene 2025"

---

## 📝 Ejemplo Completo

```json
{
  "id": "14321",
  "programa": "DGAPA",
  "nombre": "Fundamentos de Automatización de Procesos",
  "fechas": {
    "inicio": "2025-01-20",
    "termino": "2025-01-24"
  },
  "año": 2025,
  "estado": "FINALIZADO",
  "tipo": "CURSO",
  "nivel": "LICENCIATURA",
  "categoria": "DISCIPLINAR",
  "ponentes": [
    "JOSE DANIEL CASTRO DIAZ",
    "HUMBERTO MANCILLA ALONSO"
  ],
  "horario": {
    "dias": "Lunes a viernes",
    "horario": "11:00 a 15:00"
  }
}
```

---

## 🔧 Cómo Agregar un Nuevo Curso

1. **Abre** `JSON/cursos.json`

2. **Copia** la estructura de un curso existente

3. **Modifica** todos los campos según el nuevo curso:
   - Asigna un `id` único
   - Define el `programa` (DGAPA o FES ARAGÓN)
   - Actualiza `nombre`, `tipo` y `año`
   - Define el `estado` actual
   - Selecciona `categoria` y `nivel` de las tablas anteriores
   - Configura `fechas` y `horario`
   - Agrega `ponentes` (elimina los guiones "-" si no hay suficientes ponentes)

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
  "nombre": "Mi curso",
}

// ✅ Correcto
{
  "id": "123",
  "nombre": "Mi curso"
}
```

### 2. Estado inválido
```json
// ❌ Incorrecto
"estado": "abierto"

// ✅ Correcto (usa solo valores permitidos)
"estado": "INSCRIPCIONES"
```

### 3. Formato de fecha incorrecto
```json
// ❌ Incorrecto
"inicio": "20/01/2025"

// ✅ Correcto
"inicio": "2025-01-20"
```

### 4. Categoría no válida
```json
// ❌ Incorrecto (valor no existe)
"categoria": "MATEMATICAS"

// ✅ Correcto (usa una categoría de la tabla)
"categoria": "DISCIPLINAR"
```

### 5. Programa no válido
```json
// ❌ Incorrecto
"programa": "UNAM"

// ✅ Correcto (solo DGAPA o FES ARAGÓN)
"programa": "DGAPA"
```

---

## 🎯 Filtrado en el Sitio Web

Los usuarios pueden filtrar cursos por:
- **Búsqueda de texto**: Busca en el nombre del curso
- **Categoría**: Filtra por área temática
- **Programa**: DGAPA o FES ARAGÓN
- **Estado**: Inscripciones, En curso, Finalizado, Cancelado
- **Nivel**: Licenciatura o Posgrado
- **Ordenamiento**: Alfabético (A-Z, Z-A) o por fecha (más recientes)

Todos los filtros son acumulativos y funcionan en tiempo real.

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
```

**Badges de Programa:**
- DGAPA: `bg-primary` (azul Bootstrap)
- FES ARAGÓN: `bg-success` (verde Bootstrap)

**Badges de Estado:**
- INSCRIPCIONES: `bg-success` (verde)
- EN CURSO: `bg-primary` (azul)
- FINALIZADO: `bg-secondary` (gris)
- CANCELADO: `bg-danger` (rojo)

---

## 📞 Soporte

Para dudas o problemas con el archivo JSON:
- **Email**: planeacionacademica@aragon.unam.mx
- **WhatsApp**: 5575169840

---

## 📅 Última Actualización

**Fecha**: Octubre 2025  
**Versión del esquema**: 2.0 (estructura actualizada con datos reales del Panel de Monitoreo)

---

## 🔐 Notas de Seguridad

- ⚠️ No incluir información sensible en el JSON
- ✅ Verificar que los datos provengan del Panel de Monitoreo oficial
- ✅ Mantener backup del archivo antes de modificaciones grandes
- ✅ Validar la estructura JSON antes de publicar cambios
