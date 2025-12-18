# Applied Physics Walk Analysis

Tässä työssä analysoidaan Phyphox-sovelluksella mitattua puhelimen kiihtyvyys- ja GPS-dataa. Mittauksessa käytettiin Linear Acceleration- ja Location-sensoreita.

Työ on tehty OAMK:n Soveltava fysiikka ohjelmoinnissa -kurssin loppuprojektina. Analyysi on toteutettu Python-skriptinä Streamlit-kirjastolla.

![Applied Physics Walk Analysis Gif](https://github.com/user-attachments/assets/1de29586-95d1-42c9-b0ce-d0ccbb35d898)

## Menetelmä
- Kiihtyvyysdata suodatettiin kaistanpäästösuodattimella (noin 0.7–4 Hz)
- Askelmäärä määritettiin kahdella tavalla:
  1) Suodatetusta signaalista piikkien avulla
  2) Fourier-analyysin avulla tehospektrin päätaajuudesta
- Matka ja keskinopeus laskettiin GPS-datasta
- Askelpituus laskettiin jakamalla kuljettu matka askelmäärällä

## Visualisoinnit
- Suodatettu kiihtyvyysdata ja tunnistetut askeleet
- Tehospektritiheys (PSD)
- GPS-reitti kartalla

## Kiihtyvyyskomponentin valinta
Valitsin analyysiin komponentin `az`, koska siinä kävelyn jaksollinen liike erottui selkeimmin ja askelpiikit vastasivat parhaiten kävelyrytmiä verrattuna vaihtoehtoihin `ax`, `ay` ja `a_mag`.

## Data
Repo sisältää datatiedostot:
- data/Accelerometer.csv
- data/Location.csv

Sovellus lukee datan ensisijaisesti paikallisesta data/-kansiosta.
Jos sovellus ajetaan suoraan GitHub-URL:stä, data haetaan raw.githubusercontent.com-osoitteesta.

## Käynnistys (paikallinen)
Asenna riippuvuudet:
python3 -m pip install -r requirements.txt

Käynnistä:
python3 -m streamlit run app.py

## Käynnistys (URL-ajo)
Asenna: pip3 install streamlit numpy pandas scipy matplotlib folium streamlit-folium requests certifi

Aja terminaalissa:
```bash
streamlit run https://raw.githubusercontent.com/andytrix/applied-physics-walk-analysis/main/app.py
