# MLOPS-Data-Versioning-DVC
This repo implements the idea of data versioning using DVC tool
# 🚀 Data Versioning with DVC and Git

## 📌 Overview
This project demonstrates how to efficiently manage and version data using **DVC (Data Version Control)** and **Git**. It showcases a workflow for tracking dataset changes while leveraging cloud storage for remote backups. By following these steps, you will ensure reproducibility, collaboration, and better data management in machine learning and data science projects.

---

## 📂 Project Structure
```
📁 my_project
│── 📁 data          # Directory for dataset storage (tracked by DVC)
│── 📁 S3            # Remote storage directory (for demonstration purposes)
│── 📄 mycode.py     # Python script that generates and updates the dataset
│── 📄 data.dvc      # DVC tracking file for data
│── 📄 .gitignore    # Ignores data folder (tracked by DVC instead)
│── 📄 .dvcignore    # Ignore files not to be tracked by DVC
│── 📄 README.md     # Project documentation
```

---

## 🛠️ Tech Stack
- **Git & GitHub** - Version control system
- **DVC (Data Version Control)** - Data versioning
- **AWS S3** - Remote storage
- **Python** - Data processing
- **Docker & CI/CD (GitHub Actions)** - Deployment & automation

---

## 🚀 Setup Guide

### 1️⃣ Clone Repository
```bash
git clone <repo-url>
cd my_project
```

### 2️⃣ Create and Run Python Script
```bash
touch mycode.py
```
Add code inside `mycode.py` to generate a CSV file in a new `data/` folder.

Run the script:
```bash
python mycode.py
```

### 3️⃣ Initialize Git & Commit
```bash
git add .
git commit -m "Initial commit"
git push origin main
```

### 4️⃣ Install and Initialize DVC
```bash
pip install dvc
dvc init
```

### 5️⃣ Configure Remote Storage (AWS S3)
```bash
mkdir S3
dvc remote add -d myremote S3
```

### 6️⃣ Track Data with DVC
```bash
dvc add data/
git rm -r --cached data/
git commit -m "Stop tracking data with Git"
dvc add data/
git add .gitignore data.dvc
dvc commit
dvc push
git add .
git commit -m "Version 1 of data"
git push
```

### 7️⃣ Updating Data (Version 2 & Beyond)
Modify `mycode.py` to append a new row to the dataset, then:
```bash
python mycode.py
dvc status
dvc commit
dvc push
git add .
git commit -m "Version 2 of data"
git push
```

Repeat the above steps for **Version 3** and beyond.

---

## ✅ Verifying Status
Check if everything is up to date:
```bash
dvc status
git status
```

---

## 🎯 Key Features
✅ **Versioned Datasets** - Track dataset changes efficiently  
✅ **Cloud Storage Integration** - Backup and share datasets  
✅ **Reproducible Pipelines** - Ensure consistency across experiments  
✅ **CI/CD Ready** - Automate workflows with GitHub Actions & Docker  

🚀 **Take your data science workflow to the next level with Git & DVC!**


