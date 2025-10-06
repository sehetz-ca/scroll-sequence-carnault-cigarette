# 🌀 Carnault Cigarette Scroll Sequence

Smooth scroll-controlled image sequence for Shopify.  
Each frame is a transparent `.webp` exported from After Effects.  
Used inside the custom Shopify section:  
`sections/scroll-image-sequence.liquid`

---

## 📜 Scroll Behaviour
**User scrolls ↓ → animation scrubs through 60 frames**  
- Controlled via GSAP ScrollTrigger  
- Frames are loaded from GitHub (jsDelivr CDN)  
- No video — pure image sequence for transparency and performance  

Example frame path:  
https://cdn.jsdelivr.net/gh/sehetz-ca/scroll-sequence-carnault-cigarette/CA_scroll_animation_test_01.webp


---

## ⚙️ After Effects Export Guide

**MAIN** 
**PNG-SEQUENCE** 
**Export image sequence via FFmpeg:**
   - **Export with media encoder to png Sequence**   
   - **Convert png images with photoshop actions to WebM** 

**ALTERNATIVE**
**VIDEO** 
**For Video Install the WebM plugin (by fnord):**  
👉 https://fnord.com/webm/
**Export settings:**
   - **Format:** WebM  
   - **Video codec:** VP9  
   - **Channels:** RGBA *(includes Alpha)*  
   - **Framerate:** 60 fps (fixed)  
   - **Keyframe interval:** 1  
   - **Bitrate:** ~10–20 Mbps  
   - **Color space:** Rec.709  
   - **Resolution:** match comp (e.g. 1920×1080)

  

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
