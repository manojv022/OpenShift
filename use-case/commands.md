Great! Let's go over the **OpenShift CLI (`oc`) commands** in a **structured, beginner-friendly way**, so you can understand not just what they do, but **when and why** you use them.

---

## 🔹 What is `oc`?

`oc` is the **OpenShift Command Line Interface**, similar to `kubectl` in Kubernetes, but with **OpenShift-specific capabilities** like managing Builds, Routes, ImageStreams, and Projects.

---

## 🔹 Getting Started

### ✅ Login to OpenShift

```bash
oc login https://<openshift-api-url> --token=<your-token>
```

* Logs you into the OpenShift cluster.
* You can also use `--username` and `--password`.

### ✅ View Cluster Info

```bash
oc whoami         # See current user
oc status         # Quick summary of your app/project status
oc version        # Shows client & server versions
```

---

## 🔹 Project and Namespace Management

### ✅ List All Projects

```bash
oc get projects
```

### ✅ Create a New Project

```bash
oc new-project myproject
```

### ✅ Switch Between Projects

```bash
oc project myproject
```

---

## 🔹 Working with Applications

### ✅ Create a New App from Git Repo or Image

```bash
oc new-app <git-repo-url>
# Example:
oc new-app nodejs~https://github.com/user/app.git
```

### ✅ List All Deployed Resources

```bash
oc get all
```

### ✅ View Application Logs

```bash
oc logs <pod-name>
```

### ✅ View Pod in Real-Time

```bash
oc logs -f <pod-name>
```

### ✅ SSH into Pod (like docker exec)

```bash
oc rsh <pod-name>
```

---

## 🔹 Managing Pods, Deployments, and Services

### ✅ List Pods

```bash
oc get pods
```

### ✅ Describe Pod

```bash
oc describe pod <pod-name>
```

### ✅ Delete Pod

```bash
oc delete pod <pod-name>
```

### ✅ View Services

```bash
oc get svc
```

### ✅ View Routes (for external access)

```bash
oc get routes
```

### ✅ Expose Service (create a route)

```bash
oc expose svc/<service-name>
```

---

## 🔹 Builds and Images

### ✅ View BuildConfigs

```bash
oc get bc
```

### ✅ Start a Build

```bash
oc start-build <buildconfig-name>
```

### ✅ View Build Logs

```bash
oc logs build/<build-name>
```

### ✅ View ImageStreams

```bash
oc get is
```

---

## 🔹 Deployment Management

### ✅ View Deployments

```bash
oc get deployment
```

### ✅ Rollout a New Deployment

```bash
oc rollout latest <deployment-config-name>
```

### ✅ Roll Back to Previous Version

```bash
oc rollout undo <deployment-config-name>
```

### ✅ Scale Application

```bash
oc scale deployment <name> --replicas=3
```

---

## 🔹 Configuration & Secrets

### ✅ Create a ConfigMap

```bash
oc create configmap myconfig --from-literal=key=value
```

### ✅ Create a Secret

```bash
oc create secret generic mysecret --from-literal=password=12345
```

### ✅ View ConfigMaps or Secrets

```bash
oc get configmaps
oc get secrets
```

---

## 🔹 Apply, Edit, Delete Resources

### ✅ Apply Configuration File (YAML)

```bash
oc apply -f myapp.yaml
```

### ✅ Create from YAML

```bash
oc create -f deployment.yaml
```

### ✅ Edit a Resource

```bash
oc edit deployment <name>
```

### ✅ Delete Any Resource

```bash
oc delete pod <name>
oc delete all -l app=myapp
oc delete -f app.yaml
```

---

## 🔹 Role-Based Access Control (RBAC)

### ✅ View Roles

```bash
oc get roles
```

### ✅ Add Role to User

```bash
oc adm policy add-role-to-user edit user1 -n myproject
```

---

## 🔹 Advanced and Admin Tasks

### ✅ View Events (Troubleshooting)

```bash
oc get events
```

### ✅ Get Cluster Nodes

```bash
oc get nodes
```

### ✅ Taint or Label Nodes (Admin)

```bash
oc label node <node-name> env=prod
oc taint node <node-name> key=value:NoSchedule
```

---

## 🔹 Help and Command Discovery

### ✅ Get Help on Any Command

```bash
oc --help
oc get --help
oc new-app --help
```

---

## 🧠 Tip: Resources in OpenShift

You can use `oc get <resource>` for all these types:

| Resource       | Description              |
| -------------- | ------------------------ |
| `pods` or `po` | Running containers       |
| `svc`          | Services                 |
| `rc`           | ReplicationControllers   |
| `deployment`   | Deployments              |
| `bc`           | BuildConfigs             |
| `is`           | ImageStreams             |
| `route`        | External access route    |
| `cm`           | ConfigMaps               |
| `secret`       | Secrets                  |
| `pvc`          | Persistent Volume Claims |

---

## ✅ Example: Full Workflow

```bash
oc login https://api.cluster.local --token=xxx
oc new-project demo
oc new-app nodejs~https://github.com/user/app.git
oc get pods
oc logs -f <pod-name>
oc expose svc/app
oc get route
```

You now have an app running and exposed to the internet!

---

## Want More?

Let me know if you’d like:

* A **visual CLI cheat sheet**
* A **hands-on YAML deployment example**
* An **interactive lab or mini project**
* Details about **scripting with `oc`**

Just say the word!
