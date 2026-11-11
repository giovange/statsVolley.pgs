
<title>Tabellino Pallavolo</title>
<meta name="claude:viewport-fit-sides" content="cover">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@600;700;800&family=Barlow:wght@400;500;600&display=swap">
<style>
/* Layout: tre fasi (rosa → formazione → partita); in partita segnapunti fisso con tre finestre (giocatrici, attacchi, difese); statistiche e cambi in pannelli sovrapposti */
:root{
  --bg:#eef1f6; --surface:#ffffff; --fg:#13203a; --muted:#5d6a82; --line:#d6dce8;
  --navy:#16306b; --navy-fg:#ffffff; --yellow:#f5c400; --yellow-fg:#1a1a1a;
  --good:#1d8a4e; --good-bg:#e3f4ea; --bad:#c8352b; --bad-bg:#fbe7e5; --shade:rgba(10,20,40,.45);
  --good-strong:#1d8a4e; --bad-strong:#c8352b; --on-strong:#ffffff;
  --court:#f3e1c7; --free:#c9dbef; --courtline:#ffffff; --net:#13203a; --zone:rgba(19,32,58,.16); --mk-stroke:#13203a;
  --mk-blue:#1f5fe0; --mk-green:#13964f; --mk-orange:#f07c00; --mk-purple:#8a3ffc; --mk-red:#d42b2b;
  --display:"Barlow Condensed","Arial Narrow",system-ui,sans-serif;
  --body:"Barlow",system-ui,-apple-system,"Segoe UI",sans-serif;
}
@media (prefers-color-scheme: dark){:root:not([data-theme="light"]){
  --bg:#0c1220; --surface:#162033; --fg:#e8edf7; --muted:#9aa6bd; --line:#2a3650;
  --navy:#1f3d85; --navy-fg:#ffffff; --yellow:#f5c400; --yellow-fg:#1a1a1a;
  --good:#4cc283; --good-bg:#14301f; --bad:#ff7a6e; --bad-bg:#3a1a18; --shade:rgba(0,0,0,.6);
  --good-strong:#23874f; --bad-strong:#c23a30; --on-strong:#ffffff;
  --court:#5b4632; --free:#1f3049; --courtline:#e9eef7; --net:#e9eef7; --zone:rgba(255,255,255,.16); --mk-stroke:#ffffff;
  --mk-blue:#4f8bff; --mk-green:#2fc46f; --mk-orange:#ff9a2e; --mk-purple:#b17cff; --mk-red:#ff5a4f; color-scheme:dark}}
:root[data-theme="dark"]{
  --bg:#0c1220; --surface:#162033; --fg:#e8edf7; --muted:#9aa6bd; --line:#2a3650;
  --navy:#1f3d85; --navy-fg:#ffffff; --yellow:#f5c400; --yellow-fg:#1a1a1a;
  --good:#4cc283; --good-bg:#14301f; --bad:#ff7a6e; --bad-bg:#3a1a18; --shade:rgba(0,0,0,.6);
  --good-strong:#23874f; --bad-strong:#c23a30; --on-strong:#ffffff;
  --court:#5b4632; --free:#1f3049; --courtline:#e9eef7; --net:#e9eef7; --zone:rgba(255,255,255,.16); --mk-stroke:#ffffff;
  --mk-blue:#4f8bff; --mk-green:#2fc46f; --mk-orange:#ff9a2e; --mk-purple:#b17cff; --mk-red:#ff5a4f; color-scheme:dark}
*{box-sizing:border-box}
[hidden]{display:none!important}
body{background:var(--bg);color:var(--fg);font-family:var(--body);font-size:15px}
body::before{content:"";position:fixed;inset:0 0 auto;height:env(safe-area-inset-top,0px);z-index:10;background:var(--navy)}
button,input,select{font:inherit;color:inherit}
button{cursor:pointer;border:0;background:none;-webkit-tap-highlight-color:transparent}
button:disabled{opacity:.4;cursor:default}
button:focus-visible,input:focus-visible,select:focus-visible{outline:3px solid var(--yellow);outline-offset:2px}
.wrap{max-width:820px;margin:0 auto;padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px))}
h1,h2,h3{font-family:var(--display);text-transform:uppercase;letter-spacing:.04em;margin:0;text-wrap:balance}
.btn{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.06em;font-size:14px;padding:9px 14px;border-radius:8px;background:var(--line);color:var(--fg)}
.btn.primary{background:var(--yellow);color:var(--yellow-fg)}
.btn.navy{background:var(--navy);color:var(--navy-fg)}
.btn.danger{background:var(--bad);color:#fff}
.hint{color:var(--muted);font-size:13px;margin:0;max-width:65ch}
.err{color:var(--bad);font-weight:600;font-size:14px;margin:0}
.confirm{display:flex;gap:8px;align-items:center;flex-wrap:wrap;font-size:14px}

/* Barra titolo fasi */
.bar{position:sticky;top:env(safe-area-inset-top,0px);z-index:5;background:var(--navy);color:var(--navy-fg)}
.bar .wrap{padding-block:14px;display:flex;align-items:center;gap:10px;flex-wrap:wrap}
.bar h1{font-size:24px;flex:1;min-width:0}
.bar .btn{background:rgba(255,255,255,.14);color:var(--navy-fg)}
.bar .btn.primary{background:var(--yellow);color:var(--yellow-fg)}
.content{padding-block:16px 40px;display:grid;gap:14px}

/* Ruoli */
.role{flex:none;min-width:34px;height:34px;padding:0 6px;border-radius:8px;background:var(--navy);color:var(--navy-fg);font-family:var(--display);font-weight:800;font-size:17px;display:inline-grid;place-items:center}
.role.L{background:var(--yellow);color:var(--yellow-fg)}

/* Rosa */
.rows{display:grid;gap:8px}
.rrow{display:grid;grid-template-columns:28px 1fr 150px 36px;gap:8px;align-items:center;background:var(--surface);border:1px solid var(--line);border-radius:10px;padding:8px}
@media (max-width:460px){.rrow{grid-template-columns:24px 1fr 120px 32px}}
.rrow .idx{font-family:var(--display);font-weight:700;color:var(--muted);text-align:center;font-variant-numeric:tabular-nums}
.rrow input,.rrow select{min-width:0;width:100%;padding:8px;border:1px solid var(--line);border-radius:6px;background:var(--bg)}
.del{width:32px;height:32px;border-radius:6px;color:var(--muted);font-size:20px}
.del:hover{background:var(--bad-bg);color:var(--bad)}

/* Formazione */
.teamsbox{display:grid;grid-template-columns:1fr 1fr;gap:10px}
@media (max-width:460px){.teamsbox{grid-template-columns:1fr}}
.teamsbox label{display:grid;gap:4px;font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.08em;font-size:12px;color:var(--muted)}
.teamsbox input{min-width:0;width:100%;padding:10px;border:1px solid var(--line);border-radius:8px;background:var(--surface);font-family:var(--body);font-size:16px;text-transform:none;letter-spacing:0;color:var(--fg)}
.rgroup{display:grid;gap:8px}
.rgroup h3{font-size:14px;color:var(--muted);letter-spacing:.1em}
.chips{display:grid;grid-template-columns:repeat(auto-fill,minmax(170px,1fr));gap:8px}
.pick{display:flex;align-items:center;gap:8px;padding:8px;border-radius:10px;background:var(--surface);border:2px solid var(--line);text-align:left;font-weight:600;min-width:0}
.pick span.n{min-width:0;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.pick[aria-pressed="true"]{border-color:var(--navy);background:var(--good-bg)}
.pick[aria-pressed="true"]::after{content:"✓";margin-left:auto;color:var(--good);font-weight:800}
.dock{position:sticky;bottom:0;background:var(--bg);border-top:1px solid var(--line);padding-block:12px calc(12px + env(safe-area-inset-bottom,0px));margin-top:4px;display:flex;gap:10px;align-items:center;flex-wrap:wrap}
.dock .count{flex:1;font-family:var(--display);font-weight:700;font-size:18px;font-variant-numeric:tabular-nums;min-width:0}
.prev{background:var(--surface);border:1px solid var(--line);border-radius:10px;padding:10px 12px;font-family:var(--display);font-size:17px;font-variant-numeric:tabular-nums}

/* Segnapunti */
.board{position:sticky;top:env(safe-area-inset-top,0px);z-index:5;background:var(--navy);color:var(--navy-fg);box-shadow:0 2px 10px rgba(0,0,0,.25)}
.board .wrap{padding-block:8px 10px;display:grid;gap:8px}
.topline{display:flex;align-items:center;gap:10px;font-family:var(--display);letter-spacing:.06em;text-transform:uppercase;font-size:14px}
.topline #setLog{flex:1;min-width:0;opacity:.8;font-variant-numeric:tabular-nums;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.score{display:grid;grid-template-columns:1fr auto 1fr;align-items:center;gap:10px}
.team{display:grid;gap:4px;justify-items:center;min-width:0}
.team-name{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.06em;font-size:14px;max-width:100%;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.pts{display:flex;align-items:center;gap:8px}
.pts .num.bump{animation:bump .45s ease-out}
@keyframes bump{0%{transform:scale(1.35);color:var(--yellow)}100%{transform:scale(1)}}
@media (prefers-reduced-motion:reduce){.pts .num.bump{animation:none}}
.pts .num{font-family:var(--display);font-weight:800;font-size:46px;line-height:1;min-width:2ch;text-align:center;font-variant-numeric:tabular-nums}
.pbtn{width:38px;height:38px;border-radius:50%;background:rgba(255,255,255,.14);font-size:22px;font-weight:600;display:grid;place-items:center;color:var(--navy-fg)}
.pbtn.plus{background:var(--yellow);color:var(--yellow-fg)}
.sets{font-family:var(--display);text-align:center;display:grid;gap:2px}
.sets .big{font-size:26px;font-weight:800;font-variant-numeric:tabular-nums}
@media (max-width:440px){.vtab{font-size:12.5px;letter-spacing:0;padding:8px 3px}.score{gap:4px}.pts{gap:4px}.pts .num{font-size:38px}.pbtn{width:32px;height:32px;font-size:19px}.sets .big{font-size:22px}}
.sets small{font-size:11px;letter-spacing:.1em;text-transform:uppercase;opacity:.75}
.board .btn{background:rgba(255,255,255,.14);color:var(--navy-fg)}
.board .btn.small{padding:5px 10px;font-size:12px}
.views{display:flex;gap:4px;background:rgba(255,255,255,.1);border-radius:10px;padding:4px}
.vtab{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.03em;font-size:14px;padding:8px 6px;flex:1 1 auto;min-width:0;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;border-radius:7px;color:var(--navy-fg)}
.vtab[aria-selected="true"]{background:var(--yellow);color:var(--yellow-fg)}
.actions{display:flex;gap:8px;flex-wrap:wrap}
.actions .primary{margin-left:auto}

/* Schede giocatrici */
.cards{display:grid;gap:12px}
.player{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:12px;display:grid;gap:10px}
.phead{display:flex;align-items:center;gap:10px;min-width:0}
.pname{flex:1;min-width:0;font-family:var(--display);font-weight:700;font-size:21px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.ptot{font-size:12px;color:var(--muted);font-variant-numeric:tabular-nums;white-space:nowrap}
.subbtn{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.05em;font-size:13px;padding:7px 10px;border-radius:8px;border:1px solid var(--line);white-space:nowrap}
.subbtn:hover{border-color:var(--navy)}
.cats{display:grid;grid-template-columns:2fr 2fr 1fr;gap:12px}
@media (max-width:680px){.cats{grid-template-columns:1fr}}
.cat{display:grid;gap:4px;min-width:0}
.cname{font-size:13px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.cname em{font-style:normal;font-weight:500;color:var(--muted);font-size:11px;text-transform:uppercase;letter-spacing:.06em}
.lv{display:grid;gap:5px}
.lv4{grid-template-columns:repeat(4,1fr)}.lv3{grid-template-columns:repeat(3,1fr)}
.tap{display:flex;align-items:center;justify-content:space-between;gap:4px;padding:10px 8px;border-radius:8px;font-weight:700;font-variant-numeric:tabular-nums;transition:transform .08s;min-width:0}
.tap:active{transform:scale(.95)}
.tap .s{font-family:var(--display);font-size:19px;font-weight:800;letter-spacing:-.02em}
.tap .n{font-family:var(--display);font-size:22px;font-weight:800;line-height:1}
.tap.pp{background:var(--good-strong);color:var(--on-strong)}
.tap.p{background:var(--good-bg);color:var(--good)}
.tap.m{background:var(--bad-bg);color:var(--bad)}
.tap.mm{background:var(--bad-strong);color:var(--on-strong)}
.flash{animation:fl .35s}
@keyframes fl{0%{box-shadow:0 0 0 0 var(--yellow)}100%{box-shadow:0 0 0 8px transparent}}
@media (prefers-reduced-motion:reduce){.flash,.mk-new{animation:none!important}.tap{transition:none}}
.benchline{color:var(--muted);font-size:13px}

/* Campo */
.courtview{display:grid;grid-template-columns:minmax(0,1fr) 270px;grid-template-areas:"court ctl" "court info";gap:12px 16px;align-items:start}
.cv-ctl{grid-area:ctl;display:grid;gap:10px}.cv-court{grid-area:court;min-width:0}.cv-info{grid-area:info;display:grid;gap:10px}
@media (max-width:680px){.courtview{grid-template-columns:1fr;grid-template-areas:"ctl" "court" "info"}}
.orow{display:grid;gap:5px}
.olab{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.08em;font-size:12px;color:var(--muted)}
.obtns{display:flex;flex-wrap:wrap;gap:6px}
.ob{min-width:42px;height:38px;padding:0 10px;border-radius:8px;border:2px solid var(--line);background:var(--surface);font-family:var(--display);font-weight:800;font-size:18px;font-variant-numeric:tabular-nums}
.ob[aria-pressed="true"]{background:var(--yellow);color:var(--yellow-fg);border-color:var(--yellow)}
.ob.f{font-size:15px}
.ob.f[aria-pressed="true"]{background:var(--navy);color:var(--navy-fg);border-color:var(--navy)}
.otab{background:var(--surface);border:1px solid var(--line);border-radius:10px;overflow:hidden}
.otab table{font-size:14px}.otab th,.otab td{padding:6px 8px}
.otab td:first-child,.otab th:first-child{position:static;display:table-cell}
.otab tr.best td{background:var(--good-bg)}.otab tr.worst td{background:var(--bad-bg)}
.orgb{cursor:pointer}
.demo-note{background:var(--yellow);color:var(--yellow-fg);border-radius:10px;padding:10px 12px;font-size:14px;font-weight:600;display:flex;gap:10px;align-items:center;flex-wrap:wrap}
.demo-note .btn{background:var(--navy);color:var(--navy-fg)}
.court{width:100%;max-width:520px;height:auto;display:block;margin:0 auto;touch-action:manipulation;user-select:none;-webkit-user-select:none}
.court[data-court]{cursor:crosshair}
.typesel{display:grid;gap:6px}
@media (max-width:680px){.typesel{grid-template-columns:1fr 1fr}}
.type{display:flex;align-items:center;gap:8px;padding:8px 10px;border-radius:10px;border:2px solid var(--line);background:var(--surface);text-align:left;font-weight:600;font-size:14px;min-width:0}
.type[aria-pressed="true"]{border-color:var(--fg)}
.type .tl{flex:1;min-width:0;line-height:1.15}
.type .tc{font-family:var(--display);font-weight:800;font-size:20px;font-variant-numeric:tabular-nums}
.ico{width:22px;height:22px;flex:none}
.csum{font-family:var(--display);font-size:17px;font-variant-numeric:tabular-nums;background:var(--surface);border:1px solid var(--line);border-radius:10px;padding:8px 12px}
.mk-new{animation:pop .3s ease-out;transform-box:fill-box;transform-origin:center}
@keyframes pop{0%{transform:scale(2);opacity:.2}100%{transform:scale(1);opacity:1}}

/* Pannello cambi */
.shade{position:fixed;inset:0;z-index:30;background:var(--shade);display:flex;align-items:flex-end;justify-content:center}
.sheet{background:var(--surface);width:100%;max-width:560px;max-height:85%;overflow-y:auto;border-radius:16px 16px 0 0;padding-block:16px calc(20px + env(safe-area-inset-bottom,0px));padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px));display:grid;gap:12px}
.sheet h2{font-size:22px}
.sheet h3{font-size:13px;color:var(--muted);letter-spacing:.1em}
.sheet .list{display:grid;gap:6px}
.sheet .opt{display:flex;align-items:center;gap:10px;padding:10px;border-radius:10px;border:1px solid var(--line);text-align:left;font-weight:600}
.sheet .opt:hover{border-color:var(--navy)}
.sheet .opt .rl{margin-left:auto;color:var(--muted);font-size:13px;font-weight:500}

/* Statistiche */
.overlay{position:fixed;inset:0;z-index:20;background:var(--bg);overflow-y:auto}
.overlay .wrap{padding-block:calc(16px + env(safe-area-inset-top,0px)) calc(40px + env(safe-area-inset-bottom,0px));display:grid;gap:14px}
.ohead{display:flex;align-items:center;gap:10px;flex-wrap:wrap}
.ohead h2{font-size:28px;flex:1;min-width:0}
#summary .ohead h2{flex-basis:100%}
.ohead .confirm{flex-basis:100%}
.tabs{display:flex;gap:6px;flex-wrap:wrap}
.tab{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.06em;padding:8px 14px;border-radius:999px;border:1px solid var(--line);background:var(--surface)}
.tab[aria-selected="true"]{background:var(--navy);color:var(--navy-fg);border-color:var(--navy)}
.final{background:var(--navy);color:var(--navy-fg);border-radius:12px;padding:14px;display:grid;gap:4px;font-family:var(--display)}
.final .res{font-size:30px;font-weight:800;font-variant-numeric:tabular-nums}
.final .det{font-size:15px;opacity:.85;font-variant-numeric:tabular-nums}
.tablebox{overflow-x:auto;background:var(--surface);border:1px solid var(--line);border-radius:12px}
table{border-collapse:collapse;width:100%;font-variant-numeric:tabular-nums;font-size:14px}
th,td{padding:8px 7px;text-align:center;border-bottom:1px solid var(--line);white-space:nowrap}
th{font-family:var(--display);font-size:12px;text-transform:uppercase;letter-spacing:.08em;color:var(--muted);font-weight:700}
thead tr:first-child th{border-bottom:0;padding-bottom:0}
td:first-child,th:first-child{text-align:left;position:sticky;left:0;background:var(--surface);z-index:1}
td:first-child{display:flex;align-items:center;gap:8px}
td:first-child .role{min-width:26px;height:26px;font-size:14px;border-radius:6px}
.g{color:var(--good);font-weight:600}.b{color:var(--bad);font-weight:600}
td.pct{font-weight:700}
td.dim{color:var(--muted)}
tr.tot td{font-weight:700;border-top:2px solid var(--fg);border-bottom:0}
.gsep{border-left:1px solid var(--line)}
.arch-item{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:12px 14px;display:grid;gap:6px}
.arch-top{display:flex;align-items:center;gap:8px}
.arch-date{flex:1;color:var(--muted);font-size:13px;text-transform:capitalize}
.pill{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.08em;font-size:12px;padding:3px 9px;border-radius:999px;background:var(--line)}
.pill.win{background:var(--good-bg);color:var(--good)}.pill.loss{background:var(--bad-bg);color:var(--bad)}
.arch-res{font-family:var(--display);font-weight:800;font-size:24px;font-variant-numeric:tabular-nums}
.arch-sets{font-family:var(--display);font-size:15px;color:var(--muted);font-variant-numeric:tabular-nums}
.arch-act{display:flex;gap:8px;flex-wrap:wrap;align-items:center;margin-top:4px;font-size:14px}
.empty{color:var(--muted);padding:20px;text-align:center}
.maps{display:grid;grid-template-columns:1fr 1fr;gap:14px}
@media (max-width:680px){.maps{grid-template-columns:1fr}}
.map{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:12px;display:grid;gap:10px;min-width:0}
.map h3{font-size:18px}
.legend{display:grid;grid-template-columns:1fr 1fr;gap:6px 12px;font-size:13px}
.legend span{display:flex;align-items:center;gap:6px;min-width:0}
.legend b{font-family:var(--display);font-size:17px;margin-left:auto;font-variant-numeric:tabular-nums}
.legend .ico{width:18px;height:18px}
</style>

<!-- FASE 1: ROSA -->
<section id="phRoster" hidden>
  <div class="bar"><div class="wrap"><h1>Rosa della squadra</h1></div></div>
  <div class="wrap content">
    <p class="hint">Inserisci nome e ruolo di ogni giocatrice. Le righe senza nome vengono ignorate.</p>
    <div class="rows" id="rosterRows"></div>
    <div><button class="btn" id="addRow">+ Aggiungi giocatrice</button></div>
    <p class="err" id="rosterErr" hidden></p>
    <div class="dock"><span class="count" id="rosterCount"></span><button class="btn primary" id="rosterNext">Avanti: formazione</button></div>
  </div>
</section>

<!-- FASE 2: FORMAZIONE -->
<section id="phLineup" hidden>
  <div class="bar"><div class="wrap"><h1 id="lineupTitle">Formazione set 1</h1>
    <button class="btn" data-undo>↶ Annulla</button>
    <button class="btn" id="editRoster">Modifica rosa</button>
    <button class="btn" data-open-arch>Partite giocate</button>
    <button class="btn primary" id="lineupStats" hidden>Fine partita · Statistiche</button>
  </div></div>
  <div class="wrap content">
    <div class="prev" id="prevSet" hidden></div>
    <div class="teamsbox" id="teamsBox">
      <label for="teamHome">La nostra squadra<input id="teamHome" data-team="home" placeholder="Noi"></label>
      <label for="teamAway">Avversari<input id="teamAway" data-team="away" placeholder="Avversari"></label>
    </div>
    <p class="hint">Tocca chi parte in campo: 6 giocatrici più l'eventuale libero.</p>
    <div id="lineupGroups" style="display:grid;gap:16px"></div>
    <div class="dock"><span class="count" id="lineupCount"></span><button class="btn primary" id="lineupGo">Inizia il set</button></div>
  </div>
</section>

<!-- FASE 3: PARTITA -->
<section id="phMatch" hidden>
  <header class="board"><div class="wrap">
    <div class="topline"><span id="setLabel">Set 1</span><span id="setLog"></span><button class="btn small" data-undo>↶ Annulla</button></div>
    <div class="score">
      <div class="team"><span class="team-name" id="nameHome">Noi</span>
        <div class="pts"><span class="num" id="homePts">0</span><button class="pbtn plus" data-score="home" data-d="1" aria-label="Punto alla nostra squadra">+</button></div></div>
      <div class="sets"><span class="big" id="setsScore">0–0</span><small>Set vinti</small></div>
      <div class="team"><span class="team-name" id="nameAway">Avversari</span>
        <div class="pts"><span class="num" id="awayPts">0</span><button class="pbtn plus" data-score="away" data-d="1" aria-label="Punto agli avversari">+</button></div></div>
    </div>
    <div class="views" role="tablist">
      <button class="vtab" role="tab" data-view="players">Giocatrici</button>
      <button class="vtab" role="tab" data-view="att">Attacchi</button>
      <button class="vtab" role="tab" data-view="dif">Difese</button>
      <button class="vtab" role="tab" data-view="bat">Battute</button>
      <button class="vtab" role="tab" data-view="ric">Ricezioni</button>
    </div>
  </div></header>
  <div class="wrap content">
    <div class="actions">
      <button class="btn" id="closeSet">Chiudi set</button>
      <button class="btn" id="newMatch">Nuova partita</button>
      <button class="btn" data-open-arch>Partite giocate</button>
      <button class="btn primary" id="matchStats">Fine partita · Statistiche</button>
    </div>
    <div class="confirm" id="newConfirm" hidden>Nuova partita con la stessa rosa? Questa partita viene salvata in "Partite giocate". <button class="btn danger" id="newYes">Sì, nuova partita</button><button class="btn" id="newNo">No</button></div>

    <div id="vPlayers" style="display:grid;gap:12px">
      <p class="hint">Il punteggio va da solo: ++ in attacco o in battuta dà il punto a noi, −− in attacco, ricezione o battuta lo dà all'avversaria. Per gli altri punti (errori avversari, muri, attacchi non difesi) usa + accanto al punteggio della squadra. "Cambio" propone prima le riserve dello stesso ruolo.</p>
      <div class="cards" id="cards"></div>
      <p class="benchline" id="benchLine"></p>
    </div>

    <div id="vAtt" class="courtview">
      <div class="cv-ctl">
        <h3>Attacchi · campo avversario</h3>
        <div class="orow"><span class="olab">Da dove parte il nostro attacco</span><div class="obtns" id="org-att"></div></div>
        <div class="typesel" id="sel-att"></div>
      </div>
      <div class="cv-court"><svg class="court" id="court-att" data-court="att" role="img" aria-label="Attacchi · campo avversario"></svg></div>
      <div class="cv-info">
        <div class="orow"><span class="olab">Mostra sul campo</span><div class="obtns" id="flt-att"></div></div>
        <div class="csum" id="sum-att"></div>
        <div class="otab" id="otab-att"></div>
        <p class="hint">Scegli zona di partenza e tipo, poi tocca il punto in cui è caduta la palla. Puoi scegliere la zona anche toccando i cerchi numerati sul campo. I simboli ripartono da zero a ogni set.</p>
      </div>
    </div>

    <div id="vDif" class="courtview">
      <div class="cv-ctl">
        <h3>Difese · nostro campo</h3>
        <div class="orow"><span class="olab">Da dove attacca l'avversaria</span><div class="obtns" id="org-dif"></div></div>
        <div class="typesel" id="sel-dif"></div>
      </div>
      <div class="cv-court"><svg class="court" id="court-dif" data-court="dif" role="img" aria-label="Difese · nostro campo"></svg></div>
      <div class="cv-info">
        <div class="orow"><span class="olab">Mostra sul campo</span><div class="obtns" id="flt-dif"></div></div>
        <div class="csum" id="sum-dif"></div>
        <div class="otab" id="otab-dif"></div>
        <p class="hint">Scegli zona di partenza dell'attacco avversario e tipo, poi tocca il punto in cui è arrivata la palla. Puoi scegliere la zona anche toccando i cerchi numerati sul campo. I simboli ripartono da zero a ogni set.</p>
      </div>
    </div>

    <div id="vBat" class="courtview">
      <div class="cv-ctl">
        <h3>Battute · campo avversario</h3>
        <div class="typesel" id="sel-bat"></div>
      </div>
      <div class="cv-court"><svg class="court" id="court-bat" data-court="bat" role="img" aria-label="Battute · campo avversario"></svg></div>
      <div class="cv-info">
        <div class="csum" id="sum-bat"></div>
        <p class="hint">Scegli il tipo, poi tocca il punto in cui è caduta la nostra battuta. I simboli ripartono da zero a ogni set.</p>
      </div>
    </div>

    <div id="vRic" class="courtview">
      <div class="cv-ctl">
        <h3>Ricezioni · nostro campo</h3>
        <div class="typesel" id="sel-ric"></div>
      </div>
      <div class="cv-court"><svg class="court" id="court-ric" data-court="ric" role="img" aria-label="Ricezioni · nostro campo"></svg></div>
      <div class="cv-info">
        <div class="csum" id="sum-ric"></div>
        <p class="hint">Scegli il tipo, poi tocca il punto in cui è arrivata la battuta avversaria. I simboli ripartono da zero a ogni set.</p>
      </div>
    </div>
  </div>
</section>

<!-- CAMBI -->
<div class="shade" id="subShade" hidden><div class="sheet" role="dialog" aria-modal="true" aria-labelledby="subTitle">
  <h2 id="subTitle">Cambio</h2>
  <div id="subBody" style="display:grid;gap:12px"></div>
  <button class="btn" id="subCancel">Annulla</button>
</div></div>

<!-- STATISTICHE -->
<section class="overlay" id="summary" hidden><div class="wrap">
  <div class="ohead"><h2 id="sumTitle">Statistiche partita</h2>
    <button class="btn navy" id="backBtn">Torna alla partita</button>
    <button class="btn" id="sumArch" data-open-arch>Partite giocate</button>
    <button class="btn primary" id="sumNew">Nuova partita</button>
    <div class="confirm" id="sumConfirm" hidden>Iniziare una nuova partita con la stessa rosa? Questa partita viene salvata in "Partite giocate".
      <button class="btn danger" id="sumYes">Sì, nuova partita</button><button class="btn" id="sumNo">No</button></div>
  </div>
  <div class="tabs" id="tabs" role="tablist"></div>
  <div class="final" id="finalBox"></div>
  <div class="tablebox" id="tableBox"></div>
  <p class="hint">% = azioni positive (++ e +, oppure ✓) sul totale della categoria. Nel set compaiono le giocatrici scese in campo in quel set; nel totale quelle che hanno giocato almeno un set.</p>
  <div class="maps" id="maps"></div>
</div></section>

<!-- ARCHIVIO -->
<section class="overlay" id="archive" hidden><div class="wrap">
  <div class="ohead"><h2>Partite giocate</h2><button class="btn navy" id="archClose">Chiudi</button></div>
  <div id="archList" style="display:grid;gap:10px"></div>
</div></section>

<script>
const ROLES=[["Palleggiatrice","P"],["Schiacciatrice","S"],["Centrale","C"],["Opposto","O"],["Libero","L"]];
const RCODE=Object.fromEntries(ROLES), RORDER=Object.fromEntries(ROLES.map((r,i)=>[r[0],i]));
const LV4=[{s:"++",c:"pp",pos:1},{s:"+",c:"p",pos:1},{s:"−",c:"m"},{s:"−−",c:"mm"}];
const LV3=[{s:"++",c:"pp",pos:1},{s:"+",c:"p",pos:1},{s:"−−",c:"mm"}];
const CATS=[{k:"att",name:"Attacco",lv:LV4},{k:"ric",name:"Ricezione",lv:LV4},{k:"bat",name:"Battuta",lv:LV3,out:true}];
const TYPES={
  att:[{k:"a",name:"Attacco",sh:"circle",col:"blue"},{k:"ap",name:"Attacco punto",sh:"star",col:"green"},
       {k:"p",name:"Pallonetto",sh:"tri",col:"orange"},{k:"pp",name:"Pallonetto punto",sh:"diamond",col:"purple"}],
  dif:[{k:"pa",name:"Attacco difeso",sh:"circle",col:"green"},{k:"na",name:"Attacco punto",sh:"cross",col:"red"},
       {k:"pp",name:"Pallonetto difeso",sh:"tri",col:"blue"},{k:"np",name:"Pallonetto punto",sh:"diamond",col:"orange"}]
};
TYPES.bat=[{k:"ace",name:"Ace",sh:"star",col:"green"},{k:"bb",name:"Battuta buona",sh:"circle",col:"blue"}];
TYPES.ric=[{k:"rp",name:"Ricezione presa",sh:"circle",col:"green"},{k:"ra",name:"Ace subito",sh:"cross",col:"red"}];
const GOODTYPES={att:["ap","pp"],dif:["pa","pp"],bat:["ace"],ric:["rp"]};
const KINDS=["att","dif","bat","ric"],OPP=k=>k==="att"||k==="bat",HASORG=k=>k==="att"||k==="dif";
const MAPTITLE={att:"Attacchi · campo avversario",dif:"Difese · nostro campo",bat:"Battute · campo avversario",ric:"Ricezioni · nostro campo"};
const KEY="tabellino-volley-v3";
const blankStats=()=>Object.fromEntries(CATS.map(c=>[c.k,c.lv.map(()=>0)]));
const newSet=()=>({home:0,away:0,closed:false,stats:{},played:[],marks:{att:[],dif:[],bat:[],ric:[]}});
function fresh(){
  return {phase:"roster",players:Array.from({length:13},(_,i)=>({id:"p"+(i+1),name:"",role:""})),nextId:14,
    teams:{home:"",away:""},sets:[newSet()],cur:0,court:[],draft:[],view:"players",sel:{att:"a",dif:"pa"},hist:[]};
}
let S;try{S=JSON.parse(localStorage.getItem(KEY))}catch(e){}
if(!S||!S.players){
  S=fresh();
  try{const o=JSON.parse(localStorage.getItem("tabellino-volley-v2"));
    if(o&&o.players){S.players=o.players;S.nextId=o.nextId||S.nextId;if(o.teams)S.teams=o.teams;
      const ok=o.players.filter(p=>p.name.trim()&&p.role).length>=6;S.phase=ok?"lineup":"roster";S.draft=[...(o.court||[])];}
  }catch(e){}
}
S.teams=S.teams||{home:"",away:""};S.view=S.view||"players";S.sel={att:"a",dif:"pa",bat:"ace",ric:"rp",...(S.sel||{})};S.org=S.org||{att:"4",dif:"4"};S.flt=S.flt||{att:"all",dif:"all"};S.hist=S.hist||[];
const fixBat=sets=>sets.forEach(s=>{s.marks=s.marks||{};KINDS.forEach(k=>s.marks[k]=s.marks[k]||[]);Object.values(s.stats||{}).forEach(o=>{if(o.bat&&o.bat.length===2)o.bat=[0,o.bat[0],o.bat[1]]})});
fixBat(S.sets);
S.matchId=S.matchId||("m"+Date.now());
const AKEY="tabellino-volley-archivio";let ARCH=[];try{ARCH=JSON.parse(localStorage.getItem(AKEY))||[]}catch(e){}
ARCH.forEach(a=>fixBat(a.sets));
const saveArch=()=>{try{localStorage.setItem(AKEY,JSON.stringify(ARCH))}catch(e){}};
const save=()=>{try{localStorage.setItem(KEY,JSON.stringify(S))}catch(e){}};
const $=id=>document.getElementById(id);
const esc=s=>String(s).replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]));
const tn=k=>esc((S.teams[k]||"").trim()||(k==="home"?"Noi":"Avversari"));
const byId=id=>S.players.find(p=>p.id===id);
const roleSort=(a,b)=>(RORDER[byId(a)?.role]??9)-(RORDER[byId(b)?.role]??9);
const badge=p=>`<span class="role ${RCODE[p.role]||""}" title="${esc(p.role)}">${RCODE[p.role]||"?"}</span>`;
const pct=(g,t)=>t?Math.round(g/t*100)+"%":"–";

function snap(){const {hist,...rest}=S;S.hist.push(JSON.stringify(rest));if(S.hist.length>200)S.hist.shift()}
function commit(fn,after=render){snap();fn();save();after()}
function undo(){const h=S.hist.pop();if(!h)return;const hist=S.hist;S=JSON.parse(h);S.hist=hist;save();if(ARCH.some(a=>a.id===S.matchId)){ARCH=ARCH.filter(a=>a.id!==S.matchId);saveArch()}closeSub();render()}
function renderUndo(){document.querySelectorAll("[data-undo]").forEach(b=>b.disabled=!S.hist.length)}

function render(){
  $("phRoster").hidden=S.phase!=="roster";$("phLineup").hidden=S.phase!=="lineup";$("phMatch").hidden=S.phase!=="match";
  if(S.phase==="roster")renderRoster();
  if(S.phase==="lineup")renderLineup();
  if(S.phase==="match")renderMatch();
  renderUndo();
}

/* ---------- ROSA ---------- */
function renderRoster(){
  $("rosterRows").innerHTML=S.players.map((p,i)=>`<div class="rrow">
    <span class="idx">${i+1}</span>
    <input id="rn-${p.id}" data-rid="${p.id}" data-f="name" placeholder="Nome giocatrice" value="${esc(p.name)}" aria-label="Nome giocatrice ${i+1}">
    <select id="rr-${p.id}" data-rid="${p.id}" data-f="role" aria-label="Ruolo giocatrice ${i+1}">
      <option value="">Ruolo…</option>${ROLES.map(r=>`<option${p.role===r[0]?" selected":""}>${r[0]}</option>`).join("")}
    </select>
    <button class="del" data-del="${p.id}" aria-label="Rimuovi riga">×</button></div>`).join("");
  rosterCount();
}
function rosterCount(){const n=S.players.filter(p=>p.name.trim()).length;$("rosterCount").textContent=n+(n===1?" giocatrice":" giocatrici")}
$("addRow").onclick=()=>{S.players.push({id:"p"+(S.nextId++),name:"",role:""});save();renderRoster();$("rn-"+S.players.at(-1).id).focus()};
$("rosterNext").onclick=()=>{
  const named=S.players.filter(p=>p.name.trim());
  const noRole=named.filter(p=>!p.role);
  let msg="";
  if(named.length<6)msg="Servono almeno 6 giocatrici con il nome.";
  else if(noRole.length)msg="Manca il ruolo per: "+noRole.map(p=>p.name.trim()).join(", ")+".";
  $("rosterErr").hidden=!msg;$("rosterErr").textContent=msg;if(msg)return;
  commit(()=>{
    S.players=named.map(p=>({...p,name:p.name.trim()}));
    const ok=id=>!!byId(id);S.court=S.court.filter(ok);S.draft=(S.draft||[]).filter(ok);
    S.phase="lineup";
  });
  scrollTo(0,0);
};

/* ---------- FORMAZIONE ---------- */
function renderLineup(){
  if(!S.draft)S.draft=[...S.court];
  $("lineupTitle").textContent="Formazione set "+(S.cur+1);
  const prev=S.sets[S.cur-1];
  $("prevSet").hidden=!prev;
  if(prev)$("prevSet").innerHTML=`Set ${S.cur} chiuso: ${tn("home")} ${prev.home} – ${prev.away} ${tn("away")}`;
  $("teamsBox").hidden=S.cur>0;
  $("teamHome").value=S.teams.home;$("teamAway").value=S.teams.away;
  $("lineupStats").hidden=S.cur===0;
  $("editRoster").hidden=S.cur>0;
  $("lineupGroups").innerHTML=ROLES.map(([r])=>{
    const ps=S.players.filter(p=>p.role===r);if(!ps.length)return"";
    return `<div class="rgroup"><h3>${r}</h3><div class="chips">${ps.map(p=>
      `<button class="pick" data-pick="${p.id}" aria-pressed="${S.draft.includes(p.id)}">${badge(p)}<span class="n">${esc(p.name)}</span></button>`).join("")}</div></div>`;
  }).join("");
  const lib=S.draft.filter(id=>byId(id)?.role==="Libero").length,n=S.draft.length-lib;
  $("lineupCount").textContent=`${n}/6 in campo`+(lib?` + ${lib} libero`:"");
  $("lineupGo").disabled=!(n===6&&lib<=2);
}
$("lineupGo").onclick=()=>{commit(()=>{
  S.court=[...S.draft].sort(roleSort);
  const s=S.sets[S.cur];s.played=[...new Set([...s.played,...S.court])];
  S.phase="match";S.draft=null;if(!S.date)S.date=Date.now();
});scrollTo(0,0)};
$("editRoster").onclick=()=>commit(()=>{S.phase="roster"});
$("lineupStats").onclick=openSummary;

/* ---------- PARTITA ---------- */
const curSet=()=>S.sets[S.cur];
const stOf=(pid,s=curSet())=>s.stats[pid]||(s.stats[pid]=blankStats());
const posNeg=st=>{let p=0,n=0;CATS.forEach(c=>c.lv.forEach((l,j)=>l.pos?p+=st[c.k][j]:n+=st[c.k][j]));return[p,n]};
const totLabel=st=>{const [p,n]=posNeg(st);return p+n?`${p} pos · ${n} neg`:""};
function renderMatch(){
  renderScore();
  document.querySelectorAll(".vtab").forEach(b=>b.setAttribute("aria-selected",b.dataset.view===S.view));
  $("vPlayers").hidden=S.view!=="players";$("vAtt").hidden=S.view!=="att";$("vDif").hidden=S.view!=="dif";$("vBat").hidden=S.view!=="bat";$("vRic").hidden=S.view!=="ric";
  renderCards();KINDS.forEach(k=>renderCourt(k));
}
function renderCards(){
  $("cards").innerHTML=S.court.map(id=>{const p=byId(id);if(!p)return"";const st=curSet().stats[id]||blankStats();
    return `<article class="player" id="pl-${id}">
      <div class="phead">${badge(p)}<span class="pname">${esc(p.name)}</span><span class="ptot" id="tot-${id}">${totLabel(st)}</span>
        <button class="subbtn" data-sub="${id}">⇄ Cambio</button></div>
      <div class="cats">${CATS.map(c=>`<div class="cat"><span class="cname">${c.name}${c.out?" <em>fuori campo</em>":""}</span>
        <div class="lv lv${c.lv.length}">${c.lv.map((l,j)=>
          `<button class="tap ${l.c}" data-p="${id}" data-c="${c.k}" data-r="${j}" aria-label="${c.name} ${l.s}, ${esc(p.name)}"><span class="s">${l.s}</span><span class="n">${st[c.k][j]}</span></button>`).join("")}
        </div></div>`).join("")}</div></article>`;}).join("");
  const bench=S.players.filter(p=>!S.court.includes(p.id));
  $("benchLine").textContent=bench.length?"In panchina: "+bench.map(p=>p.name).join(", "):"";
}
function updateCard(id){
  const el=$("pl-"+id),st=stOf(id);
  el.querySelectorAll(".tap").forEach(b=>b.querySelector(".n").textContent=st[b.dataset.c][+b.dataset.r]);
  $("tot-"+id).textContent=totLabel(st);
}
function bump(side){const el=$(side==="home"?"homePts":"awayPts");el.classList.remove("bump");void el.offsetWidth;el.classList.add("bump")}
function renderScore(){
  $("nameHome").innerHTML=tn("home");$("nameAway").innerHTML=tn("away");
  const s=curSet();$("homePts").textContent=s.home;$("awayPts").textContent=s.away;
  const done=S.sets.filter(x=>x.closed);
  $("setsScore").textContent=`${done.filter(x=>x.home>x.away).length}–${done.filter(x=>x.away>x.home).length}`;
  $("setLabel").textContent="Set "+(S.cur+1);
  $("setLog").textContent=done.map(x=>x.home+"–"+x.away).join(" · ");
  $("closeSet").disabled=!(s.home||s.away);
  renderUndo();
}
$("closeSet").onclick=()=>commit(()=>{curSet().closed=true;S.sets.push(newSet());S.cur++;S.draft=[...S.court];S.phase="lineup"});
$("newMatch").onclick=()=>{$("newConfirm").hidden=false};
$("newNo").onclick=()=>{$("newConfirm").hidden=true};
function startNewMatch(){archiveCurrent();commit(()=>{S.matchId="m"+Date.now();S.date=null;S.sets=[newSet()];S.cur=0;S.draft=[...(S.court.length?S.court:S.draft||[])];S.court=[];S.view="players";S.phase="lineup"});scrollTo(0,0)}
$("newYes").onclick=()=>{$("newConfirm").hidden=true;startNewMatch()};
$("matchStats").onclick=openSummary;

/* ---------- CAMPO ---------- */
const NS='http://www.w3.org/2000/svg';
const VB={att:"-1.5 -1.5 12 14.4",dif:"-1.5 -3.4 12 14.4",bat:"-1.5 -1.5 12 12.3",ric:"-1.5 -1.8 12 12.3"};
const ORIG=["4","3","2","1","6"];
const OX={att:{"4":1.2,"3":4.5,"2":7.8,"1":7.8,"6":4.5},dif:{"4":7.8,"3":4.5,"2":1.2,"1":1.2,"6":4.5}};
const oPos=(k,o)=>({x:OX[k][o],d:["4","3","2"].includes(o)?-.85:-2.25});
const OLAB={"?":"Non vista"};
const toY=(k,d)=>OPP(k)?9-d:d, fromY=(k,y)=>OPP(k)?9-y:y;
const ZONES={att:{front:[2,3,4],back:[1,6,5]},dif:{front:[4,3,2],back:[5,6,1]}};ZONES.bat=ZONES.att;ZONES.ric=ZONES.dif;
function shape(t,x,y,r=.34,cls=""){
  const f=`style="fill:var(--mk-${t.col});stroke:var(--mk-stroke);stroke-width:${r*.2}"`,c=cls?` class="${cls}"`:"";
  const P=pts=>pts.map(p=>p.map(v=>v.toFixed(3)).join(",")).join(" ");
  if(t.sh==="circle")return `<circle${c} cx="${x}" cy="${y}" r="${r}" ${f}/>`;
  if(t.sh==="tri"){const R=r*1.3;return `<polygon${c} points="${P([[x,y-R],[x+R*.95,y+R*.7],[x-R*.95,y+R*.7]])}" ${f}/>`}
  if(t.sh==="diamond"){const R=r*1.3;return `<polygon${c} points="${P([[x,y-R],[x+R*.8,y],[x,y+R],[x-R*.8,y]])}" ${f}/>`}
  if(t.sh==="star"){const pts=[];for(let i=0;i<10;i++){const a=-Math.PI/2+i*Math.PI/5,R=i%2?r*.62:r*1.45;pts.push([x+R*Math.cos(a),y+R*Math.sin(a)])}return `<polygon${c} points="${P(pts)}" ${f}/>`}
  if(t.sh==="cross"){const R=r*1.05,l=(w,col)=>`<path d="M${x-R} ${y-R}L${x+R} ${y+R}M${x+R} ${y-R}L${x-R} ${y+R}" style="stroke:${col};stroke-width:${w};stroke-linecap:round;fill:none"/>`;
    return `<g${c}>${l(r*.75,"var(--mk-stroke)")}${l(r*.42,`var(--mk-${t.col})`)}</g>`}
}
const icon=t=>`<svg class="ico" viewBox="-1 -1 2 2" aria-hidden="true">${shape(t,0,0,.5)}</svg>`;
function courtInner(k,marks,newIdx=-1,opt={}){
  const Y=d=>toY(k,d),top=(a,b)=>Math.min(Y(a),Y(b));
  let s=`<rect x="-1.5" y="${top(0,10.5)}" width="12" height="10.5" style="fill:var(--free)"/>`;
  s+=`<rect x="0" y="${top(0,9)}" width="9" height="9" style="fill:var(--court)"/>`;
  s+=`<g style="stroke:var(--zone);stroke-width:.05;stroke-dasharray:.25 .2">`+[3,6].map(x=>`<line x1="${x}" x2="${x}" y1="${Y(0)}" y2="${Y(9)}"/>`).join("")+`</g>`;
  s+=`<g style="fill:var(--zone);font:700 1.5px sans-serif;text-anchor:middle;dominant-baseline:central">`+
    ZONES[k].front.map((z,i)=>`<text x="${1.5+i*3}" y="${Y(1.5)}">${z}</text>`).join("")+
    ZONES[k].back.map((z,i)=>`<text x="${1.5+i*3}" y="${Y(6)}">${z}</text>`).join("")+`</g>`;
  s+=`<g style="stroke:var(--courtline);stroke-width:.1;fill:none"><rect x="0" y="${top(0,9)}" width="9" height="9"/><line x1="0" x2="9" y1="${Y(3)}" y2="${Y(3)}"/></g>`;
  s+=`<line x1="-.7" x2="9.7" y1="${Y(0)}" y2="${Y(0)}" style="stroke:var(--net);stroke-width:.2"/>`;
  s+=`<circle cx="-.7" cy="${Y(0)}" r=".14" style="fill:var(--net)"/><circle cx="9.7" cy="${Y(0)}" r=".14" style="fill:var(--net)"/>`;
  const T=Object.fromEntries(TYPES[k].map(t=>[t.k,t]));
  if(!HASORG(k)){
    s+=`<text x="4.5" y="${Y(0)+(OPP(k)?.85:-.5)}" style="fill:var(--muted);font:700 .55px sans-serif;text-anchor:middle;letter-spacing:.15px">RETE</text>`;
    return s+marks.map((m,i)=>T[m.t]?shape(T[m.t],m.x,Y(m.d),.22,i===newIdx?"mk-new":""):"").join("");
  }
  s+=`<text x="-1.3" y="${Y(0)+(k==="att"?.55:-.3)}" style="fill:var(--muted);font:700 .42px sans-serif;letter-spacing:.1px">RETE</text>`;
  s+=`<text x="${k==="att"?-1.3:10.3}" y="${k==="att"?12.55:-3.02}" style="fill:var(--muted);font:700 .36px sans-serif;text-anchor:${k==="att"?"start":"end"}">${k==="att"?"NOSTRO CAMPO":"CAMPO AVVERSARIO"}</text>`;
  const flt=opt.filter||"all",shown=marks.map((m,i)=>[m,i]).filter(([m])=>flt==="all"||m.o===flt);
  ORIG.forEach(o=>{const p=oPos(k,o),sel=opt.org===o,dim=flt!=="all"&&flt!==o;
    s+=`<g${opt.interactive?` class="orgb" data-org="${k}:${o}"`:""} style="opacity:${dim?.35:1}"><circle cx="${p.x}" cy="${Y(p.d)}" r=".5" style="fill:${sel?"var(--yellow)":"var(--surface)"};stroke:${sel?"var(--yellow-fg)":"var(--muted)"};stroke-width:.06"/>
      <text x="${p.x}" y="${Y(p.d)}" style="fill:${sel?"var(--yellow-fg)":"var(--fg)"};font:800 .62px sans-serif;text-anchor:middle;dominant-baseline:central">${o}</text></g>`});
  s+=`<g style="stroke-linecap:round;fill:none">`+shown.map(([m])=>{if(!T[m.t]||!OX[k][m.o])return"";const p=oPos(k,m.o);
    return `<line x1="${p.x}" y1="${Y(p.d)}" x2="${m.x}" y2="${Y(m.d)}" style="stroke:var(--mk-${T[m.t].col});stroke-width:.07;opacity:${flt==="all"?.28:.6}"/>`}).join("")+`</g>`;
  s+=shown.map(([m,i])=>T[m.t]?shape(T[m.t],m.x,Y(m.d),.22,i===newIdx?"mk-new":""):"").join("");
  return s;
}
function otab(k,marks){
  const rows=[...ORIG,"?"].map(o=>{const ms=marks.filter(m=>(m.o||"?")===o),g=ms.filter(m=>GOODTYPES[k].includes(m.t)).length;return{o,n:ms.length,g}}).filter(r=>r.n);
  if(!rows.length)return `<p class="hint" style="padding:8px 10px">Ancora nessun ${k==="att"?"attacco":"attacco avversario"} segnato.</p>`;
  const cand=rows.filter(r=>r.o!=="?"&&r.n>=3),best=cand.length<2?null:cand.sort((a,b)=>(k==="att"?b.g/b.n-a.g/a.n:a.g/a.n-b.g/b.n))[0];
  return `<table><thead><tr><th>Da</th><th>${k==="att"?"Attacchi":"Subiti"}</th><th>${k==="att"?"Punti":"Difesi"}</th><th>%</th></tr></thead><tbody>${
    rows.map(r=>`<tr${best&&r===best?(k==="att"?' class="best"':' class="worst"'):""}><td><b>${r.o==="?"?"?":"Posto "+r.o}</b></td><td>${r.n}</td><td>${r.g}</td><td class="pct">${pct(r.g,r.n)}</td></tr>`).join("")}</tbody></table>`;
}
const orgBtns=(k)=>[...ORIG,"?"].map(o=>`<button class="ob" data-orgbtn="${k}:${o}" aria-pressed="${S.org[k]===o}" title="${o==="?"?"Zona non vista":"Posto "+o}">${o}</button>`).join("");
const fltBtns=(k,cur,attr)=>[["all","Tutti"],...ORIG.map(o=>[o,o])].map(([v,l])=>`<button class="ob f" data-${attr}="${k}:${v}" aria-pressed="${cur===v}">${l}</button>`).join("");
function counts(k,marks){const o=Object.fromEntries(TYPES[k].map(t=>[t.k,0]));marks.forEach(m=>{if(m.t in o)o[m.t]++});return o}
function sumLine(k,marks,flt="all"){
  if(flt!=="all")marks=marks.filter(m=>m.o===flt);
  const pre=flt==="all"?"":`Da posto ${flt} · `;
  const c=counts(k,marks),tot=marks.length,g=GOODTYPES[k].reduce((a,t)=>a+c[t],0);
  return pre+`${{att:"Punti in attacco",dif:"Palloni difesi",bat:"Ace",ric:"Ricezioni prese"}[k]}: <b>${g}</b> su ${tot} (${pct(g,tot)})`;
}
function renderCourt(k,newIdx=-1){
  const marks=curSet().marks[k],svg=$("court-"+k);
  svg.setAttribute("viewBox",VB[k]);const h=HASORG(k);svg.innerHTML=courtInner(k,marks,newIdx,h?{filter:S.flt[k],org:S.org[k],interactive:true}:{});
  if(h){$("org-"+k).innerHTML=orgBtns(k);$("flt-"+k).innerHTML=fltBtns(k,S.flt[k],"flt");$("otab-"+k).innerHTML=otab(k,marks)}
  const c=counts(k,marks);
  $("sel-"+k).innerHTML=TYPES[k].map(t=>`<button class="type" data-type="${k}:${t.k}" aria-pressed="${S.sel[k]===t.k}">${icon(t)}<span class="tl">${t.name}</span><span class="tc">${c[t.k]}</span></button>`).join("");
  $("sum-"+k).innerHTML=sumLine(k,marks,h?S.flt[k]:"all");
}
function courtClick(svg,e){
  const k=svg.dataset.court,pt=svg.createSVGPoint();pt.x=e.clientX;pt.y=e.clientY;
  const p=pt.matrixTransform(svg.getScreenCTM().inverse()),x=p.x,d=fromY(k,p.y);
  if(d<0||d>10.5||x<-1.5||x>10.5)return;
  const h=HASORG(k);if(h&&S.flt[k]!=="all"&&S.flt[k]!==S.org[k])S.flt[k]="all";
  commit(()=>{curSet().marks[k].push({x:+x.toFixed(2),d:+d.toFixed(2),t:S.sel[k],...(h?{o:S.org[k]}:{})})},()=>{renderCourt(k,curSet().marks[k].length-1);renderUndo()});
}

/* ---------- CAMBI ---------- */
let subOut=null;
function openSub(id){
  subOut=id;const out=byId(id);
  const bench=S.players.filter(p=>!S.court.includes(p.id));
  const same=bench.filter(p=>p.role===out.role),other=bench.filter(p=>p.role!==out.role).sort((a,b)=>RORDER[a.role]-RORDER[b.role]);
  const opt=p=>`<button class="opt" data-in="${p.id}">${badge(p)}<span>${esc(p.name)}</span><span class="rl">${esc(p.role)}</span></button>`;
  $("subTitle").textContent="Esce "+out.name;
  $("subBody").innerHTML=!bench.length?'<p class="hint">Non ci sono giocatrici in panchina.</p>':
    (same.length?`<h3>Stesso ruolo · ${esc(out.role)}</h3><div class="list">${same.map(opt).join("")}</div>`:"")+
    (other.length?`<h3>Altri ruoli</h3><div class="list">${other.map(opt).join("")}</div>`:"");
  $("subShade").hidden=false;
  ($("subBody").querySelector(".opt")||$("subCancel")).focus();
}
function closeSub(){$("subShade").hidden=true;subOut=null}
$("subCancel").onclick=closeSub;
$("subShade").addEventListener("click",e=>{if(e.target===$("subShade"))closeSub()});
document.addEventListener("keydown",e=>{if(e.key==="Escape"){if(!$("subShade").hidden)closeSub();else if(!$("summary").hidden)$("summary").hidden=true}});

/* ---------- EVENTI ---------- */
document.addEventListener("click",e=>{
  const t=e.target.closest(".tap");
  if(t){const id=t.dataset.p,c=t.dataset.c,r=+t.dataset.r;
    const lv=CATS.find(x=>x.k===c).lv[r].c;
    const side=lv==="pp"&&(c==="att"||c==="bat")?"home":lv==="mm"?"away":null;
    commit(()=>{stOf(id)[c][r]++;if(side)curSet()[side]++},()=>{updateCard(id);renderScore();if(side)bump(side);t.classList.remove("flash");void t.offsetWidth;t.classList.add("flash")});return}
  const og=e.target.closest("[data-org],[data-orgbtn]");
  if(og){const [k,v]=(og.dataset.org||og.dataset.orgbtn).split(":");S.org[k]=v;save();renderCourt(k);return}
  const fl=e.target.closest("[data-flt]");if(fl){const [k,v]=fl.dataset.flt.split(":");S.flt[k]=v;save();renderCourt(k);return}
  const sf=e.target.closest("[data-sflt]");if(sf){const [k,v]=sf.dataset.sflt.split(":");sumFlt[k]=v;renderSummary();return}
  const cv=e.target.closest("svg[data-court]");if(cv){courtClick(cv,e);return}
  const ty=e.target.closest("[data-type]");
  if(ty){const [k,v]=ty.dataset.type.split(":");S.sel[k]=v;save();renderCourt(k);return}
  const vt=e.target.closest("[data-view]");if(vt){S.view=vt.dataset.view;save();renderMatch();return}
  const sc=e.target.closest("[data-score]");
  if(sc){const side=sc.dataset.score,d=+sc.dataset.d;if(curSet()[side]+d<0)return;commit(()=>{curSet()[side]+=d},()=>{renderScore();bump(side)});return}
  const sb=e.target.closest("[data-sub]");if(sb){openSub(sb.dataset.sub);return}
  const inn=e.target.closest("[data-in]");
  if(inn&&subOut){const out=subOut,id=inn.dataset.in;closeSub();
    commit(()=>{S.court[S.court.indexOf(out)]=id;const s=curSet();if(!s.played.includes(id))s.played.push(id)});return}
  const pk=e.target.closest("[data-pick]");
  if(pk){const id=pk.dataset.pick,i=S.draft.indexOf(id);i<0?S.draft.push(id):S.draft.splice(i,1);save();renderLineup();
    document.querySelector(`[data-pick="${id}"]`)?.focus();return}
  const dl=e.target.closest("[data-del]");
  if(dl){S.players=S.players.filter(p=>p.id!==dl.dataset.del);save();renderRoster();return}
  if(e.target.closest("[data-undo]"))undo();
});
document.addEventListener("input",e=>{
  const tm=e.target.dataset.team;if(tm){S.teams[tm]=e.target.value;save();return}
  const r=e.target.dataset.rid;if(!r)return;const p=byId(r);if(p){p[e.target.dataset.f]=e.target.value;save();rosterCount()}});
document.addEventListener("change",e=>{const r=e.target.dataset.rid;if(!r)return;const p=byId(r);if(p){p[e.target.dataset.f]=e.target.value;save()}});

/* ---------- STATISTICHE ---------- */
let tab="tot",M=null,fromArch=false;const sumFlt={att:"all",dif:"all"};
const liveMatch=()=>({teams:S.teams,sets:S.sets,players:S.players,date:S.date});
const usedIdx=m=>m.sets.map((s,i)=>i).filter(i=>{const s=m.sets[i];return s.closed||s.home||s.away||Object.keys(s.stats).length||KINDS.some(k=>(s.marks[k]||[]).length)});
const nm=(m,k)=>esc((m.teams[k]||"").trim()||(k==="home"?"Noi":"Avversari"));
const fmtDate=t=>t?new Date(t).toLocaleDateString("it-IT",{weekday:"short",day:"numeric",month:"short",year:"numeric"}):"";
const setsWon=m=>{const d=m.sets.filter(s=>s.closed);return[d.filter(s=>s.home>s.away).length,d.filter(s=>s.away>s.home).length]};
function agg(m,pid,idxs){const o=blankStats();idxs.forEach(i=>{const st=m.sets[i].stats[pid];if(st)CATS.forEach(c=>c.lv.forEach((_,j)=>o[c.k][j]+=st[c.k][j]||0))});return o}
function openSummary(m,arch){
  M=(m&&m.sets)?m:liveMatch();fromArch=!!arch;tab="tot";
  $("sumTitle").textContent=fromArch?"Partita archiviata":"Statistiche partita";
  $("backBtn").textContent=fromArch?"Torna all'elenco":"Torna alla partita";
  $("sumNew").hidden=fromArch;$("sumArch").hidden=fromArch;$("sumConfirm").hidden=true;
  renderSummary();$("archive").hidden=true;$("summary").hidden=false;$("summary").scrollTop=0;
}
function renderSummary(){
  const m=M,sets=usedIdx(m),pl=id=>m.players.find(p=>p.id===id);
  const rs=(a,b)=>(RORDER[pl(a)?.role]??9)-(RORDER[pl(b)?.role]??9)||pl(a).name.localeCompare(pl(b).name);
  $("tabs").innerHTML=[["tot","Totale"],...sets.map(i=>[String(i),"Set "+(i+1)])].map(([k,l])=>
    `<button class="tab" role="tab" data-tab="${k}" aria-selected="${tab===k}">${l}</button>`).join("");
  const idxs=tab==="tot"?sets:[+tab];
  if(tab==="tot"){
    const [w,l]=setsWon(m);
    $("finalBox").innerHTML=`<span>${m.date?fmtDate(m.date)+" · ":""}Risultato</span><span class="res">${nm(m,"home")} ${w} – ${l} ${nm(m,"away")}</span><span class="det">${
      sets.length?sets.map(i=>`Set ${i+1}: ${m.sets[i].home}–${m.sets[i].away}${m.sets[i].closed?"":" (in corso)"}`).join(" · "):"Nessun set giocato"}</span>`;
  }else{
    const s=m.sets[+tab];
    const st=!s.closed?"In corso":s.home>s.away?"Vinto":s.away>s.home?"Perso":"Pari";
    $("finalBox").innerHTML=`<span>Set ${+tab+1} · ${st}</span><span class="res">${nm(m,"home")} ${s.home} – ${s.away} ${nm(m,"away")}</span>`;
  }
  const ids=new Set();idxs.forEach(i=>{m.sets[i].played.forEach(x=>ids.add(x));Object.keys(m.sets[i].stats).forEach(x=>ids.add(x))});
  const rows=[...ids].filter(pl).sort(rs);
  if(!rows.length){$("tableBox").innerHTML='<p class="empty">Nessuna giocatrice è scesa in campo.</p>'}
  else{
    const showSets=tab==="tot",team=blankStats();
    const catCells=(c,arr)=>{const tot=arr.reduce((a,b)=>a+b,0);
      if(!tot)return c.lv.map((_,j)=>`<td class="dim${j?"":" gsep"}">–</td>`).join("")+`<td class="dim">–</td>`;
      const pos=arr.reduce((a,v,j)=>a+(c.lv[j].pos?v:0),0);
      return arr.map((v,j)=>`<td class="${j?"":"gsep "}${v?(c.lv[j].pos?"g":"b"):"dim"}">${v}</td>`).join("")+`<td class="pct">${pct(pos,tot)}</td>`};
    const line=o=>{const [p,n]=posNeg(o);
      return CATS.map(c=>catCells(c,o[c.k])).join("")+(p+n?`<td class="gsep"><span class="g">${p}</span> / <span class="b">${n}</span></td><td class="pct">${pct(p,p+n)}</td>`:`<td class="gsep dim">–</td><td class="dim">–</td>`)};
    const body=rows.map(id=>{const p=pl(id),o=agg(m,id,idxs);CATS.forEach(c=>c.lv.forEach((_,j)=>team[c.k][j]+=o[c.k][j]));
      const played=sets.filter(i=>m.sets[i].played.includes(id)||m.sets[i].stats[id]).map(i=>i+1).join(", ");
      return `<tr><td>${badge(p)}<span>${esc(p.name)}</span></td>${showSets?`<td class="dim">${played}</td>`:""}${line(o)}</tr>`}).join("");
    $("tableBox").innerHTML=`<table><thead>
      <tr><th></th>${showSets?"<th></th>":""}${CATS.map(c=>`<th colspan="${c.lv.length+1}" class="gsep">${c.name}</th>`).join("")}<th colspan="2" class="gsep">Totale</th></tr>
      <tr><th>Giocatrice</th>${showSets?"<th>Set</th>":""}${CATS.map(c=>c.lv.map((l,j)=>`<th${j?"":` class="gsep"`}>${l.s}</th>`).join("")+"<th>%</th>").join("")}<th class="gsep">pos / neg</th><th>%</th></tr></thead>
      <tbody>${body}<tr class="tot"><td>Squadra</td>${showSets?"<td></td>":""}${line(team)}</tr></tbody></table>`;
  }
  $("maps").innerHTML=KINDS.map(k=>{
    const marks=idxs.flatMap(i=>m.sets[i].marks[k]||[]),c=counts(k,marks),h=HASORG(k),f=h?sumFlt[k]:"all";
    return `<figure class="map" style="margin:0"><h3>${MAPTITLE[k]}</h3>
      ${h?`<div class="orow"><span class="olab">Mostra</span><div class="obtns">${fltBtns(k,f,"sflt")}</div></div>`:""}
      <svg class="court" viewBox="${VB[k]}" role="img" aria-label="Mappa ${MAPTITLE[k]}">${courtInner(k,marks,-1,{filter:f})}</svg>
      <div class="legend">${TYPES[k].map(t=>`<span>${icon(t)}${t.name}<b>${c[t.k]}</b></span>`).join("")}</div>
      <div class="csum">${sumLine(k,marks,f)}</div>
      ${h?`<div class="otab">${otab(k,marks)}</div>`:""}</figure>`}).join("");
}
$("tabs").addEventListener("click",e=>{const t=e.target.closest("[data-tab]");if(t){tab=t.dataset.tab;renderSummary()}});
$("backBtn").onclick=()=>{$("summary").hidden=true;if(fromArch)openArchive()};
$("sumNew").onclick=()=>{$("sumConfirm").hidden=false};
$("sumNo").onclick=()=>{$("sumConfirm").hidden=true};
$("sumYes").onclick=()=>{$("sumConfirm").hidden=true;$("summary").hidden=true;startNewMatch();$("teamAway").focus()};

/* ---------- ARCHIVIO ---------- */
let delId=null;
function archiveCurrent(){
  const m=liveMatch(),idx=usedIdx(m);if(!idx.length)return;
  const sets=JSON.parse(JSON.stringify(idx.map(i=>m.sets[i])));
  const last=sets[sets.length-1];if(!last.closed&&(last.home||last.away))last.closed=true;
  const entry={id:S.matchId,date:S.date||Date.now(),teams:{...S.teams},players:S.players.map(p=>({id:p.id,name:p.name,role:p.role})),sets};
  ARCH=ARCH.filter(a=>a.id!==entry.id);ARCH.unshift(entry);saveArch();
}
function openArchive(){delId=null;renderArchive();$("summary").hidden=true;$("archive").hidden=false;$("archive").scrollTop=0}
function renderArchive(){
  if(!ARCH.length){$("archList").innerHTML='<p class="empty">Nessuna partita salvata. Una partita finisce qui quando ne inizi una nuova.</p>';return}
  $("archList").innerHTML=ARCH.map(a=>{const [w,l]=setsWon(a),win=w>l;
    return `<article class="arch-item">
      <div class="arch-top"><span class="arch-date">${fmtDate(a.date)}</span><span class="pill ${w===l?"":win?"win":"loss"}">${w===l?"Pari":win?"Vinta":"Persa"}</span></div>
      <div class="arch-res">${nm(a,"home")} ${w} – ${l} ${nm(a,"away")}</div>
      <div class="arch-sets">${a.sets.map(s=>s.home+"–"+s.away).join(" · ")}</div>
      <div class="arch-act">${delId===a.id?
        `<span>Eliminare questa partita?</span><button class="btn danger" data-arch-delyes="${a.id}">Sì, elimina</button><button class="btn" data-arch-delno>No</button>`:
        `<button class="btn navy" data-arch-view="${a.id}">Vedi statistiche</button><button class="btn" data-arch-del="${a.id}">Elimina</button>`}</div>
    </article>`}).join("");
}
$("archive").addEventListener("click",e=>{
  const v=e.target.closest("[data-arch-view]");if(v){openSummary(ARCH.find(a=>a.id===v.dataset.archView),true);return}
  const d=e.target.closest("[data-arch-del]");if(d){delId=d.dataset.archDel;renderArchive();return}
  const y=e.target.closest("[data-arch-delyes]");if(y){ARCH=ARCH.filter(a=>a.id!==y.dataset.archDelyes);saveArch();delId=null;renderArchive();return}
  if(e.target.closest("[data-arch-delno]")){delId=null;renderArchive()}
});
$("archClose").onclick=()=>{$("archive").hidden=true};
document.addEventListener("click",e=>{if(e.target.closest("[data-open-arch]"))openArchive()});
document.addEventListener("keydown",e=>{if(e.key==="Escape"&&!$("archive").hidden)$("archive").hidden=true});

render();
</script>
