< index.html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>القلم — النظام المدرسي</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
:root{
  --p:#1a3a5c;--pl:#2563a8;--pp:#dbeafe;
  --a:#b8860b;--al:#fef3c7;
  --g:#15803d;--gl:#dcfce7;
  --r:#dc2626;--rl:#fee2e2;
  --o:#c2410c;--ol:#ffedd5;
  --pu:#7c3aed;--pul:#ede9fe;
  --bg:#f0f4f8;--w:#fff;--tx:#0f172a;--tm:#64748b;--b:#e2e8f0;
  --sh:0 2px 8px rgba(0,0,0,.08);
  --sh2:0 4px 20px rgba(0,0,0,.12);
}
html,body{height:100%;overflow:hidden}
body{font-family:'Tajawal',sans-serif;background:var(--bg);color:var(--tx);font-size:14px;display:flex;flex-direction:column}

/* NAV BOTTOM */
#nav{background:var(--w);border-top:1px solid var(--b);display:flex;position:fixed;bottom:0;left:0;right:0;z-index:100;box-shadow:0 -2px 12px rgba(0,0,0,.08)}
.ni{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:8px 2px 6px;cursor:pointer;color:var(--tm);transition:color .15s;gap:3px;font-size:.58rem;font-weight:700;min-width:0}
.ni .ic{font-size:1.3rem;transition:transform .15s}
.ni.on{color:var(--p)}
.ni.on .ic{transform:scale(1.15)}
.ni span{white-space:nowrap;overflow:hidden;text-overflow:ellipsis;max-width:100%;text-align:center}

/* HEADER */
#hdr{background:linear-gradient(135deg,#0f2744,#1a3a5c);color:#fff;padding:12px 16px;display:flex;align-items:center;justify-content:space-between;flex-shrink:0}
.hdr-logo{display:flex;align-items:center;gap:8px}
.hdr-ico{width:34px;height:34px;background:linear-gradient(135deg,var(--a),#e9b94a);border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:1.1rem}
.hdr-title{font-size:.95rem;font-weight:800}
.hdr-sub{font-size:.65rem;opacity:.5;margin-top:1px}
#hdr-page{font-size:.82rem;font-weight:700;opacity:.85}

/* CONTENT */
#content{flex:1;overflow-y:auto;overflow-x:hidden;padding:12px 12px 70px;-webkit-overflow-scrolling:touch}
.pg{display:none}.pg.on{display:block}

/* CARDS GRID */
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:12px}
.grid3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;margin-bottom:12px}
.stat-card{background:var(--w);border-radius:12px;padding:14px 12px;border:1px solid var(--b);display:flex;align-items:center;gap:10px;box-shadow:var(--sh)}
.stat-ico{width:40px;height:40px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.2rem;flex-shrink:0}
.stat-n{font-size:1.5rem;font-weight:900;line-height:1}
.stat-l{font-size:.65rem;color:var(--tm);margin-top:2px;font-weight:600}

/* PANEL */
.panel{background:var(--w);border-radius:12px;border:1px solid var(--b);overflow:hidden;margin-bottom:12px;box-shadow:var(--sh)}
.panel-h{padding:12px 14px;border-bottom:1px solid var(--b);display:flex;align-items:center;justify-content:space-between;font-weight:700;font-size:.88rem}
.panel-b{padding:12px 14px}

/* TABLE */
.tbl-wrap{overflow-x:auto;-webkit-overflow-scrolling:touch}
table{width:100%;border-collapse:collapse;min-width:400px}
th{background:var(--bg);padding:8px 10px;text-align:right;font-size:.72rem;color:var(--tm);font-weight:700;border-bottom:1px solid var(--b);white-space:nowrap}
td{padding:9px 10px;border-bottom:1px solid #f1f5f9;font-size:.8rem;vertical-align:middle}
tr:last-child td{border:none}
tr:active td{background:#f8fafc}

/* BTN */
.btn{padding:8px 14px;border-radius:8px;font-size:.8rem;font-weight:700;cursor:pointer;border:none;display:inline-flex;align-items:center;gap:5px;transition:all .15s;font-family:'Tajawal',sans-serif;white-space:nowrap}
.btn:active{transform:scale(.95)}
.bp{background:var(--p);color:#fff}
.ba{background:var(--a);color:#fff}
.bg{background:var(--g);color:#fff}
.br{background:var(--r);color:#fff}
.bo{background:transparent;border:1.5px solid var(--b);color:var(--tx)}
.bpu{background:var(--pu);color:#fff}
.bo2{background:var(--gl);color:var(--g);border:1px solid #86efac}
.sm{padding:5px 10px;font-size:.72rem}
.btn-full{width:100%;justify-content:center;padding:12px}

/* BADGE */
.bx{display:inline-flex;align-items:center;padding:2px 7px;border-radius:20px;font-size:.65rem;font-weight:700;white-space:nowrap}
.bx-b{background:var(--pp);color:var(--p)}
.bx-g{background:var(--gl);color:var(--g)}
.bx-r{background:var(--rl);color:var(--r)}
.bx-o{background:var(--ol);color:var(--o)}
.bx-a{background:var(--al);color:var(--a)}
.bx-pu{background:var(--pul);color:var(--pu)}

/* FORM */
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.fi{display:flex;flex-direction:column;gap:4px}
.fi.fw{grid-column:1/-1}
label{font-size:.75rem;font-weight:700;color:var(--tm)}
input,select,textarea{padding:9px 11px;border:1.5px solid var(--b);border-radius:8px;font-size:.85rem;font-family:'Tajawal',sans-serif;color:var(--tx);outline:none;width:100%;transition:border-color .15s;background:var(--w)}
input:focus,select:focus,textarea:focus{border-color:var(--p)}
select{cursor:pointer}

/* MODAL */
.mo{position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:500;display:none;align-items:flex-end;justify-content:center}
.mo.on{display:flex}
.md{background:var(--w);border-radius:16px 16px 0 0;width:100%;max-height:90vh;overflow-y:auto;animation:slideUp .25s ease}
@keyframes slideUp{from{transform:translateY(100%)}to{transform:translateY(0)}}
.md-inner{max-width:540px;margin:0 auto}
.mh{padding:14px 16px;border-bottom:1px solid var(--b);display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;background:var(--w);z-index:1}
.mh h3{font-weight:800;font-size:.92rem}
.xb{width:28px;height:28px;border-radius:7px;border:none;background:var(--bg);cursor:pointer;font-size:1rem;font-family:'Tajawal',sans-serif}
.mb{padding:14px 16px}
.mf{padding:10px 16px 16px;border-top:1px solid var(--b);display:flex;gap:8px}
.mf .btn{flex:1;justify-content:center}

/* SEARCH */
.search-bar{position:relative;margin-bottom:10px}
.search-bar input{padding-right:36px;background:var(--w)}
.search-bar::before{content:'🔍';position:absolute;right:11px;top:50%;transform:translateY(-50%);font-size:.8rem;pointer-events:none}

/* EMPTY */
.empty{text-align:center;padding:40px 16px;color:var(--tm)}
.empty .ei{font-size:2.5rem;margin-bottom:10px;opacity:.4}
.empty h3{font-size:.88rem;font-weight:700;margin-bottom:4px}
.empty p{font-size:.75rem}

/* PHOTO UPLOAD */
.photo-zone{border:2px dashed var(--b);border-radius:10px;padding:16px;text-align:center;cursor:pointer;position:relative;background:var(--bg);transition:all .2s}
.photo-zone.has{border-style:solid;border-color:var(--g);padding:0}
.photo-zone input{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;height:100%}
.photo-zone img{width:100%;height:130px;object-fit:cover;border-radius:8px;display:block}
.photo-zone .ph-rm{position:absolute;top:6px;left:6px;background:var(--r);color:#fff;border:none;border-radius:5px;padding:2px 7px;font-size:.68rem;cursor:pointer;z-index:2;font-family:'Tajawal',sans-serif}

/* AVATAR */
.av{width:32px;height:32px;border-radius:50%;background:var(--pp);display:flex;align-items:center;justify-content:center;font-size:.75rem;font-weight:800;color:var(--p);overflow:hidden;flex-shrink:0;border:1.5px solid var(--b)}
.av img{width:100%;height:100%;object-fit:cover}
.td-nm{display:flex;align-items:center;gap:8px}

/* DIST BAR */
.bar{display:flex;align-items:center;gap:8px;margin-bottom:6px}
.bar-l{width:50px;font-size:.7rem;color:var(--tm);font-weight:600;flex-shrink:0;text-align:right}
.bar-t{flex:1;background:var(--bg);border-radius:4px;height:14px;overflow:hidden}
.bar-f{height:100%;background:linear-gradient(90deg,var(--p),var(--pl));border-radius:4px;transition:width .4s}
.bar-n{width:20px;font-size:.7rem;font-weight:700;color:var(--p)}

/* TOAST */
#toast{position:fixed;bottom:76px;left:50%;transform:translateX(-50%) translateY(20px);background:#0f172a;color:#fff;padding:9px 18px;border-radius:8px;font-size:.8rem;font-weight:700;z-index:9999;opacity:0;transition:all .25s;pointer-events:none;white-space:nowrap;font-family:'Tajawal',sans-serif}
#toast.on{opacity:1;transform:translateX(-50%) translateY(0)}
#toast.ok{background:var(--g)}
#toast.er{background:var(--r)}

/* PRINT */
.prt{display:none}
@media print{
  body>*:not(.prt){display:none!important}
  .prt{display:flex!important;flex-wrap:wrap;gap:5mm;padding:6mm;background:#fff;align-content:flex-start}
  .prc{width:85.6mm;height:54mm;background:linear-gradient(135deg,#0f2744,#1a3a5c)!important;border-radius:4mm;color:#fff!important;print-color-adjust:exact;-webkit-print-color-adjust:exact;overflow:hidden;page-break-inside:avoid;font-family:'Tajawal',sans-serif;position:relative}
  .prc-stripe{height:2mm;background:linear-gradient(90deg,#b8860b,#f0d060,#b8860b)!important;print-color-adjust:exact;-webkit-print-color-adjust:exact}
  .prc-body{padding:2.5mm 3.5mm;display:flex;gap:2.5mm;align-items:center;position:relative;z-index:1}
  .prc-ph{width:15mm;height:18mm;border-radius:1.5mm;border:.4mm solid rgba(201,168,76,.7);overflow:hidden;flex-shrink:0;background:rgba(255,255,255,.1);display:flex;align-items:center;justify-content:center;font-size:11pt;font-weight:800}
  .prc-ph img{width:100%;height:100%;object-fit:cover}
  .prc-info{flex:1}
  .prc-sch{font-size:5pt;opacity:.6;font-weight:700;margin-bottom:1.5mm}
  .prc-nm{font-size:9.5pt;font-weight:800;margin-bottom:1mm}
  .prc-badges{display:flex;gap:.8mm;flex-wrap:wrap;margin-bottom:1mm}
  .prc-badge{padding:.3mm 1.5mm;border-radius:2mm;font-size:5pt;font-weight:700}
  .prc-bg{background:rgba(184,134,11,.3)!important;color:#FFE082!important;border:.2mm solid rgba(184,134,11,.6);print-color-adjust:exact;-webkit-print-color-adjust:exact}
  .prc-bw{background:rgba(255,255,255,.15)!important;color:rgba(255,255,255,.9)!important;border:.2mm solid rgba(255,255,255,.3);print-color-adjust:exact;-webkit-print-color-adjust:exact}
  .prc-right{display:flex;flex-direction:column;align-items:center;gap:.8mm;flex-shrink:0}
  .prc-qr{background:#fff!important;border-radius:1mm;padding:.8mm;width:13mm;height:13mm;display:flex;align-items:center;justify-content:center;print-color-adjust:exact;-webkit-print-color-adjust:exact}
  .prc-qr canvas,.prc-qr img{width:11mm!important;height:11mm!important}
  .prc-ql{font-size:3.5pt;opacity:.4;text-align:center}
  .prc-ft{background:rgba(0,0,0,.2)!important;padding:1.2mm 3.5mm;display:flex;justify-content:space-between;print-color-adjust:exact;-webkit-print-color-adjust:exact}
  .prc-id{font-family:monospace;font-size:4.5pt;opacity:.45}
  .prc-yr{font-size:5pt;color:#FAD7A0!important;font-weight:700;print-color-adjust:exact;-webkit-print-color-adjust:exact}
}

/* PROFESSIONAL CARD PREVIEW */
.pro-card{background:linear-gradient(135deg,#0f2744,#1a3a5c,#1e4976);border-radius:14px;color:#fff;overflow:hidden;box-shadow:var(--sh2);position:relative}
.pro-card::before{content:'';position:absolute;top:-30px;right:-30px;width:120px;height:120px;background:radial-gradient(circle,rgba(184,134,11,.2),transparent 70%);border-radius:50%}
.pc-stripe{height:5px;background:linear-gradient(90deg,var(--a),#f0d060,var(--a))}
.pc-body{padding:14px;display:flex;gap:12px;align-items:center;position:relative;z-index:1}
.pc-photo{width:68px;height:78px;border-radius:8px;border:2px solid rgba(184,134,11,.6);overflow:hidden;flex-shrink:0;background:rgba(255,255,255,.1);display:flex;align-items:center;justify-content:center;font-size:1.6rem;font-weight:800}
.pc-photo img{width:100%;height:100%;object-fit:cover}
.pc-info{flex:1;min-width:0}
.pc-sch{font-size:.58rem;opacity:.55;font-weight:700;letter-spacing:.05em;margin-bottom:6px}
.pc-nm{font-size:.95rem;font-weight:800;margin-bottom:5px}
.pc-badges{display:flex;flex-wrap:wrap;gap:4px;margin-bottom:5px}
.pc-badge{padding:1px 8px;border-radius:20px;font-size:.6rem;font-weight:700}
.pc-bg{background:rgba(184,134,11,.25);border:1px solid rgba(184,134,11,.5);color:#FFE082}
.pc-bw{background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.2);color:rgba(255,255,255,.85)}
.pc-meta{font-size:.62rem;opacity:.5;display:flex;flex-direction:column;gap:1px}
.pc-right{display:flex;flex-direction:column;align-items:center;gap:5px;flex-shrink:0}
.pc-qr{background:#fff;border-radius:6px;padding:4px;width:62px;height:62px;display:flex;align-items:center;justify-content:center}
.pc-qr canvas,.pc-qr img{width:54px!important;height:54px!important}
.pc-ql{font-size:.5rem;opacity:.4;text-align:center}
.pc-ft{background:rgba(0,0,0,.22);padding:8px 14px;display:flex;justify-content:space-between;align-items:center;position:relative;z-index:1}
.pc-id{font-family:monospace;font-size:.58rem;opacity:.4}
.pc-yr{font-size:.62rem;color:#FAD7A0;font-weight:700}

/* MODULE COLORS */
.mod-blue{--mc:var(--p);--mcl:var(--pp)}
.mod-green{--mc:var(--g);--mcl:var(--gl)}
.mod-gold{--mc:var(--a);--mcl:var(--al)}
.mod-red{--mc:var(--r);--mcl:var(--rl)}
.mod-orange{--mc:var(--o);--mcl:var(--ol)}
.mod-purple{--mc:var(--pu);--mcl:var(--pul)}

/* ACCOUNTING */
.acc-summary{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px}
.acc-card{border-radius:10px;padding:12px;text-align:center}
.acc-card .ac-n{font-size:1.3rem;font-weight:900}
.acc-card .ac-l{font-size:.65rem;font-weight:600;margin-top:2px}
.paid-card{background:var(--gl);color:var(--g)}
.unpaid-card{background:var(--rl);color:var(--r)}

/* WAREHOUSE */
.wh-card{background:var(--w);border:1.5px solid var(--b);border-radius:10px;padding:12px;margin-bottom:8px;display:flex;align-items:center;gap:10px}
.wh-ico{width:38px;height:38px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:1.1rem;flex-shrink:0}
.wh-info{flex:1;min-width:0}
.wh-nm{font-weight:700;font-size:.85rem;margin-bottom:2px}
.wh-det{font-size:.72rem;color:var(--tm)}
.wh-qty{font-size:1.1rem;font-weight:900;flex-shrink:0;text-align:center}
.wh-qty small{display:block;font-size:.6rem;color:var(--tm);font-weight:600}
.low-stock{border-color:#fca5a5;background:#fff5f5}

/* TEACHERS */
.tea-card{background:var(--w);border:1.5px solid var(--b);border-radius:10px;padding:12px;margin-bottom:8px}
.tea-top{display:flex;align-items:center;gap:10px;margin-bottom:8px}
.tea-av{width:40px;height:40px;border-radius:50%;background:var(--pul);display:flex;align-items:center;justify-content:center;font-size:.9rem;font-weight:800;color:var(--pu);flex-shrink:0}
.tea-nm{font-weight:800;font-size:.88rem}
.tea-sub{font-size:.7rem;color:var(--tm)}
.tea-stats{display:grid;grid-template-columns:1fr 1fr 1fr;gap:6px}
.tea-stat{background:var(--bg);border-radius:7px;padding:7px;text-align:center}
.tea-stat .tsn{font-size:.95rem;font-weight:800}
.tea-stat .tsl{font-size:.6rem;color:var(--tm);font-weight:600}

/* EXPENSES */
.exp-item{background:var(--w);border:1.5px solid var(--b);border-radius:10px;padding:11px 12px;margin-bottom:7px;display:flex;align-items:center;gap:10px}
.exp-ico{width:36px;height:36px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:1rem;flex-shrink:0}
.exp-info{flex:1;min-width:0}
.exp-nm{font-weight:700;font-size:.83rem}
.exp-dt{font-size:.68rem;color:var(--tm);margin-top:1px}
.exp-amt{font-weight:900;font-size:.95rem;flex-shrink:0}

/* FAB */
.fab{position:fixed;bottom:76px;left:14px;width:48px;height:48px;border-radius:50%;background:linear-gradient(135deg,var(--p),var(--pl));color:#fff;border:none;font-size:1.4rem;cursor:pointer;box-shadow:0 4px 14px rgba(26,58,92,.4);z-index:90;display:flex;align-items:center;justify-content:center;transition:transform .15s}
.fab:active{transform:scale(.9)}
</style>
</head>
<body>

<!-- HEADER -->
<div id="hdr">
  <div class="hdr-logo">
    <div class="hdr-ico">✏️</div>
    <div>
      <div class="hdr-title">مدرسة القلم</div>
      <div class="hdr-sub">النظام الإداري المتكامل</div>
    </div>
  </div>
  <div id="hdr-page">الرئيسية</div>
</div>

<!-- CONTENT -->
<div id="content">

  <!-- DASHBOARD -->
  <div class="pg on" id="p-dash">
    <div class="grid2">
      <div class="stat-card"><div class="stat-ico" style="background:var(--pp)">👨‍🎓</div><div><div class="stat-n" id="ds-stu">0</div><div class="stat-l">الطلاب</div></div></div>
      <div class="stat-card"><div class="stat-ico" style="background:var(--pul)">👩‍🏫</div><div><div class="stat-n" id="ds-tea">0</div><div class="stat-l">المدرسون</div></div></div>
    </div>
    <div class="grid3">
      <div class="stat-card" style="flex-direction:column;text-align:center;gap:4px"><div style="font-size:1.3rem">📚</div><div class="stat-n" id="ds-bk">0</div><div class="stat-l">الكتب</div></div>
      <div class="stat-card" style="flex-direction:column;text-align:center;gap:4px"><div style="font-size:1.3rem">💰</div><div class="stat-n" id="ds-paid" style="color:var(--g)">0</div><div class="stat-l">أقساط مدفوعة</div></div>
      <div class="stat-card" style="flex-direction:column;text-align:center;gap:4px"><div style="font-size:1.3rem">⚠️</div><div class="stat-n" id="ds-unpaid" style="color:var(--r)">0</div><div class="stat-l">غير مدفوعة</div></div>
    </div>
    <div class="panel">
      <div class="panel-h">📊 توزيع الطلاب على الصفوف</div>
      <div class="panel-b" id="ds-dist"><div class="empty"><div class="ei">📊</div><p>أضف طلاباً لرؤية التوزيع</p></div></div>
    </div>
    <div class="panel">
      <div class="panel-h">💸 آخر المصاريف <button class="btn bo sm" onclick="go('exp')">عرض الكل</button></div>
      <div id="ds-exp"><div class="empty" style="padding:20px"><div class="ei" style="font-size:1.8rem">💸</div><p>لا توجد مصاريف</p></div></div>
    </div>
  </div>

  <!-- STUDENTS -->
  <div class="pg" id="p-stu">
    <div class="search-bar"><input id="sq" placeholder="بحث بالاسم أو الرقم..." oninput="rStu()"></div>
    <div style="display:flex;gap:8px;margin-bottom:10px">
      <select id="sf" onchange="rStu()" style="flex:1"><option value="">كل الصفوف</option></select>
    </div>
    <div class="panel">
      <div class="panel-h">👨‍🎓 الطلاب <span id="sc2" class="bx bx-b">0</span></div>
      <div id="st"></div>
    </div>
  </div>

  <!-- CARDS -->
  <div class="pg" id="p-cd">
    <div class="search-bar"><input id="cq" placeholder="بحث عن طالب..." oninput="rCd()"></div>
    <select id="cf" onchange="rCd()" style="width:100%;margin-bottom:10px"><option value="">كل الصفوف</option></select>
    <div id="cd-list"></div>
  </div>

  <!-- BOOKS -->
  <div class="pg" id="p-bk">
    <div class="search-bar"><input id="bq" placeholder="بحث عن كتاب..." oninput="rBk()"></div>
    <select id="bf" onchange="rBk()" style="width:100%;margin-bottom:10px"><option value="">كل الصفوف</option></select>
    <div id="bk-list"></div>
  </div>

  <!-- ACCOUNTING - FEES -->
  <div class="pg" id="p-acc">
    <div class="acc-summary">
      <div class="acc-card paid-card"><div class="ac-n" id="acc-paid">0</div><div class="ac-l">✅ مدفوع</div></div>
      <div class="acc-card unpaid-card"><div class="ac-n" id="acc-unpaid">0</div><div class="ac-l">⏳ متبقي</div></div>
    </div>
    <div class="search-bar"><input id="aq" placeholder="بحث عن طالب..." oninput="rAcc()"></div>
    <select id="af" onchange="rAcc()" style="width:100%;margin-bottom:10px"><option value="">كل الصفوف</option></select>
    <div id="acc-list"></div>
  </div>

  <!-- WAREHOUSE -->
  <div class="pg" id="p-wh">
    <div class="search-bar"><input id="wq" placeholder="بحث عن مادة..." oninput="rWh()"></div>
    <div id="wh-list"></div>
  </div>

  <!-- TEACHERS -->
  <div class="pg" id="p-tea">
    <div class="search-bar"><input id="tq" placeholder="بحث عن مدرس..." oninput="rTea()"></div>
    <div id="tea-list"></div>
  </div>

  <!-- EXPENSES -->
  <div class="pg" id="p-exp">
    <div class="grid2" style="margin-bottom:10px">
      <div class="stat-card"><div class="stat-ico" style="background:var(--rl)">💸</div><div><div class="stat-n" id="exp-total" style="font-size:1rem">0</div><div class="stat-l">إجمالي المصاريف</div></div></div>
      <div class="stat-card"><div class="stat-ico" style="background:var(--al)">📅</div><div><div class="stat-n" id="exp-month" style="font-size:1rem">0</div><div class="stat-l">هذا الشهر</div></div></div>
    </div>
    <div class="search-bar"><input id="eq" placeholder="بحث عن مصروف..." oninput="rExp()"></div>
    <div id="exp-list"></div>
  </div>

</div>

<!-- BOTTOM NAV -->
<div id="nav">
  <div class="ni on" onclick="go('dash')" id="ni-dash"><div class="ic">🏠</div><span>الرئيسية</span></div>
  <div class="ni" onclick="go('stu')" id="ni-stu"><div class="ic">👨‍🎓</div><span>الطلاب</span></div>
  <div class="ni" onclick="go('acc')" id="ni-acc"><div class="ic">💰</div><span>الأقساط</span></div>
  <div class="ni" onclick="go('tea')" id="ni-tea"><div class="ic">👩‍🏫</div><span>المدرسون</span></div>
  <div class="ni" onclick="showMore()" id="ni-more"><div class="ic">⋯</div><span>المزيد</span></div>
</div>

<!-- FAB -->
<button class="fab" id="fab" onclick="fabAction()">➕</button>

<!-- MORE MENU MODAL -->
<div class="mo" id="m-more">
  <div class="md">
    <div class="md-inner">
      <div class="mh"><h3>القوائم الأخرى</h3><button class="xb" onclick="cm('m-more')">✕</button></div>
      <div class="mb" style="display:grid;grid-template-columns:1fr 1fr;gap:10px">
        <button class="btn bp btn-full" style="flex-direction:column;gap:4px;padding:16px 8px;font-size:.8rem" onclick="go('bk');cm('m-more')"><span style="font-size:1.5rem">📚</span>الكتب والملفات</button>
        <button class="btn bpu btn-full" style="flex-direction:column;gap:4px;padding:16px 8px;font-size:.8rem" onclick="go('cd');cm('m-more')"><span style="font-size:1.5rem">🪪</span>البطاقات</button>
        <button class="btn" style="background:var(--ol);color:var(--o);flex-direction:column;gap:4px;padding:16px 8px;font-size:.8rem;justify-content:center;border-radius:8px" onclick="go('wh');cm('m-more')"><span style="font-size:1.5rem">📦</span>المستودع</button>
        <button class="btn" style="background:var(--rl);color:var(--r);flex-direction:column;gap:4px;padding:16px 8px;font-size:.8rem;justify-content:center;border-radius:8px" onclick="go('exp');cm('m-more')"><span style="font-size:1.5rem">💸</span>المصاريف</button>
      </div>
    </div>
  </div>
</div>

<!-- MODAL: STUDENT -->
<div class="mo" id="m-stu">
  <div class="md">
    <div class="md-inner">
      <div class="mh"><h3 id="mstu-t">➕ إضافة طالب</h3><button class="xb" onclick="cm('m-stu')">✕</button></div>
      <div class="mb">
        <div class="fi fw" style="margin-bottom:12px">
          <label>📷 صورة الطالب</label>
          <div class="photo-zone" id="ph-zone">
            <input type="file" id="s-img" accept="image/*" onchange="onPhoto(event)">
            <div id="ph-placeholder"><div style="font-size:1.8rem;margin-bottom:4px">📷</div><p style="font-size:.75rem;color:var(--tm)">اضغط لرفع صورة</p></div>
            <img id="ph-prev" style="display:none">
            <button class="ph-rm" id="ph-rm" style="display:none" onclick="rmPhoto(event)">✕</button>
          </div>
        </div>
        <div class="form-grid">
          <div class="fi fw"><label>الاسم الكامل *</label><input id="s-n" placeholder="أحمد محمد علي"></div>
          <div class="fi"><label>رقم الطالب</label><input id="s-i" readonly style="color:var(--tm);background:#f8fafc"></div>
          <div class="fi"><label>الصف *</label><select id="s-c"></select></div>
          <div class="fi"><label>تاريخ الميلاد</label><input type="date" id="s-d"></div>
          <div class="fi"><label>هاتف ولي الأمر</label><input id="s-p" placeholder="05XXXXXXXX"></div>
          <div class="fi"><label>السنة الدراسية</label><input id="s-y" value="2024-2025"></div>
          <div class="fi"><label>القسط السنوي (ر.س)</label><input type="number" id="s-fee" placeholder="0"></div>
          <div class="fi"><label>المدفوع (ر.س)</label><input type="number" id="s-paid" placeholder="0"></div>
          <div class="fi fw"><label>ملاحظات</label><textarea id="s-no" rows="2" placeholder="ملاحظات..."></textarea></div>
        </div>
      </div>
      <div class="mf"><button class="btn bo" onclick="cm('m-stu')">إلغاء</button><button class="btn bp" onclick="saveStu()">💾 حفظ</button></div>
    </div>
  </div>
</div>

<!-- MODAL: BOOK -->
<div class="mo" id="m-bk">
  <div class="md">
    <div class="md-inner">
      <div class="mh"><h3 id="mbk-t">📚 إضافة كتاب</h3><button class="xb" onclick="cm('m-bk')">✕</button></div>
      <div class="mb">
        <div class="form-grid">
          <div class="fi fw"><label>اسم الكتاب *</label><input id="b-n" placeholder="رياضيات الصف الأول"></div>
          <div class="fi"><label>الصف *</label><select id="b-c"></select></div>
          <div class="fi"><label>المادة</label><input id="b-s" placeholder="رياضيات"></div>
          <div class="fi"><label>المؤلف</label><input id="b-a" placeholder="اسم المؤلف"></div>
          <div class="fi"><label>عدد النسخ</label><input type="number" id="b-cp" min="0" placeholder="0"></div>
          <div class="fi fw">
            <label>📎 ملف الكتاب الرقمي</label>
            <div class="photo-zone" id="bfile-zone" style="text-align:center;padding:14px">
              <input type="file" id="b-file" accept=".pdf,.doc,.docx,.ppt,.pptx" onchange="onBookFile(event)">
              <div id="bfile-ph"><div style="font-size:1.5rem;margin-bottom:4px">📎</div><p style="font-size:.75rem;color:var(--tm)">اضغط لرفع ملف PDF أو Word</p></div>
            </div>
          </div>
        </div>
      </div>
      <div class="mf"><button class="btn bo" onclick="cm('m-bk')">إلغاء</button><button class="btn bp" onclick="saveBk()">💾 حفظ</button></div>
    </div>
  </div>
</div>

<!-- MODAL: TEACHER -->
<div class="mo" id="m-tea">
  <div class="md">
    <div class="md-inner">
      <div class="mh"><h3 id="mtea-t">👩‍🏫 إضافة مدرس</h3><button class="xb" onclick="cm('m-tea')">✕</button></div>
      <div class="mb">
        <div class="form-grid">
          <div class="fi fw"><label>اسم المدرس *</label><input id="t-n" placeholder="محمد أحمد"></div>
          <div class="fi"><label>التخصص *</label><input id="t-s" placeholder="رياضيات"></div>
          <div class="fi"><label>رقم الجوال</label><input id="t-p" placeholder="05XXXXXXXX"></div>
          <div class="fi"><label>الراتب الأساسي (ر.س)</label><input type="number" id="t-sal" placeholder="0"></div>
          <div class="fi"><label>ساعة العمل (ر.س)</label><input type="number" id="t-hr" placeholder="0"></div>
          <div class="fi"><label>ساعات هذا الشهر</label><input type="number" id="t-hrs" placeholder="0"></div>
        </div>
      </div>
      <div class="mf"><button class="btn bo" onclick="cm('m-tea')">إلغاء</button><button class="btn bp" onclick="saveTea()">💾 حفظ</button></div>
    </div>
  </div>
</div>

<!-- MODAL: WAREHOUSE ITEM -->
<div class="mo" id="m-wh">
  <div class="md">
    <div class="md-inner">
      <div class="mh"><h3 id="mwh-t">📦 إضافة مادة للمستودع</h3><button class="xb" onclick="cm('m-wh')">✕</button></div>
      <div class="mb">
        <div class="form-grid">
          <div class="fi fw"><label>اسم المادة *</label><input id="w-n" placeholder="أقلام حبر"></div>
          <div class="fi"><label>الفئة</label><select id="w-cat"><option value="قرطاسية">قرطاسية</option><option value="أثاث">أثاث</option><option value="أجهزة">أجهزة</option><option value="تنظيف">مواد تنظيف</option><option value="أخرى">أخرى</option></select></div>
          <div class="fi"><label>الكمية *</label><input type="number" id="w-q" min="0" placeholder="0"></div>
          <div class="fi"><label>الحد الأدنى للتنبيه</label><input type="number" id="w-min" min="0" placeholder="5"></div>
          <div class="fi"><label>سعر الوحدة (ر.س)</label><input type="number" id="w-p" placeholder="0"></div>
          <div class="fi fw"><label>ملاحظات</label><input id="w-no" placeholder="ملاحظات..."></div>
        </div>
      </div>
      <div class="mf"><button class="btn bo" onclick="cm('m-wh')">إلغاء</button><button class="btn bp" onclick="saveWh()">💾 حفظ</button></div>
    </div>
  </div>
</div>

<!-- MODAL: EXPENSE -->
<div class="mo" id="m-exp">
  <div class="md">
    <div class="md-inner">
      <div class="mh"><h3 id="mexp-t">💸 إضافة مصروف</h3><button class="xb" onclick="cm('m-exp')">✕</button></div>
      <div class="mb">
        <div class="form-grid">
          <div class="fi fw"><label>وصف المصروف *</label><input id="e-n" placeholder="فاتورة كهرباء"></div>
          <div class="fi"><label>الفئة</label><select id="e-cat">
            <option value="فواتير">فواتير</option>
            <option value="صيانة">صيانة</option>
            <option value="رواتب">رواتب</option>
            <option value="قرطاسية">قرطاسية</option>
            <option value="أخرى">أخرى</option>
          </select></div>
          <div class="fi"><label>المبلغ (ر.س) *</label><input type="number" id="e-amt" placeholder="0"></div>
          <div class="fi"><label>التاريخ</label><input type="date" id="e-dt"></div>
          <div class="fi fw"><label>ملاحظات</label><input id="e-no" placeholder="ملاحظات..."></div>
        </div>
      </div>
      <div class="mf"><button class="btn bo" onclick="cm('m-exp')">إلغاء</button><button class="btn bp" onclick="saveExp()">💾 حفظ</button></div>
    </div>
  </div>
</div>

<!-- MODAL: CARD PREVIEW -->
<div class="mo" id="m-card">
  <div class="md">
    <div class="md-inner">
      <div class="mh"><h3>🪪 بطاقة الطالب</h3><button class="xb" onclick="cm('m-card')">✕</button></div>
      <div class="mb"><div id="m-card-body"></div></div>
      <div class="mf"><button class="btn bo" onclick="cm('m-card')">إغلاق</button><button class="btn ba" onclick="prtCard()">🖨️ طباعة</button></div>
    </div>
  </div>
</div>

<!-- MODAL: PAY INSTALLMENT -->
<div class="mo" id="m-pay">
  <div class="md">
    <div class="md-inner">
      <div class="mh"><h3>💳 تسجيل دفعة</h3><button class="xb" onclick="cm('m-pay')">✕</button></div>
      <div class="mb">
        <div id="pay-info" style="background:var(--bg);border-radius:8px;padding:10px;margin-bottom:12px;font-size:.82rem"></div>
        <div class="fi"><label>المبلغ المدفوع (ر.س) *</label><input type="number" id="pay-amt" placeholder="0"></div>
        <div class="fi" style="margin-top:8px"><label>ملاحظة</label><input id="pay-note" placeholder="دفعة جزئية..."></div>
      </div>
      <div class="mf"><button class="btn bo" onclick="cm('m-pay')">إلغاء</button><button class="btn bg" onclick="savePay()">✅ تأكيد الدفع</button></div>
    </div>
  </div>
</div>

<div id="toast"></div>
<div class="prt" id="prt"></div>

<script>
// DATA
const CL=[{id:1,n:'الأول',a:'١'},{id:2,n:'الثاني',a:'٢'},{id:3,n:'الثالث',a:'٣'},{id:4,n:'الرابع',a:'٤'},{id:5,n:'الخامس',a:'٥'},{id:6,n:'السادس',a:'٦'},{id:7,n:'السابع',a:'٧'},{id:8,n:'الثامن',a:'٨'},{id:9,n:'التاسع',a:'٩'}];
const CAT_ICO={'فواتير':'🧾','صيانة':'🔧','رواتب':'💵','قرطاسية':'✏️','أخرى':'📋','قرطاسية2':'🖊️','أثاث':'🪑','أجهزة':'💻','تنظيف':'🧹'};

let S=lget('ql_s',[]);
let B=lget('ql_b',[]);
let T=lget('ql_t',[]);
let W=lget('ql_w',[]);
let E=lget('ql_e',[]);
let P=lget('ql_p',0);

let curPage='dash',curCard=null,curPayId=null;
let eSid=null,eBid=null,eTid=null,eWid=null,eEid=null;
let curPhoto=null,curBFile=null,curBFileName=null;

function lget(k,d){try{const v=localStorage.getItem(k);return v?JSON.parse(v):d;}catch{return d;}}
function lset(k,v){try{localStorage.setItem(k,JSON.stringify(v));}catch{toast('تجاوزت سعة التخزين المحلي','er');}}
const sv=()=>{lset('ql_s',S);lset('ql_b',B);lset('ql_t',T);lset('ql_w',W);lset('ql_e',E);};
const gid=p=>p+'-'+Date.now().toString().slice(-6)+Math.random().toString(36).slice(-2);
const gcn=id=>CL.find(c=>c.id==id)?.n||'—';
const ini=n=>(n||'').split(' ').map(x=>x[0]||'').join('').slice(0,2).toUpperCase();
const fmt=n=>Number(n||0).toLocaleString('ar-SA');
const today=()=>new Date().toISOString().slice(0,10);

function toast(msg,t=''){
  const el=document.getElementById('toast');
  el.textContent=msg;el.className='on '+(t||'');
  clearTimeout(el._t);el._t=setTimeout(()=>el.className='',2500);
}
function om(id){document.getElementById(id).classList.add('on')}
function cm(id){document.getElementById(id).classList.remove('on');}
document.querySelectorAll('.mo').forEach(el=>el.addEventListener('click',e=>{if(e.target===el)cm(el.id)}));

// NAVIGATION
const pages={
  dash:{t:'الرئيسية',fab:null},
  stu:{t:'الطلاب',fab:'oAStu'},
  cd:{t:'البطاقات',fab:'prtAll'},
  bk:{t:'الكتب والملفات',fab:'oABk'},
  acc:{t:'محاسبة الأقساط',fab:null},
  tea:{t:'المدرسون والرواتب',fab:'oATea'},
  wh:{t:'المستودع',fab:'oAWh'},
  exp:{t:'المصاريف',fab:'oAExp'},
};
function go(pg){
  document.querySelectorAll('.pg').forEach(p=>p.classList.remove('on'));
  document.querySelectorAll('.ni').forEach(n=>n.classList.remove('on'));
  document.getElementById('p-'+pg).classList.add('on');
  const ni=document.getElementById('ni-'+pg);
  if(ni)ni.classList.add('on');
  document.getElementById('hdr-page').textContent=pages[pg]?.t||'';
  curPage=pg;
  const fab=document.getElementById('fab');
  fab.style.display=pages[pg]?.fab?'flex':'none';
  if(pg==='dash')rDash();
  if(pg==='stu'){pSel();rStu();}
  if(pg==='cd'){pSel();rCd();}
  if(pg==='bk'){pSel();rBk();}
  if(pg==='acc'){pSel();rAcc();}
  if(pg==='tea')rTea();
  if(pg==='wh')rWh();
  if(pg==='exp')rExp();
}
function fabAction(){
  const fn=pages[curPage]?.fab;
  if(fn&&window[fn])window[fn]();
  else if(curPage==='cd')prtAll();
}
function showMore(){om('m-more');}

// SELECT POPULATE
function pSel(){
  ['s-c','b-c','sf','bf','cf','af'].forEach(id=>{
    const el=document.getElementById(id);if(!el)return;
    const isF=['sf','bf','cf','af'].includes(id);
    const cv=el.value;
    el.innerHTML=isF?'<option value="">كل الصفوف</option>':'<option value="">-- اختر --</option>';
    CL.forEach(c=>{const o=document.createElement('option');o.value=c.id;o.textContent='الصف '+c.n;el.appendChild(o);});
    el.value=cv;
  });
}

// PHOTO
function onPhoto(e){
  const f=e.target.files[0];if(!f)return;
  if(f.size>3*1024*1024){toast('الصورة أكبر من 3MB','er');return;}
  const r=new FileReader();
  r.onload=ev=>{
    curPhoto=ev.target.result;
    document.getElementById('ph-prev').src=curPhoto;
    document.getElementById('ph-prev').style.display='block';
    document.getElementById('ph-placeholder').style.display='none';
    document.getElementById('ph-rm').style.display='block';
    document.getElementById('ph-zone').classList.add('has');
  };r.readAsDataURL(f);
}
function rmPhoto(e){
  e.stopPropagation();curPhoto=null;
  document.getElementById('s-img').value='';
  document.getElementById('ph-prev').style.display='none';
  document.getElementById('ph-placeholder').style.display='block';
  document.getElementById('ph-rm').style.display='none';
  document.getElementById('ph-zone').classList.remove('has');
}
function setPhoto(src){
  curPhoto=src||null;
  document.getElementById('ph-prev').src=src||'';
  document.getElementById('ph-prev').style.display=src?'block':'none';
  document.getElementById('ph-placeholder').style.display=src?'none':'block';
  document.getElementById('ph-rm').style.display=src?'block':'none';
  document.getElementById('ph-zone').classList.toggle('has',!!src);
}

// BOOK FILE
function onBookFile(e){
  const f=e.target.files[0];if(!f)return;
  if(f.size>20*1024*1024){toast('الملف أكبر من 20MB','er');return;}
  const r=new FileReader();
  r.onload=ev=>{
    curBFile=ev.target.result;curBFileName=f.name;
    document.getElementById('bfile-ph').innerHTML=`<div style="font-size:1.2rem">📄</div><p style="font-size:.72rem;color:var(--g);font-weight:700">${f.name}</p>`;
    document.getElementById('bfile-zone').classList.add('has');
    toast('تم رفع الملف ✅','ok');
  };r.readAsDataURL(f);
}

// QR
function makeQR(el,text,size){
  el.innerHTML='';
  try{new QRCode(el,{text,width:size,height:size,colorDark:'#0f2744',colorLight:'#fff',correctLevel:QRCode.CorrectLevel.M});}
  catch{el.innerHTML='<span style="font-size:.5rem;color:#999">QR</span>';}
}

// DASHBOARD
function rDash(){
  document.getElementById('ds-stu').textContent=S.length;
  document.getElementById('ds-tea').textContent=T.length;
  document.getElementById('ds-bk').textContent=B.length;
  const paid=S.filter(s=>(s.paid||0)>=(s.fee||0)&&(s.fee||0)>0).length;
  const unpaid=S.filter(s=>(s.paid||0)<(s.fee||0)).length;
  document.getElementById('ds-paid').textContent=paid;
  document.getElementById('ds-unpaid').textContent=unpaid;
  // dist
  const dist=document.getElementById('ds-dist');
  if(!S.length){dist.innerHTML='<div class="empty" style="padding:16px"><div class="ei" style="font-size:1.5rem">📊</div><p>أضف طلاباً</p></div>';} 
  else{
    const cnt={};CL.forEach(c=>cnt[c.id]=0);S.forEach(s=>{if(cnt[s.c]!==undefined)cnt[s.c]++;});
    const mx=Math.max(...Object.values(cnt),1);
    dist.innerHTML=CL.map(c=>`<div class="bar"><div class="bar-l">الصف ${c.n}</div><div class="bar-t"><div class="bar-f" style="width:${cnt[c.id]/mx*100}%"></div></div><div class="bar-n">${cnt[c.id]}</div></div>`).join('');
  }
  // expenses
  const expEl=document.getElementById('ds-exp');
  const last=E.slice(-3).reverse();
  if(!last.length){expEl.innerHTML='<div class="empty" style="padding:16px"><div class="ei" style="font-size:1.5rem">💸</div><p>لا توجد مصاريف</p></div>';return;}
  expEl.innerHTML=last.map(e=>`
    <div class="exp-item">
      <div class="exp-ico" style="background:var(--rl)">${CAT_ICO[e.cat]||'📋'}</div>
      <div class="exp-info"><div class="exp-nm">${e.n}</div><div class="exp-dt">${e.dt||'—'} • ${e.cat}</div></div>
      <div class="exp-amt" style="color:var(--r)">-${fmt(e.amt)}</div>
    </div>`).join('');
}

// STUDENTS
function oAStu(){
  eSid=null;curPhoto=null;
  ['s-n','s-d','s-p','s-no'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('s-i').value=gid('STU');
  document.getElementById('s-c').value='';
  document.getElementById('s-y').value='2024-2025';
  document.getElementById('s-fee').value='';
  document.getElementById('s-paid').value='';
  setPhoto(null);
  document.getElementById('mstu-t').textContent='➕ إضافة طالب جديد';
  om('m-stu');
}
function eStu(id){
  const s=S.find(x=>x.i===id);if(!s)return;eSid=id;
  document.getElementById('s-n').value=s.n;
  document.getElementById('s-i').value=s.i;
  document.getElementById('s-c').value=s.c;
  document.getElementById('s-d').value=s.d||'';
  document.getElementById('s-p').value=s.p||'';
  document.getElementById('s-y').value=s.y||'2024-2025';
  document.getElementById('s-fee').value=s.fee||'';
  document.getElementById('s-paid').value=s.paid||'';
  document.getElementById('s-no').value=s.no||'';
  setPhoto(s.img||null);
  document.getElementById('mstu-t').textContent='✏️ تعديل بيانات الطالب';
  om('m-stu');
}
function saveStu(){
  const n=document.getElementById('s-n').value.trim();
  const c=parseInt(document.getElementById('s-c').value);
  if(!n){toast('يرجى إدخال الاسم','er');return}
  if(!c){toast('يرجى اختيار الصف','er');return}
  const d={n,c,d:document.getElementById('s-d').value,p:document.getElementById('s-p').value,
    y:document.getElementById('s-y').value||'2024-2025',no:document.getElementById('s-no').value,
    fee:+document.getElementById('s-fee').value||0,paid:+document.getElementById('s-paid').value||0,img:curPhoto};
  if(eSid){const i=S.findIndex(x=>x.i===eSid);if(i>-1){S[i]={...S[i],...d};toast('تم التحديث ✅')}}
  else{S.push({i:document.getElementById('s-i').value,...d,at:Date.now()});toast('تمت الإضافة ✅','ok')}
  sv();cm('m-stu');rStu();rDash();
}
function delStu(id){
  if(!confirm('حذف هذا الطالب نهائياً؟'))return;
  S=S.filter(s=>s.i!==id);sv();rStu();rDash();toast('تم الحذف 🗑️');
}
function rStu(){
  const q=document.getElementById('sq').value.toLowerCase();
  const cl=document.getElementById('sf').value;
  const f=S.filter(s=>(!q||(s.n.toLowerCase().includes(q)||s.i.toLowerCase().includes(q)))&&(!cl||s.c==cl));
  document.getElementById('sc2').textContent=f.length;
  if(!f.length){document.getElementById('st').innerHTML=`<div class="empty"><div class="ei">👨‍🎓</div><h3>${!S.length?'لا يوجد طلاب':'لا نتائج'}</h3><p>${!S.length?'اضغط ➕ لإضافة طالب':''}</p></div>`;return}
  document.getElementById('st').innerHTML='<div class="tbl-wrap"><table><thead><tr><th>الطالب</th><th>الصف</th><th>الحالة</th><th>إجراءات</th></tr></thead><tbody>'+
  f.map(s=>{
    const rem=(s.fee||0)-(s.paid||0);
    const st=rem<=0&&(s.fee||0)>0?`<span class="bx bx-g">مكتمل</span>`:rem>0?`<span class="bx bx-r">-${fmt(rem)}</span>`:`<span class="bx bx-b">—</span>`;
    return`<tr>
      <td><div class="td-nm"><div class="av">${s.img?`<img src="${s.img}">`:`${ini(s.n)}`}</div><div><div style="font-weight:700;font-size:.8rem">${s.n}</div><div style="font-size:.65rem;color:var(--tm)">${s.i}</div></div></div></td>
      <td><span class="bx bx-b">الصف ${gcn(s.c)}</span></td>
      <td>${st}</td>
      <td><div style="display:flex;gap:4px">
        <button class="btn bo2 sm" onclick="showCard('${s.i}')">🪪</button>
        <button class="btn bo sm" onclick="eStu('${s.i}')">✏️</button>
        <button class="btn br sm" onclick="delStu('${s.i}')">🗑️</button>
      </div></td>
    </tr>`;}).join('')+'</tbody></table></div>';
}

// ACCOUNTING
function oAPay(id){
  const s=S.find(x=>x.i===id);if(!s)return;curPayId=id;
  const rem=(s.fee||0)-(s.paid||0);
  document.getElementById('pay-info').innerHTML=`
    <div style="font-weight:800;margin-bottom:4px">${s.n}</div>
    <div>القسط السنوي: <b>${fmt(s.fee)} ر.س</b></div>
    <div>المدفوع: <b style="color:var(--g)">${fmt(s.paid)} ر.س</b></div>
    <div>المتبقي: <b style="color:var(--r)">${fmt(rem)} ر.س</b></div>`;
  document.getElementById('pay-amt').value='';
  document.getElementById('pay-note').value='';
  om('m-pay');
}
function savePay(){
  const amt=+document.getElementById('pay-amt').value;
  if(!amt||amt<=0){toast('يرجى إدخال مبلغ صحيح','er');return}
  const i=S.findIndex(x=>x.i===curPayId);if(i<0)return;
  S[i].paid=(S[i].paid||0)+amt;
  sv();cm('m-pay');rAcc();rDash();
  toast(`تم تسجيل ${fmt(amt)} ر.س ✅`,'ok');
}
function rAcc(){
  const q=document.getElementById('aq').value.toLowerCase();
  const cl=document.getElementById('af').value;
  const f=S.filter(s=>(!q||s.n.toLowerCase().includes(q))&&(!cl||s.c==cl));
  const totalFee=f.reduce((a,s)=>a+(s.fee||0),0);
  const totalPaid=f.reduce((a,s)=>a+(s.paid||0),0);
  document.getElementById('acc-paid').textContent=fmt(totalPaid)+' ر.س';
  document.getElementById('acc-unpaid').textContent=fmt(totalFee-totalPaid)+' ر.س';
  const el=document.getElementById('acc-list');
  if(!f.length){el.innerHTML='<div class="empty"><div class="ei">💰</div><h3>لا يوجد طلاب</h3></div>';return}
  el.innerHTML=f.map(s=>{
    const rem=(s.fee||0)-(s.paid||0);
    const pct=(s.fee||0)>0?Math.min(100,Math.round((s.paid||0)/(s.fee||0)*100)):0;
    return`<div class="panel" style="margin-bottom:8px">
      <div class="panel-b" style="padding:10px 12px">
        <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px">
          <div class="td-nm">
            <div class="av">${s.img?`<img src="${s.img}">`:`${ini(s.n)}`}</div>
            <div>
              <div style="font-weight:700;font-size:.83rem">${s.n}</div>
              <span class="bx bx-b" style="margin-top:2px">الصف ${gcn(s.c)}</span>
            </div>
          </div>
          ${rem>0?`<button class="btn bg sm" onclick="oAPay('${s.i}')">💳 دفع</button>`:`<span class="bx bx-g">✅ مكتمل</span>`}
        </div>
        <div style="display:flex;justify-content:space-between;font-size:.72rem;color:var(--tm);margin-bottom:4px">
          <span>القسط: <b style="color:var(--tx)">${fmt(s.fee)} ر.س</b></span>
          <span>المدفوع: <b style="color:var(--g)">${fmt(s.paid)} ر.س</b></span>
          <span>المتبقي: <b style="color:var(--r)">${fmt(rem)} ر.س</b></span>
        </div>
        <div style="background:var(--bg);border-radius:4px;height:10px;overflow:hidden">
          <div style="height:100%;width:${pct}%;background:${rem<=0?'var(--g)':'var(--p)'};border-radius:4px;transition:width .4s"></div>
        </div>
        <div style="font-size:.65rem;color:var(--tm);margin-top:2px;text-align:left">${pct}%</div>
      </div>
    </div>`;}).join('');
}

// BOOKS
function oABk(){
  eBid=null;curBFile=null;curBFileName=null;
  ['b-n','b-s','b-a'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('b-c').value='';document.getElementById('b-cp').value='';
  document.getElementById('bfile-ph').innerHTML='<div style="font-size:1.5rem;margin-bottom:4px">📎</div><p style="font-size:.75rem;color:var(--tm)">اضغط لرفع ملف PDF أو Word</p>';
  document.getElementById('bfile-zone').classList.remove('has');
  document.getElementById('mbk-t').textContent='📚 إضافة كتاب جديد';
  om('m-bk');
}
function eBk(id){
  const b=B.find(x=>x.i===id);if(!b)return;eBid=id;
  document.getElementById('b-n').value=b.n;document.getElementById('b-c').value=b.c;
  document.getElementById('b-s').value=b.s||'';document.getElementById('b-a').value=b.a||'';
  document.getElementById('b-cp').value=b.cp||'';
  curBFile=b.file||null;curBFileName=b.fileName||null;
  if(b.file){document.getElementById('bfile-ph').innerHTML=`<div style="font-size:1.2rem">📄</div><p style="font-size:.72rem;color:var(--g);font-weight:700">${b.fileName||'ملف محفوظ'}</p>`;document.getElementById('bfile-zone').classList.add('has');}
  document.getElementById('mbk-t').textContent='✏️ تعديل الكتاب';
  om('m-bk');
}
function saveBk(){
  const n=document.getElementById('b-n').value.trim();
  const c=parseInt(document.getElementById('b-c').value);
  if(!n){toast('يرجى إدخال اسم الكتاب','er');return}
  if(!c){toast('يرجى اختيار الصف','er');return}
  const d={n,c,s:document.getElementById('b-s').value,a:document.getElementById('b-a').value,cp:document.getElementById('b-cp').value,file:curBFile,fileName:curBFileName};
  if(eBid){const i=B.findIndex(x=>x.i===eBid);if(i>-1){B[i]={...B[i],...d};toast('تم التحديث ✅')}}
  else{B.push({i:gid('BK'),...d,at:Date.now()});toast('تمت الإضافة ✅','ok')}
  sv();cm('m-bk');rBk();
}
function delBk(id){if(!confirm('حذف هذا الكتاب؟'))return;B=B.filter(b=>b.i!==id);sv();rBk();toast('تم الحذف 🗑️');}
function dlBk(id){const b=B.find(x=>x.i===id);if(!b?.file)return;const a=document.createElement('a');a.href=b.file;a.download=b.fileName||b.n;a.click();toast('جاري التحميل 📥','ok');}
const bIco={'رياضيات':'📐','علوم':'🔬','عربي':'✍️','إنجليزي':'🔤','تاريخ':'📜','جغرافيا':'🌍','دين':'📖'};
function getBI(s){for(const[k,v]of Object.entries(bIco))if(s&&s.includes(k))return v;return'📚'}
function rBk(){
  const q=document.getElementById('bq').value.toLowerCase();
  const cl=document.getElementById('bf').value;
  const f=B.filter(b=>(!q||b.n.toLowerCase().includes(q))&&(!cl||b.c==cl));
  const el=document.getElementById('bk-list');
  if(!f.length){el.innerHTML='<div class="empty"><div class="ei">📚</div><h3>'+(B.length?'لا نتائج':'لا توجد كتب')+'</h3></div>';return}
  el.innerHTML=f.map(b=>`
    <div class="wh-card">
      <div class="wh-ico" style="background:var(--pp)">${getBI(b.s)}</div>
      <div class="wh-info">
        <div class="wh-nm">${b.n}</div>
        <div class="wh-det">الصف ${gcn(b.c)}${b.a?' • '+b.a:''}${b.s?' • '+b.s:''}</div>
        ${b.file?`<div style="margin-top:4px"><span class="bx bx-g" style="cursor:pointer" onclick="dlBk('${b.i}')">⬇️ ${b.fileName||'تحميل'}</span></div>`:''}
      </div>
      <div style="display:flex;flex-direction:column;gap:4px;align-items:flex-end">
        ${b.cp?`<div class="wh-qty">${b.cp}<small>نسخة</small></div>`:''}
        <div style="display:flex;gap:4px">
          <button class="btn bo sm" onclick="eBk('${b.i}')">✏️</button>
          <button class="btn br sm" onclick="delBk('${b.i}')">🗑️</button>
        </div>
      </div>
    </div>`).join('');
}

// TEACHERS
function oATea(){
  eTid=null;
  ['t-n','t-s','t-p'].forEach(id=>document.getElementById(id).value='');
  ['t-sal','t-hr','t-hrs'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('mtea-t').textContent='👩‍🏫 إضافة مدرس جديد';
  om('m-tea');
}
function eTea(id){
  const t=T.find(x=>x.i===id);if(!t)return;eTid=id;
  document.getElementById('t-n').value=t.n;document.getElementById('t-s').value=t.s||'';
  document.getElementById('t-p').value=t.p||'';document.getElementById('t-sal').value=t.sal||'';
  document.getElementById('t-hr').value=t.hr||'';document.getElementById('t-hrs').value=t.hrs||'';
  document.getElementById('mtea-t').textContent='✏️ تعديل بيانات المدرس';
  om('m-tea');
}
function saveTea(){
  const n=document.getElementById('t-n').value.trim();
  if(!n){toast('يرجى إدخال الاسم','er');return}
  const d={n,s:document.getElementById('t-s').value,p:document.getElementById('t-p').value,
    sal:+document.getElementById('t-sal').value||0,hr:+document.getElementById('t-hr').value||0,hrs:+document.getElementById('t-hrs').value||0};
  if(eTid){const i=T.findIndex(x=>x.i===eTid);if(i>-1){T[i]={...T[i],...d};toast('تم التحديث ✅')}}
  else{T.push({i:gid('TEA'),...d,at:Date.now()});toast('تمت الإضافة ✅','ok')}
  sv();cm('m-tea');rTea();
}
function delTea(id){if(!confirm('حذف هذا المدرس؟'))return;T=T.filter(t=>t.i!==id);sv();rTea();toast('تم الحذف 🗑️');}
function rTea(){
  const q=document.getElementById('tq').value.toLowerCase();
  const f=T.filter(t=>!q||t.n.toLowerCase().includes(q)||( t.s&&t.s.toLowerCase().includes(q)));
  const el=document.getElementById('tea-list');
  if(!f.length){el.innerHTML='<div class="empty"><div class="ei">👩‍🏫</div><h3>'+(T.length?'لا نتائج':'لا يوجد مدرسون')+'</h3><p>'+(T.length?'':'اضغط ➕ لإضافة مدرس')+'</p></div>';return}
  el.innerHTML=f.map(t=>{
    const hrPay=(t.hr||0)*(t.hrs||0);
    const total=(t.sal||0)+hrPay;
    return`<div class="tea-card">
      <div class="tea-top">
        <div class="tea-av">${ini(t.n)}</div>
        <div style="flex:1">
          <div class="tea-nm">${t.n}</div>
          <div class="tea-sub">${t.s||'—'}${t.p?' • '+t.p:''}</div>
        </div>
        <div style="display:flex;gap:4px">
          <button class="btn bo sm" onclick="eTea('${t.i}')">✏️</button>
          <button class="btn br sm" onclick="delTea('${t.i}')">🗑️</button>
        </div>
      </div>
      <div class="tea-stats">
        <div class="tea-stat"><div class="tsn">${t.hrs||0}</div><div class="tsl">ساعة/شهر</div></div>
        <div class="tea-stat"><div class="tsn" style="font-size:.8rem">${fmt(t.hr||0)}</div><div class="tsl">ر.س/ساعة</div></div>
        <div class="tea-stat" style="background:var(--gl)"><div class="tsn" style="color:var(--g);font-size:.8rem">${fmt(total)}</div><div class="tsl" style="color:var(--g)">الراتب</div></div>
      </div>
    </div>`;}).join('');
}

// WAREHOUSE
function oAWh(){
  eWid=null;
  ['w-n','w-q','w-min','w-p','w-no'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('w-cat').value='قرطاسية';
  document.getElementById('mwh-t').textContent='📦 إضافة مادة للمستودع';
  om('m-wh');
}
function eWh(id){
  const w=W.find(x=>x.i===id);if(!w)return;eWid=id;
  document.getElementById('w-n').value=w.n;document.getElementById('w-cat').value=w.cat||'قرطاسية';
  document.getElementById('w-q').value=w.q;document.getElementById('w-min').value=w.min||5;
  document.getElementById('w-p').value=w.p||'';document.getElementById('w-no').value=w.no||'';
  document.getElementById('mwh-t').textContent='✏️ تعديل المادة';
  om('m-wh');
}
function saveWh(){
  const n=document.getElementById('w-n').value.trim();
  if(!n){toast('يرجى إدخال اسم المادة','er');return}
  const d={n,cat:document.getElementById('w-cat').value,q:+document.getElementById('w-q').value||0,
    min:+document.getElementById('w-min').value||5,p:+document.getElementById('w-p').value||0,no:document.getElementById('w-no').value};
  if(eWid){const i=W.findIndex(x=>x.i===eWid);if(i>-1){W[i]={...W[i],...d};toast('تم التحديث ✅')}}
  else{W.push({i:gid('WH'),...d,at:Date.now()});toast('تمت الإضافة ✅','ok')}
  sv();cm('m-wh');rWh();
}
function delWh(id){if(!confirm('حذف هذه المادة؟'))return;W=W.filter(w=>w.i!==id);sv();rWh();toast('تم الحذف 🗑️');}
function adjWh(id,delta){
  const i=W.findIndex(x=>x.i===id);if(i<0)return;
  W[i].q=Math.max(0,(W[i].q||0)+delta);
  sv();rWh();toast(delta>0?'تمت الإضافة ✅':'تم السحب ✅','ok');
}
function rWh(){
  const q=document.getElementById('wq').value.toLowerCase();
  const f=W.filter(w=>!q||w.n.toLowerCase().includes(q));
  const el=document.getElementById('wh-list');
  if(!f.length){el.innerHTML='<div class="empty"><div class="ei">📦</div><h3>'+(W.length?'لا نتائج':'المستودع فارغ')+'</h3><p>'+(W.length?'':'اضغط ➕ لإضافة مادة')+'</p></div>';return}
  const low=f.filter(w=>w.q<=(w.min||5));
  let html='';
  if(low.length)html+=`<div style="background:var(--rl);border-radius:8px;padding:8px 10px;margin-bottom:8px;font-size:.75rem;font-weight:700;color:var(--r)">⚠️ ${low.length} مادة وصلت للحد الأدنى</div>`;
  html+=f.map(w=>`
    <div class="wh-card ${w.q<=(w.min||5)?'low-stock':''}">
      <div class="wh-ico" style="background:${w.q<=(w.min||5)?'var(--rl)':'var(--ol)'}">${CAT_ICO[w.cat]||'📦'}</div>
      <div class="wh-info">
        <div class="wh-nm">${w.n}</div>
        <div class="wh-det">${w.cat}${w.p?' • '+fmt(w.p)+' ر.س/وحدة':''}${w.no?' • '+w.no:''}</div>
        <div style="display:flex;gap:5px;margin-top:5px">
          <button class="btn bg sm" onclick="adjWh('${w.i}',1)" style="padding:3px 8px">+</button>
          <button class="btn br sm" onclick="adjWh('${w.i}',-1)" style="padding:3px 8px">-</button>
          <button class="btn bo sm" onclick="eWh('${w.i}')">✏️</button>
          <button class="btn br sm" onclick="delWh('${w.i}')">🗑️</button>
        </div>
      </div>
      <div class="wh-qty" style="color:${w.q<=(w.min||5)?'var(--r)':'var(--tx)'}">
        ${w.q}<small>وحدة</small>
      </div>
    </div>`).join('');
  el.innerHTML=html;
}

// EXPENSES
function oAExp(){
  eEid=null;
  ['e-n','e-no'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('e-amt').value='';
  document.getElementById('e-dt').value=today();
  document.getElementById('e-cat').value='فواتير';
  document.getElementById('mexp-t').textContent='💸 إضافة مصروف جديد';
  om('m-exp');
}
function eExp(id){
  const e=E.find(x=>x.i===id);if(!e)return;eEid=id;
  document.getElementById('e-n').value=e.n;document.getElementById('e-cat').value=e.cat||'أخرى';
  document.getElementById('e-amt').value=e.amt;document.getElementById('e-dt').value=e.dt||today();
  document.getElementById('e-no').value=e.no||'';
  document.getElementById('mexp-t').textContent='✏️ تعديل المصروف';
  om('m-exp');
}
function saveExp(){
  const n=document.getElementById('e-n').value.trim();
  const amt=+document.getElementById('e-amt').value;
  if(!n){toast('يرجى إدخال الوصف','er');return}
  if(!amt||amt<=0){toast('يرجى إدخال مبلغ صحيح','er');return}
  const d={n,cat:document.getElementById('e-cat').value,amt,dt:document.getElementById('e-dt').value,no:document.getElementById('e-no').value};
  if(eEid){const i=E.findIndex(x=>x.i===eEid);if(i>-1){E[i]={...E[i],...d};toast('تم التحديث ✅')}}
  else{E.push({i:gid('EXP'),...d,at:Date.now()});toast('تمت الإضافة ✅','ok')}
  sv();cm('m-exp');rExp();rDash();
}
function delExp(id){if(!confirm('حذف هذا المصروف؟'))return;E=E.filter(e=>e.i!==id);sv();rExp();rDash();toast('تم الحذف 🗑️');}
function rExp(){
  const q=document.getElementById('eq').value.toLowerCase();
  const f=E.filter(e=>!q||e.n.toLowerCase().includes(q)||( e.cat&&e.cat.toLowerCase().includes(q)));
  const total=E.reduce((a,e)=>a+(e.amt||0),0);
  const mn=new Date().getMonth();const yr=new Date().getFullYear();
  const mTotal=E.filter(e=>e.dt&&new Date(e.dt).getMonth()===mn&&new Date(e.dt).getFullYear()===yr).reduce((a,e)=>a+(e.amt||0),0);
  document.getElementById('exp-total').textContent=fmt(total)+' ر.س';
  document.getElementById('exp-month').textContent=fmt(mTotal)+' ر.س';
  const el=document.getElementById('exp-list');
  if(!f.length){el.innerHTML='<div class="empty"><div class="ei">💸</div><h3>'+(E.length?'لا نتائج':'لا توجد مصاريف')+'</h3><p>'+(E.length?'':'اضغط ➕ لإضافة مصروف')+'</p></div>';return}
  el.innerHTML=[...f].reverse().map(e=>`
    <div class="exp-item">
      <div class="exp-ico" style="background:var(--rl)">${CAT_ICO[e.cat]||'📋'}</div>
      <div class="exp-info">
        <div class="exp-nm">${e.n}</div>
        <div class="exp-dt">${e.dt||'—'} • ${e.cat}${e.no?' • '+e.no:''}</div>
      </div>
      <div style="text-align:left">
        <div class="exp-amt" style="color:var(--r)">-${fmt(e.amt)}</div>
        <div style="display:flex;gap:4px;margin-top:4px">
          <button class="btn bo sm" onclick="eExp('${e.i}')">✏️</button>
          <button class="btn br sm" onclick="delExp('${e.i}')">🗑️</button>
        </div>
      </div>
    </div>`).join('');
}

// CARDS
function showCard(id){
  const s=S.find(x=>x.i===id);if(!s)return;curCard=s;
  const qrData=JSON.stringify({id:s.i,name:s.n,class:gcn(s.c),year:s.y||'2024-2025'});
  const ph=s.img?`<img src="${s.img}" style="width:100%;height:100%;object-fit:cover">`:`<span>${ini(s.n)}</span>`;
  document.getElementById('m-card-body').innerHTML=`
    <div class="pro-card">
      <div class="pc-stripe"></div>
      <div class="pc-body">
        <div class="pc-photo">${ph}</div>
        <div class="pc-info">
          <div class="pc-sch">✏️ مدرسة القلم للتعليم الأساسي</div>
          <div class="pc-nm">${s.n}</div>
          <div class="pc-badges">
            <span class="pc-badge pc-bg">📚 الصف ${gcn(s.c)}</span>
            <span class="pc-badge pc-bw">📅 ${s.y||'2024-2025'}</span>
          </div>
          <div class="pc-meta">
            ${s.d?`<span>🎂 ${s.d}</span>`:''}
            ${s.p?`<span>📞 ${s.p}</span>`:''}
          </div>
        </div>
        <div class="pc-right">
          <div class="pc-qr" id="qr-prev"></div>
          <div class="pc-ql">امسح للتحقق</div>
        </div>
      </div>
      <div class="pc-ft"><div class="pc-id">${s.i}</div><div class="pc-yr">السنة الدراسية ${s.y||'2024-2025'}</div></div>
    </div>`;
  om('m-card');
  setTimeout(()=>makeQR(document.getElementById('qr-prev'),qrData,54),80);
}
function rCd(){
  const q=document.getElementById('cq').value.toLowerCase();
  const cl=document.getElementById('cf').value;
  const f=S.filter(s=>(!q||s.n.toLowerCase().includes(q))&&(!cl||s.c==cl));
  const el=document.getElementById('cd-list');
  if(!f.length){el.innerHTML='<div class="empty"><div class="ei">🪪</div><h3>'+(S.length?'لا نتائج':'لا يوجد طلاب')+'</h3></div>';return}
  el.innerHTML=f.map(s=>`
    <div class="wh-card" onclick="showCard('${s.i}')" style="cursor:pointer">
      <div class="av" style="width:40px;height:40px">${s.img?`<img src="${s.img}">`:`${ini(s.n)}`}</div>
      <div class="wh-info">
        <div class="wh-nm">${s.n}</div>
        <div class="wh-det">الصف ${gcn(s.c)} • ${s.y||'2024-2025'}</div>
        <div style="font-size:.65rem;color:var(--tm);margin-top:2px">${s.i}</div>
      </div>
      <div style="font-size:.7rem;color:var(--tm)">QR ›</div>
    </div>`).join('');
}
function mkPrtCard(s){
  const ph=s.img?`<img src="${s.img}">`:`<span>${ini(s.n)}</span>`;
  const cid='c'+s.i.replace(/[^a-z0-9]/gi,'');
  return`<div class="prc" id="${cid}">
    <div class="prc-stripe"></div>
    <div class="prc-body">
      <div class="prc-ph">${ph}</div>
      <div class="prc-info">
        <div class="prc-sch">✏️ مدرسة القلم للتعليم الأساسي</div>
        <div class="prc-nm">${s.n}</div>
        <div class="prc-badges"><span class="prc-badge prc-bg">📚 الصف ${gcn(s.c)}</span><span class="prc-badge prc-bw">${s.y||'2024-2025'}</span></div>
        ${s.d?`<div style="font-size:4pt;opacity:.45;margin-top:.8mm">🎂 ${s.d}</div>`:''}
      </div>
      <div class="prc-right">
        <div class="prc-qr" id="qr-${cid}"></div>
        <div class="prc-ql">امسح للتحقق</div>
      </div>
    </div>
    <div class="prc-ft"><div class="prc-id">${s.i}</div><div class="prc-yr">${s.y||'2024-2025'}</div></div>
  </div>`;
}
function prtCard(){
  if(!curCard)return;
  document.getElementById('prt').innerHTML=mkPrtCard(curCard);
  setTimeout(()=>{
    const cid='c'+curCard.i.replace(/[^a-z0-9]/gi,'');
    const qrEl=document.getElementById('qr-'+cid);
    if(qrEl)makeQR(qrEl,JSON.stringify({id:curCard.i,name:curCard.n,class:gcn(curCard.c),year:curCard.y||'2024-2025'}),44);
    setTimeout(()=>{P++;lset('ql_p',P);window.print();toast('جاري الطباعة 🖨️','ok');},300);
  },100);
}
function prtAll(){
  if(!S.length){toast('لا يوجد طلاب','er');return}
  document.getElementById('prt').innerHTML=S.map(s=>mkPrtCard(s)).join('');
  setTimeout(()=>{
    S.forEach(s=>{
      const cid='c'+s.i.replace(/[^a-z0-9]/gi,'');
      const qrEl=document.getElementById('qr-'+cid);
      if(qrEl)makeQR(qrEl,JSON.stringify({id:s.i,name:s.n,class:gcn(s.c),year:s.y||'2024-2025'}),44);
    });
    setTimeout(()=>{P+=S.length;lset('ql_p',P);window.print();toast('طباعة الكل 🖨️','ok');},400);
  },100);
}

// INIT
pSel();
go('dash');
document.getElementById('fab').style.display='none';
</script>
</body>
</html>
