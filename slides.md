---
author: Alexander Sommer
selectable: true
theme: seriph
background: /wind2.jpg
class: text-center
highlighter: shikiji
lineNumbers: false
drawings:
  persist: false
title: Seminarvortrag Energieinformatik
exportFilename: seminarvortrag-energieinformatik-ausbauziele-nord-süd-eu
mdc: true
aspectRatio: 16/9
canvasWidth: 1920
colorSchema: light
transition: slide-left
download: true
remote: energieinformatik
---

<div class="blr">

# Seminarvortrag Energieinformatik
</br>

## Integration von Ausbauzielen in süd- und nordeuropäischen Ländern: Auswirkungen auf die Lastflüsse im europäischen Stromnetz und ihre Folgen für Baden-Württemberg

Alexander Sommer -- 13.02.2024

Link zu den Folien: https://hd1ex.github.io/seminarvortrag-einfo/

</div>

---
layout: center
---

# Grobe Idee

<style>
p {
  font-size: 4em;
}
</style>

> Wenn in Zukunft im Norden viel Wind- und im Süden viel Sonnenenergie ausgebaut wird,
> (wie) bekommen wir diese zusätzliche, ggf. stark _fluktuierende_ Leistung verteilt und welche Rolle spielt dabei Baden-Württemberg?

---
layout: two-cols
---

<Map country="Deutschland" />

::right::

# Betrachtete Länder
- Deutschland
## Südeuropa
- Portugal
- Spanien
- Italien
- Frankreich
## Nordeuropa
- Dänemark
- Norwegen
- Schweden
- Finnland

---
transition: none
---

<Overview min=0 max=20 />

---

<Overview min=1 max=1 />

---

# Installierte Leistung und Kapazitätsfaktor

<style>
blockquote {
     margin-bottom: 1cm;
     margin-top: 1.5cm;
}
p {
  font-size: 4em;
}
</style>

> Die **Installierte Leistung** ist die _maximale Leistung_ der in einem Kraftwerk installierten Generatoren bzw. die in einem Land oder einem Staat installierte Gesamtleistung aller Kraftwerke.

<v-clicks>

- Für Erneuerbare Energien stellt diese Extremwerte dar.
- Diese sind für die Lastflussanalyse interessant.


> Das Verhältnis zwischen der tatsächlich erbrachten, _durchschnittlichen_ Leistung und der installierten Leistung, wird **Kapazitätsfaktor** genannt.

- Für Wind und Photovoltaik meist deutlich unter 100&#8239;%.

</v-clicks>

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: Karl Friedrich Schäfer - Systemführung; Betrieb elektrischer Energieübertragungsnetze</footer>

---

# Beispiel Deutschland

<img src="/energy-charts_wind_pv_de.svg" class="rounded shadow" style="width: 100%; height: 80%; object-fit: contain;" />

Installierte Leistung: Wind 68,5&#8239;GW und Photovoltaik 81,8&#8239;GW

<!--
- Wind: 25 %
- PV: 9-15 %
-->

---

<Overview min=2 max=3 />

---

# Datenquellen

<br />

<v-clicks>

Daten für das Jahr 2023: `energy-charts.info`
- Nutzt öffentliche Energiedaten
- Leipziger Strombörse EEX, ENTSO-E, etc.

<p style="margin-top: 2cm;">Ausbaupläne: Website der Europäischen Kommission</p>

- EU-Verordnung über die „Gestaltung der Energieunion und der Klimaschutzmaßnahmen“
- Vepflichtung für „Nationale Energie- und Klimapläne (NECPs)“

</v-clicks>

---

# Minimale und maximale Last

<img src="/energy-charts_Durchschnittliche_öffentliche_Nettostromerzeugung_in_einer_Woche_in_Deutschland_2023.svg" class="rounded shadow" style="width: 100%; height: 90%; object-fit: contain;" />

---

<Chart2023 country='Portugal' />

---

<Chart2030 country='Portugal' />

---

<Chart2023 country='Spanien' />

---

<Chart2030 country='Spanien' />

---

<Chart2023 country='Italien' />

---

<Chart2030 country='Italien' />

---

<Chart2023 country='Frankreich' />

---

<Chart2030 country='Frankreich' />

---

<Chart2023 country='Dänemark' />

---

<Chart2030 country='Dänemark' />

---

<Chart2023 country='Norwegen' />

---

<Chart2030 country='Norwegen' />

---

<Chart2023 country='Schweden' />

---

<Chart2030 country='Schweden' />

---

<Chart2023 country='Finnland' />

---

<Chart2030 country='Finnland' />

---

<Chart2023 country='Deutschland' />

---

<Chart2030 country='Deutschland' />

---

# Zusammenfassung der Ausbauziele

<Chart2030Summary />

---

# Zusammenfassung der Ausbauziele

<Chart2030SummaryDE />

---

<Overview min=4 max=4 />

---
layout: two-cols-header
---

# HGÜ-Leitungen: Deutschland

::left::

<img src="/hgü-de.png" class="rounded" style="width: 100%; height: 94%; object-fit: contain;" />
<small>Bildquelle: https://doi.org/10.1007/978-3-658-36199-0</small>

::right::

| Verbindung | Leistung |
| --- | --- |
| A-Nord | 2&#8239;GW |
| Ultranet | 2&#8239;GW |
| SuedLink | 2x 2&#8239;GW |
| SuedOstLink | 2&#8239;GW |

---
layout: two-cols-header
---

# HGÜ-Leitungen: Norwegen

::left::

<img src="/norwegen-deutschland.svg" class="rounded" style="width: 94%; height: 75%;" />
<small>Bildquelle: https://de.wikipedia.org/wiki/NordLink</small>

::right::

| Verbindung | Leistung |
| --- | --- |
| NordLink | 1,4&#8239;GW |
| NorGer | 1,4&#8239;GW |
| NorNed | 0,7&#8239;GW |

---
layout: two-cols-header
---

# HGÜ-Leitungen: Schweden

::left::

<img src="/baltic-cable.png" class="rounded" style="width: 94%; height: 90%;" />
<small>Bildquelle: https://de.wikipedia.org/wiki/Baltic_Cable</small>

::right::

| Verbindung | Leistung |
| --- | --- |
| Baltic Cable | 0,6&#8239;GW |

---

# Überblick Übertragungsnetz DE - BW

<img src="/ünetz-bw-annot.png" class="rounded" style="width: 90%; height: 88%; object-fit: contain;" />
<small>Bildquelle: https://www.vde.com/de/fnn/dokumente/karte-deutsches-hoechstspannungsnetz</small>

<!--
- Pro 380 kV-Stromkreis ~1,4&#8239;GW
- Grobe Schätzung: 10-15&#8239;GW
-->

---

# Stromhandelskapazitäten Deutschland 2030

| Nachbarland | Leistung |
| --- | --- |
| Dänemark | 4&#8239;GW |
| Niederlande | 5&#8239;GW |
| Frankreich | 4,8&#8239;GW |
| Schweiz | 5,6&#8239;GW |
| Österreich | 7,5&#8239;GW |

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5">Quelle: Übertragungsnetzbetreiber und Bundesnetzagentur - Netzentwicklungsplan Strom 2030</footer>

---

<Overview min=5 max=5 />

---

# Sektorkopplung und Ausstieg aus fossilen Energieträgern

<v-click>

### Möglichkeit der Nutzung elektrischer Energie in anderen Sektoren:

</v-click>

<v-clicks>

- **Verkehr** steigt vermehrt auf **E-Autos** um
    <ul>
    <li style="font-size: 1em;">Wirkungsgrad von 64 Prozent</li>
    <li style="font-size: 1em;">ca. 3x effizienter <small>[1]</small></li>
    </ul>
- **Haushalte** steigen vermehrt auf **Wärmepumpen** um
- Die **Industrie** steigt auf grünen **Wasserstoff** und dessen Produkte um

</v-clicks>

<v-click>

<p class="mt-4">⇒ Steigerung des Stromverbrauchs</p>

</v-click>

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5">[1] Quelle: https://www.bmuv.de/WS5549</footer>

---

# Sektorkopplung und Ausstieg aus fossilen Energieträgern

<v-clicks>

## Beispiel Schweden
- Rechnet mit Verdopplung des Stromverbrauchs
- Stahlindustrie soll mit grünem Wasserstoff betrieben werden

## Beispiel Deutschland
- Seit dem 01. Januar 2024: Gesetz für Erneuerbares Heizen (Neubauten min. 65&#8239;% effizient)
- Projektion der Bundesregierung: Steigerung des Bruttostromverbrauchs um min. 11&#8239;% bis 2030 (595&#8239;TWh auf min. 658&#8239;TWh)

</v-clicks>

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5">
    Quellen: Tagesschau - Schwedens Atomwende, Pläne für neue AKW & Bundesministerium für Wirtschaft und Klimaschutz - Entwicklung des Bruttostromverbrauchs bis 2030
</footer>

---

# Energieverbrauch DE nach Sektoren

<img src="/eev-sektoren.png" class="rounded" style="width: 90%; height: 90%;" />

---

<Overview min=6 max=6 />

---

<style>
h1 {
    margin-bottom: 1cm;
}
</style>

# Potentielle (neue) Lastflüsse

<style>
p {
    font-size: 0.8em;
}
</style>

<v-clicks>

- **Beobachtung**: Ausgebaute Leistung übersteigt die der geplanten Stromtrassen.
- **Folgerung**: Die geplanten Trassen können oft ganz ausgelastet werden.

### Leistung nach Baden-Württemberg:

| Start | Leitungsstrecke | Leistung |
| --- | --- | --- |
| Norwegen | NorGer + A-Nord + Ultranet | 1,4&#8239;GW |
| Norwegen | Nordlink + SuedLink | 1,4&#8239;GW |
| Dänemark | SuedLink / A-Nord + Ultranet | 4&#8239;GW |
| Frankreich (auch ES/PT/IT) | AC-Netz | 4,5&#8239;GW |
| Norddeutschland | AC-Netz | 10-15&#8239;GW* |

</v-clicks>

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5">* Eigene grobe, optimistische Abschätzung basierend auf dem Netzplan des VDE mit der Annahme, dass jeder 380&#8239;kV-Stromkreis bis zu ~1,4&#8239;GW (= 380&#8239;kV · 2&#8239;kA · √3) an Leistung übertragen kann.</footer>

---

# Fazit & Ausblick

<v-clicks>

- Die europäischen Länder haben ambitionierte Ausbauziele
- Das Übertragungsnetz bedarf weiteren Ausbaus oder Entlastung durch Speicherlösungen
- **Baden-Württemberg** wird - als Industrieland - **Stromimporteur** und Transitland

<p style="margin-top: 4cm;" >
Um die viele Erneuerbare Energie international zu verarbeiten, braucht es
</p>

- weiteren Netzausbau
- Energiespeicher
- Sektorkopplung

</v-clicks>

---

# Chancen
<br />
<br />

## Beispiel Speicher an ehem. Kraftwerkstandorten


<v-clicks>

- Studie vom Fraunhofer-Institut für Solare Energiesysteme (ISE)
- Möglichkeit Batteriespeicher an ehemalige Kraftwerkstandorte installieren
- Bis zu **10,2&#8239;GW** an installierter Leistung in BW möglich

</v-clicks>

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: Fraunhofer ISE - Kurzstudie: Batteriegroßspeicher an ehemaligen Kraftwerksstandorten </footer>

---
layout: end
---

# Ende
## Vielen Dank für die Aufmerksamkeit!
## Fragen?

---

# Effizienz batteriebetriebener Elektroautos

<img src="/infografik_wirkungsgrade_elektroautos.png" class="rounded" style="width: 80%; height: 85%; object-fit: contain;" />

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: https://www.bmuv.de/WS5549 </footer>

---

<img src="/PV_Wind_Juli_2023.svg" class="rounded" style="width: 100%; height: 100%; object-fit: contain;" />

---

<img src="/tn-bw-studie-bw-export.png" class="rounded" style="width: 100%; height: 100%; object-fit: contain;" />

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: TransnetBW - Studie Stromnetz 2050</footer>

---

<img src="/tn-bw-studie-bw-energieflüsse.png" class="rounded" style="width: 100%; height: 99%; object-fit: contain;" />

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: TransnetBW - Studie Stromnetz 2050</footer>

---

<section style="display: flex;">
<div style="flex: 1;">
    <h1>Energiemengen 2050</h1>
</div>
<div style="flex: 2;">
    <img src="/tn-bw-studie-bw-energiemengen.png" class="rounded" style="width: 100%; height: 63%; object-fit: contain;" />
</div>
</section>
<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: TransnetBW - Studie Stromnetz 2050</footer>

---

<img src="/tn-bw-studie-bw-endenergieverbrauch.png" class="rounded" style="width: 100%; height: 103%; object-fit: contain;" />

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: TransnetBW - Studie Stromnetz 2050</footer>

---

<img src="/tn-bw-studie-auslastung-hs-netz.png" class="rounded" style="width: 100%; height: 103%; object-fit: contain;" />

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: TransnetBW - Studie Stromnetz 2050</footer>

---

<img src="/tn-bw-studie-zielnetz-2050.png" class="rounded" style="width: 100%; height: 103%; object-fit: contain;" />

<footer class="absolute bottom-0 left-0 right-0 p-2 mb-5"> Quelle: TransnetBW - Studie Stromnetz 2050</footer>

