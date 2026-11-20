# Machine-KI-Dashboard

Ein persönliches Python-Demoprojekt von Eyüp Cindioglu zur Visualisierung simulierter Maschinenmesswerte. Das Dashboard zeigt Temperatur und Vibration als Zeitreihen und markiert auffällige Messpunkte in Rot. Mit Dash und Plotly habe ich die Datenaufbereitung und die interaktive Darstellung zu einer lokal lauffähigen Demo verbunden.

![Vorschau des Dashboards mit Temperatur- und Vibrationsdiagramm](assets/dashboard_screenshot.png)

## Lokal starten

Voraussetzung ist Python 3.12 mit Git.

~~~bash
git clone https://github.com/Trayute/machine-ki-dashboard.git
cd machine-ki-dashboard
python -m venv .venv
~~~

Aktiviere die Umgebung mit `source .venv/bin/activate` (macOS/Linux) oder `.venv\Scripts\Activate.ps1` (Windows PowerShell).

~~~bash
python -m pip install -r requirements.txt
python dashboard.py
~~~

Öffne [http://127.0.0.1:8050/](http://127.0.0.1:8050/). Der Start verwendet die mitgelieferte Beispieldatei.

## Neue Beispieldaten erzeugen

~~~bash
python simulate_data.py
python analyze_data.py
~~~

Beide Befehle schreiben die jeweiligen CSV-Dateien im Ordner `data/` neu. Das Dashboard liest `data/machine_data_with_anomalies.csv` alle fünf Sekunden erneut ein.

## Daten und Auswertung

| Datei | Aufgabe |
| --- | --- |
| `simulate_data.py` | Erzeugt synthetische Temperatur-, Vibrations- und Druckwerte mit künstlichen Ausreißern. |
| `analyze_data.py` | Markiert Temperaturwerte über 85 °C oder Vibrationswerte über 0,04 als auffällig. |
| `dashboard.py` | Zeigt Temperatur und Vibration mit Dash und Plotly. Rote Marker kennzeichnen Zeilen mit `anomaly = -1`. |

Die Demo verwendet simulierte Daten und feste Schwellenwerte zur Anomalieerkennung.
