# Mejoras Prácticas para Optimizar el Repositorio con Gemini

## El Problema Identificado
Gemini indicó que necesita acceso a los documentos específicos (PDFs/DOCs) del plan de estudios para generar planeaciones más funcionales y coherentes con el contexto curricular.

## Solución: Estrategia de 3 Capas

### Capa 1: Documentos en Formato Texto (CRÍTICA)

#### 1.1 Convertir PDFs a Markdown
Los documentos PDF del repositorio Google Drive deben convertirse a archivos `.md` (Markdown).

**Paso a paso:**
1. Descargar cada PDF de la carpeta "Para la planeación"
2. Usar herramientas gratuitas:
   - https://smallpdf.com/es/pdf-a-word (convertir PDF → DOCX)
   - Copiar texto del DOCX y adaptarlo a Markdown
   - O usar https://www.pdftotxt.com/ para extracción de texto
3. Guardar como `.md` en las carpetas correspondientes

**Ejemplo de estructura:**
```
documentos-referencias/
├── COMPETENCIAS-BASICAS.md
├── TAXONOMIA-BLOOM.md
├── ORIENTACIONES-PEDAGOGICAS.md
├── LINEAMIENTOS-TECNOLOGIA.md
└── DIMENSIONES-DESARROLLO.md
```

### Capa 2: Índice y Sumarios (IMPORTANTE)

#### 2.1 Crear un archivo INDEX.md

En la raíz del repositorio, crear un archivo que actúe como "mapa de contenidos":

```markdown
# ÍNDICE DE CONTENIDOS DEL REPOSITORIO

## 📚 Documentos de Referencia
- **COMPETENCIAS-BASICAS.md**: Define los 4 niveles de competencia (Bajo, Básico, Alto, Superior)
- **TAXONOMIA-BLOOM.md**: Clasificación de objetivos cognitivos
- **ORIENTACIONES-PEDAGOGICAS.md**: Estrategias didácticas recomendadas
- **COMPETENCIAS-TECNOLOGIA.md**: Competencias específicas para Tecnología e Informática

## 📋 Modelos de Planeación
- Ubicados en `planeaciones-clase/`
- Incluyen estructura estándar de 8 componentes

## 🎯 Competencias por Grado
- Grado 6 a 11: Ver `competencias/`

## 📖 Metodologías
- ABP (Aprendizaje Basado en Proyectos)
- APS (Aprendizaje y Servicio)
- Aprendizaje Colaborativo
```

#### 2.2 Crear RESUMEN-EJECUTIVO.md

Para que Gemini entienda rápidamente el contexto:

```markdown
# Resumen Ejecutivo del Currículo

## Institución
[Tu institución]

## Enfoque Curricular
[Describe el enfoque institucional]

## Competencias Clave
1. Competencia 1: [Descripción]
2. Competencia 2: [Descripción]
3. Competencia 3: [Descripción]

## Escala de Evaluación
- BAJO: 0-60%
- BÁSICO: 61-75%
- ALTO: 76-89%
- SUPERIOR: 90-100%

## Áreas de Énfasis
- Innovación y Ciudadanía Digital
- Pensamiento Crítico
- Resolución de Problemas
```

### Capa 3: Sistema de Prompt Optimizado (MUY IMPORTANTE)

#### 3.1 Prompt Maestro para Gemini

Usa este prompt mejorado en Gemini:

```
ACTÚA COMO ESPECIALISTA EN DISEÑO CURRICULAR

He compartido contigo los archivos en mi repositorio GitHub:
github.com/andrescave12/recursos-educativos-gemini

IMPORTANTE: Antes de generar cualquier planeación, PRIMERO:

1. REVISA estos archivos específicos:
   - INDEX.md (mapa del repositorio)
   - RESUMEN-EJECUTIVO.md (contexto institucional)
   - documentos-referencias/COMPETENCIAS-BASICAS.md
   - documentos-referencias/ORIENTACIONES-PEDAGOGICAS.md

2. EXTRAE de estos documentos:
   - Las 4 escalas de competencia (bajo, básico, alto, superior)
   - Las competencias específicas del área
   - Las metodologías institucionales recomendadas
   - El formato de planeación estándar

3. GENERA la planeación de clase ALINEADA CON:
   - Las competencias específicas extraídas
   - La escala de evaluación institucional
   - Las metodologías recomendadas
   - El formato estándar del repositorio

Mi solicitud específica:
[AQUÍ TU SOLICITUD DE PLANEACIÓN]
```

#### 3.2 Prompts Específicos por Tipo de Documento

**Para Planeaciones de Clase:**
```
Basado en los documentos del repositorio, especialmente:
- La escala de competencia en COMPETENCIAS-BASICAS.md
- Las orientaciones en documentos-referencias/

Genera una planeación de clase que incluya:
1. Objetivo alineado con competencias [ESPECIFICAR CUÁLES]
2. Actividades que desarrollen desde BAJO hasta SUPERIOR
3. Evaluación formativa en cada nivel
4. Recursos alineados con [TEMA]
```

**Para Rúbricas:**
```
Usando la estructura de 4 niveles (BAJO-BÁSICO-ALTO-SUPERIOR) 
definida en el repositorio, crea una rúbrica para evaluar:
- Criterio 1
- Criterio 2
- Criterio 3

Cada criterio debe tener descriptores específicos para los 4 niveles.
```

### Capa 4: Archivos de Configuración (OPCIONAL PERO RECOMENDADO)

#### 4.1 Crear config.json

```json
{
  "institucion": "Tu Institución",
  "pais": "Colombia",
  "grados": [6, 7, 8, 9, 10, 11],
  "areas": ["Tecnología", "Ciencias", "Lenguaje"],
  "escala_evaluacion": {
    "bajo": "0-60%",
    "basico": "61-75%",
    "alto": "76-89%",
    "superior": "90-100%"
  },
  "metodologias": ["ABP", "APS", "Aprendizaje Colaborativo"],
  "duracion_clase": "60 minutos",
  "semanas_por_periodo": 10
}
```

## Plan de Implementación Paso a Paso

### Semana 1: Preparación
- [ ] Descargar todos los PDFs de Google Drive
- [ ] Convertir PDFs a texto/markdown
- [ ] Crear INDEX.md
- [ ] Crear RESUMEN-EJECUTIVO.md
- [ ] Crear config.json

### Semana 2: Carga
- [ ] Subir archivos .md a `documentos-referencias/`
- [ ] Subir archivos de config
- [ ] Actualizar README.md con nuevas instrucciones

### Semana 3: Optimización
- [ ] Probar con Gemini usando el prompt maestro
- [ ] Ajustar archivos según resultados
- [ ] Documentar lecciones aprendidas

## Resultado Esperado

Una vez implementadas estas 3 capas, Gemini podrá:

✅ Acceder directamente a todos los documentos
✅ Entender el contexto curricular institucional
✅ Generar planeaciones completamente alineadas
✅ Crear rúbricas con niveles específicos
✅ Diseñar materiales contextualizados
✅ Proporcionar evaluaciones coherentes
✅ Sugerir adaptaciones pedagógicas

## Ejemplo de Flujo Mejorado

```
TÚ: "Crea una planeación para grado 10, Tecnología, tema Ciberseguridad"
    ↓
GEMINI: Lee INDEX.md → entiende estructura
    ↓
GEMINI: Lee RESUMEN-EJECUTIVO.md → entiende contexto
    ↓
GEMINI: Lee COMPETENCIAS-BASICAS.md → sabe cómo evaluar
    ↓
GEMINI: Lee ORIENTACIONES → sabe qué metodologías usar
    ↓
GEMINI: Genera planeación PERFECTAMENTE ALINEADA
```

## Herramientas Recomendadas

### Para Conversión de PDF a Markdown
- **CloudConvert**: https://cloudconvert.com/ (PDF a DOCX)
- **Pandoc**: https://pandoc.org/ (conversión entre formatos)
- **PDF.io**: https://pdf.io/es/pdf-to-word (en línea)

### Para Organización
- **Obsidian**: Visualizar y conectar los .md
- **GitHub Desktop**: Sincronizar cambios fácilmente

### Para Mejora Continua
- Usar GitHub Issues para documentar mejoras
- Usar GitHub Projects para seguimiento

---

**Versión**: 1.0
**Fecha**: Noviembre 2025
**Estado**: Recomendaciones de optimización
