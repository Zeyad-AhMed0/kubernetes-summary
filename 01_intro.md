# 01 - Introduction to Kubernetes

## What is Kubernetes?
Kubernetes (K8s) is an **open-source container orchestration platform** that automates deployment, scaling, and management of containerized applications.

**In simple terms:**  
It decides **where and how containers run**, keeps them running if something fails, and helps scale up/down easily.  

💡 بالعربي:  
الـ Kubernetes مش بديل للدوكر، هو بيشتغل **فوق أي Container Runtime** زي Docker أو containerd، وهدفه ينظم ويشغل الحاويات بشكل ذكي.

---

## Why Kubernetes?
- **Automation:** No need to manually start/stop containers.  
  💡 يعني مش محتاج تفتح كل Container يدوي وتشغله.
- **Scalability:** Handle traffic spikes smoothly.  
  💡  تقدر تزود أو تقلل عدد النسخ اللي شغالة حسب الضغط على التطبيق.
- **Self-healing:** Restarts failed containers automatically.  
  💡 لو أي Pod وقع أو حصل له مشكلة، Kubernetes بيعيد تشغيله تلقائي.
- **Portability:** Works on cloud, on-premises, or hybrid.
- **Service Discovery & Load Balancing:** Automatically exposes apps.  
  💡  الخدمة أو التطبيق متعرف على كل الشبكة وبيتم توجيه الطلبات تلقائي.

---

## Core Concepts

### 1. Cluster
- **Definition:** A set of machines (nodes) running Kubernetes workloads.
- **Parts:**
  - **Master Node(s):** Controls the cluster (API server, scheduler, etc.).  
    💡  الـ Master Node دا بيكون مسؤول عن التحكم في كل حاجة جوه الكلاستر.
  - **Worker Nodes:** Run the actual applications.  
    💡  الـ Worker Nodes هي اللي بتشغل الـ Pods والحاويات نفسها.

### 2. Node
- A physical or virtual machine inside the cluster.
- Components:
  - **Kubelet:** Talks to the master.  
    💡  الـ Kubelet دا زي وسيط بيتواصل مع الـ Master Node عشان ينفذ الأوامر.
  - **Container runtime:** Docker, containerd, etc.
  - **Kube-proxy:** Handles networking.  
    💡  مسؤول عن الشبكات والاتصالات بين الـ Pods والـ Services.

### 3. Pod
- Smallest deployable unit in Kubernetes.
- Can have one or more containers sharing:
  - Network (IP)
  - Storage volumes  
  💡  كل Pod جوه Node، والـ Containers جوه الـ Pod بيشاركوا نفس الشبكة ومساحات التخزين.

### 4. Service
- Stable network endpoint for Pods.
- Types:
  - **ClusterIP:** Internal only.  
    💡  بس جوه الكلاستر، مش ظاهر بره.
  - **NodePort:** External via node IP/port.  
    💡  تقدر توصل له من بره باستخدام IP وPort.
  - **LoadBalancer:** External with load balancing.  
    💡  لو انت على Cloud، بيجيب لك IP خارجي ويعمل توزيع Load تلقائي.

### 5. Deployment
- Manages Pods at scale.
- Supports:
  - Rolling updates (no downtime)
  - Rollbacks (restore old version)  
  💡  الـ Deployment بيسهل التحديثات بدون ما يوقع التطبيق، وكمان يقدر يرجع النسخة القديمة بسهولة.

---

## Kubernetes Architecture

**Master Node:**
- **API Server:** Entry point for commands (`kubectl`).  
  💡  أي أمر هتعمله من `kubectl` بيعدي على الـ API Server.
- **Scheduler:** Decides where to run Pods.  
  💡  المسؤول عن اختيار Node مناسب لتشغيل الـ Pods.
- **Controller Manager:** Watches cluster state.
- **etcd:** Key-value store for cluster data.

**Worker Node:**
- **Kubelet:** Manages containers.
- **Kube-proxy:** Networking rules.
- **Container Runtime:** Runs containers.

💡  الفكرة إن كل Pod دايمًا جوه Node، والـ Node جوه Cluster، والـ Master Node دا المسؤول عن إدارة كل حاجة.

---

## Analogy
Think of Kubernetes as a **smart delivery system**:
- **Master Node:** Dispatcher.
- **Worker Nodes:** Delivery vehicles.
- **Pods:** Packages.
- **Service:** Address everyone uses
