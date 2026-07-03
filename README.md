# FIFO Controle

## Bestanden

Upload naar GitHub Pages:

```text
index.html
products.csv
config.js
README.md
```

## Microsoft Forms

Gebruik formulier **FIFO Controle** met precies deze vragen:

1. Shiftleider - korte tekst
2. Datum+tijd - korte tekst
3. Zuivel - lange tekst
4. Kaas/Vleeswaren - lange tekst
5. Vlees/Vis/Kip/Vega - lange tekst
6. Maaltijden/Sappen - lange tekst
7. Panklaar - lange tekst

Gebruik bij **Get pre-filled URL** deze placeholders:

```text
Shiftleider: __SHIFTLEIDER__
Datum+tijd: __DATUMTIJD__
Zuivel: __ZUIVEL__
Kaas/Vleeswaren: __KAAS_VLEESWAREN__
Vlees/Vis/Kip/Vega: __VLEES_VIS_KIP_VEGA__
Maaltijden/Sappen: __MAALTIJDEN_SAPPEN__
Panklaar: __PANKLAAR__
```

De afdelingkolommen in Excel worden gevuld als:

```text
4/4 (106375,11956,815633,540178)
```

Dat betekent: 4 correct van 4 geselecteerd. Alleen de correct gecontroleerde Nasa-nummers staan tussen haakjes.

## products.csv

De productlijst heeft alleen deze kolommen:

```csv
Nasa;Productnaam;Afdeling;Subafdeling;Actief
```

Gebruik `Actief = Ja` als het product gekozen mag worden. Gebruik `Actief = Nee` als het product in de lijst moet blijven staan maar niet gekozen mag worden.

De meest voorkomende Vega-producten zijn nu actief gezet.

## Individueel Nasa-nummer aanpassen

Per productkaart staat **Nasa aanpassen**. Daarmee kun je tijdens de controle één Nasa-nummer aanpassen. Als het nieuwe nummer in `products.csv` staat, wordt de productnaam automatisch bijgewerkt.

## GitHub Pages

1. Maak of open je GitHub repository.
2. Upload `index.html`, `products.csv`, `config.js` en `README.md` in de root.
3. Ga naar **Settings > Pages**.
4. Kies **Deploy from a branch**.
5. Kies branch **main** en folder **/ root**.
6. Klik **Save**.

De link verschijnt daarna bij **Settings > Pages**, meestal als:

```text
https://jouwnaam.github.io/fifo-controle/
```

Gebruik die link voor de winkel-QR.

## Lokaal testen

Gebruik een lokale webserver als je wilt testen of `products.csv` echt wordt gelezen:

```bash
cd map-met-de-bestanden
python3 -m http.server 8080
```

Open daarna:

```text
http://localhost:8080/
```
