Reverse engineering of "IRLR7843 MOS Module" (ALI-Express)

![PICTURE see KICAD File](https://github.com/ludwich66/IRLR7843_MOS_Trigger-Switch_Module/blob/main/LR7843_FET-Module.jpg)


Very Low RDS(on) at 4.5V VGS (see Table)

MODUL DIMENSION: 17 mm x 7 mm

V_DS 30 V / RDS(on) 3,3 mΩ

V_GS_max +-20V
ID @ TC =  25°C, Continuous Drain Current VGS @ 10V, 161A

ID @ TC = 100°C, Continuous Drain Current VGS @ 10V, 113A

PD @TC = 25°C Maximum Power Dissipation  140 W

PD @TC = 100°C Maximum Power Dissipation  71 W

| $V_{GS}$ [V_gs] | $I_D$ [A] bei 25 °C | $I_D$ [A] bei 175 °C |
| :--: | :--: | :--: |
| 2,0 | 2 | 7 |
| 2,1 | 2,5 | 10 |
| 2,2 | 3,2 | 13 |
| 2,3 | 4,3 | 17 |
| 2,4 | 5,8 | 22 |
| 2,5 | 7,7 | 29 |
| 2,6 | 10 | 37 |
| 2,7 | 13 | 46 |
| 2,8 | 18 | 57 |
| 2,9 | 24 | 71 |
| 3,0 | 31 | 85 |
| 3,1 | 40 | 100 |
| 3,2 | 52 | 115 |
| 3,3 | 65 | 130 |
| 3,4 | 79 | 145 |
| 3,5 | 93 | 155 |
| 3,6 | 107 | <165 |
| 3,7 | 118 | <173 |
| 3,8 | 126 | <180 |
| 3,9 | 132 | <185 |
| 4,0 | 137 | <190 |
| 4,1 | 141 | <194 |
| 4,2 | 144 | <197 |
| 4,3 | 147 | <199 |
| 4,4 | 149 | <200 |
| 4,5 | 150 | <201 |
| 4,6 | 151 | <202 |
| 4,7 | 152 | <203 |
| 4,8 | 153 | <204 |
| 4,9 | 154 | <205 |
| 5,0 | 155 | <206 |

KI

# Welche Wärmeabfuhr ist bei einer Platinengröße von 7 x 17 mm gut durchkontaktiert zu erwarten?

Max Strom bei 4,5 V bzw 3,3 V

Für eine Platine mit den Maßen 7 mm x 17 mm (also 119 mm²) und guter Durchkontaktierung zur Wärmeabfuhr können bei MOSFETs ähnliche Größenordnungen für den Wärmewiderstand angenommen werden:

- Wärmewiderstand von Drain-Anschluss zur Platine (Thermal Pad) durch Durchkontaktierung: ca. 1–3 K/W, abhängig von Anzahl, Durchmesser und Layout der Durchkontaktierungen.
- Platinen-Wärmewiderstand zur Umgebung bei guter Kühlung (z.B. Kühlkörper, Lüfter): ca. 5–15 K/W je nach Design.
- Gesamt-Wärmewiderstand ohne aktive Kühlung typ. 10–20 K/W für kleine Platinen.


### Abschätzung maximaler Dauerstrom

Die Verlustleistung $P = I^2 \cdot R_{DS(on)}$ und zulässige Temperaturerhöhung $\Delta T$ bestimmen den Maximalstrom $I_{max}$.

Bei typischem MOSFET $R_{DS(on)}$ von:

- 3,3 V Gate: ca. 4,5 mΩ
- 4,5 V Gate: ca. 3,2 mΩ

Angenommen maximale Gehäusetemperaturdifferenz zur Umgebung $\Delta T = 50\,^\circ C$

Mit Wärmewiderstand $R_{th} = 10\,K/W$ als Beispiel:

$$
P_{max} = \frac{\Delta T}{R_{th}} = \frac{50}{10} = 5\,W
$$

Maximaler Strom:

$$
I_{max} = \sqrt{\frac{P_{max}}{R_{DS(on)}}}
$$

Für 3,3 V Gate:

$$
I_{max} = \sqrt{\frac{5}{0,0045}} = \sqrt{1111} \approx 33\,A
$$

Für 4,5 V Gate:

$$
I_{max} = \sqrt{\frac{5}{0,0032}} = \sqrt{1562} \approx 39\,A
$$

### Fazit

- Bei der kleinen Platine mit guter Durchkontaktierung und guter Kühlung sind Dauerströme um 30–40 A bei den beiden Gate-Spannungen realistisch, ohne dass der MOSFET überhitzt.
- Höhere Ströme sind nur mit besserer Kühlung (z.B. Kühlkörper, aktivem Lüfter) oder zusätzlicher Wärmeableitung möglich.

Diese Werte sind Näherungen, da die tatsächliche Kühlleistung von vielen Platinen- und Umweltfaktoren abhängt. Für Dauerbetrieb ist eine Temperaturüberwachung und thermische Simulation empfehlenswert.
