<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Techquip</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,400..800&family=Instrument+Sans:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap">
<style>
/* Layout: asymmetric editorial desk. Left-aligned display type beside a generated silicon wafer, then a filterable news desk, a chip ledger with a to-scale chart, two calculators and an event calendar. */
:root{
  --bg:#eceff3; --surface:#f8f9fb; --surface-2:#e1e6ee; --ink:#0a1020; --muted:#556071; --line:#c7cedb;
  --accent:#2540e8; --accent-ink:#ffffff; --good:#0f7a4d; --warn:#9a5b00;
  --art-a:#2540e8; --art-b:#00857f; --art-c:#c2185b;
  --display:'Bricolage Grotesque','Helvetica Neue',Arial,sans-serif;
  --body:'Instrument Sans','Helvetica Neue',Arial,sans-serif;
  --mono:'JetBrains Mono',ui-monospace,Menlo,Consolas,monospace;
  --s1:.25rem; --s2:.5rem; --s3:.75rem; --s4:1rem; --s5:1.5rem; --s6:2.5rem; --s7:4.5rem;
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --bg:#080b12; --surface:#0f1420; --surface-2:#171e2d; --ink:#e7eaf2; --muted:#8b95a8; --line:#232c3e;
    --accent:#8aa0ff; --accent-ink:#080b12; --good:#4fd39a; --warn:#e5a94a;
    --art-a:#8aa0ff; --art-b:#37d4c8; --art-c:#ff7ab8; color-scheme:dark;
  }
}
:root[data-theme="dark"]{
  --bg:#080b12; --surface:#0f1420; --surface-2:#171e2d; --ink:#e7eaf2; --muted:#8b95a8; --line:#232c3e;
  --accent:#8aa0ff; --accent-ink:#080b12; --good:#4fd39a; --warn:#e5a94a;
  --art-a:#8aa0ff; --art-b:#37d4c8; --art-c:#ff7ab8; color-scheme:dark;
}
*,*::before,*::after{box-sizing:border-box}
html{scroll-behavior:smooth;scroll-padding-top:5rem}
body{background:var(--bg);color:var(--ink);font-family:var(--body);font-size:1rem;line-height:1.55;
  padding-block:0 4rem;padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px))}
a{color:inherit}
button,input,select{font:inherit;color:inherit}
:focus-visible{outline:2px solid var(--accent);outline-offset:2px}
.wrap{max-width:1200px;margin:0 auto}
h1,h2,h3{font-family:var(--display);text-wrap:balance;margin:0;letter-spacing:-.02em;line-height:1.08}
p{margin:0}
.mono{font-family:var(--mono)}
.eyebrow{font-family:var(--mono);font-size:.72rem;letter-spacing:.12em;text-transform:uppercase;color:var(--muted)}

/* nav */
.nav{position:sticky;top:env(safe-area-inset-top,0px);z-index:20;background:var(--bg);
  background:color-mix(in srgb,var(--bg) 90%,transparent);-webkit-backdrop-filter:blur(10px);backdrop-filter:blur(10px);
  border-bottom:1px solid var(--line)}
.nav-in{display:flex;align-items:center;gap:var(--s5);padding-block:.7rem;flex-wrap:wrap}
.brand{display:flex;align-items:center;gap:.6rem;font-family:var(--display);font-weight:700;font-size:1.25rem;letter-spacing:-.02em;text-decoration:none}
.brand svg{width:26px;height:26px}
.links{display:flex;gap:var(--s4);margin-left:auto;flex-wrap:wrap}
.links a{font-size:.9rem;text-decoration:none;color:var(--muted);padding:.25rem 0}
.links a:hover{color:var(--ink)}
.tools{display:flex;gap:var(--s2)}
.btn{border:1px solid var(--line);background:var(--surface);border-radius:4px;padding:.4rem .75rem;cursor:pointer;font-size:.85rem;display:inline-flex;align-items:center;gap:.5rem}
.btn:hover{border-color:var(--accent)}
.btn.primary{background:var(--accent);color:var(--accent-ink);border-color:var(--accent);font-weight:600}
kbd{font-family:var(--mono);font-size:.7rem;border:1px solid var(--line);border-radius:3px;padding:.05rem .35rem;color:var(--muted)}
.progress{height:3px;background:transparent}
.progress i{display:block;height:100%;width:0;background:var(--accent)}

/* hero */
.hero{display:grid;grid-template-columns:1.15fr .85fr;gap:var(--s6);align-items:center;padding-block:var(--s6) var(--s5)}
.hero > *{min-width:0}
.hero h1{font-size:clamp(2.5rem,6.4vw,5rem);font-weight:700;margin-block:var(--s4) var(--s5)}
.hero h1 em{font-style:normal;color:var(--accent)}
.lede{font-size:1.15rem;color:var(--muted);max-width:34rem}
.hero-cta{display:flex;gap:var(--s3);flex-wrap:wrap;margin-top:var(--s5)}
.hero-cta .btn{padding:.65rem 1.1rem;font-size:.95rem}
.wafer-box{display:flex;flex-direction:column;gap:var(--s3)}
#wafer{width:100%;aspect-ratio:1/1;max-width:100%;display:block;cursor:crosshair}
.caption{font-size:.78rem;color:var(--muted);max-width:30rem}

/* ticker */
.ticker{border-block:1px solid var(--line);overflow:hidden;white-space:nowrap;padding-block:.6rem;margin-block:var(--s5) 0}
.ticker-track{display:inline-flex;gap:var(--s6);animation:slide 70s linear infinite;padding-right:var(--s6)}
.ticker:hover .ticker-track{animation-play-state:paused}
.ticker a{font-size:.88rem;text-decoration:none;display:inline-flex;gap:.6rem;align-items:baseline}
.ticker a b{font-family:var(--mono);font-size:.68rem;letter-spacing:.1em;text-transform:uppercase;color:var(--accent);font-weight:500}
@keyframes slide{to{transform:translateX(-50%)}}

section{padding-block:var(--s7) 0}
.sec-head{display:flex;justify-content:space-between;align-items:end;gap:var(--s5);flex-wrap:wrap;margin-bottom:var(--s5)}
.sec-head h2{font-size:clamp(1.8rem,4vw,2.8rem);margin-top:var(--s2)}
.sec-head p{max-width:30rem;color:var(--muted)}

/* news */
.controls{display:flex;gap:var(--s3);flex-wrap:wrap;align-items:center;margin-bottom:var(--s5)}
.chips{display:flex;gap:var(--s2);flex-wrap:wrap}
.chip{border:1px solid var(--line);background:transparent;border-radius:999px;padding:.35rem .85rem;font-size:.85rem;cursor:pointer}
.chip[aria-pressed="true"]{background:var(--ink);color:var(--bg);border-color:var(--ink)}
.field{border:1px solid var(--line);background:var(--surface);border-radius:4px;padding:.45rem .7rem;min-width:0}
.controls .spacer{flex:1 1 40px}
.grid{display:grid;gap:var(--s5);grid-template-columns:repeat(3,minmax(0,1fr))}
@media (max-width:980px){.grid{grid-template-columns:repeat(2,minmax(0,1fr))}}
@media (max-width:620px){.grid{grid-template-columns:minmax(0,1fr)}}
.card{background:var(--surface);border:1px solid var(--line);border-radius:6px;overflow:hidden;display:flex;flex-direction:column;min-width:0}
.card canvas{width:100%;aspect-ratio:16/9;display:block;background:var(--surface-2)}
.card-body{padding:var(--s4);display:flex;flex-direction:column;gap:var(--s3);flex:1;min-width:0}
.meta{display:flex;gap:var(--s3);align-items:center;flex-wrap:wrap}
.desk{font-family:var(--mono);font-size:.68rem;letter-spacing:.12em;text-transform:uppercase;color:var(--accent)}
.date{font-family:var(--mono);font-size:.72rem;color:var(--muted)}
.flag{font-family:var(--mono);font-size:.64rem;letter-spacing:.08em;text-transform:uppercase;border:1px solid var(--warn);color:var(--warn);border-radius:3px;padding:.05rem .4rem}
.following{font-family:var(--mono);font-size:.64rem;letter-spacing:.08em;text-transform:uppercase;border:1px solid var(--good);color:var(--good);border-radius:3px;padding:.05rem .4rem}
.card h3{font-size:1.2rem;line-height:1.2}
.card .sum{color:var(--muted);font-size:.93rem}
.why{font-size:.9rem;border-left:2px solid var(--accent);padding-left:var(--s3)}
.card-foot{margin-top:auto;display:flex;gap:var(--s3);align-items:center;justify-content:space-between;flex-wrap:wrap;padding-top:var(--s2)}
.card-foot a{font-size:.85rem}
.mini{border:0;background:transparent;cursor:pointer;font-size:.85rem;color:var(--muted);padding:.2rem 0}
.mini:hover{color:var(--ink)}
.mini[aria-pressed="true"]{color:var(--accent);font-weight:600}
.lead{grid-column:1/-1;flex-direction:row}
.lead canvas{width:46%;aspect-ratio:auto;min-height:260px;flex:none}
.lead h3{font-size:clamp(1.5rem,3vw,2.2rem)}
@media (max-width:760px){.lead{flex-direction:column}.lead canvas{width:100%;aspect-ratio:16/9;min-height:0}}
.card.pulse{animation:pulse 1.6s ease}
@keyframes pulse{0%,100%{box-shadow:0 0 0 0 transparent}30%{box-shadow:0 0 0 3px var(--accent)}}
.empty{grid-column:1/-1;border:1px dashed var(--line);border-radius:6px;padding:var(--s6);text-align:center;color:var(--muted)}

.band{display:block;width:100%;height:clamp(90px,14vw,150px);max-width:100%;border-radius:6px;margin-bottom:var(--s5);background:var(--surface-2)}
/* ledger */
.split{display:grid;grid-template-columns:1.2fr .8fr;gap:var(--s6);align-items:start}
.split > *{min-width:0}
@media (max-width:900px){.split{grid-template-columns:minmax(0,1fr)}}
.panel{border:1px solid var(--line);border-radius:6px;background:var(--surface);padding:var(--s5)}
.panel h3{font-size:1.25rem;margin-bottom:var(--s3)}
.chart-scroll{overflow-x:auto}
svg.chart{width:100%;min-width:420px;height:auto;display:block}
.chart .ax{stroke:var(--line);stroke-width:1}
.chart .tick{fill:var(--muted);font:11px var(--mono)}
.chart .lab{fill:var(--ink);font:12px var(--mono)}
.chart .grp{fill:var(--ink);font:600 13px var(--body)}
.chart .b-act{fill:var(--accent)}
.chart .b-gd{fill:none;stroke:var(--accent);stroke-width:2;stroke-dasharray:5 3}
.legend{display:flex;gap:var(--s5);font-size:.82rem;color:var(--muted);flex-wrap:wrap;margin-top:var(--s3)}
.legend i{display:inline-block;width:12px;height:12px;margin-right:.4rem;vertical-align:-1px}
.legend .a{background:var(--accent)}
.legend .g{border:2px dashed var(--accent)}
.facts{display:flex;flex-direction:column;gap:var(--s4);list-style:none;margin:0;padding:0}
.facts li{display:flex;flex-direction:column;gap:.2rem;padding-bottom:var(--s4);border-bottom:1px solid var(--line)}
.facts li:last-child{border:0;padding-bottom:0}
.facts b{font-family:var(--display);font-size:1.05rem}
.facts span{color:var(--muted);font-size:.9rem}

/* calculators */
.calc-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:var(--s5)}
@media (max-width:900px){.calc-grid{grid-template-columns:minmax(0,1fr)}}
.form{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:var(--s3);margin-block:var(--s4)}
.form label{display:flex;flex-direction:column;gap:.3rem;font-size:.8rem;color:var(--muted)}
.form input{width:100%}
.out{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:var(--s4);border-top:1px solid var(--line);padding-top:var(--s4)}
.out div{display:flex;flex-direction:column;gap:.2rem;min-width:0}
.out small{font-family:var(--mono);font-size:.66rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted)}
.out strong{font-family:var(--display);font-size:1.5rem;font-variant-numeric:tabular-nums;overflow-wrap:anywhere}
.note{font-size:.78rem;color:var(--muted)}

/* calendar */
.cal{list-style:none;margin:0;padding:0;border-top:1px solid var(--line)}
.cal li{display:grid;grid-template-columns:9rem minmax(0,1fr) auto;gap:var(--s4);padding-block:var(--s4);border-bottom:1px solid var(--line);align-items:baseline}
.cal .when{font-family:var(--mono);font-size:.85rem}
.cal h3{font-size:1.1rem}
.cal .where{color:var(--muted);font-size:.88rem}
.cal .cd{font-family:var(--mono);font-size:.8rem;border:1px solid var(--line);border-radius:999px;padding:.2rem .7rem;white-space:nowrap;font-variant-numeric:tabular-nums}
.cal .cd.soon{border-color:var(--accent);color:var(--accent)}
@media (max-width:640px){.cal li{grid-template-columns:minmax(0,1fr)}.cal .cd{justify-self:start}}

/* follow */
.follow{display:flex;gap:var(--s5);flex-wrap:wrap;align-items:center}
.follow p{max-width:32rem;color:var(--muted)}

footer{margin-top:var(--s7);border-top:1px solid var(--line);padding-top:var(--s5);font-size:.85rem;color:var(--muted)}
footer ul{columns:2 280px;list-style:none;margin:var(--s3) 0 var(--s4);padding:0;gap:var(--s5)}
footer li{break-inside:avoid;padding-block:.15rem;overflow-wrap:anywhere}

/* palette */
.pal{position:fixed;inset:0;z-index:50;background:rgba(5,8,14,.55);display:flex;justify-content:center;align-items:flex-start;
  padding:max(12vh,env(safe-area-inset-top,0px)) max(16px,env(safe-area-inset-right,0px)) 16px max(16px,env(safe-area-inset-left,0px))}
.pal-box{width:100%;max-width:560px;background:var(--surface);border:1px solid var(--line);border-radius:8px;overflow:hidden}
.pal-box input{width:100%;border:0;border-bottom:1px solid var(--line);background:transparent;padding:1rem;font-size:1rem}
.pal-box input:focus-visible{outline:none}
.pal-box ul{list-style:none;margin:0;padding:.4rem;max-height:50vh;overflow:auto}
.pal-box li{display:flex;justify-content:space-between;gap:var(--s3);padding:.55rem .7rem;border-radius:4px;cursor:pointer;font-size:.92rem}
.pal-box li small{font-family:var(--mono);font-size:.68rem;color:var(--muted);text-transform:uppercase;letter-spacing:.08em;flex:none}
.pal-box li[aria-selected="true"]{background:var(--surface-2)}
.toast{position:fixed;left:50%;transform:translateX(-50%);bottom:calc(1.2rem + env(safe-area-inset-bottom,0px));background:var(--ink);color:var(--bg);padding:.55rem 1rem;border-radius:4px;font-size:.85rem;z-index:60}

@media (max-width:900px){.hero{grid-template-columns:minmax(0,1fr)}.wafer-box{max-width:460px}.links{display:none}.tools{margin-left:auto}}
@media (prefers-reduced-motion:reduce){html{scroll-behavior:auto}.ticker-track{animation:none;flex-wrap:wrap;white-space:normal}.ticker{white-space:normal}.card.pulse{animation:none}}
</style>
<style>:root{color-scheme:light}body{margin:0}img{max-width:100%}[hidden]{display:none!important}</style>
</head>
<body>

<div class="nav">
  <div class="wrap">
    <div class="nav-in">
      <a class="brand" href="#top" aria-label="Techquip home">
        <svg viewBox="0 0 32 32" aria-hidden="true"><circle cx="16" cy="16" r="14" fill="none" stroke="currentColor" stroke-width="2"/><g fill="var(--accent)"><rect x="9" y="9" width="6" height="6"/><rect x="17" y="9" width="6" height="6" opacity=".6"/><rect x="9" y="17" width="6" height="6" opacity=".6"/><rect x="17" y="17" width="6" height="6" opacity=".3"/></g></svg>
        Techquip
      </a>
      <nav class="links" aria-label="Sections">
        <a href="#news">News desk</a><a href="#ledger">Chip ledger</a><a href="#tools">Calculators</a><a href="#calendar">Calendar</a><a href="#follow">Follow</a>
      </nav>
      <div class="tools">
        <button class="btn" id="open-pal" type="button" aria-label="Open search and commands">Search <kbd>Ctrl K</kbd></button>
        <button class="btn" id="theme" type="button" aria-label="Switch colour theme">Theme</button>
      </div>
    </div>
  </div>
  <div class="progress" aria-hidden="true"><i id="bar"></i></div>
</div>

<main class="wrap" id="top">
  <header class="hero">
    <div>
      <p class="eyebrow" id="edition">Edition of Thursday 15 October 2026</p>
      <h1>The silicon behind the <em>intelligence</em>.</h1>
      <p class="lede">A daily desk for AI, semiconductors, robotics and space. Sourced headlines, a chart drawn to scale, working calculators and a calendar that counts down for you.</p>
      <div class="hero-cta">
        <a class="btn primary" href="#news">Read the desk</a>
        <button class="btn" type="button" id="cta-pal">Jump to anything</button>
      </div>
    </div>
    <div class="wafer-box">
      <canvas id="wafer" aria-label="Generated artwork of a silicon wafer. Each die is tinted like a thin film and brightens as the pointer passes over it." role="img"></canvas>
      <p class="caption">Original artwork, generated in your browser. Each die takes the colour a thin film reflects. Move across it.</p>
    </div>
  </header>

  <div class="ticker" aria-label="Latest headlines"><div class="ticker-track" id="ticker"></div></div>

  <section id="news">
    <div class="sec-head">
      <div><p class="eyebrow">News desk</p><h2>Fourteen stories, four desks</h2></div>
      <p>Each item is paraphrased from the linked source. Cards marked in amber rest on a single secondary source or on a headline alone.</p>
    </div>
    <div class="controls">
      <div class="chips" id="chips" role="group" aria-label="Filter by desk"></div>
      <span class="spacer"></span>
      <input class="field" id="q" type="search" placeholder="Search stories" aria-label="Search stories">
      <select class="field" id="sort" aria-label="Sort stories">
        <option value="new">Newest first</option>
        <option value="mine">My desks first</option>
        <option value="desk">By desk</option>
      </select>
    </div>
    <div class="grid" id="grid" aria-live="polite"></div>
  </section>

  <section id="ledger">
    <div class="sec-head">
      <div><p class="eyebrow">Chip ledger</p><h2>Where the money for AI hardware is landing</h2></div>
      <p>Broadcom's September report, drawn to one scale, with the other supply-chain signals from the past two months.</p>
    </div>
    <canvas class="band" data-cover="band-ledger" data-desk="Chips" aria-hidden="true"></canvas>
    <div class="split">
      <div class="panel">
        <h3>Broadcom, fiscal Q3 2026 and Q4 guidance</h3>
        <div class="chart-scroll"><svg class="chart" id="chart" viewBox="0 0 640 380" role="img" aria-label="Bar chart of Broadcom revenue in billions of dollars. Total revenue 29.6 in Q3 and 34.8 guided for Q4. AI semiconductor revenue 16.7 in Q3 and 21.7 guided for Q4."></svg></div>
        <div class="legend"><span><i class="a"></i>Reported, fiscal Q3 2026</span><span><i class="g"></i>Guidance, fiscal Q4 2026</span></div>
        <p class="note" id="chart-note" style="margin-top:.75rem"></p>
      </div>
      <ul class="facts panel" aria-label="Supply chain signals">
        <li><b>Intel 18A is yielding ahead of plan</b><span>Intel said 18A yields beat its internal milestones and that the 14A 0.9 design kit is still expected this month.</span></li>
        <li><b>AMD's MI455X gets specific</b><span>Hot Chips detail: 432 GB of HBM4 per GPU, 72 GPUs in a rack.</span></li>
        <li><b>Japan's tool makers keep climbing</b><span>July three-month billings reached ¥556.22 billion, up 35.4% on a year earlier.</span></li>
        <li><b>2 nm is spoken for</b><span>TSMC's 2 nm capacity is reported sold out well into the first half of 2027.</span></li>
      </ul>
    </div>
  </section>

  <section id="tools">
    <div class="sec-head">
      <div><p class="eyebrow">Calculators</p><h2>Put numbers on it</h2></div>
      <p>Both tools run in your browser. Change any value and the result updates at once.</p>
    </div>
    <canvas class="band" data-cover="band-tools" data-desk="AI" aria-hidden="true"></canvas>
    <div class="calc-grid">
      <div class="panel">
        <h3>Inference budget</h3>
        <p class="note">Estimate a monthly bill from traffic and token price. The price below is an example. Enter your provider's rate.</p>
        <div class="form">
          <label for="c-req">Requests per day<input class="field" id="c-req" type="number" min="0" step="100" value="20000"></label>
          <label for="c-tok">Tokens per request<input class="field" id="c-tok" type="number" min="0" step="50" value="1500"></label>
          <label for="c-price">Price per 1M tokens (USD)<input class="field" id="c-price" type="number" min="0" step="0.1" value="2"></label>
          <label for="c-days">Days in period<input class="field" id="c-days" type="number" min="1" max="366" step="1" value="30"></label>
        </div>
        <div class="out">
          <div><small>Tokens per day</small><strong id="o-tpd">-</strong></div>
          <div><small>Tokens per period</small><strong id="o-tpp">-</strong></div>
          <div><small>Cost per period</small><strong id="o-cost">-</strong></div>
          <div><small>Cost per 1,000 requests</small><strong id="o-k">-</strong></div>
        </div>
      </div>
      <div class="panel">
        <h3>Node shift</h3>
        <p class="note">Applies the figures a 2026 industry report gives for TSMC's sub-2 nm process: 30% more transistors in the same area, 25% less power. Real products vary.</p>
        <div class="form">
          <label for="n-tr">Transistors today (billions)<input class="field" id="n-tr" type="number" min="0" step="1" value="20"></label>
          <label for="n-pw">Power today (watts)<input class="field" id="n-pw" type="number" min="0" step="1" value="45"></label>
          <label for="n-up">Density gain (%)<input class="field" id="n-up" type="number" min="0" step="1" value="30"></label>
          <label for="n-dn">Power cut (%)<input class="field" id="n-dn" type="number" min="0" max="100" step="1" value="25"></label>
        </div>
        <div class="out">
          <div><small>Transistors, same area</small><strong id="o-tr">-</strong></div>
          <div><small>Power, same design</small><strong id="o-pw">-</strong></div>
          <div><small>Watts saved</small><strong id="o-sv">-</strong></div>
          <div><small>Transistors per watt</small><strong id="o-eff">-</strong></div>
        </div>
      </div>
    </div>
  </section>

  <section id="calendar">
    <div class="sec-head">
      <div><p class="eyebrow">Calendar</p><h2>What lands next</h2></div>
      <p>Countdowns are calculated from today's date on your device. Items marked expected come from press reports, not company announcements.</p>
    </div>
    <canvas class="band" data-cover="band-cal" data-desk="Space" aria-hidden="true"></canvas>
    <ul class="cal" id="cal"></ul>
  </section>

  <section id="follow">
    <div class="sec-head">
      <div><p class="eyebrow">Follow</p><h2>Choose your desks</h2></div>
    </div>
    <canvas class="band" data-cover="band-follow" data-desk="Robotics" aria-hidden="true"></canvas>
    <div class="panel follow">
      <p>Pick the desks you care about. Their stories get a Following mark and move to the top when you sort by My desks first. Choices stay in this browser.</p>
      <div class="chips" id="follow-chips" role="group" aria-label="Desks to follow"></div>
    </div>
  </section>

  <footer>
    <p><strong>Sources.</strong> Reported as of 15 October 2026. Summaries are in our own words; open the source for the original.</p>
    <ul id="sources"></ul>
    <p>Every image on this page is original artwork drawn in your browser from code: one illustration per story, a generated banner for each section, and the wafer in the header. No photographs or third-party images are used. Quantum computing is not covered yet: the searches run for this edition returned no current, verifiable items.</p>
  </footer>
</main>

<div class="pal" id="pal" hidden role="dialog" aria-modal="true" aria-label="Search and commands">
  <div class="pal-box">
    <input id="pal-q" type="text" placeholder="Search stories, sections, actions" autocomplete="off" aria-label="Search stories, sections and actions">
    <ul id="pal-list" role="listbox"></ul>
  </div>
</div>
<div class="toast" id="toast" hidden></div>

<script>
(function(){
'use strict';
var $=function(s,r){return (r||document).querySelector(s)};
var $$=function(s,r){return Array.prototype.slice.call((r||document).querySelectorAll(s))};
var esc=function(s){return String(s).replace(/[&<>"']/g,function(c){return {'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]})};
var css=function(v){return getComputedStyle(document.documentElement).getPropertyValue(v).trim()};
var store={get:function(k,d){try{var v=localStorage.getItem(k);return v==null?d:JSON.parse(v)}catch(e){return d}},set:function(k,v){try{localStorage.setItem(k,JSON.stringify(v))}catch(e){}}};
var reduce=window.matchMedia&&matchMedia('(prefers-reduced-motion: reduce)').matches;
var isDark=function(){var t=document.documentElement.getAttribute('data-theme');return t?t==='dark':matchMedia('(prefers-color-scheme: dark)').matches};

var DESKS=['AI','Chips','Robotics','Space'];
var NEWS=[
{id:'n1',desk:'AI',date:'2026-10-06',title:'A reported pile-up of AI launches on 6 October',sum:'A community roundup lists a shared agent protocol from Meta, Stripe and Shopify, a new decisions API from OpenAI, and a trillion-parameter model from Mistral said to be heading toward open weights.',why:'If the agent protocol is adopted, checkout and assistant flows could share one standard. Treat the list as unconfirmed until each company posts its own notes.',src:'Digg',url:'https://digg.com/ai/qyieg39r',flag:'Single source'},
{id:'n2',desk:'AI',date:'2026-10-01',dlabel:'October outlook',title:'OpenAI shifts its October plans as Meta readies agents',sum:'An earlier-reported OpenAI model called GPT-6.1 Astra is no longer expected to launch as first described. Meta is reportedly building a consumer agent platform called Hatch and a flagship model codenamed Watermelon. Google has set no date for Gemini 4.',why:'The pattern across labs is the same: agents are the product, and model launches are the supporting act.',src:'The Hans India',url:'https://www.thehansindia.com/tech/upcoming-ai-updates-in-october-2026-major-developments-to-watch-1127036',flag:'Reported'},
{id:'n3',desk:'AI',date:'2026-10-01',dlabel:'October outlook',title:'Siri\'s AI expansion is tipped for iOS 27.1 and 27.2',sum:'9to5Mac expects both point releases to ship before the end of October, widening Apple\'s Siri AI features.',why:'Point releases are how Apple tests AI features on a billion devices without a headline launch.',src:'The Hans India, citing 9to5Mac',url:'https://www.thehansindia.com/tech/upcoming-ai-updates-in-october-2026-major-developments-to-watch-1127036',flag:'Expected'},
{id:'n4',desk:'Chips',date:'2026-09-02',title:'Broadcom lifts its AI chip outlook to $58 billion',sum:'Fiscal Q3 revenue came in at $29.6 billion, with $16.7 billion from AI semiconductors. Guidance for Q4 is about $34.8 billion in total and $21.7 billion from AI chips. One summary also cites roughly $115 billion of AI chip revenue for fiscal 2027.',why:'Custom accelerators for a handful of large customers are now growing faster than the merchant GPU story gets credit for.',src:'Akrostec event timeline',url:'https://www.akrostec.com/indices/ASHUSEM/events/2026-09-01t00-00-00z-micron-technology-inc-mu-financial-results-6e113500'},
{id:'n5',desk:'Chips',date:'2026-08-26',title:'Intel says 18A yields are beating its own targets',sum:'The company reported 18A yields ahead of internal milestones and faster defect-density gains on 14A. The 14A 0.9 design kit is still expected in October.',why:'Customers decide on a foundry by yield and tooling. The October design kit is the next real test.',src:'Akrostec event timeline',url:'https://www.akrostec.com/indices/ASHUSEM/events/2026-08-07t00-00-00z-qualcomm-inc-qcom-commercial-a517cf2b'},
{id:'n6',desk:'Chips',date:'2026-08-24',title:'AMD details MI455X and its 72-GPU Helios rack',sum:'At Hot Chips, AMD gave new specifications: 432 GB of HBM4 memory per GPU and a rack that holds 72 of them.',why:'Memory capacity per GPU, more than raw compute, is what decides which models fit on a node.',src:'Akrostec event timeline',url:'https://www.akrostec.com/indices/ASHUSEM/events/2026-08-07t00-00-00z-qualcomm-inc-qcom-commercial-a517cf2b'},
{id:'n7',desk:'Chips',date:'2026-08-21',title:'Japanese chip-tool billings are up 35% on the year',sum:'The industry association SEAJ put three-month average billings for July at ¥556.22 billion, up 8.3% on the prior month and 35.4% on July 2025.',why:'Equipment orders lead chip output by quarters, so this is an early read on capacity coming online.',src:'Akrostec event timeline',url:'https://www.akrostec.com/indices/ASHUSEM/events/2026-08-07t00-00-00z-qualcomm-inc-qcom-commercial-a517cf2b'},
{id:'n8',desk:'Chips',date:null,dlabel:'2026 report',title:'TSMC starts sub-2 nm volume production, capacity booked into 2027',sum:'A German tech outlet reports 30% more transistors per area and 25% less power than the prior node, with 2 nm capacity sold out through much of the first half of 2027. It adds that data processing passes half of all chip revenue this year.',why:'Phones and laptops get 2 nm silicon this cycle, but data centres get first call on it.',src:'Inside Digital',url:'https://www.inside-digital.de/news/halbleiter-trends-2026',flag:'Single source'},
{id:'n9',desk:'Chips',date:null,dlabel:'Recent posts',title:'MediaTek\'s 2 nm Dimensity 9600 Pro and a US packaging push',sum:'TrendForce reports that MediaTek\'s Dimensity 9600 Pro, built on TSMC 2 nm, is priced at a record $220. It also reports that ASE\'s SPIL is nearing an Arizona expansion and that South Korea widened its espionage law to cover chip technology leaks.',why:'Packaging, not just wafers, is moving onshore. Leak laws show how closely guarded process know-how has become.',src:'TrendForce',url:'https://www.trendforce.com/',flag:'Reported'},
{id:'n10',desk:'Chips',date:'2026-08-06',title:'Anthropic is reported to be building its own AI chips',sum:'A news index lists a 6 August item with this headline. We found the headline only, not the article, so details are not summarised here.',why:'Every large AI lab is now weighing custom silicon against buying GPUs. Read the full article before drawing conclusions.',src:'Build Fast With AI index',url:'https://beta.buildfastwithai.com/blogs/all',flag:'Headline only'},
{id:'n11',desk:'Robotics',date:'2026-08-03',dlabel:'Week of 3 Aug',title:'Gemini Robotics 2 brings whole-body control',sum:'Google DeepMind says its second Gemini Robotics model can control a robot\'s full body, according to the weekly ROS community digest.',why:'Moving from arm-only tasks to whole-body control is the step that matters for humanoids.',src:'Open Robotics Discourse',url:'https://discourse.openrobotics.org/t/ros-news-for-the-week-august-3rd-2026/57223'},
{id:'n12',desk:'Robotics',date:'2026-08-03',dlabel:'Week of 3 Aug',title:'HEBI Robotics wins a NASA grant for tiny actuators',sum:'The company earned a NASA small-business research award to speed up miniaturised actuators, the motors that move robot joints.',why:'Smaller, lighter joints cut launch mass and also help every humanoid on Earth.',src:'Open Robotics Discourse',url:'https://discourse.openrobotics.org/t/ros-news-for-the-week-august-3rd-2026/57223'},
{id:'n13',desk:'Space',date:'2026-09-10',title:'Germany\'s space agency pitches robotics as sovereignty',sum:'DLR briefed the German parliament\'s aerospace group on 10 September. It argued that robots for in-orbit servicing and planetary exploration are a key technology for German and European independence.',why:'Servicing satellites in orbit is turning from research into industrial policy.',src:'Silicon Saxony',url:'https://silicon-saxony.de/en/dlr-robotics-in-space-an-opportunity-for-german-and-european-sovereignty/'},
{id:'n14',desk:'Space',date:'2026-02-11',title:'Software for NASA\'s Fly Foundational Robotics mission',sum:'Motiv Space Systems and PickNik Robotics are supplying motion planning and arm control for the mission, which will test core robotics technology in space. This is background from earlier this year.',why:'It is the planned flight demonstration behind most of the space robotics activity above.',src:'Robotics 24/7',url:'https://www.robotics247.com/topic/tag/Motiv_Space_Systems',flag:'Background'}
];
var EVENTS=[
{start:'2026-10-31',label:'By 31 October',name:'iOS 27.1 and 27.2 expected',where:'Apple, reported by 9to5Mac',url:'https://www.thehansindia.com/tech/upcoming-ai-updates-in-october-2026-major-developments-to-watch-1127036',expected:true},
{start:'2026-10-31',label:'October',name:'Intel 14A 0.9 design kit expected',where:'Intel Foundry',url:'https://www.akrostec.com/indices/ASHUSEM/events/2026-08-07t00-00-00z-qualcomm-inc-qcom-commercial-a517cf2b',expected:true},
{start:'2026-10-21',end:'2026-10-23',label:'21 to 23 Oct',name:'ROSCon UK',where:'Edinburgh',url:'https://discourse.openrobotics.org/t/ros-news-for-the-week-august-3rd-2026/57223'},
{start:'2026-10-23',end:'2026-10-26',label:'23 to 26 Oct',name:'ROSCon Singapore',where:'Singapore',url:'https://discourse.openrobotics.org/t/ros-news-for-the-week-august-3rd-2026/57223'},
{start:'2026-10-27',end:'2026-10-28',label:'27 to 28 Oct',name:'ROSCon Spain',where:'Valencia',url:'https://discourse.openrobotics.org/t/ros-news-for-the-week-august-3rd-2026/57223'},
{start:'2026-11-03',label:'3 Nov',name:'ROSCon Italy',where:'Bologna',url:'https://discourse.openrobotics.org/t/ros-news-for-the-week-august-3rd-2026/57223'},
{start:'2026-11-05',label:'5 Nov',name:'International Conference on Humanoid Robotics, Innovation & Leadership',where:'Venue not listed in the source',url:'https://discourse.openrobotics.org/t/ros-news-for-the-week-august-3rd-2026/57223'}
];

/* state */
var saved=store.get('substrate.saved',[]);
var follow=store.get('substrate.follow',[]);
var state={desk:'All',q:'',sort:store.get('substrate.sort','new')};

/* helpers */
function rng(s){return function(){s|=0;s=s+0x6D2B79F5|0;var t=Math.imul(s^s>>>15,1|s);t=t+Math.imul(t^t>>>7,61|t)^t;return((t^t>>>14)>>>0)/4294967296}}
function hash(str){var h=2166136261;for(var i=0;i<str.length;i++){h^=str.charCodeAt(i);h=Math.imul(h,16777619)}return h>>>0}
function fmtDate(n){if(n.dlabel)return n.dlabel;if(!n.date)return 'Undated';var d=new Date(n.date+'T00:00:00');return d.toLocaleDateString('en-GB',{day:'numeric',month:'short'})}
function toast(msg){var t=$('#toast');t.textContent=msg;t.hidden=false;clearTimeout(toast.t);toast.t=setTimeout(function(){t.hidden=true},1800)}

/* edition date */
(function(){var d=new Date();$('#edition').textContent='Edition of '+d.toLocaleDateString('en-GB',{weekday:'long',day:'numeric',month:'long',year:'numeric'})})();

/* theme */
function setTheme(t){document.documentElement.setAttribute('data-theme',t);store.set('substrate.theme',t);paintAll()}
(function(){var t=store.get('substrate.theme',null);if(t==='dark'||t==='light')document.documentElement.setAttribute('data-theme',t)})();
$('#theme').addEventListener('click',function(){setTheme(isDark()?'light':'dark')});
if(window.matchMedia){var mq=matchMedia('(prefers-color-scheme: dark)');(mq.addEventListener?mq.addEventListener.bind(mq,'change'):function(){})(function(){paintAll()})}

/* covers */
var ART={n1:'agents',n2:'roadmap',n3:'phone',n4:'asic',n5:'yield',n6:'rack',n7:'tools',n8:'node',n9:'package',n10:'chipai',n11:'humanoid',n12:'joint',n13:'orbit',n14:'arm'};
function drawArt(x,W,H,art,r,cols,L){
  var A=cols[0],B=cols[1],C=cols[2],cx=W/2,cy=H/2,m=Math.min(W,H),i,j;
  x.lineCap='round';x.lineJoin='round';x.globalAlpha=1;
  function dot(px,py,rad,col,al){x.globalAlpha=al==null?1:al;x.fillStyle=col;x.beginPath();x.arc(px,py,rad,0,7);x.fill();x.globalAlpha=1}
  function ln(a,b,c,d,col,w,al){x.strokeStyle=col;x.lineWidth=w||1.5;x.globalAlpha=al==null?1:al;x.beginPath();x.moveTo(a,b);x.lineTo(c,d);x.stroke();x.globalAlpha=1}
  function rr(px,py,w,h,rad){x.beginPath();if(x.roundRect)x.roundRect(px,py,w,h,rad);else x.rect(px,py,w,h)}
  if(art==='agents'){
    var N=[];for(i=0;i<16;i++)N.push([W*(.08+r()*.84),H*(.12+r()*.76)]);
    N.forEach(function(p,a){N.forEach(function(q,b){if(b>a&&Math.hypot(p[0]-q[0],p[1]-q[1])<W*.3)ln(p[0],p[1],q[0],q[1],cols[(a+b)%3],1,.45)})});
    N.forEach(function(p,a){dot(p[0],p[1],3+r()*3,cols[a%3])});
    x.strokeStyle=A;x.lineWidth=2;x.beginPath();x.arc(cx,cy,m*.14,0,7);x.stroke();dot(cx,cy,m*.06,A)
  }else if(art==='roadmap'){
    var py=function(t){return H*(.5-.26*Math.sin(t*6.28))};
    x.strokeStyle=L;x.lineWidth=2;x.setLineDash([6,6]);x.beginPath();for(i=0;i<=60;i++){var t=i/60;x[i?'lineTo':'moveTo'](W*(.06+.88*t),py(t))}x.stroke();x.setLineDash([]);
    ln(W*(.06+.88*.25),py(.25),W*(.06+.88*.5),H*.14,C,2.5,.8);dot(W*(.06+.88*.5),H*.14,7,C,.8);
    [0,.25,.5,.75,1].forEach(function(t,k){dot(W*(.06+.88*t),py(t),k===2?10:6,cols[k%3])})
  }else if(art==='phone'){
    var pw=m*.52,ph=m*.92;[A,B,C].forEach(function(col,k){dot(cx+(k-1)*pw*.28,cy+ph*.22,pw*.34,col,.32)});
    x.strokeStyle=L;x.lineWidth=3;rr(cx-pw/2,cy-ph/2,pw,ph,m*.08);x.stroke();
    x.fillStyle=L;rr(cx-pw*.14,cy-ph/2+m*.03,pw*.28,m*.03,4);x.fill();
    for(i=0;i<5;i++)ln(cx-pw*.3,cy-ph*.3+i*m*.07,cx+pw*(.3-(i%3)*.12),cy-ph*.3+i*m*.07,A,2.5,.7)
  }else if(art==='asic'){
    var s=m*.6,x0=cx-s/2,y0=cy-s/2;x.fillStyle=A;x.globalAlpha=.14;x.fillRect(x0,y0,s,s);x.globalAlpha=1;
    for(i=0;i<8;i++){var o=s*(.1+i*.11);ln(x0+o,y0,x0+o,y0-m*.08,L,2);ln(x0+o,y0+s,x0+o,y0+s+m*.08,L,2);ln(x0,y0+o,x0-m*.08,y0+o,L,2);ln(x0+s,y0+o,x0+s+m*.08,y0+o,L,2)}
    x.strokeStyle=A;x.lineWidth=3;x.strokeRect(x0,y0,s,s);
    for(i=0;i<5;i++){var bh=s*(.2+i*.14);x.fillStyle=cols[i%3];x.fillRect(x0+s*.12+i*s*.17,y0+s*.88-bh,s*.12,bh)}
  }else if(art==='yield'){
    var R=m*.44,n=13,cl=2*R/n;
    for(i=0;i<n;i++)for(j=0;j<n;j++){var px=cx-R+i*cl+cl/2,qy=cy-R+j*cl+cl/2;if(Math.hypot(px-cx,qy-cy)>R-cl*.4)continue;var bad=r()<.07;x.fillStyle=bad?C:B;x.globalAlpha=bad?.95:.55+r()*.3;x.fillRect(px-cl/2+1.5,qy-cl/2+1.5,cl-3,cl-3)}
    x.globalAlpha=1;x.strokeStyle=L;x.lineWidth=2;x.beginPath();x.arc(cx,cy,R+2,0,7);x.stroke()
  }else if(art==='rack'){
    var cw=m*.1,gw=cw*12,gh=cw*6,gx=cx-gw/2,gy=cy-gh/2;
    x.strokeStyle=L;x.lineWidth=3;x.strokeRect(gx-10,gy-10,gw+20,gh+20);
    for(i=0;i<12;i++)for(j=0;j<6;j++){x.fillStyle=cols[(i+j)%3];x.globalAlpha=.35+r()*.5;x.fillRect(gx+i*cw+2,gy+j*cw+2,cw-4,cw-4)}
    x.globalAlpha=1
  }else if(art==='tools'){
    var bw=W*.062,pts=[];
    for(i=0;i<12;i++){var h=H*(.18+i*.05+r()*.05),bx=W*.08+i*bw*1.3;x.fillStyle=B;x.globalAlpha=.55;x.fillRect(bx,H*.9-h,bw,h);x.globalAlpha=1;pts.push([bx+bw/2,H*.9-h-H*.05])}
    x.strokeStyle=A;x.lineWidth=3;x.beginPath();pts.forEach(function(p,k){x[k?'lineTo':'moveTo'](p[0],p[1])});x.stroke();pts.forEach(function(p){dot(p[0],p[1],4,A)});ln(W*.05,H*.9,W*.95,H*.9,L,2)
  }else if(art==='node'){
    var sp=m*.1,sp2=sp/Math.sqrt(1.3);
    for(i=0;i*sp<W*.46;i++)for(j=0;j*sp<H*.8;j++)dot(W*.04+i*sp,H*.1+j*sp,3,L);
    for(i=0;i*sp2<W*.46;i++)for(j=0;j*sp2<H*.8;j++)dot(W*.54+i*sp2,H*.1+j*sp2,2.6,B);
    ln(cx,H*.06,cx,H*.94,A,2);ln(cx-m*.12,cy,cx+m*.12,cy,A,3);ln(cx+m*.12,cy,cx+m*.05,cy-m*.06,A,3);ln(cx+m*.12,cy,cx+m*.05,cy+m*.06,A,3)
  }else if(art==='package'){
    var bw2=m*1.5>W*.9?W*.9:m*1.5,x0=cx-bw2/2,ys=cy+m*.12;
    x.fillStyle=L;x.globalAlpha=.7;x.fillRect(x0,ys,bw2,m*.1);x.globalAlpha=1;
    for(i=0;i<14;i++)dot(x0+bw2*(.05+i*.068),ys+m*.17,m*.025,C);
    x.fillStyle=B;x.globalAlpha=.6;x.fillRect(x0+bw2*.04,ys-m*.05,bw2*.92,m*.05);x.globalAlpha=1;
    x.fillStyle=A;x.fillRect(x0+bw2*.34,ys-m*.3,bw2*.32,m*.25);
    [.08,.7].forEach(function(f){for(var k=0;k<4;k++){x.fillStyle=cols[(k+1)%3];x.globalAlpha=.8;x.fillRect(x0+bw2*f,ys-m*.1-k*m*.055,bw2*.22,m*.045)}x.globalAlpha=1})
  }else if(art==='chipai'){
    var s2=m*.3;for(i=0;i<36;i++){var a=i/36*6.283,r1=s2*.9,r2=s2*(1.2+r()*.9);ln(cx+Math.cos(a)*r1,cy+Math.sin(a)*r1,cx+Math.cos(a)*r2,cy+Math.sin(a)*r2,cols[i%3],2,.8)}
    x.fillStyle=A;x.globalAlpha=.2;x.fillRect(cx-s2/2,cy-s2/2,s2,s2);x.globalAlpha=1;x.strokeStyle=A;x.lineWidth=3;x.strokeRect(cx-s2/2,cy-s2/2,s2,s2);
    x.strokeStyle=C;x.lineWidth=2;x.setLineDash([4,5]);x.strokeRect(cx-s2*.9,cy-s2*.9,s2*1.8,s2*1.8);x.setLineDash([])
  }else if(art==='humanoid'){
    var u=m*.1,pts2={h:[cx,cy-u*3.9],n:[cx,cy-u*3],s1:[cx-u*1.1,cy-u*2.8],s2:[cx+u*1.1,cy-u*2.8],e1:[cx-u*1.8,cy-u*1.3],e2:[cx+u*1.8,cy-u*1.6],w1:[cx-u*2,cy+u*.2],w2:[cx+u*2.5,cy-u*.6],p:[cx,cy-u*.3],k1:[cx-u*.7,cy+u*1.6],k2:[cx+u*.8,cy+u*1.6],f1:[cx-u*.8,cy+u*3.5],f2:[cx+u*1,cy+u*3.5]};
    [['n','p'],['s1','s2'],['s1','e1'],['e1','w1'],['s2','e2'],['e2','w2'],['p','k1'],['k1','f1'],['p','k2'],['k2','f2']].forEach(function(e,k){ln(pts2[e[0]][0],pts2[e[0]][1],pts2[e[1]][0],pts2[e[1]][1],cols[k%3],3.5)});
    x.strokeStyle=A;x.lineWidth=3;x.beginPath();x.arc(pts2.h[0],pts2.h[1],u*.55,0,7);x.stroke();
    ['s1','s2','e1','e2','k1','k2','p'].forEach(function(k){dot(pts2[k][0],pts2[k][1],6,C);x.strokeStyle=L;x.lineWidth=1.5;x.beginPath();x.arc(pts2[k][0],pts2[k][1],14,0,1.6);x.stroke()})
  }else if(art==='joint'){
    var g=m*.3,teeth=14;x.beginPath();for(i=0;i<teeth*2;i++){var ang=i/(teeth*2)*6.283,rad=i%2?g*.82:g;x[i?'lineTo':'moveTo'](cx-m*.2+Math.cos(ang)*rad,cy+Math.sin(ang)*rad)}x.closePath();x.fillStyle=A;x.globalAlpha=.25;x.fill();x.globalAlpha=1;x.strokeStyle=A;x.lineWidth=3;x.stroke();
    dot(cx-m*.2,cy,g*.3,C);x.strokeStyle=L;x.lineWidth=2;x.beginPath();x.arc(cx-m*.2,cy,g*.5,0,7);x.stroke();
    x.fillStyle=B;x.globalAlpha=.6;x.fillRect(cx+m*.2,cy-m*.08,m*.55,m*.16);x.globalAlpha=1;x.strokeStyle=B;x.lineWidth=3;x.strokeRect(cx+m*.2,cy-m*.08,m*.55,m*.16);ln(cx+m*.75,cy,cx+m*.95,cy,B,5)
  }else if(art==='orbit'){
    x.strokeStyle=L;x.lineWidth=3;x.beginPath();x.arc(cx,H*1.55,H*.95,Math.PI*1.2,Math.PI*1.8);x.stroke();dot(cx,H*1.55,H*.9,B,.18);
    x.strokeStyle=C;x.lineWidth=1.5;x.setLineDash([5,6]);x.beginPath();x.ellipse(cx,cy+m*.1,W*.42,m*.28,-.12,0,7);x.stroke();x.setLineDash([]);
    var sx=cx-m*.1,sy=cy-m*.08;x.fillStyle=A;x.fillRect(sx-m*.07,sy-m*.07,m*.14,m*.14);x.fillStyle=B;x.fillRect(sx-m*.36,sy-m*.03,m*.26,m*.06);x.fillRect(sx+m*.1,sy-m*.03,m*.26,m*.06);
    ln(sx+m*.07,sy+m*.07,sx+m*.22,sy+m*.2,C,4);ln(sx+m*.22,sy+m*.2,sx+m*.36,sy+m*.16,C,4);dot(sx+m*.22,sy+m*.2,5,C);dot(sx+m*.36,sy+m*.16,6,A)
  }else if(art==='arm'){
    ln(0,H*.88,W,H*.88,L,3);for(i=0;i<40;i++)dot(r()*W,H*.9+r()*H*.1,1.6,L);
    var lx=cx-m*.35,ly=H*.5;x.fillStyle=A;x.globalAlpha=.25;x.fillRect(lx,ly,m*.5,m*.2);x.globalAlpha=1;x.strokeStyle=A;x.lineWidth=3;x.strokeRect(lx,ly,m*.5,m*.2);
    ln(lx+m*.05,ly+m*.2,lx-m*.08,H*.88,L,3);ln(lx+m*.45,ly+m*.2,lx+m*.58,H*.88,L,3);
    ln(lx+m*.5,ly+m*.1,lx+m*.8,ly+m*.02,C,5);ln(lx+m*.8,ly+m*.02,lx+m*.95,H*.8,C,5);dot(lx+m*.5,ly+m*.1,6,B);dot(lx+m*.8,ly+m*.02,6,B);dot(lx+m*.95,H*.8,6,A)
  }else{return false}
  return true
}
function drawCover(c,desk,seedStr,art){
  var dpr=Math.min(window.devicePixelRatio||1,2),W=c.clientWidth||320,H=c.clientHeight||180;
  c.width=Math.round(W*dpr);c.height=Math.round(H*dpr);
  var x=c.getContext('2d');x.setTransform(dpr,0,0,dpr,0,0);
  var r=rng(hash(seedStr)),A=css('--art-a'),B=css('--art-b'),C=css('--art-c'),S=css('--surface-2'),L=css('--line');
  x.fillStyle=S;x.fillRect(0,0,W,H);
  var cols=[A,B,C];
  if(art&&drawArt(x,W,H,art,r,cols,L)){}
  else if(desk==='AI'){
    var ph=r()*10,fr=0.008+r()*0.01;
    x.lineWidth=1.2;
    for(var i=0;i<110;i++){
      var px=r()*W,py=r()*H;x.strokeStyle=cols[i%3];x.globalAlpha=.35+r()*.5;x.beginPath();x.moveTo(px,py);
      for(var s=0;s<46;s++){var a=Math.sin(px*fr+ph)*2.4+Math.cos(py*fr*1.3-ph)*2.4;px+=Math.cos(a)*5;py+=Math.sin(a)*5;x.lineTo(px,py)}
      x.stroke()
    }
  }else if(desk==='Chips'){
    var cell=Math.max(10,Math.round(W/22));
    for(var gx=0;gx<W;gx+=cell)for(var gy=0;gy<H;gy+=cell){x.globalAlpha=.08+r()*.45;x.fillStyle=cols[Math.floor(r()*3)];x.fillRect(gx+1,gy+1,cell-2,cell-2)}
    x.globalAlpha=1;x.strokeStyle=A;x.lineWidth=2;
    for(var k=0;k<7;k++){var tx=Math.round(r()*W/cell)*cell,ty=Math.round(r()*H/cell)*cell;x.beginPath();x.moveTo(tx,ty);for(var m=0;m<5;m++){if(m%2===0)tx+=(r()<.5?-1:1)*cell*Math.ceil(r()*4);else ty+=(r()<.5?-1:1)*cell*Math.ceil(r()*3);x.lineTo(tx,ty)}x.stroke();x.fillStyle=C;x.fillRect(tx-3,ty-3,6,6)}
  }else if(desk==='Robotics'){
    var bx=W*(.2+r()*.2),by=H*.88,l1=H*.5,l2=H*.4,l3=H*.25;
    for(var f=0;f<14;f++){
      var a1=-Math.PI/2+(f-7)*.16+r()*.1,a2=a1+(r()-.3)*1.5,a3=a2+(r()-.5)*1.6;
      var x1=bx+Math.cos(a1)*l1,y1=by+Math.sin(a1)*l1,x2=x1+Math.cos(a2)*l2,y2=y1+Math.sin(a2)*l2,x3=x2+Math.cos(a3)*l3,y3=y2+Math.sin(a3)*l3;
      x.globalAlpha=.25+f/20;x.strokeStyle=cols[f%3];x.lineWidth=4;x.lineCap='round';x.beginPath();x.moveTo(bx,by);x.lineTo(x1,y1);x.lineTo(x2,y2);x.lineTo(x3,y3);x.stroke();
      x.fillStyle=cols[(f+1)%3];[[x1,y1],[x2,y2],[x3,y3]].forEach(function(p){x.beginPath();x.arc(p[0],p[1],4,0,7);x.fill()})
    }
    x.globalAlpha=1;x.fillStyle=A;x.fillRect(bx-18,by-4,36,8)
  }else{
    var cx=W*(.35+r()*.3),cy=H*(.4+r()*.2);
    x.globalAlpha=1;x.fillStyle=B;x.beginPath();x.arc(cx,cy,Math.min(W,H)*.09,0,7);x.fill();
    for(var o=0;o<7;o++){
      var rx=W*(.12+o*.07),ry=rx*(.35+r()*.4),rot=r()*Math.PI;
      x.strokeStyle=o%2?A:C;x.globalAlpha=.7;x.lineWidth=1.2;x.beginPath();x.ellipse(cx,cy,rx,ry,rot,0,7);x.stroke();
      var ang=r()*7;x.globalAlpha=1;x.fillStyle=cols[o%3];x.beginPath();
      x.arc(cx+Math.cos(ang)*rx*Math.cos(rot)-Math.sin(ang)*ry*Math.sin(rot),cy+Math.cos(ang)*rx*Math.sin(rot)+Math.sin(ang)*ry*Math.cos(rot),4,0,7);x.fill()
    }
  }
  x.globalAlpha=1;x.strokeStyle=L;x.lineWidth=1;x.strokeRect(.5,.5,W-1,H-1)
}
function paintCovers(){$$('canvas[data-cover]').forEach(function(c){drawCover(c,c.getAttribute('data-desk'),c.getAttribute('data-cover'),ART[c.getAttribute('data-cover')])})}

/* ticker */
function buildTicker(){
  var items=NEWS.filter(function(n){return n.date}).sort(function(a,b){return b.date.localeCompare(a.date)}).slice(0,8);
  var h=items.map(function(n){return '<a href="#news" data-go="'+n.id+'"><b>'+esc(n.desk)+'</b>'+esc(n.title)+'</a>'}).join('');
  $('#ticker').innerHTML=h+h
}

/* chips */
function buildChips(){
  var all=['All'].concat(DESKS,['Saved']);
  $('#chips').innerHTML=all.map(function(d){var lbl=d==='Saved'?'Saved ('+saved.length+')':d;return '<button type="button" class="chip" data-desk="'+d+'" aria-pressed="'+(state.desk===d)+'">'+lbl+'</button>'}).join('');
  $('#follow-chips').innerHTML=DESKS.map(function(d){return '<button type="button" class="chip" data-follow="'+d+'" aria-pressed="'+(follow.indexOf(d)>-1)+'">'+d+'</button>'}).join('')
}

/* news render */
function list(){
  var q=state.q.trim().toLowerCase();
  var out=NEWS.filter(function(n){
    if(state.desk==='Saved'&&saved.indexOf(n.id)<0)return false;
    if(state.desk!=='All'&&state.desk!=='Saved'&&n.desk!==state.desk)return false;
    if(q&&(n.title+' '+n.sum+' '+n.desk+' '+n.src).toLowerCase().indexOf(q)<0)return false;
    return true});
  var byDate=function(a,b){return (b.date||'0').localeCompare(a.date||'0')};
  if(state.sort==='desk')out.sort(function(a,b){return a.desk.localeCompare(b.desk)||byDate(a,b)});
  else if(state.sort==='mine')out.sort(function(a,b){return (follow.indexOf(b.desk)>-1)-(follow.indexOf(a.desk)>-1)||byDate(a,b)});
  else out.sort(byDate);
  return out
}
function card(n,lead){
  var isSaved=saved.indexOf(n.id)>-1,fol=follow.indexOf(n.desk)>-1;
  return '<article class="card'+(lead?' lead':'')+'" id="'+n.id+'">'+
    '<canvas data-cover="'+n.id+'" data-desk="'+n.desk+'" aria-hidden="true"></canvas>'+
    '<div class="card-body"><div class="meta"><span class="desk">'+esc(n.desk)+'</span><span class="date">'+esc(fmtDate(n))+'</span>'+(fol?'<span class="following">Following</span>':'')+(n.flag?'<span class="flag">'+esc(n.flag)+'</span>':'')+'</div>'+
    '<h3>'+esc(n.title)+'</h3><p class="sum">'+esc(n.sum)+'</p>'+
    '<div class="why" hidden id="why-'+n.id+'"><strong>Why it matters.</strong> '+esc(n.why)+'</div>'+
    '<div class="card-foot"><a href="'+esc(n.url)+'" target="_blank" rel="noopener">'+esc(n.src)+' &#8599;</a>'+
    '<span><button class="mini" type="button" data-why="'+n.id+'" aria-expanded="false" aria-controls="why-'+n.id+'">Why it matters</button> &nbsp; <button class="mini" type="button" data-save="'+n.id+'" aria-pressed="'+isSaved+'">'+(isSaved?'Saved':'Save')+'</button></span></div></div></article>'
}
function renderNews(){
  var items=list(),g=$('#grid');
  if(!items.length){g.innerHTML='<div class="empty">'+(state.desk==='Saved'?'Nothing saved yet. Use Save on any story and it will appear here.':'No stories match. Clear the search or pick another desk.')+'</div>';return}
  var lead=items.length>=4&&state.sort==='new'&&state.desk==='All'&&!state.q;
  g.innerHTML=items.map(function(n,i){return card(n,lead&&i===0)}).join('');
  paintCovers()
}

/* chart */
function buildChart(){
  var data=[{g:'Total revenue',a:29.6,b:34.8},{g:'AI semiconductor revenue',a:16.7,b:21.7}];
  var W=640,H=380,ml=48,mr=16,mt=28,mb=56,pw=W-ml-mr,ph=H-mt-mb,max=40;
  var y=function(v){return mt+ph-(v/max)*ph};
  var s='';
  [0,10,20,30,40].forEach(function(t){s+='<line class="ax" x1="'+ml+'" x2="'+(W-mr)+'" y1="'+y(t)+'" y2="'+y(t)+'"/><text class="tick" x="'+(ml-8)+'" y="'+(y(t)+4)+'" text-anchor="end">$'+t+'B</text>'});
  var gw=pw/data.length,bw=76,gap=14;
  data.forEach(function(d,i){
    var gx=ml+gw*i+(gw-(bw*2+gap))/2;
    s+='<rect class="b-act" x="'+gx+'" y="'+y(d.a)+'" width="'+bw+'" height="'+(y(0)-y(d.a))+'"><title>'+d.g+', fiscal Q3 2026: $'+d.a+'B</title></rect>';
    s+='<rect class="b-gd" x="'+(gx+bw+gap)+'" y="'+y(d.b)+'" width="'+bw+'" height="'+(y(0)-y(d.b))+'"><title>'+d.g+', fiscal Q4 guidance: $'+d.b+'B</title></rect>';
    s+='<text class="lab" x="'+(gx+bw/2)+'" y="'+(y(d.a)-7)+'" text-anchor="middle">$'+d.a.toFixed(1)+'B</text>';
    s+='<text class="lab" x="'+(gx+bw+gap+bw/2)+'" y="'+(y(d.b)-7)+'" text-anchor="middle">$'+d.b.toFixed(1)+'B</text>';
    s+='<text class="grp" x="'+(gx+bw+gap/2)+'" y="'+(H-mb+28)+'" text-anchor="middle">'+d.g+'</text>'
  });
  s+='<line class="ax" x1="'+ml+'" x2="'+(W-mr)+'" y1="'+y(0)+'" y2="'+y(0)+'" style="stroke:var(--ink)"/>';
  $('#chart').innerHTML=s;
  var gt=((34.8/29.6-1)*100).toFixed(1),ga=((21.7/16.7-1)*100).toFixed(1);
  $('#chart-note').textContent='Guided growth from Q3 to Q4: total revenue +'+gt+'%, AI semiconductors +'+ga+'%. Source figures are as relayed by an event-timeline summary of the company report.'
}

/* calculators */
var nf=new Intl.NumberFormat('en-US',{maximumFractionDigits:0});
var cf=new Intl.NumberFormat('en-US',{style:'currency',currency:'USD',maximumFractionDigits:2});
function compact(v){return new Intl.NumberFormat('en-US',{notation:'compact',maximumFractionDigits:2}).format(v)}
function num(id){var v=parseFloat($(id).value);return isFinite(v)&&v>=0?v:0}
function calc1(){
  var req=num('#c-req'),tok=num('#c-tok'),price=num('#c-price'),days=Math.max(1,num('#c-days'));
  var tpd=req*tok,tpp=tpd*days,cost=tpp/1e6*price;
  $('#o-tpd').textContent=compact(tpd);$('#o-tpp').textContent=compact(tpp);$('#o-cost').textContent=cf.format(cost);
  $('#o-k').textContent=cf.format(tok/1e6*price*1000)
}
function calc2(){
  var tr=num('#n-tr'),pw=num('#n-pw'),up=num('#n-up'),dn=Math.min(100,num('#n-dn'));
  var ntr=tr*(1+up/100),npw=pw*(1-dn/100);
  $('#o-tr').textContent=ntr.toFixed(1)+'B';$('#o-pw').textContent=npw.toFixed(1)+' W';$('#o-sv').textContent=(pw-npw).toFixed(1)+' W';
  $('#o-eff').textContent=npw>0?(ntr/npw).toFixed(2)+'B/W':'n/a'
}
['#c-req','#c-tok','#c-price','#c-days'].forEach(function(s){$(s).addEventListener('input',calc1)});
['#n-tr','#n-pw','#n-up','#n-dn'].forEach(function(s){$(s).addEventListener('input',calc2)});

/* calendar */
function buildCal(){
  var now=new Date(),t0=new Date(now.getFullYear(),now.getMonth(),now.getDate());
  var day=function(s){return new Date(s+'T00:00:00')};
  var rows=EVENTS.map(function(e){
    var s=day(e.start),en=e.end?day(e.end):s,ds=Math.round((s-t0)/864e5),de=Math.round((en-t0)/864e5),txt,cls='cd';
    if(de<0)txt='Finished';else if(ds<=0&&de>=0&&e.end)txt='Under way';else if(ds===0)txt=e.expected?'Due today':'Today';else{txt=(e.expected?'Due in ':'In ')+ds+(ds===1?' day':' days');if(ds<=7)cls+=' soon'}
    return {e:e,txt:txt,cls:cls,k:ds}
  }).sort(function(a,b){return a.k-b.k});
  $('#cal').innerHTML=rows.map(function(r){
    var e=r.e;return '<li><span class="when">'+esc(e.label)+'</span><div><h3>'+esc(e.name)+(e.expected?' <span class="flag">Expected</span>':'')+'</h3><p class="where">'+esc(e.where)+' &middot; <a href="'+esc(e.url)+'" target="_blank" rel="noopener">Source &#8599;</a></p></div><span class="'+r.cls+'">'+r.txt+'</span></li>'
  }).join('')
}

/* sources */
function buildSources(){
  var seen={},out=[];NEWS.forEach(function(n){if(!seen[n.url]){seen[n.url]=1;out.push('<li><a href="'+esc(n.url)+'" target="_blank" rel="noopener">'+esc(n.src)+'</a></li>')}});
  $('#sources').innerHTML=out.join('')
}

/* wafer */
var wafer=(function(){
  var c=$('#wafer'),x=c.getContext('2d'),W=0,H=0,dpr=1,mx=-1,my=-1,t=0,run=false,vis=true;
  function size(){dpr=Math.min(window.devicePixelRatio||1,2);W=c.clientWidth;H=c.clientHeight;c.width=Math.round(W*dpr);c.height=Math.round(H*dpr);x.setTransform(dpr,0,0,dpr,0,0)}
  function frame(){
    x.clearRect(0,0,W,H);
    var R=W*.46,cx=W/2,cy=H/2,n=26,cell=2*R/n,dark=isDark(),lo=dark?44:46;
    for(var i=0;i<n;i++)for(var j=0;j<n;j++){
      var px=cx-R+i*cell+cell/2,py=cy-R+j*cell+cell/2,d=Math.hypot(px-cx,py-cy);
      if(d>R-cell*.25)continue;
      var dm=mx<0?1e9:Math.hypot(px-mx,py-my),lift=Math.max(0,1-dm/(W*.2));
      var hue=(205+d*.9/ (W/420)+Math.sin(i*.5+t)*32+Math.cos(j*.4-t*.7)*32)%360;
      x.fillStyle='hsl('+hue.toFixed(0)+' 72% '+(lo+lift*24).toFixed(0)+'% / '+(.5+lift*.45).toFixed(2)+')';
      var g=cell*.1;x.fillRect(px-cell/2+g,py-cell/2+g,cell-2*g,cell-2*g)
    }
    x.strokeStyle=css('--line');x.lineWidth=1.5;x.beginPath();x.arc(cx,cy,R+cell*.15,0,7);x.stroke();
    x.fillStyle=css('--muted');x.font='11px '+css('--mono');x.textAlign='center';x.fillText('300 MM  /  '+n+' x '+n+' DIE GRID',cx,H-6);
    t+=.012
  }
  function loop(){if(!run)return;frame();if(!reduce&&vis)requestAnimationFrame(loop);else run=false}
  function start(){size();if(reduce){frame();return}if(!run){run=true;requestAnimationFrame(loop)}}
  c.addEventListener('pointermove',function(e){var b=c.getBoundingClientRect();mx=e.clientX-b.left;my=e.clientY-b.top;if(reduce)frame()});
  c.addEventListener('pointerleave',function(){mx=-1;my=-1;if(reduce)frame()});
  if('IntersectionObserver' in window)new IntersectionObserver(function(en){vis=en[0].isIntersecting;if(vis&&!reduce&&!run){run=true;requestAnimationFrame(loop)}}).observe(c);
  window.addEventListener('resize',function(){size();paintCovers();if(reduce)frame()});
  return {start:start,redraw:function(){if(reduce)frame()}}
})();

function paintAll(){paintCovers();wafer.redraw()}

/* events */
$('#chips').addEventListener('click',function(e){var b=e.target.closest('[data-desk]');if(!b)return;state.desk=b.getAttribute('data-desk');buildChips();renderNews()});
$('#follow-chips').addEventListener('click',function(e){var b=e.target.closest('[data-follow]');if(!b)return;var d=b.getAttribute('data-follow'),i=follow.indexOf(d);if(i>-1)follow.splice(i,1);else follow.push(d);store.set('substrate.follow',follow);buildChips();renderNews();toast(i>-1?'Unfollowed '+d:'Following '+d)});
$('#q').addEventListener('input',function(e){state.q=e.target.value;renderNews()});
$('#sort').value=state.sort;
$('#sort').addEventListener('change',function(e){state.sort=e.target.value;store.set('substrate.sort',state.sort);renderNews()});
$('#grid').addEventListener('click',function(e){
  var w=e.target.closest('[data-why]');
  if(w){var id=w.getAttribute('data-why'),el=$('#why-'+id),open=el.hidden;el.hidden=!open;w.setAttribute('aria-expanded',String(open));return}
  var s=e.target.closest('[data-save]');
  if(s){var sid=s.getAttribute('data-save'),i=saved.indexOf(sid);if(i>-1)saved.splice(i,1);else saved.push(sid);store.set('substrate.saved',saved);buildChips();
    if(state.desk==='Saved')renderNews();else{s.setAttribute('aria-pressed',String(i<0));s.textContent=i<0?'Saved':'Save'}
    toast(i<0?'Saved to your list':'Removed from your list')}
});
function goCard(id){
  state.desk='All';state.q='';$('#q').value='';buildChips();renderNews();
  var el=document.getElementById(id);if(el){el.scrollIntoView({behavior:reduce?'auto':'smooth',block:'center'});el.classList.add('pulse');setTimeout(function(){el.classList.remove('pulse')},1700)}
}
$('#ticker').addEventListener('click',function(e){var a=e.target.closest('[data-go]');if(a){e.preventDefault();goCard(a.getAttribute('data-go'))}});

/* reading progress */
function prog(){var h=document.documentElement,max=h.scrollHeight-h.clientHeight;$('#bar').style.width=(max>0?Math.min(100,h.scrollTop/max*100):0)+'%'}
window.addEventListener('scroll',prog,{passive:true});

/* command palette */
var pal={open:false,idx:0,items:[]};
function palItems(){
  var go=function(id){return function(){var el=document.getElementById(id);if(el)el.scrollIntoView({behavior:reduce?'auto':'smooth'})}};
  var a=[
    {l:'Go to News desk',k:'Section',run:go('news')},{l:'Go to Chip ledger',k:'Section',run:go('ledger')},
    {l:'Go to Calculators',k:'Section',run:go('tools')},{l:'Go to Calendar',k:'Section',run:go('calendar')},{l:'Go to Follow',k:'Section',run:go('follow')},
    {l:'Switch colour theme',k:'Action',run:function(){setTheme(isDark()?'light':'dark')}},
    {l:'Show saved stories',k:'Action',run:function(){state.desk='Saved';buildChips();renderNews();go('news')()}}
  ];
  DESKS.forEach(function(d){a.push({l:'Show '+d+' desk',k:'Filter',run:function(){state.desk=d;state.q='';$('#q').value='';buildChips();renderNews();go('news')()}})});
  NEWS.forEach(function(n){a.push({l:n.title,k:n.desk,run:function(){goCard(n.id)}})});
  return a
}
function palRender(){
  var q=$('#pal-q').value.trim().toLowerCase();
  pal.items=palItems().filter(function(i){return !q||(i.l+' '+i.k).toLowerCase().indexOf(q)>-1}).slice(0,40);
  if(pal.idx>=pal.items.length)pal.idx=0;
  $('#pal-list').innerHTML=pal.items.length?pal.items.map(function(i,n){return '<li role="option" data-i="'+n+'" aria-selected="'+(n===pal.idx)+'"><span>'+esc(i.l)+'</span><small>'+esc(i.k)+'</small></li>'}).join(''):'<li><span>No matches</span></li>';
  var sel=$('#pal-list [aria-selected="true"]');if(sel&&sel.scrollIntoView)sel.scrollIntoView({block:'nearest'})
}
function palOpen(){pal.open=true;pal.idx=0;$('#pal').hidden=false;$('#pal-q').value='';palRender();$('#pal-q').focus()}
function palClose(){pal.open=false;$('#pal').hidden=true}
function palRun(i){var it=pal.items[i];if(!it)return;palClose();setTimeout(it.run,30)}
$('#open-pal').addEventListener('click',palOpen);
$('#cta-pal').addEventListener('click',palOpen);
$('#pal-q').addEventListener('input',function(){pal.idx=0;palRender()});
$('#pal').addEventListener('click',function(e){if(e.target===$('#pal'))palClose();var li=e.target.closest('li[data-i]');if(li)palRun(+li.getAttribute('data-i'))});
document.addEventListener('keydown',function(e){
  var tag=(document.activeElement&&document.activeElement.tagName)||'';
  if((e.ctrlKey||e.metaKey)&&e.key.toLowerCase()==='k'){e.preventDefault();pal.open?palClose():palOpen();return}
  if(e.key==='/'&&!pal.open&&tag!=='INPUT'&&tag!=='SELECT'&&tag!=='TEXTAREA'){e.preventDefault();palOpen();return}
  if(!pal.open)return;
  if(e.key==='Escape'){palClose()}
  else if(e.key==='ArrowDown'){e.preventDefault();pal.idx=(pal.idx+1)%Math.max(1,pal.items.length);palRender()}
  else if(e.key==='ArrowUp'){e.preventDefault();pal.idx=(pal.idx-1+pal.items.length)%Math.max(1,pal.items.length);palRender()}
  else if(e.key==='Enter'){e.preventDefault();palRun(pal.idx)}
});

/* boot */
buildTicker();buildChips();renderNews();buildChart();calc1();calc2();buildCal();buildSources();prog();
wafer.start();
if(document.fonts&&document.fonts.ready)document.fonts.ready.then(function(){paintCovers()});
})();
</script>

</body>
</html>
# techquip.in
high value technology-based 
