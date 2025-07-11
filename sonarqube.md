# 🛠️ SonarQube 9.9.3 Setup with PostgreSQL 16 and OpenJDK 17 on Ubuntu (EC2 Compatible)

> This guide walks you through installing SonarQube 9.9.3 LTS on an Ubuntu-based EC2 instance using PostgreSQL 16 and OpenJDK 17.

---

## 🧩 Prerequisites

- Ubuntu 20.04/22.04 EC2 Instance
- `sudo` user access
- Port 9000 open in security group (SonarQube default port)

---

## ✅ Step 1: Install OpenJDK 17

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y

✅ Step 2: Install and Configure PostgreSQL 16
sudo apt install curl ca-certificates
sudo install -d /usr/share/postgresql-common/pgdg
sudo curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc
. /etc/os-release
sudo sh -c "echo 'deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $VERSION_CODENAME-pgdg main' > /etc/apt/sources.list.d/pgdg.list"
sudo apt update
sudo apt -y install postgresql

Enable and start PostgreSQL:
sudo systemctl enable postgresql
sudo systemctl start postgresql

Set password for postgres user:
sudo passwd postgres

✅ Step 3: Setup PostgreSQL for SonarQube
su - postgres
createuser sonar
psql

