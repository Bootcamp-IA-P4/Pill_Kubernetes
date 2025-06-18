
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
| [7. Demostración Práctica con Minikube y Dashboard](#7-demostración-práctica-con-minikube-y-dashboard) | Ejemplo de despliegue y acceso |
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
- Unidad más pequeña que Kubernetes puede desplegar. 
- Contiene uno o varios contenedores que comparten: 
    - Red 
    - Sistema de archivos (volúmenes) 
    - Ciclo de vida 
- Los Pods no son permanentes. 
- Si un Pod falla, Kubernetes crea uno nuevo con otro nombre.
  
### 🔹 Nodo
- Una máquina (puede ser una instancia en la nube o un servidor físico) donde Kubernetes ejecuta las cargas de trabajo (los pods). 
- Contiene el agente `kubelet` y `kube-proxy`.

### 🔹 Control Plane
- Es el encargado de mantener el estado deseado del clúster y de controlar, por ejemplo, las aplicaciones que se ejecutan y las imágenes de contenedores que se utilizan. 
- Incluye:
    - API Server
    - Scheduler
    - Controller Manager
    - etcd (almacenamiento)

### 🔹 API Server
- Es un componente fundamental de Kubernetes que actúa como el servidor de la API de Kubernetes y es el frontend del plano de control del sistema. 
- Recibe y procesa las peticiones del sistema, validando y configurando los datos para los objetos de la API, como pods, servicios y controladores de replicación. 

### 🔹 Controller Manager (`kube-controller-manager`)
- Es un componente del nodo master de Kubernetes que se encarga de ejecutar los controladores (controllers) del clúster. 
- Ejemplos de controladores:
    - `ReplicationController`: asegura que el número deseado de réplicas de un pod esté corriendo. 
    - `NodeController`: detecta si un nodo se cae y reacciona en consecuencia. 
    - `JobController`: gestiona la ejecución de Jobs hasta su finalización. 

### 🔹 Scheduler (`kube-scheduler`)
- Su función principal es asignar (schedule) los pods pendientes (aquellos que aún no están asignados a ningún nodo) a un nodo adecuado, según las necesidades del pod y las condiciones del clúster. 
- Registra la decisión para que el kubelet del nodo correspondiente cree el pod. 

### 🔹 etcd
- Es el almacén de datos clave-valor distribuido que usa Kubernetes como base de datos central. 
- Guarda el estado del sistema. Sin etcd, Kubernetes no puede operar ni recordar su estado. 

---

## 3. Arquitectura del clúster

Un clúster de Kubernetes es un grupo de nodos (máquinas que ejecutan aplicaciones) que trabajan juntos para gestionar y ejecutar contenedores de manera automatizada y escalable. 

- Un clúster de Kubernetes contiene, como mínimo: 
- Un plano de control (Control Plane o Master). 
- Una o varias nodos trabajadores (workers). 

```
Cluster
├── Control Plane (API Server, Scheduler, etc)
└── Nodos Worker
    ├── kubelet
    ├── Container Runtime (containerd, CRI-O)
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

## 8. Demostración Práctica con Minikube y Dashboard

Para esta demostración, utilizaremos los archivos .txt que contiene el repositorio, según el sistema operativo que tengamos.


## 9. Recursos útiles

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

