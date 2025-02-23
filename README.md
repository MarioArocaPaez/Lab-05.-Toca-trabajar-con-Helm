Este proyecto despliega una aplicación modular compuesta por un frontend, backend y base de datos utilizando **Helm** en Kubernetes. Está diseñado para seguir las mejores prácticas de Helm y Kubernetes, permitiendo una configuración flexible y reutilizable.

## 📦 Estructura del Proyecto

```plaintext
my-app/
│
├── Chart.yaml                # Metadatos del chart principal
├── values.yaml               # Valores por defecto
├── charts/                   # Subcharts para cada componente
│   ├── frontend/             # Subchart del frontend
│   ├── backend/              # Subchart del backend
│   └── database/             # Subchart de la base de datos
├── templates/                # ConfigMap global
│   ├── configmap.yaml
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

---

## 📊 Ejemplo de valores predeterminados (`values.yaml`)

```yaml
frontend:
  image: nginx:latest
  replicaCount: 2
  service:
    type: ClusterIP
    port: 80

backend:
  image: my-backend:latest
  replicaCount: 2
  service:
    type: ClusterIP
    port: 8080

database:
  image: mysql:5.7
  replicaCount: 1
  service:
    type: ClusterIP
    port: 3306
  persistence:
    enabled: true
    size: 1Gi
```

---

## ⚙️ ConfigMap Global

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
  labels:
    app: my-app
data:
  redis_host: redis
  app1_host: app1
  app2_host: app2
```

---

## 📝 Estructura de Subcharts

Cada componente tiene su propio subchart para mantener la modularidad:

### 📍 Frontend

- Configuración de imagen y réplicas.
- Definición de servicio y despliegue parametrizado.

### 📍 Backend

- Imagen y puerto configurados desde `values.yaml`.
- Despliegue y servicio independientes.

### 📍 Database

- Definición de almacenamiento persistente.
- Servicio tipo ClusterIP con puerto configurado.

---

Esta estructura garantiza flexibilidad, escalabilidad y adherencia a las mejores prácticas de Helm y Kubernetes.
