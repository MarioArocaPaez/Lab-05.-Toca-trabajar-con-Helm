Este proyecto despliega una aplicación modular compuesta por un frontend, backend y base de datos utilizando **Helm** en Kubernetes. Está diseñado para seguir las mejores prácticas de Helm y Kubernetes, permitiendo una configuración flexible y reutilizable.

## 📦 Estructura del Proyecto

```plaintext
my-app/
│
├── Chart.yaml                # Metadatos del chart principal
├── values.yaml               # Valores por defecto
├── charts/                   # Subcharts para cada componente
│   ├── frontend/             # Configuración del frontend
│   ├── backend/              # Configuración del backend
│   └── database/             # Configuración de la base de datos
├── templates/                # Plantillas principales
│   ├── configmap.yaml
│   ├── deployment.yaml
│   └── service.yaml
├── values-dev.yaml           # Configuración para desarrollo
├── values-prod.yaml          # Configuración para producción
└── README.md                 # Documentación del proyecto
```

---

## 🚀 Despliegue de la Aplicación

### Instalación Básica
Para desplegar el chart en un clúster de Kubernetes:

```bash
helm install my-app .
```

### Configuración de Entorno

#### 🔧 Entorno de Desarrollo

```bash
helm install my-app . -f values-dev.yaml
```

#### 🔒 Entorno de Producción

```bash
helm install my-app . -f values-prod.yaml
```

---

## ✅ Validación del Chart

Antes de desplegar, asegúrate de que tu chart esté libre de errores ejecutando:

```bash
helm lint .
```

---

## 🔄 Actualización de la Aplicación

Si necesitas actualizar la aplicación, por ejemplo, para modificar el número de réplicas:

```bash
helm upgrade --set frontend.replicaCount=3 my-app .
```

---

## 📚 Subida del Proyecto a GitHub

```bash
# Inicializar repositorio
git init
echo "# Proyecto" >> README.md
git add .
git commit -m "Primer commit"
git branch -M main
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin main
```

---

## 💡 Notas

- Este proyecto sigue las mejores prácticas de Helm y Kubernetes.
- Se recomienda probar localmente con herramientas como Minikube antes de desplegar en producción.
