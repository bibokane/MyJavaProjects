# 🎓 University Management System

Ein umfassendes Universitätsverwaltungssystem für die Verwaltung von Studenten, Lehrern, Anwesenheit, Prüfungen und Gebühren. Entwickelt mit Java Swing für eine vollständige Desktop-Lösung.

## 📋 Übersicht

Das University Management System ist eine vollständige Verwaltungssoftware für Universitäten, Colleges und Bildungseinrichtungen. Es deckt alle wichtigen Aspekte der Universitätsverwaltung ab: Studentenverwaltung, Lehrer-Management, Anwesenheitsverfolgung, Prüfungsmanagement und Gebührenverwaltung.

## ✨ Features

### 👨‍🎓 Studentenverwaltung
- ➕ **Neue Studenten aufnehmen**: Student-Anmeldung mit vollständigen Details
- 📝 **Studentendetails**: Vollständige Profilansicht
- ✏️ **Studenten aktualisieren**: Informationen bearbeiten
- 📊 **Studentenliste**: Alle eingeschriebenen Studenten anzeigen

### 👨‍🏫 Lehrerverwaltung
- ➕ **Neue Lehrer aufnehmen**: Lehrerregistrierung
- 📝 **Lehrerdetails**: Vollständiges Lehrerprofil
- ✏️ **Lehrer aktualisieren**: Informationen bearbeiten
- 👥 **Lehrerliste**: Alle Fakultätsmitglieder anzeigen

### 📅 Anwesenheit
- 📋 **Studenten-Anwesenheit**: Anwesenheitserfassung für Studenten
- 📋 **Lehrer-Anwesenheit**: Anwesenheitserfassung für Lehrer
- 📊 **Anwesenheitsdetails**: Detaillierte Anwesenheitsberichte
  - Nach Student filtern
  - Nach Datum filtern
  - Statistiken und Trends

### 📝 Prüfungen & Noten
- 🎯 **Prüfungsdetails**: Prüfungserstellung und -verwaltung
- 📊 **Noten eingeben**: Notenerfassung für Studenten
- 📈 **Leistungsüberwachung**: Fortschrittsverfolgung
- 🎓 **Notenspiegel**: Berichtserstellung

### 💰 Gebührenverwaltung
- 📋 **Gebührenstruktur**: Flexibel konfigurierbare Gebühren
- 💳 **Gebührenverwaltung**: Zahlungsverfolgung
- 📄 **Gebührenformular**: Studenten-Gebührenformular
- 📊 **Zahlungsstatus**: Übersicht der Zahlungen

### 🛠️ Utility-Funktionen
- 📝 **Notizblock**: Eingebauter Notizblock
- 🧮 **Taschenrechner**: Desktop-Rechner
- 🌐 **Web-Browser**: Browser-Integration (Windows)

## 🛠️ Technologie-Stack

- **Java**: Programmiersprache
- **Java Swing**: GUI-Framework
- **MySQL**: Relationale Datenbank
- **JDBC**: Datenbankverbindung
- **RS2XML**: Report-Generierung für Tabellen
- **mysql-connector-java-8.0.27**: MySQL-Treiber

## 📦 Installation

### Voraussetzungen

- Java JDK 8 oder höher
- MySQL Server (Version 5.7 oder höher)
- IDE (NetBeans, Eclipse, IntelliJ IDEA)

### Setup-Schritte

#### 1. Datenbank erstellen

```sql
CREATE DATABASE university;
USE university;

-- Login-Tabelle
CREATE TABLE login (
    username VARCHAR(50),
    password VARCHAR(50)
);

-- Studenten-Tabellen (vereinfacht)
CREATE TABLE student (
    rollno VARCHAR(10) PRIMARY KEY,
    name VARCHAR(50),
    father VARCHAR(50),
    gender VARCHAR(10),
    dob VARCHAR(20),
    address VARCHAR(100),
    phone VARCHAR(20),
    email VARCHAR(50),
    x_percent VARCHAR(10),
    xii_percent VARCHAR(10),
    aadhar VARCHAR(20),
    course VARCHAR(20),
    branch VARCHAR(20)
);

-- Lehrer-Tabelle (vereinfacht)
CREATE TABLE teacher (
    employee_id VARCHAR(10) PRIMARY KEY,
    name VARCHAR(50),
    father VARCHAR(50),
    gender VARCHAR(10),
    dob VARCHAR(20),
    address VARCHAR(100),
    phone VARCHAR(20),
    email VARCHAR(50),
    education VARCHAR(50),
    department VARCHAR(20)
);

-- Anwesenheit (vereinfacht)
CREATE TABLE student_attendance (
    rollno VARCHAR(10),
    date VARCHAR(20),
    attendance VARCHAR(10)
);

CREATE TABLE teacher_attendance (
    employee_id VARCHAR(10),
    date VARCHAR(20),
    attendance VARCHAR(10)
);

-- Noten (vereinfacht)
CREATE TABLE marks (
    rollno VARCHAR(10),
    course VARCHAR(20),
    semester VARCHAR(10),
    marks INT
);

-- Gebühren (vereinfacht)
CREATE TABLE fee (
    rollno VARCHAR(10),
    amount VARCHAR(20),
    paid VARCHAR(20),
    balance VARCHAR(20)
);
```

#### 2. Datenbankverbindung konfigurieren

Bearbeiten Sie `src/university/conn.java`:

```java
Connection c = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/university",
    "root",
    "IhrPasswort"
);
```

#### 3. Projekt kompilieren

```bash
# Mit javac
javac -cp ".:rs2xml.jar:mysql-connector-java-8.0.27.jar" src/university/*.java

# Oder verwenden Sie Ihre IDE
```

#### 4. Ausführung

```bash
# Von Terminal
java -cp ".:rs2xml.jar:mysql-connector-java-8.0.27.jar" university.Login

# Oder aus Ihrer IDE
```

## 🎯 Verwendung

### Erste Schritte

1. **Login**: Starten Sie die Anwendung
2. **Datenbank konfigurieren**: Erstellen Sie die erforderlichen Tabellen
3. **Initial Login**: Erstellen Sie einen Benutzer in der `login` Tabelle

### Hauptfunktionen

#### Master (Einstellungen)
- **New Faculty**: Neuen Lehrer registrieren
- **New Student Admission**: Student aufnehmen

#### Details
- **Student Details**: Alle Studenten anzeigen
- **Teacher Details**: Alle Lehrer anzeigen

#### Anwesenheit
- **Student Attendance**: Anwesenheit für Studenten erfassen
- **Teacher Attendance**: Anwesenheit für Lehrer erfassen
- **Attendance Details**: Anwesenheitsberichte anzeigen

#### Prüfungen
- **Examination Details**: Prüfungen verwalten
- **Enter Marks**: Noten eingeben

#### Update Details
- **Update Students**: Studenten-Informationen bearbeiten
- **Update Teachers**: Lehrer-Informationen bearbeiten

#### Gebühren
- **Fee Structure**: Gebührenstruktur definieren
- **Student Fee Form**: Gebührenzahlungen verwalten

#### Utility
- **Notepad**: Windows Notepad öffnen
- **Calculator**: Windows Rechner öffnen
- **Web Browser**: Browser öffnen

## 📁 Projektstruktur

```
University Management System/
├── src/
│   ├── university/
│   │   ├── Login.java                        # Login-Fenster
│   │   ├── conn.java                        # Datenbankverbindung
│   │   ├── Project.java                     # Hauptmenü
│   │   ├── AddStudent.java                  # Student hinzufügen
│   │   ├── AddTeacher.java                  # Lehrer hinzufügen
│   │   ├── StudentDetails.java              # Studentenliste
│   │   ├── TeacherDetails.java              # Lehrerliste
│   │   ├── UpdateStudent.java               # Student aktualisieren
│   │   ├── UpdateTeacher.java               # Lehrer aktualisieren
│   │   ├── StudentAttendance.java           # Studenten-Anwesenheit
│   │   ├── TeacherAttendance.java           # Lehrer-Anwesenheit
│   │   ├── StudentAttendanceDetail.java     # Anwesenheitsdetails
│   │   ├── TeacherAttendanceDetail.java     # Anwesenheitsdetails
│   │   ├── ExaminationDetails.java          # Prüfungsverwaltung
│   │   ├── EnterMarks.java                  # Noteneingabe
│   │   ├── Marks.java                       # Notenansicht
│   │   ├── FeeStructure.java                # Gebührenstruktur
│   │   └── StudentFeeForm.java             # Gebührenformular
│   └── icons/                                # Bilder und Assets
│       ├── logo.jpg
│       └── [weitere Icons]
├── build/                                    # Kompilierte Klassen
├── out/                                      # Output-Verzeichnis
├── mysql-connector-java-8.0.27.jar
├── rs2xml.jar                               # Report-Utility
└── build.xml                                # Build-Konfiguration
```

## 🏗️ Architektur

### Datenzugriff

- **conn.java**: Zentrale Datenbankverbindung
- JDBC für MySQL-Integration
- RS2XML für Tabellen-Anzeige

### Präsentation

- **Swing GUI**: Plattformübergreifende Benutzeroberfläche
- **Menü-basiert**: Hauptmenü mit Untermenüs
- **Formulare**: Eingabemasken für alle Funktionen

### Geschäftslogik

- **CRUD-Operationen**: Studenten & Lehrer
- **Anwesenheitsverfolgung**: Automatische Berechnungen
- **Gebührenverwaltung**: Zahlungstracking
- **Notenverwaltung**: Leistungsverfolgung

## 💾 Datenbank-Schema (Vereinfacht)

### Studenten
```
rollno          VARCHAR(10)    PRIMARY KEY
name            VARCHAR(50)
father          VARCHAR(50)
gender          VARCHAR(10)
dob             VARCHAR(20)
address         VARCHAR(100)
phone           VARCHAR(20)
email           VARCHAR(50)
x_percent       VARCHAR(10)   10. Klasse Noten
xii_percent     VARCHAR(10)   12. Klasse Noten
aadhar          VARCHAR(20)
course          VARCHAR(20)
branch          VARCHAR(20)
```

### Lehrer
```
employee_id     VARCHAR(10)    PRIMARY KEY
name            VARCHAR(50)
father          VARCHAR(50)
gender          VARCHAR(10)
dob             VARCHAR(20)
address         VARCHAR(100)
phone           VARCHAR(20)
email           VARCHAR(50)
education       VARCHAR(50)
department      VARCHAR(20)
```

### Anwesenheit
```
rollno          VARCHAR(10)
date            VARCHAR(20)
attendance      VARCHAR(10)    Anwesend/Abwesend
```

### Noten
```
rollno          VARCHAR(10)
course          VARCHAR(20)
semester        VARCHAR(10)
marks           INT
```

### Gebühren
```
rollno          VARCHAR(10)
amount          VARCHAR(20)   Gesamtbetrag
paid            VARCHAR(20)   Gezahlt
balance         VARCHAR(20)   Ausstehend
```

## 🔑 Hauptfunktionen im Detail

### Studentenverwaltung

#### Neue Studenten aufnehmen
- Persönliche Informationen
- Kontaktdaten
- Bildungshintergrund (10./12. Klasse)
- Kursauswahl
- Zweig-Auswahl

#### Studentendetails
- Vollständiges Profil
- Anwesenheitsstatus
- Notenübersicht
- Gebührenstatus

### Lehrerverwaltung

#### Neue Lehrer aufnehmen
- Persönliche Informationen
- Qualifikationen
- Fachbereich
- Kontaktdaten

#### Lehrerdetails
- Vollständiges Profil
- Anwesenheitsübersicht
- Fachzuordnung

### Anwesenheit

#### Studenten-Anwesenheit
- Tägliche Erfassung
- Nach Student filtern
- Nach Datum filtern
- Statistiken berechnen

#### Lehrer-Anwesenheit
- Tägliche Erfassung
- Nach Lehrer filtern
- Überblicksberichte

### Prüfungen & Noten

#### Prüfungsdetails
- Prüfungsverwaltung
- Termine setzen
- Raumzuweisung

#### Noten eingeben
- Student auswählen
- Kurs/Semester auswählen
- Noten eingeben
- Gesamtnote berechnen

### Gebühren

#### Gebührenstruktur
- Kursbasierte Gebühren
- Semestergebühren
- Einmalige Gebühren

#### Gebührenverwaltung
- Zahlungen erfassen
- Ausstehende Beträge verfolgen
- Quittungen generieren

## 🎨 Benutzeroberfläche

### Hauptmerkmale
- **Menüleiste**: Alle Funktionen zugänglich
- **Icons**: Visuelle Hilfe
- **Tastenkombinationen**: Schnelle Navigation
- **Responsive Layout**: Anpassungsfähiges Design

### Menüstruktur
1. **Master**: Grundfunktionen (Student/Lehrer hinzufügen)
2. **Details**: Anzeigen von Listen
3. **Attendance**: Anwesenheitsverwaltung
4. **Examination**: Prüfungen & Noten
5. **Update Details**: Informationen bearbeiten
6. **Fee Details**: Gebührenverwaltung
7. **Utility**: Hilfsprogramme
8. **Exit**: Beenden

## ⚠️ Bekannte Probleme

1. **SQL-Injection**: Keine PreparedStatements
2. **Keine Validierung**: Eingaben werden nicht validiert
3. **Passwort-Sicherheit**: Klartext-Speicherung
4. **Windows-spezifisch**: Utility-Funktionen nur Windows
5. **Hardcodierte Pfade**: Pfade nicht portabel

## 🚀 Zukünftige Verbesserungen

- [ ] Implementierung von PreparedStatements
- [ ] Passwort-Verschlüsselung
- [ ] Eingabevalidierung
- [ ] Multi-Plattform-Support
- [ ] Email-Benachrichtigungen
- [ ] SMS-Integration für Anwesenheit
- [ ] Berichtsexport (PDF, Excel)
- [ ] Backup & Restore
- [ ] Cloud-Integration
- [ ] Mobile App
- [ ] Unit-Tests
- [ ] REST API
- [ ] Dashboard mit Statistiken
- [ ] Barcode-Scanner für Anwesenheit

## 📝 Entwicklerhinweise

### Code-Organisation
- Modulare Struktur
- Jede Funktion in separater Klasse
- Wiederverwendbare Komponenten

### Best Practices
- Implementieren Sie das Repository-Pattern
- Trennen Sie GUI, Service und DAO
- Verwenden Sie Dependency Injection
- Implementieren Sie Validierung auf Service-Ebene

## 🎓 Verwendungsszenarien

### Szenario 1: Semesterstart
1. Studenten aufnehmen
2. Gebührenstruktur definieren
3. Kurse zuweisen
4. Lehrer zuordnen

### Szenario 2: Tägliche Operationen
1. Anwesenheit erfassen
2. Noten eingeben
3. Gebührenzahlungen verarbeiten
4. Berichte erstellen

### Szenario 3: Semesterende
1. Noten berechnen
2. Abschlussprüfungen verwalten
3. Gebührenstatus prüfen
4. Semester-Reports erstellen

## 📄 Lizenz

Dieses Projekt ist für Bildungs- und Demonstrationszwecke erstellt worden.

## 🤝 Beitragen

Beiträge sind willkommen! Bitte:
1. Forken Sie das Repository
2. Erstellen Sie einen Feature-Branch
3. Committen Sie Ihre Änderungen
4. Erstellen Sie einen Pull Request
