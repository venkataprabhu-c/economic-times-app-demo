Prerequisites : 

#!/bin/bash
set -e

echo "==============================================="
echo "   Checking & Installing Java 17 + Maven"
echo "==============================================="

# -----------------------------
# Function to check if a command exists
# -----------------------------
command_exists() {
    command -v "$1" >/dev/null 2>&1
}

# -----------------------------
# JAVA CHECK
# -----------------------------
echo "[1] Checking Java..."

if command_exists java; then
    echo "✔ Java is already installed:"
    java -version
else
    echo "✖ Java not found. Installing OpenJDK 17..."
    sudo apt update -y
    sudo apt install -y openjdk-17-jdk
    echo "✔ Java Installed Successfully!"
    java -version
fi

# -----------------------------
# MAVEN CHECK
# -----------------------------
echo ""
echo "[2] Checking Maven..."

if command_exists mvn; then
    echo "✔ Maven is already installed:"
    mvn -version
else
    echo "✖ Maven not found. Installing Maven..."
    sudo apt update -y
    sudo apt install -y maven
    echo "✔ Maven Installed Successfully!"
    mvn -version
fi

echo ""
echo "==============================================="
echo " Java & Maven check completed successfully!"
echo "==============================================="

==============================================================================================================================================================================

cd /opt
sudo wget <TOMCAT>
sudo tar -xzf <TOMCAT>
sudo mv <folder> tomcat10
sudo chmod +x /opt/tomcat10/bin/*.sh
sudo /opt/tomcat10/bin/startup.sh

#!/bin/bash
set -e
echo "====================================="
echo " Installing Apache Tomcat 10.1.50"
echo "====================================="

cd /opt

# Clean previous installations
sudo rm -rf /opt/tomcat10
sudo rm -rf /opt/apache-tomcat-10.1.50
sudo rm -f  /opt/apache-tomcat-10.1.50.tar.gz

echo "[1] Downloading Tomcat 10.1.50..."
sudo wget https://archive.apache.org/dist/tomcat/tomcat-10/v10.1.50/bin/apache-tomcat-10.1.50.tar.gz

echo "[2] Extracting..."
sudo tar -xzf apache-tomcat-10.1.50.tar.gz

echo "[3] Renaming folder..."
sudo mv apache-tomcat-10.1.50 tomcat10

echo "[4] Setting execute permissions..."
sudo chmod +x /opt/tomcat10/bin/*.sh

echo "[5] Starting Tomcat..."
sudo /opt/tomcat10/bin/startup.sh

echo "====================================="
echo " Tomcat 10.1.50 Installed Successfully!"
echo " Access: http://<server-ip>:8080"
echo " Folder: /opt/tomcat10"
echo "====================================="
==============================================================================================================================================================================

sudo rm -rf /opt/tomcat10/webapps/economic-times-app*
sudo cp target/economic-times-app.war /opt/tomcat10/webapps/
sudo /opt/tomcat10/bin/shutdown.sh
sudo /opt/tomcat10/bin/startup.sh

