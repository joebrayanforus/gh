`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date: 25.04.2026 11:36:31
// Design Name: 
// Module Name: p5
// Project Name: 
// Target Devices: 
// Tool Versions: 
// Description: 
// 
// Dependencies: 
// 
// Revision:
// Revision 0.01 - File Created
// Additional Comments:
// 
//////////////////////////////////////////////////////////////////////////////////

module p5(
    output[3:0] seg_an,
    input[7:0] sw,
    
    output[7:0] seg_cat,
    input[3:0] btn
    );
assign seg_an=btn;
assign seg_cat=sw;
endmodule


----
set_property -dict { PACKAGE_PIN R17   IOSTANDARD LVCMOS33 } [get_ports { sw[0] }]; #IO_L19N_T3_VREF_34 Schematic=SW0
set_property -dict { PACKAGE_PIN U20   IOSTANDARD LVCMOS33 } [get_ports { sw[1] }]; #IO_L15N_T2_DQS_34 Schematic=SW1
set_property -dict { PACKAGE_PIN R16   IOSTANDARD LVCMOS33 } [get_ports { sw[2] }]; #IO_L19P_T3_34 Schematic=SW2
set_property -dict { PACKAGE_PIN N16   IOSTANDARD LVCMOS33 } [get_ports { sw[3] }]; #IO_L21N_T3_DQS_AD14N_35 Schematic=SW3
set_property -dict { PACKAGE_PIN R14   IOSTANDARD LVCMOS33 } [get_ports { sw[4] }]; #IO_L6N_T0_VREF_34 Schematic=SW4
set_property -dict { PACKAGE_PIN P14   IOSTANDARD LVCMOS33 } [get_ports { sw[5] }]; #IO_L6P_T0_34 Schematic=SW5
set_property -dict { PACKAGE_PIN L15   IOSTANDARD LVCMOS33 } [get_ports { sw[6] }]; #IO_L22N_T3_AD7N_35 Schematic=SW6
set_property -dict { PACKAGE_PIN M15   IOSTANDARD LVCMOS33 } [get_ports { sw[7] }]; #IO_L23N_T3_35 Schematic=SW7


#Push Buttons
set_property -dict { PACKAGE_PIN W14   IOSTANDARD LVCMOS33 } [get_ports { btn[0] }]; #IO_L8P_T1_34 Schematic=BTN0
set_property -dict { PACKAGE_PIN W13   IOSTANDARD LVCMOS33 } [get_ports { btn[1] }]; #IO_L4N_T0_34 Schematic=BTN1
set_property -dict { PACKAGE_PIN P15   IOSTANDARD LVCMOS33 } [get_ports { btn[2] }]; #IO_L24P_T3_34 Schematic=BTN2
set_property -dict { PACKAGE_PIN M14   IOSTANDARD LVCMOS33 } [get_ports { btn[3] }]; #IO_L23P_T3_35 Schematic=BTN3
#Seven Segmen Display Anodes
set_property -dict { PACKAGE_PIN K19   IOSTANDARD LVCMOS33 } [get_ports { seg_an[0] }]; #IO_L10P_T1_AD11P_35 Schematic=SSEG_AN0
set_property -dict { PACKAGE_PIN H17   IOSTANDARD LVCMOS33 } [get_ports { seg_an[1] }]; #IO_L13N_T2_MRCC_35 Schematic=SSEG_AN1
set_property -dict { PACKAGE_PIN M18   IOSTANDARD LVCMOS33 } [get_ports { seg_an[2] }]; #IO_L8N_T1_AD10N_35 Schematic=SSEG_AN2
set_property -dict { PACKAGE_PIN L16   IOSTANDARD LVCMOS33 } [get_ports { seg_an[3] }]; #IO_L11P_T1_SRCC_35 Schematic=SSEG_AN3
#Seven Segmen Display Cathodes
set_property -dict { PACKAGE_PIN K14   IOSTANDARD LVCMOS33 } [get_ports { seg_cat[0] }]; #IO_L20P_T3_AD6P_35 Schematic=SSEG_CA
set_property -dict { PACKAGE_PIN H15   IOSTANDARD LVCMOS33 } [get_ports { seg_cat[1] }]; #IO_L19P_T3_35 Schematic=SSEG_CB
set_property -dict { PACKAGE_PIN J18   IOSTANDARD LVCMOS33 } [get_ports { seg_cat[2] }]; #IO_L14P_T2_AD4P_SRCC_35 Schematic=SSEG_CC
set_property -dict { PACKAGE_PIN J15   IOSTANDARD LVCMOS33 } [get_ports { seg_cat[3] }]; #IO_25_35 Schematic=SSEG_CD
set_property -dict { PACKAGE_PIN M17   IOSTANDARD LVCMOS33 } [get_ports { seg_cat[4] }]; #IO_L8P_T1_AD10P_35 Schematic=SSEG_CE
set_property -dict { PACKAGE_PIN J16   IOSTANDARD LVCMOS33 } [get_ports { seg_cat[5] }]; #IO_L24N_T3_AD15N_35 Schematic=SSEG_CF
set_property -dict { PACKAGE_PIN H18   IOSTANDARD LVCMOS33 } [get_ports { seg_cat[6] }]; #IO_L8P_T1_AD10P_35 Schematic=SSEG_CG
set_property -dict { PACKAGE_PIN K18   IOSTANDARD LVCMOS33 } [get_ports { seg_cat[7] }]; #IO_L12N_T1_MRCC_35 Schematic=SSEG_DP



📘 Kompakte, prüfungsorientierte Zusammenfassung: Konfigurationsmanagement (KM)
🎯 Ziel des Konfigurationsmanagements
Konfigurationsmanagement sorgt dafür, dass ein sich ständig weiterentwickelndes Softwaresystem beherrschbar, nachvollziehbar und reproduzierbar bleibt.

Es beantwortet zentrale Fragen wie:

Was hat sich seit gestern geändert?

Wer hat wann was geändert — und warum?

Welche Version ist betroffen  ?

Welche Fehler sind in dieser Version schon behoben?

Wie stelle ich eine alte Version (z. B. von 1999) wieder her?

🧩 Definitionen
Software Configuration Management (SCM)
Gute Ingenieurpraxis für alle Softwareprojekte; erhöht Zuverlässigkeit und Qualität.
(IEEE 828)

Konfigurationsmanagement (KM)
Managementdisziplin über den gesamten Lebenszyklus eines Produkts, um Transparenz und Überwachung seiner funktionalen und physischen Merkmale sicherzustellen.
(DIN EN ISO 10007)

🔧 KM‑Prozess nach ISO 10007
1️⃣ Konfigurationsidentifizierung
Welche Bestandteile gehören zum Produkt?

Welche Versionen existieren?

Welche Baselines gibt es?

2️⃣ Konfigurationsüberwachung
Änderungen dokumentieren, begründen, genehmigen/ablehnen

Freigaben planen

3️⃣ Konfigurationsbuchführung
Lückenlose Rückverfolgbarkeit aller Änderungen

Historie bis zur letzten Baseline

4️⃣ Konfigurationsauditierung
Qualitätssicherung vor Freigabe einer Konfiguration

5️⃣ KM‑Planung
Festlegung von Standards, Rollen, Verfahren

🛠️ Arbeitsgebiete des Konfigurationsmanagements
1. Versionsmanagement
Verwaltung der Entwicklungshistorie

Wer hat wann was geändert?

Fokus dieses Kapitels

2. Variantenmanagement (ST II)
Parallel existierende Ausprägungen eines Produkts

Unterschiedliche Features, Länder, Plattformen

3. Releasemanagement
Planung von Auslieferungsständen

Welche Features kommen wann in ein Release?

4. Buildmanagement
Automatisierte Erzeugung des Produkts

Welche Datei wird womit und wann gebaut?

5. Änderungsmanagement
Verwaltung von Bug Reports und Feature Requests

Zuordnung zu Releases

🗂️ Workspaces im KM
Public Workspace (Repository)
Enthält alle Versionen aller Dokumente

Zentraler Ort für Zusammenarbeit

Developer Workspace
Privater Arbeitsbereich jedes Entwicklers

Lokale Kopien der benötigten Dokumente

Integrator Workspace
Einziger Workspace für Systemintegration

🔄 Typische Aktionen
Aktion	Bedeutung
Check‑out	Erste lokale Kopie eines Dokuments holen
Update	Lokale Version an neue Repository‑Versionen anpassen
Add	Neues Dokument erstmals ins Repository einfügen
Check‑in / Commit	Neue Version eines Dokuments einspielen
❓ Herausforderungen im Workspace‑Modell
Konsistenz abhängiger Dokumente

Konflikte bei parallelen Änderungen

Effiziente Repository‑Operationen

Offline‑Arbeit ermöglichen

📚 Zentrale Begriffe
Begriff	Bedeutung
Dokument	Datei oder Dateibaum unter Versionskontrolle
Versionsobjekt	Zustand eines Dokuments zu einem Zeitpunkt
Variante	Parallel existierende Ausprägung eines Dokuments
Revision	Zeitlich aufeinander folgende Versionen
Konfiguration	Menge von Dokumenten in bestimmter Version
Baseline	Getestete, stabile Konfiguration zu einem Meilenstein
Release	Ausgelieferte Baseline (intern oder extern) 🔧 Versionsmanagement – kompakte Zusammenfassung
🎯 Definition
Versionsmanagement verwaltet zeitlich aufeinander folgende Zustände eines Dokuments.
Es geht also darum, wie sich ein Dokument über die Zeit verändert und wie diese Änderungen nachvollziehbar gespeichert werden.

🧱 Grundprinzipien von Versionsverwaltungssystemen
📌 1. Historie statt vollständiger Kopien
Es wird nicht jede Version komplett gespeichert, sondern:

Eine Revisionshistorie, bestehend aus Änderungen (Deltas).

📌 2. Delta-basierte Speicherung
Ein Delta beschreibt die Änderungen zwischen zwei Versionen.

Deltas bestehen aus Hunks = klar abgegrenzte Blöcke, in denen Änderungen passiert sind.

Jede Revision hat eine ID.

🔍 Operationen: Diff, Patch, Merge
🟦 Diff
Ermittelt Unterschiede zwischen zwei Textdateien.

Ein Diff besteht aus:

Hunks (Änderungsblöcke)

Zeilenbasierte Analyse

Markierungen im Diff:
Symbol	Bedeutung
!	geänderte Zeile
+	hinzugefügte Zeile
-	gelöschte Zeile
(keine Markierung)	Kontextzeile zur Orientierung
🟩 Patch
Ein Patch ist ein Delta, das angewendet wird, um eine Version in eine andere zu überführen.

Zwei Arten:
Vorwärtsdelta: d1 → d2
→ erzeugt neue Version aus alter Version

Rückwärtsdelta: d2 → d1
→ stellt alte Version wieder her

📘 Beispielhafte Interpretation der gezeigten Diffs
Du hast in deinen Folien mehrere Beispiele:

Beispiel 1: Erste Revision
Parameter a, b wurden zu v, w umbenannt.

Ein else-Block wurde hinzugefügt.

Beispiel 2: Zweite Revision
if (v < w) wurde zu while (v < w) geändert.

Der else-Block wurde entfernt.

Rückwärtsdeltas
Stellen jeweils die vorherige Version wieder her.

Funktionieren wie „Undo“-Operationen.

🔄 Vorwärtsdelta vs. Rückwärtsdelta
Historienmodell	Vorteile	Nachteile
Aktuelle Version + Rückwärtsdeltas	Schneller Zugriff auf neueste Version	Langsame Rekonstruktion alter Versionen
Initiale Version + Vorwärtsdeltas	Schnelle Rekonstruktion alter Versionen	Langsamer Zugriff auf neueste Version
Moderne Systeme (Git, SVN) nutzen optimierte Mischformen.🎯 Ziele bei der Erzeugung von Deltas
Diff‑Werkzeuge versuchen, Deltas zu erzeugen, die

möglichst klein sind (wenig geänderte Zeilen),

gut lesbar bleiben (klar erkennbare Hunks, sinnvolle Kontextzeilen).

Das ist ein Spannungsfeld: kleinste Deltas sind nicht immer die lesbarsten.

📐 Gängige Regeln zur Delta‑Erzeugung
1. Hunk beginnt mit genau einer Kontextzeile
Ausnahme: Wenn das Delta am Dokumentanfang beginnt.

Danach sollen möglichst nur geänderte (!), gelöschte (-) oder eingefügte (+) Zeilen folgen.

2. Hunks müssen durch mindestens eine unveränderte Zeile getrennt sein
Dadurch wird klar, dass es sich um getrennte Änderungsbereiche handelt.

3. Gesamtzahl der Änderungen soll minimal sein
Minimierung der Summe aus:

geänderten Zeilen

gelöschten Zeilen

neu eingefügten Zeilen

4. Optional: Änderungsmarkierung „!“ statt Löschen+Einfügen
Wenn alte und neue Zeile ähnlich genug sind.

Erhöht Lesbarkeit und reduziert Delta‑Größe.

🧩 Diskussion des Beispiels
Warum fehlen im Beispiel die Kontextzeilen?

Hunk 1: Änderung ist in Zeile 1 → keine Kontextzeile möglich.

Hunk 2: Kontextzeilen wurden aus Platzgründen weggelassen.

Das Delta ist minimal, aber dadurch schwerer lesbar.

Alternative:

Beide Hunks zu einem großen Hunk zusammenfassen → bessere Lesbarkeit

Nachteil: zusätzliche unveränderte Zeilen (02–09) würden aufgenommen → Delta wird größer.

Das zeigt das Grunddilemma:
Klein vs. gut lesbar.

⚠️ Dilemma bei der Delta‑Erzeugung
Ein Diff‑Tool kennt nur:

Vorgängerversion

Nachfolgeversion

Es weiß nicht, welche Operationen der Entwickler tatsächlich ausgeführt hat.

Beispielproblem:

Ist eine Änderung in Zeile i ein

Löschen + Einfügen
oder

eine Änderung derselben Zeile?

Diff‑Tools müssen das heuristisch entscheiden.

📘 Beispiel: Nutzloses vs. nützliches Diff
❌ Nutzloses Diff
Ein großer Hunk über alle Zeilen

Viele Zeilen als geändert markiert (!)

Keine sinnvolle Struktur

Ergebnis: 5 geänderte Zeilen, obwohl eigentlich nur 2 echte Änderungen existieren

→ Minimiert nicht die Anzahl der Änderungen
→ Schlechte Lesbarkeit

✅ Nützliches Diff
Zwei getrennte Hunks

Jeder Hunk enthält nur die wirklich betroffenen Zeilen

Kontextzeilen korrekt gesetzt

Ergebnis:

2 geänderte Zeilen

2 neue Zeilen

→ Kleineres Delta
→ Deutlich besser lesbar

📦 Unified Diff Format (GNU)
Das Unified‑Format ist heute Standard (z. B. in Git).

Beispiel:

Code
@@ -1,1 +1,1 @@
- public void myMethod(int a, int b)
+ public void myMethod(int v, int w)
Merkmale:

@@ -a,b +c,d @@ beschreibt die betroffenen Zeilenbereiche

- zeigt alte Zeilen

+ zeigt neue Zeilen

Kontextzeilen werden unmarkiert angezeigt 🎓 Kurzfazit für die Prüfung
Deltas bestehen aus Hunks, die Änderungen gruppieren.

Ziel: klein und lesbar.

Hunks brauchen Kontextzeilen und müssen getrennt sein.

Diff‑Tools arbeiten heuristisch, da sie keine Änderungsoperationen kennen.

Unified Diff ist das gängigste Format.
