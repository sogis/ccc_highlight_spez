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

## Entwurf Darstellungs-Definition

Die JSON-Spezifikationen aus [CCC-Service Spezifikation Version 1.0](https://github.com/sogis/ccc-service/blob/master/docs/res/Spezifikation_CCC_Schnittstelle_V1.0.pdf) werden wie folgt ergänzt: 

| Attribut | Json-Typ | Nullable |
|---|---|---|
| style | Objekt | J |


```json
{
    "method": "...",
    [...]
    "style": {
        "circleBorder": 2,
        "circleRadius": 10,
        "fillColor": [255, 255, 64, 0.33],
        "strokeColor": [255, 128, 0, 1],
        "strokeDash": [],
        "strokeWidth": 2,
        "textFill": "black",
        "textStroke": "white"
    }
}
```
