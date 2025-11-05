# 🏦 Bank Management System

Ein vollständiges ATM (Automated Teller Machine) System, entwickelt mit Java Swing GUI. Dieses System simuliert eine echte Bankomaten-Umgebung mit allen grundlegenden Banking-Funktionen.

## 📋 Übersicht

Das Bank Management System ist eine Desktop-Anwendung, die alle wichtigen Geldautomat-Funktionen bereitstellt. Benutzer können Konten anlegen, Geld einzahlen, abheben, ihren Kontostand prüfen und Transaktionen durchführen.

## ✨ Features

### Benutzer-Features
- 🔐 **Login/Signup**: Sichere Authentifizierung mit Kartennummer und PIN
- 💰 **Einzahlung (Deposit)**: Geld auf das Konto einzahlen
- 💸 **Abhebung (Withdrawal)**: Geld vom Konto abheben
- 💵 **Schnellauszahlung (Fast Cash)**: Vordefinierte Beträge schnell abheben
- 📊 **Kontostand (Balance Enquiry)**: Aktuellen Kontostand abfragen
- 📝 **Mini-Statement**: Transaktionshistorie anzeigen
- 🔑 **PIN-Änderung**: Persönliche PIN ändern
- 🎨 **ATM-gemäßes Interface**: Realistische ATM-Benutzeroberfläche

### Technische Features
- 🗄️ **MySQL Integration**: Sichere Datenbankanbindung
- 🔒 **Sicherheit**: PIN-basierte Authentifizierung
- 📱 **Swing GUI**: Plattformübergreifende Desktop-Oberfläche
- 🎯 **Modulare Architektur**: Sauberer Code mit separater Logik für jede Funktion

## 🛠️ Technologie-Stack

- **Java**: Core-Programmiersprache
- **Java Swing**: GUI-Framework
- **MySQL**: Relationale Datenbank
- **JDBC**: Datenbankverbindung
- **JCalendar**: Datumsauswahl für Signup-Prozess
- **mysql-connector-j-9.3.0**: MySQL-Treiber

## 📦 Installation

### Voraussetzungen
1. Java JDK 8 oder höher
2. MySQL Server (Version 5.7 oder höher)
3. IDE (NetBeans, Eclipse, IntelliJ IDEA)

### Setup-Schritte

#### 1. Datenbank erstellen
```sql
CREATE DATABASE bms;
USE bms;

-- Login-Tabelle
CREATE TABLE login (
    cardno VARCHAR(20),
    pin VARCHAR(20)
);

-- Signup-Tabellen (für Benutzerdetails)
CREATE TABLE signup (
    formno VARCHAR(20),
    name VARCHAR(50),
    fname VARCHAR(50),
    dob VARCHAR(50),
    gender VARCHAR(50),
    email VARCHAR(50),
    marital VARCHAR(50),
    address VARCHAR(50),
    city VARCHAR(50),
    pincode VARCHAR(50),
    state VARCHAR(50)
);

CREATE TABLE signuptwo (
    formno VARCHAR(20),
    religion VARCHAR(20),
    category VARCHAR(20),
    income VARCHAR(20),
    education VARCHAR(20),
    occupation VARCHAR(20),
    pan VARCHAR(20),
    aadhar VARCHAR(20),
    senior VARCHAR(20),
    existing VARCHAR(20)
);

CREATE TABLE signupthree (
    formno VARCHAR(20),
    account VARCHAR(50),
    cardno VARCHAR(50),
    pin VARCHAR(50),
    facility VARCHAR(200)
);

-- Kontodetails
CREATE TABLE bank (
    pin VARCHAR(20),
    date VARCHAR(50),
    type VARCHAR(50),
    amount VARCHAR(50)
);
```

#### 2. Datenbankverbindung konfigurieren
Bearbeiten Sie `src/Bank/Conn.java` und aktualisieren Sie die Verbindungsdetails:
```java
Connection c = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/bms",
    "root",
    "IhrPasswort"
);
```

#### 3. Projekt kompilieren
```bash
# Mit javac
javac -cp ".:mysql-connector-j-9.3.0.jar" src/Bank/*.java

# Oder verwenden Sie Ihren IDE-Compiler
```

#### 4. Ausführung
```bash
# Von Terminal aus
java -cp ".:mysql-connector-j-9.3.0.jar" Bank.Login

# Oder aus Ihrer IDE heraus
```

## 🎯 Verwendung

### Neuen Benutzer registrieren
1. Starten Sie die Anwendung durch Ausführen von `Login.java`
2. Klicken Sie auf "SIGN UP"
3. Füllen Sie alle erforderlichen Informationen aus:
   - Persönliche Informationen (Signup.java)
   - Weitere Informationen (Signup2.java)
   - Konto- und Kartendetails (Signup3.java)
4. Notieren Sie sich Ihre Kartennummer und PIN

### Login und Banking-Funktionen
1. Geben Sie Ihre Kartennummer und PIN ein
2. Wählen Sie aus den verfügbaren Transaktionen:
   - **DEPOSIT**: Geld einzahlen
   - **CASH WITHDRAWL**: Geld abheben
   - **FAST CASH**: Schnelles Abheben von Standardbeträgen
   - **MINI STATEMENT**: Transaktionsverlauf anzeigen
   - **PIN CHANGE**: PIN ändern
   - **BALANCE ENQUIRY**: Kontostand prüfen
   - **EXIT**: Beenden

## 📁 Projektstruktur

```
Bank-Management-System/
├── src/Bank/
│   ├── Login.java           # Login-Fenster und Authentifizierung
│   ├── Conn.java            # Datenbankverbindung
│   ├── Signup.java          # Anmeldeformular - Teil 1
│   ├── Signup2.java         # Anmeldeformular - Teil 2
│   ├── Signup3.java         # Anmeldeformular - Teil 3
│   ├── Transactions.java    # Hauptmenü für Transaktionen
│   ├── Deposit.java         # Einzahlungsfunktion
│   ├── Withdrawl.java       # Abhebungsfunktion
│   ├── FastCash.java        # Schnellauszahlung
│   ├── MiniStatement.java   # Transaktionsverlauf
│   ├── BalanceEnquiry.java  # Kontostandabfrage
│   ├── Pin.java             # PIN-Änderung
│   ├── BalanceEquiry.java   # Balance-Detailansicht
│   └── icons/               # Bilder und Assets
│       ├── logo.jpg
│       └── atm.jpg
├── build/                   # Kompilierte Klassen
├── out/                     # Output-Verzeichnis
├── mysql-connector-j-9.3.0.jar
├── jcalendar-tz-1.3.3-4.jar
└── build.xml                # Build-Konfiguration
```

## 🏗️ Architektur

Das System besteht aus mehreren modularen Komponenten:

### Datenbankebene
- **Conn.java**: Zentrale Datenbankverbindungsklasse
- Verwendet Singleton-Pattern für Verbindungswiederverwendung

### Präsentationsebene
- Swing-basierte GUI-Komponenten
- Jeder Bildschirm ist eine separate Klasse
- Konsistente visuelle Identität mit ATM-Theme

### Geschäftslogik-Ebene
- Transaktionsbehandlung mit Validierung
- PIN-Management und Sicherheit
- Kontostandsberechnung in Echtzeit

## 🔒 Sicherheitshinweise

**Wichtig für Produktion**:
1. **PIN-Hashing**: PINs sollten niemals im Klartext gespeichert werden
2. **SQL-Injection-Schutz**: Verwenden Sie PreparedStatements
3. **Verschlüsselung**: Sensible Daten verschlüsseln
4. **Session-Management**: Implementieren Sie Zeitlimits für Sitzungen
5. **Audit-Logging**: Loggen Sie alle Transaktionen für Compliance

Dieses Projekt ist für Lernzwecke und sollte nicht ohne Sicherheitsverbesserungen für den Produktionseinsatz verwendet werden.

## 🚀 Zukünftige Verbesserungen

- [ ] Implementierung von PreparedStatements für SQL-Sicherheit
- [ ] PIN-Verschlüsselung mit Hash-Algorithmen
- [ ] Session-Management mit Timeouts
- [ ] Audit-Logging für alle Transaktionen
- [ ] CSV-Export für Transaktionsberichte
- [ ] Konfigurationsdateien für Datenbankverbindungen
- [ ] Unit-Tests hinzufügen
- [ ] Multi-Language-Support

## 📝 Entwicklerhinweise

### Code-Kommentierung
- Fügen Sie Javadoc-Kommentare hinzu
- Dokumentieren Sie komplexe Logik
- Erklären Sie Geschäftsregeln

### Code-Organisation
- Trennen Sie GUI, Logik und Datenzugriff
- Implementieren Sie das MVC-Pattern
- Verwenden Sie Services für Geschäftslogik

## 📄 Lizenz

Dieses Projekt ist für Bildungszwecke entwickelt worden. Bitte verwenden Sie es verantwortungsbewusst.

## 👥 Beitragen

Beiträge sind willkommen! Bitte erstellen Sie einen Pull Request mit detaillierter Beschreibung Ihrer Änderungen.
