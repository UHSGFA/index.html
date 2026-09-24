[index (57).html](https://github.com/user-attachments/files/32619098/index.57.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>UHSGFA — 2026 Scoreboard (Prototype)</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@500;600;700;800&family=Work+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>

  :root {
    --bg: #0E0D1B;
    --bg-elevated: #17152A;
    --bg-card: #1B1930;
    --line: #322F52;
    --red: #CE2028;
    --red-bright: #E8323B;
    --navy: #130F43;
    --blue: #2A4494;
    --blue-bright: #3D5AB8;
    --accent2: #93AAEE;
    --text: #F3EFE6;
    --text-dim: #B0ACC4;
    --text-faint: #726E8C;
    --font-display: 'Barlow Condensed', 'Arial Narrow', sans-serif;
    --font-body: 'Work Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    padding-top: env(safe-area-inset-top, 0px);
    padding-bottom: env(safe-area-inset-bottom, 0px);
  }
  @media (prefers-color-scheme: light) {
    :root:not([data-theme="dark"]) {
      --bg: #F5F2EA;
      --bg-elevated: #FFFFFF;
      --bg-card: #FFFFFF;
      --line: #E2DCCC;
      --text: #1D1B17;
      --text-dim: #55503F;
      --text-faint: #8B8570;
    }
  }
  :root[data-theme="light"] {
    --bg: #F5F2EA;
    --bg-elevated: #FFFFFF;
    --bg-card: #FFFFFF;
    --line: #E2DCCC;
    --text: #1D1B17;
    --text-dim: #55503F;
    --text-faint: #8B8570;
  }

  * { box-sizing: border-box; }
  html { scroll-padding-top: env(safe-area-inset-top, 0px); }
  html, body { height: 100%; }
  body {
    margin: 0;
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-body);
    -webkit-font-smoothing: antialiased;
  }
  a { color: inherit; }
  button { font-family: inherit; }

  /* ---------- Layout shell ---------- */
  .wrap {
    max-width: 900px;
    margin: 0 auto;
    padding: 0 20px;
  }

  .back-to-site {
    background: var(--navy);
    padding: 7px 20px;
    padding-top: calc(7px + env(safe-area-inset-top, 0px));
    text-align: center;
  }
  .back-to-site a {
    color: var(--accent2);
    font-size: 12px;
    font-weight: 600;
    text-decoration: none;
  }
  .back-to-site a:hover { text-decoration: underline; }

  header.top {
    position: sticky;
    top: env(safe-area-inset-top, 0px);
    z-index: 20;
    background: rgba(20,18,15,0.92);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid var(--line);
  }
  :root[data-theme="light"] header.top,
  @media (prefers-color-scheme: light) { header.top { background: rgba(245,242,234,0.92); } }
  header.top .bar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 14px 20px;
    max-width: 900px;
    margin: 0 auto;
    gap: 16px;
  }
  .brand {
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
  }
  .brand-logo {
    height: 34px;
    width: auto;
    display: block;
    flex-shrink: 0;
    background: #fff;
    padding: 5px 8px;
    border-radius: 6px;
  }
  .name-sub {
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 10px;
    color: var(--text-faint);
    letter-spacing: 0.4px;
    display: none;
  }
  @media (min-width: 560px) {
    .name-sub { display: block; }
  }

  .header-actions {
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .coach-btn {
    background: var(--bg-card);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 9px 16px;
    border-radius: 7px;
    font-size: 13.5px;
    font-weight: 600;
    cursor: pointer;
    white-space: nowrap;
    transition: border-color .15s ease;
  }
  .coach-btn:hover { border-color: var(--red); }
  .coach-btn.active {
    background: var(--blue);
    border-color: var(--blue);
    color: #fff;
  }
  .coach-btn.ghost {
    background: none;
    color: var(--text-faint);
    font-size: 12.5px;
    padding: 9px 12px;
  }
  .coach-btn.ghost.active {
    background: var(--red);
    border-color: var(--red);
    color: #fff;
  }

  /* ---------- Site-wide tabs (mirrors the real site's nav) ---------- */
  .site-tabs {
    display: flex;
    gap: 2px;
    max-width: 900px;
    margin: 0 auto;
    padding: 0 20px;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    scrollbar-width: none;
    border-bottom: 1px solid var(--line);
  }
  .site-tabs::-webkit-scrollbar { display: none; }
  .site-tab {
    background: none;
    border: none;
    border-bottom: 2px solid transparent;
    color: var(--text-faint);
    font-size: 13px;
    font-weight: 600;
    padding: 12px 12px 10px;
    cursor: pointer;
    white-space: nowrap;
    flex-shrink: 0;
  }
  .site-tab:hover { color: var(--text-dim); }
  .site-tab.active {
    color: var(--text);
    border-bottom-color: var(--red);
  }

  .tab-panel { display: none; }
  .tab-panel.active { display: block; }

  /* ---------- Info list pages (Season Info / About / FAQs / Swag / Calendar) ---------- */
  .info-list-page { padding: 34px 20px 10px; }
  .cal-head-row {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 14px;
  }
  .cal-pdf-btn {
    flex-shrink: 0;
    padding: 10px 18px;
    white-space: nowrap;
  }
  .info-list-page h2 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 26px;
    margin: 0 0 18px;
  }
  .about-mission {
    font-size: 14px;
    color: var(--text-dim);
    line-height: 1.6;
    max-width: 60ch;
    margin: 0 0 22px;
  }

  .emblem-explainer {
    margin-bottom: 30px;
  }
  .emblem-explainer-img {
    width: 100%;
    max-width: 640px;
    height: auto;
    display: block;
    background: #fff;
    padding: 14px;
    border-radius: 12px;
    border: 1px solid var(--line);
  }

  .team-section-head { margin-bottom: 14px; }
  .team-section-head h3 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 20px;
    margin: 0;
  }
  .team-members {
    display: flex;
    flex-direction: column;
    gap: 14px;
    margin-bottom: 8px;
  }
  .team-member {
    display: flex;
    gap: 14px;
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 12px;
    padding: 16px;
  }
  .tm-avatar {
    flex-shrink: 0;
    width: 52px;
    height: 52px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 17px;
    color: #fff;
  }
  .tm-info { min-width: 0; }
  .tm-name {
    font-size: 15px;
    font-weight: 700;
    color: var(--text);
  }
  .tm-title {
    font-size: 11.5px;
    font-weight: 600;
    color: var(--accent2);
    text-transform: uppercase;
    letter-spacing: 0.3px;
    margin: 2px 0 8px;
  }
  .tm-bio {
    font-size: 13px;
    color: var(--text-dim);
    line-height: 1.55;
    margin: 0;
  }
  @media (max-width: 480px) {
    .team-member { flex-direction: column; align-items: flex-start; }
  }

  .info-list {
    display: grid;
    gap: 10px;
    margin-bottom: 18px;
  }
  .info-list-item {
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-left: 3px solid var(--blue);
    border-radius: 9px;
    padding: 13px 16px;
  }
  .info-list-item h4 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 16px;
    margin: 0 0 3px;
    letter-spacing: 0.2px;
  }
  .info-list-item p {
    font-size: 12.5px;
    color: var(--text-faint);
    margin: 0;
    line-height: 1.4;
  }
  .info-list-note {
    font-size: 11.5px;
    color: var(--text-faint);
    border-top: 1px solid var(--line);
    padding-top: 14px;
    line-height: 1.5;
  }

  /* ---------- Standings ---------- */
  .standings-table-wrap {
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    border: 1px solid var(--line);
    border-radius: 12px;
  }
  .standings-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
  }
  .standings-table th {
    text-align: right;
    font-size: 10.5px;
    font-weight: 700;
    color: var(--text-faint);
    text-transform: uppercase;
    letter-spacing: 0.3px;
    padding: 10px 12px;
    background: var(--bg-card);
    border-bottom: 2px solid var(--line);
    white-space: nowrap;
  }
  .standings-table th.st-team { text-align: left; }
  .standings-table td {
    text-align: right;
    padding: 10px 12px;
    border-bottom: 1px solid var(--line);
    white-space: nowrap;
  }
  .standings-table tbody tr:last-child td { border-bottom: none; }
  .standings-table tbody tr {
    cursor: pointer;
    transition: background-color .12s ease;
  }
  .standings-table tbody tr:hover { background: var(--bg-card); }
  .standings-table td.st-team {
    text-align: left;
    font-weight: 600;
    color: var(--text);
  }
  .standings-table td.st-diff-pos { color: var(--blue-bright); font-weight: 600; }
  .standings-table td.st-diff-neg { color: var(--red-bright); font-weight: 600; }
  @media (max-width: 480px) {
    .standings-table th.st-wide, .standings-table td.st-wide { display: none; }
  }

  /* ---------- Team detail ---------- */
  .team-detail-head {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 8px;
    margin: 18px 0 6px;
  }
  .team-detail-head h2 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 24px;
    margin: 0;
  }
  .team-detail-record {
    font-size: 13px;
    color: var(--text-dim);
    font-weight: 600;
  }
  .leader-cards {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    gap: 10px;
    margin: 18px 0 26px;
  }
  .leader-card {
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-left: 3px solid var(--blue);
    border-radius: 9px;
    padding: 11px 13px;
  }
  .leader-card .lc-cat {
    font-size: 10px;
    font-weight: 700;
    color: var(--text-faint);
    text-transform: uppercase;
    letter-spacing: 0.3px;
    margin-bottom: 4px;
  }
  .leader-card .lc-name {
    font-size: 13.5px;
    font-weight: 600;
    color: var(--text);
  }
  .leader-card .lc-value {
    font-size: 12px;
    color: var(--text-dim);
    margin-top: 1px;
  }
  .leader-card .lc-rank {
    font-size: 10.5px;
    color: var(--accent2);
    margin-top: 4px;
    font-weight: 600;
  }
  .leader-card .lc-empty {
    font-size: 12px;
    color: var(--text-faint);
  }

  .stat-table-wrap {
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    border: 1px solid var(--line);
    border-radius: 12px;
    margin-bottom: 24px;
  }
  .stat-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 12.5px;
    background: var(--bg-card);
  }
  .stat-table th {
    text-align: center;
    font-size: 10px;
    font-weight: 700;
    color: var(--text-faint);
    text-transform: uppercase;
    letter-spacing: 0.3px;
    padding: 9px 10px;
    background: var(--bg-card);
    border-bottom: 2px solid var(--line);
    border-right: 1px solid var(--line);
    white-space: nowrap;
  }
  .stat-table th:last-child { border-right: none; }
  .stat-table th.stt-sortable {
    text-align: center;
    cursor: pointer;
    user-select: none;
    line-height: 1.3;
  }
  .stat-table th.stt-sortable span { display: block; }
  .stat-table th.stt-sortable span:first-child { color: var(--text-dim); }
  .stat-table th.stt-sortable:hover { background: var(--bg-elevated); color: var(--text); }
  .stat-table th.stt-sortable:hover span:first-child { color: var(--text); }
  .stat-table th.stt-sortable.active-sort { background: rgba(206,32,40,0.1); }
  .stat-table th.stt-sortable.active-sort span { color: var(--red-bright); }
  .stat-table td {
    text-align: center;
    padding: 9px 10px;
    border-bottom: 1px solid var(--line);
    border-right: 1px solid var(--line);
  }
  .stat-table td:last-child { border-right: none; }
  .stat-table td.stt-sorted { background: rgba(206,32,40,0.06); font-weight: 700; color: var(--text); }
  .stat-table tbody tr:last-child td { border-bottom: none; }
  .team-compare-row { cursor: pointer; }
  .team-compare-row:hover { background: var(--bg-elevated); }
  .stat-table td.stt-name { text-align: center; font-weight: 600; color: var(--text); }
  .stat-table td.stt-pos { text-align: center; color: var(--text-faint); }
  .stat-table .stt-sticky {
    position: sticky;
    z-index: 2;
    background: var(--bg-card);
    white-space: normal;
    word-break: break-word;
    line-height: 1.25;
  }
  .stat-table th.stt-sticky { z-index: 3; }
  .stat-table .stt-sticky-edge { box-shadow: 2px 0 5px rgba(0,0,0,0.08); }

  .league-compare-row {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    gap: 10px;
    padding: 9px 0;
    border-bottom: 1px dashed var(--line);
    font-size: 12.5px;
  }
  .league-compare-row:last-child { border-bottom: none; }
  .lcr-cat { color: var(--text-faint); font-weight: 600; min-width: 90px; }
  .lcr-info { text-align: right; color: var(--text-dim); }
  .lcr-info b { color: var(--text); }

  /* ---------- Calendar / Upcoming Events ---------- */
  .cal-event {
    display: flex;
    align-items: center;
    gap: 16px;
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 11px;
    padding: 13px 16px;
    margin-bottom: 10px;
  }
  .cal-date-badge {
    flex-shrink: 0;
    width: 54px;
    text-align: center;
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    border-top: 3px solid var(--red);
    border-radius: 8px;
    padding: 6px 0 7px;
    line-height: 1.1;
  }
  .cal-date-badge .cal-month {
    font-size: 10px;
    font-weight: 700;
    color: var(--red-bright);
    text-transform: uppercase;
    letter-spacing: 0.4px;
  }
  .cal-date-badge .cal-day {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 20px;
    color: var(--text);
  }
  .cal-event-info { min-width: 0; flex: 1; }
  .cal-event-title {
    font-size: 14px;
    font-weight: 600;
    color: var(--text);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .cal-event-meta {
    font-size: 12px;
    color: var(--text-faint);
    margin-top: 2px;
  }
  .cal-event-week {
    flex-shrink: 0;
    font-size: 10.5px;
    font-weight: 700;
    color: var(--accent2);
    background: rgba(42,68,148,0.16);
    padding: 3px 9px;
    border-radius: 20px;
    white-space: nowrap;
  }

  /* ---------- Playoff bracket ---------- */
  .bracket-wrap {
    display: flex;
    gap: 0;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    padding-bottom: 12px;
  }
  .bracket-col {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    gap: 14px;
    min-width: 200px;
    padding: 0 14px;
    flex-shrink: 0;
  }
  .bracket-col-title {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 13px;
    color: var(--text-dim);
    text-align: center;
    text-transform: uppercase;
    letter-spacing: 0.3px;
    margin-bottom: 6px;
  }
  .bracket-match {
    position: relative;
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 10px;
    padding: 10px 12px;
    font-size: 12.5px;
  }
  .bracket-match::after {
    content: '';
    position: absolute;
    top: 50%;
    right: -14px;
    width: 14px;
    height: 1px;
    background: var(--line);
  }
  .bracket-col:last-child .bracket-match::after { display: none; }
  .bracket-team {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 8px;
    padding: 3px 0;
  }
  .bracket-team.winner .bracket-team-name { color: var(--text); font-weight: 700; }
  .bracket-team:not(.winner) .bracket-team-name { color: var(--text-faint); }
  .bracket-team-name {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .bracket-team-score {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 13px;
    flex-shrink: 0;
  }
  .bracket-vs {
    text-align: center;
    color: var(--text-faint);
    font-size: 10px;
    font-weight: 600;
    padding: 2px 0;
  }
  .bracket-match-meta {
    text-align: center;
    font-size: 10px;
    color: var(--text-faint);
    margin-top: 6px;
    border-top: 1px dashed var(--line);
    padding-top: 5px;
  }

  .home-hero {
    padding: 34px 20px 8px;
    display: grid;
    gap: 26px;
  }
  @media (min-width: 680px) {
    .home-hero {
      grid-template-columns: 260px 1fr;
      align-items: start;
    }
  }
  .emblem-card {
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 14px;
    padding: 22px 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 14px;
  }
  .home-logo {
    width: 100%;
    max-width: 220px;
    height: auto;
    background: #fff;
    padding: 12px 16px;
    border-radius: 10px;
  }
  .emblem-caption {
    font-size: 12px;
    color: var(--text-faint);
    line-height: 1.55;
    margin: 0;
  }
  .mission-block .eyebrow {
    font-size: 13px;
    color: var(--accent2);
    font-weight: 600;
    margin-bottom: 8px;
  }
  .mission-text {
    color: var(--text-dim);
    font-size: 15px;
    line-height: 1.6;
    max-width: 56ch;
    margin: 0 0 18px;
  }

  .goal-block {
    padding: 0 0 22px;
    margin-bottom: 22px;
    border-bottom: 1px solid var(--line);
  }
  .goal-block h3 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 20px;
    margin: 0 0 8px;
  }
  .goal-block p {
    color: var(--text-dim);
    font-size: 14px;
    line-height: 1.6;
    max-width: 68ch;
    margin: 0;
  }

  .season-info { margin-bottom: 6px; }
  .info-card {
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-left: 3px solid var(--red);
    border-radius: 10px;
    padding: 18px 20px;
  }
  .info-card h3 {
    font-family: var(--font-display);
    font-size: 18px;
    font-weight: 700;
    margin: 0 0 6px;
    letter-spacing: 0.2px;
  }
  .info-card p {
    font-size: 13.5px;
    color: var(--text-dim);
    line-height: 1.55;
    margin: 0 0 14px;
    max-width: 62ch;
  }
  .info-facts {
    display: flex;
    gap: 22px;
    flex-wrap: wrap;
    border-top: 1px solid var(--line);
    padding-top: 14px;
  }
  .info-fact {
    display: flex;
    flex-direction: column;
    gap: 1px;
  }
  .fact-num {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 20px;
    color: var(--text);
    line-height: 1.1;
  }
  .fact-label {
    font-size: 10.5px;
    font-weight: 600;
    color: var(--text-faint);
    text-transform: uppercase;
    letter-spacing: 0.4px;
  }

  /* ---------- Current Teams ---------- */
  .teams-section { margin: 36px auto 0; }
  .teams-head {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 6px;
    margin-bottom: 14px;
  }
  .teams-head h2 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 20px;
    margin: 0;
  }
  .teams-sub {
    font-size: 11.5px;
    color: var(--text-faint);
    font-weight: 500;
  }
  .team-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(112px, 1fr));
    gap: 12px;
  }
  .team-badge {
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 12px;
    padding: 16px 8px 12px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 9px;
    cursor: pointer;
    font-family: inherit;
    color: inherit;
  }
  .team-badge:hover { border-color: var(--blue); }
  .team-badge.active {
    border-color: var(--red);
    background: rgba(206,32,40,0.08);
  }
  .team-badge .tb-mono {
    width: 64px; height: 64px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 20px;
    color: #fff;
    letter-spacing: 0.3px;
  }
  .team-badge .tb-logo-img {
    object-fit: contain;
    background: #fff;
    padding: 4px;
  }
  .team-badge .tb-name {
    font-size: 11.5px;
    font-weight: 600;
    color: var(--text-dim);
    text-align: center;
    line-height: 1.25;
  }
  .team-badge.active .tb-name { color: var(--text); }

  /* ---------- Section headers ---------- */
  .week-head {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    margin: 34px 0 12px;
    padding-bottom: 8px;
    border-bottom: 2px solid var(--line);
  }
  .week-head h2 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 22px;
    margin: 0;
    letter-spacing: 0.2px;
  }
  .week-done-tag {
    font-size: 10.5px;
    font-weight: 700;
    color: var(--text-faint);
    background: var(--bg-card);
    border: 1px solid var(--line);
    padding: 3px 9px;
    border-radius: 20px;
    text-transform: uppercase;
    letter-spacing: 0.3px;
  }
  .week-head .week-date {
    font-size: 12.5px;
    color: var(--text-faint);
    font-weight: 500;
  }

  /* ---------- Game card ---------- */
  .game {
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 10px;
    padding: 14px 16px;
    margin-bottom: 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  .game .meta-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 11.5px;
    color: var(--text-faint);
  }
  .status {
    padding: 2px 8px;
    border-radius: 20px;
    font-size: 10.5px;
    font-weight: 700;
    letter-spacing: 0.3px;
  }
  .status.final { background: rgba(206,32,40,0.16); color: var(--red-bright); }
  .status.scheduled { background: rgba(42,68,148,0.22); color: var(--blue-bright); }

  .matchup {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .team-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
  }
  .team-row .team-name-wrap {
    display: flex;
    align-items: center;
    gap: 9px;
    min-width: 0;
    flex: 1;
  }
  .trow-logo {
    flex-shrink: 0;
    width: 26px;
    height: 26px;
    border-radius: 50%;
    object-fit: contain;
    background: #fff;
    padding: 2px;
  }
  .trow-logo-fallback {
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 9.5px;
    color: #fff;
    letter-spacing: 0.2px;
  }
  .team-row .team-name {
    font-size: 16px;
    font-weight: 600;
    min-width: 0;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .team-row .score {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 26px;
    min-width: 36px;
    text-align: right;
    flex-shrink: 0;
  }
  .team-row.winner .team-name { color: var(--text); }
  .team-row.winner .score { color: var(--red-bright); }
  .team-row.loser .score, .team-row.loser .team-name { color: var(--text-dim); }
  .team-row.tbd .score { color: var(--text-faint); font-size: 15px; font-weight: 500; }

  .stat-line {
    font-size: 12px;
    color: var(--text-faint);
    border-top: 1px dashed var(--line);
    padding-top: 8px;
    line-height: 1.5;
  }
  .stat-line b { color: var(--text-dim); font-weight: 600; }

  .game-actions {
    display: flex;
    justify-content: flex-end;
  }
  .edit-link {
    background: none;
    border: none;
    color: var(--accent2);
    font-size: 12.5px;
    font-weight: 600;
    cursor: pointer;
    padding: 4px 0;
  }
  .edit-link:hover { text-decoration: underline; }
  .admin-edit-link { color: var(--red-bright); }

  /* ---------- empty state ---------- */
  .empty {
    color: var(--text-faint);
    font-size: 13.5px;
    padding: 10px 2px 4px;
  }

  /* ---------- Overlay / modal ---------- */
  .overlay {
    position: fixed;
    inset: 0;
    background: rgba(10,9,7,0.72);
    display: none;
    align-items: flex-start;
    justify-content: center;
    padding: 60px 16px;
    z-index: 100;
    overflow-y: auto;
  }
  .overlay.open { display: flex; }
  .modal {
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    border-radius: 14px;
    width: 100%;
    max-width: 440px;
    padding: 26px 24px 24px;
  }
  .modal h3 {
    font-family: var(--font-display);
    font-size: 24px;
    font-weight: 700;
    margin: 0 0 4px;
  }
  .modal .sub {
    font-size: 13px;
    color: var(--text-faint);
    margin: 0 0 20px;
    line-height: 1.4;
  }
  .field { margin-bottom: 14px; }
  .field label {
    display: block;
    font-size: 12px;
    font-weight: 600;
    color: var(--text-dim);
    margin-bottom: 6px;
  }
  .field input, .field select {
    width: 100%;
    background: var(--bg-card);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 10px 12px;
    border-radius: 7px;
    font-size: 14.5px;
    font-family: var(--font-body);
  }
  .field input:focus, .field select:focus {
    outline: none;
    border-color: var(--red);
  }
  .row2 { display: flex; gap: 10px; }
  .row2 .field { flex: 1; }

  .modal-actions {
    display: flex;
    gap: 10px;
    margin-top: 18px;
  }
  .btn {
    flex: 1;
    padding: 11px 16px;
    border-radius: 7px;
    border: 1px solid var(--line);
    background: var(--bg-card);
    color: var(--text);
    font-weight: 600;
    font-size: 14px;
    cursor: pointer;
  }
  .btn.primary {
    background: var(--red);
    border-color: var(--red);
    color: #fff;
  }
  .btn.primary:hover { background: var(--red-bright); }
  .btn:hover { border-color: var(--text-faint); }

  .modal-close {
    position: absolute;
    top: 16px;
    right: 16px;
  }
  .modal { position: relative; }
  .modal-wide { max-width: 560px; }

  .stat-entry {
    border-top: 1px solid var(--line);
    padding-top: 16px;
    margin-top: 4px;
  }
  .stat-entry-head {
    display: flex;
    flex-direction: column;
    gap: 2px;
    margin-bottom: 12px;
  }
  .stat-entry-head label {
    font-size: 12px;
    font-weight: 600;
    color: var(--text-dim);
  }
  .stat-entry-sub {
    font-size: 11.5px;
    color: var(--text-faint);
  }

  .player-row {
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 9px;
    padding: 10px 12px 12px;
    margin-bottom: 10px;
  }
  .player-row-top {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 8px;
  }
  .player-row-top .p-name {
    flex: 1;
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 8px 10px;
    border-radius: 6px;
    font-size: 13.5px;
    font-weight: 600;
    font-family: var(--font-body);
    min-width: 0;
  }
  .player-row-top .p-position {
    width: 58px;
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 8px 6px;
    border-radius: 6px;
    font-size: 12.5px;
    text-align: center;
    text-transform: uppercase;
    font-family: var(--font-body);
    flex-shrink: 0;
  }
  .player-row-top .p-jersey {
    width: 46px;
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 8px 6px;
    border-radius: 6px;
    font-size: 12.5px;
    text-align: center;
    font-family: var(--font-body);
    flex-shrink: 0;
  }
  .player-row-top .p-name:focus, .player-row-top .p-position:focus, .player-row-top .p-jersey:focus { outline: none; border-color: var(--red); }
  .remove-player-btn {
    background: none;
    border: none;
    color: var(--text-faint);
    font-size: 15px;
    cursor: pointer;
    padding: 4px 6px;
    line-height: 1;
    flex-shrink: 0;
  }
  .remove-player-btn:hover { color: var(--red-bright); }

  .admin-stats-block {
    border-top: 1px dashed var(--line);
    padding-top: 14px;
    margin-top: 14px;
  }
  .admin-stats-block .stats-toggle-btn { width: 100%; text-align: left; }

  .stats-toggle-btn {
    background: none;
    border: 1px dashed var(--line);
    color: var(--accent2);
    font-size: 11.5px;
    font-weight: 600;
    padding: 6px 10px;
    border-radius: 6px;
    cursor: pointer;
    margin-bottom: 4px;
  }
  .stats-toggle-btn:hover { border-color: var(--blue); }

  .stat-groups {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-top: 8px;
    padding-top: 10px;
    border-top: 1px dashed var(--line);
  }
  .stat-group-title {
    font-size: 9.5px;
    font-weight: 700;
    color: var(--text-faint);
    text-transform: uppercase;
    letter-spacing: 0.4px;
    margin-bottom: 5px;
  }
  .stat-group-fields {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  .stat-mini2 {
    width: 52px;
    flex-shrink: 0;
  }
  .stat-mini2 label {
    display: block;
    font-size: 9px;
    font-weight: 600;
    color: var(--text-faint);
    text-transform: uppercase;
    letter-spacing: 0.2px;
    margin-bottom: 3px;
  }
  .stat-mini2 input {
    width: 100%;
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 6px 4px;
    border-radius: 5px;
    font-size: 12.5px;
    text-align: center;
    font-family: var(--font-body);
  }
  .stat-mini2 input:focus { outline: none; border-color: var(--red); }

  .add-player-btn {
    width: 100%;
    background: none;
    border: 1px dashed var(--line);
    color: var(--text-dim);
    padding: 10px;
    border-radius: 8px;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
  }
  .add-player-btn:hover { border-color: var(--red); color: var(--text); }

  /* ---------- Roster quick-add chips ---------- */
  .roster-quick-add {
    margin-bottom: 12px;
  }
  .rqa-label {
    display: block;
    font-size: 11px;
    font-weight: 600;
    color: var(--text-faint);
    margin-bottom: 7px;
  }
  .rqa-chips {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
  }
  .rqa-chip {
    background: rgba(42,68,148,0.16);
    border: 1px solid var(--blue);
    color: var(--accent2);
    font-size: 12.5px;
    font-weight: 600;
    padding: 6px 12px;
    border-radius: 20px;
    cursor: pointer;
  }
  .rqa-chip:hover { background: rgba(42,68,148,0.3); }
  .rqa-chip.added {
    opacity: 0.4;
    cursor: default;
    border-color: var(--line);
    color: var(--text-faint);
    background: none;
  }
  .rqa-all {
    background: none;
    border: 1px dashed var(--blue);
    color: var(--accent2);
    font-size: 12.5px;
    font-weight: 600;
    padding: 6px 12px;
    border-radius: 20px;
    cursor: pointer;
  }
  .rqa-all:hover { background: rgba(42,68,148,0.16); }

  /* ---------- My Team panel ---------- */
  .myteam-head { margin: 30px 0 18px; }
  .myteam-head h2 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 26px;
    margin: 0 0 4px;
  }
  .myteam-sub {
    font-size: 13px;
    color: var(--text-faint);
    margin: 0;
    max-width: 50ch;
    line-height: 1.5;
  }
  .roster-row {
    display: flex;
    align-items: center;
    gap: 8px;
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 9px;
    padding: 9px 10px;
    margin-bottom: 8px;
  }
  .roster-row .r-name {
    flex: 1;
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 9px 11px;
    border-radius: 6px;
    font-size: 14px;
    font-weight: 600;
    font-family: var(--font-body);
    min-width: 0;
  }
  .roster-row .r-position {
    width: 62px;
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 9px 8px;
    border-radius: 6px;
    font-size: 13px;
    text-align: center;
    text-transform: uppercase;
    font-family: var(--font-body);
    flex-shrink: 0;
  }
  .roster-row .r-number {
    width: 50px;
    background: var(--bg-elevated);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 9px 8px;
    border-radius: 6px;
    font-size: 14px;
    text-align: center;
    font-family: var(--font-body);
    flex-shrink: 0;
  }
  .roster-row .r-name:focus, .roster-row .r-position:focus, .roster-row .r-number:focus { outline: none; border-color: var(--red); }
  .myteam-actions {
    display: flex;
    gap: 10px;
    margin-top: 6px;
  }
  .myteam-actions .add-player-btn { flex: 1; }
  .myteam-actions .btn.primary { flex: 1; }
  .myteam-status {
    font-size: 12.5px;
    color: var(--accent2);
    margin-top: 12px;
    min-height: 1em;
  }
  .roster-empty {
    font-size: 13px;
    color: var(--text-faint);
    padding: 6px 2px 14px;
  }

  /* ---------- Admin: schedule matchups ---------- */
  .admin-form {
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 12px;
    padding: 18px 18px 16px;
    margin-bottom: 28px;
  }
  .admin-form .row2 { margin-bottom: 4px; }
  .admin-list-head {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    border-bottom: 2px solid var(--line);
    padding-bottom: 8px;
    margin-bottom: 12px;
  }
  .admin-list-head h3 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 18px;
    margin: 0;
  }
  .admin-week-filter {
    background: var(--bg-card);
    border: 1px solid var(--line);
    color: var(--text);
    padding: 6px 10px;
    border-radius: 6px;
    font-size: 12.5px;
    font-weight: 600;
    font-family: inherit;
  }
  .admin-week-filter:focus { outline: none; border-color: var(--red); }
  .admin-game-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    background: var(--bg-card);
    border: 1px solid var(--line);
    border-radius: 9px;
    padding: 11px 14px;
    margin-bottom: 8px;
  }
  .admin-game-row.editing { border-color: var(--red); }
  .agr-info { min-width: 0; }
  .agr-matchup {
    font-size: 13.5px;
    font-weight: 600;
    color: var(--text);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .agr-meta {
    font-size: 11.5px;
    color: var(--text-faint);
    margin-top: 2px;
  }
  .agr-actions {
    display: flex;
    gap: 6px;
    flex-shrink: 0;
  }
  .agr-btn {
    background: none;
    border: 1px solid var(--line);
    color: var(--text-dim);
    font-size: 11.5px;
    font-weight: 600;
    padding: 6px 10px;
    border-radius: 6px;
    cursor: pointer;
  }
  .agr-btn:hover { border-color: var(--blue); color: var(--text); }
  .agr-btn.danger:hover { border-color: var(--red); color: var(--red-bright); }

  /* ---------- Player stat breakdown on scoreboard ---------- */
  .stat-block {
    border-top: 1px dashed var(--line);
    padding-top: 10px;
    margin-top: 2px;
  }
  .stat-block-title {
    font-size: 10.5px;
    font-weight: 700;
    color: var(--text-faint);
    text-transform: uppercase;
    letter-spacing: 0.4px;
    margin-bottom: 6px;
  }
  .stat-player {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    gap: 10px;
    font-size: 12.5px;
    padding: 3px 0;
  }
  .stat-player .sp-name {
    color: var(--text);
    font-weight: 600;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .sp-pos {
    display: inline-block;
    font-family: var(--font-body);
    font-weight: 700;
    font-size: 9.5px;
    color: var(--accent2);
    background: rgba(42,68,148,0.18);
    border-radius: 4px;
    padding: 1px 5px;
    margin-left: 4px;
    letter-spacing: 0.3px;
  }
  .stat-player .sp-line {
    color: var(--text-faint);
    text-align: right;
  }

  .note {
    font-size: 11.5px;
    color: var(--text-faint);
    margin-top: 14px;
    line-height: 1.5;
    border-top: 1px solid var(--line);
    padding-top: 12px;
  }

  .toast {
    position: fixed;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%) translateY(10px);
    background: var(--blue);
    color: #fff;
    padding: 11px 20px;
    border-radius: 8px;
    font-size: 13.5px;
    font-weight: 600;
    opacity: 0;
    pointer-events: none;
    transition: opacity .2s ease, transform .2s ease;
    z-index: 200;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
  }
  .toast.show {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }

  .banner {
    max-width: 900px;
    margin: 0 auto;
    padding: 10px 20px 0;
  }
  .banner .box {
    background: rgba(147,170,238,0.1);
    border: 1px solid rgba(147,170,238,0.32);
    color: var(--accent2);
    font-size: 12.5px;
    padding: 10px 14px;
    border-radius: 8px;
    line-height: 1.5;
  }

  footer {
    max-width: 900px;
    margin: 50px auto 0;
    padding: 22px 20px 40px;
    border-top: 1px solid var(--line);
    color: var(--text-faint);
    font-size: 12px;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 12px;
    line-height: 1.6;
  }
  .foot-links { display: flex; gap: 14px; }
  .foot-links a { color: var(--text-faint); text-decoration: none; font-weight: 600; }
  .foot-links a:hover { color: var(--red-bright); }

  ::-webkit-scrollbar { width: 10px; }
  ::-webkit-scrollbar-thumb { background: var(--line); border-radius: 10px; }

  @media (max-width: 480px) {
    .team-row .team-name { font-size: 14.5px; }
    .team-row .score { font-size: 22px; }
  }
</style>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
</head>
<body>

<div class="back-to-site">
  <a href="https://uhsgfa.org/">&larr; Back to UHSGFA Site</a>
</div>

<header class="top">
  <div class="bar">
    <div class="brand">
      <img class="brand-logo" src="data:image/png;base64,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" alt="UHSGFA — Utah High School Girls Football Association">
      <span class="name-sub">2026 SCOREBOARD · PROTOTYPE</span>
    </div>
    <div class="header-actions">
      <button class="coach-btn ghost" id="adminBtn">Admin</button>
      <button class="coach-btn" id="coachBtn">Coach Login</button>
    </div>
  </div>
</header>

<nav class="site-tabs" id="siteTabs">
  <button class="site-tab active" data-tab="scoreboard">Scoreboard</button>
  <button class="site-tab" data-tab="standings">Standings</button>
  <button class="site-tab" data-tab="stats">Stats</button>
  <button class="site-tab" data-tab="calendar">Calendar</button>
  <button class="site-tab" data-tab="bracket">Playoffs</button>
  <button class="site-tab" id="tabMyTeamBtn" data-tab="myteam" style="display:none;">My Team</button>
  <button class="site-tab" id="tabAdminBtn" data-tab="admin" style="display:none;">Admin</button>
</nav>

<div class="banner">
  <div class="box">
    Working prototype — the schedule below is the real 2026 season, but no results have been posted yet. Tap <b>Coach Login</b> to post one.
  </div>
</div>

<section class="tab-panel active" id="panelScoreboard" data-panel="scoreboard">
<div class="wrap teams-section">
    <div class="teams-head">
      <h2>Current Teams — Fall 2026</h2>
      <span class="teams-sub" id="teamsFilterHint">Tap a team to filter the games below</span>
    </div>
    <div class="team-grid" id="teamGrid"></div>
  </div>

  <main class="wrap" id="scoreboard">
    <!-- weeks render here -->
  </main>
</section>

<section class="tab-panel" id="panelStandings" data-panel="standings">
  <div class="wrap">

    <div id="standingsListView">
      <div class="teams-head">
        <h2>Standings</h2>
        <span class="teams-sub">Live — updates as coaches post results. Tap a team for player stats.</span>
      </div>
      <div class="standings-table-wrap">
        <table class="standings-table">
          <thead>
            <tr>
              <th class="st-team">Team</th>
              <th>W</th>
              <th>L</th>
              <th class="st-wide">PF</th>
              <th class="st-wide">PA</th>
              <th class="st-wide">Diff</th>
            </tr>
          </thead>
          <tbody id="standingsBody"></tbody>
        </table>
      </div>
    </div>

    <div id="teamDetailView" style="display:none;">
      <button class="agr-btn" id="backToStandingsBtn" type="button">← Back to Standings</button>
      <div id="teamDetailContent"></div>
    </div>

  </div>
</section>

<section class="tab-panel" id="panelStats" data-panel="stats">
  <div class="wrap">
    <div class="teams-head">
      <h2>Stats</h2>
      <select id="statsModeSelect" class="admin-week-filter">
        <option value="team">Team Stats</option>
        <option value="individual">Individual Stats</option>
      </select>
    </div>

    <div id="statsTeamPanel">
      <div class="field" style="max-width:320px; margin-top:14px;">
        <label for="statsTeamSelect">Team</label>
        <select id="statsTeamSelect"></select>
      </div>
      <div id="statsTeamContent"></div>
    </div>

    <div id="statsIndividualPanel" style="display:none;">
      <div class="row2" style="max-width:520px; margin-top:14px;">
        <div class="field">
          <label for="statsIndivTeamSelect">Team</label>
          <select id="statsIndivTeamSelect"></select>
        </div>
        <div class="field" id="statsIndivPlayerField">
          <label for="statsIndivPlayerSelect">Player</label>
          <select id="statsIndivPlayerSelect"></select>
        </div>
      </div>
      <div id="statsIndivContent"></div>
    </div>
  </div>
</section>

<section class="tab-panel" id="panelCalendar" data-panel="calendar">
  <div class="wrap info-list-page">
    <div class="cal-head-row">
      <div>
        <h2>Upcoming Events</h2>
        <p class="teams-sub" style="display:block; margin-top:4px;">Every scheduled game, pulled straight from the Scoreboard and Admin tabs.</p>
      </div>
      <button class="btn primary cal-pdf-btn" id="downloadScheduleBtn" type="button">Download PDF</button>
    </div>

    <div class="teams-head" style="margin-top:22px;">
      <h2 style="font-size:18px;">Current Teams — Fall 2026</h2>
      <span class="teams-sub" id="teamsFilterHintCal">Tap a team to filter the events below</span>
    </div>
    <div class="team-grid" id="teamGridCalendar" style="margin-bottom:22px;"></div>

    <div id="calendarList"></div>
  </div>
</section>

<section class="tab-panel" id="panelBracket" data-panel="bracket">
  <div class="wrap info-list-page">
    <h2>Playoffs</h2>
    <p class="teams-sub" style="display:block; margin-bottom:18px;">Updates automatically as playoff matchups and scores are entered in Admin. Seeds shown as placeholders until real seeding is set.</p>
    <div class="bracket-wrap" id="bracketWrap"></div>
  </div>
</section>

<section class="tab-panel" id="myTeamPanel" data-panel="myteam">
  <div class="wrap">
    <div class="myteam-head">
      <h2 id="myTeamTitle">My Team</h2>
      <p class="myteam-sub">Save your roster once, then quick-add players when you post scores each week — no more retyping names.</p>
    </div>
    <div id="rosterRows"></div>
    <div class="myteam-actions">
      <button class="add-player-btn" id="addRosterPlayerBtn" type="button">+ Add player to roster</button>
      <button class="btn primary" id="saveRosterBtn" type="button">Save roster</button>
    </div>
    <div class="myteam-status" id="rosterStatus"></div>
  </div>
</section>

<section class="tab-panel" id="panelAdmin" data-panel="admin">
  <div class="wrap">
    <div class="myteam-head">
      <h2>Schedule Matchups</h2>
      <p class="myteam-sub">Set up a game between two teams — pick the week, date, time, and venue. Existing matchups can be edited or removed below.</p>
    </div>

    <div class="admin-form">
      <div class="row2">
        <div class="field">
          <label for="adminTeamA">Team A</label>
          <input id="adminTeamA" type="text" list="adminTeamsList" placeholder="Type or pick a team">
        </div>
        <div class="field">
          <label for="adminTeamB">Team B</label>
          <input id="adminTeamB" type="text" list="adminTeamsList" placeholder="Type or pick a team">
        </div>
      </div>
      <datalist id="adminTeamsList"></datalist>
      <div class="row2">
        <div class="field">
          <label for="adminScoreA">Team A score</label>
          <input id="adminScoreA" type="number" min="0" inputmode="numeric" placeholder="Leave blank if not final">
        </div>
        <div class="field">
          <label for="adminScoreB">Team B score</label>
          <input id="adminScoreB" type="number" min="0" inputmode="numeric" placeholder="Leave blank if not final">
        </div>
      </div>
      <div class="row2">
        <div class="field">
          <label for="adminWeek">Week</label>
          <select id="adminWeek">
            <option value="1">Week 1</option>
            <option value="2">Week 2</option>
            <option value="3">Week 3</option>
            <option value="4">Week 4</option>
            <option value="5">Week 5</option>
            <option value="6">Week 6</option>
            <option value="7">Playoffs · First Round</option>
            <option value="8">Playoffs · Round of 16</option>
            <option value="9">Playoffs · Quarterfinals</option>
            <option value="10">Playoffs · Semifinals</option>
            <option value="11">Championship</option>
          </select>
        </div>
        <div class="field">
          <label for="adminDate">Date</label>
          <input id="adminDate" type="date">
        </div>
      </div>
      <div class="row2">
        <div class="field">
          <label for="adminTime">Time</label>
          <input id="adminTime" type="time">
        </div>
        <div class="field">
          <label for="adminVenue">Venue</label>
          <input id="adminVenue" type="text" placeholder="Cottonwood HS">
        </div>
      </div>

      <div class="admin-stats-block">
        <button class="stats-toggle-btn" type="button" id="adminStatsAToggle">+ Add player stats for Team A</button>
        <div class="stat-groups" id="adminStatsAWrap" style="display:none;">
          <div id="adminPlayerRowsA"></div>
          <button class="add-player-btn" type="button" id="adminAddPlayerA">+ Add player</button>
        </div>
      </div>
      <div class="admin-stats-block">
        <button class="stats-toggle-btn" type="button" id="adminStatsBToggle">+ Add player stats for Team B</button>
        <div class="stat-groups" id="adminStatsBWrap" style="display:none;">
          <div id="adminPlayerRowsB"></div>
          <button class="add-player-btn" type="button" id="adminAddPlayerB">+ Add player</button>
        </div>
      </div>

      <div class="modal-actions">
        <button class="btn" id="adminCancelEditBtn" type="button" style="display:none;">Cancel edit</button>
        <button class="btn primary" id="adminSubmitBtn" type="button" style="flex:1;">Add Matchup</button>
      </div>
    </div>

    <div class="admin-list-head">
      <h3>All Matchups</h3>
      <select id="adminWeekFilter" class="admin-week-filter">
        <option value="all">All Weeks</option>
      </select>
    </div>
    <div id="adminGameList"></div>
  </div>
</section>

<template id="rosterRowTemplate">
  <div class="roster-row">
    <input class="r-name" type="text" placeholder="Player name">
    <input class="r-position" type="text" placeholder="Pos" maxlength="4">
    <input class="r-number" type="text" placeholder="#" inputmode="numeric" maxlength="3">
    <button class="remove-player-btn" type="button" title="Remove player">✕</button>
  </div>
</template>

<footer>
  <div>
    <div>Copyright © 2026 UHSGFA / All Rights Reserved.</div>
    <div>Non-Profit Organization / 501(c)(3)</div>
  </div>
  <div class="foot-links">
    <a href="https://www.facebook.com/profile.php?id=61578391628554">Facebook</a>
    <a href="https://www.instagram.com/uhsgfa">Instagram</a>
    <a href="https://www.x.com/uhsgfa">X</a>
  </div>
</footer>

<!-- Login modal -->
<div class="overlay" id="loginOverlay">
  <div class="modal">
    <button class="coach-btn modal-close" id="loginClose" style="padding:6px 10px;">✕</button>
    <h3>Coach Login</h3>
    <p class="sub">Enter your team and the coach passcode to post game results.</p>
    <div class="field">
      <label for="teamSelect">Your team</label>
      <select id="teamSelect"></select>
    </div>
    <div class="field">
      <label for="passInput">Coach passcode</label>
      <input id="passInput" type="text" placeholder="Enter passcode" autocomplete="off" autocapitalize="off" spellcheck="false">
    </div>
    <div class="modal-actions">
      <button class="btn primary" id="loginSubmit" style="flex:1;">Log in</button>
    </div>
  </div>
</div>

<!-- Admin login modal -->
<div class="overlay" id="adminLoginOverlay">
  <div class="modal">
    <button class="coach-btn modal-close" id="adminLoginClose" style="padding:6px 10px;">✕</button>
    <h3>Admin Login</h3>
    <p class="sub">Enter the admin passcode to schedule matchups and set game times.</p>
    <div class="field">
      <label for="adminPassInput">Admin passcode</label>
      <input id="adminPassInput" type="text" placeholder="Enter passcode" autocomplete="off" autocapitalize="off" spellcheck="false">
    </div>
    <div class="modal-actions">
      <button class="btn primary" id="adminLoginSubmit" style="flex:1;">Log in</button>
    </div>
  </div>
</div>

<!-- Admin: quick score entry modal (opened directly from a scoreboard card) -->
<div class="overlay" id="adminScoreOverlay">
  <div class="modal">
    <button class="coach-btn modal-close" id="adminScoreClose" style="padding:6px 10px;">✕</button>
    <h3>Enter Final Score</h3>
    <p class="sub" id="adminScoreSub"></p>
    <div class="row2">
      <div class="field">
        <label id="adminScoreALabel">Team A score</label>
        <input id="adminScoreModalA" type="number" min="0" inputmode="numeric">
      </div>
      <div class="field">
        <label id="adminScoreBLabel">Team B score</label>
        <input id="adminScoreModalB" type="number" min="0" inputmode="numeric">
      </div>
    </div>
    <div class="modal-actions">
      <button class="btn" id="adminScoreCancel">Cancel</button>
      <button class="btn primary" id="adminScoreSubmit" style="flex:1;">Save Score</button>
    </div>
    <div class="note">Saved instantly — no need to open the Admin tab.</div>
  </div>
</div>

<!-- Post/edit result modal -->
<div class="overlay" id="resultOverlay">
  <div class="modal modal-wide">
    <button class="coach-btn modal-close" id="resultClose" style="padding:6px 10px;">✕</button>
    <h3 id="resultTitle">Post Result</h3>
    <p class="sub" id="resultSub"></p>

    <div class="row2">
      <div class="field">
        <label>Your score</label>
        <input id="scoreFor" type="number" min="0" inputmode="numeric">
      </div>
      <div class="field">
        <label>Opponent score</label>
        <input id="scoreAgainst" type="number" min="0" inputmode="numeric">
      </div>
    </div>

    <div class="stat-entry">
      <div class="stat-entry-head">
        <label>Player stats</label>
        <span class="stat-entry-sub">Add a row for each player who had a notable stat line.</span>
      </div>
      <div id="rosterQuickAdd" class="roster-quick-add" style="display:none;">
        <span class="rqa-label">From your roster:</span>
        <div id="rosterChips" class="rqa-chips"></div>
      </div>
      <div id="playerRows"></div>
      <button class="add-player-btn" id="addPlayerBtn" type="button">+ Add player</button>
    </div>

    <div class="modal-actions">
      <button class="btn" id="resultCancel">Cancel</button>
      <button class="btn primary" id="resultSubmit">Post Score</button>
    </div>
  </div>
</div>

<!-- Template for one player stat row -->
<template id="playerRowTemplate">
  <div class="player-row">
    <div class="player-row-top">
      <input class="p-name" type="text" placeholder="Player name">
      <input class="p-jersey" type="text" placeholder="#" inputmode="numeric" maxlength="3">
      <input class="p-position" type="text" placeholder="Pos" maxlength="4">
      <button class="remove-player-btn" type="button" title="Remove player">✕</button>
    </div>
    <button class="stats-toggle-btn" type="button">+ Add stats</button>
    <div class="stat-groups" style="display:none;">
      <div class="stat-group">
        <div class="stat-group-title">Rushing</div>
        <div class="stat-group-fields">
          <div class="stat-mini2"><label>Att</label><input class="p-rushAtt" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>Yds</label><input class="p-rushYds" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>TD</label><input class="p-rushTD" type="number" min="0" inputmode="numeric"></div>
        </div>
      </div>
      <div class="stat-group">
        <div class="stat-group-title">Receiving</div>
        <div class="stat-group-fields">
          <div class="stat-mini2"><label>Rec</label><input class="p-rec" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>Yds</label><input class="p-recYds" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>TD</label><input class="p-recTD" type="number" min="0" inputmode="numeric"></div>
        </div>
      </div>
      <div class="stat-group">
        <div class="stat-group-title">Passing</div>
        <div class="stat-group-fields">
          <div class="stat-mini2"><label>Att</label><input class="p-passAtt" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>Cmp</label><input class="p-passCmp" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>Yds</label><input class="p-passYds" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>TD</label><input class="p-passTD" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>INT</label><input class="p-passINT" type="number" min="0" inputmode="numeric"></div>
        </div>
      </div>
      <div class="stat-group">
        <div class="stat-group-title">Defense</div>
        <div class="stat-group-fields">
          <div class="stat-mini2"><label>INT</label><input class="p-defINT" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>Pulls</label><input class="p-flagPulls" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>Sacks</label><input class="p-sacks" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>TD</label><input class="p-defTD" type="number" min="0" inputmode="numeric"></div>
        </div>
      </div>
      <div class="stat-group">
        <div class="stat-group-title">Extra Pts</div>
        <div class="stat-group-fields">
          <div class="stat-mini2"><label>1-Pt</label><input class="p-pt1" type="number" min="0" inputmode="numeric"></div>
          <div class="stat-mini2"><label>2-Pt</label><input class="p-pt2" type="number" min="0" inputmode="numeric"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<div class="toast" id="toast"></div>

<script>
(function () {
  // ---------- Stat categories (matches the MaxPreps Flag Football Stat Sheet) ----------
  var STAT_FIELD_DEFS = [
    { key: 'rushAtt',   line1: 'Rush',      line2: 'Attempts',    friendly: 'rush att' },
    { key: 'rushYds',   line1: 'Rush',      line2: 'Yards',       friendly: 'rush yds' },
    { key: 'rushTD',    line1: 'Rush',      line2: 'TD',          friendly: 'rush TD' },
    { key: 'rec',       line1: 'Receiving', line2: 'Catches',     friendly: 'rec' },
    { key: 'recYds',    line1: 'Receiving', line2: 'Yards',       friendly: 'rec yds' },
    { key: 'recTD',     line1: 'Receiving', line2: 'TD',          friendly: 'rec TD' },
    { key: 'passAtt',   line1: 'Pass',      line2: 'Attempts',    friendly: 'pass att' },
    { key: 'passCmp',   line1: 'Pass',      line2: 'Completions', friendly: 'pass cmp' },
    { key: 'passYds',   line1: 'Pass',      line2: 'Yards',       friendly: 'pass yds' },
    { key: 'passTD',    line1: 'Pass',      line2: 'TD',          friendly: 'pass TD' },
    { key: 'passINT',   line1: 'Pass',      line2: 'INT',         friendly: 'pass INT' },
    { key: 'defINT',    line1: 'Defense',   line2: 'INT',         friendly: 'def INT' },
    { key: 'flagPulls', line1: 'Flag',      line2: 'Pulls',       friendly: 'flag pulls' },
    { key: 'sacks',     line1: 'Defense',   line2: 'Sacks',       friendly: 'sacks' },
    { key: 'defTD',     line1: 'Defense',   line2: 'TD',          friendly: 'def TD' },
    { key: 'pt1',       line1: '1-Pt',      line2: 'Conv',        friendly: '1-pt conv' },
    { key: 'pt2',       line1: '2-Pt',      line2: 'Conv',        friendly: '2-pt conv' }
  ];
  var STAT_FIELD_KEYS = STAT_FIELD_DEFS.map(function (f) { return f.key; });

  // Generic sortable stat table. leadColumns describes the non-stat columns
  // on the left (Player/Pos/# for a roster, Team for a comparison view).
  // Clicking any stat header sorts the rows by that column (desc, then
  // asc on a second click); clicking a row (if onRowClick given) drills in.
  var LEAD_COL_WIDTH = { name: 132, team: 122, position: 56, number: 46 };

  function buildStatTable(rows, leadColumns, onRowClick) {
    var tableWrap = document.createElement('div');
    tableWrap.className = 'stat-table-wrap';
    var table = document.createElement('table');
    table.className = 'stat-table';
    var thead = document.createElement('thead');
    var headRow = document.createElement('tr');

    // Compute each lead column's fixed width and cumulative left offset so
    // the whole identifying block (name/team/pos/#) locks together as one
    // unit while the stat columns scroll underneath it.
    var cumLeft = 0;
    var leadLayout = leadColumns.map(function (col) {
      var width = LEAD_COL_WIDTH[col.key] || 90;
      var left = cumLeft;
      cumLeft += width;
      return { col: col, width: width, left: left };
    });
    var lastLeadIdx = leadLayout.length - 1;

    leadLayout.forEach(function (item, i) {
      var th = document.createElement('th');
      th.className = 'stt-name stt-sticky' + (i === lastLeadIdx ? ' stt-sticky-edge' : '');
      th.style.left = item.left + 'px';
      th.style.width = item.width + 'px';
      th.style.minWidth = item.width + 'px';
      th.textContent = item.col.label;
      headRow.appendChild(th);
    });

    var sortKey = null;
    var sortDir = -1; // -1 = highest first, 1 = lowest first
    var tbody = document.createElement('tbody');

    function renderBody() {
      tbody.innerHTML = '';
      var sorted = rows.slice();
      if (sortKey) {
        sorted.sort(function (a, b) { return ((a[sortKey] || 0) - (b[sortKey] || 0)) * sortDir; });
      }
      sorted.forEach(function (r) {
        var tr = document.createElement('tr');
        if (onRowClick) tr.className = 'team-compare-row';
        leadLayout.forEach(function (item, i) {
          var col = item.col;
          var val = col.key === 'position' ? (r[col.key] || '').toUpperCase() : (r[col.key] || '');
          var td = document.createElement('td');
          td.className = 'stt-name stt-sticky' + (i === lastLeadIdx ? ' stt-sticky-edge' : '');
          td.style.left = item.left + 'px';
          td.style.width = item.width + 'px';
          td.style.minWidth = item.width + 'px';
          td.textContent = String(val);
          tr.appendChild(td);
        });
        STAT_FIELD_DEFS.forEach(function (f) {
          var td = document.createElement('td');
          if (sortKey === f.key) td.className = 'stt-sorted';
          td.textContent = r[f.key] || 0;
          tr.appendChild(td);
        });
        if (onRowClick) tr.addEventListener('click', function () { onRowClick(r); });
        tbody.appendChild(tr);
      });
    }

    STAT_FIELD_DEFS.forEach(function (f) {
      var th = document.createElement('th');
      th.className = 'stt-sortable';
      th.innerHTML = '<span>' + f.line1 + '</span><span>' + f.line2 + '</span>';
      th.title = 'Sort by ' + f.line1 + ' ' + f.line2;
      th.addEventListener('click', function () {
        if (sortKey === f.key) { sortDir = sortDir * -1; } else { sortKey = f.key; sortDir = -1; }
        table.querySelectorAll('.stt-sortable').forEach(function (h) { h.classList.remove('active-sort'); });
        th.classList.add('active-sort');
        renderBody();
      });
      headRow.appendChild(th);
    });

    thead.appendChild(headRow);
    table.appendChild(thead);
    table.appendChild(tbody);
    renderBody();
    tableWrap.appendChild(table);
    return tableWrap;
  }

  function buildFullStatTable(players) {
    return buildStatTable(players, [
      { key: 'name', label: 'Player' },
      { key: 'position', label: 'Pos' },
      { key: 'number', label: '#' }
    ]);
  }

  // ---------- Team list ----------
  // Pulled directly from the 2026 UHSGFA Regular Season Schedule PDF.
  var TEAMS = [
    "Bingham", "Carbon", "Cottonwood", "Farmington", "Farmington JV",
    "Granger", "Juan Diego", "Lone Peak", "Maple Mountain", "Northridge",
    "Olympus", "Park City Black", "Park City Red", "Park City White",
    "Riverton", "Skyridge", "Timpview", "Woods Cross"
  ];

  // ---------- Seed schedule ----------
  // Real 2026 regular-season matchups from the UHSGFA schedule PDF.
  // No scores are included since the source document is a schedule, not
  // results — every game starts as "scheduled" until a coach or admin
  // posts the real outcome.
  var SEED_GAMES = [
    { id: "g1", week: 1, dateLabel: "9/14 @ 7:30p / Cottonwood HS", teamA: "Carbon", teamB: "Woods Cross", status: "scheduled" },
    { id: "g2", week: 1, dateLabel: "9/14 @ 9:15p / Cottonwood HS", teamA: "Granger", teamB: "Bingham", status: "scheduled" },
    { id: "g3", week: 1, dateLabel: "9/15 @ 7:30p / Cottonwood HS", teamA: "Skyridge", teamB: "Timpview", status: "scheduled" },
    { id: "g4", week: 1, dateLabel: "9/15 @ 9:15p / Cottonwood HS", teamA: "Park City White", teamB: "Maple Mountain", status: "scheduled" },
    { id: "g5", week: 1, dateLabel: "9/15 @ 7:30p / Juan Diego HS", teamA: "Riverton", teamB: "Park City Red", status: "scheduled" },
    { id: "g6", week: 1, dateLabel: "9/15 @ 9:15p / Juan Diego HS", teamA: "Juan Diego", teamB: "Park City Black", status: "scheduled" },
    { id: "g7", week: 1, dateLabel: "9/16 @ 7:30p / Cottonwood HS", teamA: "Cottonwood", teamB: "Olympus", status: "scheduled" },
    { id: "g8", week: 1, dateLabel: "9/19 @ 6:00p / Farmington HS", teamA: "Farmington JV", teamB: "Lone Peak", status: "scheduled" },
    { id: "g9", week: 1, dateLabel: "9/19 @ 7:30p / Farmington HS", teamA: "Farmington", teamB: "Northridge", status: "scheduled" },
    { id: "g10", week: 2, dateLabel: "9/19 @ 5:30p / Juan Diego HS", teamA: "Granger", teamB: "Park City White", status: "scheduled" },
    { id: "g11", week: 2, dateLabel: "9/19 @ 7:15p / Juan Diego HS", teamA: "Skyridge", teamB: "Maple Mountain", status: "scheduled" },
    { id: "g12", week: 2, dateLabel: "9/21 @ 7:30p / Cottonwood HS", teamA: "Lone Peak", teamB: "Park City Red", status: "scheduled" },
    { id: "g13", week: 2, dateLabel: "9/21 @ 9:15p / Cottonwood HS", teamA: "Bingham", teamB: "Park City Black", status: "scheduled" },
    { id: "g14", week: 2, dateLabel: "9/22 @ 7:30p / Cottonwood HS", teamA: "Timpview", teamB: "Farmington JV", status: "scheduled" },
    { id: "g15", week: 2, dateLabel: "9/22 @ 9:15p / Cottonwood HS", teamA: "Olympus", teamB: "Farmington", status: "scheduled" },
    { id: "g16", week: 2, dateLabel: "9/26 @ 5:30p / Juan Diego HS", teamA: "Northridge", teamB: "Juan Diego", status: "scheduled" },
    { id: "g17", week: 2, dateLabel: "9/26 @ 7:15p / Juan Diego HS", teamA: "Riverton", teamB: "Carbon", status: "scheduled" },
    { id: "g18", week: 2, dateLabel: "9/30 @ 9:15p / Cottonwood HS", teamA: "Woods Cross", teamB: "Cottonwood", status: "scheduled" },
    { id: "g19", week: 3, dateLabel: "9/28 @ 7:30p / Cottonwood HS", teamA: "Park City White", teamB: "Northridge", status: "scheduled" },
    { id: "g20", week: 3, dateLabel: "9/28 @ 9:15p / Cottonwood HS", teamA: "Olympus", teamB: "Riverton", status: "scheduled" },
    { id: "g21", week: 3, dateLabel: "9/29 @ 7:30p / Juan Diego HS", teamA: "Lone Peak", teamB: "Carbon", status: "scheduled" },
    { id: "g22", week: 3, dateLabel: "9/29 @ 9:15p / Juan Diego HS", teamA: "Juan Diego", teamB: "Bingham", status: "scheduled" },
    { id: "g23", week: 3, dateLabel: "9/30 @ 7:30p / Cottonwood HS", teamA: "Maple Mountain", teamB: "Granger", status: "scheduled" },
    { id: "g24", week: 3, dateLabel: "10/3 @ 6:00p / Farmington HS", teamA: "Farmington JV", teamB: "Woods Cross", status: "scheduled" },
    { id: "g25", week: 3, dateLabel: "10/3 @ 7:30p / Farmington HS", teamA: "Farmington", teamB: "Timpview", status: "scheduled" },
    { id: "g26", week: 3, dateLabel: "10/3 @ 5:30p / Juan Diego HS", teamA: "Park City Red", teamB: "Cottonwood", status: "scheduled" },
    { id: "g27", week: 3, dateLabel: "10/3 @ 7:15p / Juan Diego HS", teamA: "Park City Black", teamB: "Skyridge", status: "scheduled" },
    { id: "g28", week: 4, dateLabel: "10/5 @ 7:30p / Cottonwood HS", teamA: "Park City White", teamB: "Cottonwood", status: "scheduled" },
    { id: "g29", week: 4, dateLabel: "10/5 @ 9:15p / Cottonwood HS", teamA: "Bingham", teamB: "Riverton", status: "scheduled" },
    { id: "g30", week: 4, dateLabel: "10/6 @ 7:30p / Cottonwood HS", teamA: "Park City Red", teamB: "Skyridge", status: "scheduled" },
    { id: "g31", week: 4, dateLabel: "10/6 @ 9:15p / Cottonwood HS", teamA: "Park City Black", teamB: "Olympus", status: "scheduled" },
    { id: "g32", week: 4, dateLabel: "10/7 @ 7:30p / Cottonwood HS", teamA: "Northridge", teamB: "Granger", status: "scheduled" },
    { id: "g33", week: 4, dateLabel: "10/10 @ 6:00p / Farmington HS", teamA: "Carbon", teamB: "Farmington JV", status: "scheduled" },
    { id: "g34", week: 4, dateLabel: "10/10 @ 7:30p / Farmington HS", teamA: "Woods Cross", teamB: "Farmington", status: "scheduled" },
    { id: "g35", week: 4, dateLabel: "10/10 @ 5:30p / Juan Diego HS", teamA: "Juan Diego", teamB: "Lone Peak", status: "scheduled" },
    { id: "g36", week: 4, dateLabel: "10/10 @ 7:15p / Juan Diego HS", teamA: "Timpview", teamB: "Maple Mountain", status: "scheduled" },
    { id: "g37", week: 5, dateLabel: "10/12 @ 7:30p / Cottonwood HS", teamA: "Granger", teamB: "Skyridge", status: "scheduled" },
    { id: "g38", week: 5, dateLabel: "10/12 @ 9:15p / Cottonwood HS", teamA: "Woods Cross", teamB: "Northridge", status: "scheduled" },
    { id: "g39", week: 5, dateLabel: "10/13 @ 7:30p / Cottonwood HS", teamA: "Farmington JV", teamB: "Park City White", status: "scheduled" },
    { id: "g40", week: 5, dateLabel: "10/13 @ 9:15p / Cottonwood HS", teamA: "Farmington", teamB: "Riverton", status: "scheduled" },
    { id: "g41", week: 5, dateLabel: "10/14 @ TBD / Park City?", teamA: "Park City Red", teamB: "Bingham", status: "scheduled" },
    { id: "g42", week: 5, dateLabel: "10/14 @ TBD / Park City?", teamA: "Cottonwood", teamB: "Park City Black", status: "scheduled" },
    { id: "g43", week: 5, dateLabel: "10/17 @ 5:30p / Carbon HS", teamA: "Maple Mountain", teamB: "Carbon", status: "scheduled" },
    { id: "g44", week: 5, dateLabel: "10/17 @ 5:30p / Juan Diego HS", teamA: "Timpview", teamB: "Lone Peak", status: "scheduled" },
    { id: "g45", week: 5, dateLabel: "10/17 @ 7:15p / Juan Diego HS", teamA: "Olympus", teamB: "Juan Diego", status: "scheduled" },
    { id: "g46", week: 6, dateLabel: "10/19 @ 7:30p / Cottonwood HS", teamA: "Olympus", teamB: "Timpview", status: "scheduled" },
    { id: "g47", week: 6, dateLabel: "10/19 @ 9:15p / Cottonwood HS", teamA: "Maple Mountain", teamB: "Lone Peak", status: "scheduled" },
    { id: "g48", week: 6, dateLabel: "10/20 @ 7:30p / Juan Diego HS", teamA: "Bingham", teamB: "Park City White", status: "scheduled" },
    { id: "g49", week: 6, dateLabel: "10/20 @ 9:15p / Juan Diego HS", teamA: "Cottonwood", teamB: "Juan Diego", status: "scheduled" },
    { id: "g50", week: 6, dateLabel: "10/21 @ 7:30p / Cottonwood HS", teamA: "Riverton", teamB: "Granger", status: "scheduled" },
    { id: "g51", week: 6, dateLabel: "10/24 @ 6:00p / Farmington HS", teamA: "Northridge", teamB: "Farmington JV", status: "scheduled" },
    { id: "g52", week: 6, dateLabel: "10/24 @ 7:30p / Farmington HS", teamA: "Skyridge", teamB: "Farmington", status: "scheduled" },
    { id: "g53", week: 6, dateLabel: "10/24 @ 5:30p / Juan Diego HS", teamA: "Park City Red", teamB: "Carbon", status: "scheduled" },
    { id: "g54", week: 6, dateLabel: "10/24 @ 7:15p / Juan Diego HS", teamA: "Park City Black", teamB: "Woods Cross", status: "scheduled" },

    // Playoffs — real bracket/dates from uhsgfa.org/calendar. Seeds aren't
    // determined until the regular season standings are final, so these
    // use the same seed placeholders the real site shows.
    { id: "g55", week: 7, weekLabel: "Playoffs · First Round", dateLabel: "10/26 @ 7:30p / Cottonwood HS", teamA: "Seed 15", teamB: "Seed 18", status: "scheduled" },
    { id: "g56", week: 7, weekLabel: "Playoffs · First Round", dateLabel: "10/26 @ 9:00p / Cottonwood HS", teamA: "Seed 16", teamB: "Seed 17", status: "scheduled" },

    { id: "g57", week: 8, weekLabel: "Playoffs · Round of 16", dateLabel: "10/26 @ 7:30p / Juan Diego HS", teamA: "Seed 4", teamB: "Seed 13", status: "scheduled" },
    { id: "g58", week: 8, weekLabel: "Playoffs · Round of 16", dateLabel: "10/26 @ 9:00p / Juan Diego HS", teamA: "Seed 3", teamB: "Seed 14", status: "scheduled" },
    { id: "g59", week: 8, weekLabel: "Playoffs · Round of 16", dateLabel: "10/27 @ 7:30p / TBD", teamA: "Seed 6", teamB: "Seed 11", status: "scheduled" },
    { id: "g60", week: 8, weekLabel: "Playoffs · Round of 16", dateLabel: "10/27 @ 7:30p / Cottonwood HS", teamA: "Seed 2", teamB: "Highest Seed from 10/26", status: "scheduled" },
    { id: "g61", week: 8, weekLabel: "Playoffs · Round of 16", dateLabel: "10/27 @ 9:00p / Cottonwood HS", teamA: "Seed 1", teamB: "Lowest Seed from 10/26", status: "scheduled" },
    { id: "g62", week: 8, weekLabel: "Playoffs · Round of 16", dateLabel: "10/27 @ 9:00p / TBD", teamA: "Seed 5", teamB: "Seed 12", status: "scheduled" },
    { id: "g63", week: 8, weekLabel: "Playoffs · Round of 16", dateLabel: "10/28 @ 7:30p / Cottonwood HS", teamA: "Seed 7", teamB: "Seed 10", status: "scheduled" },
    { id: "g64", week: 8, weekLabel: "Playoffs · Round of 16", dateLabel: "10/28 @ 9:00p / Cottonwood HS", teamA: "Seed 8", teamB: "Seed 9", status: "scheduled" },

    { id: "g65", week: 9, weekLabel: "Playoffs · Quarterfinals", dateLabel: "11/2 @ 7:00p / Field 1 \u00b7 TBD", teamA: "TBD", teamB: "TBD", status: "scheduled" },
    { id: "g66", week: 9, weekLabel: "Playoffs · Quarterfinals", dateLabel: "11/3 @ 7:00p / Field 2 \u00b7 TBD", teamA: "TBD", teamB: "TBD", status: "scheduled" },

    { id: "g67", week: 10, weekLabel: "Playoffs · Semifinals", dateLabel: "11/7 @ 7:00p / TBD", teamA: "TBD", teamB: "TBD", status: "scheduled" },

    { id: "g68", week: 11, weekLabel: "2026 UHSGFA Championship", dateLabel: "11/13 @ 7:00p / TBD", teamA: "TBD", teamB: "TBD", status: "scheduled" },
  ];

  var els = {
    scoreboard: document.getElementById('scoreboard'),
    coachBtn: document.getElementById('coachBtn'),
    loginOverlay: document.getElementById('loginOverlay'),
    loginClose: document.getElementById('loginClose'),
    teamSelect: document.getElementById('teamSelect'),
    passInput: document.getElementById('passInput'),
    loginSubmit: document.getElementById('loginSubmit'),
    resultOverlay: document.getElementById('resultOverlay'),
    resultClose: document.getElementById('resultClose'),
    resultTitle: document.getElementById('resultTitle'),
    resultSub: document.getElementById('resultSub'),
    scoreFor: document.getElementById('scoreFor'),
    scoreAgainst: document.getElementById('scoreAgainst'),
    playerRows: document.getElementById('playerRows'),
    addPlayerBtn: document.getElementById('addPlayerBtn'),
    playerRowTemplate: document.getElementById('playerRowTemplate'),
    resultCancel: document.getElementById('resultCancel'),
    resultSubmit: document.getElementById('resultSubmit'),
    toast: document.getElementById('toast'),
    siteTabs: document.getElementById('siteTabs'),
    tabMyTeamBtn: document.getElementById('tabMyTeamBtn'),
    myTeamPanel: document.getElementById('myTeamPanel'),
    myTeamTitle: document.getElementById('myTeamTitle'),
    rosterRows: document.getElementById('rosterRows'),
    rosterRowTemplate: document.getElementById('rosterRowTemplate'),
    addRosterPlayerBtn: document.getElementById('addRosterPlayerBtn'),
    saveRosterBtn: document.getElementById('saveRosterBtn'),
    rosterStatus: document.getElementById('rosterStatus'),
    rosterQuickAdd: document.getElementById('rosterQuickAdd'),
    rosterChips: document.getElementById('rosterChips'),
    teamGrid: document.getElementById('teamGrid'),
    teamGridCalendar: document.getElementById('teamGridCalendar'),
    teamsFilterHintCal: document.getElementById('teamsFilterHintCal'),
    downloadScheduleBtn: document.getElementById('downloadScheduleBtn'),
    statsModeSelect: document.getElementById('statsModeSelect'),
    statsTeamPanel: document.getElementById('statsTeamPanel'),
    statsIndividualPanel: document.getElementById('statsIndividualPanel'),
    statsTeamSelect: document.getElementById('statsTeamSelect'),
    statsTeamContent: document.getElementById('statsTeamContent'),
    statsIndivTeamSelect: document.getElementById('statsIndivTeamSelect'),
    statsIndivPlayerSelect: document.getElementById('statsIndivPlayerSelect'),
    statsIndivPlayerField: document.getElementById('statsIndivPlayerField'),
    statsIndivContent: document.getElementById('statsIndivContent'),
    teamsFilterHint: document.getElementById('teamsFilterHint'),
    adminBtn: document.getElementById('adminBtn'),
    adminLoginOverlay: document.getElementById('adminLoginOverlay'),
    adminLoginClose: document.getElementById('adminLoginClose'),
    adminPassInput: document.getElementById('adminPassInput'),
    adminLoginSubmit: document.getElementById('adminLoginSubmit'),
    tabAdminBtn: document.getElementById('tabAdminBtn'),
    adminWeek: document.getElementById('adminWeek'),
    adminVenue: document.getElementById('adminVenue'),
    adminTeamA: document.getElementById('adminTeamA'),
    adminTeamB: document.getElementById('adminTeamB'),
    adminDate: document.getElementById('adminDate'),
    adminTime: document.getElementById('adminTime'),
    adminScoreA: document.getElementById('adminScoreA'),
    adminScoreB: document.getElementById('adminScoreB'),
    adminSubmitBtn: document.getElementById('adminSubmitBtn'),
    adminCancelEditBtn: document.getElementById('adminCancelEditBtn'),
    adminGameList: document.getElementById('adminGameList'),
    adminStatsAToggle: document.getElementById('adminStatsAToggle'),
    adminStatsAWrap: document.getElementById('adminStatsAWrap'),
    adminPlayerRowsA: document.getElementById('adminPlayerRowsA'),
    adminAddPlayerA: document.getElementById('adminAddPlayerA'),
    adminStatsBToggle: document.getElementById('adminStatsBToggle'),
    adminStatsBWrap: document.getElementById('adminStatsBWrap'),
    adminPlayerRowsB: document.getElementById('adminPlayerRowsB'),
    adminAddPlayerB: document.getElementById('adminAddPlayerB'),
    adminScoreOverlay: document.getElementById('adminScoreOverlay'),
    adminScoreClose: document.getElementById('adminScoreClose'),
    adminScoreCancel: document.getElementById('adminScoreCancel'),
    adminScoreSub: document.getElementById('adminScoreSub'),
    adminScoreALabel: document.getElementById('adminScoreALabel'),
    adminScoreBLabel: document.getElementById('adminScoreBLabel'),
    adminScoreModalA: document.getElementById('adminScoreModalA'),
    adminScoreModalB: document.getElementById('adminScoreModalB'),
    adminScoreSubmit: document.getElementById('adminScoreSubmit'),
    adminWeekFilter: document.getElementById('adminWeekFilter'),
    calendarList: document.getElementById('calendarList'),
    bracketWrap: document.getElementById('bracketWrap'),
    standingsListView: document.getElementById('standingsListView'),
    standingsBody: document.getElementById('standingsBody'),
    teamDetailView: document.getElementById('teamDetailView'),
    teamDetailContent: document.getElementById('teamDetailContent'),
    backToStandingsBtn: document.getElementById('backToStandingsBtn')
  };

  var adminSession = false;
  var editingGameId = null;

  var rosters = {};     // teamSlug -> [{name, number}]
  var teamFilter = null; // team name currently filtering the scoreboard, or null

  var session = null;   // { team: "Union High" }
  var activeGameId = null;
  var db = null;
  var games = {};       // id -> game object, live state we render from

  SEED_GAMES.forEach(function (g) { games[g.id] = g; });

  TEAMS.forEach(function (t) {
    var opt = document.createElement('option');
    opt.value = t; opt.textContent = t;
    els.teamSelect.appendChild(opt);
  });

  var adminTeamsListEl = document.getElementById('adminTeamsList');
  TEAMS.forEach(function (t) {
    var opt = document.createElement('option');
    opt.value = t;
    adminTeamsListEl.appendChild(opt);
  });
  // Common playoff placeholders, so they're suggested too without blocking free typing.
  ['TBD', 'Highest Seed from 10/26', 'Lowest Seed from 10/26'].concat(
    Array.from({ length: 18 }, function (_, i) { return 'Seed ' + (i + 1); })
  ).forEach(function (name) {
    var opt = document.createElement('option');
    opt.value = name;
    adminTeamsListEl.appendChild(opt);
  });

  function showToast(msg) {
    els.toast.textContent = msg;
    els.toast.classList.add('show');
    setTimeout(function () { els.toast.classList.remove('show'); }, 2200);
  }

  function render() {
    var byWeek = {};
    Object.keys(games).forEach(function (id) {
      var g = games[id];
      if (teamFilter && g.teamA !== teamFilter && g.teamB !== teamFilter) return;
      byWeek[g.week] = byWeek[g.week] || [];
      byWeek[g.week].push(g);
    });
    var weekNums = Object.keys(byWeek).map(Number);
    function isWeekComplete(w) {
      return byWeek[w].every(function (g) { return g.status === 'final'; });
    }
    var liveWeeks = weekNums.filter(function (w) { return !isWeekComplete(w); }).sort(function (a, b) { return a - b; });
    var doneWeeks = weekNums.filter(function (w) { return isWeekComplete(w); }).sort(function (a, b) { return a - b; });
    var weeks = liveWeeks.concat(doneWeeks);

    els.scoreboard.innerHTML = '';
    if (!weeks.length) {
      var empty = document.createElement('div');
      empty.className = 'empty';
      empty.textContent = teamFilter ? (teamFilter + ' has no games yet.') : 'No games yet.';
      els.scoreboard.appendChild(empty);
    }
    weeks.forEach(function (w) {
      var head = document.createElement('div');
      head.className = 'week-head';
      var label = (byWeek[w][0] && byWeek[w][0].weekLabel) ? byWeek[w][0].weekLabel : ('Week ' + w);
      var doneTag = isWeekComplete(w) ? '<span class="week-done-tag">Complete</span>' : '';
      head.innerHTML = '<h2>' + escapeHtml(label) + '</h2>' + doneTag;
      els.scoreboard.appendChild(head);

      byWeek[w].slice().sort(function (a, b) {
        var pa = parseDateLabel(a.dateLabel);
        var pb = parseDateLabel(b.dateLabel);
        var ka = pa ? (pa.date + 'T' + (pa.time || '99:99')) : '9999';
        var kb = pb ? (pb.date + 'T' + (pb.time || '99:99')) : '9999';
        return ka < kb ? -1 : (ka > kb ? 1 : 0);
      }).forEach(function (g) {
        els.scoreboard.appendChild(renderGame(g));
      });
    });

    renderCalendar();
    renderBracket();
    renderStandings();
    if (currentTab === 'standings' && els.teamDetailView.style.display !== 'none') {
      // a team detail card is open while data changed underneath it — refresh in place
      var openTeamEl = els.teamDetailContent.querySelector('.team-detail-head h2');
      if (openTeamEl) showTeamDetail(openTeamEl.textContent);
    }
    if (currentTab === 'stats') {
      if (els.statsModeSelect.value === 'team') {
        renderStatsTeamContent();
      } else {
        renderStatsIndivContent();
      }
    }
  }

  var MONTH_ABBR = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];

  function renderCalendar() {
    if (!els.calendarList) return;
    els.calendarList.innerHTML = '';

    var upcoming = Object.keys(games)
      .map(function (id) { return games[id]; })
      .filter(function (g) { return g.status === 'scheduled'; })
      .filter(function (g) { return !teamFilter || g.teamA === teamFilter || g.teamB === teamFilter; })
      .map(function (g) {
        var parsed = parseDateLabel(g.dateLabel);
        return { g: g, parsed: parsed, sortKey: parsed ? (parsed.date + 'T' + (parsed.time || '99:99')) : '9999' };
      })
      .sort(function (a, b) { return a.sortKey < b.sortKey ? -1 : a.sortKey > b.sortKey ? 1 : 0; });

    if (!upcoming.length) {
      var empty = document.createElement('div');
      empty.className = 'empty';
      empty.textContent = teamFilter ? ('No upcoming games for ' + teamFilter + '.') : 'No upcoming games scheduled.';
      els.calendarList.appendChild(empty);
      return;
    }

    upcoming.forEach(function (item) {
      var g = item.g;
      var card = document.createElement('div');
      card.className = 'cal-event';

      var badge = document.createElement('div');
      badge.className = 'cal-date-badge';
      if (item.parsed) {
        var monthIdx = parseInt(item.parsed.date.split('-')[1], 10) - 1;
        var dayNum = parseInt(item.parsed.date.split('-')[2], 10);
        badge.innerHTML = '<div class="cal-month">' + MONTH_ABBR[monthIdx] + '</div><div class="cal-day">' + dayNum + '</div>';
      } else {
        badge.innerHTML = '<div class="cal-month">TBD</div><div class="cal-day">—</div>';
      }

      var info = document.createElement('div');
      info.className = 'cal-event-info';
      var title = document.createElement('div');
      title.className = 'cal-event-title';
      title.textContent = g.teamA + ' vs ' + g.teamB;
      var meta = document.createElement('div');
      meta.className = 'cal-event-meta';
      meta.textContent = g.dateLabel || 'Time TBD';
      info.appendChild(title);
      info.appendChild(meta);

      var weekTag = document.createElement('div');
      weekTag.className = 'cal-event-week';
      weekTag.textContent = g.weekLabel ? g.weekLabel : ('Wk ' + g.week);

      card.appendChild(badge);
      card.appendChild(info);
      card.appendChild(weekTag);
      els.calendarList.appendChild(card);
    });
  }

  // ---------- Playoff bracket ----------
  var BRACKET_ROUNDS = [
    { week: 7, title: 'First Round' },
    { week: 8, title: 'Round of 16' },
    { week: 9, title: 'Quarterfinals' },
    { week: 10, title: 'Semifinals' },
    { week: 11, title: 'Championship' }
  ];

  function renderBracket() {
    if (!els.bracketWrap) return;
    els.bracketWrap.innerHTML = '';
    var anyPlayoffGames = false;

    BRACKET_ROUNDS.forEach(function (round) {
      var roundGames = Object.keys(games)
        .map(function (id) { return games[id]; })
        .filter(function (g) { return g.week === round.week; })
        .sort(function (a, b) {
          var pa = parseDateLabel(a.dateLabel), pb = parseDateLabel(b.dateLabel);
          var ka = pa ? (pa.date + 'T' + (pa.time || '99:99')) : '9999';
          var kb = pb ? (pb.date + 'T' + (pb.time || '99:99')) : '9999';
          return ka < kb ? -1 : (ka > kb ? 1 : 0);
        });
      if (!roundGames.length) return;
      anyPlayoffGames = true;

      var col = document.createElement('div');
      col.className = 'bracket-col';
      var title = document.createElement('div');
      title.className = 'bracket-col-title';
      title.textContent = round.title;
      col.appendChild(title);

      roundGames.forEach(function (g) {
        var isFinal = g.status === 'final';
        var aWins = isFinal && g.scoreA > g.scoreB;
        var bWins = isFinal && g.scoreB > g.scoreA;

        var match = document.createElement('div');
        match.className = 'bracket-match';

        var rowA = document.createElement('div');
        rowA.className = 'bracket-team' + (aWins ? ' winner' : '');
        rowA.innerHTML =
          '<span class="bracket-team-name">' + escapeHtml(g.teamA) + '</span>' +
          (isFinal ? '<span class="bracket-team-score">' + g.scoreA + '</span>' : '');

        var rowB = document.createElement('div');
        rowB.className = 'bracket-team' + (bWins ? ' winner' : '');
        rowB.innerHTML =
          '<span class="bracket-team-name">' + escapeHtml(g.teamB) + '</span>' +
          (isFinal ? '<span class="bracket-team-score">' + g.scoreB + '</span>' : '');

        match.appendChild(rowA);
        if (!isFinal) {
          var vs = document.createElement('div');
          vs.className = 'bracket-vs';
          vs.textContent = 'vs';
          match.appendChild(vs);
        }
        match.appendChild(rowB);

        var meta = document.createElement('div');
        meta.className = 'bracket-match-meta';
        meta.textContent = g.dateLabel || 'Date TBD';
        match.appendChild(meta);

        col.appendChild(match);
      });

      els.bracketWrap.appendChild(col);
    });

    if (!anyPlayoffGames) {
      var empty = document.createElement('div');
      empty.className = 'empty';
      empty.textContent = 'No playoff matchups scheduled yet.';
      els.bracketWrap.appendChild(empty);
    }
  }

  // ---------- Standings & stats ----------
  var STAT_CATS = [
    { key: 'passYds', label: 'Pass Yds' },
    { key: 'passTD',  label: 'Pass TD' },
    { key: 'rushYds', label: 'Rush Yds' },
    { key: 'rushTD',  label: 'Rush TD' },
    { key: 'recYds',  label: 'Rec Yds' },
    { key: 'recTD',   label: 'Rec TD' },
    { key: 'sacks',   label: 'Sacks' },
    { key: 'flagPulls', label: 'Flag Pulls' }
  ];

  function computeStandings() {
    var table = {};
    TEAMS.forEach(function (t) { table[t] = { team: t, w: 0, l: 0, t_: 0, pf: 0, pa: 0 }; });

    Object.keys(games).forEach(function (id) {
      var g = games[id];
      if (g.status !== 'final') return;
      [g.teamA, g.teamB].forEach(function (t) {
        if (!table[t]) table[t] = { team: t, w: 0, l: 0, t_: 0, pf: 0, pa: 0 };
      });
      var rowA = table[g.teamA], rowB = table[g.teamB];
      rowA.pf += g.scoreA; rowA.pa += g.scoreB;
      rowB.pf += g.scoreB; rowB.pa += g.scoreA;
      if (g.scoreA > g.scoreB) { rowA.w++; rowB.l++; }
      else if (g.scoreB > g.scoreA) { rowB.w++; rowA.l++; }
      else { rowA.t_++; rowB.t_++; }
    });

    return Object.keys(table).map(function (t) { return table[t]; }).sort(function (a, b) {
      if (b.w !== a.w) return b.w - a.w;
      var diffA = a.pf - a.pa, diffB = b.pf - b.pa;
      if (diffB !== diffA) return diffB - diffA;
      return b.pf - a.pf;
    });
  }

  // Aggregated per-player season totals for one team, from final games only.
  function teamPlayerStats(team) {
    var byPlayer = {};
    Object.keys(games).forEach(function (id) {
      var g = games[id];
      if (g.status !== 'final') return;
      var mine = g.teamA === team ? g.statsA : (g.teamB === team ? g.statsB : null);
      if (!mine) return;
      mine.forEach(function (p) {
        var key = p.name;
        if (!byPlayer[key]) {
          byPlayer[key] = { name: p.name, position: p.position || '', number: p.number || '' };
          STAT_FIELD_KEYS.forEach(function (k) { byPlayer[key][k] = 0; });
        }
        STAT_FIELD_KEYS.forEach(function (k) { byPlayer[key][k] += p[k] || 0; });
        if (p.position) byPlayer[key].position = p.position;
        if (p.number) byPlayer[key].number = p.number;
      });
    });
    return Object.keys(byPlayer).map(function (k) { return byPlayer[k]; }).sort(function (a, b) {
      var totalA = a.rushYds + a.recYds + a.passYds;
      var totalB = b.rushYds + b.recYds + b.passYds;
      return totalB - totalA;
    });
  }

  // League-wide leaderboard for one stat category, across every team's players.
  function leagueLeaders(catKey, limit) {
    var byPlayer = {};
    Object.keys(games).forEach(function (id) {
      var g = games[id];
      if (g.status !== 'final') return;
      [[g.teamA, g.statsA], [g.teamB, g.statsB]].forEach(function (pair) {
        var team = pair[0], stats = pair[1];
        if (!stats) return;
        stats.forEach(function (p) {
          var key = team + '::' + p.name;
          if (!byPlayer[key]) byPlayer[key] = { name: p.name, team: team, position: p.position || '', value: 0 };
          byPlayer[key].value += p[catKey] || 0;
          if (p.position) byPlayer[key].position = p.position;
        });
      });
    });
    var arr = Object.keys(byPlayer).map(function (k) { return byPlayer[k]; })
      .filter(function (p) { return p.value > 0; })
      .sort(function (a, b) { return b.value - a.value; });
    return limit ? arr.slice(0, limit) : arr;
  }

  function renderStandings() {
    if (!els.standingsBody) return;
    var rows = computeStandings();
    els.standingsBody.innerHTML = '';
    rows.forEach(function (r) {
      var tr = document.createElement('tr');
      var diff = r.pf - r.pa;
      var diffClass = diff > 0 ? 'st-diff-pos' : (diff < 0 ? 'st-diff-neg' : '');
      var record = r.w + '-' + r.l + (r.t_ ? ('-' + r.t_) : '');
      tr.innerHTML =
        '<td class="st-team">' + escapeHtml(r.team) + '</td>' +
        '<td>' + r.w + '</td>' +
        '<td>' + r.l + '</td>' +
        '<td class="st-wide">' + r.pf + '</td>' +
        '<td class="st-wide">' + r.pa + '</td>' +
        '<td class="st-wide ' + diffClass + '">' + (diff > 0 ? '+' : '') + diff + '</td>';
      tr.addEventListener('click', function () { showTeamDetail(r.team); });
      els.standingsBody.appendChild(tr);
    });
  }

  function showStandingsList() {
    els.standingsListView.style.display = '';
    els.teamDetailView.style.display = 'none';
  }

  function showTeamDetail(team) {
    els.standingsListView.style.display = 'none';
    els.teamDetailView.style.display = '';

    var standings = computeStandings();
    var row = standings.filter(function (r) { return r.team === team; })[0] ||
      { team: team, w: 0, l: 0, t_: 0, pf: 0, pa: 0 };
    var diff = row.pf - row.pa;
    var record = row.w + '-' + row.l + (row.t_ ? ('-' + row.t_) : '');

    var players = teamPlayerStats(team);

    els.teamDetailContent.innerHTML = '';

    var head = document.createElement('div');
    head.className = 'team-detail-head';
    head.innerHTML =
      '<h2>' + escapeHtml(team) + '</h2>' +
      '<span class="team-detail-record">' + record + ' &nbsp;·&nbsp; PF ' + row.pf +
      ' &nbsp;·&nbsp; PA ' + row.pa + ' &nbsp;·&nbsp; Diff ' + (diff > 0 ? '+' : '') + diff + '</span>';
    els.teamDetailContent.appendChild(head);

    // Team leader cards (this team's own top player per category)
    var cardsWrap = document.createElement('div');
    cardsWrap.className = 'leader-cards';
    STAT_CATS.forEach(function (cat) {
      var top = players.slice().sort(function (a, b) { return b[cat.key] - a[cat.key]; })[0];
      var card = document.createElement('div');
      card.className = 'leader-card';
      if (top && top[cat.key] > 0) {
        var league = leagueLeaders(cat.key);
        var rankIdx = league.findIndex(function (p) { return p.team === team && p.name === top.name; });
        card.innerHTML =
          '<div class="lc-cat">' + cat.label + '</div>' +
          '<div class="lc-name">' + escapeHtml(top.name) + '</div>' +
          '<div class="lc-value">' + top[cat.key] + '</div>' +
          (rankIdx > -1 ? '<div class="lc-rank">#' + (rankIdx + 1) + ' in league</div>' : '');
      } else {
        card.innerHTML = '<div class="lc-cat">' + cat.label + '</div><div class="lc-empty">No data yet</div>';
      }
      cardsWrap.appendChild(card);
    });
    els.teamDetailContent.appendChild(cardsWrap);

    // Full team stat table
    if (players.length) {
      els.teamDetailContent.appendChild(buildFullStatTable(players));
    } else {
      var noStats = document.createElement('p');
      noStats.className = 'info-list-note';
      noStats.style.borderTop = 'none';
      noStats.textContent = 'No player stats posted for ' + team + ' yet.';
      els.teamDetailContent.appendChild(noStats);
    }

    // League comparison block
    var compareWrap = document.createElement('div');
    compareWrap.className = 'admin-form';
    var compareTitle = document.createElement('div');
    compareTitle.className = 'stat-entry-head';
    compareTitle.innerHTML = '<label>Compared to the league</label><span class="stat-entry-sub">' + escapeHtml(team) + '\u2019s best in each category vs. the league leader</span>';
    compareWrap.appendChild(compareTitle);

    STAT_CATS.forEach(function (cat) {
      var league = leagueLeaders(cat.key);
      var teamTop = players.slice().sort(function (a, b) { return b[cat.key] - a[cat.key]; })[0];
      var row = document.createElement('div');
      row.className = 'league-compare-row';
      var leagueLeader = league[0];
      var info;
      if (!teamTop || teamTop[cat.key] === 0) {
        info = 'No ' + cat.label.toLowerCase() + ' posted yet';
      } else {
        var rankIdx = league.findIndex(function (p) { return p.team === team && p.name === teamTop.name; });
        if (rankIdx === 0) {
          info = '<b>' + escapeHtml(teamTop.name) + '</b> \u2014 ' + teamTop[cat.key] + ' (#1 in league)';
        } else if (leagueLeader) {
          info = '<b>' + escapeHtml(teamTop.name) + '</b> \u2014 ' + teamTop[cat.key] +
            ' (#' + (rankIdx + 1) + '; league leader ' + escapeHtml(leagueLeader.name) + ' \u2014 ' + leagueLeader.value + ')';
        } else {
          info = '<b>' + escapeHtml(teamTop.name) + '</b> \u2014 ' + teamTop[cat.key];
        }
      }
      row.innerHTML = '<span class="lcr-cat">' + cat.label + '</span><span class="lcr-info">' + info + '</span>';
      compareWrap.appendChild(row);
    });
    els.teamDetailContent.appendChild(compareWrap);
  }

  els.backToStandingsBtn.addEventListener('click', showStandingsList);

  // ---------- Stats tab (Team Stats / Individual Stats) ----------
  function populateStatsSelects() {
    var allOpt = document.createElement('option');
    allOpt.value = 'all';
    allOpt.textContent = 'All Teams';
    els.statsTeamSelect.appendChild(allOpt);

    var allOptIndiv = document.createElement('option');
    allOptIndiv.value = 'all';
    allOptIndiv.textContent = 'All Teams';
    els.statsIndivTeamSelect.appendChild(allOptIndiv);

    TEAMS.forEach(function (t) {
      var o1 = document.createElement('option'); o1.value = t; o1.textContent = t;
      els.statsTeamSelect.appendChild(o1);
      var o2 = document.createElement('option'); o2.value = t; o2.textContent = t;
      els.statsIndivTeamSelect.appendChild(o2);
    });
  }

  // Every player league-wide, aggregated across all final games, with
  // their team attached — used for the "All Players" comparison table.
  function allLeaguePlayers() {
    var byPlayer = {};
    Object.keys(games).forEach(function (id) {
      var g = games[id];
      if (g.status !== 'final') return;
      [[g.teamA, g.statsA], [g.teamB, g.statsB]].forEach(function (pair) {
        var team = pair[0], stats = pair[1];
        if (!stats) return;
        stats.forEach(function (p) {
          var key = team + '::' + p.name;
          if (!byPlayer[key]) {
            byPlayer[key] = { name: p.name, team: team, position: p.position || '', number: p.number || '' };
            STAT_FIELD_KEYS.forEach(function (k) { byPlayer[key][k] = 0; });
          }
          STAT_FIELD_KEYS.forEach(function (k) { byPlayer[key][k] += p[k] || 0; });
          if (p.position) byPlayer[key].position = p.position;
          if (p.number) byPlayer[key].number = p.number;
        });
      });
    });
    return Object.keys(byPlayer).map(function (k) { return byPlayer[k]; }).sort(function (a, b) {
      var totalA = a.rushYds + a.recYds + a.passYds;
      var totalB = b.rushYds + b.recYds + b.passYds;
      return totalB - totalA;
    });
  }

  function buildAllPlayersTable() {
    var players = allLeaguePlayers();
    return buildStatTable(players, [
      { key: 'name', label: 'Player' },
      { key: 'team', label: 'Team' },
      { key: 'position', label: 'Pos' }
    ], function (row) {
      els.statsIndivTeamSelect.value = row.team;
      renderStatsIndivPlayers();
      els.statsIndivPlayerSelect.value = row.name;
      renderStatsIndivContent();
    });
  }

  function computeTeamTotals() {
    return TEAMS.map(function (team) {
      var totals = { team: team };
      STAT_FIELD_KEYS.forEach(function (k) { totals[k] = 0; });
      teamPlayerStats(team).forEach(function (p) {
        STAT_FIELD_KEYS.forEach(function (k) { totals[k] += p[k] || 0; });
      });
      return totals;
    }).sort(function (a, b) {
      var totalA = a.passYds + a.rushYds + a.recYds;
      var totalB = b.passYds + b.rushYds + b.recYds;
      return totalB - totalA;
    });
  }

  function buildTeamComparisonTable() {
    var totals = computeTeamTotals();
    return buildStatTable(totals, [{ key: 'team', label: 'Team' }], function (row) {
      els.statsTeamSelect.value = row.team;
      renderStatsTeamContent();
    });
  }

  function renderStatsTeamContent() {
    var team = els.statsTeamSelect.value;
    els.statsTeamContent.innerHTML = '';

    if (!team || team === 'all') {
      var note = document.createElement('p');
      note.className = 'teams-sub';
      note.style.cssText = 'display:block; margin:14px 0 10px;';
      note.textContent = 'Every team\u2019s season totals, side by side \u2014 tap a row to drill into that team.';
      els.statsTeamContent.appendChild(note);
      els.statsTeamContent.appendChild(buildTeamComparisonTable());
      return;
    }

    var players = teamPlayerStats(team);

    var cardsWrap = document.createElement('div');
    cardsWrap.className = 'leader-cards';
    cardsWrap.style.marginTop = '18px';
    STAT_CATS.forEach(function (cat) {
      var top = players.slice().sort(function (a, b) { return b[cat.key] - a[cat.key]; })[0];
      var card = document.createElement('div');
      card.className = 'leader-card';
      if (top && top[cat.key] > 0) {
        card.innerHTML =
          '<div class="lc-cat">' + cat.label + '</div>' +
          '<div class="lc-name">' + escapeHtml(top.name) + '</div>' +
          '<div class="lc-value">' + top[cat.key] + '</div>';
      } else {
        card.innerHTML = '<div class="lc-cat">' + cat.label + '</div><div class="lc-empty">No data yet</div>';
      }
      cardsWrap.appendChild(card);
    });
    els.statsTeamContent.appendChild(cardsWrap);

    if (players.length) {
      els.statsTeamContent.appendChild(buildFullStatTable(players));
    } else {
      var noStats = document.createElement('p');
      noStats.className = 'info-list-note';
      noStats.style.borderTop = 'none';
      noStats.textContent = 'No player stats posted for ' + team + ' yet.';
      els.statsTeamContent.appendChild(noStats);
    }
  }

  function renderStatsIndivPlayers() {
    var team = els.statsIndivTeamSelect.value;
    if (!team || team === 'all') {
      els.statsIndivPlayerField.style.display = 'none';
      return;
    }
    els.statsIndivPlayerField.style.display = '';
    var players = teamPlayerStats(team);
    els.statsIndivPlayerSelect.innerHTML = '';
    if (!players.length) {
      var opt = document.createElement('option');
      opt.value = '';
      opt.textContent = 'No players yet';
      els.statsIndivPlayerSelect.appendChild(opt);
      return;
    }
    players.forEach(function (p) {
      var opt = document.createElement('option');
      opt.value = p.name;
      opt.textContent = p.name + (p.position ? ' (' + p.position.toUpperCase() + ')' : '');
      els.statsIndivPlayerSelect.appendChild(opt);
    });
  }

  function renderStatsIndivContent() {
    var team = els.statsIndivTeamSelect.value;
    els.statsIndivContent.innerHTML = '';

    if (!team || team === 'all') {
      var note = document.createElement('p');
      note.className = 'teams-sub';
      note.style.cssText = 'display:block; margin:14px 0 10px;';
      note.textContent = 'Every player who has posted stats, league-wide \u2014 tap a row to drill into that player.';
      els.statsIndivContent.appendChild(note);
      els.statsIndivContent.appendChild(buildAllPlayersTable());
      return;
    }

    var playerName = els.statsIndivPlayerSelect.value;
    if (!playerName) {
      var noPlayer = document.createElement('p');
      noPlayer.className = 'info-list-note';
      noPlayer.style.borderTop = 'none';
      noPlayer.textContent = 'No player stats posted for ' + team + ' yet.';
      els.statsIndivContent.appendChild(noPlayer);
      return;
    }
    var players = teamPlayerStats(team);
    var player = players.filter(function (p) { return p.name === playerName; })[0];
    if (!player) return;

    var head = document.createElement('div');
    head.className = 'team-detail-head';
    head.style.marginTop = '18px';
    head.innerHTML =
      '<h2>' + escapeHtml(player.name) + '</h2>' +
      '<span class="team-detail-record">' + escapeHtml(team) +
      (player.position ? (' &nbsp;·&nbsp; ' + escapeHtml(player.position.toUpperCase())) : '') + '</span>';
    els.statsIndivContent.appendChild(head);

    var cardsWrap = document.createElement('div');
    cardsWrap.className = 'leader-cards';
    STAT_CATS.forEach(function (cat) {
      var card = document.createElement('div');
      card.className = 'leader-card';
      if (player[cat.key] > 0) {
        var league = leagueLeaders(cat.key);
        var rankIdx = league.findIndex(function (p) { return p.team === team && p.name === player.name; });
        card.innerHTML =
          '<div class="lc-cat">' + cat.label + '</div>' +
          '<div class="lc-value">' + player[cat.key] + '</div>' +
          (rankIdx > -1 ? '<div class="lc-rank">#' + (rankIdx + 1) + ' in league</div>' : '');
      } else {
        card.innerHTML = '<div class="lc-cat">' + cat.label + '</div><div class="lc-empty">No data yet</div>';
      }
      cardsWrap.appendChild(card);
    });
    els.statsIndivContent.appendChild(cardsWrap);

    if (players.length) {
      els.statsIndivContent.appendChild(buildFullStatTable(players.filter(function (p) { return p.name === playerName; })));
    }

    var compareWrap = document.createElement('div');
    compareWrap.className = 'admin-form';
    var compareTitle = document.createElement('div');
    compareTitle.className = 'stat-entry-head';
    compareTitle.innerHTML = '<label>Compared to other players</label><span class="stat-entry-sub">How ' + escapeHtml(player.name) + ' stacks up against the whole league, category by category</span>';
    compareWrap.appendChild(compareTitle);

    STAT_CATS.forEach(function (cat) {
      var league = leagueLeaders(cat.key);
      var row = document.createElement('div');
      row.className = 'league-compare-row';
      var info;
      if (!player[cat.key] || player[cat.key] === 0) {
        info = 'No ' + cat.label.toLowerCase() + ' posted yet';
      } else {
        var rankIdx = league.findIndex(function (p) { return p.team === team && p.name === player.name; });
        var leagueLeader = league[0];
        if (rankIdx === 0) {
          info = '<b>' + player[cat.key] + '</b> (#1 in league)';
        } else if (leagueLeader) {
          info = '<b>' + player[cat.key] + '</b> (#' + (rankIdx + 1) + ' of ' + league.length +
            '; leader ' + escapeHtml(leagueLeader.name) + ' — ' + leagueLeader.value + ')';
        } else {
          info = '<b>' + player[cat.key] + '</b>';
        }
      }
      row.innerHTML = '<span class="lcr-cat">' + cat.label + '</span><span class="lcr-info">' + info + '</span>';
      compareWrap.appendChild(row);
    });
    els.statsIndivContent.appendChild(compareWrap);
  }

  els.statsModeSelect.addEventListener('change', function () {
    var mode = els.statsModeSelect.value;
    els.statsTeamPanel.style.display = mode === 'team' ? '' : 'none';
    els.statsIndividualPanel.style.display = mode === 'individual' ? '' : 'none';
  });
  els.statsTeamSelect.addEventListener('change', renderStatsTeamContent);
  els.statsIndivTeamSelect.addEventListener('change', function () {
    renderStatsIndivPlayers();
    renderStatsIndivContent();
  });
  els.statsIndivPlayerSelect.addEventListener('change', renderStatsIndivContent);

  // ---------- Current Teams grid ----------
  var BADGE_COLORS = [
    'linear-gradient(145deg, #E8323B, #CE2028)',
    'linear-gradient(145deg, #3D5AB8, #2A4494)',
    'linear-gradient(145deg, #4a4680, #302c56)',
    'linear-gradient(145deg, #b8455a, #8f2f42)',
    'linear-gradient(145deg, #4472c4, #2c4a93)'
  ];

  // Real team logos, keyed by team name. Teams not listed here fall back
  // to a colored initials badge.
  var TEAM_LOGOS = {
    "Carbon": "data:image/png;base64,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",
    "Olympus": "data:image/png;base64,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",
    "Park City Black": "data:image/png;base64,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",
    "Park City Red": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEwAAABfCAYAAABC1SEeAAA0HklEQVR4nOW9d5xV1RX3/d2n3XvnTh8QhjJD74IgIqKIBSwgirHECpqYgjExJrFFTW8mqDFo1NixYe8dRVFEpUhRRHobkTJ9bjtlr/ePc+9lZkDQmOT5vM+z5nO47ZxdfnvttVfbGyUiwv+YWleplPqPPq/RbT6r7N/uh792dbR+3Po3Hv9GJCL4vg+AaZphe74GaN/0+W9K6r/PYbkRV7QZqvxve/v+m9S2Hw5rT3vr/T5u//oc1rqC/fUzd68GtEAggJDYVkPKFMq7dcEwDMAA+YqgKdi59XMKU0K0cyXKNMAkvBQYRrt2Zdug1e4mf5PhMb7W3UK289lGAJL9QqOz78ObAi+DBH7YvJYMtAjp19/juYsu47bv/ph4xiUIMuT5u3XZX3YJZEQjzWnuuPAy3p/+a/w5H0JDBjI+GALKgLQHvg4HQQFK0AgBwh4spfa8dJs/adOEr89hqjVYex1MlOdjBkAmA1gkP1nPO489zfaVa/h4/juccM7p2Ad0xNe6bQO+wtA7GHTsVs3BvQcy/+mXWVuzmdLBvTjh/DOx+/eGiAkZF0oKIdBgKFDqK7NV+yndnr4eh6nwCb2XGdRm7AKBiAOByfJ7Z/PMTbdRs3EzH65chtmxA4edMgnLcYg6MdCCBBpfND6CD3u5ND6aAB/QKNtg1KknsD3m89GGVdR+8QWPXv8PVt33GEFdApwYuBrM3fPTAuz8J9nHtR8Ivq7Qz3FWDj+FRtFKfDenwYzgbalh1szbiDe6bFr5GXOWzWNgn0H85YYZxEaPQBWa7Ny1HSejsQJFoFQ4CPvgBA2UHFCBciKoJo+mhUv51RVX8fHKJZw48hg6du+KU9WZb33/ApzOB0DUBltlueyr9q89HG0b9W+skm1ZNkAQCTBRqEwAaZtd737Aw089RqwgxtyXXmbTxnUcO3ocv7z+T0SH9gMHlixZxAXf+jblTT5O2sVA4UQjZDIZlDIwLRPTMHDsKJ7vkUglcSpK+NvTDzJg9EGoZAZlx8ksWsmvL7uSt5e+zaCeQxh33PHUNzVy9rfP5oDDR6EiGl1go5RBKpMi4kTaqCEhHKpV7/7LgOUL9TUkXDa9+i4vPfMsTnkx/7r7LpLpBo4ZNY6//OVvxAb0ISgy0RHF7dffxOzrb+aI4q6UpTQoIdB+vrywUwaWaeL7AYZpsMVtYnU0w83PPsSAgw/GwATXonHBYq689DLe++xDiu0Kpp03FTIeEyadSNWkozEiJloFKMtGlLRv+X8XsJxQzD0UeGlsHFRSWPrkM7y/4AOSgcdtD90BbsDY3sO4/vrr6TBxHCrQJCwwFVx++lQyiz5jNMV0TGt8P0OgfUTAMi0ikQi2beN5Ac3NzTiOQ6MtfJiqYY2Z5s43X6Dq4EMwUhnQFvWvzOPaK3/JnE2LcYwCvnfO+XipNBNPmES/M07GjBjgqOwq+O8D1lbo70v2Zb83ROU1AANwfAOVEZY88jgfzHuXxiDDnQ/dh3KFYVUDueKKK6k4bBQqlULHTJRj0dyU5KNlK9i2fTs7d+7ATyQodjWFKQ/SLrUt9SyrXctbXyxlWe1agogilgnokPQ5trI31a7iyu9NJ1m7A4mYUGBRNmEcF106nYGVfcnoJP944A7EMnnzpddZ99jzBMkAki5IqGIoFNJKZfiqXLMbsHaLhZZWBQkgOryyePv44PnQLGyc/Tzz576FayvuffxBtPbpRRHTTzmTPiedgFESQYqjeAbYhiKRSjJ43KHED+zJMtnBjpjGE8GOODTFhddYT+3YfniTxrCiRyHPt3xGJmZS6hsU7Wymr4qR2bYLMFEa0D7EAoZ/59t877wL6G13wkWYOfteiFq8+NSzfP78HHTGgIyPF/ggoLQg0pbjDFS7iz2uPbhPKwgUBO3BzGrshihi2KjAYNOLr/HWy69jFxVyw6zb+aKlgbjhcNopUxh70YVYRQ4SBS+riVtAj6ou3HLPHdzy0H348QJSVrZ4BY2OEOvek988cT+/fX4Wt7z9LMnCGLWJJpQIBX5ATIMj2e4oC21aZCIGErWYdOEFHHPk0XQxSwkI+OvDt1LSvTPPP/U0m16egxYDJ4uQYVgY6utpVrvvzoIVKPAVeIQ6UPvfCXTYu7okzR8s58lnnoaKQmY8eCdJN0N3TI4cdBBn/XQ6dp8DkEKDjKmwUDhaoVqNaCaTbjMXtDL4Ip3ALYhQn0kgWMQicUxloxyHZp3Gsw0Cy0BbBpgWGAaiDEwUWAp6HMC5P/0h4weOpL9RggZmPHgnRlkhjz4ym9qFyzEaXZQXTk8DweKrm0tt4NWEXOUT9sPIfekDmezlGdAi8HkdT896mE5V3bjzqdk0ZVIooHtBZy44byoFwwaiJUMGCSWGGChRNCdTuK5HEAREIhFEhdNCJFRRIvE46cDDsB0UJqIgWlCAKEVhYQm+qfAMwVMSrnitPTcGCB5djhjN2WefTa/irtjYbEvWM+vpx6mo7Mzs2+/B3dEISSDpQ0og3arT+6E2lklu1uV+cAitChQsu+dR1ixcim2bOLbDzu3bKa3qzO0vPMqaus8x0JQSYdKpJzPwWydj2gqxzHwFgRH2LR6PEQRg2RbNomm9RhsClqspVDZFVhQHk231dTQnmjHtcnwttAQurqUw4lGwFEF2yBUGgkZFLXAMBp/1LQbOm8sHczbSGHisbqzhsddf5PxjJvLAVb+ja8dORJ0ITU1N9Bk1jAHnnYJZHv96gGUtn/x7NOBBzZz53HbzTCriRZx40omkfY/qTv25/ZFZLFz/Gb5oKoDhPfpxzgVTcSqKQGdQTiGm8vczcoLo8DJ9KDYMUmtquPOqP1DWrRPL5r5HYdLDcgISqTR+qULbFk2pBCIKUXtZ8g2gSwmnfW8qyzetoWH1Qup1wOLNq6n8qAMXnXw6VtLD8DSLVy3k2Tkv87s+3ely1GEYMWufLo09jG+F3l2xBrY18did9zJ3w3IkHiG1uQtz5sxBK836z7eBLRS5ii7EOGnMOOKD+6McAWVny8savzrbCgXGXlQ/A4j4UO4LQyjg07tn4yEUYnMQpVQEFsoSzAjUt+yAeAGJII0jRSgVrmZKwgsEbKg+fCSHjjiYxeuWsFMHtJg+Dyydx6Iv1hAzbU48ejxPfPwmuBmeuOteph84lEjn4tCc+hLaq7cif3sAy558jkXvzKfBT1F0QAfuePoRks0ZsMCKKfwkFCN0K+jAlCln4BTGIWKHIPluqKWi2hqgOZAkBMrM9tEAKgvLiNklVClBOTYOCpV0cbUBsTjLmzaxPLWTq+64j9KikrB4wNTZooMADAPXALtzCeeceibvz3mbtTtWhtYIsK5xB24mYN2Lj1FWVkDLjgTzXp7DSUe9RK/vnI5h2/sCbO/uDAtQGkpjMQpsG0sZfLGlBhX4oQfFBF8LBqHMNAKhuWYrBX6A8jTYEbBarSmtgMpZJ0ogCjjB7umU9lzSpkJKC0grIeFpCivLqHEzfLJ9Ex+mtvGbf93GUaedim3ZIedK9lIKT/lYho2vPOxGl+2r1xNpTFOKUEeoBwZuuNI3NraAlaZMTEqjMSLKyOqaX+4l3oPD2msl1adO5tgli6jMHMI9zz9BbWNTqG7kXD2EnW4KMrz4xuuc/63jcQpKws5rD0tZ4ZQxdled8+vl68wC6JqwI0iyoGEd2xpcmrK/5/TBBCa/u/M2Jkw9G8txaGisp6SoNKuPhZ20TQcvSBMzo6hUijfefosmP0MBJrX42DpcjXO+HuVrzplyFoOLOtHp5IkYzr5dhG1+NSCvzYe1A0UOHfpWMTzoxPfjDn++9x6iVkAiE2DkVDLgM7+W91Yv54Q571I5ZSKGrVHKIVCCYrez0SBkCk2oofhZBVmAjGmwI26wM1XItbfcQKSiBJRBKpUmFi+gsLyUPiOGY5ihpltcUsIe0jkAW0Wh3uPTl97kg42r+FjvYltom4ASPAHDhogy+d4pZ3JQ30F06d4No8AP+/xVAQPysibI+seVm6JHdRWPvvAsE6ZM5JMtG3nqtTmYAcRNKHQcbBTNboa3Vi9h+o8v4ZK1P+GYSy8i0rEoW1Zr61PlB8cATAEtgrJNXFPR6KUp79mNYZMnEO9QCcpFtAZl5t0yjY2NFBeXEPg+lunkDWqlQblAwuXp62/k7nvvZVHtWgSTA8wovg5wVYASTZCGUYeP4NxzzuGdl15n2KgRKKv9/JI9PKV72gWGQcbPhB1TBjRkWDznXUo6VHD6tKls37GTsSOGU2iamAF0lzilrkkaaECxNPk5f5x5I49f/nvcD9ZCbQJcN/THZ7Xrz2u28Ifrfs0df7sJlXGJiYFlWhgCHe0CWtbVcPM1v+GGP/+WVDKdtcg0IhpEKCkpQSmFbTkoFUJvaBPlmbBhBw9d+SvueOg+FtatI4HQiE8JDh3EAa2JKRh50IGkmpOcMu0cSio78v5LbxA0eCGnoEJNWre68nJXgr1EBaDZS1BIlC0PvMiy9z/kkeXv8tKi+ViBxkQoj5bQIRqnT1lnmhsbWVG/iQbxMTGw0PSlkKNHH8V5V11K1cSjMFwfrQQVi7Jx40ZOPGQMFbUtnBCpYohRTHEATW4LTXGTpelaFtOI372cVxd/SFFxYdiuvH++taA3w06mMmyY/yEP3HQrb819i41ePbW4pIESYHhRNwoLCtjYvBM/ZrG5bhdeVr2ZNOpwpgwexZgxh9P9zIkYRU7IXUEOj91xgT2mZMZPoZQibjnI9nreWTAfcX3eWvIBkUAow6KTU8qZp53O8OEjsCyLiFY8ese9LFnzEet1E2kMVtNC05J3WfWTzVyy6kccMm0qZkkUz/Pp0aMHRw85GGPpevpTQXlSI9onikmJF6OkvCemqudz28DISGjYmrvbnhcdPuALNCWZO+sh7r7vHt79bCmNOkMEqACqKObgPkM5/3vTIOIgFrz93nwee+5pNrfsohFh/ofzOXvkOFasWEHl0YdgxzujjOyKqaysuRNWuQdgthVFp1Moy2Hhm+/Q6KdYsnQpKvCxESoo4KyTpvCdn/yUSHU3CDJQWsKww4/ktQce5JYnHuCj7etICmxzG3A3N/Gna3/FlI9WcN4vLsXp1wNa0hw++jBeeH85tYUleLYG20CZBUg6Q0ug8UxNY2NTmBYgWVnSOiTnhoDJxs3cMfOfPP/U0yzbtR4XjQnEMBjasQ/fOflMTrzwAuw+laEeI8Lw8cfS3NDI0689j+snCYC3ly+hf68+rF7+CQM7dsCMfclqKXujTCDyRVJmX/obmfGDS6VXJC4lIP2Iyk+GHy3JD1aLNAUiLZ5IyhVJJEWakiK1LfLps6/KNaecLUfEO8kATOkF0gvkEArl50OPlV33vSx6Y7MsfOwFqS6Iy2gKZTSmHEGBjI9UyBCUDMGUKpBRVdXStP1zETcpybodooNARLSIr0WaRD5/5BX54ahjZGikRLpjSTWWVIOMscrk5+NOki9emid6Z1KkKSOSyoikMyJpVyStRT5aK1ccOVGqTUvKQDqbEfnjDy6Ve6ZfJZktzSIJT8T1RLwgrM/XogMte4FRg6lILF6OkfZ4f8VHNAUuMWBQVS9+dsXlRHp1hyANUSdUTpWNIJDxGXDiBP5wyKG8NOtBHn3kYRas+ADRAY20MHf5PHb+dCtnTz2fY79/HvPmvkM6mSCRTlBUUUpTKokHWBELFQjl5eUUFBcilkWssCicIrUt0JjmmVv+xZOzH2PRF5/iCmTQlBFjZN9hnH/OORxz/jnYnTuCEYAJftaHY6JQqTT0reKyK69k4892sGT1SjYGSVZt3UCXjn3Ryz5BjjgIFTH3zWGBiASiRSfSMuf3t8i/pv5UBpR1kHKQY6Od5OWf/UG8L5pEmpMigS+ivfAST0R8kcATaWgQSWZEMr40LPlEZpx2oRxjVUgPkG4gfYjJyEgH+fUxp0vqzaUizb5IKiWiXfElLW6QkECnREsQlimeiJsSCQKRhCt1z78jMyaeJwdbRdIfR6pBBqHkpEil/HX8t6Xh7cWidzaJJDIizQkRNyPiu6K1K1pc0RKITraITreINKfl9Wv+LifGuklHDBleWS2zLrpSFv71HvGa0pJOJkS34jDx23FYqHEr0nUNbNpWQ1OiGa+lmQqiHHn4WI6a/n2suIlvC0p8Mp6HaRqYpoWpVCgoiwvDiLcSSnpX8/ObbuCgA4cx68nHWbzqY77wGklnUrz45sts3bSRk6eezYkXno1dUoipBMOx8A3BshReUwOWHUNZEajZzsuPPsnsmXfxyZZP2C4+DiZxoowcOJTLv/8jBp4yGbNTIUQUGGYosHVoJ6ic7AOIRcn4GRzRjJ96Fh++v4B1bz3Lzm2b2LhxA4ZpMrSpCadD0Z65JG1kly8iDSlZ/vhLcutFP5dpfQ6R4YYpZ3QeJJ8+/ooELa7owJeM9sUVXzzxxQ0y4gaueNqTQPuiA18k8EX7nmjXE2nJiGS01L+zVH436Vw5qbhKeqOkEqQSZEKHapl5xvcl+czbonemRWqbRHxPRGsRPxDZlRT3zSVy87k/lMPjnaS3ikoXkP4g4ws6y6+PP1Pq3l4oenuDSHOLiA7EEy2+aNGixRe/TbtEB7uvIBBJBbLyyVfljC5DZLgy5Xt9x8hfTvuerH/zfQmaUiJpX8QNRDwt4rWXYQFAhC9WrccVn3VbN1OpizlpzFH0GjMKwwFXCVopLHIeAhPJPqoVKBHyjlAJEFMgcCkdOpDr7ryDN/51Fw89/BDz1y4j0MKmXZt47smnqFu7gVO+dSpDzjoNMxNAQQQ8zYcPPMpzjz3JouVLqU3uoomAAkwG9xzE1HPPY+K087EPKCcwXIx4Aa7a7S3eazKVSF5NwACiMPDYsRx9+Fgant7CynVr6DHyQD5670O6DTkQo52p1BYwAXY0ULtxK+u3bWWrX8e3uo/gjGkX4hQWkUwliBbGQ0BaZaPkvLI62whTZ31TpgW2AVqHNlA0xrFX/YSDjxjNPX+6ifnz3uFTfxs1uoE56z+m5tEEx69ay+QzzsY2FY8+8hDzP17Mux8vIaNdfALGlvRk+KiRnH7ZD+k7dhRmPA5KYQYKCDAxkFbml0Lldd02akn2Ne2miRTFmDZtGis+XMyLmxexbsfn9OhQiTSmw4Fr5fTfAzBZvxEnE7Dls/U42uKw447G6tsTlFAQL2wLbu71y/xtnk/GdzEdG9N2UFqgJUHpmFH87O83Meifd3DnEw+xdlcNmxq30dLYQCyt2bZxC25tI7UNDSzfvhxfMsRVEYOr+vPd087i2O9MxRrQBW1qRAKUmGA6eJkEhhPL+SlbWa5Zag1algzTgFSagiNGcfik45h311qatu8ifUA97KiDTsW0zv7ZQ63YWlODpYXM5m30Ke/KMVPPwKqMQzQM4OYqVbkVV3bHjkPDVOc5HsskYhfuHl5ThWlILS70rOCE66+l7xEH8/C/7mXZosVsSH7O42vf5xAnw/H9h2MsTxAnoJwSeg8exrSfXsLAk4/HLImBIRi0Ym1DsJ2CbAtaT8V2k7LdR8eIhh6KRIajzj2V5197meTaLbR0qKZl21bKDuyeBUz2DlhDcxPr12/A1C7HjTuaeP/eqEILMVQoo8iacu0GrjXlvNGmoWiTyqA1+EGYVeOmQCt6H38C13XpxfVXXU3hlmJ2frGSd1d+ROParZw27jhO6toVN5Xih7+5jsioYaGLxGxXeWvOUV8vh0sCHwyFill0HTqYI0YeyssbHwFfs3HTZko4NJ9V1Drmka+sLtVMXUsTCBw77ihsJ7JbSO6NVFsPSC4q5wMuCl8JgdK7Q2LKDNUOJxI6pRYt4/WHZlPdvy/FRUWc2mU4h6pymtwG/vH6Q6w1Exg9DuDlRx7FW7kOMjofMM2H+VuHpb9qgBF2Z2NrCfsQc5h04kTK7FJq6+qo2bENraRVfFbtKcMat+/CEYN+PQbS86hxGLa1bznVFjvMbLtzYb4gv462uksbkNG8fv+DfPTCGziB8M6iD9hYv4EexDmsehifNH3BJw2befbtl+hR2o3jR45h5h9/x2ETjuaQC8/HKnQwnLAyX+22zb8OKaXAtEIu0+GA9jzkYLr37End9p2olA+B5MfBoNWUFBHIaPz1X6C2N3D4lGOxKitC7gqyYCi+NOnNgPC+VoHNIHufxsDUQcgKStG84jOeeOBB1m1cR02ygQXvLcDzU3TEpLiwE6edcxZnRSLcPuteFm1YwfqGLTw0/1WG9B+E98Zctq1cy+Rp52MPHwiFBp5OY9rR7Exom3S5nxzqLHDZOR4o6NaJYYeNYukTr+LUJ8AN47O5rOK2HKZgw5bN9Bk2hJMuvgjbkqz6r3arEISqzJe2QvJFZWPeWfe5b0BTkvdfeJF5r75OoqmRZZ98zLtb1xIXTe+iAxgz9GCuvuqXFB0yCqUsfjukP7f88xbe+PA9Vrd8ztyl75HsuIOYGNz++z9x6ISjGDHt28SKopBMQknB12ezELHw1QSUx1k/v5TmdTVs2vY5Wus2caJ8fpiIQFp45Jo/cPppp+Mc2h8sMwxbtcekDZe1+iCgsjEBN2QmLB8UBql3lvH844+zomYDm+t38t7i92lItlCNw5DK3hx/8mROu/RinOquISur7ETYvJ1n7riHF2fNZtnOj6kVTXG0lNFDR9C5pILuHSs5b/oPcIb1BzcBJXG0uVsN2G+efnvy/FBObtrOK888y7EXfxe7KLLbj9gGME9QzYnwwZIYvpF1ckq71U7tzraRrNZqZMHKNy0n/ZuSvPPIk3w0711sx+b5+W+xZOtqTKDULuCYQcP57vnTOPDsMzBNDy9iIPFwodFJj4gRQTW5fPrwczx4332889lHbPXqMFAM7z2UkX2H4Dg2o448gkPPPg2rvDBMSjGzlkdrwHSO/dU+OFFDyoVoBJrSEHNCEIx2gOULzClbOcbJLdntg9VK46mczqOwgUwyiW1bGMpBJQJY8RkP3HYXtalmtriNvDpvLqnmRgJ8+sY7ccyE8Xz3yp/T8aAhKBGwQCybjArT0U2MsLOuCykN67by0J9u5IVnn2e9X0stLhKJcvz44+ikHaoru3LODy7CObgfaI+MZWIrCzdwUWkfx4lk5VWe/dpeOcByMRvJgbv7/jaA5d7ude9OO9C00gRZwEwUyktj+IJSUWhoYcUzL7Jw7juk/IAX573Jitr1eKIpAEb2OpCLzjmfY6aei9WljKcee4T1y1dSGCsgo3x8NIYGw1D4WmNoRRyLaVMvIlLUkTdn/J27H3uIj3aspU4CXDRH9TuI4b37Y0Ycxh4/nsPOOR3LMSDSTi1qn264hyrSLrDdWv7swWFfkXSrfzO+C74matsoT5F4ZxlP3f8gu4Ikm5P1PPnWq2TSaUpcn+poBQcNH870n/6YHhOOxLAUM355DQ/86190dE3KMLFyO0nyvKuI2YVs8nbSu88Q/vHKixRUdGDTC29w1y23MX/pIrZm6qnHo6i4hBOPGk+nwlI6qAjnnXMuRceMQokikAxGLLb/jVyt47LqPwDY7iC6DuVaLhDR3MSzd89i46KPKSyI89zCt/lwzSektEepFWN4x25864RJfPviH+L0roK4wcxfXsvTM2/jqKoD6SgORnOSuOmgJcAzwrioo8GxIzQrn3c2r0KP6MNtjz5CQacesHwVt86cyatvz2XptpDbTGBkn0GcftjR+HUtDD9sNKPPOg2rZ4dQ5JiKfSri/3HAtEYphVICGYG6NFvnvsvrr7yMUVzABxtW8vK8t/iipZEKoCcRDus5nHN//H2GfPtUzKIooPnHddfxwm33cFJhHw5IhJs2fAsSDuioEaaJuwGdAhtpTONg01Ri8XjdKjqMGcHfZ99PQUkZiMWcf93Pozfdxsptn/GFabDDT1EZLWbyYUcysucg0k0tHD9lEp0nTgjTmSKA54UdMu12Gx/+k1NSA142LyHpEWzexgt3P0Tt59vxDc1z78zh/a2rSYgmAvS3Sjlv9Hi+/4PpRI4eGSZhFNjQ1MLkQ4+ge4NmslMNu+oICmKsSGxhIVvxQ6mIhcfBVNHXKafCtXCjJmsqI8zaNJ+/P/cUo447BsuKodIK940PuPlvN/DCsvf5pPFzBKEAOLhTf84++Vs0J5qxSwo543sXEqvuiiopgIwHlh2uqnlc9g3Y19uc5QONLgQmKx59nPcXfkBR9wNY3LCRp+e8QtJ3iaPoRIyBHbpx8omTOOvS6Th9e2SVQj9MgVJCsTLoFImifI8Mwq6oZlkywZTLrqb7iCFETJPa9Zu57/c30OI2My7eDZ3KoGsTdNFlFNkxRFloJRhRwTniQC6v+itd/3Ebjzwym/XJL2jG543tnzH/zr9x7LhxjCwbxq1/mcGEcUdz4HmnYdoO+H449839yLYs7R+w3BIbWtNsm/serz/9LKUVZTiFBdx4zx2s2VVDWoRSTCpUlMHde/Lz71/C8O9egGmnwfEgkh3RWBHS1EKRHUG5GRoad1EULaIuSJOwbSZccA4lA6qJKBMDh3lvzafpw89o0AFF8RiRwgiqxcIybBTg4eO5HoUxE9W/mnN+9xsG9O3PLXfezkfrPyMpLaTxee6dN1i66hN+dPI5LPjwA95ZuIBJp0ymxxFjMbBD7ke1XTH3YgfuAVibzKjcZHWBtVt5aubtJDIZSvt244k3X+GZD94iCAJsoCvQr6ALBw09kMuvvZrSsaNRfgpKCtCGAhWAY6MQVCRKKnARSxGPF2Ch0J6HgYmFhYmJUhZgEIjCjBfiOcU0+ZrmooC6L9JoCY1iLUZ2V5wKB7XYZMT3zuXGwQO59cabeH3e26wPaqnTwpb6Wq6+80aOPOgQpkw4gScfe5xBb33Acd+/CLv/AaGKsa8dYrIX11EbL4kAHtR//Cl3/fF6yktLcaMG1/79rzz+3hskgoBiLCowGVjcg5MnnMCvZ/yNsuFDUaaGkhgYYR6qYCCGldeydSufmtK6bWPECH8zwI0YbHEbmbdzHc9tXc5Tn86nztJ4RjisZqusnrDhARTYlB4yjGtm/JVTp0xhUEk1nYkScT0ywPwVi/nTP2/GLInjItz+q1+RWbOZzK56JJA9lfQv5bDWymlOw2/J8Nzsx9Hlce558wVeXPouiSAgapmU+gH9sBncoRen/uACjr74IizbAclm+QdhqMvMO81kL4PXbo+2UogpaAMMNNtJsqBxEwN79Gb06BOYevx4BowYRufuXTFMB53NyVWmCr0ChhmqBiURiHfh0ut/T8UtXXhp1mNsrvucDTRRH2i2Jpq49va/c8LhYzl08EHcf/tdTLvq8tDiUHsNn+wFsBxoOcAAbIcuXbryu19dx+rkFwQINlDoa7pQzKg+B/KjS35E1dRvYUSysZpYDHyvrSc0zwKt37fNGcsBFsIYoFFc+5c/ErkpQt9efUm5SeLR4qwaFQpXo3V7TQXaBB3gEYBtYPXqxHm//iUH9xrI/bffibFuBesyu6gldAy+Pv8dalau5fdXXodpRfYK0pf1oFVGTPazCUQVE06eyNEHjqS/UUAFJh0xOciu5KwJk7nithupnnoyhh3agsSsUPiZZjaYujczK1dtmyT3PGC5T4LQp08f+vcZgBiCbduA4AbpfH5/qBO2sg1NAywLiUQIImGyHaURBk6dwp/vv53TjjqOEU5neqoYHYF+KCYOOJgjTzgBq8zZu3+7lb25J4e16l9Ats9dK/nJFb+g6ap6UmtX0Lmykh+eenYoLKvLkLiF7/uYtoEoRQBYOX9+zgucc48QuntC0NonJGsMlW2EBlMJV/74p6xbvpIJhx/JmDFj6Dt0MOW9qtFuGiwTw7DbjIkYoAnjD2Zr7rUEVd2ZS2/5O/3vuIu7n3yYtRvXMKLrAC6+5BIi/btDOhPmi+yDy/ZwIOa+yXfFAJRLhwmHcbH5Gw5esIDDjxxLj9GjMQocwEU8H9MIPQtCuCejdZkaSGfbEPuylmRdtUopTDERAggUUtNA4+JPWbFsBwtuupcdBPQ+YiS/mfk3uh04OL+xQeUcB4RxSAtBoUMERYFjh9xXEeeEP1/J6JMmMOeFlxh9/DFUHDoC5ZigzN2qwZcI/j0A06rNR1KZNLFoBOVr+k0YS7/jjs7+6uMFSSzHwTDtVm6QvaSx5yK9Oco6ckNojVACmAa7N+Tq/LbDdEMzg0u6cVRRFaQ8VmR2Me/dBdTVbKPrkEG0z6/ZQy0KsgLcNMAycJWPmfEoGTKA0w86EIptcjJIZxOY9yXF9pt2HnMiYR9NA2Wau5E3bGzVPuW4VayQ3S/ZiHx4R6AhEiFqRtBeAmWaeIEHtgWeojHRTATQpsI2TcoO6EDjJ1uxa1OUa5MWO8Y6FaFATJQOwggIux18bTytCpRFPsCBUlhYqJhFvukiec4ydkP9pah9ddNof9Dvh3IDoRUgGiNi42vIiE/UMIi6gp+qg7p6nEQSLRrdmKFu5Ro6uEKZoVDJFHZhuCvY9328pmac4rLdqQrt2pdfQA21Rzv+3VOH/ueHFSnDoCWTIGUqfMcELKzmDAcAgyngR8ediNOxI6l0imgKegZR+hmlxAyPRjIk4hZ1iRQpw8cqKc6DEdA24v0Nxnaf9D8HrCnVQlFJCYXdOrF+zQYGde6I15SgwLY4JNaLStulEZ9mD7qUldIp7VCmLRIZl0ShyYq6GowDyujSr1e4wSHLMns7qeW/Qf+D053aUpD2MSyTdF0tUydMxFi1hTEH9KCnRDFTGcRUpMUjEI2NhWr2sEwDVVLEe9vX8b7Uc+Mrj9Fv9MGYxcVYKkytyQn7/QfA/z3+yy8m/1PAsrZpqGBqUrt2ce7RJ1D36aeMcDpRoQ0sZeL7bjaNywiDFlGbnX6GDzKb+NcLLzDw+GPQRoClYuisGtB6Ov7fBVgGJJOEoghKCbu21fDzH06nYd1W4soC0yDwA0w/lHcqXkBDJokZi/Dza65m2FGH4RTHiapomxh3zj7YPxz/fwNME+pGJqTxCJTGUEJUxVB4aA2BDrC8EDDfMfGVQSABWvsYhkVUWQQE2Lkw3FfZrJ2nbwbYHkI/8MNIt2F+edJQ7kg9y7IQCbcfe76HZVoIgkho92UyGSzTytt6hlLhqpYt28GmqbmJaNQmUGlMZZPOpIjFCgiCANOxcd0MMSeC6yu0GKHeZELgBZimwjAUiUSSgmgYEVKGQkvYh0AHWMoOPSBZrDzPw7bD71zfwzYt/OzG07DdJjrQbfqf2/ELfHlccm/v82i3K7B1wTnyPA+FwrRM2oe2MpkMjuMgInnj2fMzWKaD7/tYlpV/zaQ9IlEb1/UxDRPDDBXS3LPt6w8CF8PI1Zm92nlgPM8L69AayzDCPmaFoO97GIaRPTlvz37tMSWTySTRaBSlFE1NTSxatIigVX5FcXExI0eOREQwDIPVq1ezadMmbNtGRBgxYgRlZWUopdi6dSuffvppmNCRpQ4dOjBs2DBM02TDhg2s+mwlWmsOHDKULVu2kk6nsSyLI444gnQ6TTy+e6f/tm3bWLlyJaZp4roulmVx5JFH0tjYyMKFC7Esi1gswuDBg1m1ahUtiRa0F3Yvx2GHHHII6XSaNevXUV9fz4GDDiSRSLDt820UFRUxcFD/fPv3Gtje69aZLD377LMSj8dFKdXmuvnmm6WpqUm01nLqqaeKbduilJJYLCYvvviiuK4rWmv55z//KbFYrM2zpaWlMmvWLEmlUnL++edLJGoLIDfddJOMHTtWTNOUXr16yeeffy6+70sQBKK1lubmZjnjjDPEsiwxDCPnB5G7775bVq1aJeXl5WLbtnTsWCGLFy+UoUOHiGUb4li2RGxHHNsRx3Hktddekz/84Q8SjUYFkD//+S9y2mlniONEpbi4VJYsWSK+74vWOn+1pj3mlYjkkR09ejTjxo3DNE1uv/12XnrpJUpLS5k1a1Ye+SlTphCJRKiqqiKTybB48eK8jJs8eTLDhg1DKcVLL73EbbfdRiaT4bnnnsP3faZNm0ZZaQU9evTg5JNPpmPHjpimyQ033EBFRQXJZBIdaESEVatW8corrzBkyBCWLFnCgw8+SEFBAffeey9du3bllFNOAeBnl11Gvz59SDS38OOLL2Hs2LE4ts1f/3o95eXluK7HxRdfwkknTyESizN40BAGDx5MNBrlisuvYODAQeFxp7nthblNYdl5aH0ZWAAHHHAAXbp0QSlFr169GDQoLCwnf0SE9evX43ke06dP57e//S3vv/8+Woed7Nq1K47joJSiurqazp07Y9t2Phg8YMAAHMchHo/zzDPP8Oqrr3LiiScyYcIElFIUFhbmZZVlWViWRVVVFX369KGkpITTTz89HFDDpGvXrhiGQYeKCpxoAc8++yw9e/bklFNOxQ8Cxk+YwKSTTiIaLaC4qIhf/epXvPryy9x+x+18+umnVFdXM/3i6UQiTsgMOVZqtwC3zUBsBx6EAhrgJz/5CSJCfX09nTp1wjRN0uk0CxYsyK+KnTt3Zv78+ezatYvu3bsD4DgOpmlywQUX0NzcTCqVokuX8DhS3/cxTZOVK1fyy1/+Es/zmDp1KiJCJpPBMAy01liWRRAEBEFAIpFAROjRowd33XVXvm7LsrKCOnQx9e/fD9O2ybgZgsDHcRx69eqFYRiIhiGDBvKdiy7itltn4rouDz7wEIXxOF/PRd0aML1bPVBK0blzZ3r06MEFF1zADTfcQCwWo6GhgdWrVyMiXHXVVWzatInm5mZWr16N1hrf9xERgiBARFizZg2xWIwf/ehHRCKh2yiRSNCvXz9uvvlmotEo995zLwAFBaFqYVmhWuI4Do7jUFxcjO/7bNy4kVNPPZVHHn6ETCZDJpPJcm7oQjLt8Bg/xw45vKWlBc/zwpOGg4BAhPPOO5fikjKGDz+Yk0+ZTNvdD/sBrI1vnFAPa25uZvv27QBMnTqVZ555hjtuv4Nu3bqhlOKtt95ix44djB8/nlWrVnHVVVdh2zavv/56/tkcR8ycOTPPRQ8++GC4Mm3bhud5pNNpDjvsMMaOHcucN+Ywe/bsvBz0PA+tNQ0NDaRSKTZs2MC6deuYP38+c+fO5ZZbb8HzPLZv345t23z+xQ6S6QzptEttbR07a3fhBQHbt29vpQ+G8ZLmxgZSyRY8L0NjYyO2vacKtIf7Y2+rY25levLJJ6WgoEAAKSkpkaVLl4qbCVfAHTt2yIABAyQajUr37t1l69atctxxx0lRUZEA8sEHH8iMGTMkGo2K4zhy7bXXys9+9jOJRCJiWZasWLFCLrnkEonFYgLIP/7xDxk7dqzEYjGprKyU1atXSzqdFq21pNNp8X1fpk6dKpFIROLxuAASjUbliSeekI8//liKiorEMAwpLy+XLVu2iO/7csstt0hRUZHE43E55phjpLm5Od9H3/NlypQpYlmWAPLHP/5RUqnUHqtie/pS0yjwAzzfY+HChXieR0FBAcOGDSMajea5YsWKFdlDPAyGDRvG2rVraWhowDAMBg0ahNaatWvXkkwm6dmzJy0tLdTU1FBUVMTw4cPZsmUL9fX1uK5LVVUVDQ0NNDQ0UFpaSr9+/YhGo7iuC4SysKmpiRUrVuB5HqZpUllZSffu3UmlUqxZs4ZEIkFBQQGDBg0iHo9TU1PDZ599hmmadOjQgYEDB2KaZl4pXrlyJVu3biUWi9GnTx86d+7cRmHdG+0BWJA90dL3fbTWmIaJaZk5bkQphQ7Cg26MnJacXTFz0yg3xXdztcL1XBzbwbR2N1gpReAHBDrAyB5F+mUJb3tVIltRKpUiGo22+U4HGj/wwyMbbDtvFuUsldwzyWSSeDz+lU5N3wOwL2G4L6WcUDcMI7+SmaaJae7ufOvX1itgrvGe74WHr2XLyqklkUiEdDqdtzygrVmVqzdvXmVzvnILlYjkwWkNxr76uD/Qvs62nL3SRRddxKBBg6iurua+++4jCAKWLl3K2LFj6du3L+eeey7Lli2jT58+9O3bl379+lFTU8NVV11FVVUVPXv1ZOnSpcyaNYvKykq6devG008/zfPPP09lZSXDhw+nQ4cOdO3alcrKSqZPn8727ds5/PDDGTZsGD169KCqqoouXbrw8MMPIyK0tLRwzTXXUF1dTWWXSjp16sSFF17Izp0729ive6P9Mcw3Bqy8vJzNmzdTU1PDHXfcgdaa2bNn89FHH7F+/XoikQh9+vRh4MCBbNu2jcGDB1NSUkLPnj2pra1l69at3HzzzXTv3p1kMkkqlaJz585UVVVhWRarV69m0qRJTJw4kbq6Ourq6vA8j4qKCtasWUOnTp04/vjjaWxs5PLLLyfRkmDu3LncfffdlJWV8YMf/IChQ4fy4IMPMnPmzLxe+W9T+1WgtQ31Va6FCxdKYWGhFBcXi+M4MmPGDOnWrZuUlJSIYRgyY8YMaWxslJtvvlmi0ajccMMNkkqlZPPmzdKrVy9RSklhYaE89dRT0qtXL+nWrZvU1NSI1lpOOukksW1bFixYIDU1NfLnP/9ZFixYIJ7nyV133SWxWEyuuOIKqa2tlVGjRolpmrJmzRp55JFHpLy8XK688kppaGiQ1157TW699VZZunSp+L6/377ui/Y8oe4rCL7299u2zYgRI0gmk1x55ZX07t2bI488kieeeCJfXiqVyg0Qvu+TSqXYuXMnffv2xTAMnn/+eSKR8Czq3H9dkVtMxo8fz6hRo3jyySfz5lLOg/Lxxx/z5JNPUlNTg4gQjUbp0qULpmly4403cv/991NWVsbEiRO58MIL82X/u/SNo0aWZaG1pri4mAkTJvDRRx8xefJkSktLMQwDx3GIRCJ5zT63KESjUSKRCF26dOGoo47ihhtuwPd9SktL852ysyfFjRs3jnHjxhGLxfKnc+asiLlz5zJnzhxc1+W6666jrLSMsWPHMmvWLJ599llM02TRokXMnDmTeDzO1Vdfvcdq+nXoG8uw3OqolOLMM89kypQpnHvuufmVLac+iAixbJ68YRh5Dd73fU466SSKi4vzHJLJZPJcpJTi6quv5pRTTmHy5Mk89thjZDIZbNvGMAx+8YtfMGvWLAoLC9m8eTOu57J06VIeeOABhg0bxt/++jcu/8XlWJbFrl278kL962oDedrnhP0KdM0110gkEpGSkhJ5//33xfd9qa+vl0GDBklRUZFMmjRJNm3aJP379xfTNGXIkCFSU1MjM2bMkOLiYgFk3rx5cuGFF4pt29KrVy+pr6+X2bNn562MQYMGyYABA8S2bTnllFNk9erVMnToUDEMQ8aMGSOvv/66lJeX5/1q8+bNk6KiIiksLJShQ4dKdXW1KKXkn//8p2Qymf3K6q8lw74uVVVVMW3aNJLJJLFYmJtjmibHHXcc27ZtY8iQIQAcfvjhjB07Nj99+/bty+TJk0mn05SWlnLZZZfh+z69evXCNE369euX97Xl5OCYMWMYPnw4VVVVjB8/nuHDh9OtWzfKy8s57bTTaGxsJBKJMHz4cO68805eeOEFHMehubmZSy+9lO985zs4jvON+vsfixpprfPehdx08jyPWCyWd+PsS/9pTzmLo7WrWLIBl9z3re/J+dgkq2flXvMdzSq2lrV/HtlXG7+xDANwXTfvGQ380Gfl+z6xWCz0/SujTadbWloQEVKpVBtZorUmmUwiInuYYznZ1zqxpPU9nufl25EDz/O8vPafA+ub/qdR/7W4ZK7Y9g3Mfd86VNfe/IFwEHKrpA6y28FEt4lEua6bH5gcx2XcTP5ze85sSbRQVFS0X9D29fv/PLfi/zR92UB+VfqfZ+/8n6ZvOiX/IzLs/yX6/wDt1vDscXonyAAAAABJRU5ErkJggg==",
    "Park City White": "data:image/png;base64,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",
    "Riverton": "data:image/png;base64,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",
    "Skyridge": "data:image/png;base64,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",
    "Timpview": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAF0AAABfCAYAAACKucvIAABBfklEQVR4nO29d3wcxf3//5zdvX469WbLkiz3hnvvFNObqSH0kBAghPABUoAQCCQhQCAkhNBLqDYYsKkuuOFecK+yZUmWrd5Opyvb5vvHnmzZ2GBCQh6P3+P39mO9p9u9nZnXvOc97zazQkopOQGybRshBLawD30nEHDoODZ9/VWgc+mdbrQ7fSU6/W1ZEilthFDQFIE87sPtEyy/0x3HKP+bqPPzO6AUotODjoGu9k0PlVLSuV8EAlvaX6lkx7X/FimAJZ0GaYqKEM7fhxslO2H336tHZzoW4B2fjwD+KDoB0K1DRRiGCYpEKMrXPvRb0Tc8RjdM3JqKEALLsnCpCjYCaYMQznFiY/U/TxIwdB0AVXXq2HEcomO07xtBVxTnlmhC0twaJTUziILA1cFlQoKwESiHKgIOZ4pOYNjJCnzjcO80ri0BlqIRNqC6to3y8gra2lowDJO8vHz69OpJerrD9RoCgTwBHu8sOJIVksnPMnldgIJwOveoX8rkueMpuqGgqeBRFRQhOBFe/EbQAUxA8wj+9uJs1m6s4EfX3MB5k3LwugWaSxDDQDXcuDUwhQRMpws6GoNACoGNgnJo8B8pc21A2MK5akFbO2zeW8/BxhY+XbiUlWs2o2hu0tKCJPQELY0tYFtcdP5Z3HrTWWT6XPjVDhlvH6Nz7aPOJOW5wuGJwQYrDpoKwo1ugksFXYAtk+JMQEMcVq1r4aUXXmDUwDzuuvVSVFVDc57GVwX5kTU5PuidudTBAYlKxc4yHrrrbuYU53HJZWcy4fwxBENevC6ImqCoAlUoya7qKFNgC43OIviYDJH8cvmSUmZ++BE5xd0R3lRMy8XFF1+D5vYSDjejYpOTmknDwRre/NcbtNY18OiDV6ELN5rCN3Cb0qkwcXgilclrmh+EhbRBVaHdBEWDuAktjZJlXyxlxttzKKtKEG5rZXjfLlidnm4nS/i6KpwQp3eQ145x2cRehCybNcuX8ci9S3n6zSGcOv1izj93PF1zNVRAkRq2AEUxEdjYqMgjqnKY2zp3hC3gYK3BG5/M4paf/YjC4ixKyyK4FMnK5Uso3VtJbk4aRlsrbRXVTJt8Kj+cchrzFsxj2dSRnDZtAEJVj3juYY5XOoHcqfAOSn5t6TqKpiGSA8Dlgn0H4L0PV7Dk4zm0bFtLmgZXTj6FmrYQqdIZ1S5Axeqk0XWmIzn/W4Gu2iaFGV66+zXS6tNJyCzWHjjIrMce5IPnUzjnogu48OIfUFTsBlVDCA0FE4FA/Wr7vkI2sGnXHvoNHYXq9rJkySZcgUzOOH0KU8adzOMPP4kRb6JLRoAcVyYZjTsQafkUmO3Mm/MZIyf0JiPkyPhDWsXXlXnUlzZgKG48CrSasL88xuyZn/DZ7I9INNdTFBCc1Tef/PQQWYUZrCyPoWGjdO7hE6BvFC+WbYGqEJeCWCxGTE+QGpCc5G0hYLQyrqefyribJQcb+eS553l/5hJGTJnGhRedzMTRWQQ0zel7G4xoDDwCTfNgC0fCy05cIIF4zMPKFbsp3bYPRVVJ7dqLopYUsjx+pk6awvYVn5HRtIcJvhZyRIK2tgMcdNWzZvMW6tssgiHwHKMpMvkprifwuT2YNggFFCGIxW0UVaBpgqgK81c3M2PGZ2xa/gUpbfsYlSGZ2E/Qw6WTQRt1ES9SOwk8fuK6M0ITNoCFV9FQxHcUL6qqYgKKgLZIHNvjI+ALkWhsIOSJYMgo3dypTOtZSK+ufjZXxdjx3mvsmPcuQ8YM57Szp3HKKUPwulVUjw9bATs5pdqHJlORPEPXvEzCTfXcfP2t7K+p453PlrN86TpGdOtCLu1kx+sItu0nLZTAG2tB84Xome5lcU2EveU6hXn+I1p19JTm9riTGogAG6QCLpdCIgFfLNrK26+9yfYvtyAsjXHFXRjcr4QimslPNJISacITi6IpaRDwE5HNGG0tKFIiJQRUN0IcXeK/ATo4erAQ0KVrEdtXb2FsflfiWhbbqpuodqmkdUmli0sl1ahnSjeT5mybzS0JVi9dyqNL1vP60DGcdvGFTJzSnaIsBbeQ2MivcLoClBQFufbKkxlyUpDBw9IYM7E3v7j+t+yZ/zmBNJXCgEWPghRkVNLmSwWXRjAjlUR5G5Vl+5AjB4P6VUu1o3stW2Aa4NKcDom0wbxPS5kxYw6VG5fT0yrnmpIUilMV0tytuHQVUwlQmQjQ0uwnJxZBSXcR8nrYum8PE6dOwi0ELmlxeJL+jqAn9ARoboQQDBsxin1r99Acs0jJzsewo0QTGnv2tRKy2+mfm4mMh0kN+BiQEyIzO0iF6WFl6TqefWANbz6fyZmnT+DyH1xEdo4HKQQuVSSHo6MF56QpnHbKSAJu1RELqTB+3CjqCJPqNqlv3M/B3dW4pCQ1JUhDUyOBkhLcwSB7d5ahmINQ3AKJeoTWruBoYEKBgAdqq+HjWZ8xd+YcqveWU5CVxwW9CzgpLUTIPEjApWNLwb4GnX0NEWqll+xAKvlZXnJ79GZbbRPB1AyGDBmCpqioqBzT5v93QPe4PcSTFva27dvQzQRbS3fRS5g0xaPYShdkMIMvGiWflElyfIWclOdjWI6gi91AbzXOuFTJtkadFRXVzHzqIB+8v5WJZ5/O+RdMYGgfDbfqwGKiY+LC43eDTOobAjaV76eqzc16UyHo74MdjJDq8qDoJm1qATRmkEjxUVPTjNBthF8jEbMgacm6Vec5CQs27LGYPetjFr05g0DjQQaHJBf1S6Mo0EB6WoSDsTg1rgy2tphsr5M0x9NREPTLkWhKE22xCGpjK412E2bEZsvGPUye3B9FUzF0G7dbOULEOLrMierpnahD703EI8Qj9ViBIIYWI5iaSVs8hagZIJ6dRUMCaprraWswKd23k4HpJkOKQvgVi355aXTN78WOxgBbq9tZ9Mzf+eLNFxh36jhOPftkJk3thaq5MQDTBLfp1G7TLosFKzZyy6134PWm4PV7SPX5KEjzsXf3froVFfDenOVs+Hw53po2pEuCUDEtEB0qkw0bV5bz1ptvsGTRItI1F6PTUhnWfyBdFYM0GYF4EzXtMdbUtrGqppaGYBealXzafcWkKhI1NYwfnZAZJ94exlAaIdqOYVmYSFThzH8OfT3HnzDoEohHW5g2uR8lIkpky3ZaW8OEjRCGAm1tNcR1g//7yVWcc8o45s9fwdxPP2PJnhqKMjz0SxcUalGGmBVMKdRo7yrYUtfA/A/eY+n81eQPHMW5l17ABWfko0qFqE8iFJg9dwHd+w6h/GAtU6b0QDE0fBqUV9eR3b2A8lbB3qYoCTWVqCVoaRcEAuAJQmsM5i1r4L033mb3srl0V5u4LM+gf0hSENDRzRYi3iLWtPjZHfazJxxHze7JBXdfyslTR/LCKx/y4oxVBPx+mhrDtGtRIkY9brfG4IHpiLw8opaNDvgUHAHzn3IDKDgTUSLRTsRuxfIZCCNKekoqe8M+qlvbaWsP85Mbr+WGa8aC0LjopklUu7N57oU3aI2rRCorqGrby6RuKURbm0kLpTKkSzrpeZmURn2s3LiWZ9ev5os3ijjnsjMYduoIdM3Nhi83kqKF+HDWDLZv/BIpVRLRGPFomOzsLkQTUF5Wg1/xE2u2aIpIfAFYPHc17814j22bdpAiTc4b0I1+6bnkmPtJUwz0mM3BcIKNe3exKeKjKrU3ZTEXV592KedeMRIvGvf85kI8qYW8+uwrNHshrAWwpQufTyUt1Y2rWWKgY3BYGhzWyb4j6DaObPKHUmlpaMFw+1GxCLe3ciCRSa2tcP/9d3HxRcOxoypbtu9jW0ULVRWVSJebYRMn4963nLZ9BrMO6BhRm175IQYXpNNdC9NHrWNCb4OdzQlW7a7nj7/bgveNkyjs3Yd92zfhEzAgpxvVlXs4EG5n6iln4lG8LP/sc3J8CsNCXiLhvSi2m5dfns+2zesI7/6SYqWJm0tcdPebpPvLiNpe9imZLG1V2LovTDxm0z0vjcLCLhT0HkfZ3EXs2bWFp55uZ3i/Pkwc25Vf/nw4GUHJP59+CSUhKUoL4BY2aR4/rfF6Yt44QkriuoHflXR7foMj4IRAN0wbVRXg8rJy6x76Th2FUEMkvFDX3M5d9z3M2af1oKqsidr6ahS3j/PPO4m0vGJmzV9JwoJYW5SuhSW0Gho9evakunQ7n25axcCQzsCCEJnpfkZkp5ER99GtVWFLfTNlu+dwapFGYbeu1Cr5tLaU0ifbx29vOge/x88vtq/HisQZ0j2XHEXQVF/NkleeIjs7jwn9Shia0wNPw1bSPKDbsGF/HYsaa4in96Jw+GnEW1vpmmIT0S0SHh+xuM45087kknO6smZJFZ99uJHCHl256uphmB6V9//2GDFviKjbos0VZHPZBkrGdscSAs3dAfY3hz++EXTDNNBUDR3B6LGTWL9+G1VGOr70vpTv2cEd997GqNO6c2B/OwWFmRT2ziKefHD5vp3o8QjSSuAWkhTVQI8cZOygMQz/7f2s+ngFTz/3LAvKmshNgyEFPnqoMaZnupnkFzSoEfoGDSK6xStVMZpqGnj0jsvpk6hGsbzcdsXJ/PqJt9hfJxifV0d2oIZ++VEy8iyCvhgtjQaVopiPKprZXNOCklnID39xJVddcxZrF2xnzquvkmrZuF0p1Bk2qvRQd7AJj+zCGWMKEVoh5WGDsoNhpp87hMEZN7PmmSfo0Ws4e+N+rPQiTp42DZfQcEkL02xG00Lf6A44Pugder7lWKNCwr7dZXTv2pN4QuDzZXH3A4+QNqgfdU02QgRZ+WWYTbs3s3HbetL9LoIp+ajCAmETSM+isXYbma4YB7YsY9i0yRT268PNf/gL0hvgpWf/xrxNqymJ1jKpWxdyXH66ZGoEjGZq6g32VSQYOmg4Z581nnWvPEJUtzjj5t/x0kcrqK3YSy2VFIcSDM4LklBMymqb2dgYYXu7RUqfofzinrtoiocpKvCApVK7cxV5njit4TiegiKa2hKkBNOJxiPc+8DbEGlj5Ojh5PYtoqg4C1fCYMqEkYxQb2LJkuU0N9eTlZrCzo0bGT04B91KoCmuQ6L4W4Du+MIPkwDFUfs1Exr2VbHri+W4C/LoV5zJik/mseGl19jbKtjbGGBvTZiYjNAl38c/H/s1wdQQr85ayq6dOzltSE8qKrYxMDVA2bKlbCjug6ekH7nd+1LU089Jj93LuzPn8OWGbTy1aBFjvVGG5qWRkd6TdXvraNU8PHzHrXgadxOp3IQZN6B8C3fc8ANu//U9bAkbZObkEHD5WL29hk2xEHknTWB8vwJ+8rMfkJLj5kBNFnM/+ZTItrXsWTKP3MxcNoRtRg2YyI652zGFzenThxGNFnHnXQ/zry/WEvCEyFRsxhQF6e4OM6k4hN18AL1tL7X7Guidl47QJSLoRQgLBfXbgt5BdnIOVpGKSkdcKOhx06ukG32yQzTv2ERLQz2t/gxiSi4xM4jwpTJy4CD+9ODl9Cty8+XGevKzU9l/oBJ7/Dhy+o5h5bo5jOrbl9kfzCbimsup06eTGzwD3UrQb9BJnHzV2VTvvI13fv4TIsFMynWbpbX7mXrhNAYO8aG2phDIyUZPJCDXz4Su3Rg5ZgDrl+wjy8okPWYQS8vlFw/9iSGnFlC5sxU7rpCokqz44ENWL5lPSDXpl9GVtTsrSB12JjUihW1l5eTkBtm4dSOXnDOSl19/ijvv/CvlO6rxuLxE68Mk1Fb21GwmPdXDiP4jabM8uFGTYlzDTroala+YQ0fSMZwFSqcDtA5VSAVPihvDlaBnz2xKPAlGpLnJtsCPZH9NKUNGFfHc05eTHXTz8ZxNtIUT/OTGH2Grgrc+WIivZDzeSZcza38MM5BB79w0Ns9+kxd/fStvPP4YmZpCpiIYMcBPt6Ie1Jk+VjZ7qM8s5PqbLiQUciFysxl+zY2M+PGtqEUF4DO46bYf0ppWwqJqD63+AlLz8hk9MZugphBSdF7+85945KZr2fnJDHoFPUhT49MdzbiHnkvGoIm89O5s4rRx330/Y9jAoXz4wWKyXQavPvkLBvQtINzWiG4IPJaLYsVFSjhMuicTm1R0xYeuOvJBnqCn/CjQO2bgjsCTc9lOOrzcXjf1kTZ8WRnoiShCGmiaoKamhlNPnsgfHryMcIubxkaTKaecxOhxBYweXcg1P7gQSzd49d0PqfFkMf7a23H1HMzafXXUtujEYjbNtW08++gT/ON3T7N9eTlRApS2qayraODiSy6mX76G2rILjCgphSVkdO+BYiegfiuDeqZy0eWXUBG12FIfJ6oGaCmtZ8ZfX+Tvf3gQS4/jTwlgKBqlBxpJKejHyAt/RGtKF557fQa63sq1V55D0K/Sp8TDDy45FTsm0EzJE3++lZFDBxGLxfF6fXjdLoIpqXizulHa0EZUUTGFSPL4N0aAHUb+6lei0yVH/XEpYFjQo08v1j62j9UDahnaeyDhA/vZVdbCuDMu4Cf3XI3hddOqQEJqzFlUyzvvvMG0SUP5zS0TUVoTzJ63ipkz3+eLnkVMHHUSPS8agt1YzcZVyzHqGyjJDIG+kfd37WBrawbryxop6d2dm88cy8YH78BVsQGXCOJxBxAKuF2S2ppSUkdM4Wc/eIClKzewdU8DRszmzT8+icduxa+62Fp1gJjbTfehExlQNJQN28pZO38xDc2N5KanMHXSKO66eRwvv7qAu3+1gDPPOIfJYwZRnJdBl1zBs0/eyAsPzuTAio+ozbbpWlLM2qY2Vh+sY/qwAQiPiks4iJ1IHEMcL9nIgVtiYoFUcSFojcGTL8yjeddOru4dZNeqRVgFvTjz2p+xY38zq7fuZ9XWcnaWH2Dv/r2cfcZEXnjsh2zf2oQkm6JeCk++tpm3P/qUA3W1ZIRC9C7I4/SRo/FHwpSv+wLZuAtvag7r2zLZ2xTm0Qdv4JRiwdKHf8y5p47GndWFrS++ikdVKbnhatSq3Xy0YjPTHn2HN9fW8uBDL9I7kMHkkElt+U7aMrPpNn4CdnYO60vLWbt6K0JxkZEVYuyowTx05+msX9NI3YFSzjxrLL/6/Zu8+8F8clI89C/KZWhBDqcOG8zEwUNZOutVPM2bKBk+iuf2qNSl5HLdtWfQp4sLrwTFduKp35QR8I2gd4QXOtIPHnlhGTuWLyd//3pKAjoZBdmUN7RyMKKwvcqgXu9KzB0ivSiDZ569BY/uIRiEUDrM+nQfAX8K48dn8Ps/fMreinrWrttMImExavhIBvcpIVMVtDY28+HiNYwY2ZcX/zadxr07UVsPkj+wBCUSZtVvfo0/LcCAX9+Nmp7PzpWbyR8+FSPg58afPsP65VuZOmwwPUt6YKdksHb3Hj5duhgCgkkjB5GVqnDffVfzykufkp5SzA1XDsJoVinfW04ovxu/uecJtm/ezUk5KfTUy+iqhEnxuzipbz/aqmvY3gIbUgbh7zeAP9xzFiGfC2ElQVP5xjyT40p+x7YS6FLHhQuEIBKHrjlZzNi0lfGnjEM5uBVvrI1h6QrpsRbyCnPY0uqhNJzgVzfdQEHIjYzCitX7+Mdbb7OzdDczXnyKsm0xLr7oLApLBAvmN7JmwybmzFvAl7u2kh/KZ9SQYeSX9OCKH07H7XZT0LMXuHoi7CjoUSIYKP4AUvOCdNH35LNAKMSAm2/9KX8xXyVY3JsP129ix+4ygplpXHTF5cRijfz6jrOorWpl05qdnH3aZH7yk/tYtbgXt/7wXIYOLMJWFe7+2U/5zS/vxxtvo2eaRmokTFFmDpG6MlrsFFK792PHsr1Mn3Iy0hJgxkH1gHpiQVIFKY8MyR/B6eASbhDOFJHigfOn9KVPcRdq4iq9hp2MEjFJqa7i5BSFsd42MuRebvzhZM4a42PzJ1X8/hf/5P47HmHl4m2cd+5lZGW48aWo5PaGex6eQXE3L1efP5JX//5rzjplIKZoYdZn76G7DXoPgUQCUH1Yqh+MBBgJPNhOvBXAp6DLMJa0kEhK+gpMTfLPZ/9JW3MN004bzgP3XMe9Px3PyN4hbrzlIbxpQQYNGIxfaJw77TR2bd3O7377MHfedj/vvvwBvbM9/P4XN5KiGZjxGHnZObgSOpZhkj58NEZRMZl56Vx10WCCXg2EF6QJ0jihdLMTiy8lSQgI+eC6a3/AZ6vWs6XJxF08kqKBE0lVIUuvZVKRi7GZEV686S4+fPhOjH2bKPSrFKencOb4saS7Neoqy/jZjY+yYtlKQn5BSWEK8XAzRfk5zJ55N7/55S3sqyjj84UtuNxOBMUC8HjAttE0DU1zAh1E47hFCrYNhgELl9exrbScG2+8gSee/C0pqX7y8jPAkgzpW0jD/nJuu/Z2lr3/MdkoXHXu2XRJTyXF60OJxNgwZyZ/v+XHxL78hIsG55HrtckvKKR4+CnkDD+DalJ59p33uezKC8jIcHHYg644vHsCzP6tQAeI6zrTzh3MkNMm8/LKjXyulvBGnY8VB2twyVb6JKqpmfkY/eoXcn5BLZNy6inU9vCzi8YyJN/HW397mqfue5Dq9aX0yigmK02lokrnV798hHC9SaoKfiOCR3qY+eZsaut0LNOJ8AuczCuPPw2vP4jADf4QJgpSVYmbgpdefZ9oXJCVn0tJL0F1UzsP/OUZWjAo6NGdYfndKIgkWPTcCzx9152kxdq4+bILibfUkWa1c1qmwhmuOjLXzSB7zwJ6+9rYuGMXH9f5WBgr4rn3lzN+wmQuvnwkiltDHnIoqiBdJ4T6twbdF3CjCMGjf7yOy66/lhX7W1l6IEE4tYiYJ4CHKHnuBCmuOClKGzl2FRNydAZYZcz67fVUfPI6w7wJRqYYjM9yE9law7O/+SVprXX0UNo5sHAT85/5A/38kuqdm5n13mLaE4YTTrJtOFBHdX0ztfXN2PsPgO34O9ri8M9nF7Hty634jTbe/8fvKV2wk5O8ksbli3nhtw+QHa5lWq7G5DSDM0qyyY3W8MrdN+ArX83pRX66GNVkqe34RYQ0dzsFGSqay8IKBJm5bhcbmiyuuPEWHnzoZhTFhUR3cktOMDbaQULa8siAXpKOzg/vTJYNkSjsLo9z6bW/5PwJo7mom426dzE07cDjdhHqPpItGzfTVWkmYLRh48IfTKW5NYwrPY/trTZKqCvxtgTRuE7EMsnNSkGL16D60ginDGX+zloqpMk/Xv4Lw3r6Yf9OPn/6rwRibSheP83uAKf94h6srCzWbhXcdMtvCHk8jChMwbNrHj08Nl0zelBT20xzopn8HA/ZVjPpfo2o9BH0pWC1NaKgo6ERTtg0aRoTTp5M2fa1GPEIrYZN0eRLeHJ1jM+3V/LBa3+mT5Ef1ZnqUGQnfIQF4pszmr9VhpdDEoHErQl6Fnt5+emHuO+uu1Hq0rlw3GkE4/3o36uY196ZS6zVYmCum4BlEEOgmVE8kTpSXRYjAn6qWxpRfN1QfF7a2+pJk00kogdRAz1pSfPh9fioO1DPP56ZyZN/uIJQRj7Tfn4nGHHwuMEdBF8GGvDu7EXUN1uIYJz+Bb0Y4C4ms7GMgHWQQLwZmV+EbYUpUiN49Tg76g1aghn0Liqi+cBe8v0WaW4v9bEUluyqYdr5P2Xbrp3kBnzM3lDK/iZ44blH6F7sQ3UdTtM+nEImT8wy4luLFxMII5V2TC9oQRgzOMQrL/6Rclvlpy9/znvhnvzu44Os2HCA3GAaRiRKQ0xi9JtIfNBUqrQMElKQYbaRS4ScrjkkMCkM6uSb9WS7QHUFWFnZxsZmBZe/K8uXb2HBsnJ0GUQGM2lZtY7YF8uRbi+4FOYuqeaTz1ajBrqyP+pmc1kdIU8armgEj12PN2hSY/lQ8wYQaYdUTwoF+QVsKW9gp6eQpuIR7G5voi3eSMCdxvyFe3jq42q+aB/AdU8tYU29ysOPPsSYk7x4PCAUy4n4H0qW7AD8xOD8lqB3pOw4rh0PjkJRUhLir8/ez2+ffJxt7RYvLVpDv6lncNLp08mbMJ3MKVfSWjSBl1ZWUqVk0ORNpSyqI3OL8RQOZEt1C6biJipU2gI5JLJ6Uho2yekxCFvxIwny9+ffJ2IasP8ASxfPY8Hn8zDL9mOHbZ5/+T0iCYEhvKRmFbByaxm1tpcG4aJeDyPSPSzdvRvZtTd2l77saZe0qy5cuQXM3FhF7rRryZp8GUbRSLqPPpuew0/nxdlfsKPB4FeP/oO/vfIog/oEMBMxVHSE6JzmbR2W64dSw7+etOPdoxxTqmuAHwWBl2QZyeGVlwLnjE+hW8E59OgimTl7Not2+SnOzqFLl2J2bGlCcfVi/LBB2K4WdJ8Hb8FA3v90F2GtiF1WPYGUID1Ou4x35+/AX1hMUPcQjesEUkOs3lTFux9s47oBNoreQrthIKPtvDZrFVv2RpDeAKZpkpmaTd/iscypWs704eNo2bkEqWqoeaks3lPGzef+gI2fz8Kj2PTr14vPljfwp4+3c+nk6azcPo/SNV8S1lXOPmcqV111OicNc6OqIIQk5FeTTi3lMCxS7QzaUex57DnxuG6Ar/9Zkjp+KZ3sQF0oNJmO56exGRbOX86qFVvJySrkrTc/oGd2gAsGZ+GmhdaAB0PLZNmCPVx13jkMzmsjlOFi9qb9fLRyN1dcfSdP//MtDtS2UNSjL+MnT2D1Zy8x78kbKF38NlHbYvTZ1zP1J88w8qwb+HjRUlpbGrGijdz782tYNfclxhT7GJIjkNLNjvZ83vlkEeeeMpgQbbRU7aQu4WJJXQrbaqJcdOYUPKbB8AGDGT1sMIMGq1g2uDxJ2S0SSUw0jnBtneBCtc6kfXOG79Hm6rEeYyOFjSpsMl0CA0jPUOl52Xh+etl4Kg6YTBndk12btlO5Yyd1DQZ9R/ajsraZsC+Nfy1fR1CroyVcQ4vh4aab7sLj1lDtGKk+F247Ttc0N9FYgj++vYA7b7sDr9fNn/8xg6oWk/GuAH5bwRImutJCtO0gV//wpzz+yMO8HQ3jDaZjiygNiRDr621SU3w0JlJw+1M47byJXNe9hOH9ezK0pxtDF3g9hyfJjmxf0cnVfWKp/8cnYUt5HHX+eFHtTqAf4nQLKWwQEolNwkhg2qAqbqSt4XdrWLbAtkHqTqYsXqhugXYdYnHQvE5DVaAoC/58z5usXrEFXUmnNWaSmZfJyDGDWbhsLg8+9EsCfh+/+tWD9Op1Cjt27KelsQ6vFqFbepSgZvDc87+jqd1HQxziOuSkOCsrdAE5eeBOSgiVI4XnYX+Vk+R65Moj8dXj3+H04yB7YiQ6nt4h65yvfK5OGeK2k5KsdVx0TEtsoCAdDBwT30he9gONlRb71i5iSHEf9rR4OdDaSsX2MqacdzEJuZ4nnvoIoZm0xNyU9Cjmk48+wZ/iJisoKfFK6g7upq6+ifxe+WQrCooEteNIlmNJp2pK52YANgYCHSUZdjsc2OmArjPox0A0SV+noXxri/S4JJXDR+eKda5jxwhNNlbFxoPEiwO2BweMrRs30FpVSrrLwE5EwTbx+/3Mn7+A/v0GUllVTem+SgYOGsS6pQvITxEERIQMt0lhlgerrYa95buIGCaqlLiFxI1Ek452h22j2hKX7XTE0bEywVFt+A/Tdwf9KyNOAhZ28rCEjqV0HAZSccajLQFbQbEFLhO8Ovh1iMVgxfptDBzYnzSPhk/o+BWDktwU9m9fTVaawtDBxYwc0pvCTB9Vm75gQJpCF9lOgVfic+vklRTw5aa9+CW4pEA1BcIUHavVOLz+6KtgKLhQ8CHw4bBB53jQf2bB6n+O08WR6ywd6ryM0DlsnGEtRSeVU3AIkLZ2WLFhD4PGTWPwuEl06VZEmmYyvIubLOMA8Zo9VO3dyf49uwlXV5Kl19E/DXJVi67ZOaQX9GbqeVexasM+muPOKrmvBBeOxbySr+oMh6R+52D9d+d+5fg/V45zHPWLTnVwrnZumYpAQ+BOnlUnBiWkY0Yr0BaNIRWJ7YqTUCUbtxvsrDTYm0gha9hw9hyoJz/oYkRKHWNS6ilb/QVmq44dsSlduYrBaZLenghBTbCzoonh0y6hThSyemstX26JkzAkFs4IM91gKyCF5FCoR8oTYGC103F8teNEDsl/ktM7kdLp3+HO6pCaHQ4LG4mNP8XrcL6m4dZgw8aNtMclHy/dwPV3/IX12/biTQkQjbRQmJuBFm2l2O+lR8CHq62FvMw0opZBRrdiNpYe4M7fv8RLM+bSloBNW7dhCgtbdXzdBia2YnJoBJ7A+qD/Dj7fe3GHi+wYvM4njbpWwcZ1Sxg5vDcHq2vYU15DID+XYdPOITjwDLIHnIqIxxiYCsNSBd72Jny9+mH0GcZJ51xCeu9+7Kgop3J/GZPGj2Tt6hW0tJooyTQJbIlyottb/Bfpewa9c7HOYOsYbpYJ2zaW4VYt7v7VD5l29hRu/b9baWqP0ZDQGH7u6czbepDB46aQnpNFamYqw6aezKLd9Yy9/DLKIoID4QQ/uuUmzjnvTO777fWowmDPvoOEYzZxXTqy5Ygm/+c1kxOh76anf2eSh6S/S4FFC1aR6vVQ2A3++NA5vP/Jfjyal1mzF7Fzz17WVkWY0LU7Z118BUJVmP/MC6woq+DeP81jc0UtlfUR/KEQ99xzHi4pcAmTxUtXMWZIAZbpRnUdubD3P0HfNHD+88bRv0NHLWHuyHJtaYCq/XUMHt6b+Z+txJWRzisvvo1HERixNj5buBR/KMTcdTsIlmxAc2t8vq0CT1o+KzdtxVbddMnL5oMP3iPFcxpWex0Txo9h5ep1tNs2ITfYxv+kxV+h/5F44dA2HwKQFqxdU099dStnnD6JzHQ3vXt0JyvVx9UXTSVAI4N696BLl2LCCQ+vz/qcV99egC6DZHbJoEePNNL9EW77yXRCIZUhQ/PJy07nvLNPJRKLsWV7BMs8KuvhGBb9f8kW+gp9//1+qFGHfdKKhHVfLMcVa8PbXMMZwwcxb/NB9IjJj6+bSI/CAvqM7MOj/1hAbrcM1m/cgKXrDB44kIDH4s7bL2Tn5n2cekpXFi2oZ+OKbVx13mAOljZgNzSwaeVyxg86C6m4vvfmHov+66B3HkrO1GnjRKAci0UA8QbJrpXz6eNWWfjEQ2QUdeONrXEMJY1oVHD2uf0prYbKyk385a8/563Xm9DDCjdcdx63/+oxmhstzr+gD+FWcJlR3vnb3/BtHgTRdnpjsHXeHJovGU92biaWODLN87sy978jKr5XTndWnjnbL0lnqQEg2LFpC7K5kt59eiKbmqjRNWLNKQybMoJFS9aSkZHKwhV7aG+sxa9J7rjlanyWs22TqSf45ONPiUZ7YrSHGTZoMKsrqgk3RkhU7WNEVipf7NzGto1bGH7qRAKa9j8X69+7THeUNoFAw0LQ2A4ffb6CHDVGrs/Al9ubXc0uGtrjXHzpRAq7d8Xj1bjwrNPRW9r5aMbnGFELIy6YOXMtjS1xxkycTH5WDnmZ2Zx9/vnUxzUWb62BQB4Fbii0dT6ZsZD2uIktj7T4O28PdWQyxdF3HdNP8G9j8D2TA3vHHimNUVi2oZRQt2KaVQ8LdtezvqoJt5XAPNDI1CHFnDW1P9s2b6BHrxJ69+3DzDfe55035tC9az6FXQvZ+eV2xvTMYtqgPtDQjE+BqrDOvPWlHGiTdO01nG2lLezea2MepeP9L2zS73WkWQhsXI73XYKZgFmz17G7RUcE3HxeVU1Gr6EMGJxJy8r5lM1+jbz4WHa2tvPqjDmUDBnBKVMLEfFq0hQvp0zJ492PMln67icscrUzpDiFLUuXkG/XM2L6tVRVN/Pspx+RntOFne0uZry/jIE9puIPuFCSDrfDrhd5yBN92FXR8fk7SP1j9Or3LN6cSSysx0h1eTF0ySez38YWMUK9ejH9lNM5d/pA/vnAB/hoJaV+B5++vI76UB6WmWD3rq3s3VLFOaMGEPClsH9bI/VllXh0wbalq9n93layM6FYaYZEM3c9cCmlF13Ev16fibZjO3PmzODHlw0mq0+Os8mO4D+31eG3oO8N9KRTlwQJvG5Hqu3Zs4nrL5nAqDHjyCvIIuhTaI1Dw56tjOmikCeqcWVn0xyPo9gWKcDC55+k4OThaKEMPpr1BV4zQFM8Qbglwam9SlAb1qNrLaxc/Qkh74WMHR5gwphr2NsIsz96n9a6Cqxembg0jVgijtvl+d6B/145XSDw4KZj+ho+fAjDhw8FIGbG0fBQf0DQVFeH8NkkFEFVm8HmilbC4QD5qZKuMs6il54kxecnPa0vPpdKQknwZWUNPbK60j8lg9xAiNrSMNt2m4wcIFFVQa8CuOumCw8JChvwebxOMOV7pu95IhXJyKPqyNLklrKWaeESTtpx5f56muIGem4P9qhdmLklTKDvNK654XZiDQ24Io0UeE0y7QhBq4XK/Zs55fKzKTr9HJ5fu4flbSFas4ez38xizfYaYlLSGmnHwsZGJuNZh6Q4inBy+VUhkpHejm45TvzghD3nyUMcfZzoGrz/IAnZuWGOTBWK43Y1bFi5bh1RT4CFe6s4WLGXgadfya333kQg6GHn52/y5Z41TOnVFb/qYn3pAUKZhfz4lkmEAgH+EpC8P+stCqN+tNwerN9dxrWUEEoLIDBxwogdvv3/HX1vnN4R1Dh6WauUEkVRsGyLpiis3LGDzfX1RDK78H+PPs4TT/6cohwPaV64/uc/YU00lWVyIF8wkIWNfn58++3kBr2kKPC7+6/j10/9nZasPDZX17B4zRpqw5aTC2VKsB2Xw/E08++N5PdMtm0f80gkErK8tl1eevtT8sl3d8j9jaaMx6S0ElLatpR6zDk/8dc5csCAi2TfXhfLPzz4rmyL6tK2pYzGpYzpUoYNKSsjUj712UE58ZrH5KI1+2W8zZJ2e0JK05DSNqXV6Z8t7W/ZAus7Hrb8mrS675cs00KiYEpnx2gFcHckwyZDTHZSj7733ieJxgQP/eFGfH4PCPuQZ15J6t3xpB7uTXK3SG5P5dxmf43q/e/q5ScakhJfl8v4P6LOde9UM7sjtyeZu2KBY8woNlLo2HgQCFSpJ0OfySTyo1vXAfpx6b8P+r8/oxwnney7kt1plnGCyYczKFRATbZNTZZvYGMlc7GceKv7q3UUnToN28lIOKLy/x/Q0+1O/x9ulNnpL5HUIg67WTt+I5MTnEhCbXdK9hEdcSYzedZEp4yDJB3hk3LMTvtQCR1xquPpDx33dtTTTu5sAd+8t8WJ07fXXo5ytFn64aWT0sLZmk862oqJTsLUkdIGEiRki7Pekk5pSCZIG2xpEdOjKFLFjMcRUkfFxGVZiISBakVRpI1QAI8KHgXdTmCE29FsgUs6w1Z0xLxtQFFAEVhWDCHjCHSnyVLBNiXSksQT0eSrFRzAdaujPU4HmSRoJ0K7Fce05dcsEz06P+j49O1l+jEW+Zr2YRBl0tgQySw2x3UkAf1QrpRpCBK48GoCl3A6Se+ougWqkJhmBEVVEPiTZrqNZemothvhEkRsG5eq4LbFob3KDNN5lprc/NKywLQs3B4FISxAxTYFInkdCYYtOfSKD0VgKhBPgE8DVTWwRcdm5K5DabInJpCOn/X87UA/ist1Aabo2OvEIReH7TiFr85jquHsHWMKZ5WeR3EAsG0nZdrvc3bccKlOB9qWA56igtaxd2sStJh0tBNhgK6AcDkWpplwylLczn41cdNheqSTdWAmN29SjmJI3QZTA484LPISybZ4+ebMvCPp+KB/e5kubJACO5nLIIEvVm9jw7Zd2PgIqmmYUadQj1dQUJTK/v37sE0P3QtL8CA5UFWJDnQtzOGUcf3QUNm+u5XVX27HsGxS0wIUd89n1ao1BHxZhMNtpIQ8dC8uYNSIYj7+ZA1xxUN9XS1nTRpHXfVBKuqaaE/oFHbrSnVVNdJWKCjoSreiTJYsWUR6Wi56zAAgFouSmpZKj+ISDlTV0dzcRHZuKoOHDWLu4jV4PF40K8yEcSPYuGMHNQcrKcrL4NTJ40gJur6zg+zbgS5sRwB32oLetuGvj79KTVOMrJwitmypoEdJXywZo6W1hksuP4M5c+ZSvreRX97+SwJewTPPzKI5KkhP8zHzjd9TVODjmbc/Z+a7CzAxuejSc5kY6srfXpuLtL10714CJNi161V+cMl09u3fz/qt+/D6PHTp3o/a6kb+9fZs6hqauPnm61j4+VI2b9jL+eedz8TJQ3jlg0VEWyXdi3vi9do0tzRQVlbOz356B5/PW8nu0h1MOnkAad378M6HK9mzu5w+BekUFQ5n6aLdfDhnFiePG8Cp48egSHHYdvheQJfJ8SgOnxQbgh6NKy+ZzrnnT+SMs3/Lz2+9nsxsH7fedgcXTR9HuLWdfV0buPjyfvi9HhavHkPCDlG6axurvjxIdn53SivrGTJ2MuFwCzfcOI38rh6mrTqXyvJm/vnUdAJ+N/c98Cmr1q/n/t/fyQ0/f4RLLv8Bk08pJOApZu7SL5ly+jlcefUY0rMzaG2dzc9vP5OuXbxs3n4Ku3Y08M+nfkjA52FfOdx/358YObovxd0H8tCDD3L1VdcwZJCPk08/m807nmPKtAvoP9iHL+0KduzYw+23/wJf4Ojt8P89+nbai+j4ibM/uQJ4NfjDPTdy9fQReE0VnxXBaIkzup/k5afvpyjTh4i2QqyRTJfE64ZIWxtFxV0oLOzGl2sqWLnceUPXhAlDkHorLksSEKDqceor9/HXR9by6MPLWfTpRwzsVcCgHgrjhw5g4SdzUC2dsl2t1FTu4owpI/GoGom2g/jUBHq7xLZBsSM0HNzPs09s4PHfzyXbbfDSU79h7FAfU0e7yPCE2bd1A0bMZNmKL8gtyGHe4nm4VIMVKzeTlpZCYQ83ilsks37/Hag7ZjlxLNC/Lsn3q6Rg06c4l9w0L8KIoCFRLAMBDOydglsRCEOgGo7G7VEA0yQ3zceoIYPYtaOSD2YtYkDfvmSFPLhsE58KMgFBlwvV1FGsdqRex+23Xs09d16JR3Nz7pmTqKnaQ/V+m5XLVtKnKJ/BfRSyNEhxuXHbCplBCCkQ1BQSbS00N9ShmjYuCdmp4FWc8+D+xaxfvY7NG6JEwg3cecctHKiqZvU6m62bdzNs+BBU7dtOfx2YHQa7g7Sjb7QPgfxV6jBsHKiTxoKloOIhlrBJGCpuXwaWrWGbIFTQLdDtNISIYhgCsxlSvSECVowzTx3Ku6+9S2VFJY89/EtamxswY3EsXRLwgG3alHTvxp13TCaY6iGUVENtYOrkbPLyU3lz5ueU7tzItCknkeVR8QiQhg/bcGHrwon+W1BU0JV7755GfpaXyiq48ua/cd21lzNhcDYjR43gtbfn8/yLbzCsbxFnjnfzTteBzPjXSmobGrnq8rMJqeoxMTk+ya9+TKZmf4XTj7cU4FBfJd/gpXSsOrMBVaDrNm++NZPa6nLeeuslDlS2EtQkn31WxqrVq9m6ZSMfflDNwgW1bF23jHnvvUHdvipKijLIznChtzcxZ+a/OFC+nffeXsbcj2tYuWQh61bN481/fQa6QbuMkTAMdF0S1ODsaROZ+fYb1NVUc/qpY/C5NHbsauPT9z+iumI3r76wkGWLKlm5ZCkHy3fxm1++wC23PMc99zzG8mXL2bFjO4piMX7cUFpb6lj8+acMG1iMX1EZO2IQixd+TIrXZOhJCoYqOm0T+t1SM47idOWo8/E6z0aIpF9PBSzQhEJGyM0vfnEV8WgEn2ohgPRUnbNOH4yaEGSEDKSW4KorTiGoCfKyXNxw/TQisRgD+qQzekQxw0YUUlISoku2m0sunEJMr6VbV0hVQBEuojKGzxUkbMIPp5+BGtcp6JpBfm6QuJkg6IXxo/sxamgfcvPcaHY7k8cOJ5SSQTweR1EltvAwcMhZTB7bB7+m0KdXgNtvvYSa+iZOnzocxVa55MKRBL1N9O6diyv5ti7HIWEdG5sjcsaOglZ0gOfIkUPGUYeNJI/lmev02w6jQQrnxRsKgkQYNLezjZUuHDM63mrj8gpMj0ATzuq5cCu4Uhxjxy+clXTtiiPnjTiEvM776kwgGgGvz1nviZCE420IoRB0B7CEIBoDf3LtKYBh2c5WIMJZbNMx0QPo0nE3CIVDL43qeG2InrBIdStELcezY5mgaeBTIWY4xpZLc6zso318xzKS7KPOh+853FnCNEypqIc52xKChOlYgF4BcemsMYtZjgXZYWIrHPacimRlRaft8YQBqBATENPBJx3t3lSTFl6yBXGXYzVKA0wdUv3QZkDA5XRgTLeQGLhdnkPrljUBpuFoTkJwxCzU4XqxpGND2Mm2ulyOp9GdbAsSQsn6iSQkVlJ+CAmq5nSOwOFZC8evJG1QFceaVZMMpiaxMOXhOiR08LqdZ8SMKCHNh5V8nkiGQwBYuGQtS1bvod1w4ff5AYhEIgSDQXr360tp6S7ao63kZ4e45ofTWL1mG+s2NmALL4V5AWqq9xOORsnMSOWqi09l5cpNrNhSgS+QSq9u2VRXVRKJxxkxYgSnTixi584wMz78FMXj5qRePSnfs4+YbuNye4nGwuR3yeS886fQLc3Fm3M2Urp3H1IxMBMGJDR8qptQqoupp5/CgqXLaAmH8bhUGuua6NKlG1OnTKGg0MV7sxbR0BR1Rky4hqz0VM494yzy8v08+exsdMsk6DGZMG4sa1ftxDRswvE63B5BMJDGxReeSUqqi5deehNTd2HoAikl2dnZnH32BLKyNLwCFn6xjw9nf0TQH2DqlCmUV+5kxOhe9O3dHVVVk+7ppBtACIFt26z9chNvvb+MwaPPYO3ahbg9bgYOGMjSWXO49FIvFVXVLP1iEadMGcVlP7TZdzDMq+/NB8XPZReezKYNu1i1biOTx43l4ktOpqymjVfeWExxSV/cZwRYsng9q9duJSPjcz5493Esxdlbpba+idtv6cnWnU0sXbaRIcOHEgjZfDhvGS+9No/nn/s9Mb0LL//rFVJzffQqKcFreGmuq6SiajuZ3fqzbE0FCxYtZtLY4QR8AeYuXMr7H27ivt/fwoadFXz00Rf07zeIjOwgH3w8n09mr+MvT95PaQUsWLiY8WN6MOAkD0tWlrJi1VpGjxlEWmYGWzav4r0PN/HIY3exdW8j8z5dTr++w8jMzGTXx2t58Y35PPnXe7Glj5t/8SeGD+yFLz+dP//pH2zbsY6XX3uU/r1KsG0bRSTXxicSCWnbtrQsS/7+4b/Li376sCxtj8nTfvSSvOqeBbK03ZAjz/+dfObTOvmvpbrMH3+XnL+rXTZYUtZIKc/7v1ny0vsWy/KYId9c0iS7T/q1XFQalXWWlPvjUp5y3Rvyl/+okPvjlvzT80vlhOl/lsNOv19efdsrsqw1IX/7t1J51vXvyer2hPx8g5R9xj8g3/siKqviUu5pk3LMBX+R0658Q5a1JuQ5170sL7ntfVkW1eWBNinnLrXl+T94XG49EJPvLZNy6FmPy0U7YrLaknLGF1KmD7xdfrS2Xa6pkLLr8Nvk64vaZYUh5TMfHpS5/a6WK3ZG5KI9UvY/62H50twaWW/Y8l+fxWSviQ/JpfuissKS8vVFUqYNvEV+tqtdLiqXMn/0TXL2una535Byb0TKMZc8IU+77hX5t3cPyPxBN8i357bK2ogt12+T8k9PLJRrt1fLNtOScSmlIaU0pZSa23040nL3L2+hJhxF83qQpg56gqCUvPHMPYRyNOYuOohX8fL4n+eQk66huRS2bPySkWNHEbclRqIdgJZWR9aFPKBbdcTMGloTXUjIJgp7+Bg36nQe+/PjlJdfjOZW8fsd166ttWJYtfhcEq+ArABcfME5vPzqO4SbbdK9cXZv3cZ9t1tkZqj85tdn89q/bkdRYcv6KLItzvN/f4/Mrrks3rCNUVOHMniARsWeFpAGr742h9lzgmzYtJLLrruElFw3zQegrb0S1Z+gHUnUsmiL6Tz2xBzS09LYtbOCk6dNoribxu6KGiwRxbQkmgVBP1x13RU8+Me/cFPBRQwY1J2b7vo1XfN7M7jfEK65YiIlvTVQLTTkoSDIoRm04zW92ak+Agq4pYJPc+MBCtJd+IRAtU0US9C3pB+FXQoo6JJHyOcnEWlHWBLbiuHRXLjEYTeoquroeit+j8Q0DGqqKzjzzN707deX55/7gFi4jfbWBmwpieutzu5wTk4OcQsnUUhYKC5JNN6Gpnnp1as/hT2K0RWFiOFoOx6PH5fiIiM1k1g0xq6tm7lo+vl4FRdCN3Brbrrk5tO/b1+GDhzM5s3biEQscjLAqwiMRBwT8HkCBAJpZGamIlSDsn17OO+8c9FcbmzbBkVgWxY+TaIJaAmHSdgm+fkKzzx7N/c/8ACjJ01hy45SLr/yZpYt24bHdNLDDd1GSPlVhVxKBWkJPKobxXLW1CvCWSQlEwKX1Jh+fm9uu2UMd/5sHD0KS8hN7YZXVeiWm0l7UzNVZe1gS7ZsN6ncU0ZhbjZuoeAV6aR6snBJwc9uvIktmzby2YdzyEhJxS0EmupDSi8uj6OmVdTAjHdmUVTcA+lWiRGk+4DBXHNzT867agird8Y57eJfsbkyStwLbdLisssm86cHzmHksFEsmbsMt22SGsxGtTXOO2skN1/fk1t/fCll28pZvegAerONX2ShmW6EDrId3LabG66awh/uPYeeBQWsW7YJTBOvko6tu7FsFcsWlO6F11+fyaABg6mu1rj/vrcZ1C+Ve+4awsvP/Zj0kMquHTtoMy1MS+J2OTvZfcWhYFvw1usL2Lx+OdiCCScFuOjCEewri/L6y8/RHq7h7399mccf+RHPPP0Om9auIGFKhvYXXDx9NBPHDOT+u3/NjNe6UV1TTmG3HK64oA97d5nM/fgzKvfv5p0Zw7jmqpOZMvEk3pv1OUMGF9LaBo/+6Q9EW2v43b1/Ji0lyK49pWTnF3D3nRcx/9NSNn65AX9KFTfcWI5ut9DcWktlVQVr1x3gvXfnUV1dyiOPPMPT/7iJccP68/wzz/BUhkpZ6S4aa8p49KHHeCbo42BVOSEvFOSm8szfZ9BSfZDXX3gZv7iFN175iJbaUh5+8Emeeuo2xo4s4fXXnyYv+wa27tiMHQ3z1GOP85bHx/adO0jvXsiffnsp29ceYO6c2dTVVqG5NWLhOC4lzuiRQwm6NOftOR1SpXPkqCNsO2/hWioqwximydD+xQwZ0pOmcIIPP5mHbgs0DW644iyWr97E5rJqTFsysFchk8YMoqZOZdXqXWzZvom8/DTOPmsi6eleqqoizJu3EM1rMWhQP0YN6U1DWPL5/NUUdyukT/9cZr3zDtmZxbTUR7GkIDsziwnjB1GQp/Lpgt3sKavCtJNvdlR0ECaBYICTThrGlk07Sehx0kMuTj51JE1tGvM/W0zvbtkkYhEaw+20RKNYCehWkE3f/gUUFeUzf+6XNDa0kZ6eRt/+A1m7ZhNCs7FkmCsun0x5dStLl35Bzx792L/vIG6p0NYcJkXz0a2oG4PH9iIQUKmrslizbh25JYUsX7kS0zSZNGEUI4cW4tYUR9zKY4DeQXpyTUjH+5otR5Q5bzdPdow7eY7gpEn4kkaUZTq7gfqCELUgtZOfKCGgLW6T4hH4hCCGE97TcX4rcQyaDgawTMeIUt2gm4fLFiSNMOFYrC1tkJri/B01nbh1h9EkcCZ1UzqjuMOo01QLVThOOz3hhAhVDbSksaYn62N1WJJSSW4tkTT8TA5vedBpnwY9eTjBeQ4tFk4a1oeNo86Ax2M6LreKEBJd1/F4fJi2jW2auN3OKzItTJRkmDYZX3fK7WilgGjyeb5kJW3NybqyLKczTdGOgoaCG3fSoyGAtvYYfr8XQwjaEu1ka37MOOAHWwg0G1TrSPNbCMcH5FiQh/d8tywHTBRQVQtFGCioYEuk1DF0Fdvw4lIFakdwVzUwZByXCIIQJCwLl6IgMVBxgSWQEnTdcMJ+GSGUZBReApZwMhaE6JxdIzoWehyf0zm07FAipYqUAiktFEUcepjg8BZSBkkghNObpoSECopwdi3quC9mSdyK4x+JGGGCWhA92UtuAVFLd7QN4XSmjYUdNQj4PESTex/6D+WfOM+0jc7uh+QQRcG2JaYhDvkspN2GIgw0zYMQSZ+p7QFLYOlJv4wX4vEGvN4UhHDsR123UFWBoiRzTYQPaYKFjqa6EZY4lK5nmzoS59XJUohk7rt2RH2/BnQ4/L6jzk74ozKjZLI3k2B33snDSpbTeS9auzN7HsMl1Jk6OP/QnlvJ74+VMX4kHfncw38dI7NLHhUGEuAkPXb80bm049T3K5luR8YinDVN4pBT6pji5XiV//b0XX//n6H/dS2O8N5y2IH2/9N/kTrSNTpz9v8DJ1i5bF8wByAAAAAASUVORK5CYII=",
    "Woods Cross": "data:image/png;base64,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",
    "Bingham": "data:image/png;base64,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",
    "Cottonwood": "data:image/png;base64,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",
    "Farmington": "data:image/png;base64,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",
    "Farmington JV": "data:image/png;base64,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",
    "Granger": "data:image/png;base64,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",
    "Juan Diego": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFAAAABcCAYAAAD50zLWAAAxdElEQVR4nO29ebRdxX3n+6na05nvPGi+miU0IiEGYRCTwGAMNgnYTmLHThzbnY4Tv2T59VtOei1n6HReXvK6Ox07r53YjkPigQA2g7GZsQQChBASGhCa5zsP555xT1Xvj9rnDkICYXDeWq+77trrnLvvHqq+9fv96jfV7wqtteb/h02hpv0ukW9/w7koiIt7zzs89X+1d2r2z3ujOuf3/1ln4ucGcGqLgUry+W7b1ImQySF4K0c1rm2841wOk1OumXrmQhMrAQtIJZ8T7SJZt9HeE4AaTRhHlITDf3vgFY4NBTiui+PYxNHbwSkRGrSQRAK0UCAUjlK4sUJoiKQZuqUjAGJhEwqXupUCJI6uI4iIBUgUbgxoSWCBEhKpwVJgaZAabNsj0jFBFKB0jWppmLtuuoq71nQg/RDPcwAzAQrzzIvhqveFAkMBrxzu4/BwhOu62I5DHEUXuNoMzgAIvmU+BQpLK7zIEEEkzXDsKQAGIkVdZlFC4qk6Ap/QMgC5sflsAAjgxBZODFIplNJoAZGtQQT45RHWDJYp00Gb7Uz0TnF+6r9Qe48UONk8z8PzLBzHwXYcqmF4gbtiFAopIpQwg46RaCBCoqVhLwUgNCp5i0YTixBNHaFBiTpmrZUoAcjkWUKZ37WNlhoZG2rSqo7lSmQ6i2VnsaiTSqWwgFhppPUueTdp75kC9Xnea+mIy5bMwlEXoEKhEESAQgtp2CahGqnBDNlcJ3VDqhmmioUNQmHpLFpAKGxiYSM02DrCSp6rsJFa4sQSS0Eu7TBcrXG8FDJaqRBFEVEUowEpfj7w4H1iYQCtNUJKKtUq11y1mi9/dD65c14UA1Hy3cZQWT0CL/klJ6E05W8BkAWqQIPJylVozUCDvqPkugpmQcgn12qmL1Baw1kfvvhffoaMLWxhY1lGO5QyuUGYj38zFr5Qc3REDmia0hWBwA99BBaBlpwYGmfmzGbSCppggm+zfhXHSxFqiSfh6LFB5szpIO2YS/JWgKUtQOFrm1AKXGBwOCSVd8hYGiesgGODkKBd0wENxZgJmfp+tYtX397t1JzTgijAth3Sjs1Quco3HnqSEwpiF/oCKIcQao2XThNIjbBgVMEPnnyG/tBQZh2wPBclNFo4VIWgpKAG3Pvjn7D3bD+BJVCua3SThk6UcKgUoGREJBVKTNLne+Dg81CgBkRjIU8Qngqent6p87XpK5l5imu7bH99H/0Vxf6zRV4+ViTz5HFmOyGrZ7Vw6cJ2lIBK7LP70DEOD8WcHqmz/WAv+Wdeo6spzZyOJi5bNoM0NjGaY6dOse9kjWLssuvoAAE7GDjcxMw03HT15QDECYlYmD5LAiR20klJjNEiGrrg5DDlOTrquaZDcl41rMaG0FAKlDl7rhxBYYRO/M6ka/QphUiOGE26q4eXBj3u31OE9mU8s203Z8700jO7HReNrUOE9FiwbDmvngl46KUTFN0OHnxiG3uP9NEyY8ZEFywdMqOtjVKoufehpxmtp3n59dPs2H+CdEs3PrYBhwgfRV2CtsAVPrI+hgwjbOFSAXwzpAnwGgp7POW8mqaqTx4TOKgGRSXU1XjYW4DSXBQ7G6vCQmrb6GkIFndlue76JcSxxC8VyYqQ3/z4tRQ8cISP0AqjEcI9d60jDkMcpUg7kk9+7DrmNkEOCGOzKOSyWT54/TJWLF0Ifg0Zhdxww42su2QR9bqhNImkGtTxQ3BtsOolCnEFa3wQxx+nacoYhTbDtxIYplpGcgK06c2eClE8DS1luFTL6WCdI1cuBJ6FsQSEFmbqgzoWKQZfPsinrlzI7R9awkMP/owTu3azeMMKiCMQNkKY1fTEjqN8ZN1Mfv0T1/Kjf32Wo9t3smjTOup1sC1F7Li4wKljg8xwSvzOVz/L8cNHGTi8E2/lbaRTKQBcoNnNEAagIvjTL32G0wNlRvrP0tOVJQNIHWFjgwYpIngLWPICnyDiKe6sqTiJBnmqKajqiT+ChAhNqCJGhcPn/+/HOTqm8X2fD1+xkj/+pYXkI4iFuVyV6jjNKYaKYOUMpjoCzx8jl3UnAPRlhnoMkQLbhrQwQymOlmjJ5UBpYgnCkVSAkfGAjoJZaWsYCZSW4CsYGjHmZEubRbOAYgJoYx1OJxPtYRYDOSEgEgB1MnZxYQAnFpHGqbACjgWkpgCnEuSkmADw/CJ1OtbFGpQ0ZHPQ3Gwoor0JimXIZsCyQ0OhKjY9EAKbmJwlsSxBrVZDCUEqlcJuyqMA1xFUkyFGAcwouASYFbq3BrveLLL/2BlODozQOzRMtVIjn80wY/YM8mmH2R1tzOhopzWbprsVuhKx0ARYWuIJF+2XwU0jxFQ3w1SqnBy9PbHqxCB8kENAK9OFwBTgGuC9k0YTASf6xvib7/+EFWvWcfu1S5nRDM2A7YKOE/FspUCFaGkjsLC0SvQKQTrlEIURQaipIfC1uVckgI0qeOmNIQ4cPcWeg6c4M1pjqBxAtoUoncVXLTjpVnwNfadHqAz1kglKtGbThJHEslLMnjGH5T0z+MTti5jpmnGlvBxjSTeyNKSVTFbqSXcDgK0S28DC9Kr42gioiNYNbVCIIWUb4eHYYJtlf/L287fGgpTtbuZENea153bw7O69XL5yMTdeuZp1MyDEIogtpAVCekZmApIItEomywbXpqLBF0YRPnAEDp3s5eDx45zoG+LU4Cihdsi1tlMOBU62iUxzM/VqiCM9rFAThXViGbF0wVzm2xFRzWdIpxgLbI6NaA73H2HbG/u56+aNrJzZTlPaWEipNGQdaEtBBkghp/TPUJctaSgyErLglgXjZ0c51HuU9sXttCycAzO9CcFhNZaoZDYaK5dUEqk0MpGZMdBbLBHmmvDa2jgycIJTz7/CMy+/wpUrlvKrH/0AM3JmMlzMwkFjYgTECEbrsP9Mkf0nh3jz5CBHzw7RO1oishxKQUQoXGS2Cyedp4IkSqXQRKhaQC2IyKbSCAviAOJI097WzbXrL2H+fHj6dcWLuw/Re7gfLVKUhsv8j/ueIoNCxjG25xIFVdqyDv/Hv/s11sxIuE5PuDoMBVoNMWgBNXAJaal7dIUziV6NqBzqJTuvGZY0w0wgZ3xsmhgtNCnLIQeo0EIoiQzruAmbuzmLih9Q9GukCgWkSlGJbbYcHGXb//UQGzes5iPXz2dhNpkTbVxPWkpeP3yYex/bxgtH6/jpTiq1ECeTItvcDWisIEQI42CIQh8hLCwBCEGkFSnHRimfSIN2BJbIs/vgGfa9eQwN+I6FwsZK21ixQHptWJagoiGIIlxb4qQ0J6rj/Lfv/pS//t0PknNACRuhBaLBwlOcR+aEVshYYgUFLAF2FFCsjFM82kdmdp725TNhvkBYVoOK8QTMzaU59OZBbE/gxDUcjF4lE8slFhDbNkKkkNrGtR1+/PxuXnplJ9euXcwd165mYRtkLJcRP2DZ4sX86icXUHp4O8/vP0OcSmOl8kTSoeb7RFhTbDDF+ewxrWNiwKwFFhFpIjwQhuukVkgi4+RQFj4SJS1iYa6XIiKdTnHoyBG+98MX+MI9V5MDbDFpt9gNmWYlFCC0MWNix0Vho7BxIptCVRIeqjB8/CCFuV04a5uhABQgjOA/fuoqrlwym8de3kJelkgBqTBFKgJXxglbS0Lb6IdEPsJJcbbm88OXDvHKgRP88uaruW5tKy2Oiw2sarX4409fxVMHinz7sRc5M1alVvZwHS/xDb6TLnC+Ztxb6cRhHlmgLAiFIptLQxAzXhpD2BLPjpjfZBF3FnjwyS3MnDuP26+cTRqj+khABFprUDhIKEPwoz6iIwpLtBpPhohABFgiRFqKul+mpkKipgKFha2kl9vQjfEh2XAyhDP9g1y5oIMDZwO++F9/wIiVBc+ibkvjktc2nhK4OMa96tdwVYCuj7Kqp5PP/PItXDLDzE8FGNdwpAzffXg3e14/iJXOU8IilFMU2mkqB5M63BTgGs2JIR2B1ArfjoitCK1D6uUxupryXNIzjzXLF7F6UZZO13BR3xhEQcCaHpdm0dAbtQFQogwFViXFh3rhmKJJdEFooeIQrWOUjJDS+I0BwigktBQ0WaR7WrDXOjDDTE3gK1yp8KXNT/cO8szuI2x//QA1kaaWasLKNjM0OEZTIUfO0kTVIpYwq3ekJa5jsfna9XzmhnZmAlEElg1DwL33beHJHXsppWcxHEg8z8OS1jsC6NgetXodgLybwQsEQXUc6UZIPU57XvKBtUu4Yf1KFnWZhS2hCWMIJM+xmTT1YMISUSbwXIXBJwaIDoVkKynSOoPjGAVXK4WOo8RLnDxRxYRaUUoFjLUpnDkes+c3IXoc85a00dfORnBmAJ54YS/P7dnPSChRbgspL4MnIqKgThhrAhxq0kMBNnXWzW/lDz66lm4HOtJQSYC896nX+NZzh/DTnfi+j+cZhlJqCkufA2AU6QnzTlWquLUasj5OZ1uKOzZfw6bL2ujMQNeUexrAacCagHC6X0boWGukUWN0FfpfLFE6UCJfkuSVi2M5SAQiAmJl5Bdy0kbWikj6jLpVAjsi7bi09rTC+jTMgNGKxsoJHNu4//eXYh54dhvbd/cxUpHUlCDT1E6AQ6AFoZJorbF0hB1V6MhE/Pt7buXaRYJ0DJ5lvCd/tXWU+557DSklcRy/IwVOBVBUhmkLB7j18pXcc9tldGXAVuBoo2GIRDGZajBYqEn9dKot3AAwQht1ehwYBH0aqv1jjPWOIQLI6BRO5GIriVQm3mApCbECQgK7jnBtdOhScerUZoXMvG0m5EDZIB0YrddRKYsaDidG4eltB3h+90GG6uB7TYTCQwgHrQwYcVgjbUekwyF+/+PXc+3yZpqAcgTjNnzt8X4effJZ3GwLyrISPkroQ1goZaGF0TJStkVYK+GogGYv4n//jbtYMxvaAMqQayiiDWsrwajh/pQXBFBpbU4mxnM0BfYqMBhRHwgoHi8hihJdgpRKkxUp7FBDGBhHgKWIpSS0HGp2jO9VaFvdinO5S+hoZFoQY15VUzGOtNHAriH458e2svXIWcZUCtduBZkiQiCUxolCPGp4eoAv3H0b96xpIoggbcMY8Jf/tINtbxzFdwvEMrFkACFTjFcjcLNk0x5WZYCMqnD7Neu49abFtNrQPwyXtiVKfOKiixtW6zlakZygyXMBnPDGJACKBvJRoiya1ZkQOAXV0xCO1an2jpEOJOnYxtM2xIJYQ2BJlGVir06ng/uhvOlhwcRsLWX6GumQUElwLHzgn1/p57GtuzlyZoxs20xKoUBjI2OBLUJSlk9eFfnCXZu5YXWOmclwdvTDX33nEQ6WILA9LILEr2jjpZsoBQpVHWNOyucLv3YXly40gaQt+8Y59Pp2/ugTN+FFFSw7i9JTHE7nBfCtbRLAKa6qGBOPFcb5PYEvfvK9BAxA7UyF8okKsgjpKI0VCYQOjZz0Y2I7xm+NyF86C5YBafAdsxi0FqBei8C2SZICOFiBr92/jWd3HUDkZuFbWWrSAqVplhLLL5K3q3zpkx/l1kVmlawCD2w7zd8+sZdRK4ckwNIRropIWRbj5QqLOnJ85dM3M7/drOQPPNvLjx95iCuXzeL//NyHyaIn4rPqAiGLt0sROT+yCBR6AtdQa1TagEArsALS67N0bOqk7apO/K46pWyRaqpG3fGxvDSybpEPWxh74TQDD/VTfhW8cWjNAhVIKZtU4i8UCrol/P6nNvLrH7qCXDBIJiri6DqICN8PsdKtDMdZvvPos+wfMuFMR8Om9bOZO6MdrTSxMMq/jgJ0eYRLZ2b5s9+9maXtZrD/8vBhvv/wU5DKEQubagQqSoKkieUk9cVH2956nQZLC2wlcBHJRGgcSyEbUQI7BL8CmTIsBZbXaLmrg/Y7ZyFXeQwUqpRyCpVN44/4NOs2ckNpgp3DDPykhP8zjHczZtIjKSGbhi4Bn75pBV/5zJ00hQM06XGaHI0QgkqgCZwcx0dC7n96L1UgqEHBgU0bLsHTVcIwxE15xL7P4q4cf/m7tzDfMfOugP7hMbx8K5GVws4049qYwLDSycE7OzvfFsAERBrBZj1FMIB5utZGn8hYQAndGhtH3ywoXNXG/LsWIFttIhe8pmbwHTJRhkItg9cfMr67l4FHT8N+zEoQAXWwdIxDjQIRm5bl+ZN/9wlylQFkaQDbiogkRMIlEBme23mYHYeMY1bEsGFphoKo4OiA6vgoc9tzfOk3PkyLhiYRTphesTDZDTEusbAnA0ai4YWOk+PdAiimHDLRgIQ20lQkcQ1tgXIAF0SKukpTJ8+YyFEFKonyTBayC9JU4yK+9gmkRimwlKQQSwp1G3fAZvT5XoJHRuANoAIiUthEuJRJh2Nc2ZPir3/vN1lScLGooqVZIBQ2xSjFN3/4FCXAdWBBFq5a1AH+GB15l9/++K0sbDaOdYHApk4SYifGTnJqpirFDQCT4yLJ8C0UOBHmPPcR5yTtBcroSlXgP339u/zJtx/jp3vOMNAQwp1Qzo1TdMbwvRqxjBBKIwKJV7NpCrI0VzM4J0L8Z47B8RCGYoiM0LAdDxdYO0vye79yJ9m4jKvqOMoo/XEqzbGhIj99ZYCyMgywdl4X7lgfv7J5I1fMk3gTY7AgUaF0bIJlMRhdkcQB3BDEUk0Gzi4GQDUNMpNL3Mgnfgu6U+J8rjTdCoHxuMBP9hT50396hr+7bwv1JmA29NyzjM6rOojbfEqqSKRi4/7wbUSkED6IWhqvmKey5TRqdxEGJPgu4KFjhaPhqnnwh795D52Wj0uIUhHaUYisw8927kRIYzK2uhY3LOjkY+tyNGPc8SZmIQhj12ASBTgqwlYKx7KMmSaMuYolwEk+z2nqAsfFp3a8TUA4JENFNlORbdRlhjrgZ4EWDUstmjd30HpNF+EsxVi6BO0WuCGI0DwvtvGiPIP7xhh+uR+GMhBLhJCgzERdOR9+4yM3QHWIOKqghCKwLU4Mj7H/jMIBetpbuOfay8iHRvWUTGKhsIx0ijU2sYk6WiYG/Ra4LiJo1miTgfVzft4K3LtrGswKm8dY6NdC+q486ZuaOd10mnq+RJyqU0/XKNshVV+TCdvwjnj0PngI3sTonRJ0bJKVrl+VZvPG5YhozIRUrQwnhqrsO3IagDmdTWzasJT0eTYeNBTjhtorNVgTfuVGjkHjuPj27q6+yNaQK2UrZiSlGc5qxlyotIB3aYrZH12C6rEZb6pRylTxPR8vnSJn5cn57RRGm+n/2VE4biZSWBKlQlzgE7ctY0FHBoIaGpvQSnN6aJwAKGQspA2WNak5TLCaSFI14hitNbEyXiXjcdET107CcnHQ/EIABLAlVCyLFyp9HE/SKYWDceXmIfPhObTctpjcggw1xtDUqI6X0BVBNt1Bdsil77lDMAphKLClg6U0izz4zOYrcGojWFLh5ts52jtMmLyTIDqvGiIbuX9ao7Uw+YzC6LlKa6b9aD2NHt+ONn9hAI7XwUfwT1u2ce+be3ipHtEP9AFxCjOaVkhv6Gb25pWUnXHiVIh2BNFAjZxsJVXOcuiJI6h+gQOktcCNFNeubmft/E6i0iiWl6J/rMJ4LXmxZRsfPYlGoifzAhQm40ErhVYGwPfafiEAaqAlZXwQcXYeL56N+OYrx/l/9g2wEzgM1BNKpAtYBO03LCTsDBmL+xCeIkKS87rhsEXxpRIMQFaYJKRmC26/fh0ZVSYK6oyUqgyVTGoHFgSJU6SxuAoxuVBorSfi1tKyzu36u27vGcCpflpBCCJCAaM6SYhMNxOlW+nVGXaO1vnbp7fxzdd2syeGfhsCG1QeWClou2UuhVVN9MpeyqqKCCVzvU6qB0cY2xWYsKuQ2IRcs7KLVfPaqYyM4tge4+WACLPuRPCWHN9G1tW0wScU+F5ypKXk/D/TTZNzj0nwIkgSvyOQdZQM0ICdyJxycZC0jBE2RF6Garabl4cj/vKF1/jOiQFew3hIAGgH+/Y8XbfMoSqLqOoYXlilp9DC2K6TcArwPRwUXcCVl8yjM5tC1yM8xyXC6KXSjicSsmXDB6rN9zhx1CkBQogpTqgpP28D6MXIxXfVFMYTpBJbUouJPAcywJqWZhZZgragQjwyQL1Wx2pr5Yyd4uEDR/j6c9t5arDIIaCSgbEsOJd6zNwwi4o1BnYAlRqtYZrg9RJUwYosMsCqBbPJ2xJPTqojMecJEeupX+UECzeAEm/VBC+6vack88kZMLyiBajkkRqYB3x27XJGFbxxqsKuM6fYXeplXElEuglZaOawjji7/wA7utq4cdkiegDS0LzepSlqgUMV/L4ahVQnw0fHaVuRh4JxAiybmaers5ndr+2f6ItNEsy3eIup4AuzgUcnjPR+LCLvCcBpaTKAEpJYyiQYo0khmCugE1iwIMv6Bcs4FC/jjaEBXjlwjJqlGZc2VS/LK8Oj7H78Ca5ZPIc7FixnSRvkNrZAVSBKCgLIqRzlfb3kZs1Ae+Cl4ZIlPRzavw8LHwcPqfUkgI1+YUSNETckG3w00rLeA+2Z9nOysLFOGhlVAoWXziCkR6itJINLUIvrCOVTcEz+3Xzgegs+29XJf9p0BZ9aNJuVtqYFRYDDSL6DR8+M8fUDB9kBjDcDG5qx5jVRVlU828Xvr8MpsCIDyJrls0k5IR3NJsPLidXkopDEvBSGtcdi6B8ZwnWNX8aeAqBGmCPREadZrhe2Yt8LBUYIk89gfositLQIlKCGAUxpC5nsy7DR2FPmuw2Y1d3Bqu4OXilGvNzbx4GBYeJUG4eGStx3YA/ZZatY2w3OhiYYiYh8H9eXBMeHcRe1GZYVUMhZZFMgVR0ryRkAqNQVtpB4nolCaAu8dIbxaoxQhoUbbs+flxJ/Tgqc9JdJjMxx3RRKC4aGixwfMO52YTtYWBBU8KlRIyQAIm0CeVQjekK4vcnm8z2z+d1Va1hRk+TKmr2nR/nOvv0c9YDFkFneRIkxZKwZOdYHoYmJtOShZ1YnGQcsgol+RYC2JbGCYmhSRF7ec4paFJDOZAjCkCAMCIEgmNzXp8S7W1t/TgqcdJhZgKsC4nKV9vYOzg4N8tW/+ns2rr2EWzeu4+qeNCiXkBiFxNbgKHAtcDI2xJCtGTDaCjB/0yJeOhPy+BvbOXzkGA9Gii+tWUl6nU39cJ1MJUM0Xod+n0zBo8mDRXNbgcBExIWFFoYLbBvGBRztrXDfU4/zwoHTyOZFaOWTFxXyoo4HWLadUOG7p6f3wMI2CqOqrF3UzWuHtlPuD8kUWqh7GR7aO8CTex/k5jWL+PXbr2BR1qKmkpS3xiMiE5UTaeO7a6g+bbMclrdcxtOvvcruUwPc3+lzd95jxqpZ1F4eJkUKNVZB+h5ercLKBZ2gQQkPKS1qGgaA4+Pw3LYDPPX8y4zH0DJzNWNjFcT4GZY6Ja6Z32S2TSTd0WBy/85xHk9r55wX77XoRCWG0IJtxyJ+9Nwr7DvWT0l7iEIrfr2KGO+jWde4bu1ifunma5jXCTqAThd8v4awTK5gnUnjoZFy1wvcu+Mw9ZEiX960nhklqNx3mrG+YVLr87TdvICztXHKVsS8ptaJZPMy8N2nD/Lkq3vpHanjZvJIS1IaHWJGS5YbVy/kN2+8lHkZ8666H+F5NkZLbGREvw2I7x1APeE3tHEooQkw2fO7j5Z5+LmdvHK0QlVnEFKT9iyC8SEKbszmazdw28Z5LMlBVhuHp2RyVxDJZzmxGOrA1h0nKMgad61bBs/A8L5jlHNV5n10BUEeypaRcTXg2X017n/8OU72jWBnCriZPCN9Z+lIRWxaPY9P3XIVC1pcMkCsQcXGqWDL6Qr4W5j5Aij93BQYJfRiA3UVoGWaKBlEBLxyDH685RAv7j1AaDm42TSuoxkfPsXsvMNHNq7kurUrWNguqMaQtqZvg42AYT8m61mM1uCFHdvZvPJyZtTh5MNHcHMW3Vf1QA+clrBt/wgPbNnOS0cGcfLtZKVE+zWkCrhkXjd3fGAtVywtMMsC5Y+T8goTYzmf9/kXDmBDbjT28U7NZAKzuAzV4cXDZX66Yx/bD55Cp9IgJXHoUx8do6spw62bruCem+YxG0N5KTRKhQTSgWTbF8CJgRJeXbIglaXv1SEqp4ZYePMy/BnwF/e/wKMv7cDPtVHLt+FIF2u4n8UdGe6+aSOb13WaHUlMqiwOjaShi2y/aAAnXqAx2yJUADJF3ZYMAc/sHOWxrdvZe/AwblMHMt1BqVTCiyss6sxy/fql3LhhKbOaGpuzYyysaRMUVyEbw8DrRYr7T7P4wys448Dv/e0DjAqbvmqVcqTIO4Jfu+FKPnbDAjots0ChYrSQ+AmfurxLHe4XB2BD5E/OZ6QVMQqEjZuI5QAYqMPOfX384KmXeLUvQOZasVWAqpfwVI2eWZ3cuvkG1l+SIidjWqyQAh4ugkoNZGyysurHYg4/9xorb76MXQ585VuP0zdeJF9w2bRhBR+6ejE9WcjFkLUBVTfOQctFyUkT+f0A8OdWY6Y7taZ/s4Q9md2p68RRhAotmrXDbeu7uWztR7j/xVGefHk3h46epKWtHS3S9NYkf/3PD7FgTgsfv+1S1i3sIBImwhY4cORQkcsWN5HqtsCNoAC1YRjqO8x1113L5utWsbHbUFcajGtfAjKx2sU5q+z70N6zGjN9as5nEBkjUmuBVkamhYlH5PQ4PL/zCM+8sosDvcMEbgFRaKFcKUNtlKUL5nHrdZtpbYIHH3iZ0qmDfOM/fJIeB/Y9/QIrbria7SdPctovc/kVl+ABOQ2piMn9gY3+WRgvwnkyr95Lex8AvLhmgjnJq7Qk9COUbRO40FeHLXv6ePDprfRXAnzp4aUKDAyN4VlpCoVmamWfeSnFX3zmZi7thP3PvMglm6+iHkf4nkRJiQNkoyTN5VxX0bmgvU8g/kKKTlyoNfxvURybEJplFqEZKbh1QzcbL72bx5/dyfO7DnKqNEZz2sVLZ4n8Gs0pB+WPk0vKcjR1dkIElhCoKMZ2DcmJ94s3L3ZM/5YU2GiGkwQxEMQQaLOXEQxhjADffux1fvbqm4yMVsilMtihz60bL+Nzdy5HDmnikQFa5nUlwi4JKAGpxFx8R4p7nyjw3wxAmBoRM/nSjWZcE41AtyIQDiXgTAkefvQZwlqNX/7gzcwqOLRmgEqSNWZjSFiawhGNZ733WNvFt/+PANQTAJpoHmafsCbJhLcJpUMIjNYh40DLVIppJMI3NCdpMsUatrSc8qdfdPs3BRBMDo5GEU8plieRWNpUdGskugdCm+puJIqwXzNLt0z2I0yG0ybITolJe/qdMtQuHtypL3prex8XkekvilSSajHl/NS8Q2P6yQkfnGE7iTal3NDapGNkG4/30uZZk3VImNylOX1wb92M0MD5YhPSpvvvzV3nB/DCKb7nxgA0EIP2JyknQlNPXhDHPo2BhJik9Hoc0oArJk64TRJrRTwhwCwkk3vdQm3YUcnzdVhMViSSoUlSdATI0ASKMBRRjfXEwBrDkEn6rooCVKjRDTFwbjJqFEPgg052pievm7xscvpBvw0LJzImavS3cY8FQRBhu9IAhdkKkUocUgHuJAVoU6tKStBJIZyGCTUQ1nGc1MRmvpQCFZnKHTLZFqY0EBlQa9K4vgqYOAi6BtoH7KR8gEBbKZLqJRPoaC1BaTKWQMUBSA9XmGCTNZUgJcQ+iDhEOiLZ82W4BM4XAk1iyucDsAHA1PoItm+4JRAmJ7lROqQxkYk2QR0IFXhy0uPRCCk2vCA+Co0pW6I0pITJJE0LM1FKxcTSR0uPKIl0lM3ckdOadFQx4sGymFyKTVpHyKSxobWRi40QcSOjNkjeZWkzcVgwVgfXNX3RMWi7cY9GanUOgJOM+7YycOotdQ3j5ZCX3zzC3AXzmdvtsWv3ISLpcumqeQjgjcPHKfmKOXPmMLPg0F+LOTlQZGSszNyZXczp8IiB40Nl9pzq5ZIVS+lyoa8Mbxw6TU9XJ0tbXdK2RkqP/sDnYL/PmWKISmdpznksKFh0p3O4Gvbu2UssbFasXMZIGU73DzNSrAAQ1qrM7O5i7rwWUjYcH9UcPHqEcmWctpYWVi2aT0c62XAN7DpV5ezgCFkrZv6cLubONNzhJllKVrI8NRIHGhCeF0BTBFEhVUQsFbHwUK5g5xtD/Pm9P+aqTZv47Y9fxt//6FkqgeaP5n+e2Tn4/lM72L5rP//hy3+Al3c4PFDjK//9fsaKJX711o381l1XUVTwvad28Y+PPskVV2zgz794Bwf6a3zlG49x160380d39ICyCYBxneGP/+Ff8J0mimNlpAppzcKX//3nWdQNf/fQiwwXS3z1z5axY98gf//tfyJTaKFQKFCv1OhqzfHnX/4oO85ovvo336Iax8xuT9N/4hjzOrr46h9+niYPvvadrTz32htEIk0URzR7gt/55B1cs7qVHJB7GwP6/BQolKlqY2kkMZUgBjdLXaYoWQWKTjNVoCYzVKWgahnWrco8VStHXWbwBGzbdYC6zDBz2RK27T/FdTdfxdwckG6mefYSDveV+dGW0yxbPpuyXaAuc0ZsNPL5NNRljkDk+JM/vIdXX+njwZ8+xo9fepNPf2QpFauZirSpWFB3W6m7rVx25Y388l1zGR+DtqzZhvL1f/w+1Ujwmc99jsuXwpYtpwjKJSIPth6GJ3fsZemK1XzyN67m4BH49j/cywM/eZZVS38Jz21gZ4TZuSv8BVjY7ONN2ykcjGyoY2prhVKazSoTj5meHquRxEIwBDy35Xmu33gj7XOX8M/3/ZDth2Pa11qkqCGjGqmmWTz8wi7O+i6WjvB01ehvGlwFqdjsLfFUxOUt0HN5N1tfmcO+o8OJ7J3c61Gu1rAcj/0H3uTP/2IfBMNsvHwd111/CWOVMqtnt3HjUnjjUExYruJmCgxW4dBAhXIYc93a+axxYd5y2LlgBocPHWCsBh3eZNVNJsb4DhSoMHnJPjDs1zjeN8qceTOpy4xJZZuYAUUsLQJpHKaBdAFTBPbVQzGD1ZAo9CEOqCvY/vp+7li7Ct/3sQTcfNONbN26lRe3vYylTRXfqZ2wFKBthLIJMYtCuVonk86YjicFZ7UAJ50jUIrumTO5ZuMKauOjLJ7fgopARCEiCskCA30DvPba6xw+cYxC+5ewbZs4johik9dY1RCHvtGWEpswBOxEmZFT9q5PpcRz6A9sKfCAn+04wpf+9Bt87ZEj7DpdROPSlsvhAi1tBfpGx9hxEB5/E44MjJDPOcydC4+/uo+weRZ7jx7j4YfuJ+Npjh87QG8MTlMbw6MjLF2U4iObLsepDlPIZVFIyqFxMCgJuODYaao4bDkJ//jsIfrH+pk/u5kMkPVspBDUQqPqCMuhqZBj7hxon9VCPYCuDFy6ZDFvnBrlB1tLLF8/gyuuvhYHgRX4XL7co6uliS2vHubpY/D8HnjzRC9L58+iOTU1zCoTbMJEIdMXpkBQ2EIx5odcdulKLtm2h20vbKESaJbN6OBDV3aSAz56w1XUqs/yw299jThWdDenufvDm2Ecjux5lXmdXfzBb91GIQP/+sjrPPHTn3DglaNkCMiLOm5Fccf6Jo5sb+bFfWfw4gqeBEKF9CSOAKc2gq1s/vvffJO6X+a6Dev4wj0ryAGy3IfjBzS7kI6rOLURDr/yLF/58RC4GVpSDt/8z7/FR2/YyOm+YR558Hs88oOAlFRcvryH1bPydOfh4zd/gB89/ix/9Wc7cTN5Fs/p5JN3fZhOx8BkQBJMxgwn23n0wIbGrPDDmNhJUQH2HRpEC0lXRxsLmiblwnhVMzA0SrVaobW5wNzuJsbqcKy3SGd3E13pxEUVQn/vODPyFlbK5c3BUebO7aQDGC4H9BUVLdkUc606bt5YKFVfc2y4TilWZNMuwoZcs0MKU3FteGCI/opi9vxONNA7qMhaGtezKNYhDiNWdpvwwlgdTg8UGa2GZD2bDfObzS6rOqRSpjrwsdP9KOnQM6eVnAcEkHYg8zZG9QUAlNSBShCTdq0Ji6eR8dCouTdeg6b0dDlQjY1+G/oQx9CUMfvp/MjUMUsp8JUmtE3QPA/4UYxtm1SzDIYCccxTiyE4DtQCTdY1OS8uYKsYT1qMJGWUG1X/EouZKpO18mHSQT2GUbvTQBgpHNtYVFai/JuyoebTTyZK0agTk9jUU/yN57VEguRFNSb1/IZFca6vMpsMqAF9o+Necn6USWumYavGyXVR8uwoAJkU3m1YJIM+ZDxzfTrpUwoYq0A6PZll6k8BJ8Z0OpWUWwmT92kFUQhNHhNWzQxguA4iZfrqxSDRKEvQVwGZeDEKU4BsvMdJDvQFZGAIPLrtNFtefR0n9nFlTCqV4sbNN/PSzj0cOXYSx8ti6YhmK+Kzn76DVAq+/o0fc6ZYZ/nCHn7v7vVsffUYP3h2N6Fl6u46OuDuO28jiAL+4V/v4/IrruDqS1fwg+/eT7Ue87/9/sd4efsYP33yCT72iTvZsf0FSgNnTS1VO8tV69Zy56YluBJOluH7Dz/DgaOnyeTyuFLT7Fl88TN3cmZI8df3PkotjLjhshVcd81Svv6tRxgaryG8DK5UrF86l82b1/IP391GeWSAz995NUvmdFADHntmO68ePmUKAZUH6W7O8B9/51MTzloxhYzs86U1KKB/vMquAydYMLMFopDjJ9+kc9nlHC4KXjg0yNzZFn65SL0yxvpBmDcPXu0v0jswht1coAqcGh9nx8k+2nqWoutlhs6ewtq2g3XrL2XX0V5u+kgPugD7TvQR+op9J+Gp3Sc4G6RId3nsePMQIorJ5VoYH/E5+/hWPrh+CdkCuFk4UwwZqMY0u1ArjpKa00nKhRMDwxwfqTE0WuSyFTUcB/aeHacS23S0WJRHBjh5/Ahrrl7L68f7saMqc+d0AFBXcLJ/hAPHB+ieORtHpcim8slGH7C0b0ja8kDI81OgBo4dP4adSnPHPR+nKQ8H9p2gtb2Tg0++xE2338UnPtzOvd/fz8ED+8nNgEee6+f00DiF1g6qsaYIHDw7iNPUxhd//3rOnoGv/ZfvsHj1Ok6cHSCXLbB0WZZjp2HEt8hlm9n++in6hoa5YuNV9A1B30iFj9xxO7fcvIQdO326XYGXNs6AioZDZ4bJt83gzjs+yCVzjdI7BDz8/C7GY4vQ9iDTwrEinCn63HjrLdxxazuHdtWZWbAZG4e+oVGu2bBmQkzVtVFjZvYs45ZbrmfNHJiXM+LIUqFxc4lELogp/2hIM+lDs4BVi+aS9Vz+7t5H+P7DO9i4YR6iOshY30mWL2ynAJw9epQZLe2oKmx7ZitXrr2MjCVpzrUSAfuPDiK05MH7T/GjB14i5aSY3Zli8NQJls/uYp4NW7ftReQ7SbXPZtfePVQHD7K8O8fpI31kU83Efp0//eo3+clj91OpjmI7Jv5x6BSMVAP2HzrKN//+mxN1+5/cq9l2bJw1l2/E9dL46U5+9noRJ50jjEK++mc/4d7v3cfRI28ycLaXoF5j1arV+IlsPHImYmC8yuGTp7n33u8hA2gSYCq1+kk6mTMR/pugwDiKiLTGc1yOnRokiiI+9elf4c0hzcMP3Mejj2lStqC9vY2FPSbgUx4vsXrFKvbtK1EsFoHEDEtneP0MlGOHjOuw56Wt5PM5fvVjHwMLXt+9h5uvvZIQOH78JHPnL6ajo4M9L/+M1pzDnO40L766h/b2OVx/02r6B/vYu2sn3a1Zytr4A1/aeZAAh+tv+iCLO/PIxH329PY9VO1mipUqkYSxUHHixGlS+Rybrp9BEAVseeIR2mfO49TJU1iZPN09DqMJ5+0+2ktNpLls4yZWLphJNtsoDaiSgLM9LXY6UYTWth00EGjFjl2v860fPMusdUMEXhupfDMdcxby8ovbqESCr3/jRUpjvfiENHW18PjTT+ETcfTscYbHR1idy7H3eI3BYpXLl3dyZOwUt151BR9aCz/cEXOmGLJs5RoGx+HUyeNsXrmGru5OthVHWbqom2wezg4OMVSu87f/uI36yBgrF8zl0sU5pIbRAE729hFhcfLsIKePvokXLWLGnB72v3kEmWnhtb07qVVHCWTAUHmYkdoo/+M7zzE2NkrP8mXkZ+XY8uMTRF4rf/xfn6I5GuKmTR/gtWPDlMlwoneIgdPHUX0FvvChtXjC5VwluqHeTLRYm6z2dasvYfPpcY6PDSOCKh+7aSN3Xd1Cq1xHbsdehsfPknJ87v6VuykWi7RbPp/97V/H9my++y//QsofIR4JuWLZHD73sWt54tEaZ/e/SHnjQqLhU6xbMoflcyz27z1FT5PFrVfMQml4scXhihXzWVCADcu6OX56iPHxIRbPaOdzd15DJ1DWScnpaj9r5zYT+wPoepGCPY99O7ayrqeVW+7cxMhQhaeeeIxl7WlaV/Swdfgk2XCUzhaXu3/pJgo22PUSizq7UFFANFqhvZCmyQpZ0p1H1vuhNkp382XnuE+nb/KaVoi7gaum4a5nwg3fSAdrRDmmNjlxp2l6yvdzje2GTtiI3Tb+x0ije40uNmzQhi431eMdMxkaIfnuJv1u6H/ne3ejTe4NmfRge0z3nmuMSEglz57spTtt/OcFcOr2rck2ER1h6gxMu/ScU0kcatqfGxtzGp41hZyMO0ycN4epxuZORIaUnMxASGPqnxokGgOUJlMfeyI8et60NDF1bMl0NTxBSWHbxm3WhI0DJOVSphoTbwHwQkHid3ThXKBN/d9ejRDuVADP9+QYu1EuwcQskh7Hcnpip8Vbp7lBAI26D+eOpzHwaWPQTFkYDI/E53GevuNz3q5NjXJO7bQ65zj3NzHlmJ4xcKFXy4n3TbxhCgpme5mayD9sXDuZpC6nnT/fOKZz0PlMient3CummrL/LyCuUUMsL29TAAAAAElFTkSuQmCC",
    "Lone Peak": "data:image/png;base64,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",
    "Maple Mountain": "data:image/png;base64,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",
    "Northridge": "data:image/png;base64,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"
  };

  function initials(name) {
    return name.split(/\s+/).map(function (w) { return w[0]; }).join('').slice(0, 3).toUpperCase();
  }

  function buildTeamGridInto(container) {
    if (!container) return;
    container.innerHTML = '';
    TEAMS.forEach(function (team, i) {
      var badge = document.createElement('button');
      badge.type = 'button';
      badge.className = 'team-badge' + (teamFilter === team ? ' active' : '');
      var mono;
      if (TEAM_LOGOS[team]) {
        mono = document.createElement('img');
        mono.className = 'tb-mono tb-logo-img';
        mono.src = TEAM_LOGOS[team];
        mono.alt = team + ' logo';
      } else {
        mono = document.createElement('span');
        mono.className = 'tb-mono';
        mono.style.background = BADGE_COLORS[i % BADGE_COLORS.length];
        mono.textContent = initials(team);
      }
      var label = document.createElement('span');
      label.className = 'tb-name';
      label.textContent = team;
      badge.appendChild(mono);
      badge.appendChild(label);
      badge.addEventListener('click', function () {
        teamFilter = (teamFilter === team) ? null : team;
        var hintOn = teamFilter ? ('Showing ' + teamFilter + ' \u2014 tap again to clear') : null;
        els.teamsFilterHint.textContent = hintOn || 'Tap a team to filter the games below';
        els.teamsFilterHintCal.textContent = hintOn || 'Tap a team to filter the events below';
        renderTeamGrid();
        render();
      });
      container.appendChild(badge);
    });
  }

  function renderTeamGrid() {
    buildTeamGridInto(els.teamGrid);
    buildTeamGridInto(els.teamGridCalendar);
  }

  function renderGame(g) {
    var card = document.createElement('div');
    card.className = 'game';

    var isFinal = g.status === 'final';
    var aWins = isFinal && g.scoreA > g.scoreB;
    var bWins = isFinal && g.scoreB > g.scoreA;

    var meta = document.createElement('div');
    meta.className = 'meta-row';
    meta.innerHTML =
      '<span>' + g.dateLabel + '</span>' +
      '<span class="status ' + (isFinal ? 'final' : 'scheduled') + '">' +
        (isFinal ? 'FINAL' : 'SCHEDULED') + '</span>';
    card.appendChild(meta);

    var matchup = document.createElement('div');
    matchup.className = 'matchup';

    matchup.appendChild(teamRow(g.teamA, isFinal ? g.scoreA : null, aWins, bWins));
    matchup.appendChild(teamRow(g.teamB, isFinal ? g.scoreB : null, bWins, aWins));

    card.appendChild(matchup);

    var hasStats = isFinal && ((g.statsA && g.statsA.length) || (g.statsB && g.statsB.length));
    if (hasStats) {
      var statBlock = renderStatBlock(g);
      statBlock.style.display = 'none';
      var statToggle = document.createElement('button');
      statToggle.className = 'edit-link stats-toggle-link';
      statToggle.textContent = 'View player stats';
      statToggle.addEventListener('click', function () {
        var open = statBlock.style.display !== 'none';
        statBlock.style.display = open ? 'none' : '';
        statToggle.textContent = open ? 'View player stats' : 'Hide player stats';
      });
      var toggleWrap = document.createElement('div');
      toggleWrap.className = 'game-actions';
      toggleWrap.appendChild(statToggle);
      card.appendChild(toggleWrap);
      card.appendChild(statBlock);
    }

    if (session && (session.team === g.teamA || session.team === g.teamB)) {
      var actions = document.createElement('div');
      actions.className = 'game-actions';
      var link = document.createElement('button');
      link.className = 'edit-link';
      link.textContent = isFinal ? 'Edit result' : 'Post final score';
      link.addEventListener('click', function () { openResultModal(g); });
      actions.appendChild(link);
      card.appendChild(actions);
    }

    if (adminSession) {
      var adminActions = document.createElement('div');
      adminActions.className = 'game-actions';
      var adminLink = document.createElement('button');
      adminLink.className = 'edit-link admin-edit-link';
      adminLink.textContent = isFinal ? 'Admin: Edit score' : 'Admin: Enter final score';
      adminLink.addEventListener('click', function () { openAdminScoreModal(g); });
      adminActions.appendChild(adminLink);
      card.appendChild(adminActions);
    }

    return card;
  }

  function teamRow(name, score, isWinner, otherWon) {
    var row = document.createElement('div');
    row.className = 'team-row ' + (score === null ? 'tbd' : (isWinner ? 'winner' : 'loser'));

    var logoHtml;
    if (TEAM_LOGOS[name]) {
      logoHtml = '<img class="trow-logo" src="' + TEAM_LOGOS[name] + '" alt="">';
    } else {
      var idx = TEAMS.indexOf(name);
      var bg = BADGE_COLORS[(idx > -1 ? idx : 0) % BADGE_COLORS.length];
      logoHtml = '<span class="trow-logo trow-logo-fallback" style="background:' + bg + '">' + escapeHtml(initials(name)) + '</span>';
    }

    var nameSpan = '<span class="team-name-wrap">' + logoHtml + '<span class="team-name">' + escapeHtml(name) + '</span></span>';
    var scoreSpan = '<span class="score">' + (score === null ? 'TBD' : score) + '</span>';
    row.innerHTML = nameSpan + scoreSpan;
    return row;
  }

  function renderStatBlock(g) {
    var block = document.createElement('div');
    block.className = 'stat-block';

    if (g.statsA && g.statsA.length) {
      block.appendChild(statGroup(g.teamA, g.statsA));
    }
    if (g.statsB && g.statsB.length) {
      block.appendChild(statGroup(g.teamB, g.statsB));
    }
    return block;
  }

  function statGroup(teamName, players) {
    var wrap = document.createElement('div');
    wrap.style.marginBottom = '8px';
    var title = document.createElement('div');
    title.className = 'stat-block-title';
    title.textContent = teamName;
    wrap.appendChild(title);
    players.forEach(function (p) {
      var row = document.createElement('div');
      row.className = 'stat-player';
      var nameHtml = escapeHtml(p.name || 'Player') +
        (p.position ? ' <span class="sp-pos">' + escapeHtml(p.position.toUpperCase()) + '</span>' : '');
      row.innerHTML =
        '<span class="sp-name">' + nameHtml + '</span>' +
        '<span class="sp-line">' + escapeHtml(formatPlayerLine(p)) + '</span>';
      wrap.appendChild(row);
    });
    return wrap;
  }

  function formatPlayerLine(p) {
    var parts = [];
    STAT_FIELD_DEFS.forEach(function (f) {
      if (p[f.key]) parts.push(p[f.key] + ' ' + f.friendly);
    });
    return parts.length ? parts.join(' · ') : '—';
  }

  function escapeHtml(s) {
    var div = document.createElement('div');
    div.textContent = s;
    return div.innerHTML;
  }

  // ---------- Coach login ----------
  els.coachBtn.addEventListener('click', function () {
    if (session) {
      session = null;
      els.coachBtn.textContent = 'Coach Login';
      els.coachBtn.classList.remove('active');
      els.tabMyTeamBtn.style.display = 'none';
      if (currentTab === 'myteam') switchTab('scoreboard');
      showToast('Logged out');
      render();
      return;
    }
    els.loginOverlay.classList.add('open');
  });

  els.loginClose.addEventListener('click', function () {
    els.loginOverlay.classList.remove('open');
  });

  els.loginSubmit.addEventListener('click', function () {
    var team = els.teamSelect.value;
    var pass = els.passInput.value.trim().toLowerCase();
    var expected = 'coach' + team.toLowerCase().replace(/\s+/g, '');
    if (pass !== expected) {
      showToast('Incorrect passcode');
      return;
    }
    session = { team: team };
    els.coachBtn.textContent = team + ' ✓';
    els.coachBtn.classList.add('active');
    els.loginOverlay.classList.remove('open');
    els.passInput.value = '';
    els.tabMyTeamBtn.style.display = '';
    els.myTeamTitle.textContent = 'My Team — ' + team;
    loadRoster(team);
    switchTab('scoreboard');
    showToast('Logged in as ' + team);
    render();
  });

  // ---------- Admin login ----------
  els.adminBtn.addEventListener('click', function () {
    if (adminSession) {
      adminSession = false;
      els.adminBtn.textContent = 'Admin';
      els.adminBtn.classList.remove('active');
      els.tabAdminBtn.style.display = 'none';
      if (currentTab === 'admin') switchTab('scoreboard');
      showToast('Admin logged out');
      render();
      return;
    }
    els.adminLoginOverlay.classList.add('open');
  });

  els.adminLoginClose.addEventListener('click', function () {
    els.adminLoginOverlay.classList.remove('open');
  });

  els.adminLoginSubmit.addEventListener('click', function () {
    var pass = els.adminPassInput.value.trim();
    if (pass !== 'harvestright') {
      showToast('Incorrect passcode');
      return;
    }
    adminSession = true;
    els.adminBtn.textContent = 'Admin ✓';
    els.adminBtn.classList.add('active');
    els.adminLoginOverlay.classList.remove('open');
    els.adminPassInput.value = '';
    els.tabAdminBtn.style.display = '';
    switchTab('admin');
    showToast('Admin logged in');
    render();
  });

  // ---------- Admin: quick score entry (from a scoreboard card) ----------
  var adminScoreGameId = null;

  function openAdminScoreModal(g) {
    adminScoreGameId = g.id;
    els.adminScoreSub.textContent = g.teamA + ' vs ' + g.teamB + ' — Week ' + g.week;
    els.adminScoreALabel.textContent = g.teamA + ' score';
    els.adminScoreBLabel.textContent = g.teamB + ' score';
    els.adminScoreModalA.value = (g.status === 'final' && typeof g.scoreA === 'number') ? g.scoreA : '';
    els.adminScoreModalB.value = (g.status === 'final' && typeof g.scoreB === 'number') ? g.scoreB : '';
    els.adminScoreOverlay.classList.add('open');
  }

  function closeAdminScoreModal() {
    els.adminScoreOverlay.classList.remove('open');
    adminScoreGameId = null;
  }
  els.adminScoreClose.addEventListener('click', closeAdminScoreModal);
  els.adminScoreCancel.addEventListener('click', closeAdminScoreModal);

  els.adminScoreSubmit.addEventListener('click', function () {
    var g = games[adminScoreGameId];
    if (!g) return;
    var sa = parseInt(els.adminScoreModalA.value, 10);
    var sb = parseInt(els.adminScoreModalB.value, 10);
    if (isNaN(sa) || isNaN(sb)) {
      showToast('Enter both scores');
      return;
    }
    g.status = 'final';
    g.scoreA = sa;
    g.scoreB = sb;
    persistGame(g);
    closeAdminScoreModal();
    showToast('Score saved');
    render();
    renderTeamGrid();
  });

  // ---------- Site-wide tabs (mirrors the real site's nav) ----------
  var currentTab = 'scoreboard';
  function switchTab(tab) {
    currentTab = tab;
    els.siteTabs.querySelectorAll('.site-tab').forEach(function (btn) {
      btn.classList.toggle('active', btn.dataset.tab === tab);
    });
    document.querySelectorAll('.tab-panel').forEach(function (panel) {
      panel.classList.toggle('active', panel.dataset.panel === tab);
    });
    if (tab === 'myteam' && session) {
      renderRosterRows(rosters[slugify(session.team)]);
    }
    if (tab === 'admin' && adminSession) {
      renderAdminList();
    }
    if (tab === 'standings') {
      showStandingsList();
    }
  }
  els.siteTabs.querySelectorAll('.site-tab').forEach(function (btn) {
    btn.addEventListener('click', function () { switchTab(btn.dataset.tab); });
  });

  // ---------- Roster (My Team) ----------
  function slugify(team) {
    return team.toLowerCase().replace(/[^a-z0-9]+/g, '-').replace(/(^-|-$)/g, '');
  }

  function renderRosterRows(players) {
    els.rosterRows.innerHTML = '';
    var list = players && players.length ? players : [{}];
    list.forEach(function (p) { addRosterRow(p); });
  }

  function addRosterRow(data) {
    var frag = els.rosterRowTemplate.content.cloneNode(true);
    var row = frag.querySelector('.roster-row');
    if (data) {
      row.querySelector('.r-name').value = data.name || '';
      row.querySelector('.r-position').value = data.position || '';
      row.querySelector('.r-number').value = data.number || '';
    }
    row.querySelector('.remove-player-btn').addEventListener('click', function () { row.remove(); });
    els.rosterRows.appendChild(row);
  }
  els.addRosterPlayerBtn.addEventListener('click', function () { addRosterRow(); });

  function collectRosterRows() {
    var rows = els.rosterRows.querySelectorAll('.roster-row');
    var players = [];
    rows.forEach(function (row) {
      var name = row.querySelector('.r-name').value.trim();
      if (!name) return;
      players.push({
        name: name,
        position: row.querySelector('.r-position').value.trim(),
        number: row.querySelector('.r-number').value.trim()
      });
    });
    return players;
  }

  els.saveRosterBtn.addEventListener('click', function () {
    if (!session) return;
    var players = collectRosterRows();
    saveRoster(session.team, players);
  });

  function loadRoster(team) {
    var slug = slugify(team);
    // 1) paint instantly from this browser's local copy, if any
    try {
      var local = localStorage.getItem('uhsgfa_roster_' + slug);
      if (local) rosters[slug] = JSON.parse(local);
    } catch (e) { /* ignore */ }
    renderRosterQuickAdd();

    // 2) reconcile with shared storage, if available, so the roster
    //    follows the coach across devices/sessions rather than just this browser
    if (db) {
      try {
        db.doc('rosters/' + slug).get().then(function (doc) {
          if (doc && doc.data && doc.data.players) {
            rosters[slug] = doc.data.players;
            renderRosterQuickAdd();
            if (els.myTeamPanel.classList.contains('active')) renderRosterRows(rosters[slug]);
          }
        }).catch(function () { /* no saved roster yet, or read unavailable */ });
      } catch (e) { /* ignore */ }
    }
  }

  function saveRoster(team, players) {
    var slug = slugify(team);
    rosters[slug] = players;
    try { localStorage.setItem('uhsgfa_roster_' + slug, JSON.stringify(players)); } catch (e) { /* ignore */ }

    if (db) {
      try {
        db.doc('rosters/' + slug).set({ team: team, players: players }).then(function () {
          els.rosterStatus.textContent = 'Roster saved — synced across devices.';
        }).catch(function () {
          els.rosterStatus.textContent = 'Roster saved to this browser only (sync unavailable).';
        });
      } catch (e) {
        els.rosterStatus.textContent = 'Roster saved to this browser only.';
      }
    } else {
      els.rosterStatus.textContent = 'Roster saved to this browser only.';
    }
    renderRosterQuickAdd();
    showToast('Roster saved');
  }

  function renderRosterQuickAdd() {
    if (!session) { els.rosterQuickAdd.style.display = 'none'; return; }
    var players = rosters[slugify(session.team)] || [];
    els.rosterChips.innerHTML = '';
    if (!players.length) { els.rosterQuickAdd.style.display = 'none'; return; }

    els.rosterQuickAdd.style.display = '';
    var allBtn = document.createElement('button');
    allBtn.type = 'button';
    allBtn.className = 'rqa-all';
    allBtn.textContent = '+ Add whole roster';
    allBtn.addEventListener('click', function () {
      players.forEach(function (p) { addPlayerRow(p); });
      markChipsAdded();
    });
    els.rosterChips.appendChild(allBtn);

    players.forEach(function (p) {
      var chip = document.createElement('button');
      chip.type = 'button';
      chip.className = 'rqa-chip';
      var label = p.number ? ('#' + p.number + ' ' + p.name) : p.name;
      if (p.position) label += ' — ' + p.position.toUpperCase();
      chip.textContent = label;
      chip.dataset.name = p.name;
      chip.addEventListener('click', function () {
        addPlayerRow(p);
        chip.classList.add('added');
      });
      els.rosterChips.appendChild(chip);
    });
  }

  function markChipsAdded() {
    els.rosterChips.querySelectorAll('.rqa-chip').forEach(function (c) { c.classList.add('added'); });
  }

  // ---------- Post / edit result ----------
  function openResultModal(g) {
    activeGameId = g.id;
    var isSelfA = session.team === g.teamA;
    var oppTeam = isSelfA ? g.teamB : g.teamA;
    els.resultTitle.textContent = 'Post Result';
    els.resultSub.textContent = session.team + ' vs ' + oppTeam + ' — Week ' + g.week;
    els.scoreFor.value = g.status === 'final' ? (isSelfA ? g.scoreA : g.scoreB) : '';
    els.scoreAgainst.value = g.status === 'final' ? (isSelfA ? g.scoreB : g.scoreA) : '';

    els.playerRows.innerHTML = '';
    var existing = (isSelfA ? g.statsA : g.statsB) || [];
    if (existing.length) {
      existing.forEach(function (p) { addPlayerRow(p); });
    } else {
      addPlayerRow(); // start with one blank row for convenience
    }
    renderRosterQuickAdd();

    els.resultOverlay.classList.add('open');
  }

  function addPlayerRow(data, container) {
    container = container || els.playerRows;
    var frag = els.playerRowTemplate.content.cloneNode(true);
    var row = frag.querySelector('.player-row');
    var hasAnyStat = false;
    if (data) {
      row.querySelector('.p-name').value = data.name || '';
      row.querySelector('.p-jersey').value = data.number || data.jersey || '';
      row.querySelector('.p-position').value = data.position || '';
      STAT_FIELD_KEYS.forEach(function (key) {
        var el = row.querySelector('.p-' + key);
        if (!el) return;
        if (data[key]) { el.value = data[key]; hasAnyStat = true; }
      });
    }
    row.querySelector('.remove-player-btn').addEventListener('click', function () {
      row.remove();
    });

    var toggleBtn = row.querySelector('.stats-toggle-btn');
    var groups = row.querySelector('.stat-groups');
    if (hasAnyStat) {
      groups.style.display = '';
      toggleBtn.textContent = '\u2212 Hide stats';
    }
    toggleBtn.addEventListener('click', function () {
      var open = groups.style.display !== 'none';
      groups.style.display = open ? 'none' : '';
      toggleBtn.textContent = open ? '+ Add stats' : '\u2212 Hide stats';
    });

    container.appendChild(row);
  }

  els.addPlayerBtn.addEventListener('click', function () { addPlayerRow(null, els.playerRows); });

  function collectPlayerRows(container) {
    container = container || els.playerRows;
    var rows = container.querySelectorAll('.player-row');
    var players = [];
    rows.forEach(function (row) {
      var name = row.querySelector('.p-name').value.trim();
      if (!name) return; // skip blank rows
      var player = {
        name: name,
        position: row.querySelector('.p-position').value.trim(),
        number: row.querySelector('.p-jersey').value.trim()
      };
      STAT_FIELD_KEYS.forEach(function (key) {
        var el = row.querySelector('.p-' + key);
        player[key] = el ? (parseInt(el.value, 10) || 0) : 0;
      });
      players.push(player);
    });
    return players;
  }

  els.resultClose.addEventListener('click', closeResultModal);
  els.resultCancel.addEventListener('click', closeResultModal);
  function closeResultModal() {
    els.resultOverlay.classList.remove('open');
    activeGameId = null;
  }

  els.resultSubmit.addEventListener('click', function () {
    var g = games[activeGameId];
    if (!g) return;
    var sf = parseInt(els.scoreFor.value, 10);
    var sa = parseInt(els.scoreAgainst.value, 10);
    if (isNaN(sf) || isNaN(sa)) {
      showToast('Enter both scores');
      return;
    }
    var isSelfA = session.team === g.teamA;
    g.scoreA = isSelfA ? sf : sa;
    g.scoreB = isSelfA ? sa : sf;
    g.status = 'final';

    var players = collectPlayerRows();
    if (isSelfA) { g.statsA = players; } else { g.statsB = players; }

    persistGame(g);
    closeResultModal();
    showToast('Score posted');
    render();
  });

  // ---------- Shared storage (best-effort; falls back to in-memory demo) ----------
  async function initStorage() {
    try {
      if (window.claude && typeof window.claude.use === 'function') {
        db = await window.claude.use('db');
      }
    } catch (e) { db = null; }

    if (db) {
      try {
        db.collection('games').onSnapshot(function (docs) {
          docs.forEach(function (d) {
            games[d.id] = Object.assign({ id: d.id }, d.data);
          });
          render();
        });
      } catch (e) { /* fall back silently to seed data */ }
    }
  }

  function persistGame(g) {
    if (!db) return; // demo mode: state lives in memory for this session only
    try {
      db.doc('games/' + g.id).set(g).catch(function () {
        showToast('Could not sync — showing your update locally only');
      });
    } catch (e) { /* ignore in demo mode */ }
  }

  function deleteGameRemote(id) {
    if (!db) return;
    try {
      db.doc('games/' + id).delete().catch(function () {
        showToast('Could not sync deletion — removed locally only');
      });
    } catch (e) { /* ignore in demo mode */ }
  }

  // ---------- Admin: schedule matchups ----------
  function formatDateLabel(dateStr, timeStr, venue) {
    if (!dateStr || !timeStr) return venue || '';
    var dParts = dateStr.split('-');
    var month = parseInt(dParts[1], 10);
    var day = parseInt(dParts[2], 10);
    var tParts = timeStr.split(':');
    var hour24 = parseInt(tParts[0], 10);
    var minute = tParts[1];
    var ampm = hour24 >= 12 ? 'p' : 'a';
    var hour12 = hour24 % 12;
    if (hour12 === 0) hour12 = 12;
    var label = month + '/' + day + ' @ ' + hour12 + ':' + minute + ampm;
    if (venue) label += ' / ' + venue;
    return label;
  }

  function parseDateLabel(label) {
    if (!label) return null;
    var m = /^(\d{1,2})\/(\d{1,2}) @ (\d{1,2}):(\d{2})(a|p)(?: \/ (.+))?$/i.exec(label.trim());
    if (m) {
      var month = ('0' + m[1]).slice(-2);
      var day = ('0' + m[2]).slice(-2);
      var hour12 = parseInt(m[3], 10);
      var minute = m[4];
      var isPM = /p/i.test(m[5]);
      var hour24 = hour12 % 12 + (isPM ? 12 : 0);
      return {
        date: '2026-' + month + '-' + day,
        time: ('0' + hour24).slice(-2) + ':' + minute,
        venue: m[6] || ''
      };
    }
    // Date known, but time is TBD (e.g. "10/14 @ TBD / Park City?")
    var m2 = /^(\d{1,2})\/(\d{1,2}) @ TBD(?: \/ (.+))?$/i.exec(label.trim());
    if (m2) {
      var month2 = ('0' + m2[1]).slice(-2);
      var day2 = ('0' + m2[2]).slice(-2);
      return {
        date: '2026-' + month2 + '-' + day2,
        time: null,
        venue: m2[3] || ''
      };
    }
    return null;
  }

  // ---------- Schedule PDF export ----------
  async function downloadSchedulePDF() {
    if (!window.jspdf || !window.jspdf.jsPDF) {
      showToast('PDF library failed to load');
      return;
    }
    if (!window.claude || typeof window.claude.use !== 'function') {
      showToast('Downloads aren\u2019t available in this view');
      return;
    }
    var downloads = await window.claude.use('downloads');
    if (!downloads) {
      showToast('Downloads aren\u2019t available in this view');
      return;
    }

    var doc = new window.jspdf.jsPDF({ unit: 'pt', format: 'letter' });
    var pageWidth = doc.internal.pageSize.getWidth();
    var pageHeight = doc.internal.pageSize.getHeight();
    var margin = 44;
    var y = 54;

    doc.setFont('helvetica', 'bold');
    doc.setFontSize(18);
    doc.setTextColor(206, 32, 40);
    doc.text(teamFilter ? (teamFilter + ' \u2014 2026 Schedule') : 'UHSGFA \u2014 2026 Season Schedule', margin, y);
    y += 18;

    doc.setFont('helvetica', 'normal');
    doc.setFontSize(10);
    doc.setTextColor(110, 110, 110);
    doc.text(teamFilter ? (teamFilter + '\u2019s games only, regular season and playoffs') : 'All teams \u2014 regular season and playoffs', margin, y);
    y += 22;

    var byWeek = {};
    Object.keys(games).forEach(function (id) {
      var g = games[id];
      if (teamFilter && g.teamA !== teamFilter && g.teamB !== teamFilter) return;
      byWeek[g.week] = byWeek[g.week] || [];
      byWeek[g.week].push(g);
    });
    var weekNums = Object.keys(byWeek).map(Number).sort(function (a, b) { return a - b; });

    function ensureSpace(needed) {
      if (y + needed > pageHeight - 40) {
        doc.addPage();
        y = 54;
      }
    }

    weekNums.forEach(function (w) {
      var weekGames = byWeek[w].slice().sort(function (a, b) {
        var pa = parseDateLabel(a.dateLabel), pb = parseDateLabel(b.dateLabel);
        var ka = pa ? (pa.date + 'T' + (pa.time || '99:99')) : '9999';
        var kb = pb ? (pb.date + 'T' + (pb.time || '99:99')) : '9999';
        return ka < kb ? -1 : (ka > kb ? 1 : 0);
      });
      var label = weekGames[0].weekLabel ? weekGames[0].weekLabel : ('Week ' + w);

      ensureSpace(40);
      doc.setFont('helvetica', 'bold');
      doc.setFontSize(13);
      doc.setTextColor(20, 20, 20);
      doc.text(label, margin, y);
      y += 6;
      doc.setDrawColor(210, 210, 210);
      doc.line(margin, y, pageWidth - margin, y);
      y += 16;

      weekGames.forEach(function (g) {
        ensureSpace(22);
        var scoreText = g.status === 'final' ? ('  \u2014  Final ' + g.scoreA + '-' + g.scoreB) : '';
        doc.setFont('helvetica', 'bold');
        doc.setFontSize(10.5);
        doc.setTextColor(30, 30, 30);
        doc.text(g.teamA + ' vs ' + g.teamB + scoreText, margin, y);
        doc.setFont('helvetica', 'normal');
        doc.setFontSize(9.5);
        doc.setTextColor(120, 120, 120);
        doc.text(g.dateLabel || '', pageWidth - margin, y, { align: 'right' });
        y += 17;
      });
      y += 12;
    });

    var filename = 'UHSGFA-2026-Schedule' + (teamFilter ? ('-' + teamFilter.replace(/\s+/g, '-')) : '') + '.pdf';
    var blob = doc.output('blob');

    try {
      var result = await downloads.save({ filename: filename, data: blob });
      showToast(result.status === 'saved' ? 'PDF downloaded' : 'PDF sent');
    } catch (err) {
      if (err && err.code === 'declined') {
        // viewer said no; no toast needed
      } else if (err && err.code === 'rate_limited') {
        showToast('Try again in a moment');
      } else {
        showToast('Could not save the PDF');
      }
    }
  }
  els.downloadScheduleBtn.addEventListener('click', downloadSchedulePDF);

  var WEEK_LABELS = {
    7: 'Playoffs \u00b7 First Round',
    8: 'Playoffs \u00b7 Round of 16',
    9: 'Playoffs \u00b7 Quarterfinals',
    10: 'Playoffs \u00b7 Semifinals',
    11: 'Championship'
  };

  function resetAdminForm() {
    editingGameId = null;
    els.adminWeek.value = '1';
    els.adminVenue.value = '';
    els.adminDate.value = '';
    els.adminTime.value = '';
    els.adminScoreA.value = '';
    els.adminScoreB.value = '';
    els.adminTeamA.value = '';
    els.adminTeamB.value = '';
    els.adminSubmitBtn.textContent = 'Add Matchup';
    els.adminCancelEditBtn.style.display = 'none';

    els.adminPlayerRowsA.innerHTML = '';
    els.adminPlayerRowsB.innerHTML = '';
    els.adminStatsAWrap.style.display = 'none';
    els.adminStatsBWrap.style.display = 'none';
    els.adminStatsAToggle.textContent = '+ Add player stats for Team A';
    els.adminStatsBToggle.textContent = '+ Add player stats for Team B';
  }

  function toggleAdminStatsSection(toggleBtn, wrap, teamLabel) {
    var open = wrap.style.display !== 'none';
    wrap.style.display = open ? 'none' : '';
    toggleBtn.textContent = (open ? '+ Add player stats for ' : '\u2212 Hide player stats for ') + teamLabel;
  }
  els.adminStatsAToggle.addEventListener('click', function () {
    toggleAdminStatsSection(els.adminStatsAToggle, els.adminStatsAWrap, els.adminTeamA.value.trim() || 'Team A');
  });
  els.adminStatsBToggle.addEventListener('click', function () {
    toggleAdminStatsSection(els.adminStatsBToggle, els.adminStatsBWrap, els.adminTeamB.value.trim() || 'Team B');
  });
  els.adminAddPlayerA.addEventListener('click', function () { addPlayerRow(null, els.adminPlayerRowsA); });
  els.adminAddPlayerB.addEventListener('click', function () { addPlayerRow(null, els.adminPlayerRowsB); });

  els.adminSubmitBtn.addEventListener('click', function () {
    var week = parseInt(els.adminWeek.value, 10);
    var teamA = els.adminTeamA.value.trim();
    var teamB = els.adminTeamB.value.trim();
    var date = els.adminDate.value;
    var time = els.adminTime.value;
    var venue = els.adminVenue.value.trim();
    var scoreAraw = els.adminScoreA.value.trim();
    var scoreBraw = els.adminScoreB.value.trim();

    if (!teamA || !teamB) { showToast('Enter both team names'); return; }
    if (!week || week < 1) { showToast('Pick a week'); return; }
    if (teamA === teamB) { showToast('Team A and Team B must be different'); return; }
    if (!date || !time) { showToast('Set both a date and a time'); return; }
    if ((scoreAraw === '') !== (scoreBraw === '')) {
      showToast('Enter both scores, or leave both blank');
      return;
    }

    var dateLabel = formatDateLabel(date, time, venue);
    var hasScores = scoreAraw !== '' && scoreBraw !== '';
    var scoreA = hasScores ? parseInt(scoreAraw, 10) : null;
    var scoreB = hasScores ? parseInt(scoreBraw, 10) : null;
    var weekLabel = WEEK_LABELS[week] || null;
    var statsA = collectPlayerRows(els.adminPlayerRowsA);
    var statsB = collectPlayerRows(els.adminPlayerRowsB);

    if (editingGameId) {
      var existing = games[editingGameId];
      existing.week = week;
      if (weekLabel) { existing.weekLabel = weekLabel; } else { delete existing.weekLabel; }
      existing.teamA = teamA;
      existing.teamB = teamB;
      existing.dateLabel = dateLabel;
      if (hasScores) {
        existing.status = 'final';
        existing.scoreA = scoreA;
        existing.scoreB = scoreB;
      } else {
        existing.status = 'scheduled';
        delete existing.scoreA;
        delete existing.scoreB;
      }
      if (statsA.length) { existing.statsA = statsA; } else { delete existing.statsA; }
      if (statsB.length) { existing.statsB = statsB; } else { delete existing.statsB; }
      persistGame(existing);
      showToast('Matchup updated');
    } else {
      var id = 'g' + Date.now();
      var newGame = { id: id, week: week, teamA: teamA, teamB: teamB, dateLabel: dateLabel, status: hasScores ? 'final' : 'scheduled' };
      if (weekLabel) newGame.weekLabel = weekLabel;
      if (hasScores) { newGame.scoreA = scoreA; newGame.scoreB = scoreB; }
      if (statsA.length) newGame.statsA = statsA;
      if (statsB.length) newGame.statsB = statsB;
      games[id] = newGame;
      persistGame(newGame);
      showToast(hasScores ? 'Final score posted' : 'Matchup scheduled');
    }

    resetAdminForm();
    renderAdminList();
    renderTeamGrid();
    render();
  });

  els.adminCancelEditBtn.addEventListener('click', function () {
    resetAdminForm();
    renderAdminList();
  });

  function editMatchup(id) {
    var g = games[id];
    if (!g) return;
    editingGameId = id;
    els.adminWeek.value = g.week;
    els.adminTeamA.value = g.teamA;
    els.adminTeamB.value = g.teamB;
    var parsed = parseDateLabel(g.dateLabel);
    els.adminDate.value = parsed ? parsed.date : '';
    els.adminTime.value = (parsed && parsed.time) ? parsed.time : '';
    els.adminVenue.value = parsed ? parsed.venue : '';
    els.adminScoreA.value = (g.status === 'final' && typeof g.scoreA === 'number') ? g.scoreA : '';
    els.adminScoreB.value = (g.status === 'final' && typeof g.scoreB === 'number') ? g.scoreB : '';

    els.adminPlayerRowsA.innerHTML = '';
    els.adminPlayerRowsB.innerHTML = '';
    var statsA = g.statsA || [];
    var statsB = g.statsB || [];
    statsA.forEach(function (p) { addPlayerRow(p, els.adminPlayerRowsA); });
    statsB.forEach(function (p) { addPlayerRow(p, els.adminPlayerRowsB); });
    els.adminStatsAWrap.style.display = statsA.length ? '' : 'none';
    els.adminStatsBWrap.style.display = statsB.length ? '' : 'none';
    els.adminStatsAToggle.textContent = (statsA.length ? '\u2212 Hide' : '+ Add') + ' player stats for ' + (g.teamA || 'Team A');
    els.adminStatsBToggle.textContent = (statsB.length ? '\u2212 Hide' : '+ Add') + ' player stats for ' + (g.teamB || 'Team B');

    els.adminSubmitBtn.textContent = 'Save Changes';
    els.adminCancelEditBtn.style.display = '';
    renderAdminList();
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  function removeMatchup(id) {
    delete games[id];
    deleteGameRemote(id);
    if (editingGameId === id) resetAdminForm();
    renderAdminList();
    renderTeamGrid();
    render();
    showToast('Matchup deleted');
  }

  function renderAdminList() {
    els.adminGameList.innerHTML = '';

    var allIds = Object.keys(games).sort(function (a, b) {
      return games[a].week - games[b].week;
    });

    // Rebuild the week filter options, preserving the current selection if still valid.
    var currentFilter = els.adminWeekFilter.value || 'all';
    var weeksPresent = [];
    allIds.forEach(function (id) {
      var w = games[id].week;
      if (weeksPresent.indexOf(w) === -1) weeksPresent.push(w);
    });
    weeksPresent.sort(function (a, b) { return a - b; });
    els.adminWeekFilter.innerHTML = '<option value="all">All Weeks</option>';
    weeksPresent.forEach(function (w) {
      var label = games[allIds.filter(function (id) { return games[id].week === w; })[0]].weekLabel;
      var opt = document.createElement('option');
      opt.value = String(w);
      opt.textContent = label ? label : ('Week ' + w);
      els.adminWeekFilter.appendChild(opt);
    });
    if (currentFilter === 'all' || weeksPresent.indexOf(parseInt(currentFilter, 10)) > -1) {
      els.adminWeekFilter.value = currentFilter;
    } else {
      els.adminWeekFilter.value = 'all';
    }

    var activeFilter = els.adminWeekFilter.value;
    var ids = activeFilter === 'all'
      ? allIds
      : allIds.filter(function (id) { return String(games[id].week) === activeFilter; });

    if (!ids.length) {
      var empty = document.createElement('div');
      empty.className = 'empty';
      empty.textContent = 'No matchups scheduled yet.';
      els.adminGameList.appendChild(empty);
      return;
    }
    ids.forEach(function (id) {
      var g = games[id];
      var row = document.createElement('div');
      row.className = 'admin-game-row' + (editingGameId === id ? ' editing' : '');

      var info = document.createElement('div');
      info.className = 'agr-info';
      var matchup = document.createElement('div');
      matchup.className = 'agr-matchup';
      matchup.textContent = (g.weekLabel ? g.weekLabel : ('Wk ' + g.week)) + ' — ' + g.teamA + ' vs ' + g.teamB +
        (g.status === 'final' ? ' (Final ' + g.scoreA + '-' + g.scoreB + ')' : '');
      var meta = document.createElement('div');
      meta.className = 'agr-meta';
      meta.textContent = g.dateLabel || '';
      info.appendChild(matchup);
      info.appendChild(meta);

      var actions = document.createElement('div');
      actions.className = 'agr-actions';
      var editBtn = document.createElement('button');
      editBtn.className = 'agr-btn';
      editBtn.textContent = 'Edit';
      editBtn.addEventListener('click', function () { editMatchup(id); });
      var delBtn = document.createElement('button');
      delBtn.className = 'agr-btn danger';
      delBtn.textContent = 'Delete';
      delBtn.addEventListener('click', function () { removeMatchup(id); });
      actions.appendChild(editBtn);
      actions.appendChild(delBtn);

      row.appendChild(info);
      row.appendChild(actions);
      els.adminGameList.appendChild(row);
    });
  }

  els.adminWeekFilter.addEventListener('change', function () { renderAdminList(); });

  populateStatsSelects();
  renderStatsTeamContent();
  renderStatsIndivPlayers();
  renderStatsIndivContent();

  renderTeamGrid();
  render();
  initStorage();
})();
</script>

</body>
</html>
