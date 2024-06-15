# PatientMasterData-HL7-FHIR
Eine Anwendung, die einen Endpunkt für die Erstellung eines neuen Patientenstammdatensatzes gemäß der Spezifikation von HL7 FHIR R4 bereitstellt

## Installation
1. Clone the repository
2. Navigate to the project directory
3. Run `mvn clean install`
4. Start the application using `mvn spring-boot:run`

## Nutzung
1. Starten Sie Mockoon und importieren Sie die `Test-Patient-API_Dev.json`-Datei.
2. Starten Sie den Mock-Server auf Port 3001.
3. Senden Sie eine POST-Anfrage an `http://localhost:8080/Patient` mit der Beispiel-FHIR-Ressource.

## Beispiel-FHIR-Ressource
Verwenden Sie die Beispiel-FHIR-Ressource `Beispiel-FHIR-Ressource-Patient.json` als Anfragekörper.

## Entwicklermodus
Um die Anwendung zu entwickeln, folgen Sie den üblichen Schritten zur Java/Spring Boot Entwicklung. Stellen Sie sicher, dass Sie sinnvolle Commits und Commit-Nachrichten verwenden.
