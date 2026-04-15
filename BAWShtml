<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BA Workshop Whiteboard — Change &amp; Transformation Toolkit</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Playfair+Display:wght@400;600&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #eae7e0;
  --surface: #ffffff;
  --ink: #1c1917;
  --ink-mid: #57534e;
  --ink-light: #8c8580;
  --accent: #b45309;
  --accent-hover: #92400e;
  --accent-bg: #fef3c7;
  --blue: #1d4ed8;
  --green: #15803d;
  --purple: #7e22ce;
  --amber: #b45309;
  --red: #b91c1c;
  --teal: #0f766e;
  --rose: #be123c;
  --slate: #475569;
  --sticky-yellow: #fef9c3;
  --sticky-pink: #fce7f3;
  --sticky-blue: #dbeafe;
  --sticky-green: #dcfce7;
  --sticky-orange: #ffedd5;
  --sticky-purple: #f3e8ff;
  --border: #d6d3d1;
  --border-light: #e7e5e4;
  --shadow: 0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04);
  --shadow-lg: 0 4px 24px rgba(0,0,0,0.08), 0 0 0 1px rgba(0,0,0,0.04);
  --radius: 10px;
  --radius-sm: 6px;
  --sidebar-w: 240px;
}

* { margin:0; padding:0; box-sizing:border-box; }
body { font-family:'DM Sans',sans-serif; background:var(--bg); color:var(--ink); height:100vh; overflow:hidden; }

/* ── TOP BAR ── */
.topbar {
  position:fixed; top:0; left:0; right:0; height:50px;
  background:var(--ink); color:#fff;
  display:flex; align-items:center; padding:0 20px; z-index:200;
  gap:14px;
}
.topbar-logo { font-family:'Playfair Display',serif; font-size:18px; font-weight:600; letter-spacing:-0.3px; }
.topbar-sep { width:1px; height:24px; background:rgba(255,255,255,0.15); }
.topbar-title { font-size:13px; color:rgba(255,255,255,0.7); }
.topbar-right { margin-left:auto; display:flex; gap:8px; }
.topbar-btn {
  padding:5px 14px; border-radius:6px; font-size:12px; font-weight:600;
  cursor:pointer; border:1px solid rgba(255,255,255,0.2); background:transparent;
  color:rgba(255,255,255,0.85); transition:all 0.15s;
}
.topbar-btn:hover { background:rgba(255,255,255,0.1); color:#fff; }
.topbar-btn.primary { background:var(--accent); border-color:var(--accent); color:#fff; }
.topbar-btn.primary:hover { background:var(--accent-hover); }

/* ── SIDEBAR ── */
.sidebar {
  position:fixed; top:50px; left:0; bottom:0; width:var(--sidebar-w);
  background:var(--surface); border-right:1px solid var(--border);
  overflow-y:auto; z-index:100; padding:12px 0;
}
.sidebar::-webkit-scrollbar { width:4px; }
.sidebar::-webkit-scrollbar-thumb { background:var(--border); border-radius:4px; }

.side-category {
  padding:6px 16px; font-size:10px; font-weight:700; text-transform:uppercase;
  letter-spacing:1.4px; color:var(--ink-light); margin-top:10px;
}
.side-category:first-child { margin-top:0; }

.side-item {
  display:flex; align-items:center; gap:8px;
  padding:7px 16px; font-size:13px; font-weight:500; color:var(--ink-mid);
  cursor:pointer; transition:all 0.12s; border-left:3px solid transparent;
  user-select:none;
}
.side-item:hover { background:#f5f3f0; color:var(--ink); }
.side-item.active {
  background:var(--accent-bg); color:var(--accent); border-left-color:var(--accent);
  font-weight:600;
}
.side-dot {
  width:7px; height:7px; border-radius:50%; flex-shrink:0;
}
.side-count {
  margin-left:auto; font-size:10px; background:var(--border-light);
  padding:1px 6px; border-radius:10px; color:var(--ink-light); font-weight:600;
}

/* ── CANVAS ── */
.canvas {
  position:fixed; top:50px; left:var(--sidebar-w); right:0; bottom:0;
  overflow:auto; padding:28px;
  background:
    radial-gradient(circle at 1px 1px, #cec9c1 0.8px, transparent 0) 0 0 / 20px 20px;
}

/* ── BOARD ── */
.board {
  background:var(--surface); border-radius:var(--radius);
  box-shadow:var(--shadow-lg); max-width:1140px; margin:0 auto;
  animation:boardIn 0.3s ease-out;
}
@keyframes boardIn { from{opacity:0;transform:translateY(12px) scale(0.99)} to{opacity:1;transform:none} }

.board-head {
  padding:22px 26px 14px; border-bottom:1px solid var(--border-light);
}
.board-head h2 {
  font-family:'Playfair Display',serif; font-size:26px; font-weight:600; letter-spacing:-0.5px;
}
.board-head p { font-size:12px; color:var(--ink-light); margin-top:3px; line-height:1.5; }
.board-head .board-tag {
  display:inline-block; font-size:10px; font-weight:700; text-transform:uppercase;
  letter-spacing:1px; padding:2px 8px; border-radius:4px; margin-top:6px;
}

/* ── GRID LAYOUTS ── */
.g { display:grid; min-height:440px; }
.g-2x2 { grid-template-columns:1fr 1fr; grid-template-rows:1fr 1fr; }
.g-2col { grid-template-columns:1fr 1fr; }
.g-3col { grid-template-columns:1fr 1fr 1fr; }
.g-4col { grid-template-columns:1fr 1fr 1fr 1fr; }
.g-5col { grid-template-columns:1fr 1fr 1fr 1fr 1fr; }
.g-bmc { grid-template-columns:1fr 1fr 1fr 1fr 1fr; grid-template-rows:auto auto; }
.g-forces { grid-template-columns:1fr 1fr 1fr; grid-template-rows:auto auto auto; }
.g-linear { grid-template-columns:1fr; }
.g-whys { grid-template-columns:1fr; gap:0; }
.g-isnt { grid-template-columns:1fr 1fr; }

/* ── CELL ── */
.cell {
  border:0.5px solid var(--border-light); padding:14px;
  display:flex; flex-direction:column; position:relative; min-height:160px;
  transition:background 0.12s;
}
.cell:hover { background:#fdfcfa; }
.cell.empty-cell { pointer-events:none; background:transparent; border:none; min-height:0; }

.cell-lbl {
  font-size:10px; font-weight:700; text-transform:uppercase;
  letter-spacing:1.1px; margin-bottom:4px;
  display:flex; align-items:center; gap:5px;
}
.cell-lbl .cdot { width:7px; height:7px; border-radius:50%; }
.cell-hint { font-size:11px; color:var(--ink-light); margin-bottom:8px; line-height:1.4; font-style:italic; }

.notes { flex:1; display:flex; flex-wrap:wrap; gap:5px; align-content:flex-start; }

.sticky {
  padding:6px 9px; border-radius:4px; font-size:11.5px; line-height:1.35;
  box-shadow:1px 1px 3px rgba(0,0,0,0.06); position:relative;
  max-width:180px; word-break:break-word; cursor:default;
  animation:pop 0.18s ease-out;
}
@keyframes pop { from{opacity:0;transform:scale(0.85)} to{opacity:1;transform:none} }

.sticky .rx {
  position:absolute; top:-4px; right:-4px; width:15px; height:15px;
  border-radius:50%; background:var(--red); color:#fff; font-size:9px;
  display:none; align-items:center; justify-content:center; cursor:pointer;
  border:none; line-height:1;
}
.sticky:hover .rx { display:flex; }

.add-btn {
  width:100%; margin-top:auto; padding:5px; border:1.5px dashed var(--border);
  border-radius:var(--radius-sm); background:transparent; color:var(--ink-light);
  font-size:11px; font-weight:500; cursor:pointer; transition:all 0.15s;
  display:flex; align-items:center; justify-content:center; gap:4px;
}
.add-btn:hover { border-color:var(--accent); color:var(--accent); background:#fef7f0; }
.add-btn svg { width:13px; height:13px; }

/* ── LINEAR STEP CELLS ── */
.step-cell {
  border:0.5px solid var(--border-light); padding:14px;
  display:flex; gap:14px; min-height:120px; transition:background 0.12s;
}
.step-cell:hover { background:#fdfcfa; }
.step-num {
  width:32px; height:32px; border-radius:50%;
  display:flex; align-items:center; justify-content:center;
  font-size:13px; font-weight:700; color:#fff; flex-shrink:0;
}
.step-body { flex:1; display:flex; flex-direction:column; }

/* ── WHYS ROW ── */
.why-row {
  border:0.5px solid var(--border-light); padding:14px;
  display:flex; gap:12px; align-items:flex-start; min-height:90px;
  transition:background 0.12s;
}
.why-row:hover { background:#fdfcfa; }
.why-arrow {
  font-size:18px; color:var(--accent); flex-shrink:0; margin-top:2px; font-weight:700;
}
.why-body { flex:1; display:flex; flex-direction:column; }

/* ── MODAL ── */
.overlay {
  position:fixed; inset:0; background:rgba(0,0,0,0.3); z-index:300;
  display:flex; align-items:center; justify-content:center;
  animation:fadeIn 0.12s;
}
@keyframes fadeIn { from{opacity:0} to{opacity:1} }

.modal {
  background:var(--surface); border-radius:var(--radius); padding:22px;
  width:380px; max-width:90vw; box-shadow:0 12px 40px rgba(0,0,0,0.18);
  animation:modalIn 0.18s ease-out;
}
@keyframes modalIn { from{opacity:0;transform:scale(0.96) translateY(6px)} to{opacity:1;transform:none} }

.modal h3 { font-family:'Playfair Display',serif; font-size:18px; margin-bottom:3px; }
.modal .msub { font-size:11px; color:var(--ink-light); margin-bottom:12px; }
.modal textarea {
  width:100%; border:1.5px solid var(--border); border-radius:var(--radius-sm);
  padding:9px 11px; font-family:'DM Sans',sans-serif; font-size:13px;
  resize:vertical; min-height:64px; outline:none; transition:border 0.15s;
}
.modal textarea:focus { border-color:var(--accent); }
.cpick { display:flex; gap:5px; margin:10px 0; }
.cswatch {
  width:24px; height:24px; border-radius:50%; cursor:pointer;
  border:2.5px solid transparent; transition:all 0.12s;
}
.cswatch:hover { transform:scale(1.12); }
.cswatch.on { border-color:var(--ink); transform:scale(1.12); }
.mactions { display:flex; justify-content:flex-end; gap:8px; margin-top:12px; }
.mactions button {
  padding:7px 16px; border-radius:6px; font-size:12px; font-weight:600;
  cursor:pointer; border:1.5px solid var(--border); background:var(--surface);
  color:var(--ink); transition:all 0.12s;
}
.mactions button.pr { background:var(--accent); border-color:var(--accent); color:#fff; }
.mactions button.pr:hover { background:var(--accent-hover); }

/* ── RESPONSIVE ── */
@media(max-width:900px) {
  .sidebar { width:180px; }
  :root { --sidebar-w:180px; }
}
@media(max-width:700px) {
  .sidebar { display:none; }
  :root { --sidebar-w:0px; }
  .topbar-title { display:none; }
  .mobile-menu-btn { display:flex !important; }
  .g-2x2,.g-2col,.g-3col,.g-4col,.g-5col,.g-bmc,.g-forces,.g-isnt {
    grid-template-columns:1fr !important;
  }
  .g-bmc>*,.g-forces>* { grid-column:auto!important; grid-row:auto!important; }
}

.mobile-menu-btn {
  display:none; padding:5px 10px; border-radius:6px; font-size:12px;
  font-weight:600; cursor:pointer; border:1px solid rgba(255,255,255,0.2);
  background:transparent; color:#fff; align-items:center; gap:4px;
}
</style>
</head>
<body>

<div class="topbar">
  <span class="topbar-logo">BA Workshop</span>
  <div class="topbar-sep"></div>
  <span class="topbar-title">Change &amp; Transformation Toolkit</span>
  <button class="mobile-menu-btn" onclick="toggleSidebar()">&#9776; Tools</button>
  <div class="topbar-right">
    <button class="topbar-btn" onclick="clearBoard()">Clear Board</button>
    <button class="topbar-btn primary" onclick="exportAll()">Export All Notes</button>
  </div>
</div>

<div class="sidebar" id="sidebar"></div>
<div class="canvas" id="canvas"></div>

<div class="overlay" id="overlay" style="display:none" onclick="closeModal(event)">
  <div class="modal" onclick="event.stopPropagation()">
    <h3 id="mTitle">Add Note</h3>
    <p class="msub" id="mSub"></p>
    <textarea id="mInput" placeholder="Type your idea here…"></textarea>
    <div class="cpick" id="cpick"></div>
    <div class="mactions">
      <button onclick="closeModal()">Cancel</button>
      <button class="pr" onclick="submitNote()">Add</button>
    </div>
  </div>
</div>

<script>
const COLORS = [
  {n:'Yellow',v:'#fef9c3'},{n:'Pink',v:'#fce7f3'},{n:'Blue',v:'#dbeafe'},
  {n:'Green',v:'#dcfce7'},{n:'Orange',v:'#ffedd5'},{n:'Purple',v:'#f3e8ff'}
];

const CAT = {
  'Strategic Analysis': '#1d4ed8',
  'Change & Transformation': '#b45309',
  'Problem Solving': '#b91c1c',
  'Planning & Delivery': '#15803d',
  'Benefits & Value': '#7e22ce',
  'Stakeholders & People': '#0f766e',
  'Design & Innovation': '#be123c',
};

const F = [
  // ─── STRATEGIC ANALYSIS ───
  {
    id:'swot', name:'SWOT Analysis', cat:'Strategic Analysis',
    desc:'Evaluate internal strengths & weaknesses against external opportunities & threats.',
    layout:'g g-2x2',
    cells:[
      {id:'str',label:'Strengths',color:'#15803d',hint:'Internal capabilities & advantages'},
      {id:'wk',label:'Weaknesses',color:'#b91c1c',hint:'Internal limitations & gaps'},
      {id:'opp',label:'Opportunities',color:'#1d4ed8',hint:'External factors you can exploit'},
      {id:'thr',label:'Threats',color:'#b45309',hint:'External risks & challenges'},
    ]
  },
  {
    id:'pest', name:'PESTLE Analysis', cat:'Strategic Analysis',
    desc:'Scan the macro-environment across six dimensions.',
    layout:'g g-3col',
    cells:[
      {id:'pol',label:'Political',color:'#1d4ed8',hint:'Government policy, regulation, trade barriers, tax'},
      {id:'eco',label:'Economic',color:'#15803d',hint:'Growth rates, inflation, exchange rates, employment'},
      {id:'soc',label:'Social',color:'#7e22ce',hint:'Demographics, culture, lifestyle trends, attitudes'},
      {id:'tech',label:'Technological',color:'#b45309',hint:'Innovation, automation, R&D, digital disruption'},
      {id:'leg',label:'Legal',color:'#b91c1c',hint:'Employment law, health & safety, consumer rights'},
      {id:'env',label:'Environmental',color:'#0f766e',hint:'Climate, sustainability, carbon, waste, ESG'},
    ]
  },
  {
    id:'porter', name:"Porter's Five Forces", cat:'Strategic Analysis',
    desc:'Analyse the competitive intensity and attractiveness of a market.',
    layout:'g g-forces',
    cells:[
      {id:'pe1',label:'',color:'',hint:'',style:'grid-column:1;grid-row:1;',empty:true},
      {id:'newent',label:'Threat of New Entrants',color:'#1d4ed8',hint:'Barriers to entry, capital requirements, regulation',style:'grid-column:2;grid-row:1;'},
      {id:'pe2',label:'',color:'',hint:'',style:'grid-column:3;grid-row:1;',empty:true},
      {id:'suppl',label:'Supplier Power',color:'#7e22ce',hint:'Concentration, switching costs, uniqueness',style:'grid-column:1;grid-row:2;'},
      {id:'rival',label:'Competitive Rivalry',color:'#b91c1c',hint:'Number of competitors, growth rate, differentiation',style:'grid-column:2;grid-row:2;'},
      {id:'buyer',label:'Buyer Power',color:'#15803d',hint:'Concentration, price sensitivity, alternatives',style:'grid-column:3;grid-row:2;'},
      {id:'pe3',label:'',color:'',hint:'',style:'grid-column:1;grid-row:3;',empty:true},
      {id:'subs',label:'Threat of Substitutes',color:'#b45309',hint:'Availability, switching costs, buyer propensity',style:'grid-column:2;grid-row:3;'},
      {id:'pe4',label:'',color:'',hint:'',style:'grid-column:3;grid-row:3;',empty:true},
    ]
  },
  {
    id:'bmc', name:'Business Model Canvas', cat:'Strategic Analysis',
    desc:'Map your business model across 9 building blocks (Osterwalder).',
    layout:'g g-bmc',
    cells:[
      {id:'bpartners',label:'Key Partners',color:'#7e22ce',hint:'Key partners & suppliers',style:'grid-row:1/3;grid-column:1;'},
      {id:'bactivities',label:'Key Activities',color:'#1d4ed8',hint:'Critical activities for value delivery',style:'grid-column:2;'},
      {id:'bvalue',label:'Value Propositions',color:'#b45309',hint:'Value delivered to the customer',style:'grid-row:1/3;grid-column:3;'},
      {id:'brelations',label:'Customer Relationships',color:'#15803d',hint:'Relationship types per segment',style:'grid-column:4;'},
      {id:'bsegments',label:'Customer Segments',color:'#0f766e',hint:'Who are you creating value for?',style:'grid-row:1/3;grid-column:5;'},
      {id:'bresources',label:'Key Resources',color:'#1d4ed8',hint:'Assets required for value delivery',style:'grid-column:2;'},
      {id:'bchannels',label:'Channels',color:'#15803d',hint:'How you reach & deliver to customers',style:'grid-column:4;'},
      {id:'bcosts',label:'Cost Structure',color:'#b91c1c',hint:'Biggest costs in this model',style:'grid-column:1/4;'},
      {id:'brevenue',label:'Revenue Streams',color:'#b45309',hint:'How and for what customers pay',style:'grid-column:4/6;'},
    ]
  },
  {
    id:'vpc', name:'Value Proposition Canvas', cat:'Strategic Analysis',
    desc:'Align your offering to what the customer truly needs (Osterwalder).',
    layout:'g g-2col',
    cells:[
      {id:'vprod',label:'Products & Services',color:'#1d4ed8',hint:'What you offer'},
      {id:'vjobs',label:'Customer Jobs',color:'#0f766e',hint:'Tasks customers are trying to complete'},
      {id:'vgainc',label:'Gain Creators',color:'#15803d',hint:'How you create gains'},
      {id:'vgains',label:'Gains',color:'#15803d',hint:'Outcomes & benefits customers want'},
      {id:'vpainr',label:'Pain Relievers',color:'#b45309',hint:'How you alleviate pains'},
      {id:'vpains',label:'Pains',color:'#b91c1c',hint:'Frustrations & risks customers face'},
    ]
  },

  // ─── CHANGE & TRANSFORMATION ───
  {
    id:'adkar', name:'ADKAR Model', cat:'Change & Transformation',
    desc:'Prosci\'s model for individual change: Awareness → Desire → Knowledge → Ability → Reinforcement.',
    layout:'g g-5col',
    cells:[
      {id:'awareness',label:'Awareness',color:'#1d4ed8',hint:'Why is the change needed?'},
      {id:'desire',label:'Desire',color:'#7e22ce',hint:'Willingness to support & participate'},
      {id:'knowledge',label:'Knowledge',color:'#15803d',hint:'How to change — skills & info needed'},
      {id:'ability',label:'Ability',color:'#b45309',hint:'Demonstrated capability to implement'},
      {id:'reinforcement',label:'Reinforcement',color:'#0f766e',hint:'Sustaining the change long-term'},
    ]
  },
  {
    id:'forcefield', name:'Force Field Analysis', cat:'Change & Transformation',
    desc:'Lewin\'s model: weigh driving forces against restraining forces to assess change readiness.',
    layout:'g g-2col',
    cells:[
      {id:'driving',label:'Driving Forces',color:'#15803d',hint:'Factors pushing towards the desired change'},
      {id:'restraining',label:'Restraining Forces',color:'#b91c1c',hint:'Factors resisting or blocking the change'},
    ]
  },
  {
    id:'asis', name:'As-Is / To-Be / Gap', cat:'Change & Transformation',
    desc:'Map current state, desired future state, and identify the gaps.',
    layout:'g g-3col',
    cells:[
      {id:'asis',label:'As-Is (Current State)',color:'#b91c1c',hint:'How things work today — processes, issues, pain points'},
      {id:'gap',label:'Gap Analysis',color:'#b45309',hint:'What needs to change? Barriers, missing capabilities'},
      {id:'tobe',label:'To-Be (Future State)',color:'#15803d',hint:'Desired future — processes, outcomes, experience'},
    ]
  },
  {
    id:'changeimp', name:'Change Impact Assessment', cat:'Change & Transformation',
    desc:'Assess who is impacted by the change, how, and what support they need.',
    layout:'g g-4col',
    cells:[
      {id:'who',label:'Who Is Impacted',color:'#1d4ed8',hint:'Teams, roles, individuals, customers'},
      {id:'howchange',label:'How They Are Impacted',color:'#b45309',hint:'What changes for them — process, tools, roles'},
      {id:'severity',label:'Impact Severity',color:'#b91c1c',hint:'High / Medium / Low — degree of disruption'},
      {id:'support',label:'Support Needed',color:'#15803d',hint:'Training, comms, coaching, new tools'},
    ]
  },

  // ─── PROBLEM SOLVING ───
  {
    id:'fishbone', name:'Root Cause (Fishbone / Ishikawa)', cat:'Problem Solving',
    desc:'Categorise potential root causes across six dimensions.',
    layout:'g g-3col',
    cells:[
      {id:'people',label:'People',color:'#1d4ed8',hint:'Skills, knowledge, staffing, culture'},
      {id:'process',label:'Process',color:'#15803d',hint:'Steps, procedures, workflows, policies'},
      {id:'technology',label:'Technology',color:'#7e22ce',hint:'Systems, tools, software, hardware'},
      {id:'environment',label:'Environment',color:'#0f766e',hint:'Physical space, market conditions, culture'},
      {id:'management',label:'Management',color:'#b45309',hint:'Leadership, governance, decision-making'},
      {id:'materials',label:'Materials / Data',color:'#b91c1c',hint:'Inputs, data quality, supplies, information'},
    ]
  },
  {
    id:'fivewhys', name:'5 Whys', cat:'Problem Solving',
    desc:'Drill down iteratively to find the root cause of a problem.',
    type:'whys',
    cells:[
      {id:'problem',label:'Problem Statement',color:'#b91c1c',hint:'Clearly define the problem you are investigating'},
      {id:'why1',label:'Why? (1st)',color:'#b45309',hint:'Why does this problem occur?'},
      {id:'why2',label:'Why? (2nd)',color:'#b45309',hint:'Why does the above cause happen?'},
      {id:'why3',label:'Why? (3rd)',color:'#b45309',hint:'Keep asking why…'},
      {id:'why4',label:'Why? (4th)',color:'#b45309',hint:'Dig deeper…'},
      {id:'why5',label:'Why? (5th)',color:'#b45309',hint:'Nearly there…'},
      {id:'rootcause',label:'Root Cause',color:'#15803d',hint:'The underlying cause to address'},
    ]
  },
  {
    id:'isnot', name:'Is / Is Not Analysis', cat:'Problem Solving',
    desc:'Sharpen problem definition by contrasting what IS happening versus what IS NOT.',
    layout:'g g-isnt',
    cells:[
      {id:'whatIs',label:'What IS the problem?',color:'#b91c1c',hint:'What is actually happening / affected?'},
      {id:'whatNot',label:'What IS NOT?',color:'#15803d',hint:'What is not happening / not affected?'},
      {id:'whereIs',label:'Where IS it occurring?',color:'#b91c1c',hint:'Locations, systems, areas affected'},
      {id:'whereNot',label:'Where IS it NOT?',color:'#15803d',hint:'Where is it not a problem?'},
      {id:'whenIs',label:'When DOES it occur?',color:'#b91c1c',hint:'Timing, frequency, patterns'},
      {id:'whenNot',label:'When DOES it NOT?',color:'#15803d',hint:'When is the problem absent?'},
      {id:'extentIs',label:'What is the EXTENT?',color:'#b91c1c',hint:'Scale, volume, severity'},
      {id:'extentNot',label:'What is NOT the extent?',color:'#15803d',hint:'What scope is not affected?'},
    ]
  },

  // ─── PLANNING & DELIVERY ───
  {
    id:'edipec', name:'EDIPEC', cat:'Planning & Delivery',
    desc:'Structured investigation lifecycle: Explore → Define → Investigate → Plan → Execute → Close.',
    type:'steps',
    cells:[
      {id:'explore',label:'Explore',color:'#1d4ed8',hint:'Understand context, scope boundaries, stakeholders & initial concerns'},
      {id:'define',label:'Define',color:'#7e22ce',hint:'Define the problem/opportunity, objectives, success criteria & terms of reference'},
      {id:'investigate',label:'Investigate',color:'#b45309',hint:'Analyse the current situation, gather evidence, model options'},
      {id:'plan',label:'Plan',color:'#15803d',hint:'Plan the approach, deliverables, timescales & resources'},
      {id:'execute',label:'Execute',color:'#b91c1c',hint:'Implement the solution, manage change, deliver outputs'},
      {id:'close',label:'Close',color:'#0f766e',hint:'Review outcomes, capture lessons, hand over & confirm benefits'},
    ]
  },
  {
    id:'moscow', name:'MoSCoW Prioritisation', cat:'Planning & Delivery',
    desc:'Prioritise requirements into Must, Should, Could and Won\'t.',
    layout:'g g-4col',
    cells:[
      {id:'must',label:'Must Have',color:'#b91c1c',hint:'Non-negotiable — the solution fails without these'},
      {id:'should',label:'Should Have',color:'#b45309',hint:'Important but not vital — workaround exists'},
      {id:'could',label:'Could Have',color:'#1d4ed8',hint:'Desirable — include if time/budget allows'},
      {id:'wont',label:'Won\'t Have (this time)',color:'#475569',hint:'Agreed out of scope for now'},
    ]
  },
  {
    id:'raci', name:'RACI Matrix', cat:'Planning & Delivery',
    desc:'Clarify who is Responsible, Accountable, Consulted & Informed for each activity.',
    layout:'g g-4col',
    cells:[
      {id:'responsible',label:'Responsible',color:'#1d4ed8',hint:'Who does the work?'},
      {id:'accountable',label:'Accountable',color:'#b91c1c',hint:'Who is the decision-maker / owner?'},
      {id:'consulted',label:'Consulted',color:'#b45309',hint:'Who provides input or expertise?'},
      {id:'informed',label:'Informed',color:'#15803d',hint:'Who needs to be kept in the loop?'},
    ]
  },
  {
    id:'sipoc', name:'SIPOC', cat:'Planning & Delivery',
    desc:'High-level process map: Suppliers → Inputs → Process → Outputs → Customers.',
    layout:'g g-5col',
    cells:[
      {id:'suppliers',label:'Suppliers',color:'#7e22ce',hint:'Who provides inputs?'},
      {id:'inputs',label:'Inputs',color:'#1d4ed8',hint:'What materials, data or resources are needed?'},
      {id:'process',label:'Process',color:'#b45309',hint:'Key process steps at a high level'},
      {id:'outputs',label:'Outputs',color:'#15803d',hint:'What is produced or delivered?'},
      {id:'customers',label:'Customers',color:'#0f766e',hint:'Who receives the outputs?'},
    ]
  },
  {
    id:'impeffort', name:'Impact / Effort Matrix', cat:'Planning & Delivery',
    desc:'Prioritise initiatives by plotting impact against effort required.',
    layout:'g g-2x2',
    cells:[
      {id:'quickwins',label:'Quick Wins',color:'#15803d',hint:'High impact, low effort — do these first!'},
      {id:'major',label:'Major Projects',color:'#1d4ed8',hint:'High impact, high effort — plan & resource carefully'},
      {id:'fillins',label:'Fill-Ins',color:'#b45309',hint:'Low impact, low effort — do if capacity allows'},
      {id:'avoid',label:'Thankless Tasks',color:'#b91c1c',hint:'Low impact, high effort — deprioritise or drop'},
    ]
  },

  // ─── BENEFITS & VALUE ───
  {
    id:'bam', name:'Benefits Analysis Model (BAM)', cat:'Benefits & Value',
    desc:'Link objectives to benefits, dis-benefits, enablers and business changes.',
    layout:'g g-5col',
    cells:[
      {id:'objectives',label:'Objectives',color:'#1d4ed8',hint:'Strategic or project objectives being targeted'},
      {id:'benefits',label:'Benefits',color:'#15803d',hint:'Measurable improvements resulting from the change'},
      {id:'disbenefits',label:'Dis-benefits',color:'#b91c1c',hint:'Negative consequences that must be managed'},
      {id:'enablers',label:'Enablers',color:'#7e22ce',hint:'Outputs or capabilities that enable benefits'},
      {id:'bizchange',label:'Business Changes',color:'#b45309',hint:'Changes to processes, people, or org needed'},
    ]
  },
  {
    id:'benprofile', name:'Benefits Profile', cat:'Benefits & Value',
    desc:'Document individual benefit details — ownership, measurement, dependencies.',
    layout:'g g-3col',
    cells:[
      {id:'bendesc',label:'Benefit Description',color:'#15803d',hint:'What is the benefit? How does it help?'},
      {id:'benmeasure',label:'Measures & KPIs',color:'#1d4ed8',hint:'How will you measure it? Baseline → Target'},
      {id:'benowner',label:'Benefit Owner',color:'#b45309',hint:'Who is accountable for realisation?'},
      {id:'bendeps',label:'Dependencies',color:'#b91c1c',hint:'What must happen for this benefit to be realised?'},
      {id:'bentimeline',label:'Realisation Timeline',color:'#7e22ce',hint:'When will the benefit start to be realised?'},
      {id:'benrisks',label:'Risks to Realisation',color:'#b91c1c',hint:'What could prevent or reduce this benefit?'},
    ]
  },

  // ─── STAKEHOLDERS & PEOPLE ───
  {
    id:'stakemap', name:'Stakeholder Map (Power/Interest)', cat:'Stakeholders & People',
    desc:'Map stakeholders by power and interest to guide your engagement strategy.',
    layout:'g g-2x2',
    cells:[
      {id:'manage',label:'Manage Closely',color:'#b91c1c',hint:'High power, high interest — key players'},
      {id:'satisfy',label:'Keep Satisfied',color:'#b45309',hint:'High power, low interest — keep onside'},
      {id:'inform',label:'Keep Informed',color:'#1d4ed8',hint:'Low power, high interest — show consideration'},
      {id:'monitor',label:'Monitor',color:'#15803d',hint:'Low power, low interest — minimum effort'},
    ]
  },
  {
    id:'stakeengage', name:'Stakeholder Engagement Plan', cat:'Stakeholders & People',
    desc:'Plan how to engage each stakeholder group — current vs. desired disposition.',
    layout:'g g-4col',
    cells:[
      {id:'sname',label:'Stakeholder / Group',color:'#0f766e',hint:'Who are they?'},
      {id:'scurrent',label:'Current Position',color:'#b91c1c',hint:'Unaware, resistant, neutral, supportive, champion?'},
      {id:'sdesired',label:'Desired Position',color:'#15803d',hint:'Where do you need them to be?'},
      {id:'sactions',label:'Engagement Actions',color:'#1d4ed8',hint:'What will you do to move them?'},
    ]
  },

  // ─── DESIGN & INNOVATION ───
  {
    id:'dthinking', name:'Design Thinking', cat:'Design & Innovation',
    desc:'Human-centred innovation: Empathise → Define → Ideate → Prototype → Test.',
    type:'steps',
    cells:[
      {id:'empathise',label:'Empathise',color:'#be123c',hint:'Understand the user — observe, engage, immerse in their experience'},
      {id:'dtdefine',label:'Define',color:'#b45309',hint:'Synthesise findings into a clear problem statement or "How Might We…"'},
      {id:'ideate',label:'Ideate',color:'#7e22ce',hint:'Brainstorm boldly — diverge then converge on promising ideas'},
      {id:'prototype',label:'Prototype',color:'#1d4ed8',hint:'Build quick, cheap representations of solutions to learn from'},
      {id:'test',label:'Test',color:'#15803d',hint:'Put prototypes in front of users — learn, iterate, refine'},
    ]
  },
  {
    id:'kano', name:'Kano Model', cat:'Design & Innovation',
    desc:'Classify features by customer satisfaction impact.',
    layout:'g g-3col',
    cells:[
      {id:'basic',label:'Basic / Must-Be',color:'#b91c1c',hint:'Expected by default — absence causes dissatisfaction'},
      {id:'performance',label:'Performance',color:'#1d4ed8',hint:'More is better — linear relationship with satisfaction'},
      {id:'delight',label:'Delight / Excitement',color:'#15803d',hint:'Unexpected features that create wow — differentiators'},
    ]
  },
];

// ── STATE ──
let current = 0;
let data = {};
let modalTarget = null;
let selColor = COLORS[0].v;

F.forEach(f => { data[f.id] = {}; f.cells.forEach(c => { data[f.id][c.id] = []; }); });

// ── SIDEBAR ──
function renderSidebar() {
  let html = '';
  let lastCat = '';
  F.forEach((f, i) => {
    if (f.cat !== lastCat) {
      html += `<div class="side-category">${f.cat}</div>`;
      lastCat = f.cat;
    }
    const count = Object.values(data[f.id]).reduce((s, a) => s + a.length, 0);
    html += `<div class="side-item ${i === current ? 'active' : ''}" onclick="go(${i})">
      <span class="side-dot" style="background:${CAT[f.cat] || '#888'}"></span>
      <span>${f.name}</span>
      ${count ? `<span class="side-count">${count}</span>` : ''}
    </div>`;
  });
  document.getElementById('sidebar').innerHTML = html;
}

function go(i) { current = i; renderSidebar(); renderBoard(); }

// ── BOARD ──
function renderBoard() {
  const f = F[current];
  const d = data[f.id];
  const catColor = CAT[f.cat] || '#888';

  let inner = '';

  if (f.type === 'steps') {
    inner = f.cells.map((c, ci) => {
      const notes = d[c.id] || [];
      return `<div class="step-cell">
        <div class="step-num" style="background:${c.color}">${ci + 1}</div>
        <div class="step-body">
          <div class="cell-lbl">${c.label}</div>
          <div class="cell-hint">${c.hint}</div>
          <div class="notes">${renderNotes(notes, c.id)}</div>
          ${addBtn(c.id, c.label)}
        </div>
      </div>`;
    }).join('');
    inner = `<div class="g g-linear">${inner}</div>`;
  } else if (f.type === 'whys') {
    inner = f.cells.map((c, ci) => {
      const notes = d[c.id] || [];
      const arrow = ci > 0 && ci < f.cells.length - 1 ? '↓' : (ci === f.cells.length - 1 ? '✓' : '▸');
      return `<div class="why-row">
        <div class="why-arrow">${arrow}</div>
        <div class="why-body">
          <div class="cell-lbl"><span class="cdot" style="background:${c.color}"></span>${c.label}</div>
          <div class="cell-hint">${c.hint}</div>
          <div class="notes">${renderNotes(notes, c.id)}</div>
          ${addBtn(c.id, c.label)}
        </div>
      </div>`;
    }).join('');
    inner = `<div class="g g-whys">${inner}</div>`;
  } else {
    inner = f.cells.map(c => {
      if (c.empty) return `<div class="cell empty-cell" style="${c.style || ''}"></div>`;
      const notes = d[c.id] || [];
      return `<div class="cell" style="${c.style || ''}">
        <div class="cell-lbl"><span class="cdot" style="background:${c.color}"></span>${c.label}</div>
        <div class="cell-hint">${c.hint}</div>
        <div class="notes">${renderNotes(notes, c.id)}</div>
        ${addBtn(c.id, c.label)}
      </div>`;
    }).join('');
    inner = `<div class="${f.layout}">${inner}</div>`;
  }

  document.getElementById('canvas').innerHTML =
    `<div class="board">
      <div class="board-head">
        <h2>${f.name}</h2>
        <p>${f.desc}</p>
        <span class="board-tag" style="background:${catColor}15;color:${catColor}">${f.cat}</span>
      </div>
      ${inner}
    </div>`;
}

function renderNotes(notes, cellId) {
  return notes.map((n, i) =>
    `<div class="sticky" style="background:${n.color}">${esc(n.text)}<button class="rx" onclick="rmNote('${cellId}',${i})">×</button></div>`
  ).join('');
}

function addBtn(cellId, label) {
  return `<button class="add-btn" onclick="openModal('${cellId}','${esc(label)}')">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
    Add note
  </button>`;
}

// ── MODAL ──
function openModal(cellId, label) {
  modalTarget = cellId;
  selColor = COLORS[0].v;
  document.getElementById('mTitle').textContent = `Add to: ${label}`;
  const cell = F[current].cells.find(c => c.id === cellId);
  document.getElementById('mSub').textContent = cell ? cell.hint : '';
  document.getElementById('mInput').value = '';
  renderCP();
  document.getElementById('overlay').style.display = 'flex';
  setTimeout(() => document.getElementById('mInput').focus(), 50);
}

function closeModal(e) {
  if (e && e.target !== document.getElementById('overlay')) return;
  document.getElementById('overlay').style.display = 'none';
  modalTarget = null;
}

function renderCP() {
  document.getElementById('cpick').innerHTML = COLORS.map(c =>
    `<div class="cswatch ${c.v===selColor?'on':''}" style="background:${c.v}" onclick="pickC('${c.v}')" title="${c.n}"></div>`
  ).join('');
}
function pickC(v) { selColor = v; renderCP(); }

function submitNote() {
  const t = document.getElementById('mInput').value.trim();
  if (!t || !modalTarget) return;
  data[F[current].id][modalTarget].push({ text: t, color: selColor });
  closeModal();
  renderSidebar();
  renderBoard();
}

function rmNote(cellId, i) {
  data[F[current].id][cellId].splice(i, 1);
  renderSidebar();
  renderBoard();
}

function clearBoard() {
  const f = F[current];
  if (!confirm(`Clear all notes from "${f.name}"?`)) return;
  f.cells.forEach(c => { data[f.id][c.id] = []; });
  renderSidebar();
  renderBoard();
}

// ── EXPORT ──
function exportAll() {
  let out = `BA WORKSHOP — CHANGE & TRANSFORMATION TOOLKIT\nExported: ${new Date().toLocaleString()}\n${'═'.repeat(50)}\n`;
  let hasAny = false;
  F.forEach(f => {
    const d = data[f.id];
    let section = '';
    f.cells.forEach(c => {
      if (c.empty) return;
      const notes = d[c.id];
      if (notes.length) {
        section += `\n  [${c.label}]\n`;
        notes.forEach(n => { section += `    • ${n.text}\n`; });
      }
    });
    if (section) {
      hasAny = true;
      out += `\n\n${'─'.repeat(40)}\n${f.cat.toUpperCase()} — ${f.name}\n${'─'.repeat(40)}${section}`;
    }
  });
  if (!hasAny) { alert('No notes to export yet!'); return; }
  const blob = new Blob([out], { type: 'text/plain' });
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'ba-workshop-notes.txt';
  a.click();
  URL.revokeObjectURL(a.href);
}

// ── UTIL ──
function esc(s) { const d = document.createElement('div'); d.textContent = s; return d.innerHTML; }

function toggleSidebar() {
  const sb = document.getElementById('sidebar');
  sb.style.display = sb.style.display === 'none' ? 'block' : 'none';
}

document.addEventListener('keydown', e => {
  if (e.key === 'Escape') closeModal();
  if (e.key === 'Enter' && !e.shiftKey && document.getElementById('overlay').style.display === 'flex') {
    e.preventDefault(); submitNote();
  }
});

renderSidebar();
renderBoard();
</script>
</body>
</html>
