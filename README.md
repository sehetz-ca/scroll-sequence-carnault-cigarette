# 🌀 Carnault Cigarette Scroll Sequence

Smooth scroll-controlled image sequence for Shopify.  
Each frame is a transparent `.webp` exported from After Effects.  
Used inside the custom Shopify section:  
`sections/scroll-image-sequence.liquid`

---

## 📜 Scroll Behaviour
────────────────────────────
**User scrolls ↓ → animation scrubs through 60 frames**  
- Controlled via GSAP ScrollTrigger  
- Frames are loaded from GitHub (jsDelivr CDN)  
- No video — pure image sequence for transparency and performance  

Example frame path:  
https://cdn.jsdelivr.net/gh/sehetz-ca/scroll-sequence-carnault-cigarette/CA_scroll_animation_test_01.webp

markdown
Code kopieren

---

## ⚙️ After Effects Export Guide
────────────────────────────
1. **Install the WebM plugin (by fnord):**  
   👉 https://fnord.com/webm/

2. **In After Effects → Add your comp to Adobe Media Encoder**

3. **Export settings:**
   - **Format:** WebM  
   - **Video codec:** VP9  
   - **Channels:** RGBA *(includes Alpha)*  
   - **Framerate:** 60 fps (fixed)  
   - **Keyframe interval:** 1  
   - **Bitrate:** ~10–20 Mbps  
   - **Color space:** Rec.709  
   - **Resolution:** match comp (e.g. 1920×1080)

4. **Optional — export image sequence via FFmpeg:**
   ```bash
   ffmpeg -i animation.webm CA_scroll_animation_test_%02d.webp
All exported frames (01–60) go in this repo root.

🧠 Tech Stack
────────────────────────────

Shopify Section (Liquid + GSAP)

jsDelivr (CDN for GitHub images)

60 .webp frames (with alpha)

Smooth interpolation via ScrollTrigger

🧩 Used in Shopify Section
/sections/scroll-image-sequence.liquid

json
Code kopieren
{
  "repo_base_url": "https://cdn.jsdelivr.net/gh/sehetz-ca/scroll-sequence-carnault-cigarette/"
}
