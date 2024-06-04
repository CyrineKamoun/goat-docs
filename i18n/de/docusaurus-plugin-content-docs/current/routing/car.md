---
sidebar_position: 4

---

# Auto

Das **Car Routing** wird für alle Analysen in GOAT verwendet, die Autofahrten enthalten.


## 1. Ziele

Car Routing wird für viele Indikatoren in GOAT verwendet, wie z.B. [Catchment Areas](../toolbox/accessibility_indicators/catchments) und [Heatmaps](../toolbox/accessibility_indicators/connectivity). 

Da GOAT auch die Erstellung von [Scenarios on the Paths Network](../scenarios/ways) erlaubt, wird ein **angepasster Routing-Algorithmus** benötigt, der auch die Änderungen des Szenarios in den Erreichbarkeitsanalysen widerspiegelt. Für den Verkehrsträger Auto werden dabei **nur Wege berücksichtigt, die für das Fahren geeignet sind**.

## 2. Daten

### Routing Netzwerk

Daten von der  **[Overture Maps Foundation](https://overturemaps.org/)**  werden in GOAT als Routing-Netzwerk verwendet. Dieses beschreibt die Verkehrsinfrastruktur mit **Kanten** (für jeden durchgehenden Weg, der nicht von einem anderen halbiert wird) und **Knoten** (für jeden Punkt, an dem sich zwei verschiedene Wege kreuzen), die reale Netzwerke darstellen.


## 3. Technische Details

### Datenvorverarbeitung

Die folgenden Schritte werden an den Daten durchgeführt, um ein **schnelles** und **genaues** Routing für Autos zu ermöglichen:

1.  **Attribut-Parsing:** Kategorisierung der Attribute von Kanten (Straßen `class` und `surface`).
2.  **Geospatial Indexing:**  Nutzung des  **[Uber's H3 grid-based](../further_reading/glossary#h3-grid)**  Indexing für effizientes Routing.
3.  **Extrahieren von Beschränkungen:** Identifizieren von Einweg-Zugangsbeschränkungen zusätzlich zu den Geschwindigkeitsbegrenzungen für beide Richtungen der Kante (`maxspeed_forward` and `maxspeed_backward`).

### Routing-Prozess-Schritte

#### Extraktion von Teilnetzen

1.  **Pufferregion:** Basierend auf der Herkunft des Nutzers, der Reisezeit und der maximal möglichen Fahrgeschwindigkeit.
2.  **Kantenfilterung:** Es werden nur die für die Fahrt relevanten Kanten berücksichtigt.

Für das Auto-Routing werden die Kanten der folgenden Straßenklassen berücksichtigt:

`motorway`, `primary`, `secondary`, `tertiary`, `residential`, `living_street`, `trunk`, `parking_aisle`, `driveway`, `alley` and `track`.
    
Weitere Informationen zu dieser Klassifizierung finden Sie im [Overture Wiki](https://docs.overturemaps.org/schema/reference/transportation/segment).

#### Erstellung künstlicher Kanten

Für alle Kanten im Teilnetz wird ein Kostenwert (dargestellt als Zeit) auf der Grundlage von Weglänge und Fahrgeschwindigkeit berechnet.

Kostenfunktion für Auto:

`cost_forward = length / maxspeed_forward`

`cost_reverse = length / maxspeed_backward`

Bei der Berechnung von `cost_reverse` wird eine Kante, die eine Einbahnstraßenbeschränkung enthält und daher nicht in umgekehrter Richtung befahren werden darf, mit sehr hohen Kosten belegt. Dadurch wird verhindert, dass der Routing-Algorithmus solche Kanten für das Routing in umgekehrter Richtung in Betracht zieht.


:::info Note
Der Routing-Algorithmus von GOAT berücksichtigt derzeit keine **historischen Verkehrsmuster** für das Routing von Fahrzeugen. Diese Funktion befindet sich derzeit in der Entwicklung. 🧑🏻‍💻
:::

#### Netzwerkausbreitung

Um den kürzesten Weg vom Ausgangspunkt zu verschiedenen Zielen zu berechnen, wird eine benutzerdefinierte Implementierung des bekannten [Dijkstra Algorithm](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) verwendet.


<div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center' }}>
  <img src={require('/img/routing/walk/dijkstra.gif').default}  alt="Dijkstra Algorithm" style={{ width: "auto", height: "auto", objectFit: "cover"}}/>
<p style={{ textAlign: 'center' }}>GIF: <a href="https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm">Dijkstra Algorithm</a></p>
</div>

Die Implementierung hat eine Zeitkomplexität von *O(ElogV)*, ist in **Python** geschrieben und verwendet den Just-in-Time-Compiler **Numba**.