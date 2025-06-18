
# 🌐 Introducción a Kubernetes

Este repositorio contiene una introducción práctica y teórica a **Kubernetes**, ideal para presentaciones, formaciones o autoaprendizaje.

---

## 📋 Tabla de contenidos

| Sección | Descripción |
|--------|-------------|
| [1. ¿Qué es Kubernetes?](#1-qué-es-kubernetes) | Definición general |
| [2. Componentes principales](#2-componentes-principales) | Estructura básica del clúster |
| [3. Arquitectura del clúster](#3-arquitectura-del-clúster) | Control Plane, nodos y pods |
| [4. ¿Qué es Minikube?](#4-qué-es-minikube) | Clúster local para pruebas |
| [5. Comunicación dentro del clúster](#5-comunicación-dentro-del-clúster) | kubelet, API Server y tráfico de red |
| [6. Cómo se distribuye el tráfico](#6-cómo-se-distribuye-el-tráfico) | Services, kube-proxy y balanceo |
| [7. ¿Dónde se ejecuta un clúster?](#7-dónde-se-ejecuta-un-clúster) | Local, nube o servidores físicos |
| [8. Recursos útiles](#8-recursos-útiles) | Enlaces y referencias |

---

## 1. ¿Qué es Kubernetes?

**Kubernetes** es un **orquestador de contenedores open source** desarrollado por Google.

> “Docker crea contenedores. Kubernetes los organiza y los mantiene funcionando correctamente.”

Kubernetes se encarga de:
- Desplegar aplicaciones en contenedores
- Escalar automáticamente
- Realizar actualizaciones sin interrupciones
- Gestionar la disponibilidad

---

## 2. Componentes principales

### 🔹 Pod
- Unidad más pequeña en Kubernetes.
- Contiene uno o varios contenedores.

### 🔹 Nodo
- Máquina (física o virtual) donde se ejecutan los pods.
- Contiene el agente `kubelet` y `kube-proxy`.

### 🔹 Control Plane
- Componente central que gestiona el clúster.
- Incluye:
  - API Server
  - Scheduler
  - Controller Manager
  - etcd (almacenamiento)

### 🔹 API Server
- Punto de entrada del clúster.
- Recibe las peticiones de usuarios y herramientas como `kubectl`.

---

## 3. Arquitectura del clúster

Un clúster de Kubernetes se compone de:

```
Cluster
├── Control Plane (API Server, Scheduler, etc)
└── Nodos Worker
    ├── kubelet
    ├── kube-proxy
    └── Pods (contenedores)
```

- El **Control Plane** da las órdenes.  
- Los **nodos** ejecutan los Pods (aplicaciones).  
- La **comunicación** se da a través del API Server.

---


## 4. ¿Qué es Minikube?

**Minikube** es una herramienta que permite crear un clúster Kubernetes local en tu PC para fines de desarrollo o formación.

- Crea un **clúster con un solo nodo** que funciona como Control Plane y Worker.
- Útil para aprender Kubernetes sin pagar servicios en la nube.

> ✅ Ideal para practicar con `kubectl` y aprender los conceptos básicos.

---

## 5. Comunicación dentro del clúster

- **`kubelet`**: Agente que corre en cada nodo y se comunica con el API Server.
- **`kube-proxy`**: Encargado del enrutamiento de red y el balanceo de tráfico hacia los pods.
- El **API Server** es el corazón de la comunicación. Todo pasa por él.

---

## 6. Cómo se distribuye el tráfico

Kubernetes usa diferentes componentes para enrutar el tráfico:

- **Services**: Definen una dirección estable para acceder a Pods.
- **kube-proxy**: Gestiona las reglas de red para distribuir tráfico entre Pods.
- **Ingress** (opcional): Gestiona accesos HTTP desde fuera del clúster.

> El tráfico entra por el Service o Ingress, pasa por el kube-proxy y llega al Pod correspondiente.

---

## 7. ¿Dónde se ejecuta un clúster?

Un clúster Kubernetes puede ejecutarse:

| Entorno       | Herramienta o proveedor |
|---------------|--------------------------|
| Local         | Minikube, Kind, k3s      |
| Cloud         | AWS EKS, GCP GKE, Azure AKS |
| On-premise    | Servidores propios        |

Puedes empezar sin contratar ningún servicio en la nube.

---

## 8. Recursos útiles

- [Documentación oficial de Kubernetes](https://kubernetes.io/es/docs/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Guía de kubectl](https://kubernetes.io/docs/reference/kubectl/)
- [Kubernetes en español - Comunidad CNCF](https://www.kubernetes.io/es/community/)

---

## 🧑‍💻 Collaborators
This project was developed by the following contributors:
- [Fernando García Catalán](https://github.com/fergarcat/)    
- [Nhoeli Salazar Romero](https://github.com/Nho89/)   
---
<p align="right">(<a href="#-index">⬆️ Back to top</a>)</p>

