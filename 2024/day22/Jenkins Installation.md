# Jenkins Installation Guide

Welcome to the Jenkins Installation Guide! This repository provides a detailed, step-by-step guide on how to install Jenkins on various operating systems, including **Ubuntu**, **Red Hat**, **Windows**, and **macOS**.

Jenkins is an open-source automation server that helps developers automate repetitive tasks like building, testing, and deploying software. Think of it as your personal assistant to streamline your DevOps process!

---

## Table of Contents
1. [What is Jenkins?](#what-is-jenkins)
2. [Prerequisites for Installation](#prerequisites-for-installation)
3. [Installing Jenkins on Different OS](#installing-jenkins-on-different-os)
   - [Ubuntu](#ubuntu)
   - [Red Hat](#red-hat)
   - [Windows](#windows)
   - [macOS](#macos)
4. [Checking Jenkins Version](#checking-jenkins-version)

---

## Prerequisites for Installation 🔧

Before you begin the installation process, make sure you have the following prerequisites:

1. **Java**: Jenkins requires Java to run. Install **Java 11** or higher.
2. **System Requirements**: At least **2 GB RAM** and an active internet connection.
3. **Permissions**: Ensure you have **administrator/root access** for installation on some systems.

---

## Installing Jenkins on Different OS 🖥️

### Ubuntu (Linux) 🍃

1. **Install Java**:
   ```bash
   sudo apt update
   sudo apt install openjdk-11-jdk
   ```

2. **Add Jenkins Repository**:
   ```bash
   wget -q -O - https://pkg.jenkins.io/jenkins.io.key | sudo apt-key add -
   sudo sh -c 'echo deb http://pkg.jenkins.io/debian/ stable main > /etc/apt/sources.list.d/jenkins.list'
   sudo apt update
   ```

3. **Install Jenkins**:
   ```bash
   sudo apt install jenkins
   ```

4. **Start Jenkins**:
   ```bash
   sudo systemctl start jenkins
   ```

5. **Check Jenkins Status**:
   ```bash
   sudo systemctl status jenkins
   ```

6. **Access Jenkins**: Open your browser and visit `http://localhost:8080`. Retrieve the unlock password:
   ```bash
   cat /var/lib/jenkins/secrets/initialAdminPassword
   ```

---

### Red Hat (Linux) 🐱

1. **Install Java**:
   ```bash
   sudo yum install java-11-openjdk
   ```

2. **Add Jenkins Repository**:
   ```bash
   wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
   sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
   ```

3. **Install Jenkins**:
   ```bash
   sudo yum install jenkins
   ```

4. **Start Jenkins**:
   ```bash
   sudo systemctl start jenkins
   sudo systemctl enable jenkins
   ```

5. **Access Jenkins**: Visit `http://localhost:8080` to complete the setup.

---

### Windows 💻

1. **Download Jenkins**: Go to the [Jenkins download page](https://www.jenkins.io/download/) and download the Windows installer.

2. **Run Installer**: Double-click to run the installer and follow the on-screen instructions.

3. **Start Jenkins**: Jenkins starts automatically after installation. Visit `http://localhost:8080` to unlock Jenkins.

4. **Unlock Jenkins**: Find the password in the `C:\Program Files (x86)\Jenkins\secrets\initialAdminPassword` file.

---

### macOS 🍏

1. **Install Homebrew** (if not already installed):
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Java**:
   ```bash
   brew install openjdk@11
   ```

3. **Install Jenkins**:
   ```bash
   brew install jenkins-lts
   ```

4. **Start Jenkins**:
   ```bash
   brew services start jenkins-lts
   ```

5. **Access Jenkins**: Visit `http://localhost:8080` to finish the setup.

---

## Checking Jenkins Version 🔍

Once Jenkins is installed, you can verify the version by running the following command in your terminal or command prompt:

```bash
jenkins --version
```

This will show you the Jenkins version that is currently installed.

---

## Conclusion 🎉

Congratulations! You've successfully installed Jenkins on your system. You're now ready to start automating your software builds, tests, and deployments. Jenkins is a vital tool for developers and DevOps engineers who want to improve efficiency and speed up their CI/CD pipeline. 🚀

Happy coding! ✨
