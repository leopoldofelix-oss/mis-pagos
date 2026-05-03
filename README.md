# mis-pagos
https://claude.ai/public/artifacts<!DOCTYPE html>

<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="Mis Pagos">
<meta name="theme-color" content="#F2EBDC">
<title>Mis Pagos</title>

<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect width='100' height='100' rx='18' fill='%231F3A2E'/%3E%3Ctext x='50' y='68' font-family='Georgia,serif' font-size='56' font-weight='500' fill='%23F2EBDC' text-anchor='middle'%3EM%3C/text%3E%3C/svg%3E">
<link rel="apple-touch-icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 180 180'%3E%3Crect width='180' height='180' rx='36' fill='%231F3A2E'/%3E%3Ctext x='90' y='122' font-family='Georgia,serif' font-size='100' font-weight='500' fill='%23F2EBDC' text-anchor='middle'%3EM%3C/text%3E%3C/svg%3E">

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300;9..144,400;9..144,500;9..144,600;9..144,700&family=Plus+Jakarta+Sans:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">

<style>
  :root {
    --cream: #F2EBDC;
    --paper: #FBF6EA;
    --ink: #1A1815;
    --forest: #1F3A2E;
    --terra: #B8492C;
    --taupe: #8A7E6A;
    --line: #DCD2BB;
    --gold: #C99846;
  }
  * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; margin: 0; padding: 0; }
  html, body {
    background: var(--cream);
    color: var(--ink);
    font-family: 'Plus Jakarta Sans', system-ui, -apple-system, sans-serif;
    min-height: 100vh;
    min-height: 100dvh;
    background-image: radial-gradient(rgba(26,24,21,0.04) 1px, transparent 1px);
    background-size: 3px 3px;
    -webkit-font-smoothing: antialiased;
  }
  .display { font-family: 'Fraunces', Georgia, serif; font-optical-sizing: auto; }
  .mono { font-family: 'JetBrains Mono', ui-monospace, monospace; font-feature-settings: 'tnum'; }

  .app {
    max-width: 640px;
    margin: 0 auto;
    padding: max(env(safe-area-inset-top), 1.5rem) 1.25rem calc(6rem + env(safe-area-inset-bottom));
    min-height: 100vh;
    min-height: 100dvh;
  }

  header {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    margin-bottom: 1.5rem;
  }
  header .eyebrow { font-size: 0.7rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--taupe); }
  header h1 { font-family: 'Fraunces', Georgia, serif; font-size: 1.875rem; font-weight: 500; line-height: 1; margin-top: 0.25rem; }
  header .today-day { font-size: 0.7rem; color: var(--taupe); text-align: right; }
  header .today-date { font-family: 'Fraunces', Georgia, serif; font-size: 1.125rem; line-height: 1; text-align: right; }

  .card {
    background: var(--paper);
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 1rem;
  }
  .card-lg { padding: 1.5rem; }
  .card.dashed { border-style: dashed; }

  /* HERO total mes */
  .hero { margin-bottom: 1.25rem; }
  .hero .row { display: flex; align-items: baseline; justify-content: space-between; margin-bottom: 0.25rem; }
  .hero .label { font-size: 0.7rem; letter-spacing: 0.18em; text-transform: uppercase; color: var(--taupe); }
  .hero .total { font-family: 'Fraunces', Georgia, serif; font-size: 3rem; font-weight: 300; letter-spacing: -0.02em; margin-top: 0.5rem; line-height: 1; }
  .hero .currency { font-size: 0.7rem; color: var(--taupe); margin-top: 0.25rem; }
  .hero .footer { margin-top: 1rem; padding-top: 1rem; border-top: 1px solid var(--line); display: flex; align-items: baseline; justify-content: space-between; }
  .hero .footer .sub { font-size: 0.7rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--taupe); }
  .hero .footer .val { font-family: 'JetBrains Mono', monospace; font-size: 0.875rem; font-weight: 600; color: var(--forest); }

  /* Section heads */
  .section-head { display: flex; align-items: baseline; justify-content: space-between; margin-bottom: 0.875rem; padding: 0 0.25rem; }
  .section-head h2 { font-family: 'Fraunces', Georgia, serif; font-size: 1.5rem; font-weight: 500; }
  .section-head .count { color: var(--taupe); font-family: 'JetBrains Mono', monospace; font-size: 0.875rem; margin-left: 0.25rem; }
  .section-head .meta { font-size: 0.7rem; color: var(--taupe); text-transform: uppercase; letter-spacing: 0.1em; }

  .pulse::before {
    content: '';
    display: inline-block;
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--terra);
    margin-right: 8px;
    vertical-align: middle;
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%, 100% { opacity: 1; } 50% { opacity: 0.3; } }

  /* Alert / event card */
  .event {
    display: flex;
    align-items: center;
    gap: 1rem;
    background: var(--paper);
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 1rem;
    margin-bottom: 0.5rem;
    animation: slideUp 0.25s ease-out;
  }
  .event .date-block { text-align: center; width: 3.5rem; flex-shrink: 0; }
  .event .date-block .day { font-family: 'Fraunces', Georgia, serif; font-size: 1.5rem; font-weight: 500; line-height: 1; }
  .event .date-block .mon { font-size: 0.625rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--taupe); margin-top: 0.25rem; }
  .event .divider { width: 1px; height: 2.5rem; background: var(--line); flex-shrink: 0; }
  .event .info { flex: 1; min-width: 0; }
  .event .name { font-weight: 500; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .event .sub { font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.1em; margin-top: 0.125rem; }
  .event .amount { font-family: 'JetBrains Mono', monospace; font-size: 0.875rem; font-weight: 600; flex-shrink: 0; }
  .text-terra { color: var(--terra); }
  .text-gold { color: var(--gold); }
  .text-forest { color: var(--forest); }
  .text-taupe { color: var(--taupe); }

  @keyframes slideUp { from { transform: translateY(20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
  @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
  .fade-in { animation: fadeIn 0.4s ease-out; }

  /* Item rows (sub & gasto) */
  .item-row {
    display: flex; align-items: center; gap: 1rem;
    background: var(--paper); border: 1px solid var(--line);
    border-radius: 4px; padding: 1rem; margin-bottom: 0.5rem;
  }
  .item-row .info { flex: 1; min-width: 0; }
  .item-row .name { font-weight: 500; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .item-row .desc { font-size: 0.75rem; color: var(--taupe); margin-top: 0.125rem; }
  .item-row .amount { font-family: 'JetBrains Mono', monospace; font-size: 0.875rem; font-weight: 600; flex-shrink: 0; }
  .row-actions { display: flex; gap: 0.25rem; flex-shrink: 0; }
  .icon-btn { background: transparent; border: 0; padding: 0.5rem; color: var(--taupe); cursor: pointer; display: flex; align-items: center; justify-content: center; }
  .icon-btn:hover { color: var(--forest); }
  .icon-btn.danger:hover { color: var(--terra); }

  /* Card (tarjeta) */
  .tarjeta { background: var(--paper); border: 1px solid var(--line); border-radius: 4px; overflow: hidden; margin-bottom: 0.75rem; }
  .tarjeta .top { padding: 1rem; }
  .tarjeta .head-row { display: flex; align-items: flex-start; justify-content: space-between; gap: 0.75rem; }
  .tarjeta .name { font-family: 'Fraunces', Georgia, serif; font-size: 1.125rem; font-weight: 500; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .tarjeta .last4 { font-family: 'JetBrains Mono', monospace; font-size: 0.7rem; color: var(--taupe); margin-top: 0.125rem; }
  .tarjeta .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 0.75rem; margin-top: 1rem; padding-top: 1rem; border-top: 1px solid var(--line); }
  .date-cell .lbl { font-size: 0.625rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--taupe); }
  .date-cell .date { font-family: 'Fraunces', Georgia, serif; font-size: 1.25rem; font-weight: 500; margin-top: 0.25rem; }
  .date-cell .rel { font-size: 0.7rem; color: var(--taupe); margin-top: 0.125rem; }
  .date-cell .amt { font-family: 'JetBrains Mono', monospace; font-size: 0.7rem; font-weight: 600; margin-top: 0.5rem; }

  /* Empty state */
  .empty { background: var(--paper); border: 1px dashed var(--line); border-radius: 4px; padding: 2rem; text-align: center; color: var(--taupe); font-size: 0.875rem; }
  .empty.hero { padding: 2rem 1.5rem; }
  .empty .title { font-family: 'Fraunces', Georgia, serif; font-size: 1.125rem; color: var(--ink); margin-bottom: 0.25rem; }
  .empty .desc { font-size: 0.875rem; margin-bottom: 1.25rem; }
  .empty-actions { display: flex; gap: 0.5rem; justify-content: center; flex-wrap: wrap; }

  /* Buttons */
  .btn {
    background: var(--forest);
    color: var(--paper);
    border: 0;
    padding: 0.5rem 0.75rem;
    border-radius: 4px;
    font-family: inherit;
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    font-weight: 500;
    display: inline-flex;
    align-items: center;
    gap: 0.375rem;
    cursor: pointer;
  }
  .btn-outline {
    background: var(--paper);
    color: var(--ink);
    border: 1px solid var(--line);
  }
  .btn-block {
    width: 100%;
    padding: 1rem;
    font-size: 0.875rem;
    justify-content: center;
    margin-top: 0.5rem;
  }

  /* Bottom nav */
  nav.bottom {
    position: fixed; bottom: 0; left: 0; right: 0;
    background: var(--paper);
    border-top: 1px solid var(--line);
    padding-bottom: env(safe-area-inset-bottom);
    z-index: 30;
  }
  nav.bottom .grid {
    max-width: 640px; margin: 0 auto;
    display: grid; grid-template-columns: repeat(4, 1fr);
  }
  .tab {
    background: transparent; border: 0; padding: 0.75rem 0;
    display: flex; flex-direction: column; align-items: center; gap: 0.25rem;
    color: var(--taupe); cursor: pointer; font-family: inherit;
    transition: color 0.15s;
  }
  .tab.active { color: var(--forest); }
  .tab .lbl { font-size: 0.625rem; letter-spacing: 0.1em; text-transform: uppercase; font-weight: 500; }

  /* Modal */
  .overlay {
    position: fixed; inset: 0;
    background: rgba(0,0,0,0.4);
    display: flex; align-items: flex-end; justify-content: center;
    z-index: 100;
    animation: fadeIn 0.2s ease-out;
  }
  @media (min-width: 640px) { .overlay { align-items: center; } }
  .modal {
    background: var(--cream);
    width: 100%; max-width: 420px;
    max-height: 92vh;
    overflow-y: auto;
    border-radius: 12px 12px 0 0;
    animation: slideUp 0.25s ease-out;
  }
  @media (min-width: 640px) { .modal { border-radius: 12px; } }
  .modal-head {
    display: flex; justify-content: flex-end;
    padding: 0.75rem;
    position: sticky; top: 0;
    background: var(--cream);
    border-bottom: 1px solid var(--line);
    z-index: 1;
  }
  .modal-body { padding: 0 1.25rem 1.5rem; }
  .modal-body h3 { font-family: 'Fraunces', Georgia, serif; font-size: 1.5rem; font-weight: 500; margin-bottom: 0.25rem; }
  .modal-body .hint { font-size: 0.75rem; color: var(--taupe); margin-bottom: 1.25rem; }

  /* Form */
  label.field { display: block; margin-bottom: 1rem; }
  label.field .lbl { display: block; font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--taupe); margin-bottom: 0.5rem; }
  input, select {
    width: 100%; background: var(--paper); border: 1px solid var(--line);
    padding: 0.75rem; border-radius: 4px;
    font-family: inherit; font-size: 1rem; color: var(--ink);
  }
  input.mono-in { font-family: 'JetBrains Mono', monospace; }
  input.day-in { font-family: 'JetBrains Mono', monospace; text-align: center; font-size: 1.125rem; }
  input:focus, select:focus { outline: 2px solid var(--forest); outline-offset: -2px; }
  .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 0.75rem; }
  .pill-group { display: grid; grid-template-columns: 1fr 1fr; gap: 0.5rem; }
  .pill {
    padding: 0.75rem;
    border-radius: 4px;
    border: 1px solid var(--line);
    background: var(--paper);
    color: var(--taupe);
    font-family: inherit;
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    cursor: pointer;
  }
  .pill.active { background: var(--forest); color: var(--paper); border-color: var(--forest); }
  .money-wrap { position: relative; }
  .money-wrap span.peso { position: absolute; left: 0.75rem; top: 50%; transform: translateY(-50%); color: var(--taupe); font-family: 'JetBrains Mono', monospace; pointer-events: none; }
  .money-wrap input { padding-left: 1.75rem; font-family: 'JetBrains Mono', monospace; }

  .loading { text-align: center; padding: 4rem 0; color: var(--taupe); font-size: 0.875rem; }
</style>

</head>
<body>

<div id="app" class="app">
  <div class="loading">Cargando…</div>
</div>

<nav class="bottom">
  <div class="grid">
    <button class="tab" data-tab="inicio"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9,22 9,12 15,12 15,22"/></svg><span class="lbl">Inicio</span></button>
    <button class="tab" data-tab="tarjetas"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="14" x="2" y="5" rx="2"/><line x1="2" x2="22" y1="10" y2="10"/></svg><span class="lbl">Tarjetas</span></button>
    <button class="tab" data-tab="subs"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m17 2 4 4-4 4"/><path d="M3 11v-1a4 4 0 0 1 4-4h14"/><path d="m7 22-4-4 4-4"/><path d="M21 13v1a4 4 0 0 1-4 4H3"/></svg><span class="lbl">Subs</span></button>
    <button class="tab" data-tab="gastos"><svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 2v20l2-1 2 1 2-1 2 1 2-1 2 1 2-1 2 1V2l-2 1-2-1-2 1-2-1-2 1-2-1-2 1Z"/><path d="M16 8h-6a2 2 0 1 0 0 4h4a2 2 0 1 1 0 4H8"/><path d="M12 17.5v-11"/></svg><span class="lbl">Gastos</span></button>
  </div>
</nav>

<script>
/* ============== ESTADO Y PERSISTENCIA ============== */
const STORAGE_KEY = 'misPagos.v1';
const state = {
  cards: [],
  subs: [],
  expenses: [],
  tab: 'inicio',
  modal: null
};

function uid() {
  return 'id-' + Date.now().toString(36) + '-' + Math.random().toString(36).slice(2, 8);
}

function load() {
  try {
    const raw = localStorage.getItem(STORAGE_KEY);
    if (raw) {
      const data = JSON.parse(raw);
      state.cards = data.cards || [];
      state.subs = data.subs || [];
      state.expenses = data.expenses || [];
    }
  } catch (e) { console.error('Load error', e); }
}

function save() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify({
      cards: state.cards,
      subs: state.subs,
      expenses: state.expenses
    }));
  } catch (e) { console.error('Save error', e); }
}

/* ============== UTILIDADES DE FECHA ============== */
const MESES = ['enero','febrero','marzo','abril','mayo','junio','julio','agosto','septiembre','octubre','noviembre','diciembre'];
const MESES_C = ['ene','feb','mar','abr','may','jun','jul','ago','sep','oct','nov','dic'];
const DIAS = ['domingo','lunes','martes','miércoles','jueves','viernes','sábado'];

function daysInMonth(y, m) { return new Date(y, m + 1, 0).getDate(); }

function nextOccurrenceOfDay(day, from) {
  const d = new Date(from); d.setHours(0,0,0,0);
  let y = d.getFullYear(), m = d.getMonth();
  let target = Math.min(day, daysInMonth(y, m));
  let cand = new Date(y, m, target);
  if (cand < d) {
    m += 1; if (m > 11) { m = 0; y += 1; }
    target = Math.min(day, daysInMonth(y, m));
    cand = new Date(y, m, target);
  }
  return cand;
}

function nextSubBilling(sub, from) {
  if (sub.frequency === 'anual' && sub.billingMonth != null) {
    const today = new Date(from); today.setHours(0,0,0,0);
    let y = today.getFullYear();
    const m = sub.billingMonth - 1;
    let t = Math.min(sub.billingDay, daysInMonth(y, m));
    let c = new Date(y, m, t);
    if (c < today) {
      y += 1;
      t = Math.min(sub.billingDay, daysInMonth(y, m));
      c = new Date(y, m, t);
    }
    return c;
  }
  return nextOccurrenceOfDay(sub.billingDay, from);
}

function daysUntil(date, from) {
  const a = new Date(from); a.setHours(0,0,0,0);
  const b = new Date(date); b.setHours(0,0,0,0);
  return Math.round((b - a) / 86400000);
}

function fmtMoney(n) {
  return '$' + Number(n || 0).toLocaleString('es-MX', { minimumFractionDigits: 0, maximumFractionDigits: 2 });
}

function fmtShort(d) {
  const date = new Date(d);
  return date.getDate() + ' ' + MESES_C[date.getMonth()];
}

function relDay(n) {
  if (n === 0) return 'hoy';
  if (n === 1) return 'mañana';
  if (n < 0) return 'hace ' + Math.abs(n) + 'd';
  return 'en ' + n + ' días';
}

function escapeHtml(s) {
  return String(s || '').replace(/[&<>"']/g, c => ({ '&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;' }[c]));
}

/* ============== ICONOS SVG ============== */
const I = {
  plus: '<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="M12 5v14"/></svg>',
  pencil: '<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21.174 6.812a1 1 0 0 0-3.986-3.987L3.842 16.174a2 2 0 0 0-.5.83l-1.321 4.352a.5.5 0 0 0 .623.622l4.353-1.32a2 2 0 0 0 .83-.497z"/></svg>',
  trash: '<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18"/><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"/><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"/></svg>',
  x: '<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 6 6 18"/><path d="m6 6 12 12"/></svg>',
  chev: '<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>',
  check: '<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6 9 17l-5-5"/></svg>'
};

/* ============== EVENTOS Y CÁLCULOS ============== */
function computeEvents(now) {
  const list = [];
  const horizon = new Date(now); horizon.setDate(horizon.getDate() + 60);

  state.cards.forEach(c => {
    list.push({ id: c.id + '-cut', kind: 'corte', name: c.name, date: nextOccurrenceOfDay(c.cutoffDay, now), amount: null });
    list.push({ id: c.id + '-pay', kind: 'pago', name: c.name, date: nextOccurrenceOfDay(c.paymentDay, now), amount: c.estimatedPayment || null });
  });
  state.subs.forEach(s => {
    list.push({ id: s.id, kind: 'sub', name: s.name, date: nextSubBilling(s, now), amount: s.amount, freq: s.frequency });
  });
  state.expenses.forEach(e => {
    let d;
    if (e.recurring) d = nextOccurrenceOfDay(e.day, now);
    else d = new Date(e.date);
    list.push({ id: e.id, kind: 'gasto', name: e.name, date: d, amount: e.amount, recurring: e.recurring });
  });

  return list.filter(ev => ev.date <= horizon).sort((a, b) => a.date - b.date);
}

function monthStats(events, now) {
  const y = now.getFullYear(), m = now.getMonth();
  const start = new Date(y, m, 1);
  const end = new Date(y, m + 1, 0); end.setHours(23,59,59,999);
  const inMonth = events.filter(e => e.date >= start && e.date <= end && e.amount);
  const total = inMonth.reduce((s, e) => s + (e.amount || 0), 0);
  const remaining = inMonth.filter(e => e.date >= now).reduce((s, e) => s + (e.amount || 0), 0);
  return { total, remaining, count: inMonth.length };
}

/* ============== RENDERIZADO ============== */
function render() {
  const now = new Date();
  const app = document.getElementById('app');
  const events = computeEvents(now);
  const stats = monthStats(events, now);

  const headerHtml = `
    <header class="fade-in">
      <div>
        <p class="eyebrow">Agenda</p>
        <h1>Mis Pagos</h1>
      </div>
      <div>
        <p class="today-day">${DIAS[now.getDay()]}</p>
        <p class="today-date">${now.getDate()} ${MESES_C[now.getMonth()]}</p>
      </div>
    </header>
  `;

  let body = '';
  if (state.tab === 'inicio') body = renderInicio(events, stats, now);
  else if (state.tab === 'tarjetas') body = renderTarjetas(now);
  else if (state.tab === 'subs') body = renderSubs(now);
  else if (state.tab === 'gastos') body = renderGastos(now);

  app.innerHTML = headerHtml + '<div class="fade-in">' + body + '</div>';

  // Update active tab
  document.querySelectorAll('.tab').forEach(btn => {
    btn.classList.toggle('active', btn.dataset.tab === state.tab);
  });

  // Render modal if open
  renderModal();
}

function renderInicio(events, stats, now) {
  const monthName = MESES[now.getMonth()];
  const alerts = events.filter(e => {
    const d = daysUntil(e.date, now);
    return d >= 0 && d <= 7;
  }).slice(0, 8);
  const hasAny = state.cards.length + state.subs.length + state.expenses.length > 0;

  let hero = `
    <section class="card card-lg hero">
      <div class="row">
        <p class="label">Total de ${monthName}</p>
        <p class="mono" style="font-size:0.7rem;color:var(--taupe)">${stats.count} cargo${stats.count !== 1 ? 's' : ''}</p>
      </div>
      <p class="display total">${fmtMoney(stats.total)}</p>
      <p class="currency">MXN</p>
      ${stats.remaining > 0 && stats.remaining < stats.total ? `
        <div class="footer">
          <span class="sub">Por pagar</span>
          <span class="val">${fmtMoney(stats.remaining)}</span>
        </div>
      ` : ''}
    </section>
  `;

  let alertsSection = `
    <section>
      <div class="section-head">
        <h2><span class="${alerts.length ? 'pulse' : ''}">Alertas</span></h2>
        <span class="meta">próximos 7 días</span>
      </div>
  `;

  if (!hasAny) {
    alertsSection += `
      <div class="empty hero">
        <p class="title">Empieza tu agenda</p>
        <p class="desc">Agrega tus tarjetas, suscripciones y gastos para verlos aquí.</p>
        <div class="empty-actions">
          <button class="btn" data-action="open-modal" data-type="card">+ Tarjeta</button>
          <button class="btn btn-outline" data-action="open-modal" data-type="sub">+ Suscripción</button>
          <button class="btn btn-outline" data-action="open-modal" data-type="exp">+ Gasto</button>
        </div>
      </div>
    `;
  } else if (alerts.length === 0) {
    alertsSection += `
      <div class="empty">
        <div style="color:var(--forest);margin-bottom:0.5rem">${I.check}</div>
        <p>Todo en orden esta semana</p>
      </div>
    `;
  } else {
    alerts.forEach(ev => {
      const d = daysUntil(ev.date, now);
      const urgent = d <= 2;
      const labels = { corte: 'Corte', pago: 'Pago tarjeta', sub: 'Suscripción', gasto: 'Gasto' };
      const colorClass = (ev.kind === 'pago' || urgent) ? 'text-terra' : ev.kind === 'corte' ? 'text-gold' : 'text-forest';
      alertsSection += `
        <div class="event">
          <div class="date-block">
            <p class="day">${ev.date.getDate()}</p>
            <p class="mon">${MESES_C[ev.date.getMonth()]}</p>
          </div>
          <div class="divider"></div>
          <div class="info">
            <p class="name">${escapeHtml(ev.name)}</p>
            <p class="sub ${colorClass}">${labels[ev.kind]} · ${relDay(d)}</p>
          </div>
          ${ev.amount != null ? `<p class="amount">${fmtMoney(ev.amount)}</p>` : ''}
        </div>
      `;
    });
  }
  alertsSection += '</section>';

  return hero + alertsSection;
}

function renderTarjetas(now) {
  let html = `
    <div class="section-head">
      <h2>Tarjetas <span class="count">${state.cards.length}</span></h2>
      <button class="btn" data-action="open-modal" data-type="card">${I.plus} Agregar</button>
    </div>
  `;
  if (state.cards.length === 0) {
    html += '<div class="empty">Aún no tienes tarjetas registradas.</div>';
    return html;
  }
  state.cards.forEach(c => {
    const cutoff = nextOccurrenceOfDay(c.cutoffDay, now);
    const payment = nextOccurrenceOfDay(c.paymentDay, now);
    html += `
      <article class="tarjeta">
        <div class="top">
          <div class="head-row">
            <div style="flex:1;min-width:0">
              <p class="name">${escapeHtml(c.name)}</p>
              ${c.lastFour ? `<p class="last4">•••• ${escapeHtml(c.lastFour)}</p>` : ''}
            </div>
            <div class="row-actions">
              <button class="icon-btn" data-action="edit" data-type="card" data-id="${c.id}">${I.pencil}</button>
              <button class="icon-btn danger" data-action="delete" data-type="card" data-id="${c.id}">${I.trash}</button>
            </div>
          </div>
          <div class="grid">
            <div class="date-cell">
              <p class="lbl">Corte</p>
              <p class="date text-gold">${fmtShort(cutoff)}</p>
              <p class="rel">${relDay(daysUntil(cutoff, now))}</p>
            </div>
            <div class="date-cell">
              <p class="lbl">Pago</p>
              <p class="date text-terra">${fmtShort(payment)}</p>
              <p class="rel">${relDay(daysUntil(payment, now))}</p>
              ${c.estimatedPayment ? `<p class="amt">${fmtMoney(c.estimatedPayment)}</p>` : ''}
            </div>
          </div>
        </div>
      </article>
    `;
  });
  return html;
}

function renderSubs(now) {
  const monthlyTotal = state.subs.filter(s => s.frequency !== 'anual').reduce((s, x) => s + (x.amount || 0), 0);
  let html = `
    <div class="section-head">
      <h2>Suscripciones <span class="count">${state.subs.length}</span></h2>
      <button class="btn" data-action="open-modal" data-type="sub">${I.plus} Agregar</button>
    </div>
  `;
  if (state.subs.length > 0) {
    html += `
      <div class="card" style="margin-bottom:0.75rem;display:flex;align-items:baseline;justify-content:space-between">
        <span style="font-size:0.7rem;text-transform:uppercase;letter-spacing:0.1em;color:var(--taupe)">Total mensual</span>
        <span class="display" style="font-size:1.25rem;font-weight:500">${fmtMoney(monthlyTotal)}</span>
      </div>
    `;
  } else {
    html += '<div class="empty">Aún no tienes suscripciones.</div>';
    return html;
  }
  state.subs.forEach(s => {
    const next = nextSubBilling(s, now);
    const d = daysUntil(next, now);
    html += `
      <div class="item-row">
        <div class="info">
          <p class="name">${escapeHtml(s.name)}</p>
          <p class="desc">${s.frequency === 'anual' ? 'Anual' : 'Mensual'} · próximo cobro ${fmtShort(next)} (${relDay(d)})</p>
        </div>
        <p class="amount">${fmtMoney(s.amount)}</p>
        <div class="row-actions">
          <button class="icon-btn" data-action="edit" data-type="sub" data-id="${s.id}">${I.pencil}</button>
          <button class="icon-btn danger" data-action="delete" data-type="sub" data-id="${s.id}">${I.trash}</button>
        </div>
      </div>
    `;
  });
  return html;
}

function renderGastos(now) {
  let html = `
    <div class="section-head">
      <h2>Gastos <span class="count">${state.expenses.length}</span></h2>
      <button class="btn" data-action="open-modal" data-type="exp">${I.plus} Agregar</button>
    </div>
  `;
  if (state.expenses.length === 0) {
    html += '<div class="empty">Aún no tienes gastos registrados.</div>';
    return html;
  }
  state.expenses.forEach(e => {
    const date = e.recurring ? nextOccurrenceOfDay(e.day, now) : new Date(e.date);
    const days = daysUntil(date, now);
    html += `
      <div class="item-row">
        <div class="info">
          <p class="name">${escapeHtml(e.name)}</p>
          <p class="desc">${e.recurring ? 'Recurrente · día ' + e.day : fmtShort(date)} · ${relDay(days)}</p>
        </div>
        <p class="amount">${fmtMoney(e.amount)}</p>
        <div class="row-actions">
          <button class="icon-btn" data-action="edit" data-type="exp" data-id="${e.id}">${I.pencil}</button>
          <button class="icon-btn danger" data-action="delete" data-type="exp" data-id="${e.id}">${I.trash}</button>
        </div>
      </div>
    `;
  });
  return html;
}

/* ============== MODAL ============== */
function renderModal() {
  let existing = document.querySelector('.overlay');
  if (!state.modal) {
    if (existing) existing.remove();
    document.body.style.overflow = '';
    return;
  }
  if (existing) existing.remove();

  document.body.style.overflow = 'hidden';
  const overlay = document.createElement('div');
  overlay.className = 'overlay';
  overlay.innerHTML = `
    <div class="modal" role="dialog">
      <div class="modal-head">
        <button class="icon-btn" data-action="close-modal">${I.x}</button>
      </div>
      <div class="modal-body">${getFormHtml()}</div>
    </div>
  `;
  overlay.addEventListener('click', (e) => {
    if (e.target === overlay) closeModal();
  });
  document.body.appendChild(overlay);

  // Wire form submit & pill toggles
  const form = overlay.querySelector('form');
  if (form) {
    form.addEventListener('submit', (e) => {
      e.preventDefault();
      handleFormSubmit(form);
    });
    overlay.querySelectorAll('.pill').forEach(p => {
      p.addEventListener('click', (e) => {
        e.preventDefault();
        const group = p.dataset.group;
        overlay.querySelectorAll(`.pill[data-group="${group}"]`).forEach(x => x.classList.remove('active'));
        p.classList.add('active');
        const hidden = form.querySelector(`input[name="${group}"]`);
        if (hidden) hidden.value = p.dataset.value;
        // Toggle visibility for sub frequency
        if (group === 'frequency') {
          const monthlyDay = form.querySelector('.field-monthly-day');
          const yearlyFields = form.querySelector('.field-yearly');
          if (monthlyDay && yearlyFields) {
            if (p.dataset.value === 'anual') {
              monthlyDay.style.display = 'none';
              yearlyFields.style.display = '';
            } else {
              monthlyDay.style.display = '';
              yearlyFields.style.display = 'none';
            }
          }
        }
        if (group === 'recurring') {
          const dayF = form.querySelector('.field-exp-day');
          const dateF = form.querySelector('.field-exp-date');
          if (dayF && dateF) {
            if (p.dataset.value === 'true') {
              dayF.style.display = '';
              dateF.style.display = 'none';
            } else {
              dayF.style.display = 'none';
              dateF.style.display = '';
            }
          }
        }
      });
    });
  }
}

function getFormHtml() {
  const { type, item } = state.modal;
  if (type === 'card') return cardFormHtml(item);
  if (type === 'sub') return subFormHtml(item);
  if (type === 'exp') return expFormHtml(item);
  return '';
}

function cardFormHtml(item) {
  return `
    <h3>${item ? 'Editar tarjeta' : 'Nueva tarjeta'}</h3>
    <p class="hint">Captura el día del mes para corte y pago.</p>
    <form>
      <input type="hidden" name="formType" value="card">
      <input type="hidden" name="id" value="${item?.id || ''}">
      <label class="field">
        <span class="lbl">Nombre del banco / tarjeta</span>
        <input name="name" value="${escapeHtml(item?.name || '')}" placeholder="BBVA Platinum" required>
      </label>
      <label class="field">
        <span class="lbl">Últimos 4 dígitos (opcional)</span>
        <input name="lastFour" class="mono-in" value="${escapeHtml(item?.lastFour || '')}" placeholder="1234" maxlength="4" pattern="\\d*">
      </label>
      <div class="grid-2">
        <label class="field">
          <span class="lbl">Día de corte</span>
          <input name="cutoffDay" class="day-in" type="number" min="1" max="31" value="${item?.cutoffDay || 1}" required>
        </label>
        <label class="field">
          <span class="lbl">Día límite de pago</span>
          <input name="paymentDay" class="day-in" type="number" min="1" max="31" value="${item?.paymentDay || 20}" required>
        </label>
      </div>
      <label class="field">
        <span class="lbl">Pago estimado mensual (opcional)</span>
        <div class="money-wrap">
          <span class="peso">$</span>
          <input name="estimatedPayment" type="number" step="0.01" min="0" value="${item?.estimatedPayment || ''}" placeholder="0.00">
        </div>
      </label>
      <button type="submit" class="btn btn-block">Guardar ${I.chev}</button>
    </form>
  `;
}

function subFormHtml(item) {
  const freq = item?.frequency || 'mensual';
  return `
    <h3>${item ? 'Editar suscripción' : 'Nueva suscripción'}</h3>
    <p class="hint">Netflix, Spotify, iCloud, etc.</p>
    <form>
      <input type="hidden" name="formType" value="sub">
      <input type="hidden" name="id" value="${item?.id || ''}">
      <input type="hidden" name="frequency" value="${freq}">
      <label class="field">
        <span class="lbl">Nombre</span>
        <input name="name" value="${escapeHtml(item?.name || '')}" placeholder="Spotify" required>
      </label>
      <label class="field">
        <span class="lbl">Monto (MXN)</span>
        <div class="money-wrap">
          <span class="peso">$</span>
          <input name="amount" type="number" step="0.01" min="0" value="${item?.amount || ''}" placeholder="0.00" required>
        </div>
      </label>
      <div class="field">
        <span class="lbl">Frecuencia</span>
        <div class="pill-group">
          <button type="button" class="pill ${freq === 'mensual' ? 'active' : ''}" data-group="frequency" data-value="mensual">mensual</button>
          <button type="button" class="pill ${freq === 'anual' ? 'active' : ''}" data-group="frequency" data-value="anual">anual</button>
        </div>
      </div>
      <label class="field field-monthly-day" style="${freq === 'anual' ? 'display:none' : ''}">
        <span class="lbl">Día del mes en que se cobra</span>
        <input name="billingDayMonthly" class="day-in" type="number" min="1" max="31" value="${item?.billingDay || 1}">
      </label>
      <div class="grid-2 field-yearly" style="${freq === 'anual' ? '' : 'display:none'}">
        <label class="field">
          <span class="lbl">Mes de cobro</span>
          <select name="billingMonth">
            ${MESES.map((m, i) => `<option value="${i+1}" ${(item?.billingMonth === i+1) ? 'selected' : ''}>${m}</option>`).join('')}
          </select>
        </label>
        <label class="field">
          <span class="lbl">Día</span>
          <input name="billingDayYearly" class="day-in" type="number" min="1" max="31" value="${item?.billingDay || 1}">
        </label>
      </div>
      <button type="submit" class="btn btn-block">Guardar ${I.chev}</button>
    </form>
  `;
}

function expFormHtml(item) {
  const recurring = item ? !!item.recurring : true;
  const today = new Date().toISOString().slice(0,10);
  return `
    <h3>${item ? 'Editar gasto' : 'Nuevo gasto'}</h3>
    <p class="hint">Renta, luz, internet, colegiatura…</p>
    <form>
      <input type="hidden" name="formType" value="exp">
      <input type="hidden" name="id" value="${item?.id || ''}">
      <input type="hidden" name="recurring" value="${recurring}">
      <label class="field">
        <span class="lbl">Concepto</span>
        <input name="name" value="${escapeHtml(item?.name || '')}" placeholder="Renta" required>
      </label>
      <label class="field">
        <span class="lbl">Monto (MXN)</span>
        <div class="money-wrap">
          <span class="peso">$</span>
          <input name="amount" type="number" step="0.01" min="0" value="${item?.amount || ''}" placeholder="0.00" required>
        </div>
      </label>
      <div class="field">
        <span class="lbl">Tipo</span>
        <div class="pill-group">
          <button type="button" class="pill ${recurring ? 'active' : ''}" data-group="recurring" data-value="true">Recurrente</button>
          <button type="button" class="pill ${!recurring ? 'active' : ''}" data-group="recurring" data-value="false">Único</button>
        </div>
      </div>
      <label class="field field-exp-day" style="${recurring ? '' : 'display:none'}">
        <span class="lbl">Día del mes</span>
        <input name="day" class="day-in" type="number" min="1" max="31" value="${item?.day || 1}">
      </label>
      <label class="field field-exp-date" style="${recurring ? 'display:none' : ''}">
        <span class="lbl">Fecha</span>
        <input name="date" type="date" class="mono-in" value="${item?.date ? new Date(item.date).toISOString().slice(0,10) : today}">
      </label>
      <button type="submit" class="btn btn-block">Guardar ${I.chev}</button>
    </form>
  `;
}

function handleFormSubmit(form) {
  const data = Object.fromEntries(new FormData(form));
  if (data.formType === 'card') {
    const id = data.id || uid();
    const item = {
      id,
      name: data.name.trim(),
      lastFour: (data.lastFour || '').trim(),
      cutoffDay: Number(data.cutoffDay),
      paymentDay: Number(data.paymentDay),
      estimatedPayment: data.estimatedPayment ? Number(data.estimatedPayment) : null
    };
    if (data.id) state.cards = state.cards.map(c => c.id === id ? item : c);
    else state.cards.push(item);
  } else if (data.formType === 'sub') {
    const id = data.id || uid();
    const freq = data.frequency;
    const item = {
      id,
      name: data.name.trim(),
      amount: Number(data.amount),
      frequency: freq,
      billingDay: freq === 'anual' ? Number(data.billingDayYearly) : Number(data.billingDayMonthly),
      billingMonth: freq === 'anual' ? Number(data.billingMonth) : null
    };
    if (data.id) state.subs = state.subs.map(s => s.id === id ? item : s);
    else state.subs.push(item);
  } else if (data.formType === 'exp') {
    const id = data.id || uid();
    const recurring = data.recurring === 'true';
    const item = {
      id,
      name: data.name.trim(),
      amount: Number(data.amount),
      recurring,
      day: recurring ? Number(data.day) : null,
      date: recurring ? null : data.date
    };
    if (data.id) state.expenses = state.expenses.map(e => e.id === id ? item : e);
    else state.expenses.push(item);
  }
  save();
  closeModal();
  render();
}

function closeModal() {
  state.modal = null;
  renderModal();
}

/* ============== EVENT DELEGATION ============== */
document.addEventListener('click', (e) => {
  const target = e.target.closest('[data-action]');
  if (!target) return;
  const action = target.dataset.action;
  const type = target.dataset.type;
  const id = target.dataset.id;

  if (action === 'open-modal') {
    state.modal = { type };
    renderModal();
  } else if (action === 'close-modal') {
    closeModal();
  } else if (action === 'edit') {
    let item = null;
    if (type === 'card') item = state.cards.find(c => c.id === id);
    else if (type === 'sub') item = state.subs.find(s => s.id === id);
    else if (type === 'exp') item = state.expenses.find(x => x.id === id);
    if (item) {
      state.modal = { type, item };
      renderModal();
    }
  } else if (action === 'delete') {
    if (!confirm('¿Eliminar este registro?')) return;
    if (type === 'card') state.cards = state.cards.filter(c => c.id !== id);
    else if (type === 'sub') state.subs = state.subs.filter(s => s.id !== id);
    else if (type === 'exp') state.expenses = state.expenses.filter(x => x.id !== id);
    save();
    render();
  }
});

document.querySelectorAll('.tab').forEach(btn => {
  btn.addEventListener('click', () => {
    state.tab = btn.dataset.tab;
    render();
  });
});

/* ============== INIT ============== */
load();
render();
</script>

</body>
</html>/4bcf37b3-3e2d-4fcf-876d-177660655270