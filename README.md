
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Turni delle pulizie</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Kalam:wght@400;700&family=Work+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #263329;
    --bg-2: #2d3c31;
    --paper: #f4efe0;
    --paper-2: #ece5cf;
    --ink: #262b22;
    --ink-soft: #5b6355;
    --chalk: #f1ede1;
    --chalk-soft: #c7cdbd;
    --line: rgba(241,237,225,0.14);
    --line-strong: rgba(241,237,225,0.28);
    --today: #f4d35e;

    --lilly: #e6a3b6;
    --gio: #d8b23c;
    --leo: #5ba9c9;
    --heidy: #b98cce;
    --cami: #f0935a;

    --radius: 6px;
  }

  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:
      radial-gradient(ellipse at 20% -10%, rgba(255,255,255,0.05), transparent 45%),
      radial-gradient(ellipse at 90% 10%, rgba(255,255,255,0.035), transparent 40%),
      var(--bg);
    color:var(--chalk);
    font-family:'Work Sans', sans-serif;
    line-height:1.5;
    -webkit-font-smoothing:antialiased;
  }

  h1,h2,.display{
    font-family:'Kalam', cursive;
    font-weight:700;
    letter-spacing:0.2px;
  }

  a{color:inherit;}
  button{font-family:inherit;}

  .wrap{
    max-width:960px;
    margin:0 auto;
    padding:0 24px 96px;
  }

  /* ---------- HERO ---------- */
  .hero{
    padding:72px 0 40px;
    border-bottom:1px solid var(--line);
  }
  .hero h1{
    font-size:clamp(2.6rem, 6vw, 4.2rem);
    margin:0 0 18px;
    line-height:1.05;
    color:var(--chalk);
  }
  .hero p{
    max-width:52ch;
    color:var(--chalk-soft);
    font-size:1.05rem;
    margin:0 0 8px;
  }
  .hero .rule{
    color:var(--chalk-soft);
    font-size:0.95rem;
    margin-top:20px;
    border-top:1px dashed var(--line-strong);
    padding-top:18px;
  }

  /* ---------- LEGEND ---------- */
  .legend{
    display:flex;
    flex-wrap:wrap;
    gap:22px;
    margin-top:28px;
  }
  .legend-item{
    display:flex;
    align-items:center;
    gap:8px;
    color:var(--chalk-soft);
    font-size:0.9rem;
  }
  .legend-item svg{width:19px;height:19px;color:var(--chalk-soft);flex-shrink:0;}

  /* ---------- PEOPLE FILTER ---------- */
  .filter-section{
    padding:36px 0 28px;
    border-bottom:1px solid var(--line);
  }
  .filter-section h2{
    font-size:1.5rem;
    margin:0 0 4px;
  }
  .filter-hint{
    color:var(--chalk-soft);
    font-size:0.9rem;
    margin:0 0 18px;
  }
  .pills{
    display:flex;
    flex-wrap:wrap;
    gap:10px;
  }
  .pill{
    display:inline-flex;
    align-items:center;
    gap:9px;
    padding:9px 16px 9px 12px;
    border-radius:999px;
    border:1.5px solid var(--line-strong);
    background:transparent;
    color:var(--chalk);
    cursor:pointer;
    font-size:0.95rem;
    font-weight:500;
    transition:border-color .15s ease, background .15s ease, transform .1s ease;
  }
  .pill:hover{border-color:var(--chalk-soft);}
  .pill:active{transform:scale(0.97);}
  .pill .dot{
    width:11px;height:11px;border-radius:50%;
    background:var(--c);
    flex-shrink:0;
  }
  .pill.active{
    background:var(--paper);
    color:var(--ink);
    border-color:var(--paper);
  }
  .pill:focus-visible{outline:2px solid var(--today);outline-offset:2px;}
  .clear-btn{
    background:none;border:none;color:var(--chalk-soft);
    text-decoration:underline;font-size:0.85rem;cursor:pointer;
    margin-left:4px;padding:8px 4px;
  }
  .clear-btn:hover{color:var(--chalk);}

  /* ---------- THIS WEEK PANEL ---------- */
  .this-week{
    margin:28px 0 0;
    background:var(--paper);
    color:var(--ink);
    border-radius:var(--radius);
    padding:22px 24px;
    box-shadow: 0 10px 24px -14px rgba(0,0,0,0.55);
  }
  .this-week .tw-label{
    display:inline-flex;align-items:center;gap:6px;
    font-size:0.78rem;text-transform:none;
    color:#8a6b1f;
    font-weight:600;
    margin-bottom:10px;
  }
  .this-week .tw-label::before{
    content:"";width:7px;height:7px;border-radius:50%;
    background:var(--today);
    box-shadow:0 0 0 3px rgba(244,211,94,0.35);
  }
  .this-week .tw-range{
    font-family:'Kalam',cursive;
    font-size:1.4rem;
    margin:0 0 14px;
  }
  .tw-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(190px,1fr));
    gap:10px;
  }
  .tw-item{
    display:flex;align-items:center;gap:10px;
    padding:10px 12px;
    border-radius:5px;
    background:var(--paper-2);
    border-left:4px solid var(--c);
  }
  .tw-item svg{width:18px;height:18px;color:var(--ink-soft);flex-shrink:0;}
  .tw-item .tw-task{font-size:0.85rem;color:var(--ink-soft);display:block;}
  .tw-item .tw-person{font-weight:600;font-size:0.98rem;}

  /* ---------- MONTH NAV ---------- */
  .month-nav{
    position:sticky;
    top:0;
    z-index:5;
    background:var(--bg);
    padding:16px 0;
    margin-top:8px;
    display:flex;
    gap:8px;
    overflow-x:auto;
    border-bottom:1px solid var(--line);
  }
  .month-nav::-webkit-scrollbar{height:4px;}
  .month-nav-btn{
    flex-shrink:0;
    background:transparent;
    border:1px solid var(--line-strong);
    color:var(--chalk-soft);
    padding:6px 14px;
    border-radius:999px;
    font-size:0.85rem;
    cursor:pointer;
    white-space:nowrap;
    transition:border-color .15s, color .15s;
  }
  .month-nav-btn:hover{color:var(--chalk);border-color:var(--chalk-soft);}
  .month-nav-btn.current{color:var(--ink);background:var(--today);border-color:var(--today);}

  /* ---------- CALENDAR ---------- */
  .calendar{margin-top:20px;}
  .month-group{margin-bottom:6px;}
  .month-header{
    display:flex;align-items:baseline;gap:12px;
    width:100%;
    background:none;border:none;
    color:var(--chalk);
    cursor:pointer;
    padding:20px 0 14px;
    text-align:left;
  }
  .month-header h2{font-size:1.7rem;margin:0;}
  .month-header .count{color:var(--chalk-soft);font-size:0.85rem;}
  .month-header .chev{
    margin-left:auto;
    color:var(--chalk-soft);
    transition:transform .2s ease;
    font-size:1.1rem;
  }
  .month-group.collapsed .chev{transform:rotate(-90deg);}
  .month-group.collapsed .weeks{display:none;}

  .weeks{
    display:flex;
    flex-direction:column;
    gap:10px;
    padding-bottom:10px;
  }

  .week-card{
    background:var(--paper);
    border-radius:var(--radius);
    padding:16px 18px;
    display:grid;
    grid-template-columns:130px 1fr;
    gap:14px;
    align-items:start;
  }
  .week-card.current{
    box-shadow:0 0 0 2px var(--today);
  }
  .week-range{
    color:var(--ink-soft);
    font-size:0.88rem;
    font-weight:600;
    padding-top:9px;
  }
  .week-range .today-tag{
    display:block;
    margin-top:4px;
    font-size:0.72rem;
    color:#8a6b1f;
    font-weight:700;
  }
  .task-list{
    list-style:none;
    margin:0;padding:0;
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(200px,1fr));
    gap:8px;
  }
  .task{
    display:flex;
    align-items:center;
    gap:10px;
    padding:8px 10px;
    border-radius:5px;
    background:var(--paper-2);
    border-left:4px solid var(--c);
    color:var(--ink);
    transition:opacity .15s ease, box-shadow .15s ease;
  }
  .task svg{width:17px;height:17px;color:var(--ink-soft);flex-shrink:0;}
  .task .t-task{display:block;font-size:0.78rem;color:var(--ink-soft);}
  .task .t-person{font-weight:600;font-size:0.94rem;}

  .task.dim{opacity:0.32;}
  .task.match{box-shadow:0 0 0 2px var(--c);}

  /* ---------- BALANCE TABLE ---------- */
  .balance{
    margin-top:56px;
    padding-top:32px;
    border-top:1px solid var(--line);
  }
  .balance h2{font-size:1.5rem;margin:0 0 6px;}
  .balance p{color:var(--chalk-soft);font-size:0.9rem;margin:0 0 20px;max-width:60ch;}
  .balance-table{
    width:100%;
    border-collapse:collapse;
    background:var(--paper);
    border-radius:var(--radius);
    overflow:hidden;
    font-size:0.88rem;
  }
  .balance-table th, .balance-table td{
    padding:11px 12px;
    text-align:center;
    color:var(--ink);
    border-bottom:1px solid rgba(38,43,34,0.08);
  }
  .balance-table th{
    font-weight:600;
    color:var(--ink-soft);
    font-size:0.78rem;
  }
  .balance-table td:first-child, .balance-table th:first-child{
    text-align:left;
    font-weight:600;
  }
  .balance-table tr:last-child td{border-bottom:none;}
  .name-cell{display:flex;align-items:center;gap:8px;}
  .name-cell .dot{width:9px;height:9px;border-radius:50%;background:var(--c);}

  footer{
    margin-top:56px;
    padding-top:24px;
    border-top:1px solid var(--line);
    color:var(--chalk-soft);
    font-size:0.85rem;
  }

  @media (max-width:640px){
    .wrap{padding:0 16px 72px;}
    .hero{padding:48px 0 32px;}
    .week-card{grid-template-columns:1fr;}
    .week-range{padding-top:0;}
  }

  @media (prefers-reduced-motion: reduce){
    html{scroll-behavior:auto;}
    *{transition:none !important;}
  }
</style>
</head>
<body>

<div class="wrap">
  <section class="filter-section">
    <h2>Trova i tuoi turni</h2>
    <p class="filter-hint">Seleziona uno o più nomi: i compiti corrispondenti si illuminano in tutto il calendario.</p>
    <div class="pills" id="pills"></div>
  </section>

  <section class="this-week" id="this-week"></section>

  <nav class="month-nav" id="month-nav"></nav>

  <main class="calendar" id="calendar"></main>

  <section class="balance">
    <h2>Equilibrio dei turni</h2>
    <p>Quante volte tocca a ciascuno, da settembre 2026 a fine giugno 2027. Utile per controllare che nessuno faccia sempre la stessa cosa.</p>
    <table class="balance-table" id="balance-table"></table>
  </section>

  <footer>
    Calendario dal 7 settembre 2026 al 27 giugno 2027 (anno accademico). Le settimane iniziano di lunedì.
  </footer>

</div>

<script>
(function(){

  /* ---------------- DATA ---------------- */

  const PEOPLE = {
    lilly: { name:"Lilly", color:"var(--lilly)", group:"f" },
    gio:   { name:"Gio",   color:"var(--gio)",   group:"m" },
    leo:   { name:"Leo",   color:"var(--leo)",   group:"m" },
    heidy: { name:"Heidy", color:"var(--heidy)", group:"f" },
    cami:  { name:"Cami",  color:"var(--cami)",  group:"f" },
  };
  const BOYS = ["leo","gio"];
  const GIRLS = ["lilly","heidy","cami"];
  const ORDER = ["lilly","gio","leo","heidy","cami"];

  const ICONS = {
    aspirapolvere: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M5 20h4"/><path d="M9 20V9a3 3 0 0 1 3-3h1a3 3 0 0 1 3 3v2"/><circle cx="16" cy="15" r="3"/><path d="M16 12V6"/><path d="M13 4h6"/></svg>',
    spazzatura: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M4 7h16"/><path d="M9 7V4h6v3"/><path d="M6 7l1 13h10l1-13"/><path d="M10 11v6"/><path d="M14 11v6"/></svg>',
    cucina: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M4 11h16v3a5 5 0 0 1-5 5H9a5 5 0 0 1-5-5v-3z"/><path d="M2 11h2"/><path d="M20 11h2"/><path d="M9 8c0-1 1-1 1-2s-1-1-1-2"/><path d="M14 8c0-1 1-1 1-2s-1-1-1-2"/></svg>',
    bagno: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"><path d="M12 3s6 7 6 11a6 6 0 0 1-12 0c0-4 6-11 6-11z"/></svg>',
  };

  const TASK_TYPES = [
    { key:"aspirapolvere", label:"Aspirapolvere spazi comuni" },
    { key:"spazzatura", label:"Spazzatura" },
    { key:"cucina", label:"Cucina" },
    { key:"bagno-f", label:"Bagno (Lilly · Heidy · Cami)", icon:"bagno" },
    { key:"bagno-m", label:"Bagno (Leo · Gio)", icon:"bagno" },
  ];

  const MONTHS_IT = ["gennaio","febbraio","marzo","aprile","maggio","giugno","luglio","agosto","settembre","ottobre","novembre","dicembre"];
  const MONTHS_IT_SHORT = ["gen","feb","mar","apr","mag","giu","lug","ago","set","ott","nov","dic"];

  function addDays(d, n){ const r = new Date(d); r.setDate(r.getDate()+n); return r; }
  function cap(s){ return s.charAt(0).toUpperCase()+s.slice(1); }

  function firstMondayOnOrAfter(date){
    const d = new Date(date);
    const day = d.getDay();
    const diff = day===0 ? 1 : (day===1 ? 0 : 8-day);
    d.setDate(d.getDate()+diff);
    d.setHours(0,0,0,0);
    return d;
  }

  const START = firstMondayOnOrAfter(new Date(2026,8,1));
  const END = new Date(2027,5,30);

  const weeks = [];
  { let cur = new Date(START); let idx=0;
    while(cur <= END){
      weeks.push({ index: idx, start: new Date(cur), end: addDays(cur,6) });
      cur = addDays(cur,7);
      idx++;
    }
  }

  function assignWeek(w){
    const bagnoM = BOYS[w % 2];
    const bagnoF = GIRLS[w % 3];

    // Ruota l'ordine delle 5 persone ogni settimana, poi assegna i 3 compiti
    // comuni ai tre che quella settimana non sono di turno in bagno.
    // Questo garantisce che, sul lungo periodo, ognuno faccia tutte e tre
    // le mansioni comuni in modo equilibrato (non solo una o due).
    const rotated = ORDER.map((_, k) => ORDER[(k + w) % ORDER.length]);
    const remaining3 = rotated.filter(p => p !== bagnoM && p !== bagnoF);
    const tasks3 = ["cucina", "aspirapolvere", "spazzatura"];
    const map3 = {};
    remaining3.forEach((person, i) => { map3[person] = tasks3[i]; });

    const assignment = { "bagno-f": bagnoF, "bagno-m": bagnoM };
    remaining3.forEach(person => { assignment[map3[person]] = person; });
    return assignment;
  }

  weeks.forEach(w => { w.assignment = assignWeek(w.index); });

  function formatRange(start, end){
    const sD = start.getDate(), eD = end.getDate();
    const sM = start.getMonth(), eM = end.getMonth();
    if(sM === eM){
      return `${sD}\u2013${eD} ${MONTHS_IT_SHORT[sM]}`;
    }
    return `${sD} ${MONTHS_IT_SHORT[sM]} \u2013 ${eD} ${MONTHS_IT_SHORT[eM]}`;
  }

  const today = new Date();
  today.setHours(0,0,0,0);
  let currentWeek = weeks.find(w => today >= w.start && today <= w.end);

  /* ---------------- STATE ---------------- */
  const selected = new Set();

  /* ---------------- RENDER: LEGEND ---------------- */
  const legendEl = document.getElementById('legend');
  legendEl.innerHTML = TASK_TYPES.slice(0,4).map(t => {
    const icon = ICONS[t.icon || t.key];
    const label = t.key === 'bagno-f' ? 'Bagno' : t.label;
    return `<div class="legend-item">${icon}<span>${label}</span></div>`;
  }).join('');

  /* ---------------- RENDER: PILLS ---------------- */
  const pillsEl = document.getElementById('pills');
  function renderPills(){
    pillsEl.innerHTML = Object.keys(PEOPLE).map(id => {
      const p = PEOPLE[id];
      const active = selected.has(id) ? 'active' : '';
      return `<button class="pill ${active}" data-id="${id}" style="--c:${p.color}" aria-pressed="${selected.has(id)}">
        <span class="dot"></span>${p.name}
      </button>`;
    }).join('') + `<button class="clear-btn" id="clear-btn">azzera selezione</button>`;

    pillsEl.querySelectorAll('.pill').forEach(btn => {
      btn.addEventListener('click', () => {
        const id = btn.dataset.id;
        if(selected.has(id)) selected.delete(id); else selected.add(id);
        renderPills();
        applyHighlight();
        renderThisWeek();
      });
    });
    const clearBtn = document.getElementById('clear-btn');
    if(clearBtn){
      clearBtn.addEventListener('click', () => {
        selected.clear();
        renderPills();
        applyHighlight();
        renderThisWeek();
      });
    }
  }
  renderPills();

  /* ---------------- RENDER: THIS WEEK ---------------- */
  const thisWeekEl = document.getElementById('this-week');
  function renderThisWeek(){
    if(!currentWeek){
      thisWeekEl.style.display = 'none';
      return;
    }
    const a = currentWeek.assignment;
    const items = TASK_TYPES.map(t => {
      const personId = a[t.key];
      const p = PEOPLE[personId];
      const label = t.key.startsWith('bagno') ? 'Bagno' : t.label;
      const isMatch = selected.size === 0 || selected.has(personId);
      return `<div class="tw-item" style="--c:${p.color}; ${isMatch ? '' : 'opacity:0.4'}">
        ${ICONS[t.icon || t.key]}
        <span>
          <span class="tw-task">${label}</span>
          <span class="tw-person">${p.name}</span>
        </span>
      </div>`;
    }).join('');

    thisWeekEl.innerHTML = `
      <div class="tw-label">Questa settimana</div>
      <div class="tw-range">${formatRange(currentWeek.start, currentWeek.end)} ${currentWeek.start.getFullYear()}</div>
      <div class="tw-grid">${items}</div>
    `;
  }
  renderThisWeek();

  /* ---------------- RENDER: MONTH NAV + CALENDAR ---------------- */
  const monthNavEl = document.getElementById('month-nav');
  const calendarEl = document.getElementById('calendar');

  const monthGroups = [];
  { const map = new Map();
    weeks.forEach(w => {
      const key = `${w.start.getFullYear()}-${w.start.getMonth()}`;
      if(!map.has(key)){
        map.set(key, { key, year:w.start.getFullYear(), month:w.start.getMonth(), weeks:[] });
        monthGroups.push(map.get(key));
      }
      map.get(key).weeks.push(w);
    });
  }

  const currentMonthKey = currentWeek ? `${currentWeek.start.getFullYear()}-${currentWeek.start.getMonth()}` : null;

  monthNavEl.innerHTML = monthGroups.map(mg => {
    const cur = mg.key === currentMonthKey ? 'current' : '';
    return `<button class="month-nav-btn ${cur}" data-target="month-${mg.key}">${cap(MONTHS_IT_SHORT[mg.month])} ${mg.year}</button>`;
  }).join('');

  function weekCardHTML(w){
    const isCurrent = currentWeek && w.index === currentWeek.index;
    const tasksHTML = TASK_TYPES.map(t => {
      const personId = w.assignment[t.key];
      const p = PEOPLE[personId];
      const label = t.key.startsWith('bagno') ? 'Bagno' : t.label;
      return `<li class="task" data-person="${personId}" style="--c:${p.color}">
        ${ICONS[t.icon || t.key]}
        <span>
          <span class="t-task">${label}</span>
          <span class="t-person">${p.name}</span>
        </span>
      </li>`;
    }).join('');

    return `<article class="week-card ${isCurrent ? 'current' : ''}">
      <div class="week-range">${formatRange(w.start, w.end)}${isCurrent ? '<span class="today-tag">Questa settimana</span>' : ''}</div>
      <ul class="task-list">${tasksHTML}</ul>
    </article>`;
  }

  calendarEl.innerHTML = monthGroups.map(mg => {
    const collapsed = mg.key === currentMonthKey ? '' : 'collapsed';
    return `<section class="month-group ${collapsed}" id="month-${mg.key}">
      <button class="month-header" data-key="${mg.key}">
        <h2>${cap(MONTHS_IT[mg.month])} ${mg.year}</h2>
        <span class="count">${mg.weeks.length} settiman${mg.weeks.length===1?'a':'e'}</span>
        <span class="chev">&#9662;</span>
      </button>
      <div class="weeks">${mg.weeks.map(weekCardHTML).join('')}</div>
    </section>`;
  }).join('');

  calendarEl.querySelectorAll('.month-header').forEach(btn => {
    btn.addEventListener('click', () => {
      btn.closest('.month-group').classList.toggle('collapsed');
    });
  });

  monthNavEl.querySelectorAll('.month-nav-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      const target = document.getElementById(btn.dataset.target);
      target.classList.remove('collapsed');
      target.scrollIntoView({ behavior:'smooth', block:'start' });
    });
  });

  /* ---------------- HIGHLIGHT LOGIC ---------------- */
  function applyHighlight(){
    const tasks = calendarEl.querySelectorAll('.task');
    tasks.forEach(el => {
      const person = el.dataset.person;
      el.classList.remove('dim','match');
      if(selected.size === 0) return;
      if(selected.has(person)) el.classList.add('match');
      else el.classList.add('dim');
    });
  }
  applyHighlight();

  /* ---------------- BALANCE TABLE ---------------- */
  const balanceEl = document.getElementById('balance-table');
  function renderBalance(){
    const counts = {};
    Object.keys(PEOPLE).forEach(id => counts[id] = { aspirapolvere:0, spazzatura:0, cucina:0, bagno:0 });
    weeks.forEach(w => {
      Object.entries(w.assignment).forEach(([taskKey, personId]) => {
        if(taskKey.startsWith('bagno')) counts[personId].bagno++;
        else counts[personId][taskKey]++;
      });
    });

    const rows = Object.keys(PEOPLE).map(id => {
      const p = PEOPLE[id];
      const c = counts[id];
      const total = c.aspirapolvere + c.spazzatura + c.cucina + c.bagno;
      return `<tr>
        <td><div class="name-cell"><span class="dot" style="--c:${p.color}"></span>${p.name}</div></td>
        <td>${c.aspirapolvere}</td>
        <td>${c.spazzatura}</td>
        <td>${c.cucina}</td>
        <td>${c.bagno}</td>
        <td><strong>${total}</strong></td>
      </tr>`;
    }).join('');

    balanceEl.innerHTML = `
      <thead>
        <tr>
          <th>Persona</th>
          <th>Aspirapolvere</th>
          <th>Spazzatura</th>
          <th>Cucina</th>
          <th>Bagno</th>
          <th>Totale</th>
        </tr>
      </thead>
      <tbody>${rows}</tbody>
    `;
  }
  renderBalance();

})();
</script>

</body>
</html>
