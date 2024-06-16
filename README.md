# FHIR to Proprietary API Facade

#### Diese Anwendung implementiert eine Fassade, die einen Endpunkt zur Erstellung eines neuen Patientenstammdatensatzes gemäß der HL7 FHIR R4 Spezifikation bereitstellt. Bei der Anlieferung von Patientenstammdaten werden bestimmte Eigenschaften extrahiert und an eine proprietäre REST-API weitergeleitet, um einen Patienteneintrag in einem externen System anzulegen. Abhängig von der Antwort des externen Systems gibt die Fassade eine entsprechende Rückmeldung an den FHIR-Client.

### Installation

## Voraussetzungen

    - Java Development Kit (JDK) 17 oder höher
    - Maven
    - Mockoon oder Postman (für die Simulation der proprietären API)

1. Repository klonen
    Klonen Sie das Repository auf Ihren lokalen Rechner:
        git clone <repository-url>
2. In das Projektverzeichnis wechseln
    Wechseln Sie in das Verzeichnis des geklonten Projekts:
        cd <project-directory>
3. Projekt bauen
    Bauen Sie das Projekt mit Maven:
        Run `mvn clean install`
4. Anwendung starten
    Starten Sie die Spring Boot Anwendung:
        `mvn spring-boot:run`

## Nutzung

## Mockoon zur Simulation der proprietären API
Um die proprietäre API zu simulieren, verwenden wir Mockoon. Folgen Sie diesen Schritten:

1. Mockoon starten:
    Laden Sie Mockoon herunter und installieren Sie es von mockoon.com
    Starten Sie Mockoon und importieren Sie die bereitgestellte Datei `Test-Patient-API_Dev.json`

2. Mock-Server starten:
    Starten Sie den Mock-Server auf Port 3001.

## Postman zur API-Testung
Verwenden Sie Postman, um Ihre API-Endpunkte zu testen. Folgen Sie diesen Schritten:

1. Postman öffnen:
    Starten Sie Postman nach der Installation.

2. Neue Anfrage erstellen:
    Klicken Sie auf `New` und wählen Sie `Request` aus.
    Geben Sie der Anfrage einen Namen, z.B. "Create Patient".
    Erstellen Sie eine neue Sammlung (Collection) oder wählen Sie eine bestehende aus, um Ihre Anfrage zu speichern.

3. Anfrage konfigurieren:
    Wählen Sie den HTTP-Methodentyp `POST` aus.
    Geben Sie die URL Ihres Endpunkts ein: `http://localhost:8080/fhir/Patient`.
    Stellen Sie sicher, dass der Endpunkt Ihrer laufenden Spring Boot Anwendung entspricht.

4. Header hinzufügen:
    Gehen Sie zum Tab `Headers`.
    Fügen Sie einen neuen Header hinzu: `Content-Type` mit dem Wert `application/json`.

5. Wechseln Sie zum Tab Body.
    Wählen Sie die Option raw aus.
    Stellen Sie sicher, dass der Datentyp auf JSON gesetzt ist.
    Fügen Sie den Inhalt Ihrer Beispiel-FHIR-Ressource `Beispiel-FHIR-Ressource-Patient.json` in das Textfeld ein als Anfragekörper.

6. Anfrage senden:
    Klicken Sie auf `Send`, um die Anfrage zu senden. Postman wird die Anfrage an Ihren Endpunkt schicken und die Antwort anzeigen.

7. Überprüfen der Antwort:
    Postman zeigt die Antwort des Servers im unteren Bereich des Fensters an. Überprüfen Sie die folgenden Punkte:

    Statuscode: Stellen Sie sicher, dass Sie den erwarteten Statuscode zurückerhalten. Bei erfolgreicher Erstellung sollte dies `201 Created` sein.
    Antwortinhalt: Überprüfen Sie den Inhalt der Antwortnachricht, um sicherzustellen, dass die Patientenerstellung erfolgreich war.

## Beispiel-FHIR-Ressource
Verwenden Sie die Beispiel-FHIR-Ressource `Beispiel-FHIR-Ressource-Patient.json` als Anfragekörper.


# Architektur und Codeerläuterung

## Projektstruktur

Das Projekt ist in mehrere Pakete unterteilt, um eine klare Trennung der Verantwortlichkeiten zu gewährleisten:

    controller: Enthält den FHIR Controller.
    service: Beinhaltet die Logik zur Verarbeitung der FHIR-Ressourcen.

## Fehlerbehandlung
Die Anwendung behandelt Fehlerfälle, indem sie Statuscodes interpretiert und entsprechende Nachrichten zurückgibt:

    Erfolgreiche Anlage: Statuscode 201
    Fehlerhafte Anlage: Statuscode 500 oder andere Fehlercodes ≥ 400

