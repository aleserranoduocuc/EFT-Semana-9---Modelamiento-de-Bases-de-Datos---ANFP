# EFT Semana 9 - Modelamiento de Bases de Datos

**Evaluación Final Transversal (EFT)**  
**Asignatura:** Modelamiento de Bases de Datos  
**Carrera:** Desarrollo de Aplicaciones  
**Estudiante:** Alejandro Serrano  
**Profesor:** Juan Carlos Navarrete Ibacache  
**Fecha:** 11-10-2026

---

## 📋 Descripción del Proyecto

Diseño e implementación de una base de datos relacional normalizada para la **Asociación Nacional de Fútbol Profesional (ANFP)**, que permita gestionar la información de jugadores, clubes, entrenadores, contratos y demás actores vinculados al fútbol profesional y amateur en Chile.

El proyecto abarca las 4 fases del modelamiento:

1. **Fase 1:** Diseño del Modelo Entidad-Relación Extendido (MER-E).
2. **Fase 2:** Transformación del MER-E a Modelo Relacional Normalizado (MR).
3. **Fase 3:** Implementación del modelo mediante script DDL + poblamiento.
4. **Fase 4:** Recuperación de información mediante consultas SQL (SELECT).

---

## 🗂️ Estructura del Repositorio
📁 Modelamiento_Base_Datos/
├── 📄 Encargo_Semanal.docx → Documento Word con las capturas del MER-E y MR
├── 📄 Encargo_Semanal.sql → Script SQL de creación, poblamiento y consultas
├── 📄 Modelo_Base.zip → Archivo .dmd + carpeta de recursos del modelo
└── 📄 README.md → Este archivo

text

---

## 🎯 Entidades del Modelo (12)

| # | Entidad | Descripción |
|---|---|---|
| 1 | **REGION** | Regiones de Chile. |
| 2 | **COMUNA** | Comunas de cada región. |
| 3 | **NACIONALIDAD** | Nacionalidades de los trabajadores. |
| 4 | **ASOCIACION** | Asociaciones de fútbol (profesional o amateur). |
| 5 | **CLUB_FUTBOL** | Clubes de fútbol con su patrimonio. |
| 6 | **ESCUELA_FUTBOL** | Escuelas donde se formaron los jugadores. |
| 7 | **IDIOMA** | Idiomas que pueden dominar los jugadores. |
| 8 | **TRABAJADOR** | Entidad principal (supertipo) con datos comunes. |
| 9 | **JUGADOR** | Subtipo de TRABAJADOR. |
| 10 | **PERSONAL_PLANTA** | Subtipo de TRABAJADOR. |
| 11 | **CONTRATO** | Contratos entre trabajadores y clubes. |
| 12 | **JUGADOR_IDIOMA** | Tabla intermedia N:M entre jugador e idioma. |

---

## 🔑 Restricciones Implementadas

- **PK** (Primary Key): Claves primarias en todas las tablas.
- **FK** (Foreign Key): Claves foráneas que garantizan la integridad referencial.
- **UN** (Unique): `nombre_club` en CLUB_FUTBOL y `(rut, dv)` en TRABAJADOR.
- **CK** (Check): Validaciones en `fecha_creacion` (≥ 31-12-1980), `tipo` (P/A), `genero` (M/F/O), `tipo_trabajador` (JUGADOR/PERSONAL_PLANTA).
- **IDENTITY**: `id_nacionalidad` comienza en 210 e incrementa de 2 en 2.
- **SEQUENCE**: `seq_club` comienza en 703 e incrementa de 4 en 4.

---

## 🧬 Herencia Implementada

La entidad **TRABAJADOR** es el supertipo, con dos subtipos:

- **JUGADOR** (con atributos específicos: puesto, monto_premios, id_asociacion, id_escuela, anio_fin_amateur).
- **PERSONAL_PLANTA** (con atributos específicos: horas_trabajadas, valor_horas_extras).

Se utiliza un **discriminador** llamado `tipo_trabajador` para distinguir el tipo.

---

## 📊 Informes Generados

### Informe 1: Asociaciones de fútbol profesional
Lista las asociaciones profesionales creadas después del año 2000, ordenadas por fecha descendente.

### Informe 2: Patrimonio de clubes de fútbol
Muestra el patrimonio en pesos chilenos y su conversión a dólares (tipo de cambio $955), filtrando por clubes cuyo nombre contenga la letra "a", patrimonio > $200.000.000 y tipo profesional.

---

## 🛠️ Tecnologías Utilizadas

- **Oracle SQL Developer Data Modeler** → Diseño de MER-E y MR.
- **Oracle Database Actions (Oracle Cloud)** → Ejecución del script SQL.
- **Oracle SQL** → Implementación de tablas, restricciones y consultas.
- **GitHub** → Repositorio del proyecto.

---

## 📁 Archivos del Proyecto

| Archivo | Descripción |
|---|---|
| `Encargo_Semanal.docx` | Documento Word con las capturas del MER-E (notación Barker) y el MR normalizado. |
| `Encargo_Semanal.sql` | Script SQL completo: creación de tablas, poblamiento e informes. |
| `Modelo_Base.zip` | Archivo `.dmd` con su carpeta de recursos para abrir en Data Modeler. |

---

## 📹 Video de Presentación

El video de presentación del proyecto se encuentra en:

🔗 **[https://duoc-blackboardultrapilot1.kaf.kaltura.com/media/t/1_arp52laf/413754232]**

---

## 📌 Observaciones

- El proyecto cumple con las 4 fases del modelamiento.
- El modelo está normalizado hasta 3FN.
- Se implementó la herencia mediante discriminador.
- Se respetaron todas las restricciones solicitadas (PK, FK, UN, CK, IDENTITY, SEQUENCE).

---

**Duoc UC - Online | Semana 9 | 2026**
