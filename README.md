# Flutter Testprojekt - T5 Zugriff auf Dateisystem

Dieses Projekt wurde als Testprojekt zur Evaluierung der Thesis entwickelt.

## Anforderung

**T5 Zugriff auf Dateisystem**  
Nutzer müssen in der Lage sein, Dateien aus dem Dateisystem auszuwählen.  
**Priorität:** **MUSS**

## Wie wird diese Anforderung in der App evaluiert?

- Die App bietet eine Benutzeroberfläche mit folgenden Funktionen:
  - Auswahl einer oder mehrerer Dateien aus dem Dateisystem.
  - Auswahl eines Verzeichnisses.
  - Speicherung von Dateien mit einer "Speichern unter"-Funktion.
- Nutzer können Dateitypen filtern und die Auswahl auf spezifische Formate beschränken.

## Technische Details

### Genutzte Bibliothek

- **Third-Party-Lösung:** [file_picker](https://pub.dev/packages/file_picker)

### Hauptfunktionen der Bibliothek

1. **Dateiauswahl:**
   - Unterstützt die Auswahl einzelner oder mehrerer Dateien.
   - Ermöglicht das Filtern nach spezifischen Dateitypen (z. B. `.jpg`, `.pdf`).
2. **Verzeichnisauswahl:**
   - Nutzer können ein Verzeichnis aus dem Dateisystem auswählen.
3. **Speichern von Dateien:**
   - "Speichern unter"-Funktion, um Dateien an einem gewünschten Speicherort abzulegen.
4. **Plattformübergreifende Unterstützung:**
   - Funktioniert auf Android, iOS, Web und Desktop mit konsistenter API.
5. **Optionen für Dateifilterung:**
   - Einschränkung auf bestimmte Dateiformate oder Erweiterungen (z. B. `.doc`, `.png`).

### Funktionsweise der Bibliothek

- **Android:**
  - Verwendet das `Intent`-System, um eine native Dateiauswahl bereitzustellen.
- **iOS:**
  - Nutzt die `UIDocumentPickerViewController` API für die native Dateiauswahl.

### Beispielcode

```dart
void _pickFiles() async {
  List<PlatformFile>? paths = (await FilePicker.platform.pickFiles(
    allowMultiple: true,
    type: FileType.custom,
    allowedExtensions: ['jpg', 'png', 'pdf'],
  ))
      ?.files;

  if (paths != null) {
    print("Ausgewählte Dateien: ${paths.map((e) => e.name).toList()}");
  }
}
```

### Features der App

- **UI-Komponenten:**
  - Buttons für die Dateiauswahl, Verzeichnisauswahl und Dateispeicherung.
  - Anzeige der ausgewählten Dateien und Verzeichnisse.
- **Interaktion mit der Bibliothek:**
  - Nutzung der `file_picker`-API für plattformübergreifende Dateiverwaltung.