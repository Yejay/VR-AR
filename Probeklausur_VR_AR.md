# Probeklausur: Virtual Reality & Augmented Reality

**Prüfung:** Probeklausur zur Vorbereitung
**Zeit:** 90 Minuten (+ Puffer)
**Punkte:** 100 Punkte gesamt
**Hilfsmittel:** Keine

---

## Hinweise zur Bearbeitung

- Bei **"Nennen Sie..."** Fragen reichen Stichpunkte/Begriffe
- Bei **"Erläutern/Erklären Sie..."** Fragen sind mindestens 2-3 Sätze erforderlich
- Bei **"Was ist...?"** Fragen: Definition + 2-3 Eigenschaften

---

## Teil 1: XR Grundlagen (15 Punkte)

### Frage 1 (5 Punkte)
**Wofür steht XR und was beschreibt dieser Begriff?**

---

### Frage 2 (5 Punkte)
**Nennen Sie die drei Technologien, die unter XR fallen, und beschreiben Sie jeweils in einem Satz, was sie bedeuten.**

---

### Frage 3 (5 Punkte)
**Was unterscheidet Mixed Reality (MR) von Augmented Reality (AR)?**

---

## Teil 2: VR Rendering (20 Punkte)

### Frage 4 (6 Punkte)
**Nennen Sie drei Besonderheiten des VR-Renderings gegenüber herkömmlichem Rendering.**

---

### Frage 5 (7 Punkte)
**Erläutern Sie, was man unter Stereoscopic Rendering versteht. Gehen Sie dabei auf das Prinzip, den Effekt und einen Nachteil ein.**

---

### Frage 6 (7 Punkte)
**Erklären Sie das Problem der Lens Distortion und wie es gelöst wird.**

---

## Teil 3: VR Tracking (15 Punkte)

### Frage 7 (6 Punkte)
**Erklären Sie den Unterschied zwischen 3DoF und 6DoF. Nennen Sie jeweils ein Beispielgerät.**

---

### Frage 8 (5 Punkte)
**Was ist eine IMU? Nennen Sie die drei Komponenten und deren Funktion.**

---

### Frage 9 (4 Punkte)
**Nennen Sie die drei Rotationsachsen und die zugehörige Kopfbewegung.**

---

## Teil 4: VR Immersion & Comfort (15 Punkte)

### Frage 10 (5 Punkte)
**Was ist Immersion?**

---

### Frage 11 (5 Punkte)
**Erläutern Sie den Unterschied zwischen Immersion und Presence.**

---

### Frage 12 (5 Punkte)
**Erklären Sie das Konzept des Uncanny Valley.**

---

## Teil 5: Motion Sickness (10 Punkte)

### Frage 13 (5 Punkte)
**Erklären Sie, wie Motion Sickness in VR entsteht (Sensory Conflict Theory).**

---

### Frage 14 (5 Punkte)
**Nennen Sie vier Maßnahmen zur Reduzierung von Motion Sickness.**

---

## Teil 6: VR Interface & Locomotion (10 Punkte)

### Frage 15 (5 Punkte)
**Was bedeutet Affordance im Kontext von VR? Nennen Sie zwei Beispiele.**

---

### Frage 16 (5 Punkte)
**Was ist Redirected Walking? Erklären Sie kurz das Prinzip.**

---

## Teil 7: AR Grundlagen (15 Punkte)

### Frage 17 (5 Punkte)
**Nennen Sie die drei definierenden Eigenschaften von AR nach Azuma.**

---

### Frage 18 (5 Punkte)
**Erklären Sie den Unterschied zwischen Optical See-Through und Video See-Through. Nennen Sie jeweils einen Vorteil.**

---

### Frage 19 (5 Punkte)
**Was ist der Unterschied zwischen Feature Detection und Feature Matching?**

---

### Frage 20 (5 Punkte)
**Was ist das Occlusion-Problem bei AR und wie kann es gelöst werden?**

---

# Lösungen

---

## Teil 1: XR Grundlagen

### Lösung 1
XR steht für **Extended Reality**. Es ist der Sammelbegriff für alle immersiven Technologien und beschreibt das gesamte Spektrum zwischen realer und virtueller Umgebung (Reality-Virtuality Continuum).

### Lösung 2
- **VR (Virtual Reality):** Nutzer ist komplett in eine digital generierte Umgebung eingetaucht, die reale Welt wird vollständig ausgeblendet.
- **AR (Augmented Reality):** Die reale Welt wird durch digitale Elemente erweitert, wobei die Realität sichtbar bleibt.
- **MR (Mixed Reality):** Virtuelle und reale Objekte interagieren miteinander, z.B. reagiert ein virtuelles Objekt auf die Physik der realen Welt.

### Lösung 3
Bei AR werden digitale Inhalte nur über die Realität gelegt, ohne direkte Interaktion. Bei MR interagieren virtuelle und reale Objekte miteinander - ein virtueller Ball kann z.B. von einem realen Tisch abprallen.

---

## Teil 2: VR Rendering

### Lösung 4
1. Lens Distortion (und inverse Barrel-Distortion als Korrektur)
2. Chromatic Aberration (und RGB-Shift-Korrektur)
3. Stereoscopic Rendering (zwei Bilder pro Frame)

### Lösung 5
Beim **stereoskopischen Rendering** werden zwei leicht versetzte Bilder gerendert – eines für jedes Auge. Der Versatz entspricht der **Interpupillardistanz (IPD)**, also dem Abstand zwischen den Augen. Dadurch entsteht im Gehirn ein räumlicher **3D-Tiefeneffekt**, wie beim natürlichen Sehen. **Nachteil:** Die Render-Last verdoppelt sich.

### Lösung 6
VR-Linsen (meist Fresnel-Linsen) erzeugen eine **Pincushion-Distortion** (Kissenverzerrung), wodurch das Bild verzerrt wahrgenommen würde. **Lösung:** Die Software wendet beim Rendern eine **Barrel-Distortion** (Tonnenverzerrung) an. Da beide Verzerrungen entgegengesetzt sind, heben sie sich gegenseitig auf und das Bild erscheint korrekt.

---

## Teil 3: VR Tracking

### Lösung 7
- **3DoF** erfasst nur die **Rotation** in drei Achsen (Yaw, Pitch, Roll). Beispiel: Google Cardboard
- **6DoF** erfasst zusätzlich die **Position** im Raum (x, y, z). Beispiel: Meta Quest 2/3

### Lösung 8
IMU = **Inertial Measurement Unit**. Komponenten:
1. **Accelerometer:** Misst lineare Beschleunigung (+ Schwerkraft)
2. **Gyroskop:** Misst Winkelgeschwindigkeit (Rotation)
3. **Magnetometer:** Misst Magnetfelder (Drift-Korrektur)

### Lösung 9
- **Yaw (Gieren):** Kopf nach links/rechts drehen
- **Pitch (Nicken):** Kopf nach oben/unten neigen
- **Roll (Rollen):** Kopf zur Seite kippen

---

## Teil 4: VR Immersion & Comfort

### Lösung 10
Immersion ist eine **objektive, technische Eigenschaft** des VR-Systems. Sie beschreibt die Qualität technischer Faktoren wie FOV, Auflösung, Tracking-Qualität und Framerate. Die Technologie ermöglicht das "Eintauchen" in die virtuelle Welt.

### Lösung 11
**Immersion** ist objektiv/technisch – sie beschreibt die Eigenschaften des Systems. **Presence** ist subjektiv/psychologisch – das Gefühl, wirklich "dort" zu sein ("Being there"). Wichtig: Ohne Immersion kann keine Presence entstehen – die Technologie schafft die Voraussetzung.

### Lösung 12
Das **Uncanny Valley** beschreibt eine Akzeptanzlücke bei fast menschenähnlichen Figuren. Wenn virtuelle Charaktere sehr menschlich aussehen, aber nicht perfekt sind, wirken sie **gruselig oder unheimlich**. Die Akzeptanz sinkt stark. Bei noch höherem Realismus steigt sie wieder.

---

## Teil 5: Motion Sickness

### Lösung 13
Motion Sickness entsteht durch einen **sensorischen Konflikt**: Das Auge sieht Bewegung in der virtuellen Welt, aber das **Vestibularorgan (Innenohr)** spürt Stillstand. Der Körper interpretiert diese Diskrepanz als Vergiftungssymptom und reagiert mit **Übelkeit**.

### Lösung 14
1. Hohe Framerate (90+ FPS)
2. Teleportation statt künstlicher Smooth-Bewegung
3. Statische Referenzpunkte (Cockpit, künstlicher Horizont)
4. Niedrige Latenz

---

## Teil 6: VR Interface & Locomotion

### Lösung 15
**Affordance** bedeutet, dass das Design eines Objekts seine Funktion kommuniziert. Beispiele:
- Ein Griff sieht greifbar aus
- Ein Knopf sieht drückbar aus
- Ein Hebel sieht ziehbar aus

### Lösung 16
Bei **Redirected Walking** wird der Nutzer unmerklich manipuliert. Er läuft z.B. in der Realität im Kreis, glaubt aber virtuell geradeaus zu gehen. Dies nutzt aus, dass Menschen kleine Abweichungen zwischen visueller und physischer Bewegung nicht bemerken.

---

## Teil 7: AR Grundlagen

### Lösung 17
Die drei Säulen nach Azuma:
1. **Kombiniert Realität und Virtualität**
2. **Interaktiv in Echtzeit**
3. **Registriert im 3D-Raum** (räumlich verankert)

### Lösung 18
- **Optical See-Through** (z.B. HoloLens): Nutzer sieht Realität direkt durch transparente Gläser. Vorteil: Keine Latenz bei der Realitätsdarstellung.
- **Video See-Through** (z.B. Quest 3): Kameras filmen Realität, wird auf Display angezeigt. Vorteil: Okklusion einfach umsetzbar, großes FOV.

### Lösung 19
- **Feature Detection:** Findet markante Punkte im Bild (Ecken, Kanten). Algorithmen: Harris, FAST
- **Feature Matching:** Erkennt gefundene Punkte in neuen Bildern wieder für Tracking. Algorithmen: SIFT, FLANN

### Lösung 20
**Problem:** Virtuelle Objekte müssen hinter realen Objekten verschwinden können (Verdeckung).
**Lösung:** **Phantom Shader / Phantom Objects** – unsichtbare 3D-Hüllen der realen Objekte, die nur in den Tiefenpuffer schreiben und so virtuelle Objekte korrekt verdecken.

---

## Notenspiegel (Orientierung)

| Note | Punkte |
|------|--------|
| 1,0 | 95-100 |
| 1,3 | 90-94 |
| 1,7 | 85-89 |
| 2,0 | 80-84 |
| 2,3 | 75-79 |
| 2,7 | 70-74 |
| 3,0 | 65-69 |
| 3,3 | 60-64 |
| 3,7 | 55-59 |
| 4,0 | 50-54 |
| 5,0 | < 50 |

---

**Tipp:** Bei 90 Minuten für 20 Fragen hast du ca. 4-5 Minuten pro Frage. Mit dem Puffer von 30-40 Minuten sogar 6-7 Minuten pro Frage. Entspann dich und lies die Fragen sorgfältig!
