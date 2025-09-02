# 🌍 Geoinformations-Seite - GND Community Space

## Übersicht
Die Geoinformations-Seite (`gndcs-geoinfo.html`) ist ein Addon für die GND Community Space Anwendung, das es Benutzern ermöglicht, geografische Informationen zu beliebigen GND-Entitäten hinzuzufügen. Es unterstützt m:n-Beziehungen, bei denen mehrere GND-Entitäten mit einer Geoinformation verknüpft werden können und umgekehrt.

## 🎯 Hauptfunktionalitäten

### 1. GND-Entitäten-Verwaltung
- **Verknüpfte GND-Entitäten**: Anzeige aller mit der Geoinformation verknüpften GND-Entitäten
- **Entitäten hinzufügen**: Suchfunktion für GND-Nummern oder Entitätsnamen
- **Entitäten entfernen**: Einzelne Entitäten aus der Verknüpfung entfernen
- **Automatische Vorbefüllung**: GND-Nummer wird automatisch gesetzt, wenn von `gndcs-edit.html` navigiert wird

### 2. Koordinateneingabe
#### Strukturierte Eingabe
- **Punktkoordinaten**: Einzelne Koordinatenpaare (Breiten- und Längengrad)
- **Linien**: Mehrere Punkte für Flussläufe, Grenzen, Verkehrswege
- **Flächen (Multipolygon)**: Mindestens 3 Punkte für Gebietsumrisse
- **Rahmenkoordinaten (Bounding Box)**: 4 Werte für grobe Bereichsabgrenzung

#### Textstring-Eingabe
- **Unterstützte Formate**: GeoJSON, WKT (Well-Known Text), GML, KML
- **Automatische Validierung**: Parsing und Überprüfung der eingegebenen Koordinaten
- **Formatbeispiele**: Platzhalter mit Beispielen für jeden Koordinatentyp

### 3. Interaktive Karte
- **Eingebettete Leaflet-Karte**: Direkt in das Formular integriert (kein Popup)
- **Polygonsymbol-Steuerung**: Kartensteuerung unterhalb der Zoom-Controls
- **Klick-Modus**: Koordinaten durch Klicken auf die Karte setzen
- **Verschiebbare Marker**: Alle Marker können mit der Maus verschoben werden
- **Automatische Synchronisation**: Karte aktualisiert sich bei Änderungen der Eingabefelder

### 4. Zusatzinformationen
- **Art der Relation**: Wertliste je nach Koordinatentyp
  - Punkte: Zentrum, Verwaltungssitz, Historisches Zentrum, Geografischer Mittelpunkt
  - Linien: Flusslauf, Grenzlinie, Verkehrsweg, Historische Route
  - Flächen: Umriss, Administrative Grenze, Historische Grenze, Naturraum
  - Bounding Box: Rahmenkoordinaten, Grobbereich, Näherungsbereich

- **Koordinatendatierung**:
  - Anfangsdatum (YYYY-MM-DD) mit ungefährer Angabe
  - Enddatum (YYYY-MM-DD) mit ungefährer Angabe
  - Verbale Datierung (Freitext)

- **Metadaten**:
  - Quelle (Freitext)
  - Bemerkungen (Freitext)

## 🔧 Technische Implementierung

### JavaScript-Funktionalitäten
- **Event-Handling**: Automatische Updates bei Eingabeänderungen
- **Map-Integration**: Leaflet.js für interaktive Kartendarstellung
- **Dynamische Formulare**: Anpassung der Eingabefelder je nach Koordinatentyp
- **Validierung**: Überprüfung der eingegebenen Daten

## 📋 Anforderungen

1. **m:n-Beziehungen**: Mehrere GND-Entitäten können mit einer Geoinformation verknüpft werden
2. **Koordinatentypen**: Unterstützung für Punkte, Linien, Flächen und Bounding Boxes
3. **Textstring-Eingabe**: Verschiedene Koordinatenformate (GeoJSON, WKT, GML, KML)
4. **GND-Nummer-Vorbefüllung**: Automatische Auswahl bei Navigation von der Bearbeitungsseite
5. **Kartenintegration**: 
   - Kein Popup, sondern direkte Einbettung in das Formular
   - Polygonsymbol als Kartensteuerung statt "Klick-Modus"-Button
   - Verschiebbare Marker für alle Koordinatentypen
6. Standardmäßig geöffnete erste beiden Sektionen

## 🚀 Verwendung

### Grundlegende Workflow
1. **Entität auswählen**: GND-Nummer eingeben oder von Bearbeitungsseite navigieren
2. **Koordinatentyp wählen**: Punkt, Linie, Polygon oder Bounding Box
3. **Eingabemodus wählen**: Strukturierte Eingabe/Karteneingabe oder Textstring
4. **Koordinaten eingeben**: 
   - Manuell in die Eingabefelder
   - Durch Klicken auf die Karte (Polygonsymbol aktivieren)
   - Als Textstring in verschiedenen Formaten
5. **Zusatzinformationen ergänzen**: Relationstyp, Datierung, Quelle, Bemerkungen
6. **Speichern**: Geoinformation wird mit allen verknüpften Entitäten gespeichert

### Karteneingabe
- **Polygonsymbol klicken**: Aktiviert den Klick-Modus
- **Auf Karte klicken**: Setzt Koordinaten je nach gewähltem Typ
- **Marker verschieben**: Ziehen der Marker mit der Maus aktualisiert automatisch die Eingabefelder
- **Geometrien**: Linien und Polygone werden automatisch neu gezeichnet

## 🔗 Integration

### Navigation
- **Von gndcs-edit.html**: Automatische Übertragung der GND-Nummer
- **Breadcrumb-Navigation**: Klare Orientierung in der Anwendung
- **Zurück-Navigation**: Logo führt zur Startseite

### Datenverwaltung
- **Verknüpfte Entitäten**: Anzeige und Verwaltung der m:n-Beziehungen
- **Bestehende Geoinformationen**: Übersicht über bereits gespeicherte Daten
- **Bearbeitung und Löschung**: Funktionen für bestehende Einträge

## 📱 Responsive Design

### Layout-Anpassungen
- **Flexible Grids**: Anpassung an verschiedene Bildschirmgrößen
- **Mobile Optimierung**: Touch-freundliche Bedienung
- **Kartenintegration**: Responsive Kartendarstellung

## 🔒 Validierung und Fehlerbehandlung

### Eingabevalidierung
- **Koordinatenformat**: Überprüfung der eingegebenen Werte
- **Pflichtfelder**: Mindestanforderungen für verschiedene Koordinatentypen
- **Fehlermeldungen**: Benutzerfreundliche Hinweise bei ungültigen Eingaben

### Datenintegrität
- **Duplikatprüfung**: Verhindert doppelte Entitätsverknüpfungen
- **Formatkonsistenz**: Sicherstellung der Datenqualität
- **Automatische Updates**: Synchronisation zwischen Eingabefeldern und Karte

## 🎨 Benutzerfreundlichkeit

### Intuitive Bedienung
- **Visuelle Rückmeldungen**: Klare Anzeige des aktuellen Zustands
- **Hilfetexte**: Detaillierte Anleitungen für alle Funktionen
- **Konsistente Bedienung**: Einheitliche Interaktionsmuster

### Workflow-Optimierung
- **Standardmäßige Einstellungen**: Reduzierung der notwendigen Klicks
- **Automatische Updates**: Minimierung manueller Aktualisierungen
- **Kontextsensitive Hilfe**: Relevante Informationen je nach gewähltem Modus

## 🔮 Erweiterungsmöglichkeiten
- **API-Integration**: Anbindung an externe Geodatendienste

---

*Diese Dokumentation beschreibt die aktuelle Implementierung der Geoinformations-Seite basierend auf den Anforderungen aus unseren Gesprächen und der technischen Umsetzung.*
