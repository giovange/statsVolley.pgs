
<title>Tabellino Pallavolo</title>
<meta name="claude:viewport-fit-sides" content="cover">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@600;700;800&family=Barlow:wght@400;500;600&display=swap">
<style>
/* Layout: tre fasi (rosa → formazione → partita) a colonna singola; segnapunti fisso in partita; statistiche e cambi in pannelli sovrapposti */
:root{
  --bg:#eef1f6; --surface:#ffffff; --fg:#13203a; --muted:#5d6a82; --line:#d6dce8;
  --navy:#16306b; --navy-fg:#ffffff; --yellow:#f5c400; --yellow-fg:#1a1a1a;
  --good:#1d8a4e; --good-bg:#e3f4ea; --bad:#c8352b; --bad-bg:#fbe7e5; --shade:rgba(10,20,40,.45);
  --display:"Barlow Condensed","Arial Narrow",system-ui,sans-serif;
  --body:"Barlow",system-ui,-apple-system,"Segoe UI",sans-serif;
}
@media (prefers-color-scheme: dark){:root:not([data-theme="light"]){
  --bg:#0c1220; --surface:#162033; --fg:#e8edf7; --muted:#9aa6bd; --line:#2a3650;
  --navy:#1f3d85; --navy-fg:#ffffff; --yellow:#f5c400; --yellow-fg:#1a1a1a;
  --good:#4cc283; --good-bg:#14301f; --bad:#ff7a6e; --bad-bg:#3a1a18; --shade:rgba(0,0,0,.6); color-scheme:dark}}
:root[data-theme="dark"]{
  --bg:#0c1220; --surface:#162033; --fg:#e8edf7; --muted:#9aa6bd; --line:#2a3650;
  --navy:#1f3d85; --navy-fg:#ffffff; --yellow:#f5c400; --yellow-fg:#1a1a1a;
  --good:#4cc283; --good-bg:#14301f; --bad:#ff7a6e; --bad-bg:#3a1a18; --shade:rgba(0,0,0,.6); color-scheme:dark}
*{box-sizing:border-box}
[hidden]{display:none!important}
body{background:var(--bg);color:var(--fg);font-family:var(--body);font-size:15px}
body::before{content:"";position:fixed;inset:0 0 auto;height:env(safe-area-inset-top,0px);z-index:10;background:var(--navy)}
button,input,select{font:inherit;color:inherit}
button{cursor:pointer;border:0;background:none;-webkit-tap-highlight-color:transparent}
button:disabled{opacity:.4;cursor:default}
button:focus-visible,input:focus-visible,select:focus-visible{outline:3px solid var(--yellow);outline-offset:2px}
.wrap{max-width:780px;margin:0 auto;padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px))}
h1,h2,h3{font-family:var(--display);text-transform:uppercase;letter-spacing:.04em;margin:0;text-wrap:balance}
.btn{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.06em;font-size:14px;padding:9px 14px;border-radius:8px;background:var(--line);color:var(--fg)}
.btn.primary{background:var(--yellow);color:var(--yellow-fg)}
.btn.navy{background:var(--navy);color:var(--navy-fg)}
.btn.danger{background:var(--bad);color:#fff}
.hint{color:var(--muted);font-size:13px;margin:0;max-width:65ch}
.err{color:var(--bad);font-weight:600;font-size:14px;margin:0}

/* Barra titolo fasi */
.bar{position:sticky;top:env(safe-area-inset-top,0px);z-index:5;background:var(--navy);color:var(--navy-fg)}
.bar .wrap{padding-block:14px;display:flex;align-items:center;gap:10px;flex-wrap:wrap}
.bar h1{font-size:24px;flex:1;min-width:0}
.bar .btn{background:rgba(255,255,255,.14);color:var(--navy-fg)}
.bar .btn.primary{background:var(--yellow);color:var(--yellow-fg)}
.phase .content{padding-block:16px 40px;display:grid;gap:14px}

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
.rgroup{display:grid;gap:8px}
.rgroup h3{font-size:14px;color:var(--muted);letter-spacing:.1em}
.chips{display:grid;grid-template-columns:repeat(auto-fill,minmax(170px,1fr));gap:8px}
.pick{display:flex;align-items:center;gap:8px;padding:8px;border-radius:10px;background:var(--surface);border:2px solid var(--line);text-align:left;font-weight:600;min-width:0}
.pick span.n{min-width:0;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.pick[aria-pressed="true"]{border-color:var(--navy);background:var(--good-bg)}
.pick[aria-pressed="true"]::after{content:"✓";margin-left:auto;color:var(--good);font-weight:800}
.dock{position:sticky;bottom:0;background:var(--bg);border-top:1px solid var(--line);padding-block:12px calc(12px + env(safe-area-inset-bottom,0px));margin-top:4px;display:flex;gap:10px;align-items:center;flex-wrap:wrap}
.dock .count{flex:1;font-family:var(--display);font-weight:700;font-size:18px;font-variant-numeric:tabular-nums;min-width:0}
.teamsbox{display:grid;grid-template-columns:1fr 1fr;gap:10px}
@media (max-width:460px){.teamsbox{grid-template-columns:1fr}}
.teamsbox label{display:grid;gap:4px;font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.08em;font-size:12px;color:var(--muted)}
.teamsbox input{min-width:0;width:100%;padding:10px;border:1px solid var(--line);border-radius:8px;background:var(--surface);font-family:var(--body);font-size:16px;text-transform:none;letter-spacing:0;color:var(--fg)}
.ohead .confirm{flex-basis:100%}
.prev{background:var(--surface);border:1px solid var(--line);border-radius:10px;padding:10px 12px;font-family:var(--display);font-size:17px;font-variant-numeric:tabular-nums}

/* Segnapunti */
.board{position:sticky;top:env(safe-area-inset-top,0px);z-index:5;background:var(--navy);color:var(--navy-fg);box-shadow:0 2px 10px rgba(0,0,0,.25)}
.board .wrap{padding-block:10px 12px;display:grid;gap:8px}
.topline{display:flex;justify-content:space-between;align-items:center;font-family:var(--display);letter-spacing:.08em;text-transform:uppercase;font-size:14px}
.score{display:grid;grid-template-columns:1fr auto 1fr;align-items:center;gap:10px}
.team{display:grid;gap:6px;justify-items:center}
.team-name{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.06em;font-size:14px}
.pts{display:flex;align-items:center;gap:8px}
.pts .num{font-family:var(--display);font-weight:800;font-size:52px;line-height:1;min-width:2ch;text-align:center;font-variant-numeric:tabular-nums}
.pbtn{width:40px;height:40px;border-radius:50%;background:rgba(255,255,255,.14);font-size:22px;font-weight:600;display:grid;place-items:center;color:var(--navy-fg)}
.pbtn.plus{background:var(--yellow);color:var(--yellow-fg)}
.sets{font-family:var(--display);text-align:center;display:grid;gap:2px}
.sets .big{font-size:28px;font-weight:800;font-variant-numeric:tabular-nums}
.sets small{font-size:11px;letter-spacing:.1em;text-transform:uppercase;opacity:.75}
.setlog{font-family:var(--display);font-size:14px;text-align:center;opacity:.85;min-height:1.2em;font-variant-numeric:tabular-nums}
.actions{display:flex;gap:8px;flex-wrap:wrap}
.board .btn{background:rgba(255,255,255,.14);color:var(--navy-fg)}
.board .btn.primary{background:var(--yellow);color:var(--yellow-fg);margin-left:auto}
.board .btn.small{padding:5px 10px;font-size:12px}
.confirm{display:flex;gap:8px;align-items:center;flex-wrap:wrap;font-size:14px}
.board .confirm .btn.danger{background:var(--bad);color:#fff}

/* Schede giocatrici in campo */
.cards{display:grid;gap:12px}
.player{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:12px;display:grid;gap:10px}
.phead{display:flex;align-items:center;gap:10px;min-width:0}
.pname{flex:1;min-width:0;font-family:var(--display);font-weight:700;font-size:21px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.ptot{font-size:12px;color:var(--muted);font-variant-numeric:tabular-nums;white-space:nowrap}
.subbtn{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.05em;font-size:13px;padding:7px 10px;border-radius:8px;border:1px solid var(--line);white-space:nowrap}
.subbtn:hover{border-color:var(--navy)}
.cats{display:grid;grid-template-columns:repeat(4,1fr);gap:10px}
@media (max-width:640px){.cats{grid-template-columns:1fr 1fr}}
.cat{display:grid;gap:4px;min-width:0}
.cname{font-size:13px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.cname em{font-style:normal;font-weight:500;color:var(--muted);font-size:11px;text-transform:uppercase;letter-spacing:.06em}
.pair{display:grid;grid-template-columns:1fr 1fr;gap:6px}
.tap{display:flex;align-items:center;justify-content:space-between;gap:4px;padding:10px 9px;border-radius:8px;font-weight:600;font-variant-numeric:tabular-nums;transition:transform .08s}
.tap:active{transform:scale(.95)}
.tap .n{font-family:var(--display);font-size:22px;font-weight:800;line-height:1}
.tap .s{font-size:17px}
.tap.g{background:var(--good-bg);color:var(--good)}
.tap.b{background:var(--bad-bg);color:var(--bad)}
.flash{animation:fl .35s}
@keyframes fl{0%{box-shadow:0 0 0 0 var(--yellow)}100%{box-shadow:0 0 0 8px transparent}}
@media (prefers-reduced-motion:reduce){.flash{animation:none}.tap{transition:none}}
.benchline{color:var(--muted);font-size:13px}

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
.ohead h2{font-size:28px}
.ohead .btn{margin-left:auto}
.tabs{display:flex;gap:6px;flex-wrap:wrap}
.tab{font-family:var(--display);font-weight:700;text-transform:uppercase;letter-spacing:.06em;padding:8px 14px;border-radius:999px;border:1px solid var(--line);background:var(--surface)}
.tab[aria-selected="true"]{background:var(--navy);color:var(--navy-fg);border-color:var(--navy)}
.final{background:var(--navy);color:var(--navy-fg);border-radius:12px;padding:14px;display:grid;gap:4px;font-family:var(--display)}
.final .res{font-size:32px;font-weight:800;font-variant-numeric:tabular-nums}
.final .det{font-size:15px;opacity:.85;font-variant-numeric:tabular-nums}
.tablebox{overflow-x:auto;background:var(--surface);border:1px solid var(--line);border-radius:12px}
table{border-collapse:collapse;width:100%;font-variant-numeric:tabular-nums;font-size:14px}
th,td{padding:8px;text-align:center;border-bottom:1px solid var(--line);white-space:nowrap}
th{font-family:var(--display);font-size:12px;text-transform:uppercase;letter-spacing:.08em;color:var(--muted);font-weight:700}
thead tr:first-child th{border-bottom:0;padding-bottom:0}
td:first-child,th:first-child{text-align:left;position:sticky;left:0;background:var(--surface)}
td:first-child{display:flex;align-items:center;gap:8px}
td:first-child .role{min-width:26px;height:26px;font-size:14px;border-radius:6px}
.g{color:var(--good);font-weight:600}.b{color:var(--bad);font-weight:600}
td.pct{font-weight:700}
td.dim{color:var(--muted)}
tr.tot td{font-weight:700;border-top:2px solid var(--fg);border-bottom:0}
.gsep{border-left:1px solid var(--line)}
.empty{color:var(--muted);padding:20px;text-align:center}
</style>

<!-- FASE 1: ROSA -->
<section class="phase" id="phRoster" hidden>
  <div class="bar"><div class="wrap"><h1>Rosa della squadra</h1></div></div>
  <div class="wrap content">
    <p class="hint">Inserisci nome e ruolo di ogni giocatrice. Le righe senza nome vengono ignorate.</p>
    <div class="rows" id="rosterRows"></div>
    <div style="display:flex;gap:8px;flex-wrap:wrap"><button class="btn" id="addRow">+ Aggiungi giocatrice</button></div>
    <p class="err" id="rosterErr" hidden></p>
    <div class="dock"><span class="count" id="rosterCount"></span><button class="btn primary" id="rosterNext">Avanti: formazione</button></div>
  </div>
</section>

<!-- FASE 2: FORMAZIONE -->
<section class="phase" id="phLineup" hidden>
  <div class="bar"><div class="wrap"><h1 id="lineupTitle">Formazione set 1</h1>
    <button class="btn undo" data-undo>↶ Annulla</button>
    <button class="btn" id="editRoster">Modifica rosa</button>
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
<section class="phase" id="phMatch" hidden>
  <header class="board"><div class="wrap">
    <div class="topline"><span id="setLabel">Set 1</span><button class="btn small undo" data-undo>↶ Annulla</button></div>
    <div class="score">
      <div class="team"><span class="team-name" id="nameHome">Noi</span>
        <div class="pts"><button class="pbtn" data-score="home" data-d="-1" aria-label="Togli punto a noi">−</button><span class="num" id="homePts">0</span><button class="pbtn plus" data-score="home" data-d="1" aria-label="Punto a noi">+</button></div></div>
      <div class="sets"><span class="big" id="setsScore">0–0</span><small>Set vinti</small></div>
      <div class="team"><span class="team-name" id="nameAway">Avversari</span>
        <div class="pts"><button class="pbtn" data-score="away" data-d="-1" aria-label="Togli punto agli avversari">−</button><span class="num" id="awayPts">0</span><button class="pbtn plus" data-score="away" data-d="1" aria-label="Punto agli avversari">+</button></div></div>
    </div>
    <div class="setlog" id="setLog"></div>
    <div class="actions">
      <button class="btn" id="closeSet">Chiudi set</button>
      <button class="btn" id="newMatch">Nuova partita</button>
      <button class="btn primary" id="matchStats">Fine partita · Statistiche</button>
    </div>
    <div class="confirm" id="newConfirm" hidden>Nuova partita con la stessa rosa? Punteggi e statistiche verranno azzerati. <button class="btn danger" id="newYes">Sì, azzera</button><button class="btn" id="newNo">No</button></div>
  </div></header>
  <div class="wrap content">
    <p class="hint">✓ azione buona, ✗ non buona. "Cambio" fa uscire una giocatrice e propone prima le riserve dello stesso ruolo.</p>
    <div class="cards" id="cards"></div>
    <p class="benchline" id="benchLine"></p>
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
  <div class="ohead"><h2>Statistiche partita</h2>
    <button class="btn navy" id="backBtn">Torna alla partita</button>
    <button class="btn primary" id="sumNew" style="margin-left:0">Nuova partita</button>
    <div class="confirm" id="sumConfirm" hidden>Iniziare una nuova partita con la stessa rosa? Punteggi e statistiche di questa partita verranno azzerati.
      <button class="btn danger" id="sumYes">Sì, nuova partita</button><button class="btn" id="sumNo">No</button></div>
  </div>
  <div class="tabs" id="tabs" role="tablist"></div>
  <div class="final" id="finalBox"></div>
  <div class="tablebox" id="tableBox"></div>
  <p class="hint">Ogni categoria mostra azioni buone / non buone e la percentuale di buone sul totale. Nel set compaiono le giocatrici scese in campo in quel set; nel totale quelle che hanno giocato almeno un set.</p>
</div></section>

<script>
const ROLES=[["Palleggiatrice","P"],["Schiacciatrice","S"],["Centrale","C"],["Opposto","O"],["Libero","L"]];
const RCODE=Object.fromEntries(ROLES), RORDER=Object.fromEntries(ROLES.map((r,i)=>[r[0],i]));
const CATS=[{k:"att",name:"Attacco"},{k:"ric",name:"Ricezione"},{k:"dif",name:"Difesa"},{k:"bat",name:"Battuta",out:true}];
const KEY="tabellino-volley-v2";
const blankStats=()=>Object.fromEntries(CATS.map(c=>[c.k,[0,0]]));
const newSet=()=>({home:0,away:0,closed:false,stats:{},played:[]});
function fresh(){
  return {phase:"roster",players:Array.from({length:13},(_,i)=>({id:"p"+(i+1),name:"",role:""})),nextId:14,
    sets:[newSet()],cur:0,court:[],draft:[],hist:[]};
}
let S;try{S=JSON.parse(localStorage.getItem(KEY))}catch(e){}
if(!S||!S.players)S=fresh();
if(!S.teams)S.teams={home:"",away:""};
const tn=k=>esc((S.teams[k]||"").trim()||(k==="home"?"Noi":"Avversari"));
const save=()=>{try{localStorage.setItem(KEY,JSON.stringify(S))}catch(e){}};
const $=id=>document.getElementById(id);
const esc=s=>String(s).replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]));
const byId=id=>S.players.find(p=>p.id===id);
const roleSort=(a,b)=>(RORDER[byId(a)?.role]??9)-(RORDER[byId(b)?.role]??9);
const badge=p=>`<span class="role ${RCODE[p.role]||""}" title="${esc(p.role)}">${RCODE[p.role]||"?"}</span>`;

function snap(){const {hist,...rest}=S;S.hist.push(JSON.stringify(rest));if(S.hist.length>150)S.hist.shift()}
function commit(fn,after=render){snap();fn();save();after()}
function undo(){const h=S.hist.pop();if(!h)return;const hist=S.hist;S=JSON.parse(h);S.hist=hist;save();closeSub();render()}
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
$("lineupGo").onclick=()=>commit(()=>{
  S.court=[...S.draft].sort(roleSort);
  const s=S.sets[S.cur];s.played=[...new Set([...s.played,...S.court])];
  S.phase="match";S.draft=null;
});
$("editRoster").onclick=()=>commit(()=>{S.phase="roster"});
$("lineupStats").onclick=openSummary;

/* ---------- PARTITA ---------- */
const curSet=()=>S.sets[S.cur];
const stOf=(pid,s=curSet())=>s.stats[pid]||(s.stats[pid]=blankStats());
function renderMatch(){
  renderScore();
  $("cards").innerHTML=S.court.map(id=>{const p=byId(id);if(!p)return"";const st=curSet().stats[id]||blankStats();
    return `<article class="player" id="pl-${id}">
      <div class="phead">${badge(p)}<span class="pname">${esc(p.name)}</span><span class="ptot" id="tot-${id}">${totLabel(st)}</span>
        <button class="subbtn" data-sub="${id}">⇄ Cambio</button></div>
      <div class="cats">${CATS.map(c=>`<div class="cat"><span class="cname">${c.name}${c.out?" <em>fuori campo</em>":""}</span><div class="pair">
        <button class="tap g" data-p="${id}" data-c="${c.k}" data-r="0" aria-label="${c.name} buono, ${esc(p.name)}"><span class="s">✓</span><span class="n">${st[c.k][0]}</span></button>
        <button class="tap b" data-p="${id}" data-c="${c.k}" data-r="1" aria-label="${c.name} non buono, ${esc(p.name)}"><span class="s">✗</span><span class="n">${st[c.k][1]}</span></button>
      </div></div>`).join("")}</div></article>`;}).join("");
  const bench=S.players.filter(p=>!S.court.includes(p.id));
  $("benchLine").textContent=bench.length?"In panchina: "+bench.map(p=>p.name).join(", "):"";
}
const totLabel=st=>{const g=CATS.reduce((a,c)=>a+st[c.k][0],0),b=CATS.reduce((a,c)=>a+st[c.k][1],0);return g+b?`${g} ✓ · ${b} ✗`:""};
function updateCard(id){
  const el=$("pl-"+id),st=stOf(id);
  el.querySelectorAll(".tap").forEach(b=>b.querySelector(".n").textContent=st[b.dataset.c][+b.dataset.r]);
  $("tot-"+id).textContent=totLabel(st);
}
function renderScore(){
  $("nameHome").innerHTML=tn("home");$("nameAway").innerHTML=tn("away");
  const s=curSet();$("homePts").textContent=s.home;$("awayPts").textContent=s.away;
  const done=S.sets.filter(x=>x.closed);
  $("setsScore").textContent=`${done.filter(x=>x.home>x.away).length}–${done.filter(x=>x.away>x.home).length}`;
  $("setLabel").textContent="Set "+(S.cur+1);
  $("setLog").textContent=done.map(x=>x.home+"–"+x.away).join("  ·  ");
  $("closeSet").disabled=!(s.home||s.away);
  renderUndo();
}
$("closeSet").onclick=()=>commit(()=>{curSet().closed=true;S.sets.push(newSet());S.cur++;S.draft=[...S.court];S.phase="lineup"});
$("newMatch").onclick=()=>{$("newConfirm").hidden=false};
$("newNo").onclick=()=>{$("newConfirm").hidden=true};
function startNewMatch(){commit(()=>{S.sets=[newSet()];S.cur=0;S.draft=[...(S.court.length?S.court:S.draft||[])];S.court=[];S.phase="lineup"});scrollTo(0,0)}
$("newYes").onclick=()=>{$("newConfirm").hidden=true;startNewMatch()};
$("sumNew").onclick=()=>{$("sumConfirm").hidden=false};
$("sumNo").onclick=()=>{$("sumConfirm").hidden=true};
$("sumYes").onclick=()=>{$("sumConfirm").hidden=true;$("summary").hidden=true;startNewMatch();$("teamAway").focus()};
$("matchStats").onclick=openSummary;

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
    commit(()=>{stOf(id)[c][r]++},()=>{updateCard(id);renderUndo();t.classList.remove("flash");void t.offsetWidth;t.classList.add("flash")});return}
  const sc=e.target.closest("[data-score]");
  if(sc){const side=sc.dataset.score,d=+sc.dataset.d;if(curSet()[side]+d<0)return;commit(()=>{curSet()[side]+=d},renderScore);return}
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
document.addEventListener("input",e=>{const tm=e.target.dataset.team;if(tm){S.teams[tm]=e.target.value;save();return}
  const r=e.target.dataset.rid;if(!r)return;const p=byId(r);if(p){p[e.target.dataset.f]=e.target.value;save();rosterCount()}});
document.addEventListener("change",e=>{const r=e.target.dataset.rid;if(!r)return;const p=byId(r);if(p){p[e.target.dataset.f]=e.target.value;save()}});

/* ---------- STATISTICHE ---------- */
let tab="tot";
const usedSets=()=>S.sets.map((s,i)=>i).filter(i=>{const s=S.sets[i];return s.closed||s.home||s.away||Object.keys(s.stats).length});
function agg(pid,idxs){const o=blankStats();idxs.forEach(i=>{const st=S.sets[i].stats[pid];if(st)CATS.forEach(c=>{o[c.k][0]+=st[c.k][0];o[c.k][1]+=st[c.k][1]})});return o}
const pct=(g,b)=>g+b?Math.round(g/(g+b)*100)+"%":"–";
function openSummary(){tab="tot";renderSummary();$("summary").hidden=false;$("summary").scrollTop=0}
function renderSummary(){
  const sets=usedSets();
  $("tabs").innerHTML=[["tot","Totale"],...sets.map(i=>[String(i),"Set "+(i+1)])].map(([k,l])=>
    `<button class="tab" role="tab" data-tab="${k}" aria-selected="${tab===k}">${l}</button>`).join("");
  const idxs=tab==="tot"?sets:[+tab];
  // riquadro risultato
  if(tab==="tot"){
    const done=sets.map(i=>S.sets[i]);
    const w=done.filter(s=>s.closed&&s.home>s.away).length,l=done.filter(s=>s.closed&&s.away>s.home).length;
    $("finalBox").innerHTML=`<span>Risultato</span><span class="res">${tn("home")} ${w} – ${l} ${tn("away")}</span><span class="det">${
      sets.length?sets.map(i=>`Set ${i+1}: ${S.sets[i].home}–${S.sets[i].away}${S.sets[i].closed?"":" (in corso)"}`).join(" · "):"Nessun set giocato"}</span>`;
  }else{
    const s=S.sets[+tab];
    const st=!s.closed?"In corso":s.home>s.away?"Vinto":s.away>s.home?"Perso":"Pari";
    $("finalBox").innerHTML=`<span>Set ${+tab+1} · ${st}</span><span class="res">${tn("home")} ${s.home} – ${s.away} ${tn("away")}</span>`;
  }
  // giocatrici da mostrare
  const ids=new Set();idxs.forEach(i=>{S.sets[i].played.forEach(x=>ids.add(x));Object.keys(S.sets[i].stats).forEach(x=>ids.add(x))});
  const rows=[...ids].filter(byId).sort((a,b)=>roleSort(a,b)||byId(a).name.localeCompare(byId(b).name));
  if(!rows.length){$("tableBox").innerHTML='<p class="empty">Nessuna giocatrice è ancora scesa in campo.</p>';return}
  const showSets=tab==="tot";
  const team=blankStats();
  const cell=(g,b)=>g+b?`<td class="gsep"><span class="g">${g}</span> / <span class="b">${b}</span></td><td class="pct">${pct(g,b)}</td>`:`<td class="gsep dim">–</td><td class="dim">–</td>`;
  const line=o=>{let G=0,B=0;const cs=CATS.map(c=>{G+=o[c.k][0];B+=o[c.k][1];return cell(o[c.k][0],o[c.k][1])}).join("");return cs+cell(G,B)};
  const body=rows.map(id=>{const p=byId(id),o=agg(id,idxs);CATS.forEach(c=>{team[c.k][0]+=o[c.k][0];team[c.k][1]+=o[c.k][1]});
    const played=sets.filter(i=>S.sets[i].played.includes(id)||S.sets[i].stats[id]).map(i=>i+1).join(", ");
    return `<tr><td>${badge(p)}<span>${esc(p.name)}</span></td>${showSets?`<td class="dim">${played}</td>`:""}${line(o)}</tr>`}).join("");
  $("tableBox").innerHTML=`<table><thead>
    <tr><th></th>${showSets?"<th></th>":""}${CATS.map(c=>`<th colspan="2" class="gsep">${c.name}</th>`).join("")}<th colspan="2" class="gsep">Totale</th></tr>
    <tr><th>Giocatrice</th>${showSets?"<th>Set</th>":""}${"<th class='gsep'>✓ / ✗</th><th>%</th>".repeat(CATS.length+1)}</tr></thead>
    <tbody>${body}<tr class="tot"><td>Squadra</td>${showSets?"<td></td>":""}${line(team)}</tr></tbody></table>`;
}
$("tabs").addEventListener("click",e=>{const t=e.target.closest("[data-tab]");if(t){tab=t.dataset.tab;renderSummary()}});
$("backBtn").onclick=()=>{$("summary").hidden=true};

render();
</script>

</body></html>
