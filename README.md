# TaskMate
# TaskMate (Mock) — Autonomy‑First Demo

A zero‑setup, single‑file HTML prototype that demonstrates **excellent usability** and a **clear UX flow** for planning, attention‑risk cues, and a focus timer — with **ethics‑by‑design** controls that preserve user autonomy.

## ✨ Highlights
- **Single file, no build**: pure HTML + Tailwind CDN + vanilla JS.
- **Goal → Plan → Focus → Done**: linear, low‑friction flow.
- **Autonomy‑first settings**: users control **if/when/how** guidance appears.
- **Local‑only**: all preferences persist via `localStorage`; no cloud sync.
- **Accessible defaults**: status toast uses `role="status"` and `aria-live="polite"`.

## 🧩 Core Features
- **Planner**: enter a goal, click **Generate Plan (AI)** for atomic subtasks; or add your own (title + minutes).
- **Plan list**: pick current subtask (radio), then **Mark Done** or **Delete**.
- **Attention Risk (simulated)**: slider + color bar with Low/Medium/High labels.
- **Focus Timer**: Start/Pause/Complete + progress indicator.
- **Focus Mode (DND)**: demo switch that isolates the panel (blocks page clicks outside).

## 🛡️ Autonomy & Ethics (Design Rationale)
Guidance can **never auto‑change** your settings or state. Users explicitly set:
- **Proactive suggestions**: `On (opt‑in)` or `Off`.
- **Frequency**: rate‑limits nudge cadence to avoid manipulation.
- **Tone**: neutral / supportive / direct to match preference.
- **Channel**: toast / inline banner / none (you can silence nudges).
- **Transparency**: optional **“Why this suggestion”** explainer.
- **Consent to learning (local only)**: lets the system down‑tune future frequency after dismissals.

These controls operationalize: *granted to users to control the frequency and tone of guidance, thereby avoiding ethical issues associated with machine manipulation.*

## 🚀 Quick Start
1. Copy the entire HTML file content (from this repo’s `taskmate.html`).  
2. **Option A**: Save as `taskmate.html` and double‑click to open.  
3. **Option B**: Paste into CodePen / JSFiddle / Tailwind Play **HTML** panel and run.

> Requires internet to fetch Tailwind from CDN (dev use). No Node / React / bundler needed.

## 🔧 Configuration (UI → Settings Tab)
- **Timer Defaults**
  - *Default Pomodoro length* (minutes)
- **Guidance & Autonomy**
  - *Proactive suggestions*: on/off (opt‑in)
  - *Guidance frequency*: `none | light | standard | high`
  - *Guidance tone*: `neutral | supportive | direct`
  - *Guidance channel*: `toast | banner | none`
- **Transparency & Consent**
  - *Show “Why this suggestion” explanations*
  - *Allow learning from my accept/dismiss (local only)*

Preferences are saved locally. Clearing browser storage resets the demo.

## 🗃️ Persistence Schema (excerpt)
Saved under `tm_state` in `localStorage`:
```json
{
  "settings": {
    "pomodoro": 25,
    "guidance": {
      "enabled": true,
      "frequency": "standard",
      "tone": "neutral",
      "channel": "toast",
      "showWhy": true,
      "learnPrefs": false,
      "lastSuggestTs": 0,
      "history": []
    }
  }
}
```

## ⏱️ Frequency Policy (built‑in)
| Level    | Cooldown (min) | Max per hour |
|----------|-----------------|--------------|
| none     | ∞               | 0            |
| light    | 20              | 2            |
| standard | 10              | 4            |
| high     | 5               | 6            |

The policy enforces a cool‑down and per‑hour cap to prevent over‑nudging.

## ♿ Accessibility Notes
- Toast uses `role="status"` with polite live region.  
- Radio controls for active subtask; clear button labels and focusable elements.  
- Color cues paired with text labels (“Low/Medium/High”).

## 🧱 File Layout
```
/ (single file)
├─ taskmate.html   # the entire demo (HTML + CSS via CDN + JS)
```

## 📸 Screens (examples)
- *Goal & Plan*: goal input, AI plan, add subtask, list actions.  
- *Risk & Timer*: risk slider + timer controls + progress.  
- *Tips/Stats/Settings*: guidance, transparency, and local‑only consent.

## 🧪 Known Limitations
- Risk is a **simulator**; no real sensor/behavior data.  
- “Generate Plan (AI)” uses a fixed demo template.  
- No background sync or multi‑tab state sharing.

## 🤝 Contributing
PRs welcome for: real risk model hooks, richer stats, keyboard shortcuts, i18n, tests.

## 📜 License
MIT. See `LICENSE` (or copy the MIT text into your project).
