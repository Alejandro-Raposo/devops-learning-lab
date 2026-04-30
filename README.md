# DevOps Learning Lab 🚀

Este repositorio es un laboratorio personal de aprendizaje de prácticas DevOps modernas, incluyendo CI/CD, análisis de calidad de código y gestión de artefactos.

---

# 🧠 Objetivo del proyecto

El objetivo es construir una arquitectura DevOps completa y reproducible que incluya:

- Integración continua (CI) con GitHub Actions
- Análisis de calidad de código con Sonar
- Construcción de paquetes Python
- Publicación de artefactos en Nexus
- Entorno reproducible en local con Docker

---

# 🏗️ Arquitectura del sistema

```text
GitHub (repo)
   ↓
GitHub Actions (CI/CD)
   ↓
Self-hosted Runner (local)
   ↓
Sonar (análisis de código)
   ↓
Build Python package
   ↓
Nexus Repository (artefactos)
```

---

# 🧩 Componentes

## 1. GitHub
Repositorio principal donde vive el código y los workflows.

## 2. GitHub Actions
Orquesta el pipeline CI/CD.

## 3. Self-hosted Runner
Máquina local que ejecuta los jobs del pipeline.

## 4. Sonar (SonarQube / SonarCloud)
Herramienta de análisis de calidad de código.

## 5. Nexus Repository
Repositorio local para almacenar artefactos generados (paquetes Python).

---

# 🐳 Infraestructura local (Docker)

Se utiliza Docker para levantar servicios locales:

```yaml
services:
  sonarqube:
    image: sonarqube:lts-community
    ports:
      - "9000:9000"

  nexus:
    image: sonatype/nexus3
    ports:
      - "8081:8081"
```

---

# ⚙️ Flujo CI/CD

## 1. Trigger
Un push a la rama principal activa el workflow.

## 2. Checkout
GitHub Actions descarga el código.

## 3. Runner
El job se ejecuta en el runner local.

## 4. Sonar Analysis
Se analiza la calidad del código.

## 5. Build
Se genera el paquete Python (dist/).

## 6. Publish
El artefacto se sube a Nexus.

---

# 🧪 Estructura del proyecto

```text
devops-learning-lab/
│
├── src/
│   └── app/
│
├── tests/
│
├── .github/workflows/
│
├── pyproject.toml
├── docker-compose.yml
├── README.md
```

---

# 🚨 Entornos

## 🏢 Entorno corporativo

- Proxy restrictivo
- SSL inspeccionado
- No permite descargas externas
- No apto para instalación de herramientas DevOps

## 🏠 Entorno local (recomendado)

- Sin restricciones
- Docker habilitado
- Control total de herramientas
- Ideal para aprendizaje

---

# 🛠️ Instalación local

## 1. Clonar repositorio

```bash
git clone https://github.com/TU_USUARIO/devops-learning-lab.git
```

## 2. Crear entorno Python

```bash
python -m venv .venv
.venv\Scripts\activate  # Windows
```

## 3. Instalar dependencias

```bash
pip install build twine setuptools wheel
```

## 4. Levantar infraestructura

```bash
docker compose up -d
```

---

# 🔍 Accesos locales

| Servicio | URL |
|----------|-----|
| Sonar | http://localhost:9000 |
| Nexus | http://localhost:8081 |

---

# 🧠 Conceptos aprendidos

- CI/CD con GitHub Actions
- Self-hosted runners
- Quality gates con Sonar
- Gestión de artefactos con Nexus
- Packaging Python
- Arquitecturas DevOps locales

---

# 🚀 Evolución del proyecto

Futuras mejoras:

- Automatización completa de versionado
- Deploy a entornos cloud
- Integración con Kubernetes
- Pipeline multi-stage avanzado

---

# 📌 Notas importantes

Este proyecto está diseñado como laboratorio de aprendizaje DevOps.
No debe usarse en producción sin ajustes de seguridad adicionales.

