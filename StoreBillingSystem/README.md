# 🏪 Store Billing System

Ein umfassendes Laden-Kassensystem mit vollständiger Produkt- und Lagerverwaltung, Verkaufsabwicklung und Administrator-Panel. Entwickelt mit Java Swing für eine benutzerfreundliche Desktop-Oberfläche.

## 📋 Übersicht

Das Store Billing System ist eine vollständige Retail-Management-Lösung für kleine bis mittlere Geschäfte. Es bietet Produktverwaltung, Lagerbestandsverfolgung, Verkaufsabwicklung, Rechnungserstellung und ein Administrator-Panel für die Verwaltung von Kassierern und Produkten.

## ✨ Features

### 🛒 Geschäfts-Features

#### Produktverwaltung
- ➕ **Produkt hinzufügen**: Neue Produkte mit Details, Hersteller und Bestand
- ✏️ **Produkt aktualisieren**: Bestehende Produkte bearbeiten
- 🗑️ **Produkt löschen**: Produkte aus dem System entfernen
- 🔍 **Produkt suchen**: Schnelle Suche nach Produkt-ID
- 📦 **Lagerbestand anzeigen**: Übersicht des gesamten Warenbestands
- 📊 **Nach Hersteller filtern**: Produkte nach Unternehmen gruppieren

#### Verkauf & Rechnung
- 🛍️ **Verkauf**: Kundentransaktionen mit Produktsuche
- 🧾 **Rechnung erstellen**: Professionelle Rechnungsgenerierung
- 💳 **Zahlungsarten**: Flexible Zahlungsoptionen
- 📋 **Rechnungsdetails**: Vollständige Rechnungsinformationen
- 💰 **Gesamtbetrag**: Automatische Berechnung von Summen

#### Benutzerverwaltung
- 👥 **Kassierer-Verwaltung**: Hinzufügen und Verwalten von Kassierern
- 🔐 **Sicherheit**: Login-System mit Rollen (Admin/Kassierer)
- 🚫 **Kassierer löschen**: Entfernen von Benutzern
- 🔎 **Kassierer suchen**: Benutzersuche nach E-Mail

#### Administrator-Panel
- 👨‍💼 **Admin-Funktionen**: 
  - Produkt-Management
  - Kassierer-Verwaltung
  - Lagerbestandsübersicht
  - Verkaufsanalyse
- 📊 **Berichte**: Verkaufsübersicht und Statistiken

## 🛠️ Technologie-Stack

- **Java**: Programmiersprache
- **Java Swing**: GUI-Framework
- **MySQL**: Relationale Datenbank
- **JDBC**: Datenbankverbindung
- **mysql-connector-java-8.0.27**: MySQL-Treiber

## 📦 Installation

### Voraussetzungen

- Java JDK 8 oder höher
- MySQL Server (Version 5.7 oder höher)
- IDE (NetBeans, Eclipse, IntelliJ IDEA)

### Setup-Schritte

#### 1. Datenbank erstellen

```sql
CREATE DATABASE sbs;
USE sbs;

-- Produkttabelle
CREATE TABLE stock (
    ProductID VARCHAR(20) PRIMARY KEY,
    Detail VARCHAR(100),
    Company VARCHAR(100),
    Quantity INT
);

-- Benutzertabelle
CREATE TABLE users (
    Email VARCHAR(100) PRIMARY KEY,
    Password VARCHAR(50)
);

-- Verkaufstabelle
CREATE TABLE sale (
    ProductID VARCHAR(20),
    Company VARCHAR(100),
    Date VARCHAR(20),
    Payment VARCHAR(20),
    Quantity INT,
    CashierName VARCHAR(100)
);
```

#### 2. Datenbankverbindung konfigurieren

Bearbeiten Sie `src/store/DB.java`:

```java
Connection conn = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/sbs",
    "root",
    "IhrPasswort"
);
```

#### 3. Projekt kompilieren

```bash
# Mit javac
javac -cp ".:mysql-connector-java-8.0.27.jar" src/store/*.java

# Oder verwenden Sie Ihre IDE
```

#### 4. Ausführung

```bash
# Von Terminal
java -cp ".:mysql-connector-java-8.0.27.jar" store.Login

# Oder aus Ihrer IDE
```

## 🎯 Verwendung

### Erste Schritte

1. **Login**: Starten Sie die Anwendung
2. **Admin-Account erstellen**:
   - Standard Admin-Login: `admin` / `[Ihr Passwort]`
   - Erstellen Sie zunächst einen Admin-User über MySQL

### Workflow

#### 1. Admin-Panel (Administrator)

- **Produkte verwalten**:
  - Product → Add Product: Neues Produkt hinzufügen
  - Product → Update Product: Bestand aktualisieren
  - Product → Delete Product: Produkt entfernen
  - Stock → Show Stock: Lagerbestand anzeigen

- **Kassierer verwalten**:
  - Cashier → Add Cashier: Neuen Kassierer hinzufügen
  - Cashier → Delete Cashier: Kassierer entfernen
  - Search → Search Cashier: Kassierer suchen

- **Verkäufe analysieren**:
  - Sale → View Sale: Verkaufsübersicht

#### 2. Verkaufs-Terminal (Kassierer)

- **Kunde bedienen**:
  - Produkte suchen und hinzufügen
  - Mengen anpassen
  - Gesamtbetrag berechnen
  - Rechnung erstellen
  - Zahlung verarbeiten

#### 3. Alltägliche Operationen

- **Lagerbestand prüfen**: Vor Verkäufen Lagerbestand überprüfen
- **Produkte aktualisieren**: Bestände nach neuen Lieferungen aktualisieren
- **Verkäufe bearbeiten**: Transaktionen durchführen
- **Berichte erstellen**: Verkaufsstatistiken anzeigen

## 📁 Projektstruktur

```
StoreBillingSystem/
├── src/store/
│   ├── Login.java           # Login-Fenster
│   ├── DB.java              # Datenbankzugriff & Business-Logic
│   ├── AdminPanel.java      # Admin-Hauptfenster
│   ├── addProduct.java      # Produkt hinzufügen
│   ├── updateProduct.java   # Produkt aktualisieren
│   ├── deleteProduct.java   # Produkt löschen
│   ├── searchProduct.java   # Produkt suchen
│   ├── showStock.java       # Lagerbestand anzeigen
│   ├── addCashier.java      # Kassierer hinzufügen
│   ├── deleteCashier.java   # Kassierer löschen
│   ├── searchCashier.java   # Kassierer suchen
│   ├── generateInvoice.java # Rechnung generieren
│   ├── Sale.java            # Verkaufs-Terminal
│   └── Invoice.java         # Rechnungsansicht
├── build/                   # Kompilierte Klassen
├── out/                     # Output-Verzeichnis
├── mysql-connector-java-8.0.27.jar
└── build.xml               # Build-Konfiguration
```

## 🏗️ Architektur

### Datenzugriffsschicht

- **DB.java**: 
  - Zentrale Datenbankverbindung
  - Alle CRUD-Operationen
  - Wiederverwendbare Methoden für Datenbankzugriffe

### Präsentationsschicht

- **Login**: Authentifizierung und Rollenverwaltung
- **AdminPanel**: Hauptverwaltungsoberfläche
- **Verkaufs-Terminals**: Benutzerfreundliche Verkaufssoberflächen
- **Formulare**: Eingabemasken für verschiedene Operationen

### Geschäftslogik

- **Produktverwaltung**: CRUD-Operationen für Produkte
- **Benutzerverwaltung**: Kassierer-Management
- **Verkaufslogik**: Transaktionsverarbeitung
- **Rechnungserstellung**: Automatische Berechnungen

## 💾 Datenbank-Schema

### stock (Produkte)
```
ProductID     VARCHAR(20)    PRIMARY KEY
Detail        VARCHAR(100)   Produktbeschreibung
Company       VARCHAR(100)   Hersteller/Firma
Quantity      INT            Lagerbestand
```

### users (Benutzer)
```
Email         VARCHAR(100)   PRIMARY KEY
Password      VARCHAR(50)    Passwort
```

### sale (Verkäufe)
```
ProductID     VARCHAR(20)    Produkt-ID
Company       VARCHAR(100)   Hersteller
Date          VARCHAR(20)    Verkaufsdatum
Payment       VARCHAR(20)    Zahlungsmethode
Quantity      INT            Verkaufte Menge
CashierName   VARCHAR(100)   Kassierer-Name
```

## 🔒 Sicherheit

### Aktuelle Implementierung

- Passwort-basierte Authentifizierung
- Rollenbasierte Zugriffskontrolle (Admin/Kassierer)
- Datenbank-Validierung

### Empfehlungen für Produktion

⚠️ **Wichtige Sicherheitsverbesserungen erforderlich**:

1. **Passwort-Hashing**: Verwendens Sie BCrypt oder Argon2
2. **SQL-Injection-Schutz**: Implementieren Sie PreparedStatements
3. **Session-Management**: Implementieren Sie Token-basierte Sessions
4. **Audit-Logging**: Loggen Sie alle Transaktionen
5. **Backup-System**: Automatische Datenbanksicherungen
6. **Input-Validierung**: Validieren Sie alle Benutzereingaben
7. **Konfigurationsdateien**: Entfernen Sie hardcodierte Passwörter

## 📊 Hauptfunktionen im Detail

### Produktverwaltung

#### Produkt hinzufügen
- Produkt-ID (eindeutig)
- Detail/Beschreibung
- Hersteller/Firma
- Anfangsbestand

#### Produkt aktualisieren
- Produkt-ID auswählen
- Neue Details eingeben
- Bestand anpassen

#### Lagerbestand
- Gesamtübersicht aller Produkte
- Nach Hersteller filtern
- Mengenstatus in Echtzeit

### Verkaufssystem

1. **Verkauf starten**:
   - Produkt-ID eingeben
   - System zeigt Produktname und Hersteller
   - Bestand wird geprüft

2. **Produkt hinzufügen**:
   - Warenkorb füllen
   - Mengen anpassen
   - Gesamtbetrag wird automatisch berechnet

3. **Rechnung erstellen**:
   - Kundendaten eingeben
   - Zahlungsmethode wählen
   - Rechnung drucken

### Berichte

- **Verkaufsübersicht**: Alle Transaktionen
- **Nach Datum filtern**: Bestimmte Zeiträume
- **Nach Hersteller filtern**: Produktgruppen

## 🐛 Bekannte Probleme

1. **SQL-Injection**: Keine PreparedStatements
2. **Passwort-Sicherheit**: Klartext-Speicherung
3. **Keine Validierung**: Eingaben werden nicht validiert
4. **Fehlerbehandlung**: Basale Exception-Behandlung
5. **GUI-Updates**: Thread-Sicherheit bei DB-Operationen

## 🚀 Zukünftige Verbesserungen

- [ ] Implementierung von PreparedStatements
- [ ] Passwort-Verschlüsselung mit BCrypt
- [ ] Barcode-Scanner-Integration
- [ ] Export zu Excel/PDF
- [ ] Bestandswarnungen bei niedrigem Lagerbestand
- [ ] Multi-Benutzer-Support mit Sessions
- [ ] Dark Mode UI
- [ ] Tastenkombinationen für schnelle Eingabe
- [ ] Backup & Restore-Funktionalität
- [ ] Unit-Tests hinzufügen
- [ ] REST API entwickeln
- [ ] Mobile App Integration

## 📝 Entwicklerhinweise

### Code-Struktur

- **DB.java** enthält alle Datenbankoperationen
- Modulare Klasse-Struktur
- GUI-Komponenten getrennt

### Best Practices

- Implementieren Sie das Repository-Pattern
- Trennen Sie GUI, Service und DAO
- Verwenden Sie Dependency Injection
- Implementieren Sie Transaction Management

## 🎓 Lernressourcen

Dieses Projekt demonstriert:
- Java Swing GUI-Entwicklung
- MySQL-Integration mit JDBC
- CRUD-Operationen
- Software-Architektur-Pattern
- Desktop-Anwendungsentwicklung

## 📄 Lizenz

Dieses Projekt ist für Bildungs- und Demonstrationszwecke erstellt worden.

## 🤝 Beitragen

Beiträge sind willkommen! Bitte:
1. Forken Sie das Repository
2. Erstellen Sie einen Feature-Branch
3. Committen Sie Ihre Änderungen
4. Erstellen Sie einen Pull Request mit detaillierter Beschreibung
