 🛒 UltimatePOS - JavaFX Point of Sale System

[![Java Version](https://img.shields.io/badge/Java-17%2B-blue.svg)](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
[![JavaFX](https://img.shields.io/badge/JavaFX-21-red.svg)](https://openjfx.io/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Maven](https://img.shields.io/badge/Maven-3.9.9-blue.svg)](https://maven.apache.org/)
[![Database](https://img.shields.io/badge/Database-H2-4479A1.svg)](https://www.h2database.com/)
[![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen.svg)]()

> **A production-ready, feature-rich Point of Sale system built for modern retail. Designed with resellers in mind, it allows effortless rebranding for multiple clients.**

---

## ✨ Features That Make a Difference

### Core Business Logic
*   **📦 Product Management:** Add, edit, delete, and search products with barcode support. Includes a comprehensive demo dataset for quick testing.
*   **🧑‍🤝‍🧑 Customer Management:** Track customer information and purchase history to build loyalty.
*   **📊 Sales & Reporting:** Process new sales, generate printable PDF receipts, and view detailed sales history with powerful date filtering.
*   **🔔 Stock Alerts:** Get automatic low-stock warnings on the dashboard to ensure you never run out of key items.

### Designed for Resellers (Your Superpower)
*   **🏷️ One-Click Rebranding:** The hidden `Ctrl + Shift + B` Branding Wizard allows you to instantly update the company name, logo, address, tax rate, and receipt footer without touching a single line of code.
*   **⚙️ Config-Driven:** All branding and business settings are managed externally via `config.properties`, making client onboarding incredibly fast.

### Technical Excellence
*   **🔒 Role-Based Access:** Secure login system with `Admin` and `Cashier` roles, each with tailored permissions.
*   **💾 Zero-Config Database:** Uses an embedded H2 database that requires no separate installation. The schema is auto-created on first run.
*   **📄 Professional PDF Receipts:** Generates clean, professional receipts automatically after every transaction.

---

## 🛠️ Tech Stack

| Category | Technology |
| :--- | :--- |
| **Language** | [Java 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) |
| **Frontend** | [JavaFX 21](https://openjfx.io/) (FXML + CSS) |
| **Build Tool** | [Apache Maven](https://maven.apache.org/) |
| **Database** | [H2 Database Engine](https://www.h2database.com/) (Embedded Mode) |
| **PDF Generation** | [OpenPDF](https://github.com/LibrePDF/OpenPDF) |

---

## 🗂️ Project Structure

A clean, organized structure following the MVC (Model-View-Controller) pattern.
UltimatePOS/
├── pom.xml # Maven build configuration
├── README.md # This file
├── LICENSE # MIT License
├── .gitignore # Git ignore rules
│
├── src/
│ ├── main/
│ │ ├── java/com/pos/ # All Java source code
│ │ │ ├── MainApp.java # Application entry point
│ │ │ ├── controllers/ # Handles user input & UI logic
│ │ │ ├── models/ # Data models (User, Product, Sale, etc.)
│ │ │ ├── dao/ # Data Access Objects for DB operations
│ │ │ └── utils/ # Helper classes (DB init, config, PDF gen)
│ │ └── resources/ # Static resources
│ │ ├── fxml/ # JavaFX layout files
│ │ ├── css/ # Application styling (styles.css)
│ │ ├── images/ # Logos and UI icons
│ │ └── config.properties # External configuration file
│
├── database/ # H2 database files (auto-created)
└── receipts/ # Generated PDF receipts

text

---

## 🚀 Getting Started

Follow these simple steps to get the system up and running.

### Prerequisites
*   **Java 17** or higher (JDK). You can download it [here](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html).
*   **Maven** (optional, but recommended). The IDE can also manage dependencies.

### Quick Start Guide

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/GitwithHaseeb/POS-System-JAVA-.git
    cd POS-System-JAVA-
Build and Run (with Maven)

bash
mvn clean javafx:run
Default Login Credentials

Role	Username	Password
Administrator	admin	admin
Cashier	cashier	cashier
⚠️ Important: Change the default admin password immediately after your first login for security.

🔧 Customization & Packaging
Rebranding for a Client
Run the application.

From the Dashboard, press Ctrl + Shift + B to open the Branding Wizard.

Update the company name, address, logo, tax rate, and receipt footer.

Click Save. All changes are applied instantly.

Building a Distributable JAR
Create a single, executable JAR file containing your application and all its dependencies.

bash
mvn clean package
The output POS-System-1.0.0-jar-with-dependencies.jar will be in the target/ directory.

Creating a Native Windows Installer
For a professional, one-click installation experience, use the jpackage tool bundled with the JDK.

Install WiX Toolset: Download and install WiX Toolset. Add its bin folder to your system's PATH.

Run the jpackage command: Navigate to the target/ directory and execute:

bash
jpackage --type msi --input . --main-jar POS-System-1.0.0-jar-with-dependencies.jar --main-class com.pos.MainApp --name UltimatePOS --dest installer-output
This command will create an MSI installer in the installer-output folder.

🤝 Contributing
Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

Fork the Project

Create your Feature Branch (git checkout -b feature/AmazingFeature)

Commit your Changes (git commit -m 'Add some AmazingFeature')

Push to the Branch (git push origin feature/AmazingFeature)

Open a Pull Request

📞 Contact & Support
Your Name - @GitwithHaseeb - haseebch8130@gmail.com

Project Link: https://github.com/GitwithHaseeb/POS-System-JAVA-

📜 License
This project is licensed under the MIT License - see the LICENSE file for details.

🙏 Acknowledgements
JavaFX for the rich UI framework.

H2 Database for the lightweight, embedded database engine.

OpenPDF for the PDF generation library.

Icons8 for the beautiful UI icons.

🔧 How to Use This Template
Copy the entire template.

Replace the placeholder <YOUR_NAME_HERE> with your details.

Update the Your GitHub URL and Your LinkedIn URL links.

Create an LICENSE file (MIT recommended) in your repository root.

Commit the new README.md and LICENSE to your repository.

text

### 📦 Phase 2: A Step-by-Step Guide to Generate a Distributable JAR

Once your `README.md` is polished, the next step is to create a distributable file for your clients.

#### Step 1: Prepare the `pom.xml` for Packaging
Your `pom.xml` needs a plugin to create a "fat JAR" (a JAR file that includes your code and all its dependencies). Add the following `maven-assembly-plugin` configuration inside the `<plugins>` section.

```xml
<plugin>
    <artifactId>maven-assembly-plugin</artifactId>
    <version>3.7.1</version>
    <configuration>
        <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
        </descriptorRefs>
        <archive>
            <manifest>
                <mainClass>com.pos.MainApp</mainClass>
            </manifest>
        </archive>
    </configuration>
    <executions>
        <execution>
            <id>make-assembly</id>
            <phase>package</phase>
            <goals>
                <goal>single</goal>
            </goals>
        </execution>
    </executions>
</plugin>
Step 2: Build the JAR
Run the Maven package command:

bash
mvn clean package
After a successful build, you'll find your executable JAR here:
target/POS-System-1.0.0-jar-with-dependencies.jar

Step 3: Test Your JAR
Open a terminal in the target/ directory and run:

bash
java -jar POS-System-1.0.0-jar-with-dependencies.jar
If the application launches successfully, your JAR is ready for distribution.

