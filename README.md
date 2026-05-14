# b2b.cal1
<!DOCTYPE html>
<html lang="lv">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>B2B Elektrības kalkulators – CRM mockup</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@3.19.0/dist/tabler-icons.min.css">
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#ffffff;--bg2:#f7f8fa;--bg3:#f0f1f3;
  --text:#111;--text2:#555;--text3:#888;
  --border:#e0e2e6;--border2:#c8ccd4;
  --blue:#185FA5;--blue-bg:#E6F1FB;--blue-text:#0C447C;
  --green:#3B6D11;--green-bg:#EAF3DE;--green-text:#27500A;
  --amber:#854F0B;--amber-bg:#FAEEDA;--amber-text:#633806;
  --red:#A32D2D;--red-bg:#FCEBEB;--red-text:#791F1F;
  --radius:8px;--radius-lg:12px;
  --font:'Inter',system-ui,sans-serif;
}
@media(prefers-color-scheme:dark){
  :root{
    --bg:#1a1b1e;--bg2:#222428;--bg3:#2a2c31;
    --text:#f0f0f0;--text2:#a0a3ab;--text3:#666;
    --border:#333640;--border2:#454a55;
    --blue:#378ADD;--blue-bg:#0c2a4a;--blue-text:#85B7EB;
    --green:#639922;--green-bg:#1a2e0a;--green-text:#97C459;
    --amber:#EF9F27;--amber-bg:#2e1f00;--amber-text:#FAC775;
    --red:#E24B4A;--red-bg:#2e0e0e;--red-text:#F09595;
  }
}
body{font-family:var(--font);font-size:14px;color:var(--text);background:var(--bg3);min-height:100vh}
a{color:var(--blue)}

/* ── NAV ── */
.app-shell{display:flex;min-height:100vh}
.sidebar{width:220px;background:var(--bg);border-right:1px solid var(--border);display:flex;flex-direction:column;flex-shrink:0}
.sidebar-logo{padding:18px 16px 14px;border-bottom:1px solid var(--border);display:flex;align-items:center;gap:10px}
.sidebar-logo span{font-size:15px;font-weight:600;letter-spacing:-.3px}
.sidebar-logo small{font-size:10px;color:var(--text3);display:block;font-weight:400}
.nav-section{padding:10px 8px 4px;font-size:10px;color:var(--text3);text-transform:uppercase;letter-spacing:.6px;font-weight:600}
.nav-item{display:flex;align-items:center;gap:10px;padding:8px 10px;border-radius:var(--radius);cursor:pointer;font-size:13px;color:var(--text2);margin:1px 4px;transition:background .15s}
.nav-item:hover{background:var(--bg2)}
.nav-item.active{background:var(--blue-bg);color:var(--blue-text);font-weight:500}
.nav-item i{font-size:17px;width:20px;text-align:center}

.main{flex:1;display:flex;flex-direction:column;overflow:hidden}
.topbar{background:var(--bg);border-bottom:1px solid var(--border);padding:0 24px;height:52px;display:flex;align-items:center;gap:12px}
.topbar-title{font-size:15px;font-weight:500;flex:1}
.content{flex:1;overflow-y:auto;padding:20px 24px}

/* ── SHARED COMPONENTS ── */
.screen{display:none}
.screen.active{display:block}

.card{background:var(--bg);border:1px solid var(--border);border-radius:var(--radius-lg);padding:16px 18px;margin-bottom:12px}
.card-hdr{font-size:11px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:.5px;margin-bottom:14px;display:flex;align-items:center;gap:7px}
.card-hdr i{font-size:16px}

.btn{display:inline-flex;align-items:center;gap:6px;padding:7px 14px;border:1px solid var(--border2);border-radius:var(--radius);font-size:13px;cursor:pointer;background:var(--bg);color:var(--text);font-family:var(--font)}
.btn:hover{background:var(--bg2)}
.btn-primary{background:var(--blue);color:#fff;border-color:var(--blue)}
.btn-primary:hover{opacity:.9}
.btn-sm{padding:5px 11px;font-size:12px}
.btn-ghost{border-color:transparent}
.btn-ghost:hover{background:var(--bg2);border-color:var(--border)}

.badge{display:inline-flex;align-items:center;gap:4px;padding:3px 9px;border-radius:20px;font-size:11px;font-weight:500}
.badge-blue{background:var(--blue-bg);color:var(--blue-text)}
.badge-green{background:var(--green-bg);color:var(--green-text)}
.badge-amber{background:var(--amber-bg);color:var(--amber-text)}
.badge-red{background:var(--red-bg);color:var(--red-text)}

.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px}
.form-grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:10px}
.form-group{display:flex;flex-direction:column;gap:4px}
.label{font-size:12px;color:var(--text2);display:flex;align-items:center;gap:4px}
.req{color:var(--red);font-size:11px}
.hint{font-size:11px;color:var(--text3);margin-top:2px}
input,select,textarea{width:100%;padding:7px 10px;border:1px solid var(--border2);border-radius:var(--radius);font-size:13px;background:var(--bg);color:var(--text);font-family:var(--font)}
input:focus,select:focus,textarea:focus{outline:none;border-color:var(--blue);box-shadow:0 0 0 3px rgba(24,95,165,.12)}
input.auto,select.auto{background:var(--bg2);color:var(--text2)}
textarea{resize:vertical;min-height:70px}
.divider{border:none;border-top:1px solid var(--border);margin:12px 0}

.alert{border-radius:var(--radius);padding:10px 13px;display:flex;align-items:flex-start;gap:10px;margin-bottom:10px}
.alert i{font-size:17px;margin-top:1px;flex-shrink:0}
.alert-amber{background:var(--amber-bg);border:1px solid #BA7517}
.alert-amber i{color:var(--amber)}
.alert-green{background:var(--green-bg);border:1px solid #3B6D11}
.alert-green i{color:var(--green)}
.alert-red{background:var(--red-bg);border:1px solid var(--red)}
.alert-red i{color:var(--red)}
.alert-blue{background:var(--blue-bg);border:1px solid var(--blue)}
.alert-blue i{color:var(--blue)}
.alert-body strong{display:block;font-size:12px;font-weight:600;margin-bottom:2px}
.alert-body p{font-size:12px;color:var(--text2);margin:0}

.metric-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:8px;margin-bottom:12px}
.metric{background:var(--bg2);border-radius:var(--radius);padding:10px 12px}
.metric-label{font-size:11px;color:var(--text3);margin-bottom:3px}
.metric-val{font-size:18px;font-weight:600}
.metric-unit{font-size:11px;color:var(--text3)}

.final-price-box{background:var(--blue-bg);border-radius:var(--radius);padding:12px 16px;display:flex;align-items:center;justify-content:space-between;margin:10px 0}
.fpl{font-size:12px;font-weight:600;color:var(--blue-text)}
.fpv{font-size:22px;font-weight:700;color:var(--blue-text)}
.green-price-box{background:var(--green-bg);border-radius:var(--radius);padding:9px 14px;display:flex;align-items:center;justify-content:space-between;font-size:12px;margin-bottom:10px}
.gpl{color:var(--green-text)}
.gpv{font-weight:600;color:var(--green)}

.steps-list{display:flex;flex-direction:column;gap:0}
.step-row{display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--border)}
.step-row:last-child{border-bottom:none}
.dot{width:9px;height:9px;border-radius:50%;flex-shrink:0}
.dot-done{background:var(--green)}
.dot-active{background:var(--blue)}
.dot-todo{background:var(--border2)}
.step-name{font-size:13px;font-weight:500}
.step-sub{font-size:11px;color:var(--text3)}

table.data-table{width:100%;border-collapse:collapse;font-size:12px}
.data-table th{text-align:left;padding:7px 10px;background:var(--bg2);color:var(--text3);font-weight:600;border-bottom:1px solid var(--border)}
.data-table td{padding:7px 10px;border-bottom:1px solid var(--border);color:var(--text)}
.data-table tr:last-child td{border-bottom:none}
.data-table tbody tr:hover{background:var(--bg2)}

.two-col{display:grid;grid-template-columns:minmax(0,2fr) minmax(0,1fr);gap:12px}
.sidebar-col{display:flex;flex-direction:column;gap:12px}

/* ── EMAIL PREVIEW ── */
.email-frame{background:#f5f5f5;border:1px solid var(--border);border-radius:var(--radius-lg);overflow:hidden}
.email-chrome{background:var(--bg3);padding:10px 14px;border-bottom:1px solid var(--border);display:flex;align-items:center;gap:8px;font-size:12px;color:var(--text3)}
.email-chrome input{flex:1;padding:4px 8px;height:28px;font-size:12px}
.email-body{background:#fff;padding:32px;font-family:Arial,sans-serif;font-size:13px;color:#222;max-width:700px;margin:0 auto}
.email-logo{font-size:20px;font-weight:700;color:#1F4E79;margin-bottom:24px}
.email-intro{margin-bottom:20px;line-height:1.7;color:#333}
.email-table{width:100%;border-collapse:collapse;margin-bottom:20px;font-size:12px}
.email-table th{background:#1F4E79;color:#fff;padding:8px 12px;text-align:left}
.email-table td{padding:7px 12px;border-bottom:1px solid #e0e0e0}
.email-table tr:nth-child(even) td{background:#f9f9f9}
.email-footer{font-size:11px;color:#888;border-top:1px solid #e0e0e0;padding-top:14px;line-height:1.7}

/* ── CONTRACT ── */
.contract-status-bar{display:flex;align-items:center;gap:0;margin-bottom:16px;overflow:hidden;border-radius:var(--radius);border:1px solid var(--border)}
.cs-step{flex:1;padding:9px 12px;font-size:11px;font-weight:600;text-align:center;background:var(--bg2);color:var(--text3);border-right:1px solid var(--border)}
.cs-step:last-child{border-right:none}
.cs-step.done{background:var(--green-bg);color:var(--green-text)}
.cs-step.active{background:var(--blue-bg);color:var(--blue-text)}

/* ── MOVEIN ── */
.movein-banner{background:var(--amber-bg);border:1px solid #BA7517;border-radius:var(--radius-lg);padding:14px 18px;margin-bottom:14px;display:flex;align-items:flex-start;gap:12px}
.movein-banner i{font-size:22px;color:var(--amber);flex-shrink:0}

.tab-bar{display:flex;gap:2px;background:var(--bg2);border-radius:var(--radius);padding:3px;margin-bottom:16px;border:1px solid var(--border)}
.tab{padding:6px 16px;border-radius:6px;font-size:12px;cursor:pointer;color:var(--text3);font-weight:500}
.tab.active{background:var(--bg);color:var(--text);border:1px solid var(--border)}

@media(max-width:900px){
  .sidebar{width:56px}
  .sidebar-logo span,.sidebar-logo small,.nav-item span,.nav-section{display:none}
  .nav-item{justify-content:center}
  .two-col{grid-template-columns:1fr}
}
</style>
</head>
<body>

<div class="app-shell">

<!-- SIDEBAR -->
<nav class="sidebar">
  <div class="sidebar-logo">
    <i class="ti ti-bolt" style="font-size:22px;color:#185FA5"></i>
    <div><span>Virši CRM</span><small>B2B Elektroenerģija</small></div>
  </div>
  <div style="padding:8px 4px;flex:1">
    <div class="nav-section">Piedāvājumi</div>
    <div class="nav-item active" onclick="showScreen('offer')"><i class="ti ti-file-text"></i><span>Jauns piedāvājums</span></div>
    <div class="nav-item" onclick="showScreen('movein')"><i class="ti ti-home-move"></i><span>MoveIn scenārijs</span></div>
    <div class="nav-section">Komunikācija</div>
    <div class="nav-item" onclick="showScreen('email')"><i class="ti ti-mail"></i><span>E-pasta priekšskats</span></div>
    <div class="nav-section">Līgumi</div>
    <div class="nav-item" onclick="showScreen('contract')"><i class="ti ti-writing"></i><span>Līguma izveide</span></div>
    <div class="nav-section">Atsauce</div>
    <div class="nav-item" onclick="showScreen('fields')"><i class="ti ti-list-details"></i><span>Lauku apraksts</span></div>
  </div>
  <div style="padding:12px 8px;border-top:1px solid var(--border)">
    <div class="nav-item" style="font-size:11px;color:var(--text3)">
      <i class="ti ti-info-circle"></i><span>CRM-91 · CRM-716 · DK-324</span>
    </div>
  </div>
</nav>

<!-- MAIN -->
<div class="main">

<!-- TOPBAR (dynamic) -->
<div class="topbar" id="topbar">
  <i class="ti ti-file-text" id="topbar-icon" style="font-size:18px;color:var(--blue)"></i>
  <span class="topbar-title" id="topbar-title">Jauns piedāvājums — FIX/SPOT</span>
  <span class="badge badge-blue" id="topbar-badge">Procesā</span>
  <div style="display:flex;gap:6px">
    <button class="btn btn-sm" onclick="alert('Saglabāts')"><i class="ti ti-device-floppy"></i> Saglabāt</button>
    <button class="btn btn-sm btn-primary" id="topbar-primary-btn" onclick="showScreen('email')"><i class="ti ti-send"></i> Nosūtīt klientam</button>
  </div>
</div>

<div class="content">

<!-- ════════════════════════════════════════════
     SCREEN 1 – OFFER FORM
═════════════════════════════════════════════ -->
<div class="screen active" id="screen-offer">

<div class="two-col">
<div><!-- LEFT COLUMN -->

<div class="card">
  <div class="card-hdr"><i class="ti ti-user"></i>Klienta informācija</div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Klients <span class="req">*</span></span>
      <input value="AUGĻU NAMS KS" class="auto" readonly>
    </div>
    <div class="form-group">
      <span class="label">Reģ. nr.</span>
      <input value="40103499109" class="auto" readonly>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Klienta EIC</span>
      <input value="43X-STJ01298477L" class="auto" readonly>
      <span class="hint">Automātiski no konta</span>
    </div>
    <div class="form-group">
      <span class="label">Apmaksas dienas <span class="req">*</span></span>
      <select id="paydays" onchange="calcFinal()">
        <option>10</option><option>15</option><option selected>20</option>
        <option>30</option><option>45</option><option>60</option>
      </select>
    </div>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-calendar"></i>Piedāvājuma parametri</div>
  <div class="tab-bar">
    <div class="tab active" onclick="setProduct('FIX6',this)">FIX 6m</div>
    <div class="tab" onclick="setProduct('FIX12',this)">FIX 12m</div>
    <div class="tab" onclick="setProduct('FIX24',this)">FIX 24m</div>
    <div class="tab" onclick="setProduct('SPOT',this)">SPOT</div>
    <div class="tab" onclick="setProduct('MAN',this)">Manuāli</div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Sākuma datums <span class="req">*</span></span>
      <input type="date" id="dateFrom" value="2026-06-01" onchange="calcEndDate()">
      <span class="hint">Vienmēr mēneša 1. datums</span>
    </div>
    <div class="form-group">
      <span class="label">Beigu datums</span>
      <input id="dateTo" value="2026-11-30" class="auto" readonly>
      <span class="hint" id="date-hint">CRM aprēķina automātiski (+6m)</span>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Piedāvājums derīgs līdz</span>
      <input value="14.05.2026 17:00" class="auto" readonly>
      <span class="hint">Šodien 17:00 — max +5 d.d. ar Revise</span>
    </div>
    <div class="form-group">
      <span class="label">Quote ID</span>
      <input value="QUO-01204-Z8H1P0" class="auto" readonly>
    </div>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-database"></i>DatuKuba dati <span id="dk-badge" class="badge badge-green" style="margin-left:4px">1002 – Veiksmīgi</span></div>
  <div class="alert alert-green" id="dk-msg">
    <i class="ti ti-circle-check"></i>
    <div class="alert-body"><strong>Aprēķini pabeigti</strong><p>DK atbildēja uzreiz. Lauki aizpildīti automātiski.</p></div>
  </div>
  <div class="form-grid-3">
    <div class="form-group">
      <span class="label">Kopējais apjoms (gads)</span>
      <input id="volume" value="120" class="auto" readonly>
      <span class="hint">MWh — no DK (Claviz)</span>
    </div>
    <div class="form-group">
      <span class="label">Bāzes cena</span>
      <input id="basePrice" value="108.00" class="auto" readonly>
      <span class="hint">EUR/MWh — no DK</span>
    </div>
    <div class="form-group">
      <span class="label">Dienu piemaksa</span>
      <input id="dayFee" value="1.00" class="auto" readonly>
      <span class="hint">EUR/MWh — CRM aprēķina</span>
    </div>
  </div>
  <div style="display:flex;gap:6px;flex-wrap:wrap">
    <button class="btn btn-sm" onclick="simDK('pending')"><i class="ti ti-clock"></i>Simulēt 1001</button>
    <button class="btn btn-sm" onclick="simDK('success')"><i class="ti ti-check"></i>Simulēt 1002</button>
    <button class="btn btn-sm" onclick="simDK('error5')"><i class="ti ti-alert-triangle"></i>Simulēt 1005</button>
    <button class="btn btn-sm" onclick="simDK('error7')"><i class="ti ti-alert-triangle"></i>Simulēt 1007</button>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-pencil"></i>Menedžera ievade</div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Uzcenojums <span class="req">*</span> <span id="markup-note" style="font-size:11px;color:var(--red)"></span></span>
      <input type="number" id="markup" value="12.00" min="0" step="0.01" oninput="checkMarkup();calcFinal()">
      <span class="hint">EUR/MWh — apjoms <span id="vol-disp">120</span> MWh, min: <span id="min-mkp">5.00</span></span>
      <div id="markup-warn" style="display:none;margin-top:4px" class="alert alert-red">
        <i class="ti ti-alert-triangle"></i>
        <div class="alert-body"><strong>Uzcenojums zem minimuma!</strong><p>Apjoms ≥ 50 MWh — uzcenojums nedrīkst būt zemāks par minimālo robežu (5.00 EUR/MWh).</p></div>
      </div>
    </div>
    <div class="form-group">
      <span class="label">Apkalpošanas maksa <span class="req">*</span></span>
      <input type="number" id="serviceFee" value="5.00" min="0" step="0.01" oninput="calcFinal()">
      <span class="hint">EUR/objekts/mēnesī</span>
    </div>
  </div>
  <div style="display:flex;align-items:center;gap:8px;margin-bottom:10px">
    <input type="checkbox" id="greenCheck" onchange="toggleGreen()" style="width:16px;height:16px">
    <label for="greenCheck" style="font-size:13px;display:flex;align-items:center;gap:5px"><i class="ti ti-leaf" style="color:var(--green)"></i>Zaļās enerģijas apliecinājums</label>
  </div>
  <div id="green-row" style="display:none;margin-bottom:10px">
    <div class="form-group">
      <span class="label">Zaļās enerģijas cena</span>
      <input type="number" id="greenPrice" value="2.50" step="0.01" oninput="calcFinal()">
      <span class="hint">EUR/MWh — uzrādīts atsevišķi, netiek summēts gala cenā (CRM-716)</span>
    </div>
  </div>
  <hr class="divider">
  <div class="metric-grid">
    <div class="metric"><div class="metric-label">Bāzes cena</div><div class="metric-val" id="d-base">108.00</div><div class="metric-unit">EUR/MWh</div></div>
    <div class="metric"><div class="metric-label">Uzcenojums</div><div class="metric-val" id="d-mkp">12.00</div><div class="metric-unit">EUR/MWh</div></div>
    <div class="metric"><div class="metric-label">Dienu piemaksa</div><div class="metric-val" id="d-day">1.00</div><div class="metric-unit">EUR/MWh</div></div>
    <div class="metric"><div class="metric-label">Apkalp. maksa</div><div class="metric-val" id="d-svc">5.00</div><div class="metric-unit">EUR/obj/mēn</div></div>
  </div>
  <div class="final-price-box">
    <span class="fpl"><i class="ti ti-calculator"></i> Gala cena (bez zaļās)</span>
    <span class="fpv" id="final-price">121.00 EUR/MWh</span>
  </div>
  <div class="green-price-box" id="green-disp" style="display:none">
    <span class="gpl"><i class="ti ti-leaf"></i> Zaļās enerģijas uzcenojums (atsevišķi — netiek summēts)</span>
    <span class="gpv" id="green-val">+ 2.50 EUR/MWh</span>
  </div>
</div>

</div><!-- /left -->

<div class="sidebar-col"><!-- RIGHT COLUMN -->

<div class="card">
  <div class="card-hdr"><i class="ti ti-list-check"></i>Procesa statuss</div>
  <div class="steps-list">
    <div class="step-row"><div class="dot dot-done"></div><div><div class="step-name">Klients atlasīts</div><div class="step-sub">AUGĻU NAMS KS</div></div></div>
    <div class="step-row"><div class="dot dot-done"></div><div><div class="step-name">EIC objekti pievienoti</div><div class="step-sub">1 objekts</div></div></div>
    <div class="step-row"><div class="dot dot-done"></div><div><div class="step-name">DK aprēķini saņemti</div><div class="step-sub">Statuss 1002</div></div></div>
    <div class="step-row"><div class="dot dot-active"></div><div><div class="step-name">Menedžeris aizpilda</div><div class="step-sub">Uzcenojums, maksa</div></div></div>
    <div class="step-row"><div class="dot dot-todo"></div><div><div class="step-name">Nosūtīt klientam</div><div class="step-sub">E-pasts ar PDF</div></div></div>
    <div class="step-row"><div class="dot dot-todo"></div><div><div class="step-name">Izveidot līgumu</div><div class="step-sub">Pēc akceptēšanas</div></div></div>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-building"></i>EIC objekti</div>
  <table class="data-table">
    <tr><th>EIC kods</th><th>Objekts</th></tr>
    <tr><td style="font-family:monospace;font-size:11px">43Z-STO01308407B</td><td>NOLIKTAVA</td></tr>
  </table>
  <button class="btn btn-sm" style="margin-top:8px;width:100%"><i class="ti ti-plus"></i>Pievienot objektu</button>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-info-circle"></i>Formula (CRM-716)</div>
  <div style="font-size:11px;color:var(--text2);line-height:1.8">
    <code style="display:block;background:var(--bg2);padding:8px 10px;border-radius:var(--radius);font-size:11px;line-height:1.7;color:var(--text)">Gala cena =
  Bāze
+ Markup
+ Dienu piemaksa
+ Apkalp. maksa
≠ Zaļā (atsevišķa rinda!)</code>
    <div style="margin-top:8px">
      <div style="margin-bottom:3px"><span class="badge badge-red" style="font-size:10px">≥50 MWh</span> Markup ≥ min robeža</div>
      <div><span class="badge" style="background:var(--bg3);color:var(--text3);font-size:10px">&lt;50 MWh</span> Markup = 0.00</div>
    </div>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-link"></i>Jira</div>
  <div style="font-size:12px;display:flex;flex-direction:column;gap:5px">
    <a href="https://virsi.atlassian.net/browse/CRM-91" target="_blank"><i class="ti ti-external-link" style="font-size:13px"></i> CRM-91 – B2B kalkulators</a>
    <a href="https://virsi.atlassian.net/browse/CRM-716" target="_blank"><i class="ti ti-external-link" style="font-size:13px"></i> CRM-716 – Piedāvājumu izmaiņas</a>
    <a href="https://virsi.atlassian.net/browse/DK-324" target="_blank"><i class="ti ti-external-link" style="font-size:13px"></i> DK-324 – DK aprēķini</a>
  </div>
</div>

</div><!-- /right -->
</div><!-- /two-col -->
</div><!-- /screen-offer -->


<!-- ════════════════════════════════════════════
     SCREEN 2 – MOVEIN
═════════════════════════════════════════════ -->
<div class="screen" id="screen-movein">
<div class="movein-banner">
  <i class="ti ti-home-move"></i>
  <div>
    <div style="font-weight:600;font-size:14px;color:var(--amber-text);margin-bottom:3px">MoveIn scenārijs — ierobežots process</div>
    <div style="font-size:13px;color:var(--amber-text)">Klientam nav vēstures datu par šo objektu (tikko ievācies). No Sadales tīkla objektu dati netika atgriezti. DatuKubs netiek izsaukts — pieejams tikai SPOT standarta piedāvājums.</div>
  </div>
</div>

<div class="two-col">
<div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-user"></i>Klienta informācija</div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Klients <span class="req">*</span></span>
      <input value="SIA JAUNS KLIENTS" class="auto" readonly>
    </div>
    <div class="form-group">
      <span class="label">Klienta EIC</span>
      <input value="43X-STJ09988776K" class="auto" readonly>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Apmaksas dienas <span class="req">*</span></span>
      <select>
        <option>10</option><option selected>20</option><option>30</option>
      </select>
    </div>
    <div class="form-group">
      <span class="label">Sākuma datums</span>
      <input type="date" value="2026-07-01">
      <span class="hint">Mēneša 1. datums</span>
    </div>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-bolt"></i>Standarta SPOT piedāvājums</div>
  <div class="alert alert-blue" style="margin-bottom:14px">
    <i class="ti ti-info-circle"></i>
    <div class="alert-body"><strong>Iepriekš definēti parametri</strong><p>MoveIn gadījumā tiek izmantots fiksēts standarta piedāvājums. Parametrus var mainīt tikai enerģētikas daļa CRM konfigurācijā.</p></div>
  </div>
  <div class="form-grid-3">
    <div class="form-group">
      <span class="label">Produkts</span>
      <input value="SPOT" class="auto" readonly>
    </div>
    <div class="form-group">
      <span class="label">Biržas uzcenojums</span>
      <input value="3.50" class="auto" readonly>
      <span class="hint">EUR/MWh — standarta</span>
    </div>
    <div class="form-group">
      <span class="label">Apkalpošanas maksa</span>
      <input value="5.00" class="auto" readonly>
      <span class="hint">EUR/obj/mēn</span>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Periods</span>
      <input value="Beztermiņa (SPOT)" class="auto" readonly>
    </div>
    <div class="form-group">
      <span class="label">Beigu datums</span>
      <input value="—" class="auto" readonly>
      <span class="hint">SPOT — netiek noteikts</span>
    </div>
  </div>
  <div class="final-price-box">
    <span class="fpl"><i class="ti ti-bolt"></i> Biržas cena + uzcenojums</span>
    <span class="fpv">Biržas cena + 3.50 EUR/MWh</span>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-send"></i>Darbības</div>
  <div style="display:flex;gap:8px;flex-wrap:wrap">
    <button class="btn btn-primary" onclick="showScreen('email')"><i class="ti ti-mail"></i>Nosūtīt piedāvājumu klientam</button>
    <button class="btn" onclick="showScreen('contract')"><i class="ti ti-writing"></i>Izveidot līgumu</button>
  </div>
</div>

</div>

<div class="sidebar-col">
<div class="card">
  <div class="card-hdr"><i class="ti ti-list-check"></i>MoveIn procesa soļi</div>
  <div class="steps-list">
    <div class="step-row"><div class="dot dot-done"></div><div><div class="step-name">Klients atlasīts</div></div></div>
    <div class="step-row"><div class="dot dot-done"></div><div><div class="step-name">ST — objekti nav atrasti</div><div class="step-sub">→ aktivizēts MoveIn</div></div></div>
    <div class="step-row"><div class="dot dot-done"></div><div><div class="step-name">DK netiek izsaukts</div><div class="step-sub">Nav vēstures datu</div></div></div>
    <div class="step-row"><div class="dot dot-active"></div><div><div class="step-name">Standarta SPOT piedāvājums</div><div class="step-sub">Automātiski aizpildīts</div></div></div>
    <div class="step-row"><div class="dot dot-todo"></div><div><div class="step-name">Nosūtīt klientam</div></div></div>
    <div class="step-row"><div class="dot dot-todo"></div><div><div class="step-name">Parakstīt līgumu</div></div></div>
  </div>
</div>
<div class="card">
  <div class="card-hdr"><i class="ti ti-building"></i>Objekts</div>
  <div style="font-size:13px;color:var(--text2);padding:6px 0">
    <div style="margin-bottom:5px"><span style="color:var(--text3);font-size:12px">Adrese:</span></div>
    <div style="font-weight:500">Rīga, Brīvības iela 55</div>
    <div style="font-size:12px;color:var(--text3);margin-top:4px">Nav EIC — klients tikko ievācies</div>
  </div>
</div>
</div>
</div>
</div><!-- /screen-movein -->


<!-- ════════════════════════════════════════════
     SCREEN 3 – EMAIL PREVIEW
═════════════════════════════════════════════ -->
<div class="screen" id="screen-email">

<div class="card" style="margin-bottom:12px">
  <div class="card-hdr"><i class="ti ti-mail"></i>E-pasta iestatījumi</div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">No</span>
      <input value="haralds.lukins@virsi.lv" readonly class="auto">
    </div>
    <div class="form-group">
      <span class="label">Kam</span>
      <input id="email-to" value="info@auglunamks.lv">
    </div>
  </div>
  <div class="form-group" style="margin-bottom:10px">
    <span class="label">Temats</span>
    <input id="email-subject" value="Virši — aktuālais elektroenerģijas cenas piedāvājums">
  </div>
  <div class="form-group">
    <span class="label">Personalizēts ievads (CRM-716)</span>
    <textarea id="email-intro-text" oninput="updateEmailPreview()">Sveiki,

pēc mūsu sarunas sūtu aktuālo elektroenerģijas cenas piedāvājumu. Piedāvājums ir spēkā līdz šodienas plkst. 17:00.</textarea>
  </div>
  <div style="display:flex;gap:8px;margin-top:10px">
    <button class="btn btn-primary" onclick="alert('E-pasts nosūtīts!')"><i class="ti ti-send"></i>Nosūtīt</button>
    <button class="btn" onclick="alert('PDF pievienots')"><i class="ti ti-paperclip"></i>PDF pielikums</button>
  </div>
</div>

<div style="font-size:11px;color:var(--text3);margin-bottom:8px;text-align:center">Priekšskatījums</div>
<div class="email-frame">
  <div class="email-chrome">
    <i class="ti ti-mail" style="font-size:15px"></i>
    <span>Priekšskatījums</span>
    <input id="email-subj-disp" value="Virši — aktuālais elektroenerģijas cenas piedāvājums" readonly class="auto">
  </div>
  <div class="email-body">
    <div class="email-logo"><i class="ti ti-bolt" style="color:#1F4E79;font-size:18px"></i> VIRŠI</div>

    <table width="100%" cellpadding="0" cellspacing="0" style="margin-bottom:20px">
      <tr>
        <td style="font-size:12px;color:#666">Klients: <strong>AUGĻU NAMS KS</strong></td>
        <td style="font-size:12px;color:#666;text-align:right">Piedāvājums Nr.: <strong>QUO-01204-Z8H1P0</strong></td>
      </tr>
      <tr>
        <td style="font-size:12px;color:#666">Reģ. Nr.: LV40103499109</td>
        <td style="font-size:12px;color:#666;text-align:right">Datums: 14.05.2026</td>
      </tr>
      <tr>
        <td style="font-size:12px;color:#666">Jur. adrese: Rīga, Brīvības 55</td>
        <td style="font-size:12px;color:#666;text-align:right">Derīgs līdz: <strong style="color:#c0392b">14.05.2026 17:00</strong></td>
      </tr>
    </table>

    <div class="email-intro" id="email-body-preview">Sveiki,

pēc mūsu sarunas sūtu aktuālo elektroenerģijas cenas piedāvājumu. Piedāvājums ir spēkā līdz šodienas plkst. 17:00.</div>

    <div style="font-weight:700;font-size:14px;color:#1F4E79;margin:20px 0 10px;text-transform:uppercase;letter-spacing:.5px">Elektroenerģijas tirdzniecības cenu piedāvājums</div>

    <table class="email-table">
      <tr>
        <th>Tirdzniecības periods</th>
        <th>Elektroenerģijas cena (EUR/MWh)</th>
        <th>Objekta apkalpošanas maksa (EUR/mēn./objekts)</th>
      </tr>
      <tr><td>01.06.2026 – undefined</td><td>0.00</td><td>undefined</td></tr>
      <tr><td>01.06.2026 – 30.11.2026</td><td>121.00</td><td>5.00</td></tr>
      <tr><td>01.06.2026 – 31.05.2027</td><td>116.00</td><td>5.00</td></tr>
      <tr><td>01.06.2026 – 31.05.2028</td><td>116.00</td><td>5.00</td></tr>
    </table>

    <table class="email-table">
      <tr>
        <th>Elektroenerģija</th>
        <th>Elektroenerģijas cena</th>
        <th>Tirdzniecības uzcenojums</th>
        <th>Objekta apkalp. maksa</th>
      </tr>
      <tr>
        <td>01.06.2026 – beztermiņa</td>
        <td>Biržas cena*</td>
        <td>2,000</td>
        <td>undefined</td>
      </tr>
    </table>

    <div style="background:#fff8e1;border-left:3px solid #f39c12;padding:10px 14px;font-size:11px;color:#555;margin:14px 0;border-radius:0 4px 4px 0">
      * Biržas cena — Nord Pool elektroenerģijas biržas SPOT cena attiecīgajam piegādes mēnesim (MWh)
    </div>

    <div style="background:#e8f5e9;border:1px solid #a5d6a7;border-radius:4px;padding:10px 14px;font-size:12px;color:#2e7d32;margin:14px 0">
      <strong><i class="ti ti-leaf" style="font-size:14px;vertical-align:-2px"></i> Zaļās enerģijas apliecinājums</strong><br>
      Zaļās izcelsmes uzcenojums: <strong>+ 2.50 EUR/MWh</strong> (uzrādīts atsevišķi — netiek summēts gala cenā)
    </div>

    <div class="email-footer">
      <strong>Jautājumu gadījumā sazinieties:</strong><br>
      Haralds Lūkins | haralds.lukins@virsi.lv | +371 XXXXXXXX<br>
      AS "Latvijas nafta" | Reģ. nr. XXXXXXXXX<br><br>
      Šis piedāvājums sagatavots elektroniski un ir derīgs bez paraksta.
    </div>
  </div>
</div>
</div><!-- /screen-email -->


<!-- ════════════════════════════════════════════
     SCREEN 4 – CONTRACT
═════════════════════════════════════════════ -->
<div class="screen" id="screen-contract">

<div class="contract-status-bar">
  <div class="cs-step done"><i class="ti ti-check" style="font-size:13px"></i> Piedāvājums</div>
  <div class="cs-step done"><i class="ti ti-check" style="font-size:13px"></i> Klients akceptē</div>
  <div class="cs-step active"><i class="ti ti-writing" style="font-size:13px"></i> Līguma izveide</div>
  <div class="cs-step">Ģenerē dokumentu</div>
  <div class="cs-step">Parakstīšana</div>
  <div class="cs-step">DK — numurs</div>
</div>

<div class="two-col">
<div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-file-text"></i>Vispārīgā informācija</div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Konts (klients)</span>
      <input value="AUGĻU NAMS KS" class="auto" readonly>
    </div>
    <div class="form-group">
      <span class="label">Līguma nr.</span>
      <input value="ELE/2026-7756" class="auto" readonly>
      <span class="hint">Automātiski ģenerēts</span>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Līguma veids</span>
      <input value="Elektrība" class="auto" readonly>
    </div>
    <div class="form-group">
      <span class="label">Līguma statuss</span>
      <select>
        <option selected>Līgums sagatavots</option>
        <option>Aktīvs</option>
        <option>Pārtraukts</option>
      </select>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Līguma parakstīšanas datums</span>
      <input type="date" value="">
    </div>
    <div class="form-group">
      <span class="label">Līguma īpašnieks</span>
      <input value="Haralds Lūkins" class="auto" readonly>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Rēķina e-pasts</span>
      <input value="info@auglunamks.lv">
    </div>
    <div class="form-group">
      <span class="label">Reģ. nr.</span>
      <input value="40103499109" class="auto" readonly>
    </div>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-bolt"></i>Elektrības līguma detaļas</div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Produkts <span class="req">*</span></span>
      <input value="Fiksētā elektrība" class="auto" readonly>
    </div>
    <div class="form-group">
      <span class="label">Pārdošanas periods no <span class="req">*</span></span>
      <input type="date" value="2026-06-01">
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Pārdošanas periods līdz <span class="req">*</span></span>
      <input type="date" value="2026-11-30">
    </div>
    <div class="form-group">
      <span class="label">Ikmēneša maksa bez PVN <span class="req">*</span></span>
      <input value="5.00">
      <span class="hint">EUR</span>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Cena bez uzcenojuma EUR/MWh <span class="req">*</span></span>
      <input value="110.00" class="auto" readonly>
    </div>
    <div class="form-group">
      <span class="label">Apmaksas termiņš (dienas)</span>
      <select>
        <option>20</option><option>30</option><option>60</option>
      </select>
    </div>
  </div>
  <hr class="divider">
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:12px">
    <div style="display:flex;align-items:center;gap:8px">
      <input type="checkbox" id="c-power" checked style="width:15px;height:15px">
      <label for="c-power" style="font-size:13px">Piemērot jaudas bilanci</label>
    </div>
    <div style="display:flex;align-items:center;gap:8px">
      <input type="checkbox" id="c-green" checked style="width:15px;height:15px">
      <label for="c-green" style="font-size:13px;color:var(--green)"><i class="ti ti-leaf"></i> Zaļā elektrība</label>
    </div>
    <div style="display:flex;align-items:center;gap:8px">
      <input type="checkbox" id="c-dso" style="width:15px;height:15px">
      <label for="c-dso" style="font-size:13px">Sadales pakalpojumi (DSO)</label>
    </div>
  </div>
  <div class="form-grid">
    <div class="form-group">
      <span class="label">Zaļās elektr. cena <span class="req">*</span></span>
      <input value="">
      <span class="hint">EUR/MWh</span>
    </div>
    <div class="form-group">
      <span class="label">Sistēmas operators (DSO)</span>
      <input value='AS "Sadales tīkls"' class="auto" readonly>
    </div>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-building"></i>Objektu EIC saraksts</div>
  <table class="data-table" style="margin-bottom:10px">
    <tr><th>Objekta nosaukums</th><th>EIC kods</th><th>Adrese</th></tr>
    <tr><td>NOLIKTAVA</td><td style="font-family:monospace;font-size:11px">43Z-STO01308407B</td><td>Tukuma nov., Pūre</td></tr>
  </table>
  <button class="btn btn-sm"><i class="ti ti-plus"></i>Pievienot EIC objektu</button>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-send"></i>Līguma ģenerēšana</div>
  <div class="alert alert-blue" style="margin-bottom:12px">
    <i class="ti ti-info-circle"></i>
    <div class="alert-body"><strong>Pēc saglabāšanas</strong><p>CRM nosūtīs DK izvēlētā piedāvājuma pazīmi. Pārējo piedāvājumu aprēķinu dati tiks dzēsti. Pēc parakstīšanas DK saņems līguma numuru ELE/2026-7756.</p></div>
  </div>
  <div style="display:flex;gap:8px;flex-wrap:wrap">
    <button class="btn btn-primary" onclick="alert('Līgums saglabāts! Sūta DK pazīmi...')"><i class="ti ti-device-floppy"></i>Saglabāt līgumu</button>
    <button class="btn" onclick="alert('Ģenerē PDF dokumentu...')"><i class="ti ti-file-export"></i>Ģenerēt līgumu PDF</button>
    <button class="btn" onclick="alert('Līgums nosūtīts parakstīšanai!')"><i class="ti ti-writing"></i>Nosūtīt parakstīšanai</button>
  </div>
</div>

</div><!-- /left -->

<div class="sidebar-col">
<div class="card">
  <div class="card-hdr"><i class="ti ti-list-check"></i>Līguma statuss</div>
  <div class="steps-list">
    <div class="step-row"><div class="dot dot-done"></div><div><div class="step-name">Piedāvājums akceptēts</div><div class="step-sub">QUO-01204-Z8H1P0</div></div></div>
    <div class="step-row"><div class="dot dot-active"></div><div><div class="step-name">Līgums tiek veidots</div><div class="step-sub">ELE/2026-7756</div></div></div>
    <div class="step-row"><div class="dot dot-todo"></div><div><div class="step-name">DK — piedāvājuma pazīme</div></div></div>
    <div class="step-row"><div class="dot dot-todo"></div><div><div class="step-name">Dokuments ģenerēts</div></div></div>
    <div class="step-row"><div class="dot dot-todo"></div><div><div class="step-name">Parakstīts</div></div></div>
    <div class="step-row"><div class="dot dot-todo"></div><div><div class="step-name">DK — līguma numurs</div></div></div>
  </div>
</div>
<div class="card">
  <div class="card-hdr"><i class="ti ti-receipt"></i>Avots — piedāvājums</div>
  <div style="font-size:12px;display:flex;flex-direction:column;gap:5px;color:var(--text2)">
    <div>Quote: <strong style="color:var(--text)">QUO-01204-Z8H1P0</strong></div>
    <div>Produkts: <strong style="color:var(--text)">FIX 6m</strong></div>
    <div>Gala cena: <strong style="color:var(--blue-text)">121.00 EUR/MWh</strong></div>
    <div>Periods: <strong style="color:var(--text)">01.06. – 30.11.2026</strong></div>
    <div>Apjoms: <strong style="color:var(--text)">120 MWh (gads)</strong></div>
  </div>
</div>
</div>
</div>
</div><!-- /screen-contract -->


<!-- ════════════════════════════════════════════
     SCREEN 5 – FIELDS REFERENCE
═════════════════════════════════════════════ -->
<div class="screen" id="screen-fields">
<div class="card">
  <div class="card-hdr"><i class="ti ti-list-details"></i>Lauku apraksts — B2B kalkulators</div>
  <div style="display:flex;gap:8px;margin-bottom:12px;flex-wrap:wrap">
    <span class="badge" style="background:var(--bg3);color:var(--text3)">auto = CRM/DK aizpilda</span>
    <span class="badge badge-red"><span class="req">*</span> obligāts</span>
    <span class="badge badge-green">zaļā — atsevišķi</span>
    <span class="badge badge-amber">≥50 MWh min markup</span>
  </div>
  <div style="overflow-x:auto">
  <table class="data-table" style="min-width:700px">
    <tr><th>#</th><th>Lauks</th><th>Avots</th><th>Formāts</th><th>Loģika / Validācija</th><th>Jira</th></tr>
    <tr><td>1</td><td><strong>Klienta EIC</strong></td><td>auto (ST)</td><td>43X-…</td><td>Automātiski no Account</td><td>CRM-91</td></tr>
    <tr><td>2</td><td><strong>Objekta EIC</strong> *</td><td>Menedžeris atlasa</td><td>43Z-… (vairāki)</td><td>Vismaz 1; semikols</td><td>CRM-91</td></tr>
    <tr><td>3</td><td><strong>Sākuma datums</strong> *</td><td>Menedžeris</td><td>DD.MM.GGGG</td><td>Vienmēr mēneša 1. datums</td><td>CRM-91</td></tr>
    <tr><td>4</td><td><strong>Beigu datums</strong></td><td>auto (FIX) / manuāls</td><td>DD.MM.GGGG / —</td><td>Pēdējā mēneša diena; SPOT = tukšs</td><td>CRM-91</td></tr>
    <tr><td>5</td><td><strong>Periods</strong> *</td><td>Dropdown</td><td>6/12/24/manuāli/SPOT</td><td>Tikai atļautās vērtības</td><td>CRM-91</td></tr>
    <tr><td>6</td><td><strong>Produkts</strong> *</td><td>Dropdown</td><td>FIX / SPOT</td><td>—</td><td>CRM-91</td></tr>
    <tr><td>7</td><td><strong>Kopējais apjoms (gads)</strong></td><td>auto (DK)</td><td>MWh</td><td>Gada apjoms no Claviz (CRM-716)</td><td>CRM-91, CRM-716</td></tr>
    <tr><td>8</td><td><strong>Bāzes cena</strong></td><td>auto (DK)</td><td>EUR/MWh</td><td>Pēc DK algoritma</td><td>CRM-91, DK-324</td></tr>
    <tr><td>9</td><td><strong>Uzcenojums</strong> *</td><td>Menedžeris</td><td>EUR/MWh ≥ 0</td><td>≥50 MWh → ≥ min_markup; &lt;50 → =0</td><td>CRM-91, CRM-716</td></tr>
    <tr><td>10</td><td><strong>Apkalpošanas maksa</strong> *</td><td>Menedžeris</td><td>EUR/obj/mēn ≥ 0</td><td>Nevar būt negatīvs</td><td>CRM-91</td></tr>
    <tr><td>11</td><td><strong>Zaļā enerģija</strong></td><td>Checkbox</td><td>Jā/Nē</td><td>Ja Jā → obligāta cena</td><td>CRM-91, CRM-716</td></tr>
    <tr><td>12</td><td><strong>Zaļās enerģijas cena</strong></td><td>Menedžeris</td><td>EUR/MWh</td><td>Atsevišķa rinda — netiek summēta!</td><td>CRM-716</td></tr>
    <tr><td>13</td><td><strong>Apmaksas dienas</strong> *</td><td>Dropdown</td><td>10/15/20/30/45/60</td><td>Tikai atļautās vērtības</td><td>CRM-91</td></tr>
    <tr><td>14</td><td><strong>Dienu piemaksa</strong></td><td>auto (CRM)</td><td>EUR/MWh</td><td>Pēc iekšējas tabulas</td><td>CRM-91</td></tr>
    <tr><td>15</td><td><strong>Gala cena</strong></td><td>auto (CRM formula)</td><td>EUR/MWh</td><td>Bāze + Markup + Piemaksa + Apkalp.</td><td>CRM-91, CRM-716</td></tr>
    <tr><td>16</td><td><strong>Quote ID</strong></td><td>auto (CRM)</td><td>QUO-XXXXX-…</td><td>Pēc saglabāšanas</td><td>CRM-91</td></tr>
    <tr><td>17</td><td><strong>Derīguma termiņš</strong></td><td>auto + Revise</td><td>Šodien 17:00</td><td>Max +5 darba dienas (CRM-716)</td><td>CRM-91, CRM-716</td></tr>
    <tr><td>18</td><td><strong>Min markup cena</strong></td><td>Konfigurācija</td><td>EUR/MWh</td><td>Globāls iestatījums (CRM-716)</td><td>CRM-716</td></tr>
  </table>
  </div>
</div>

<div class="card">
  <div class="card-hdr"><i class="ti ti-database"></i>DK statusa kodi</div>
  <table class="data-table">
    <tr><th>Kods</th><th>Paziņojums</th><th>Darbība CRM</th></tr>
    <tr><td><span class="badge badge-amber">1001</span></td><td>Aprēķini procesā</td><td>Gaida DK callback (requestId)</td></tr>
    <tr><td><span class="badge badge-green">1002</span></td><td>Veiksmīgi apstrādāts</td><td>Aizpilda cenas automātiski</td></tr>
    <tr><td><span class="badge badge-red">1004</span></td><td>Nederīgs pieprasījums</td><td>Rāda kļūdas paziņojumu</td></tr>
    <tr><td><span class="badge badge-red">1005</span></td><td>Trūkst datu — manuāli!</td><td>Nodod enerģētikas daļai</td></tr>
    <tr><td><span class="badge badge-amber">1006</span></td><td>Izveidots standarta piedāvājums</td><td>Aizpilda ar standarta vērtībām</td></tr>
    <tr><td><span class="badge badge-red">1007</span></td><td>Apjoms pārsniedz limitu — manuāli!</td><td>Nodod enerģētikas daļai</td></tr>
  </table>
</div>
</div><!-- /screen-fields -->

</div><!-- /content -->
</div><!-- /main -->
</div><!-- /app-shell -->

<script>
var currentScreen='offer';
var product='FIX6';

function showScreen(name){
  document.querySelectorAll('.screen').forEach(function(s){s.classList.remove('active')});
  document.getElementById('screen-'+name).classList.add('active');
  document.querySelectorAll('.nav-item').forEach(function(n){n.classList.remove('active')});
  var icons={offer:'ti-file-text',movein:'ti-home-move',email:'ti-mail',contract:'ti-writing',fields:'ti-list-details'};
  var titles={offer:'Jauns piedāvājums — FIX/SPOT',movein:'MoveIn scenārijs',email:'E-pasta priekšskatījums',contract:'Līguma izveide',fields:'Lauku apraksts'};
  var badges={offer:'Procesā',movein:'MoveIn',email:'Priekšskats',contract:'Sagatavots',fields:'Atsauce'};
  var bclass={offer:'badge-blue',movein:'badge-amber',email:'badge-blue',contract:'badge-green',fields:'badge-blue'};
  document.getElementById('topbar-icon').className='ti '+icons[name];
  document.getElementById('topbar-title').textContent=titles[name]||name;
  var b=document.getElementById('topbar-badge');
  b.textContent=badges[name]||'';
  b.className='badge '+(bclass[name]||'badge-blue');
  var primaryBtns={offer:'Nosūtīt klientam',movein:'Nosūtīt klientam',email:'Nosūtīt',contract:'Saglabāt līgumu',fields:''};
  var pb=document.getElementById('topbar-primary-btn');
  if(primaryBtns[name]){pb.style.display='';pb.innerHTML='<i class="ti ti-send"></i> '+primaryBtns[name];}
  else{pb.style.display='none';}
  currentScreen=name;
}

function setProduct(p,el){
  product=p;
  document.querySelectorAll('.tab').forEach(function(t){t.classList.remove('active')});
  el.classList.add('active');
  var hint=document.getElementById('date-hint');
  var to=document.getElementById('dateTo');
  if(p==='SPOT'){to.value='—';hint.textContent='SPOT — beigu datums netiek noteikts';}
  else if(p==='MAN'){to.value='';to.removeAttribute('readonly');to.classList.remove('auto');hint.textContent='Ievadiet manuāli (mēneša pēdējā diena)';}
  else{to.setAttribute('readonly','');to.classList.add('auto');calcEndDate();}
}

function calcEndDate(){
  var from=document.getElementById('dateFrom').value;
  if(!from||product==='SPOT'||product==='MAN')return;
  var d=new Date(from);
  var m={FIX6:6,FIX12:12,FIX24:24}[product]||6;
  d.setMonth(d.getMonth()+m);d.setDate(0);
  document.getElementById('dateTo').value=d.toISOString().slice(0,10);
  document.getElementById('date-hint').textContent='CRM aprēķina automātiski (+'+m+'m)';
}

function calcFinal(){
  var base=parseFloat(document.getElementById('basePrice').value)||0;
  var mkp=parseFloat(document.getElementById('markup').value)||0;
  var day=parseFloat(document.getElementById('dayFee').value)||0;
  var svc=parseFloat(document.getElementById('serviceFee').value)||0;
  var fin=(base+mkp+day).toFixed(2);
  document.getElementById('final-price').textContent=fin+' EUR/MWh';
  document.getElementById('d-base').textContent=base.toFixed(2);
  document.getElementById('d-mkp').textContent=mkp.toFixed(2);
  document.getElementById('d-day').textContent=day.toFixed(2);
  document.getElementById('d-svc').textContent=svc.toFixed(2);
  if(document.getElementById('greenCheck').checked){
    var gp=parseFloat(document.getElementById('greenPrice').value)||0;
    document.getElementById('green-val').textContent='+ '+gp.toFixed(2)+' EUR/MWh';
  }
}

function checkMarkup(){
  var vol=parseFloat(document.getElementById('volume').value)||0;
  var mkp=parseFloat(document.getElementById('markup').value)||0;
  document.getElementById('vol-disp').textContent=vol.toFixed(0);
  if(vol>=50){
    document.getElementById('min-mkp').textContent='5.00';
    document.getElementById('markup-note').textContent='(min 5.00)';
    document.getElementById('markup-warn').style.display=mkp<5?'flex':'none';
  }else{
    document.getElementById('min-mkp').textContent='0.00';
    document.getElementById('markup-note').textContent='(<50 MWh → 0)';
    document.getElementById('markup-warn').style.display='none';
  }
}

function toggleGreen(){
  var c=document.getElementById('greenCheck').checked;
  document.getElementById('green-row').style.display=c?'block':'none';
  document.getElementById('green-disp').style.display=c?'flex':'none';
  calcFinal();
}

function simDK(state){
  var msg=document.getElementById('dk-msg');
  var badge=document.getElementById('dk-badge');
  if(state==='pending'){
    msg.className='alert alert-amber';
    msg.innerHTML='<i class="ti ti-clock"></i><div class="alert-body"><strong>Aprēķini procesā (1001)</strong><p>DK neatbildēja 1 min. laikā. Jāgaida callback ar requestId. Turpiniet aizpildīt pārējos laukus.</p></div>';
    badge.className='badge badge-amber';badge.textContent='1001 – Procesā';
    document.getElementById('basePrice').value='';document.getElementById('dayFee').value='';document.getElementById('volume').value='';
  }else if(state==='success'){
    msg.className='alert alert-green';
    msg.innerHTML='<i class="ti ti-circle-check"></i><div class="alert-body"><strong>Aprēķini pabeigti (1002)</strong><p>DK atbildēja uzreiz. Cenas lauki aizpildīti automātiski.</p></div>';
    badge.className='badge badge-green';badge.textContent='1002 – Veiksmīgi';
    document.getElementById('basePrice').value='108.00';document.getElementById('dayFee').value='1.00';document.getElementById('volume').value='120';
  }else if(state==='error5'){
    msg.className='alert alert-red';
    msg.innerHTML='<i class="ti ti-alert-triangle"></i><div class="alert-body"><strong>Trūkst datu (1005)</strong><p>Objekts nav pie klienta pietiekami ilgi. Piedāvājums jāveido manuāli — nodod enerģētikas daļai.</p></div>';
    badge.className='badge badge-red';badge.textContent='1005 – Manuāli';
    document.getElementById('basePrice').value='—';document.getElementById('dayFee').value='—';document.getElementById('volume').value='—';
  }else{
    msg.className='alert alert-red';
    msg.innerHTML='<i class="ti ti-alert-triangle"></i><div class="alert-body"><strong>Apjoms pārsniedz limitu (1007)</strong><p>Kopējais patēriņš pārsniedz noteikto robežu. Nodod enerģētikas daļai manuālam aprēķinam.</p></div>';
    badge.className='badge badge-red';badge.textContent='1007 – Manuāli';
    document.getElementById('basePrice').value='—';document.getElementById('dayFee').value='—';document.getElementById('volume').value='—';
  }
  checkMarkup();calcFinal();
}

function updateEmailPreview(){
  var t=document.getElementById('email-intro-text').value;
  document.getElementById('email-body-preview').textContent=t;
  document.getElementById('email-subj-disp').value=document.getElementById('email-subject').value;
}

checkMarkup();calcFinal();
</script>
</body>
</html>
