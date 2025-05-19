# FacturaPy

FacturaPy es una aplicación web que permite calcular el monto a pagar por el consumo de electricidad en Paraguay, basado en la lectura del medidor en kWh. 
Ofrece dos implementaciones: una monolítica y otra nativa para la nube con contenedores.

---

## 📁 Estructura del Repositorio

```
FacturaPy/
├── monolitico/       # Implementación monolítica con Django + PostgreSQL
├── cloud/            # Implementación nativa para la nube (Docker + PostgreSQL + React)
└── README.md         # Documentación del proyecto
```

---

## 🔧 Requisitos

- Docker
- Docker Compose
- PostgreSQL (para monolítico)
- Python 3.11+
- Git

---

## 🚀 Cómo levantar cada versión

### 📦 Versión Monolítica

#### Pasos:
```bash
cd monolitico
python -m venv env
source env/bin/activate  # en Windows usar env\Scripts\activate
pip install -r requirements.txt
```

Configurar PostgreSQL localmente:
```sql
CREATE DATABASE facturapy;
CREATE USER admin WITH PASSWORD 'admin123';
GRANT ALL PRIVILEGES ON DATABASE facturapy TO admin;
```

Luego ejecutar:
```bash
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

#### Accesos:
- Admin Django: `http://localhost:8000/admin`
- API REST: `http://localhost:8000/api/`

---

### ☁️ Versión Nativa para la Nube

#### Pasos:
```bash
cd cloud
docker-compose up --build
```

Inicializar base de datos:
```bash
docker exec -it cloud-backend-1 bash
python manage.py migrate
python manage.py createsuperuser
```

#### Accesos:
- Frontend React: `http://localhost:3000`
- Backend API: `http://localhost:8000/api/`
- Admin Django: `http://localhost:8000/admin`

---

## 🧰 Tecnologías utilizadas

- **Django + DRF**: Backend RESTful
- **React**: Interfaz básica en la nube
- **PostgreSQL**: Base de datos para ambas versiones
- **Docker & Compose**: Contenedores y orquestación

---

## 📂 Archivos importantes

### .gitignore
Ignora:
- `.env`, `__pycache__`, `*.sqlite3`, `node_modules/`, `media/`, `.DS_Store`, `build/`

---

## 🧑‍💻 Autor
- GitHub: [simpozo](https://github.com/simpozo)

## 📄 Licencia
Este proyecto se publica bajo la licencia MIT.

---

¡Contribuciones son bienvenidas!
