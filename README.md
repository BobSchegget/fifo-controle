# FIFO Controle - productieversie

Deze map bevat de bestanden voor GitHub Pages:

- `index.html` - de webapp
- `products.csv` - de beheerlijst met Nasa-nummers/producten/afdelingen
- `config.js` - de Microsoft Forms prefilled link

## Microsoft Forms

Gebruik je bestaande formulier **FIFO Controle** met deze vragen:

1. Shiftleider - korte tekst
2. Datum+tijd - korte tekst
3. Zuivel - lange tekst
4. Kaas/Vleeswaren - lange tekst
5. Vlees/Vis/Kip/Vega - lange tekst
6. Maaltijden/Sappen - lange tekst
7. Panklaar - lange tekst

Maak een prefilled link via `... > Get pre-filled URL` en vul de velden zo in:

- Shiftleider: `__SHIFTLEIDER__`
- Datum+tijd: `__DATUMTIJD__`
- Zuivel: `__ZUIVEL__`
- Kaas/Vleeswaren: `__KAAS_VLEESWAREN__`
- Vlees/Vis/Kip/Vega: `__VLEES_VIS_KIP_VEGA__`
- Maaltijden/Sappen: `__MAALTIJDEN_SAPPEN__`
- Panklaar: `__PANKLAAR__`

Plak daarna de volledige prefilled link in `config.js` bij `window.FIFO_FORMS_URL_TEMPLATE`.

## Statistieken in Excel

Met alleen de 7 huidige velden schrijft de app de aantallen per afdeling bovenaan elk tekstblok:

`Zuivel: Goed 3, Fout 1, Niet gevuld 0, Open 0`

Wil je later makkelijk draaitabellen maken zonder tekstsplitsing, voeg dan extra korte tekstvelden toe aan Forms. De app ondersteunt deze placeholders al:

- `__ZUIVEL_CORRECT__`, `__ZUIVEL_FOUT__`, `__ZUIVEL_NIET_GEVULD__`
- `__KAAS_VLEESWAREN_CORRECT__`, `__KAAS_VLEESWAREN_FOUT__`, `__KAAS_VLEESWAREN_NIET_GEVULD__`
- `__VLEES_VIS_KIP_VEGA_CORRECT__`, `__VLEES_VIS_KIP_VEGA_FOUT__`, `__VLEES_VIS_KIP_VEGA_NIET_GEVULD__`
- `__MAALTIJDEN_SAPPEN_CORRECT__`, `__MAALTIJDEN_SAPPEN_FOUT__`, `__MAALTIJDEN_SAPPEN_NIET_GEVULD__`
- `__PANKLAAR_CORRECT__`, `__PANKLAAR_FOUT__`, `__PANKLAAR_NIET_GEVULD__`

## Producten beheren

Pas `products.csv` aan. Gebruik puntkomma's:

```csv
Nasa;Productnaam;Afdeling;Subafdeling;Actief;Gewicht;AanwezigInPakbonnen;OntbreektInPakbonnen;BronPakbonnen;Opmerking
106375;ah bio halfv melk 1 lt;Zuivel;Zuivel;Ja;6;6;0;Pakbon,Pakbon2,Pakbon3,Pakbon5,Pakbon6,Pakbon7;strikt pakbonfilter
```

Gebruik deze afdelingen exact:

- Zuivel
- Kaas/Vleeswaren
- Vlees/Vis/Kip/Vega
- Maaltijden/Sappen
- Panklaar

Gebruik deze subafdelingen exact:

- Zuivel
- Kaas/Vleeswaren
- Vis
- Vlees
- Kip
- Vega
- Maaltijden
- Sappen
- Panklaar

`Actief = Ja` betekent: mag gekozen worden. `Actief = Nee` betekent: bewaren, maar niet kiezen.

De app kiest per datum deterministisch dezelfde producten. Pas `products.csv` daarom liever niet midden op de dag aan.

## GitHub Pages

Upload `index.html`, `products.csv`, `config.js` en `README.md` naar je repository. Zet daarna GitHub Pages aan via:

Settings > Pages > Deploy from a branch > main > / root > Save

De winkel-QR verwijst naar de GitHub Pages URL, bijvoorbeeld:

`https://jouwnaam.github.io/fifo-controle/`

## Lokaal testen en products.csv

Als je dubbelklikt op `index.html`, opent de browser de app via `file://`. In die modus mag JavaScript meestal geen los bestand zoals `products.csv` lezen. De app gebruikt dan de ingebouwde reserve-productlijst.

Wil je lokaal testen of wijzigingen in `products.csv` echt worden gelezen, host de map lokaal:

```bash
cd map-met-de-bestanden
python3 -m http.server 8080
```

Open daarna:

```text
http://localhost:8080/
```

Op GitHub Pages wordt `products.csv` wel normaal geladen. De app haalt `products.csv` telkens met cache-bypass op, zodat wijzigingen na upload snel zichtbaar zijn.

Als je op dezelfde dag al eerder hebt getest, kan je browser nog een dagselectie in lokale opslag hebben. Deze versie gebruikt een nieuwe opslagversie, zodat oude testselecties niet worden meegenomen.


## Verzenden

De knop **Opslaan FIFO Controle** opent niet meteen Microsoft Forms. Eerst verschijnt een tussenpagina met samenvatting. Daar kun je:

- doorgaan naar Microsoft Forms;
- terug om iets aan te passen;
- opnieuw proberen als Forms niet opent.

In Microsoft Forms moet de shiftleider daarna nog zelf op **Verzenden** klikken.


## Individueel Nasa-nummer aanpassen

Per productkaart staat een knop **Nasa aanpassen**.

Gebruik:
1. Klik bij het product op **Nasa aanpassen**.
2. Vul het nieuwe Nasa-nummer in.
3. Klik **Opslaan Nasa**.

Als het Nasa-nummer voorkomt in `products.csv`, wordt de productnaam automatisch aangepast.
Als het Nasa-nummer niet voorkomt, blijft de controle bruikbaar en wordt de productnaam `Handmatig ingevoerd Nasa-nummer`.

In Microsoft Forms komt dit terug als:

```text
123456 (aangepast van 106375)
```

De oorspronkelijke productnaam wordt ook in de afdelingstekst vermeld.
