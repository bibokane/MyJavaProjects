# 🦠 COVID-19 Tracker

Eine moderne Spring Boot Web-Anwendung zur Echtzeit-Trackierung von COVID-19 Fallzahlen weltweit. Die Anwendung ruft aktuelle Daten von JHU CSSE ab und stellt sie in einer benutzerfreundlichen Web-Oberfläche dar.

## 📋 Übersicht

Der COVID-19 Tracker ist eine Spring Boot Web-Anwendung, die täglich aktualisierte COVID-19 Fallzahlen aus dem Johns Hopkins Center for Systems Science and Engineering (CSSE) Dataset abruft und anzeigt. Die Anwendung zeigt die Gesamtzahl der gemeldeten Fälle, die Anzahl neuer Fälle sowie eine detaillierte Aufschlüsselung nach Ländern und Regionen.

## ✨ Features

- 🌍 **Weltweite COVID-19-Daten**: Echtzeit-Updates aus dem JHU CSSE Dataset
- 📊 **Interaktive Darstellung**: Übersichtliche Anzeige aller Länder und Regionen
- 📈 **Statistiken**: 
  - Gesamtanzahl gemeldeter Fälle weltweit
  - Anzahl neuer Fälle seit dem Vortag
  - Fallzahlen nach Ländern
- 🔄 **Automatische Updates**: Scheduler lädt alle Daten automatisch aktualisiert
- 🎨 **Moderne UI**: Thymeleaf-basierte Vorlagen für ein responsive Design
- ⚡ **Hohe Performance**: Caching und effiziente Datenverarbeitung

## 🛠️ Technologie-Stack

- **Java 21**: Moderne Java-Version
- **Spring Boot 3.5.0**: Web-Framework
- **Thymeleaf**: Template-Engine für dynamische HTML-Seiten
- **Apache Commons CSV**: CSV-Datenverarbeitung
- **HttpClient**: HTTP-Anfragen für Datenabruf
- **Maven**: Dependency Management und Build-Tool

## 📦 Installation

### Voraussetzungen

- Java JDK 21 oder höher
- Maven 3.6+ (oder Maven Wrapper verwendet das Projekt)
- Internetverbindung (für Datenabruf)

### Setup-Schritte

#### 1. Repository klonen/navigieren
```bash
cd covid-tracker
```

#### 2. Maven-Abhängigkeiten installieren
```bash
# Verwenden Sie den Maven Wrapper
./mvnw clean install

# Oder verwenden Sie Ihr lokales Maven
mvn clean install
```

#### 3. Anwendung starten
```bash
# Mit Maven Wrapper
./mvnw spring-boot:run

# Oder mit lokalem Maven
mvn spring-boot:run

# Oder als JAR
java -jar target/covid-tracker-0.0.1-SNAPSHOT.jar
```

#### 4. Zugriff auf die Anwendung
Öffnen Sie Ihren Browser und navigieren Sie zu:
```
http://localhost:8080
```

## 🚀 Verwendung

### Starten der Anwendung

1. **Von der IDE aus**:
   - Öffnen Sie das Projekt in Ihrer IDE (IntelliJ IDEA, Eclipse, VS Code)
   - Navigieren Sie zu `CovidTrackerApplication.java`
   - Führen Sie die `main` Methode aus

2. **Von Terminal aus**:
   ```bash
   cd covid-tracker
   ./mvnw spring-boot:run
   ```

### Datenabruf

Die Anwendung:
- Startet und lädt sofort Daten beim ersten Start (`@PostConstruct`)
- Aktualisiert die Daten automatisch jede Minute (Scheduler: `@Scheduled(cron = "1 * * * * *")`)
- Verbindet zu: `https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv`

## 📁 Projektstruktur

```
covid-tracker/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/covidtracker/covid_tracker/
│   │   │       ├── CovidTrackerApplication.java    # Hauptklasse
│   │   │       ├── controllers/
│   │   │       │   └── HomeController.java          # MVC Controller
│   │   │       ├── models/
│   │   │       │   └── LocationStates.java          # Datenmodell
│   │   │       └── services/
│   │   │           └── CoronaVirusDataService.java  # Service-Schicht
│   │   └── resources/
│   │       ├── application.properties               # Konfiguration
│   │       └── templates/
│   │           └── home.html                        # Thymeleaf Template
│   └── test/
│       └── java/
│           └── .../                                  # Test-Klassen
├── pom.xml                                           # Maven-Konfiguration
├── mvnw                                              # Maven Wrapper
└── mvnw.cmd                                          # Maven Wrapper (Windows)
```

## 🏗️ Architektur

### MVC-Pattern

- **Model**: `LocationStates.java` - Repräsentiert COVID-19-Daten für eine Region
- **View**: `home.html` (Thymeleaf Template) - UI-Darstellung
- **Controller**: `HomeController.java` - Verarbeitet HTTP-Anfragen

### Service-Layer

- **CoronaVirusDataService**: 
  - Lädt CSV-Daten von GitHub
  - Verarbeitet und konvertiert CSV in Domain-Objekte
  - Caching von Daten im Speicher
  - Automatische Aktualisierung über Scheduler

### Datenfluss

```
Internet (GitHub) 
    ↓
CoronaVirusDataService (lädt CSV)
    ↓
Parsing & Konvertierung
    ↓
Memory Cache (List<LocationStates>)
    ↓
HomeController (holt Daten)
    ↓
Thymeleaf Template
    ↓
Browser (HTML-Seite)
```

## 🔧 Konfiguration

### application.properties

```properties
spring.application.name=covid-tracker
# Server-Port kann angepasst werden
server.port=8080
```

### Scheduler-Anpassung

Um die Update-Frequenz zu ändern, bearbeiten Sie `CoronaVirusDataService.java`:

```java
// Aktuell: Jede Sekunde (1 * * * * *)
@Scheduled(cron = "1 * * * * *")

// Alle 5 Minuten
@Scheduled(cron = "0 */5 * * * *")

// Täglich um Mitternacht
@Scheduled(cron = "0 0 0 * * *")
```

## 📊 Datenmodell

### LocationStates

```java
public class LocationStates {
    private String state;           // Bundesstaat/Provinz
    private String country;          // Land
    private int latestTotalCases;   // Gesamtfälle
    private int diffFromPrevDay;    // Neufälle seit gestern
}
```

## 🌐 API-Integration

Die Anwendung nutzt die kostenlose JHU CSSE COVID-19 Datenquelle:
- **URL**: GitHub Repository von Johns Hopkins CSSE
- **Format**: CSV (Comma-Separated Values)
- **Update-Frequenz**: Täglich aktualisiert
- **Lizenz**: Öffentlich verfügbar

## 🎨 Benutzeroberfläche

Die Anwendung verwendet Thymeleaf-Templates für die Darstellung:
- Responsive Design
- Tabellendarstellung der Daten
- Hervorhebung von Statistiken
- Länder/Region-spezifische Aufschlüsselung

## 🔄 Scheduler-Konfiguration

Die Anwendung verwendet Spring Scheduling:
- `@PostConstruct`: Lädt Daten beim Start
- `@Scheduled`: Lädt Daten periodisch
- Default: Alle 1 Minute (konfigurierbar)


## 🚀 Deployment

### Als JAR-Datei

```bash
# Build erstellen
./mvnw clean package

# JAR ausführen
java -jar target/covid-tracker-0.0.1-SNAPSHOT.jar
```

### Docker (Optional)

```dockerfile
FROM openjdk:21-jdk-slim
COPY target/covid-tracker-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

## ⚠️ Bekannte Einschränkungen

1. **Datenverzögerung**: Daten werden erst am nächsten Tag aktualisiert
2. **Keine Historie**: Nur aktuelle Daten werden angezeigt
3. **Kein Persisting**: Daten werden nur im Speicher gehalten
4. **Rate Limiting**: GitHub kann Anfragen limitieren

## 🔮 Zukünftige Verbesserungen

- [ ] Datenbank-Integration für historische Daten
- [ ] Charts und Visualisierungen hinzufügen
- [ ] Export-Funktionalität (Excel, PDF, CSV)
- [ ] Filtern und Suchen nach Ländern
- [ ] Push-Benachrichtigungen für Updates
- [ ] REST API bereitstellen
- [ ] Docker-Container
- [ ] Kubernetes-Deployment
- [ ] Unit-Tests erweitern
- [ ] Integration-Tests hinzufügen

## 📝 Entwicklerhinweise

### Lokale Entwicklung

```bash
# Projekt starten
./mvnw spring-boot:run

# Mit Hot-Reload (Spring DevTools)
# Änderungen werden automatisch übernommen
```

### Debugging

- Logs in `application.properties` aktivieren
- Verwenden Sie Postman für API-Tests
- Browser DevTools für Frontend-Debugging

## 📄 Lizenz

Dieses Projekt ist für Bildungszwecke erstellt worden. Die COVID-19-Daten stammen aus dem öffentlichen JHU CSSE Repository.

## 🌍 Datenquelle

Daten werden bereitgestellt von:
- **Johns Hopkins Center for Systems Science and Engineering (JHU CSSE)**
- GitHub Repository: [CSSEGISandData/COVID-19](https://github.com/CSSEGISandData/COVID-19)

## 👥 Beitragen

Beiträge sind willkommen! Bitte:
1. Forken Sie das Repository
2. Erstellen Sie einen Feature-Branch
3. Committen Sie Ihre Änderungen
4. Erstellen Sie einen Pull Request
