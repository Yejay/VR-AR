# VR & AR Klausurvorbereitung – Kompletter Lernleitfaden

> **Prüfung:** 02.12.2025, 12:15–13:45 Uhr (90 Min)  
> **Format:** ca. 20 Fragen (Definitionen, Erklärungen, Eigenschaften nennen)  
> **Hilfsmittel:** Keine (kein Handy, keine Smartwatch)  
> **Wichtig:** Stift (nicht rot!), evtl. Extrablatt mitbringen

---

## Antwort-Strategie

| Fragetyp | Was ist gefordert? | Beispiel |
|----------|-------------------|----------|
| **"Nennen Sie..."** | Stichpunkte/Begriffe aufzählen | "Nennen Sie 3 Komponenten einer IMU" → Accelerometer, Gyroskop, Magnetometer |
| **"Erläutern/Erklären Sie..."** | Mind. 2 Sätze mit Erklärung | "Erläutern Sie Stereoscopic Rendering" → Vollständige Erklärung des Konzepts |
| **"Was ist...?"** | Definition (1 Satz) + 2-3 Eigenschaften | "Was ist AR?" → Definition + 3 Eigenschaften nach Azuma |

---

# Teil A: Themen-Zusammenfassung

---

## 1. XR Grundlagen & Spektrum (Milgram)

### Das Reality-Virtuality Continuum

Das Spektrum beschreibt den Übergang von realer zu virtueller Umgebung:

```
Real Environment ←——— Mixed Reality ———→ Virtual Environment
        ↑                                        ↑
   Augmented Reality                      Virtual Reality
```

### Definitionen der XR-Technologien

| Begriff | Definition | Kernmerkmal |
|---------|-----------|-------------|
| **XR (Extended Reality)** | Sammelbegriff für alle immersiven Technologien | Umbrella Term für VR, AR, MR |
| **VR (Virtual Reality)** | Nutzer ist komplett in digital generierte Umgebung eingetaucht | Vollständige Abschottung von Realität |
| **AR (Augmented Reality)** | Erweiterung der realen Welt durch digitale Elemente | Realität bleibt sichtbar |
| **MR (Mixed Reality)** | Interaktion zwischen realen und virtuellen Objekten | Virtuelle Objekte reagieren auf reale Physik |

---

## 2. VR Technology

### 2.1 VR Rendering – Besonderheiten

#### Lens Distortion (Linsenverzerrung)

| Aspekt | Beschreibung |
|--------|-------------|
| **Problem** | VR-Linsen (meist Fresnel) erzeugen **Pincushion-Distortion** (Kissenverzerrung) |
| **Lösung** | Software wendet vorher **Barrel-Distortion** (Tonnenverzerrung) an |
| **Ergebnis** | Beide Effekte heben sich gegenseitig auf → korrektes Bild |

#### Chromatic Aberration (Farbfehler)

| Aspekt | Beschreibung |
|--------|-------------|
| **Problem** | Linsen brechen verschiedene Lichtwellenlängen unterschiedlich stark → Farbsäume an Rändern |
| **Lösung** | Verschiebung der Farbkanäle (RGB) beim Rendern im Post-Processing |

#### Stereoscopic Rendering

| Aspekt | Beschreibung |
|--------|-------------|
| **Prinzip** | Zwei Bilder werden gerendert – eines pro Auge, leicht versetzt |
| **Versatz** | Entspricht der Interpupillardistanz (IPD) |
| **Effekt** | Gehirn erzeugt räumlichen 3D-Tiefeneffekt |
| **Nachteil** | Verdoppelt die Render-Last |

### 2.2 VR Rendering – Optimierungen

#### Frustum Culling

| Aspekt | Traditionell | VR-spezifisch |
|--------|-------------|---------------|
| **Form** | Pyramidenförmig | Kegelförmig |
| **Grund** | Rechteckiger Monitor | Runde Linsen |
| **Funktion** | Objekte außerhalb des Sichtfelds werden nicht gerendert |

#### Foveated Rendering

| Aspekt | Beschreibung |
|--------|-------------|
| **Prinzip** | Nur fokussierter Bereich (Fovea) wird scharf gerendert |
| **Peripherie** | Wird unscharf gerendert |
| **Vorteil** | Spart massiv Rechenleistung |
| **Voraussetzung** | Eye-Tracking |
| **Alternative** | Fixed Foveated Rendering (nur Bildmitte scharf, ohne Eye-Tracking) |

#### Space Warp (ASW – Asynchronous Space Warp)

| Aspekt | Beschreibung |
|--------|-------------|
| **Funktion** | Generiert künstliche Zwischenframes bei niedrigen Framerates |
| **Vorteil** | Reduziert benötigte Rechenleistung um bis zu 70% |
| **Zweck** | Verhindert Motion Sickness durch niedrige FPS |

#### Saccade & Change Blindness

| Begriff | Beschreibung |
|---------|-------------|
| **Saccade** | Schnelle Augenbewegung zwischen Fixationspunkten |
| **Change Blindness** | Während Sakkaden oder Blinzeln können Änderungen in der Szene vorgenommen werden, ohne dass der Nutzer es bemerkt |

### 2.3 VR Tracking

#### Degrees of Freedom (DoF)

| Typ | Erfasst | Bewegungen | Beispiel |
|-----|---------|-----------|----------|
| **3DoF** | Nur Rotation | Yaw, Pitch, Roll (Kopfdrehung) | Google Cardboard |
| **6DoF** | Rotation + Position | + Bewegung in x, y, z | Meta Quest 2 |

#### Rotationsachsen

| Achse | Bewegung | Beschreibung |
|-------|----------|-------------|
| **Yaw** | Gieren | Kopf nach links/rechts drehen |
| **Pitch** | Nicken | Kopf nach oben/unten neigen |
| **Roll** | Rollen | Kopf zur Seite kippen |

#### IMU (Inertial Measurement Unit)

| Komponente | Funktion |
|------------|----------|
| **Accelerometer** | Misst lineare Beschleunigung (+ Schwerkraft) |
| **Gyroskop** | Misst Winkelgeschwindigkeit (Rotation) |
| **Magnetometer** | Misst Magnetfelder (Drift-Korrektur / Nordausrichtung) |

#### Tracking-Arten

| Typ | Beschreibung | Vorteile | Nachteile |
|-----|-------------|----------|-----------|
| **Lighthouse (Outside-In)** | Stationäre Laser-Basisstationen im Raum | Sehr präzise | Aufwendiger Aufbau, Verdeckungsprobleme (Occlusion) |
| **Inside-Out** | Kameras am Headset scannen Umgebung (SLAM) | Kein Aufbau nötig, unbegrenzter Raum | Rechenintensiv, Controller-Tracking hinterm Rücken problematisch |

---

## 3. VR Immersion

### 3.1 Kernbegriffe

| Begriff | Typ | Definition |
|---------|-----|-----------|
| **Immersion** | Objektiv/Technisch | Eigenschaft des Systems (FOV, Auflösung, Tracking) – ermöglicht das "Eintauchen" |
| **Presence** | Subjektiv/Psychologisch | Gefühl, wirklich "dort" zu sein ("Being there") |
| **Self-Embodiment** | Psychologisch | Gefühl, dass der virtuelle Körper (Avatar) der eigene ist |

**Wichtiger Zusammenhang:** Keine Presence ohne Immersion möglich – die Technologie schafft die Voraussetzung.

### 3.2 Break-in-Presence (Störungen)

| Typ | Beispiele |
|-----|----------|
| **Ungewollt** | Tracking-Verlust, Lags, Kabelberührung, reale Geräusche |
| **Gewollt** | Chaperone/Guardian-System (Sicherheit bei Wandannäherung) |

### 3.3 Comfort Zone

| Aspekt | Beschreibung |
|--------|-------------|
| **Definition** | Persönlicher Abstand, den Menschen auch in VR benötigen |
| **Verletzung** | NPCs oder Objekte, die zu nah kommen oder "ins Gesicht fliegen" |
| **Folge** | Erzeugt Stress und Unbehagen |
| **Relevanz** | Muss beim VR-Design berücksichtigt werden |

### 3.4 Uncanny Valley

| Aspekt | Beschreibung |
|--------|-------------|
| **Definition** | Akzeptanzlücke bei fast menschenähnlichen Figuren |
| **Effekt** | Figuren wirken gruselig/zombiehaft, wenn sie nicht perfekt menschlich sind |
| **Verlauf** | Akzeptanz sinkt stark, steigt aber wieder bei noch höherem Realismus |

### 3.5 Motion Sickness / Cybersickness

#### Entstehung (Sensory Conflict Theory)

Das Auge sieht Bewegung, aber das Vestibularorgan (Innenohr) spürt Stillstand → Körper interpretiert dies als Vergiftung → Übelkeit.

#### Risikofaktoren

1. Frauen sind anfälliger
2. Kinder sind anfälliger
3. Niedrige Framerate
4. Hohe Latenz
5. Künstliche Rotation/Bewegung
6. Lange Nutzungsdauer
7. Individuelle Anfälligkeit

#### Symptome

Übelkeit, Schwindel, Schweißausbrüche, Kopfschmerzen, Desorientierung

#### Gegenmaßnahmen

1. Hohe Framerate (90+ FPS)
2. Niedrige Latenz
3. Teleportation statt künstlicher Bewegung
4. Statische Referenzpunkte (künstlicher Horizont, Cockpit)
5. Natürliche Bewegung ermöglichen
6. Pausen einlegen

---

## 4. VR Interface

### 4.1 Klassisches UI vs. VR UI

| Aspekt | Klassisches UI | VR UI |
|--------|---------------|-------|
| **Raum** | Screen Space (2D-Overlay) | World Space (3D-positioniert) |
| **Problem in VR** | Fokus-Probleme, Verdeckung | – |
| **Lösung** | – | Floating Interface im 3D-Raum |

### 4.2 Viewing Zones

| Zone | Beschreibung |
|------|-------------|
| **Comfortable Viewing** | Angenehmer Sichtbereich für UI-Platzierung |
| **Peripheral Viewing** | Peripheres Sichtfeld |
| **Rotational Viewing** | Erfordert Kopfdrehung |
| **Curiosity Zone** | Erfordert Körperdrehung |

### 4.3 Interface Objects (Diegetische Interfaces)

| Aspekt | Beschreibung |
|--------|-------------|
| **Definition** | UI-Elemente, die Teil der Spielwelt sind |
| **Beispiele** | Lebensanzeige auf Armbanduhr, Munitionsanzeige auf Waffe |
| **Vorteil** | Erhöht Immersion, keine externen UI-Elemente |

### 4.4 Affordance

| Aspekt | Beschreibung |
|--------|-------------|
| **Definition** | Das Design eines Objekts erklärt seine Funktion |
| **Beispiele** | Griff sieht greifbar aus, Knopf sieht drückbar aus |
| **Relevanz VR** | Nutzer muss intuitiv verstehen, wie Interaktion funktioniert |

---

## 5. VR Interaction

### 5.1 Definition

VR Interaction = Aktion des Nutzers + Reaktion der VR-Anwendung

### 5.2 Universal Simulation Principle (Lavalle)

Jede Interaktion der realen Welt kann in VR simuliert werden (Greifen, Werfen, Schieben, Drücken etc.)

### 5.3 Feedback-Arten

| Typ | Beschreibung | Beispiel |
|-----|-------------|----------|
| **Visuell** | Optische Rückmeldung | Objekt leuchtet auf, ändert Farbe |
| **Auditiv** | Akustische Rückmeldung | Sound beim Berühren/Einrasten |
| **Haptisch** | Taktile Rückmeldung | Controller-Vibration (Rumble) |

### 5.4 Design Considerations

- Fitting Interactions: Interaktionen müssen zur VR-Welt passen
- Fitting Feedback: Feedback muss zur Aktion passen
- Beispiel: Inventar öffnen durch "auf Gürtel schauen" statt "X drücken"

---

## 6. VR Locomotion

### 6.1 Kernproblem

| Problem | Beschreibung |
|---------|-------------|
| **Virtuelle Welt** | Theoretisch unbegrenzt groß |
| **Reale Welt** | Physischer Raum ist begrenzt |
| **Herausforderung** | Bewegung ohne Motion Sickness ermöglichen |

### 6.2 Setup-Varianten

| Variante | Beschreibung |
|----------|-------------|
| **Standing VR** | Nutzer steht, kann sich leicht bewegen |
| **Seated VR** | Nutzer sitzt (z.B. Rennsimulation) |
| **Natural Walking** | 1-zu-1 Bewegung (beste Immersion, aber raumbegrenzt) |

### 6.3 Teleportation

| Typ | Beschreibung | Vor-/Nachteile |
|-----|-------------|----------------|
| **Blink** | Bildschirm wird schwarz → neuer Ort | Sehr komfortabel, aber kurzer Orientierungsverlust |
| **Shift/Dash** | Schnelles Gleiten zum Zielort | Bessere Orientierung, höheres Motion-Sickness-Risiko |

### 6.4 Passive Locomotion Techniken

#### Impossible Spaces

| Aspekt | Beschreibung |
|--------|-------------|
| **Prinzip** | Virtuelle Räume überlappen sich (real nicht möglich) |
| **Konzept** | Ignoriert euklidische Geometrie |
| **Nutzen** | Begrenzten physischen Raum besser nutzen |

#### Redirected Walking (RDW)

| Aspekt | Beschreibung |
|--------|-------------|
| **Prinzip** | Nutzer wird unmerklich manipuliert (läuft im Kreis, denkt er läuft geradeaus) |
| **Grundlage** | Menschen bemerken kleine Abweichungen zwischen visueller und physischer Bewegung nicht |

#### RDW Gain-Typen

| Gain | Beschreibung | Beispiel |
|------|-------------|----------|
| **Rotation Gain** | Virtuelle Rotation ≠ reale Rotation | Real 90° → Virtuell 100° |
| **Translation Gain** | Virtuelle Strecke ≠ reale Strecke | Real 1m → Virtuell 1.2m |
| **Curvature Gain** | Kurve fühlt sich wie Gerade an | Nutzer läuft Kurve, sieht Gerade |

#### Change Blindness

Änderungen in der Welt vornehmen, wenn der Nutzer blinzelt oder das Auge schnell bewegt (Saccade).

---

## 7. AR Overview

### 7.1 Definition nach Azuma – Die 3 Säulen

1. **Kombiniert Realität und Virtualität**
2. **Interaktiv in Echtzeit**
3. **Registriert im 3D-Raum** (räumlich verankert)

### 7.2 AR Device-Typen

#### Optical See-Through (z.B. HoloLens, Magic Leap)

| Vorteile | Nachteile |
|----------|-----------|
| Reale Welt in nativer Auflösung | Kleines FOV für virtuelle Objekte |
| Keine Latenz bei Realitätsdarstellung | Schwarz kann nicht dargestellt werden (wird transparent) |
| Sicher bei Stromausfall | Schwierige Okklusion |

#### Video See-Through (z.B. Quest 3, Apple Vision Pro)

| Vorteile | Nachteile |
|----------|-----------|
| Großes FOV | Latenz bei Realitätsdarstellung |
| Okklusion einfach umsetzbar | Auflösung durch Kamerasensor begrenzt |
| Schwarzwerte darstellbar (pixelgenaue Kontrolle) | Unsicher bei Stromausfall |

#### Spatial AR (Projection Mapping)

| Aspekt | Beschreibung |
|--------|-------------|
| **Prinzip** | Beamer projizieren auf echte Objekte |
| **Vorteil** | Keine Brille nötig |

---

## 8. AR Spatial Understanding

### 8.1 Feature Extraction

#### Feature Detection

| Aspekt | Beschreibung |
|--------|-------------|
| **Funktion** | Finden von markanten Punkten (Ecken, Kanten) |
| **Algorithmen** | Harris Corner Detection, FAST, SIFT |

#### Feature Matching

| Aspekt | Beschreibung |
|--------|-------------|
| **Funktion** | Wiedererkennen der Punkte in neuen Bildern |
| **Algorithmen** | SIFT (skaleninvariant), FLANN |

#### Unterschied Detection vs. Matching

- **Detection:** Punkte im Bild finden
- **Matching:** Gefundene Punkte in anderen Bildern wiedererkennen

### 8.2 Marker Tracking

#### Fiducial Marker

| Aspekt | Beschreibung |
|--------|-------------|
| **Definition** | Schwarz-weiß Muster (QR-Code-ähnlich) |
| **Beispiele** | ARToolKit, ARTag, AprilTag, ArUco |
| **Eigenschaften** | Extrem schnell, robust, präzise (Größe/Form bekannt) |

### 8.3 Plane Detection

| Aspekt | Beschreibung |
|--------|-------------|
| **Methode** | Gruppen von Punkten erkennen, die in einer Ebene liegen |
| **Tracking** | Feature Movement Tracking |
| **Typen** | Horizontale (Boden, Tisch) und vertikale (Wand) Flächen |
| **Nutzen** | Virtuelle Objekte können auf Flächen platziert werden |

### 8.4 Render Challenges

#### Occlusion (Verdeckung)

| Problem | Lösung |
|---------|--------|
| Virtuelles Objekt muss hinter realem verschwinden | **Phantom Shader / Phantom Objects** |
| – | Unsichtbare 3D-Hüllen der realen Objekte, die nur in den Tiefenpuffer schreiben |

#### Lighting

| Problem | Lösung |
|---------|--------|
| Virtuelle Objekte brauchen passende Schatten/Beleuchtung | **Light Estimation** |
| – | Bestimmung der realen Lichtquelle zur korrekten Schattenberechnung |

---

## 9. AR Interaction

### 9.1 Input Types

| Plattform | Input-Methoden |
|-----------|---------------|
| **Mobile** | Touch Input (single + multi), Device Movement (virtuelle Kamera) |
| **HMD** | Hand Tracking, Eye Tracking, Gesten, Controller, Device Movement |
| **Spatial** | Marker Movement, 3D Object Movement |

### 9.2 Output Types

| Plattform | Output-Methoden |
|-----------|----------------|
| **Mobile** | Visual, Audio, Haptics (Vibration) |
| **HMD** | (Stereoscopic) Visual, (Stereo) Audio, Haptics (Hand + HMD Vibration) |

---

# Teil B: Fragenkatalog mit Musterantworten

---

## 1. XR Grundlagen & Spektrum

### Frage 1.1
**Wofür steht XR?**

**Antwort:** XR steht für Extended Reality.

---

### Frage 1.2
**Erklären Sie XR.**

**Antwort:** XR (Extended Reality) ist der Sammelbegriff für alle immersiven Technologien. Es umfasst VR (Virtual Reality), AR (Augmented Reality) und MR (Mixed Reality). XR beschreibt das gesamte Spektrum zwischen realer und virtueller Umgebung.

---

### Frage 1.3
**Nennen Sie die drei Technologien, die unter XR fallen, und beschreiben Sie jeweils in einem Satz, was sie bedeuten.**

**Antwort:**
- **VR (Virtual Reality):** Nutzer ist komplett in eine digital generierte Umgebung eingetaucht, die reale Welt wird vollständig ausgeblendet.
- **AR (Augmented Reality):** Die reale Welt wird durch digitale Elemente erweitert, wobei die Realität sichtbar bleibt.
- **MR (Mixed Reality):** Virtuelle und reale Objekte interagieren miteinander, z.B. reagiert ein virtuelles Objekt auf die Physik der realen Welt.

---

## 2. VR Rendering

### Frage 2.1
**Nennen Sie drei Besonderheiten des VR-Renderings gegenüber herkömmlichem Rendering.**

**Antwort:** Lens Distortion (und inverse Distortion), Chromatic Aberration, Stereoscopic Rendering.

---

### Frage 2.2
**Erläutern Sie, was man unter Stereoscopic Rendering versteht.**

**Antwort:** Beim stereoskopischen Rendering werden zwei leicht versetzte Bilder gerendert – eines für jedes Auge. Der Versatz entspricht der Interpupillardistanz (IPD), also dem Abstand zwischen den Augen. Dadurch entsteht im Gehirn ein räumlicher 3D-Tiefeneffekt, wie wir ihn auch beim natürlichen Sehen haben. Nachteil ist die verdoppelte Render-Last.

---

### Frage 2.3
**Erklären Sie das Problem der Lens Distortion und wie es gelöst wird.**

**Antwort:** VR-Linsen (meist Fresnel-Linsen) erzeugen eine Pincushion-Distortion (Kissenverzerrung), wodurch das Bild verzerrt wahrgenommen würde. Die Lösung: Die Software wendet beim Rendern eine Barrel-Distortion (Tonnenverzerrung) an. Da beide Verzerrungen entgegengesetzt sind, heben sie sich gegenseitig auf und das Bild erscheint korrekt.

---

### Frage 2.4
**Was ist Chromatic Aberration und wie wird sie korrigiert?**

**Antwort:** Chromatic Aberration ist ein Farbfehler, bei dem Linsen verschiedene Lichtwellenlängen (Farben) unterschiedlich stark brechen. Dadurch entstehen Farbsäume an den Bildrändern. Die Korrektur erfolgt durch Verschiebung der einzelnen Farbkanäle (RGB) beim Rendern im Post-Processing.

---

### Frage 2.5
**Was ist Frustum Culling und worin unterscheidet sich VR Frustum Culling vom traditionellen?**

**Antwort:** Frustum Culling ist eine Optimierungstechnik, bei der Objekte außerhalb des Sichtfelds (Frustum) nicht gerendert werden. Traditionell ist das Frustum pyramidenförmig, da Monitore rechteckig sind. Bei VR ist das Frustum kegelförmig, weil die Linsen rund sind.

---

### Frage 2.6
**Erläutern Sie das Prinzip von Foveated Rendering.**

**Antwort:** Beim Foveated Rendering wird nur der Bereich scharf gerendert, den das Auge gerade fokussiert (Fovea). Der periphere Bereich wird mit geringerer Auflösung gerendert. Dies spart massiv Rechenleistung. Voraussetzung ist Eye-Tracking, um zu wissen, wohin der Nutzer schaut. Ohne Eye-Tracking gibt es "Fixed Foveated Rendering", bei dem nur die Bildmitte scharf gerendert wird.

---

### Frage 2.7
**Was ist Space Warp (ASW)?**

**Antwort:** Space Warp (Asynchronous Space Warp) ist eine Technik, die künstliche Zwischenframes generiert, wenn die GPU die Ziel-Framerate (z.B. 90Hz) nicht halten kann. Dadurch wird die benötigte Rechenleistung um bis zu 70% reduziert und Motion Sickness durch niedrige Framerates wird verhindert.

---

## 3. VR Tracking

### Frage 3.1
**Erklären Sie den Unterschied zwischen 3DoF und 6DoF.**

**Antwort:** 3DoF (3 Degrees of Freedom) erfasst nur die Rotation des Kopfes in drei Achsen: Yaw (links/rechts drehen), Pitch (oben/unten neigen) und Roll (zur Seite kippen). Die Position im Raum wird nicht erfasst. 6DoF (6 Degrees of Freedom) erfasst zusätzlich zur Rotation auch die Position im Raum (Bewegung in x, y, z). Beispiel: Google Cardboard hat 3DoF, Meta Quest 2 hat 6DoF.

---

### Frage 3.2
**Was ist eine IMU und aus welchen Komponenten besteht sie?**

**Antwort:** IMU steht für Inertial Measurement Unit – ein Sensor zur Bewegungserkennung. Sie besteht aus drei Komponenten:
- **Accelerometer:** Misst lineare Beschleunigung (inklusive Schwerkraft)
- **Gyroskop:** Misst Winkelgeschwindigkeit (Rotation)
- **Magnetometer:** Misst Magnetfelder zur Drift-Korrektur und Nordausrichtung

---

### Frage 3.3
**Nennen Sie zwei Tracking-Arten und jeweils einen Vor- und Nachteil.**

**Antwort:**
- **Lighthouse (Outside-In):** Stationäre Laser-Basisstationen im Raum. Vorteil: Sehr präzise. Nachteil: Aufwendiger Aufbau und Verdeckungsprobleme möglich.
- **Inside-Out:** Kameras am Headset scannen die Umgebung. Vorteil: Kein Aufbau nötig, theoretisch unbegrenzter Bewegungsraum. Nachteil: Rechenintensiv, Controller-Tracking hinter dem Rücken problematisch.

---

### Frage 3.4
**Nennen Sie die drei Rotationsachsen und beschreiben Sie die zugehörige Bewegung.**

**Antwort:**
- **Yaw (Gieren):** Kopf nach links/rechts drehen
- **Pitch (Nicken):** Kopf nach oben/unten neigen
- **Roll (Rollen):** Kopf zur Seite kippen

---

## 4. VR Immersion

### Frage 4.1
**Was ist Immersion?**

**Antwort:** Immersion ist eine objektive, technische Eigenschaft des VR-Systems. Sie beschreibt die Qualität der technischen Faktoren wie Field of View (FOV), Auflösung, Tracking-Qualität und Framerate. Die Technologie ermöglicht das "Eintauchen" in die virtuelle Welt. Auch andere Medien wie Bücher können Immersion erzeugen.

---

### Frage 4.2
**Was ist Presence?**

**Antwort:** Presence ist das subjektive, psychologische Gefühl, wirklich "dort" zu sein ("Being there"). Es ist die persönliche Wahrnehmung, sich tatsächlich in der virtuellen Umgebung zu befinden, obwohl man weiß, dass man es nicht ist.

---

### Frage 4.3
**Erläutern Sie den Unterschied zwischen Immersion und Presence.**

**Antwort:** Immersion ist objektiv und technisch – sie beschreibt die Eigenschaften des Systems (FOV, Auflösung, Tracking). Presence ist subjektiv und psychologisch – das Gefühl, wirklich "dort" zu sein. Wichtig: Ohne Immersion kann keine Presence entstehen. Die Technologie (Immersion) schafft erst die Voraussetzung für das Gefühl (Presence).

---

### Frage 4.4
**Was ist Self-Embodiment?**

**Antwort:** Self-Embodiment ist das Gefühl, dass der virtuelle Körper (Avatar) der eigene Körper ist. Der Nutzer nimmt den virtuellen Körper als Teil von sich selbst wahr und identifiziert sich mit ihm.

---

### Frage 4.5
**Nennen Sie drei Gründe für ungewollte Unterbrechungen der Presence (Break-in-Presence).**

**Antwort:** Tracking-Verlust, Lags/hohe Latenz, Kabelberührung, reale Geräusche von außen, niedrige Framerate.

---

### Frage 4.6
**Wann will man die Presence absichtlich unterbrechen?**

**Antwort:** Aus Sicherheitsgründen, z.B. durch das Chaperone/Guardian-System. Dieses zeigt Gitterlinien an, wenn sich der Nutzer einer realen Wand oder einem Hindernis nähert, um Kollisionen zu verhindern.

---

## 5. Comfort Zone & Uncanny Valley

### Frage 5.1
**Was versteht man unter Comfort Zone in VR und warum ist sie wichtig?**

**Antwort:** Die Comfort Zone ist der persönliche Abstand, den Menschen auch in VR benötigen. Wenn virtuelle NPCs, Charaktere oder Objekte zu nah kommen (z.B. "ins Gesicht fliegen" oder "Nacken atmen"), erzeugt das Stress und Unbehagen beim Nutzer. VR-Designer müssen diese Zone respektieren, um eine angenehme Erfahrung zu schaffen.

---

### Frage 5.2
**Erklären Sie das Konzept des Uncanny Valley.**

**Antwort:** Das Uncanny Valley beschreibt eine Akzeptanzlücke bei fast menschenähnlichen Figuren. Wenn virtuelle Charaktere sehr menschlich aussehen, aber nicht perfekt sind, wirken sie gruselig, unheimlich oder zombiehaft. Die Akzeptanz sinkt stark ab. Wird die Darstellung noch realistischer und perfekter, steigt die Akzeptanz wieder an.

---

## 6. Motion Sickness / Cybersickness

### Frage 6.1
**Erklären Sie, wie Motion Sickness in VR entsteht.**

**Antwort:** Motion Sickness entsteht durch einen sensorischen Konflikt (Sensory Conflict Theory): Das Auge sieht Bewegung in der virtuellen Welt, aber das Vestibularorgan (Innenohr) spürt Stillstand, da der Körper sich real nicht bewegt. Der Körper interpretiert diese Diskrepanz als Vergiftungssymptom und reagiert mit Übelkeit.

---

### Frage 6.2
**Nennen Sie fünf Risikofaktoren für Motion Sickness.**

**Antwort:**
1. Frauen sind statistisch anfälliger
2. Kinder sind anfälliger
3. Niedrige Framerate (unter 90 FPS)
4. Hohe Latenz
5. Künstliche Rotation oder Bewegung (Smooth Locomotion)

---

### Frage 6.3
**Nennen Sie Symptome von Motion Sickness.**

**Antwort:** Übelkeit, Schwindel, Schweißausbrüche, Kopfschmerzen, Desorientierung, allgemeines Unwohlsein.

---

### Frage 6.4
**Nennen Sie vier Maßnahmen zur Reduzierung von Motion Sickness.**

**Antwort:**
1. Hohe Framerate (90+ FPS)
2. Teleportation statt künstlicher Smooth-Bewegung
3. Statische Referenzpunkte (künstlicher Horizont, Cockpit, Nasenmodell)
4. Natürliche 1-zu-1 Bewegung ermöglichen

---

## 7. VR Interface

### Frage 7.1
**Was muss man beim Design von VR User Interfaces im Vergleich zu klassischen UIs beachten?**

**Antwort:** Klassische 2D-Overlays (Screen Space UI) funktionieren in VR schlecht, da sie Fokus-Probleme und Verdeckungen verursachen. VR UIs müssen im 3D-Raum positioniert sein (World Space / Floating Interface). Sie sollten im angenehmen Sichtbereich (Comfortable Viewing) platziert werden, um Nackenschmerzen durch ständiges Kopfdrehen zu vermeiden.

---

### Frage 7.2
**Was sind Interface Objects (diegetische Interfaces) in VR?**

**Antwort:** Interface Objects sind UI-Elemente, die als Teil der Spielwelt integriert sind. Beispiele: Eine Lebensanzeige auf einer Armbanduhr des Charakters oder eine Munitionsanzeige direkt auf der Waffe. Der Vorteil ist eine erhöhte Immersion, da die Informationen nicht als externe UI-Elemente wahrgenommen werden.

---

### Frage 7.3
**Was bedeutet Affordance im Kontext von VR?**

**Antwort:** Affordance bedeutet, dass das Design eines Objekts seine Funktion kommuniziert. Ein Griff sieht greifbar aus, ein Knopf sieht drückbar aus, ein Hebel sieht ziehbar aus. In VR ist dies besonders wichtig, da Nutzer ohne Anleitung intuitiv verstehen müssen, wie sie mit Objekten interagieren können.

---

### Frage 7.4
**Nennen Sie die vier Viewing Zones bei VR Interfaces.**

**Antwort:**
1. **Comfortable Viewing:** Angenehmer Sichtbereich ohne Kopfbewegung
2. **Peripheral Viewing:** Peripheres Sichtfeld (Augenwinkel)
3. **Rotational Viewing:** Erfordert Kopfdrehung
4. **Curiosity Zone:** Erfordert Körperdrehung

---

## 8. VR Interaction

### Frage 8.1
**Definieren Sie VR Interaction.**

**Antwort:** VR Interaction besteht aus zwei Komponenten: einer Aktion des Nutzers und der entsprechenden Reaktion der VR-Anwendung auf diese Aktion.

---

### Frage 8.2
**Was besagt das Universal Simulation Principle nach Lavalle?**

**Antwort:** Das Universal Simulation Principle besagt, dass jede Interaktion der realen Welt in VR simuliert werden kann. Dazu gehören natürliche Aktionen wie Greifen, Werfen, Schieben, Drücken, Ziehen und alle anderen physischen Interaktionen.

---

### Frage 8.3
**Nennen Sie drei Feedback-Arten bei VR Interactions und geben Sie jeweils ein Beispiel.**

**Antwort:**
- **Visuell:** Objekt leuchtet auf oder ändert die Farbe bei Berührung (Highlight)
- **Auditiv:** Sound beim Berühren, Aufheben oder Einrasten eines Objekts
- **Haptisch:** Vibration des Controllers (Rumble) bei Kollision oder Interaktion

---

## 9. VR Locomotion

### Frage 9.1
**Was ist das Kernproblem bei VR Locomotion?**

**Antwort:** Die virtuelle Welt ist theoretisch unbegrenzt groß, während der physische Raum des Nutzers stark begrenzt ist (z.B. ein Wohnzimmer). Es muss eine Lösung gefunden werden, wie man sich in einer unendlichen virtuellen Welt frei bewegen kann, ohne dabei Motion Sickness zu erzeugen.

---

### Frage 9.2
**Erklären Sie den Unterschied zwischen Blink- und Shift/Dash-Teleportation.**

**Antwort:**
- **Blink:** Der Bildschirm wird kurz schwarz und der Nutzer erscheint am neuen Ort. Sehr komfortabel und Motion-Sickness-frei, aber man verliert kurz die räumliche Orientierung.
- **Shift/Dash:** Der Nutzer gleitet schnell zum Zielort, die Bewegung ist sichtbar. Bessere räumliche Orientierung, aber höheres Motion-Sickness-Risiko.

---

### Frage 9.3
**Was sind Impossible Spaces?**

**Antwort:** Impossible Spaces sind virtuelle Räume, die sich überlappen, was in der realen Welt nicht möglich wäre. Sie ignorieren die euklidische Geometrie, um den begrenzten physischen Raum besser zu nutzen. Der Nutzer bemerkt nicht, dass er denselben realen Raum mehrfach durchquert, während er verschiedene virtuelle Räume erkundet.

---

### Frage 9.4
**Erläutern Sie das Prinzip von Redirected Walking.**

**Antwort:** Bei Redirected Walking wird der Nutzer unmerklich manipuliert. Er läuft beispielsweise in der Realität im Kreis, glaubt aber virtuell geradeaus zu gehen. Dies basiert auf der Beobachtung, dass Menschen kleine Abweichungen zwischen visueller und physischer Bewegung nicht bemerken.

---

### Frage 9.5
**Nennen und erklären Sie drei Gain-Typen bei Redirected Walking.**

**Antwort:**
- **Rotation Gain:** Virtuelle Rotation weicht von realer ab. Beispiel: Nutzer dreht sich real 90°, virtuell werden 100° angezeigt.
- **Translation Gain:** Virtuelle Strecke weicht von realer ab. Beispiel: Nutzer läuft real 1m, virtuell werden 1.2m zurückgelegt.
- **Curvature Gain:** Eine Kurve fühlt sich wie eine Gerade an. Nutzer läuft real eine Kurve, sieht virtuell aber einen geraden Weg.

---

## 10. AR Overview

### Frage 10.1
**Nennen Sie die drei definierenden Eigenschaften von AR nach Azuma.**

**Antwort:**
1. Kombiniert Realität und Virtualität
2. Interaktiv in Echtzeit
3. Registriert im 3D-Raum (räumlich verankert)

---

### Frage 10.2
**Was ist kein AR?**

**Antwort:** Einfache 2D-Overlays ohne räumliche Verankerung sind kein AR. Beispiel: Ein Navigationspfeil, der fest auf dem Bildschirm liegt und nicht im 3D-Raum registriert ist. AR erfordert, dass digitale Objekte räumlich in der realen Welt verankert sind.

---

### Frage 10.3
**Erklären Sie den Unterschied zwischen Optical See-Through und Video See-Through.**

**Antwort:**
- **Optical See-Through** (z.B. HoloLens): Der Nutzer sieht die reale Welt direkt durch transparente Gläser, virtuelle Objekte werden auf diese eingeblendet. Vorteile: Keine Latenz, native Auflösung der Realität, sicher bei Stromausfall. Nachteile: Kleines FOV für virtuelle Objekte, Schwarz nicht darstellbar, schwierige Okklusion.
- **Video See-Through** (z.B. Quest 3): Kameras filmen die Realität, die dann zusammen mit virtuellen Objekten auf dem Display angezeigt wird. Vorteile: Großes FOV, Okklusion einfach umsetzbar, Schwarz darstellbar. Nachteile: Latenz bei der Realitätsdarstellung, Auflösung durch Kamera begrenzt.

---

### Frage 10.4
**Was ist Spatial AR?**

**Antwort:** Bei Spatial AR projizieren Beamer direkt auf echte Objekte oder Oberflächen (Projection Mapping). Der große Vorteil ist, dass keine Brille oder kein Headset benötigt wird.

---

## 11. AR Spatial Understanding

### Frage 11.1
**Was ist der Unterschied zwischen Feature Detection und Feature Matching?**

**Antwort:**
- **Feature Detection:** Findet markante Punkte im Bild wie Ecken und Kanten. Algorithmen: Harris Corner Detection, FAST.
- **Feature Matching:** Erkennt die gefundenen Punkte in neuen Bildern wieder, um Tracking zu ermöglichen. Algorithmen: SIFT (skaleninvariant), FLANN.

---

### Frage 11.2
**Was sind Fiducial Marker und welche Eigenschaften haben sie?**

**Antwort:** Fiducial Marker sind schwarz-weiße Muster, ähnlich wie QR-Codes, die speziell für AR-Tracking entwickelt wurden. Beispiele sind ARToolKit, ARTag, AprilTag und ArUco. Eigenschaften: Sie sind extrem schnell, robust und präzise erkennbar, da ihre Größe und Form dem System bekannt sind.

---

### Frage 11.3
**Wie funktioniert Plane Detection?**

**Antwort:** Bei der Plane Detection werden aus einer Punktwolke (Point Cloud) Gruppen von Punkten erkannt, die in einer Ebene liegen. Durch Feature Movement Tracking kann zwischen horizontalen Flächen (Boden, Tisch) und vertikalen Flächen (Wände) unterschieden werden. Dies ermöglicht das Platzieren virtueller Objekte auf realen Oberflächen.

---

### Frage 11.4
**Nennen Sie zwei Render-Challenges bei AR und erklären Sie die Lösungen.**

**Antwort:**
- **Occlusion (Verdeckung):** Problem: Virtuelle Objekte müssen hinter realen Objekten verschwinden können. Lösung: Phantom Shader / Phantom Objects – unsichtbare 3D-Hüllen der realen Objekte, die nur in den Tiefenpuffer schreiben und so virtuelle Objekte verdecken.
- **Lighting:** Problem: Virtuelle Objekte brauchen passende Schatten und Beleuchtung. Lösung: Light Estimation – die reale Lichtquelle wird erkannt und für die Schattenberechnung der virtuellen Objekte verwendet.

---

## 12. AR Interaction

### Frage 12.1
**Nennen Sie drei Input-Typen für AR auf HMDs.**

**Antwort:** Hand Tracking, Eye Tracking, Gesten, Controller, Device Movement (als virtuelle Kamera).

---

### Frage 12.2
**Nennen Sie Input-Typen für mobile AR.**

**Antwort:** Touch Input (Single-Touch und Multi-Touch), Device Movement (Smartphone als virtuelle Kamera).

---

### Frage 12.3
**Nennen Sie Output-Typen für mobile AR und HMD-basierte AR.**

**Antwort:**
- **Mobile:** Visual (Bildschirm), Audio (Lautsprecher), Haptics (Vibration im Gerät)
- **HMD:** Stereoscopic Visual, Stereo Audio, Haptics (Vibration in Controllern und HMD)

---

# Teil C: Schnellreferenz (Cheat Sheet für letzte Wiederholung)

---

## Begriffe zum Auswendiglernen

| Begriff | Kurzdefinition |
|---------|---------------|
| XR | Sammelbegriff für VR/AR/MR |
| VR | Komplett virtuelle Umgebung |
| AR | Realität + digitale Elemente |
| MR | Reale und virtuelle Objekte interagieren |
| Immersion | Technische Eigenschaft des Systems |
| Presence | Subjektives Gefühl "dort zu sein" |
| Self-Embodiment | Avatar fühlt sich wie eigener Körper an |
| Motion Sickness | Übelkeit durch sensorischen Konflikt |
| Affordance | Design erklärt Funktion |
| 3DoF | Nur Rotation |
| 6DoF | Rotation + Position |
| Frustum Culling | Nicht sichtbare Objekte nicht rendern |
| Foveated Rendering | Nur fokussierter Bereich scharf |
| Space Warp | Künstliche Zwischenframes |
| Occlusion | Verdeckung virtueller durch reale Objekte |

## IMU-Komponenten

1. **Accelerometer** → Beschleunigung
2. **Gyroskop** → Rotation
3. **Magnetometer** → Magnetfeld

## AR nach Azuma (3 Säulen)

1. Kombiniert Real + Virtuell
2. Echtzeit-Interaktion
3. 3D-Registrierung

## Motion Sickness Gegenmaßnahmen

1. Hohe FPS (90+)
2. Teleportation
3. Statische Referenzpunkte
4. Niedrige Latenz

## VR Rendering Besonderheiten

1. Lens Distortion (→ Barrel Distortion)
2. Chromatic Aberration (→ RGB-Shift)
3. Stereoscopic Rendering (→ 2 Bilder)

## Redirected Walking Gains

1. **Rotation** → 90° real = 100° virtuell
2. **Translation** → 1m real = 1.2m virtuell
3. **Curvature** → Kurve = Gerade

---

**Viel Erfolg bei der Klausur, Yejay!** 🎯
