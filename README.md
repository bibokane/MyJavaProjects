# My Java Projects

Dieses Repository enthält eine Sammlung von Java-Anwendungen, die verschiedene Geschäftsbereiche abdecken. Alle Projekte wurden mit Swing GUI entwickelt und nutzen MySQL als Datenbank.

## 📋 Übersicht der Projekte

Dieses Repository enthält die folgenden vier Java-Projekte:

### 1. 🏦 [Bank Management System](Bank-Management-System/)
Ein vollständiges ATM (Automated Teller Machine) System mit Swing GUI, das alle wichtigen Banking-Operationen unterstützt.

### 2. 🦠 [COVID-19 Tracker](covid-tracker/)
Eine moderne Spring Boot Web-Anwendung, die COVID-19 Fallzahlen weltweit in Echtzeit anzeigt.

### 3. 🏪 [Store Billing System](StoreBillingSystem/)
Ein umfassendes Laden-Kassensystem mit Produkt- und Lagerverwaltung, Verkaufsabwicklung und Abrechnung.

### 4. 🎓 [University Management System](University%20Management%20System/)
Ein vollständiges Universitätsverwaltungssystem für Studenten, Lehrer, Anwesenheit, Prüfungen und Gebühren.

---

## 🛠️ Technologie-Stack

### Gemeinsame Technologien
- **Java** - Hauptprogrammiersprache
- **MySQL** - Datenbank für Datenverwaltung
- **Swing GUI** - Für Desktop-Anwendungen (3 von 4 Projekten)
- **Maven** - Build-Management (COVID-Tracker)

### Projekt-spezifische Technologien
- **Bank Management System**: Java Swing, MySQL Connector, JCalendar
- **COVID-19 Tracker**: Spring Boot 3.5.0, Thymeleaf, Apache Commons CSV
- **Store Billing System**: Java Swing, MySQL Connector
- **University Management System**: Java Swing, MySQL Connector, RS2XML

---

## 📋 Voraussetzungen

Um diese Projekte auszuführen, benötigen Sie:

- **Java JDK** (Version 8 oder höher)
- **MySQL Server** (Version 5.7 oder höher)
- **Maven** (nur für COVID-Tracker erforderlich)
- **IDE** (NetBeans, Eclipse, IntelliJ IDEA oder andere)

### MySQL Setup
1. Installieren Sie MySQL Server
2. Starten Sie den MySQL Service
3. Erstellen Sie die erforderlichen Datenbanken für jedes Projekt

---

## 🚀 Schnellstart

### 1. Bank Management System
```bash
cd Bank-Management-System
# Kompilieren Sie die Java-Dateien
javac src/Bank/*.java
# Erstellen Sie die Datenbank 'bms'
# Führen Sie Login.java aus
java -cp ".:mysql-connector-j-9.3.0.jar" Bank.Login
```

### 2. COVID-19 Tracker
```bash
cd covid-tracker
./mvnw spring-boot:run
# Öffnen Sie http://localhost:8080
```

### 3. Store Billing System
```bash
cd StoreBillingSystem
# Kompilieren Sie die Java-Dateien
javac src/store/*.java
# Erstellen Sie die Datenbank 'sbs'
# Führen Sie Login.java aus
java -cp ".:mysql-connector-java-8.0.27.jar" store.Login
```

### 4. University Management System
```bash
cd "University Management System"
# Kompilieren Sie die Java-Dateien
javac src/university/*.java
# Erstellen Sie die Datenbank
# Führen Sie Login.java aus
java -cp ".:rs2xml.jar:mysql-connector-java-8.0.27.jar" university.Login
```

---

## 📁 Projektstruktur

```
MyJavaProjects-main/
├── Bank-Management-System/       # ATM Banking System
│   ├── src/Bank/                 # Java-Quellcode
│   ├── build/                    # Kompilierte Klassen
│   └── mysql-connector-j-9.3.0.jar
│
├── covid-tracker/                # COVID-19 Tracker Web-App
│   ├── src/main/java/            # Spring Boot Anwendung
│   ├── src/main/resources/       # Templates & Config
│   ├── pom.xml                   # Maven Konfiguration
│   └── mvnw                      # Maven Wrapper
│
├── StoreBillingSystem/           # Laden-Kassensystem
│   ├── src/store/                # Java-Quellcode
│   ├── build/                    # Kompilierte Klassen
│   └── mysql-connector-java-8.0.27.jar
│
├── University Management System/  # Universitätsverwaltung
│   ├── src/university/           # Java-Quellcode
│   ├── build/                    # Kompilierte Klassen
│   ├── rs2xml.jar               # Report-Utility
│   └── mysql-connector-java-8.0.27.jar
│
└── README.md                     # Hauptdokumentation
```

---

## 🔧 Konfiguration

### Datenbankverbindungen

Jedes Projekt erfordert eine MySQL-Datenbankkonfiguration. Die Verbindungsdetails sind in den jeweiligen Projekt-READMEs dokumentiert.

**Wichtiger Hinweis**: Die Projekte enthalten hardcodierte Datenbankzugangsdaten. Für Produktionszwecke sollten diese in Konfigurationsdateien verschoben werden.

---

## 📚 Projekt-Details

Für detaillierte Informationen zu jedem Projekt, siehe die individuellen README-Dateien:

- [Bank Management System README](Bank-Management-System/README.md)
- [COVID-19 Tracker README](covid-tracker/README.md)
- [Store Billing System README](StoreBillingSystem/README.md)
- [University Management System README](University%20Management%20System/README.md)

---

## 🤝 Beitragen

Dieses Repository enthält Beispielprojekte für Lernzwecke. Beiträge sind willkommen!

### Wie man beiträgt:
1. Forken Sie das Repository
2. Erstellen Sie einen Feature-Branch
3. Committen Sie Ihre Änderungen
4. Pushen Sie zum Branch
5. Erstellen Sie einen Pull Request

- Entwickelt für Lern- und Demonstrationszwecke
- Bank Management System - ATM Simulation
- COVID-19 Tracker - Web-basierte COVID-19 Datenvisualisierung
- Store Billing System - Ladenverwaltungssystem
- University Management System - Universitätsverwaltung
