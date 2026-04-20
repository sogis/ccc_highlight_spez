# Spezifikation Highlight Style CCC

## Idee
Damit kann ein Client die dynamisch gerenderten Symbole für die Selektionsanzeige und das Styling der Geometrien im CCC-Edit-Modus setzen.

In erster Priorität sind Geometrien, die mit der CCC-Methode `showGeoObject` erstellt werden, in diesem Style anzuzeigen. Wenn damit auch der Style von Geometrien `createGeoObject`, `editGeoObject`, usw. einfach anzupassen ist, so soll das auch umgesetzt werden.

## Konzept

Es wird keine eigene CCC-Nachricht dafür implementiert. Die CCC-Methoden `createGeoObject`, `editGeoObject`, `showGeoObject` werden um ein optionales JSON-Atrribut `style` ergänzt, das die Darstellung im Web GIS Client steuert.

|Methode|Richtung|Typ|Beschreibung|
|---|---|---|---|
|`createGeoObject`, `editGeoObject`, `showGeoObject`|F > K|RUN|Aufforderung an die Kartenapplikation, mit optionaler Darstellungsdefinition |

F: Fachapplikation

K: Kartenapplikation (Web GIS Client)

> [!IMPORTANT]
> Rückwärtskompatibilität muss gewährleistet sein. Fachapplikationen, die diese Methoden ohne `style`-Attribut verwenden, müssen weiterhin vom Web GIS Client verstanden werden. Als Style soll der heutige Default angewendet werden.

## Darstellungs-Definition

Die JSON-Spezifikationen aus [CCC-Service Spezifikation Version 1.0](https://github.com/sogis/ccc-service/blob/master/docs/res/Spezifikation_CCC_Schnittstelle_V1.0.pdf) werden wie folgt ergänzt: 

| Attribut | Json-Typ | Nullable |
|---|---|---|
| style | Objekt | J |


```json
{
    "method": "...",
    [...]
    "style": {
        "strokeColor": [255, 0, 0, 1],
        "strokeWidth": 2,
        "strokeDash": [],
        "fillColor": [255, 0, 9, 0.5],
        "circleRadius": 8,
        "vertexStrokeColor": [255, 0, 0, 1],
        "vertexFillColor": [255, 255, 255, 1]
    }

}
```

Beispiel für `strokeDash`: 
```
- - - - => [2, 2]
- . - . - => [2, 2, 1, 2, 2, 2, 1, 2, 2]
-- -- -- => [4, 2, 4, 2, 4] 
```

- Ungerade Elemente der Liste: Breite des Stirches
- Gerade Elemente der Liste:   Breite des Leerabstandes
