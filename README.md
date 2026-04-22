# 🎓 Gestión Escolar – Módulo Odoo

Módulo desarrollado en Odoo para la gestión de clases, alumnos y eventos dentro de un entorno escolar.

---

## 📌 Descripción

Este módulo permite:

- Gestionar clases con tutor asignado
- Registrar alumnos y asignarlos a clases
- Crear eventos asociados a alumnos (ausencias, retrasos, etc.)
- Controlar accesos mediante roles (Docente / Director)
- Soporte multiidioma (español y catalán)

---

## 🧱 Modelos

### 📚 Clase (`gestion_escolar.class`)
- Nombre
- Curso
- Tutor (empleado)
- Fechas (inicio/fin)
- Número de alumnos (calculado)
- Descripción
- Relación con alumnos (One2many)

---

### 👨‍🎓 Alumno (`gestion_escolar.student`)
- Nombre
- Apellidos
- DNI/NIE (único)
- Fecha de nacimiento
- Edad (calculada)
- Activo
- Clase (Many2one)
- Eventos (Many2many)

---

### 📅 Evento (`gestion_escolar.event`)
- Fecha
- Tipo:
  - Absence
  - Delay
  - Congratulations
  - Behavior
- Descripción
- Alumnos asociados

---

## 🔗 Relaciones

- Clase → Alumnos (One2many)
- Alumno → Clase (Many2one)
- Alumno ↔ Evento (Many2many)

---

## 🔐 Seguridad

Se han definido dos grupos:

- 👨‍🏫 **Docente**
  - Lectura de clases y alumnos
  - Gestión de eventos

- 🧑‍💼 **Director**
  - Acceso completo al sistema

---

## 🌍 Traducciones

El módulo incluye soporte para:

- 🇪🇸 Español (`es.po`)
- 🏴 Catalán (`ca.po`)

Ubicación:
i18n/
---

## 🧪 Datos de demostración

Se incluyen datos demo:

- 1 clase (DAM 2A)
- 2 alumnos
- 2 eventos
- usuarios docente y director

Archivo:

demo/demo.xml


---

## 🛠️ Tecnologías

- Odoo 18
- Python (ORM)
- XML (vistas y datos)
- PostgreSQL (Docker)

---

## 📂 Estructura del módulo


gestion_escolar/
├── models/
├── views/
├── security/
├── demo/
├── i18n/
├── manifest.py


---

## 🚀 Instalación

```bash
docker exec -it odoo_backup odoo \
--db_host odoo_db_backup \
--db_port 5432 \
--db_user odoo \
--db_password odoo \
-d odoo18_rescue_restaurada \
-i gestion_escolar \
--stop-after-init
