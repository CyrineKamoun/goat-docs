---
sidebar_position: 20
---

# Basic Styling

Wenn Sie eine neue Layer zu Ihrem Projekt hinzufügen, wird ihr ein Standardstil zugewiesen, welche je nach Datensatz unterschiedlich sein kann. Durch die Anpassung der Optionen im Menü <code>Layer Style<img src={require('/img/map/styling/styling_icon.webp').default} alt="Styling Icon" style={{ maxHeight: "15px", maxWidth: "15px", objectFit: "cover"}}/></code> können Sie die Darstellung des Layers anpassen und **ansprechende Karten** erstellen. Die verfügbaren Gestaltungsoptionen hängen von der Art der in einer Layer enthaltenen Daten ab, d. h. davon, ob es sich um Punkte, Linien oder Polygone handelt. Dabei können mehrere visuelle Aspekte wie **Farben**, **Striche** und **Optionen** angepasst werden.

## Farbeinstellungen

### Füllfarbe

Die Füllfarbe wird verwendet, um das **Innere** von **Punkt- oder Polygon-Features** auf einer Karte darzustellen. Die Füllfarbe ist ein Aspekt der Kartographie und der GIS-Visualisierung, da sie zur besseren Lesbarkeit der Karte beiträgt. Der [Color Picker](#color-picker--preset-colors) bietet verschiedene Optionen, um die Farben Ihrer Wahl auszuwählen.

<div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center'}}>

  <img src={require('/img/map/styling/fill_color.gif').default} alt="Fill-Stroke Color" style={{ maxHeight: "auto", maxWidth: "auto", objectFit: "cover"}}/>

</div> 

#### Deckkraft

Um die Deckkraft Ihrer Layerstile für die Füllfarbe anzupassen, ändern Sie die Deckkraft einfach auf einen beliebigen **Wert zwischen 0 und 1**. Mit dieser numerischen Skala können Sie genau den gewünschten Grad der Deckkraft festlegen, wobei **0 transparent** und **1 undurchsichtig** ist. Stellen Sie die Deckkraft nach Ihren Wünschen ein, indem Sie entweder den Schieberegler verwenden oder den genauen Wert direkt in das Textfeld eingeben.

<div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center'}}>

  <img src={require('/img/map/styling/opacity.gif').default} alt="Opacity" style={{ maxHeight: "auto", maxWidth: "auto", objectFit: "cover"}}/>

</div> 


### Strichfarbe

Ähnlich wie die Füllfarbe kann auch die Strichfarbe eingestellt werden. Die Strichfarbe bezieht sich auf die Farbe, die auf die **Außenlinien oder Kanten** von Kartenmerkmalen wie Polygonen, Linien und Punkten angewendet wird. Sie wird verwendet, um die Kanten von räumlichen Elementen abzugrenzen, sie voneinander zu unterscheiden und ihre Sichtbarkeit auf der Karte zu verbessern. Der [Color Picker](#color-picker--preset-colors) bietet verschiedene Optionen, um die Farben Ihrer Wahl auszuwählen.


### Farbwähler & voreingestellte Farben

Wann immer Sie eine Farbe ändern möchten, sei es **Füllfarbe** oder **Strichfarbe**, öffnet sich das Farbmenü. Sie können die Farben entweder über den <code>Farbpicker</code> einstellen, indem Sie den Picker im Farbfeld **bewegen** oder **hex-Code** oder **RGB-Werte** definieren, oder Sie können eine der Farben auswählen, die wir in den <code>Voreinstellungsfarben</code> bereitstellen.

<div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center'}}>

  <img src={require('/img/map/styling/color_picker.gif').default} alt="Color Picker" style={{ maxHeight: "400px", maxWidth: "400px", objectFit: "cover"}}/>

</div> 


## Benutzerdefinierte Icons

Für Punktlayer können benutzerdefinierte Marker für die Visualisierung verwendet werden. Dazu kann der Marker aus einer **Icon**-Liste ausgewählt werden. Die Markergröße kann über den Schieberegler eingestellt werden.

<div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center'}}>

  <img src={require('/img/map/styling/marker.gif').default} alt="Marker" style={{ maxHeight: "300px", maxWidth: "300px", objectFit: "cover"}}/>

</div> 

## Breite & Radius

## Strichbreite

Neben der Farbe kann auch die **Strichstärke** der Striche für **Linienlayern** definiert werden. Passen Sie die Strichstärke nach Ihren Wünschen an, indem Sie entweder den Schieberegler für die Strichstärke verwenden oder die genaue Größe direkt in das dafür vorgesehene Textfeld eingeben.

<div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center'}}>

  <img src={require('/img/map/styling/stroke_width.png').default} alt="Stroke Width" style={{ maxHeight: "300px", maxWidth: "300px", objectFit: "cover"}}/>

</div> 


### Radius

Bei **Punktdatensätzen** kann der **Radius** angepasst werden. Daher können Sie entweder den Radius-Schieberegler verwenden, um schrittweise Änderungen vorzunehmen, oder die gewünschte Radiusgröße direkt in das Textfeld eingeben, um eine präzise Steuerung zu ermöglichen.

<div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center'}}>

  <img src={require('/img/map/styling/radius.png').default} alt="Radius" style={{ maxHeight: "300px", maxWidth: "300px", objectFit: "cover"}}/>

</div> 


## Standardeinstellungen 

Durch Klicken auf die drei Punkte <img src={require('/img/map/filter/3dots.png').default} alt="Options" style={{ maxHeight: "25px", maxWidth: "25px", objectFit: "cover"}}/>,  öffnen sich weitere Einstellungen. 

<div style={{ display: 'flex', flexDirection: 'column', alignItems: 'center'}}>

  <img src={require('/img/map/styling/default.png').default} alt="Default Settings" style={{ maxHeight: "300px", maxWidth: "300px", objectFit: "cover"}}/>

</div> 

Wenn Sie <code>Speichern als Standard</code> wählen, werden die aktuellen Stileinstellungen an den Datensatz angehängt. Wann immer Sie diesen Datensatz zu einem Projekt hinzufügen, wird dieser Standardstil verwendet (*Hinweis: bestehende Projekte, in denen dieser Datensatz angezeigt wird, sind davon nicht betroffen*). 

Wenn Sie auf <code>Rücksetzen</code> klicken, können Sie die aktuellen Stileinstellungen des Layers im Projekt wieder auf die Standardwerte zurücksetzen. 


:::tip TIPP
Interessieren Sie sich für **Smart Styling** Optionen? Schauen Sie sich unser  [Attribute-based Styling](../layer_style/attribute_based_styling) an.
:::