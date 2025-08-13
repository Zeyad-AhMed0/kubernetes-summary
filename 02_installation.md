# 02 - Installing Minikube and kubectl

## Installing kubectl
`kubectl` is the command-line tool to interact with Kubernetes clusters.  
It allows you to deploy applications, inspect resources, and manage the cluster.

### On Linux
1. Download the latest release:
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```
2. Make it executable:
```bash
chmod +x kubectl
```
3. Move it to a directory in your PATH:
```bash
sudo mv kubectl /usr/local/bin/
```
4. Verify installation:
```bash
kubectl version --client
```
لو ظهرت لك نسخة الـ client، يبقى `kubectl` جاهز للاستخدام على جهازك. على Linux ممكن تستخدمه مباشرة من الطرفية بدون أي واجهة رسومية.

### On Windows
1. Download the `kubectl.exe` from the official Kubernetes release page.
2. Add the folder containing `kubectl.exe` to your system PATH.
3. Open Command Prompt or PowerShell and run:
```powershell
kubectl version --client
```
لو ظهرت النسخة، يبقى كل حاجة تمام وجاهز للتعامل مع أي cluster.

## Installing Minikube
Minikube allows you to run a local Kubernetes cluster on your machine for testing and development.

### On Linux
1. Download the latest Minikube binary:
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
2. Make it executable:
```bash
chmod +x minikube-linux-amd64
```
3. Move it to a directory in your PATH and rename it:
```bash
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
```
4. Start a local cluster:
```bash
minikube start
```
لو ظهرت الرسائل اللي بتقول إن الكلاستر شغّال، يبقى كل حاجة تمام. Minikube بيعمل VM أو container بيحتوي على Master و Node واحدة عشان تجرب الـ Kubernetes بدون أي cloud.

### On Windows
1. Download the Minikube installer `.exe` from the official page.
2. Run the installer and follow the instructions.
3. Open Command Prompt or PowerShell and start the cluster:
```powershell
minikube start
```
لو ظهرت رسائل بدء الكلاستر، يبقى جاهز للتجارب المحلية.

## Checking the Cluster
بعد ما تبدأ Minikube، تقدر تتأكد إن كل حاجة شغالة بالأوامر دي:
```bash
kubectl get nodes
kubectl get pods -A
```
هيظهرلك الـ Node المحلي والـ Pods اللي شغالة، وده يثبت إن الكلاستر جاهز للاستخدام. أي أمر هتعمله بعد كده من `kubectl` هيتنفذ على هذا الكلاستر المحلي.

## Tips
- لو عايز توقف الكلاستر:
```bash
minikube stop
```
- لو عايز تحذفه نهائيًا:
```bash
minikube delete
```
- Minikube بيقدر يشتغل مع Docker Desktop على Windows لو حابب، وده بيوفر VM أقل تعقيدًا وسرعة أكبر.
