module v2_require_4(
    input  [3:0] btn,
    output [5:0] led
);

// Example logic (cleaned and valid)

assign led[0] = ( btn[0] & ~btn[1] & ~btn[2] & ~btn[3]) |
                (~btn[0] &  btn[1] & ~btn[2] & ~btn[3]) |
                (~btn[0] & ~btn[1] &  btn[2] & ~btn[3]) |
                (~btn[0] & ~btn[1] & ~btn[2] &  btn[3]);

assign led[1] = ( btn[0] &  btn[1] & ~btn[2] & ~btn[3]) |
                ( btn[0] & ~btn[1] &  btn[2] & ~btn[3]) |
                (~btn[0] &  btn[1] & ~btn[2] &  btn[3]) |
                (~btn[0] & ~btn[1] &  btn[2] &  btn[3]);

assign led[2] = ( btn[0] &  btn[1] &  btn[2] & ~btn[3]) |
                ( btn[0] &  btn[1] & ~btn[2] &  btn[3]) |
                ( btn[0] & ~btn[1] &  btn[2] &  btn[3]) |
                (~btn[0] &  btn[1] &  btn[2] &  btn[3]);

assign led[3] = btn[0] & btn[1] & btn[2] & btn[3];

// All OFF condition
assign led[4] = ~btn[0] & ~btn[1] & ~btn[2] & ~btn[3];

// XOR (odd parity)
assign led[5] = btn[0] ^ btn[1] ^ btn[2] ^ btn[3];

// If you actually want EVEN parity instead, use:
// assign led[5] = ~(btn[0] ^ btn[1] ^ btn[2] ^ btn[3]);

endmodule
# 3. Circuit 4

module top(
    input [7:0] sw,
    output [3:0] led
);

assign led[3] = // your simplified Circuit 4 logic

endmodule
#r4
module top(
    input  [3:0] btn,
    output [5:0] led
);

wire [2:0] count;

// Count how many buttons are pressed
assign count = btn[0] + btn[1] + btn[2] + btn[3];

// Exactly one pressed
assign led[0] = (count == 1);

// Exactly two pressed
assign led[1] = (count == 2);

// Exactly three pressed
assign led[2] = (count == 3);

// All four pressed
assign led[3] = (count == 4);

// Odd number (1 or 3)
assign led[4] = count[0];

// Even number (0,2,4)
assign led[5] = ~count[0];

endmodule
#Full Combined Challenge File
module top(
    input  [11:0] sw,
    input  [3:0] btn,
    output [9:0] led
);

// Challenge 1
assign led[1] =
btn[0] &
(
(sw[4:0] == 5'b10010) |
(sw[4:0] == 5'b00101) |
(sw[4:0] == 5'b11010)
);

// Challenge 2
assign led[0] = sw[8] | sw[9] | sw[10] | sw[11];

endmodule
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
