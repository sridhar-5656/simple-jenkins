# 🚀 Jenkins CI/CD Pipeline Project

## 📌 Objective
Set up a **basic Jenkins pipeline** to automate the **build, test, Dockerize, and deploy** process for a sample Node.js application.

---

## 📂 Project Structure
```
jenkins-ci-cd-pipeline/
│── app/
│   ├── server.js
│   ├── package.json
│── Dockerfile
│── Jenkinsfile
│── README.md
```

---

## 🛠 Tools Used
- **Jenkins** (Pipeline automation)
- **Docker** (Containerization)
- **Node.js + Express** (Sample application)
- **GitHub** (Source code repository)

---

## ⚙️ Steps to Execute

### 1️⃣ Install Jenkins
- Install Jenkins locally or use a cloud VM.  
- Install plugins:  
  - **Pipeline**  
  - **Docker Pipeline**  
  - **NodeJS**  

### 2️⃣ Configure Jenkins
- Add **NodeJS tool** (Manage Jenkins → Global Tool Configuration).  
- Add **DockerHub credentials** (Manage Jenkins → Credentials).  

### 3️⃣ Create a New Pipeline Job
- Go to Jenkins Dashboard → New Item → *Pipeline*.  
- Set pipeline script from SCM → Connect GitHub repo.  

### 4️⃣ Run Pipeline
- Stages:
  1. **Checkout** – Pulls code from GitHub  
  2. **Build** – Installs dependencies  
  3. **Test** – Runs tests  
  4. **Docker Build** – Builds image  
  5. **Docker Push** – Pushes image to DockerHub  
  6. **Deploy** – Runs container  

### 5️⃣ Verify Deployment
- Open browser → `http://localhost:3000`  
- Output:  
  ```
  🚀 Hello from Jenkins CI/CD Pipeline!
  ```

---

## ❓ Interview Questions

1. **What is Jenkins, and how is it used in CI/CD?**  
   Jenkins is an open-source automation server used to automate building, testing, and deploying applications.  

2. **What is a Jenkinsfile?**  
   A Jenkinsfile defines the pipeline as code. It contains stages like build, test, and deploy.  

3. **How do you create and configure Jenkins pipelines?**  
   By creating a pipeline job in Jenkins and linking it to a Jenkinsfile in your repo.  

4. **What are some common stages in a Jenkins pipeline?**  
   - Checkout  
   - Build  
   - Test  
   - Deploy  

5. **Difference between declarative and scripted pipeline?**  
   - **Declarative**: Simple, structured syntax, recommended for most use cases.  
   - **Scripted**: More flexible, written in Groovy, used for complex pipelines.  

---

✅ **Outcome**: You’ve automated the process of building, testing, containerizing, and deploying an app using Jenkins Pipeline.
