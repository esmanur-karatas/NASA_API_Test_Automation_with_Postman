
<h1 align="center">
  🚀 NASA API Test Automation Project
</h1>


<p align="center">
  <img src="https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif" width="100" alt="rocket launch"/>
  <img src="https://img.shields.io/badge/Postman-F24E1E?style=for-the-badge&logo=postman&logoColor=white"/>
  <img src="https://img.shields.io/badge/Newman-000000?style=for-the-badge&logo=newman&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white"/>
  <img src="https://img.shields.io/badge/NASA-0B3D91?style=for-the-badge&logo=nasa&logoColor=white"/>
</p>

---

## 🌌 Overview

This project is designed to **automatically test NASA's public APIs** using **Postman**, **Newman**, **Jenkins**, and **GitHub Actions**. It includes **positive** and **negative** test cases for multiple API endpoints and generates detailed reports using continuous integration pipelines.

---

## 📡 Tested NASA APIs

This repository includes positive and negative test cases for the following NASA endpoints:

- NASA APOD GET  
- NASA NEO Feed GET  
- NASA NEO Detail GET  
- NASA NEO Browse GET  
- NASA OSDR File Access GET  
- NASA Mars Insight Weather GET  
- DONKI-CME-GET  
- DONKI-CMEanalysis-GET  
- DONKI-GST-GET  
- DONKI-IPS-GET  
- DONKI-FLR-GET  
- DONKI-SEP-GET  
- DONKI-MPC-GET  
- DONKI-RBE-GET  
- DONKI-HSS-GET  
- DONKI-WSA-GET  
- Earth-Assets-GET  

---

## 📁 Project Structure

```
├── .postman/collections/        # Postman collections (positive & negative)
├── Postman_Environments/        # Environment variables (NASA_ENV)
├── Jenkinsfile                  # Jenkins CI/CD pipeline configuration
├── .github/workflows/           # GitHub Actions workflows (optional)
└── README.md                    # You are here 🚀
```

---

## ⚙️ How to Setup Locally

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/NASA_API_Test_Automation.git
cd NASA_API_Test_Automation
```

### 2. Install Newman & Reporter Globally

```bash
npm install -g newman newman-reporter-junitfull
```

### 3. Set Environment Variables

Update your API keys and variables in:

```
Postman_Environments/NASA_ENV.postman_environment.json
```

---

## ⚒️ Jenkins Setup

1. Install **NodeJS Plugin**
2. Add a NodeJS installation called `NodeJS_24`
3. Create a **Pipeline job** pointing to this GitHub repository
4. Jenkinsfile will:
   - Checkout source code
   - Install Newman and reporter
   - Run positive & negative tests
   - Archive test reports
   - Continue running all tests even if some fail

---

## 📊 Reports

After test execution:

- ✔️ Passed tests
- ❌ Failed tests
- 📄 Detailed test logs
- 📁 HTML & JUnit reports archived via Jenkins

View reports directly in Jenkins or access the `reports/` directory.

---

## 🧪 Run Tests Manually (Optional)

```bash
newman run .postman/collections/NASA_Positive_Tests.json -e Postman_Environments/NASA_ENV.postman_environment.json -r cli,html,junit
```

```bash
newman run .postman/collections/NASA_Negative_Tests.json -e Postman_Environments/NASA_ENV.postman_environment.json -r cli,html,junit
```

---

## 💡 Sample Jenkins Pipeline Output

![jenkins-output](https://user-images.githubusercontent.com/12345678/jenkins-sample.gif)

---

## ✨ SVG Banner

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=24&duration=4000&pause=1000&color=F7F7F7&background=000000&center=true&vCenter=true&width=800&height=60&lines=Test+NASA+APIs+Like+a+Pro+🚀;CI%2FCD+Ready+with+Jenkins+and+Newman;Real+World+Automation+Project" alt="Typing SVG">
</p>

---

## 🛠 Tools & Technologies

| Tool      | Purpose                    |
|-----------|----------------------------|
| Postman   | API Testing GUI            |
| Newman    | CLI Test Runner            |
| Jenkins   | CI/CD Automation           |
| NodeJS    | Runtime for Newman         |
| GitHub    | Source Code Management     |

---

## 🌟 Contribute

Pull requests are welcome! If you like the project, don’t forget to give it a ⭐ and share.

---

![image](https://github.com/user-attachments/assets/fca4f95c-aad7-49a5-8d81-23b56ad2e458)

![image](https://github.com/user-attachments/assets/6f41789e-dcba-422d-9c76-7d68aa14e32f)



## 📬 Contact

📧 Email: esmanurkaratas0@outlook.com
🐙 Linkdln: https://www.linkedin.com/in/esmanur-karatas/

---

