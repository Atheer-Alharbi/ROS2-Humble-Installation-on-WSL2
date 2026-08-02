# ROS 2 Humble Installation on WSL2

## 📌 Project Description

This project demonstrates the installation of Ubuntu 22.04 and ROS 2 Humble on Windows using Windows Subsystem for Linux (WSL2).

---

## 🛠 Installation Steps

### 1. Enable WSL

Enable the following Windows features:

- Windows Subsystem for Linux
- Virtual Machine Platform

Restart the computer.

---

### 2. Install Ubuntu 22.04

```bash
wsl --install -d Ubuntu-22.04
```

Create a Linux username and password.

---

### 3. Update Ubuntu

```bash
sudo apt update
sudo apt upgrade -y
```

---

### 4. Install Required Packages

```bash
sudo apt install software-properties-common curl
```

---

### 5. Add the ROS 2 Repository

```bash
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

```bash
sudo apt update
```

---

### 6. Install ROS 2 Humble

```bash
sudo apt install ros-humble-desktop
```

---

### 7. Configure the Environment

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

```bash
source ~/.bashrc
```

---

## ✅ Verify the Installation

```bash
echo $ROS_DISTRO
```

Output:

```text
humble
```

Run the demo node:

```bash
ros2 run demo_nodes_cpp talker
```

---

## ⚠️ Problems Encountered

During the installation, I encountered the following issues:

- WSL installation failed with **Catastrophic failure**.
- Windows Subsystem for Linux returned **Error 1603**.
- The C: drive did not have enough free storage.
- After freeing more than 15 GB on the C: drive, the WSL installation completed successfully.

---

## 📷 Output

### ROS Distribution

![ROS Distribution](images/ros_distro.png)

### Demo Node

![Talker Output](images/talker_output.png)

---

## ✅ Result

Ubuntu 22.04 and ROS 2 Humble were successfully installed on WSL2. The installation was verified by checking the ROS distribution and running the ROS 2 demo node successfully.
