# ClinicOS — Clinic Analytics & Operations Dashboard

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/clinic-analytics-dashboard/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

A responsive, runnable HTML/CSS/JavaScript reconstruction of the uploaded **5.27-second** screen recording (720 × 1280, 30 fps).

## Run locally
1. Extract `clinic-analytics-dashboard.zip`.
2. Open `index.html` in Chrome, Edge, Firefox or Safari.
3. No npm installation, build step or backend is required.

Optional local server:
```bash
python3 -m http.server 8000
```
Open `http://localhost:8000`.

## What the video shows

The video shows a dark blue analytics/operations workspace for a clinic network. The interface has a slim icon sidebar, breadcrumb/search bar, Live status, theme control, notifications and a New button. The visible screens change between Funnels, Campaigns (Board and Results) and Cohorts.

### Funnels screen
- Four saved funnels: **Visit to paid**, **Onboarding**, **Practice to Group**, and **Recall campaign**.
- The selected Visit to paid funnel shows five stages:
  1. Visited pricing — 48k
  2. Started trial — 9.6k
  3. Booked a phone call — 4.4k
  4. Invited the team — 2.8k
  5. Paid — 1.8k
- Overall conversion displayed as 3.83%.
- Channel tabs: All channels, Organic search, Paid search, Client referrals, Dental societies and Direct.
- Supporting panels show stage detail and the largest conversion leak.

### Campaigns screen
- Board / Results tabs.
- Board columns: Draft, Scheduled, Live and Done.
- Example campaign: **Recall session: winter check-ups**.
- Results screen shows the sent/opened/clicked/converted funnel and attributed revenue.
- The recording shows campaign cards and a campaign revenue chart.

### Cohorts screen
- Summary cards: Month 1 (86.2%), Month 6 (76.6%), Month 11 (71.4%) and strongest start (May 2026).
- Cohort retention matrix with monthly signup cohorts as rows and months since signup as columns.
- Toggle between Clinics and Revenue, plus CSV and Save to Reports actions.

### Other visible navigation
Overview, Funnels, Campaigns, Cohorts, Reports, Clinics, People, Messages, Automations, Reviews, Settings and Team.

## Exact readable source code visible in the video

The lower source panel is titled **`src/motion.ts`** and shows a 16-line TypeScript function. The following is transcribed from the screen, with line wrapping normalized:

```ts
export function slidePill(pill: HTMLElement, target: HTMLElement) {
  const box = pill.parentElement!;
  const W = box.offsetWidth, H = box.offsetHeight;
  const to: Edges = { l: target.offsetLeft, t: target.offsetTop,
    r: W - (target.offsetLeft + target.offsetWidth),
    b: H - (target.offsetTop + target.offsetHeight) };
  const st = host.__st ?? { ...prev };
  gsap.killTweensOf(st);
  const fwd = to.t > prev.t;                 // the sidebar: down or up
  const [lead, trail] = fwd ? ['b', 't'] : ['t', 'b'];
  const paint = () => gsap.set(pill, { clipPath: clip(st) });
  gsap.to(st, { [lead]: to[lead], duration: 0.36,
    ease: 'power3.out', onUpdate: paint });
  gsap.to(st, { [trail]: to[trail], duration: 0.55,
    ease: 'power3.inOut', onUpdate: paint });
}
```

**Note:** `Edges`, `host`, `prev`, and `clip` are referenced by the visible function but their definitions are outside the visible snippet. The implementation below recreates the same sliding/clip-path navigation-pill idea with plain JavaScript and CSS; it does not require GSAP.

## Included in this runnable project
- Dark blue responsive clinic analytics dashboard.
- Collapsible icon sidebar with active navigation state.
- Overview metrics, performance chart and top clinic list.
- Saved funnel selector with step-by-step conversion visualization.
- Campaign board with Draft / Scheduled / Live / Done columns.
- Drag-and-drop campaign status changes.
- Campaign Results screen with conversion stages and attributed revenue.
- Cohort summary cards and a retention heatmap table.
- Clinics, People, Reports, Messages, Automations, Reviews, Settings and Team views.
- Create campaign and funnel dialogs.
- CSV export for campaign data.
- Light/dark theme toggle and search navigation.
- Animated sliding tab indicator using clip-path and measured target bounds.

## Project files
- `index.html` — application shell and modal.
- `styles.css` — dashboard styling, responsive layout, chart and cohort matrix.
- `app.js` — sample data, navigation, campaign/funnel interactions, export and tab animation.
- `README.md` — video observations, source transcription and run instructions.

## Accuracy and limitations
This is a screen-based recreation, not the original clinic analytics repository. The visible screen supports the named modules, funnel steps, campaign states and cohort figures listed above. The source preview only exposes the `slidePill` function; other code is reconstructed from the visible interface. Several overview values and sample records in this demo are illustrative where the video does not show exact data.

No real clinic records, patient data, CRM, appointment system, campaign delivery service, messaging provider, billing or analytics backend is connected. All data and actions are local demo content. Campaign cards, funnel creation and CSV export work in the browser only.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)
