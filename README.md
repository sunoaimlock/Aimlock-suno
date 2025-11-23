<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Painel Suno — Visual Premium</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#070607;
  --accent:#ff2b2b;
  --accent-2:#ff6b6b;
  --neon:#00ff7f;
  --muted:#9b9b9b;
  --glass:rgba(255,255,255,0.03);
}
*{box-sizing:border-box;margin:0;padding:0;font-family:"Poppins",sans-serif}
body{
  min-height:100vh;
  background:radial-gradient(700px 400px at 20% 20%,rgba(255,43,43,0.06),transparent 60%),var(--bg);
  color:#eaeaea;
  display:flex;align-items:center;justify-content:center;padding:22px;
}

/* LOGIN OVERLAY */
#loginOverlay{
  position:fixed;inset:0;
  background:rgba(0,0,0,0.9);
  display:flex;align-items:center;justify-content:center;
  z-index:9999;
}
.login-box{
  background:rgba(255,255,255,0.03);
  border:1px solid rgba(255,255,255,0.04);
  padding:24px;
  border-radius:14px;
  width:100%;max-width:360px;
  text-align:center;
  box-shadow:0 20px 40px rgba(0,0,0,0.7);
}
.login-box .logo{
  width:58px;height:58px;margin:0 auto 12px;
  border-radius:12px;
  background:linear-gradient(135deg,var(--accent),var(--accent-2));
  display:flex;align-items:center;justify-content:center;
  color:#fff;font-weight:800;font-size:18px;
  box-shadow:0 6px 20px rgba(255,43,43,0.12);
}
.login-box h1{font-size:1.1rem;color:var(--accent-2);margin-bottom:16px}
.login-box input{
  width:100%;padding:12px;border-radius:10px;
  background:rgba(255,255,255,0.03);
  border:1px solid rgba(255,255,255,0.05);
  color:#fff;font-size:.95rem;
}
.login-box button{
  width:100%;margin-top:10px;padding:12px;border:none;border-radius:10px;
  font-weight:700;cursor:pointer;transition:.2s;
}
.login-btn{
  background:linear-gradient(90deg,var(--accent),var(--accent-2));
  color:#fff;box-shadow:0 8px 20px rgba(255,43,43,0.12);
}
.cancel-btn{
  background:transparent;border:1px solid rgba(255,255,255,0.06);
  color:var(--muted);
}
.msg{margin-top:10px;display:none;font-size:.9rem;font-weight:600}
.msg.error{color:#ff6b6b}
.msg.ok{color:var(--neon)}
small{display:block;margin-top:8px;color:var(--muted);font-size:.8rem}

/* MAIN PANEL */
.container{
  width:100%;max-width:660px;
  border-radius:18px;overflow:hidden;
  background:linear-gradient(180deg,rgba(255,255,255,0.015),rgba(255,255,255,0.01));
  box-shadow:0 20px 40px rgba(0,0,0,0.7);
  border:1px solid rgba(255,255,255,0.04);
  display:none;
}
.header{display:flex;justify-content:space-between;align-items:center;padding:14px 18px;background:#0c0c0c;border-bottom:1px solid rgba(255,255,255,0.04)}
.brand{display:flex;gap:12px;align-items:center}
.logo2{width:44px;height:44px;border-radius:10px;background:linear-gradient(135deg,var(--accent),var(--accent-2));display:flex;align-items:center;justify-content:center;font-weight:700;color:#fff}
.brand h1{font-size:1.05rem;margin:0;color:var(--accent-2)}
.status{display:flex;gap:10px;align-items:center;font-weight:700}
.status .dot{width:12px;height:12px;border-radius:50%;background:#500;box-shadow:0 0 6px #300}
.status.online .dot{background:var(--neon);box-shadow:0 0 10px var(--neon)}
.status .label{color:#ff6b6b}
.status.online .label{color:var(--neon)}

.tabs{display:flex;gap:8px;padding:10px 16px;background:#121212;border-bottom:1px solid rgba(255,255,255,0.03)}
.tab{padding:8px 14px;border-radius:12px;background:transparent;border:0;color:#aaa;cursor:pointer;font-weight:600;transition:.2s}
.tab.active{background:linear-gradient(90deg,var(--accent),var(--accent-2));color:#fff;box-shadow:0 8px 24px rgba(255,43,43,0.12)}
.tab:hover{color:#fff;}

.content{padding:18px;display:none}
.content.active{display:block}
.panel{background:var(--glass);border-radius:12px;padding:14px;border:1px solid rgba(255,255,255,0.04);margin-bottom:14px}
h2{color:var(--accent);margin:0 0 8px 0;font-size:1rem}
.small{color:var(--muted);font-size:.9rem;margin-bottom:8px}
.functions{display:flex;flex-direction:column;gap:10px}
.func{display:flex;align-items:center;justify-content:space-between;padding:12px;border-radius:10px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);cursor:pointer;}
.badge{min-width:62px;text-align:center;padding:8px 10px;border-radius:10px;font-weight:700;color:#ff6b6b;background:rgba(255,43,43,0.1);border:1px solid rgba(255,43,43,0.12);}
.badge.on{color:var(--neon);background:rgba(0,255,127,0.15);border-color:rgba(0,255,127,0.3);box-shadow:0 0 12px rgba(0,255,127,0.4);}
.inject-row{display:flex;align-items:center;justify-content:center;gap:12px;margin-top:8px}
.inject-btn{background:linear-gradient(90deg,var(--accent),var(--accent-2));color:#fff;padding:12px 28px;border-radius:12px;border:0;font-weight:800;cursor:pointer;box-shadow:0 12px 30px rgba(255,43,43,0.14)}
.inject-btn:hover{opacity:0.9}
.injected-success{display:none;margin:14px auto 0 auto;padding:10px 16px;border-radius:12px;background:linear-gradient(90deg,#05c76a,#00d57f);color:#022;font-weight:800;text-align:center;width:fit-content;box-shadow:0 10px 30px rgba(0,213,127,0.12);}
.terminal{height:220px;background:#040404;border-radius:8px;border:1px solid rgba(0,255,127,0.06);padding:12px;font-family:monospace;font-size:13px;color:var(--neon);overflow:auto;line-height:1.4;white-space:pre-wrap;word-break:break-word;}
.line{opacity:0;animation:fadeIn .32s forwards;margin-bottom:6px}
@keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
footer{padding:14px;text-align:center;color:#777;background:#0a0a0a;border-top:1px solid rgba(255,255,255,0.03)}
button, .func { outline:none !important; -webkit-tap-highlight-color:transparent; }
@media(max-width:520px){.container{padding:0 8px;}.tabs{overflow:auto}}
</style>
</head>
<body>

<!-- LOGIN -->
<div id="loginOverlay">
  <div class="login-box">
    <div class="logo">SU</div>
    <h1>Acesso ao Painel</h1>
    <input type="password" id="pwd" placeholder="Digite a senha..." />
    <button class="login-btn" id="enterBtn">Entrar</button>
    <button class="cancel-btn" onclick="location.reload()">Cancelar</button>
    <div class="msg" id="msg"></div>
    <small>Tentativas restantes: <span id="tries">5</span></small>
    <small id="cooldown" style="display:none">Bloqueado por <span id="seconds">60</span>s</small>
  </div>
</div>

<!-- PAINEL -->
<div class="container" id="painel">
  <div class="header">
    <div class="brand"><div class="logo2">OB</div><h1>Painel SUNO</h1></div>
    <div class="status" id="statusEl"><div class="dot"></div><div class="label">Offline</div></div>
  </div>

  <div class="tabs">
    <button class="tab active" data-tab="principal">Principal</button>
    <button class="tab" data-tab="ia">IA</button>
    <button class="tab" data-tab="bypass">Bypass</button>
    <button class="tab" data-tab="aimbot">Aimbot Rage</button>
  </div>

  <div id="principal" class="content active">
    <div class="panel">
      <h2>BY Dnzinzzk</h2>
      <div class="functions">
        <div class="func"><div>Cabeça</div><div class="badge">OFF</div></div>
        <div class="func"><div>Pescoço</div><div class="badge">OFF</div></div>
        <div class="func"><div>Peito</div><div class="badge">OFF</div></div>
      </div>
      <div class="inject-row">
        <button class="inject-btn" id="injectBtn">INJETAR FUNÇÕES</button>
      </div>
      <div class="injected-success" id="injectedSuccess">Injetado com sucesso</div>
    </div>
  </div>

  <div id="ia" class="content">
    <div class="panel">
      <h2>IA</h2>
      <div class="terminal" id="terminal"></div>
    </div>
  </div>

  <div id="bypass" class="content">
    <div class="panel">
      <h2>Bypass</h2>
      <div class="func"><div>Ativar Bypass</div><div class="badge">OFF</div></div>
    </div>
  </div>

  <div id="aimbot" class="content">
    <div class="panel">
      <h2>Bônus De Auxílio</h2>
      <div class="functions">
        <div class="func"><div>Aimbot Rage</div><div class="badge">OFF</div></div>
        <div class="func"><div>Norecoil</div><div class="badge">OFF</div></div>
        <div class="func"><div>Calibrar Mira</div><div class="badge">OFF</div></div>
        <div class="func"><div>Mira Pro</div><div class="badge">OFF</div></div>
      </div>
    </div>
  </div>

  <footer>© Programador Dnzinzzk</footer>
</div>

<script>
// LOGIN
(() => {
  const CORRECT = 'suno.sensi';
  const MAX_TRIES = 5;
  const LOCK_TIME = 60; // segundos
  const pwd = document.getElementById('pwd');
  const btn = document.getElementById('enterBtn');
  const msg = document.getElementById('msg');
  const triesEl = document.getElementById('tries');
  const coolEl = document.getElementById('cooldown');
  const secEl = document.getElementById('seconds');
  const overlay = document.getElementById('loginOverlay');
  const painel = document.getElementById('painel');
  let tries = MAX_TRIES;
  let cooldownTimer = null;

  const lockKey = 'sunk_lock_until';
  const storedLock = localStorage.getItem(lockKey);
  if(storedLock && Date.now() < +storedLock) startCooldown(Math.ceil((+storedLock-Date.now())/1000));

  function showMsg(t, ok=false){
    msg.style.display='block';
    msg.textContent=t;
    msg.className='msg '+(ok?'ok':'error');
  }

  function tryUnlock(){
    if(coolEl.style.display==='block') return;
    if(!pwd.value.trim()) return showMsg('Digite a senha.');
    if(pwd.value===CORRECT){
      showMsg('Acesso permitido.',true);
      setTimeout(()=>{
        overlay.style.display='none';
        painel.style.display='block';
      },600);
      return;
    }
    tries--;
    triesEl.textContent=tries;
    if(tries<=0){
      showMsg('Bloqueado por 1 minuto.');
      const until=Date.now()+LOCK_TIME*1000;
      localStorage.setItem(lockKey,until);
      startCooldown(LOCK_TIME);
    } else {
      showMsg('Senha incorreta.');
    }
  }

  function startCooldown(t){
    btn.disabled=true;pwd.disabled=true;
    coolEl.style.display='block';
    secEl.textContent=t;
    cooldownTimer=setInterval(()=>{
      t--;
      secEl.textContent=t;
      if(t<=0){
        clearInterval(cooldownTimer);
        btn.disabled=false;pwd.disabled=false;
        coolEl.style.display='none';
        msg.style.display='none';
        tries=MAX_TRIES;
        triesEl.textContent=tries;
        localStorage.removeItem(lockKey);
      }
    },1000);
  }

  btn.addEventListener('click',tryUnlock);
  pwd.addEventListener('keydown',e=>e.key==='Enter'&&tryUnlock());
})();

// PAINEL INTERNO
const tabs=document.querySelectorAll('.tab');
const contents=document.querySelectorAll('.content');
tabs.forEach(tab=>{
  tab.addEventListener('click',()=>{
    tabs.forEach(t=>t.classList.remove('active'));
    contents.forEach(c=>c.classList.remove('active'));
    tab.classList.add('active');
    document.getElementById(tab.dataset.tab)?.classList.add('active');
  });
});
document.querySelectorAll('.func').forEach(f=>{
  f.addEventListener('click',()=>{
    const b=f.querySelector('.badge');
    if(!b)return;
    b.classList.toggle('on');
    b.textContent=b.classList.contains('on')?'ON':'OFF';
    updateStatus();
  });
});
const injectedSuccess=document.getElementById('injectedSuccess');
document.getElementById('injectBtn')?.addEventListener('click',()=>{
  const any=document.querySelectorAll('.badge.on').length>0;
  if(!any)return;
  injectedSuccess.style.display='block';
  setTimeout(()=>injectedSuccess.style.display='none',1500);
});
const statusEl=document.getElementById('statusEl');
function updateStatus(){
  const anyOn=document.querySelectorAll('.badge.on').length>0;
  const label=statusEl.querySelector('.label');
  if(anyOn){statusEl.classList.add('online');label.textContent='Online';}
  else{statusEl.classList.remove('online');label.textContent='Offline';}
}
// Terminal IA
(function terminal(){
  const terminal=document.getElementById('terminal');
  if(!terminal)return;
  const lines=[
`InformesFuncion=Activado (R.id.switch1);//on`,
`ComienzaActividadesOcupación1Si=("On");`,
`sensitivity "string builder = sensitivity "+"case_sensitivity "+Lo Of = ("com.dts.freefireth");`,
`if ("sensitivity" > "99999");`,
`sensitivity ("string builder" = <sensitivity> + "99999");`,
`ComienzaActividadesOcupación2Si=("Of");`,
`Cancelar ComienzaActividadesOcupación2=("true");`,
`ComienzaActividadesOcupación3Si=("On");`,
`["TXT":"auxaims","switch1":"UI/Weapon/auxaims"]`,
`"TXT_SETTING_VIEW"=dword:10000601`,
`("true");`,
`Patches.aimfov 1x`
  ];
  function add(){
    const d=document.createElement('div');
    d.className='line';
    d.textContent=lines[Math.floor(Math.random()*lines.length)];
    terminal.appendChild(d);
    if(terminal.children.length>60)terminal.removeChild(terminal.firstChild);
    terminal.scrollTop=terminal.scrollHeight;
  }
  setInterval(add,180);
})();
</script>
</body>
</html>
