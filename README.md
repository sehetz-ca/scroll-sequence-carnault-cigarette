# 🌀 Carnault Cigarette Scroll Sequence

> **Animated Scroll Interaction for Shopify**  
> Smooth, transparent WebP frame-by-frame animation controlled by scroll position.

---

## 🎬 Scroll Behaviour
─────────────────────────────────────────────
**User scrollt ↓ → Animation spielt Frame für Frame ab**

- Beim Betreten der Section wird die erste Frame geladen.
- Während des Scrollens wechselt GSAP automatisch zwischen den 60 `.webp`-Frames.
- Beim Verlassen der Section bleibt der letzte Frame stehen.
- Die Animation läuft **frame-genau synchron zur Scrollposition** (scrubbing).
- Die Bilder werden aus einem externen **GitHub-CDN (jsDelivr)** geladen.

---

## 🧠 Technical Overview
─────────────────────────────────────────────

| Component | Beschreibung |
|------------|--------------|
| **Platform** | Shopify (Custom Liquid Section) |
| **Animation** | Scroll-basierte Frame-Interpolation (GSAP + ScrollTrigger) |
| **Media Format** | `.webp` (exportiert mit Alpha/Transparenz) |
| **Scroll Control** | `gsap.ScrollTrigger` (progress → image index) |
| **Performance** | Lazy preloading in kleinen Batches (10 Frames / 150ms Delay) |
| **Transparency** | Unterstützt → Overlay möglich auf Hintergrund-Video oder Farbe |

---

## ⚙️ Tech Stack
─────────────────────────────────────────────

| Tool | Zweck |
|------|-------|
| **After Effects** | Animationserstellung |
| **Fnord WebM Plugin (V9)** | Alpha-Export möglich |
| **Photoshop / AE Render Queue** | Einzelbilder exportieren |
| **ImageMagick / TinyPNG** | Optionales Frame-Komprimieren |
| **GitHub + jsDelivr CDN** | Kostenfreier, performanter Bild-Host |
| **GSAP 3.12.5** | Scroll-Animation + Frame-Interpolation |
| **Shopify Section** | Integration in Theme Editor (voll editierbar) |

---

## 🖼️ File Naming Convention
─────────────────────────────────────────────

Alle Frames folgen einem nummerierten Pattern:
CA_scroll_animation_test_01.webp
CA_scroll_animation_test_02.webp
...
CA_scroll_animation_test_60.webp

yaml
Code kopieren

👉 Stelle sicher, dass jede Datei exakt 2-stellig nummeriert ist (`01`, `02`, … `60`).  
Diese Struktur wird im Liquid-Code automatisch erkannt und fortlaufend geladen.

---

## 🌐 Hosting via jsDelivr CDN
─────────────────────────────────────────────

GitHub-Repo-Dateien werden automatisch über CDN bereitgestellt:

**Base Path:**
https://cdn.jsdelivr.net/gh/sehetz-ca/scroll-sequence-carnault-cigarette/

makefile
Code kopieren

**Beispiel-Frame:**
https://cdn.jsdelivr.net/gh/sehetz-ca/scroll-sequence-carnault-cigarette/CA_scroll_animation_test_01.webp

yaml
Code kopieren

→ Shopify lädt diese Frames direkt aus diesem Pfad.

---

## 🧩 Shopify Integration
─────────────────────────────────────────────

**Section:**  
`/sections/scroll-image-sequence.liquid`

**Editor Settings:**
- `Base GitHub CDN URL` → `https://cdn.jsdelivr.net/gh/sehetz-ca/scroll-sequence-carnault-cigarette/`
- `Scroll Duration` → z. B. `300vh`

**Liquid Schema-Auszug:**
```json
{
  "type": "text",
  "id": "repo_base_url",
  "label": "Base GitHub CDN URL",
  "default": "https://cdn.jsdelivr.net/gh/sehetz-ca/scroll-sequence-carnault-cigarette/"
}
🧩 Scroll Behaviour in Shopify
─────────────────────────────────────────────

scss
Code kopieren
User scrollt ↓
↓
GSAP ScrollTrigger berechnet Scroll-Progress (0 → 1)
↓
progress × totalFrames → Frame Index
↓
<IMG> src aktualisiert auf passendes Frame
Kein Autoplay, kein Video-Tag — alles statisch + performant.

Die Scrollhöhe ist in der Section über duration_vh (z. B. 300 vh) definiert.

💡 Export Workflow (After Effects)
─────────────────────────────────────────────

Komposition:

Frame Rate: 60 fps (empfohlen)

Hintergrund: Transparent

Länge: so kurz wie nötig

Export über Adobe Media Encoder:

Format: WebM

Codec: VP9

Channels: RGBA (mit Alpha)

Framerate: fix auf 60 fps

Keyframe Distance: 1

Bitrate: 10–20 Mbps

Farbprofil: Rec.709

Optional:

Einzelbilder mit ffmpeg erzeugen:

bash
Code kopieren
ffmpeg -i animation.webm CA_scroll_animation_test_%02d.webp
oder direkt aus AE Render Queue exportieren.

🧩 Credits
─────────────────────────────────────────────

Developer: @sehetz-ca
Design & Motion: Carnault Creative
Technology: GSAP + Shopify + jsDelivr CDN

🧰 Example Usage
─────────────────────────────────────────────

liquid
Code kopieren
<section id="section-scroll-sequence-example">
  <img src="https://cdn.jsdelivr.net/gh/sehetz-ca/scroll-sequence-carnault-cigarette/CA_scroll_animation_test_01.webp" />
</section>
🧾 License
─────────────────────────────────────────────
This project is part of the Carnault Shopify Theme System.
All assets © Carnault, used for internal design & development purposes only.
