# ccc_highlight_spez

## Idee
Mit dieser Methode kann ein Client die dynamisch gerenderten Symbole für die Selektionsanzeige und das Styling der Geometrien im CCC-Edit-Modus setzen.

## Nachricht


|Methode|Richtung|Typ|Beschreibung|
|---|---|---|---|
|`setHighlightStyle`|F > K|RUN|Aufforderung an die Kartenapplikation, eine Darstellungsdefinition zu übernehmen|

F: Fachapplikation

K: Kartenapplikation (Web GIS Client)

## Entwurf: Umfang einer Darstellungs-Definition

```json
{
    "circleBorder": 2,
    "circleRadius": 10,
    "fillColor": [255, 255, 64, 0.33],
    "strokeColor": [255, 128, 0, 1],
    "strokeDash": [],
    "strokeWidth": 2,
    "textFill": "black",
    "textStroke": "white"
}
```
