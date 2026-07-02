<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover" />
<meta name="theme-color" content="#3a0a1c" />
<title>דייט?</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Frank+Ruhl+Libre:wght@500;700;900&family=Assistant:wght@400;600;700&family=Fraunces:ital,opsz,wght@1,9..144,600&display=swap" rel="stylesheet">
<style>
  :root{
    --wine-1:#4a0e22;
    --wine-2:#2c0714;
    --gold:#e8b866;
    --gold-soft:#d9a24a;
    --cream:#f8ede0;
    --rose:#ef6f88;
    --rose-deep:#c8324f;
  }
  *{box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
  html,body{height:100%;margin:0;}
  body{
    font-family:'Assistant',system-ui,sans-serif;
    background:
      radial-gradient(120% 90% at 50% 8%, rgba(232,184,102,.18), transparent 55%),
      radial-gradient(140% 120% at 50% 120%, #63122f 0%, var(--wine-1) 35%, var(--wine-2) 100%);
    color:var(--cream);
    min-height:100dvh;
    overflow:hidden;
    position:relative;
    display:flex;align-items:center;justify-content:center;
    padding:24px;
  }
  /* vignette */
  body::after{
    content:"";position:fixed;inset:0;pointer-events:none;
    box-shadow:inset 0 0 200px 40px rgba(20,3,10,.7);
    z-index:1;
  }
  .drift{position:fixed;inset:0;overflow:hidden;pointer-events:none;z-index:0;}
  .drift span{position:absolute;bottom:-40px;font-size:22px;opacity:.0;filter:blur(.2px);
    animation:rise linear infinite;}
  @keyframes rise{
    0%{transform:translateY(0) rotate(0);opacity:0;}
    12%{opacity:.5;}
    90%{opacity:.35;}
    100%{transform:translateY(-112dvh) rotate(40deg);opacity:0;}
  }

  .stage{position:relative;z-index:2;width:100%;max-width:440px;text-align:center;}

  .card{
    background:linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.02));
    border:1px solid rgba(232,184,102,.28);
    border-radius:26px;
    padding:40px 26px 34px;
    backdrop-filter:blur(6px);
    -webkit-backdrop-filter:blur(6px);
    box-shadow:0 24px 60px -20px rgba(0,0,0,.65), inset 0 1px 0 rgba(255,255,255,.08);
  }

  .eyebrow{
    font-family:'Fraunces',serif;font-style:italic;
    letter-spacing:.02em;font-size:15px;
    color:var(--gold);
    display:flex;align-items:center;justify-content:center;gap:10px;
    margin-bottom:18px;
  }
  .eyebrow::before,.eyebrow::after{content:"";height:1px;width:26px;background:linear-gradient(90deg,transparent,var(--gold-soft));opacity:.7;}

  h1{
    font-family:'Frank Ruhl Libre',serif;font-weight:900;
    font-size:clamp(30px,9vw,44px);line-height:1.12;
    margin:0 0 14px;color:var(--cream);
    text-wrap:balance;
  }
  h1 .name{color:var(--gold);}
  .sub{
    font-size:clamp(15px,4.4vw,18px);line-height:1.6;
    color:rgba(248,237,224,.82);margin:0 auto 30px;max-width:22ch;font-weight:400;
  }

  .buttons{display:flex;flex-direction:column;align-items:center;gap:16px;min-height:120px;justify-content:center;}

  .btn{
    border:0;cursor:pointer;font-family:'Assistant',sans-serif;font-weight:700;
    border-radius:999px;transition:transform .18s ease, box-shadow .25s ease, background .2s;
    touch-action:manipulation;
  }
  .yes{
    background:linear-gradient(180deg,#ff849b,var(--rose-deep));
    color:#fff;font-size:22px;padding:18px 54px;
    box-shadow:0 14px 30px -8px rgba(200,50,79,.7), inset 0 1px 0 rgba(255,255,255,.35);
    display:inline-flex;align-items:center;gap:10px;
  }
  .yes:active{transform:scale(.97);}
  .no{
    background:rgba(255,255,255,.07);
    color:rgba(248,237,224,.75);
    font-size:17px;padding:12px 34px;
    border:1px solid rgba(255,255,255,.16);
  }
  .no.loose{position:fixed;z-index:40;margin:0;}

  /* reveal */
  .reveal{display:none;}
  .reveal.show{display:block;animation:pop .5s cubic-bezier(.2,.9,.3,1.2);}
  @keyframes pop{from{opacity:0;transform:scale(.9) translateY(10px);}to{opacity:1;transform:none;}}
  .yay{
    font-family:'Frank Ruhl Libre',serif;font-weight:900;
    font-size:clamp(38px,13vw,60px);margin:6px 0 6px;color:var(--gold);
    text-shadow:0 6px 24px rgba(232,184,102,.35);
  }
  .reveal p.lead{font-size:18px;margin:0 0 24px;color:rgba(248,237,224,.9);}
  .ticket{
    text-align:right;border:1px dashed rgba(232,184,102,.45);
    border-radius:18px;padding:20px 22px;background:rgba(0,0,0,.18);
    display:grid;grid-template-columns:auto 1fr;gap:12px 14px;align-items:center;
  }
  .ticket .ico{font-size:20px;text-align:center;width:26px;}
  .ticket .k{font-size:12px;color:var(--gold);letter-spacing:.03em;margin-bottom:1px;}
  .ticket .v{font-size:17px;font-weight:600;color:var(--cream);line-height:1.3;}
  .ticket .row{display:contents;}
  .place-latin{font-family:'Fraunces',serif;font-style:italic;}
  .foot{margin-top:22px;font-size:13px;color:rgba(248,237,224,.55);font-style:italic;font-family:'Fraunces',serif;}

  .confetti{position:fixed;top:-30px;z-index:60;pointer-events:none;font-size:22px;will-change:transform;}
  @keyframes fall{
    to{transform:translateY(112dvh) rotate(var(--r));opacity:.9;}
  }

  @media (prefers-reduced-motion: reduce){
    .drift span{animation-duration:1s;animation-iteration-count:1;opacity:.3;}
    .btn{transition:none;}
  }
</style>
</head>
<body>
  <div class="drift" id="drift" aria-hidden="true"></div>

  <div class="stage">
    <!-- INVITE -->
    <section class="card" id="invite">
      <div class="eyebrow">יום ראשון · ערב</div>
      <h1>נועה,<br>בא לך <span class="name">דייט</span>?</h1>
      <p class="sub">שולחן לשניים, פסטה טרייה ואווירה איטלקית מטורפת ב־Circolo&nbsp;Popolare. רק תגידי מילה אחת. 🍷</p>
      <div class="buttons" id="buttons">
        <button class="btn yes" id="yes">כן! 💛</button>
        <button class="btn no" id="no">לא</button>
      </div>
    </section>

    <!-- REVEAL -->
    <section class="card reveal" id="reveal">
      <div class="eyebrow">רשמית ומאושרת</div>
      <div class="yay">יש!! 🎉</div>
      <p class="lead">ידעתי שתגידי כן ❤️</p>
      <div class="ticket">
        <div class="row"><div class="ico">📍</div><div><div class="k">המקום</div><div class="v"><span class="place-latin">Circolo Popolare</span></div></div></div>
        <div class="row"><div class="ico">🗓️</div><div><div class="k">מתי</div><div class="v">יום ראשון · 18:30</div></div></div>
        <div class="row"><div class="ico">🍝</div><div><div class="k">התוכנית</div><div class="v">פסטה, פיצה דקה ולשבת עד שסוגרים</div></div></div>
        <div class="row"><div class="ico">🚕</div><div><div class="k">הכתובת</div><div class="v">40–41 Rathbone Pl, W1T&nbsp;1HX</div></div></div>
      </div>
      <div class="foot">אני מזמין. את רק צריכה להופיע יפה (זה קורה לבד).</div>
    </section>
  </div>

<script>
(function(){
  // floating background hearts
  var drift = document.getElementById('drift');
  var glyphs = ['❤️','🤍','🍷','✨','🍝'];
  for(var i=0;i<14;i++){
    var s=document.createElement('span');
    s.textContent=glyphs[i%glyphs.length];
    s.style.left=(Math.random()*100)+'%';
    s.style.fontSize=(14+Math.random()*20)+'px';
    s.style.animationDuration=(9+Math.random()*10)+'s';
    s.style.animationDelay=(-Math.random()*12)+'s';
    drift.appendChild(s);
  }

  var no = document.getElementById('no');
  var yes = document.getElementById('yes');
  var invite = document.getElementById('invite');
  var reveal = document.getElementById('reveal');

  var taunts = ['לא','בטוחה?','ממ.. לא','נסי שוב 😌','אי אפשר','תתפסי אותי!','לא היום','אין מצב 🙈','ויתרת?'];
  var count = 0;
  var loose = false;

  function moveNo(){
    var w = no.offsetWidth, h = no.offsetHeight;
    var pad = 14;
    var maxX = Math.max(pad, window.innerWidth  - w - pad);
    var maxY = Math.max(pad, window.innerHeight - h - pad);
    var x = pad + Math.random()*(maxX-pad);
    var y = pad + Math.random()*(maxY-pad);
    if(!loose){ no.classList.add('loose'); loose = true; }
    no.style.left = x+'px';
    no.style.top  = y+'px';
    count++;
    no.textContent = taunts[Math.min(count, taunts.length-1)];
    // yes grows a touch, gets more tempting
    var scale = Math.min(1 + count*0.045, 1.32);
    yes.style.transform = 'scale('+scale+')';
  }

  function dodge(e){ if(e){ e.preventDefault(); } moveNo(); }

  // react before the tap can land on touch devices
  ['touchstart','pointerdown','mousedown','pointerenter','mouseenter','click','focus'].forEach(function(evt){
    no.addEventListener(evt, dodge, {passive:false});
  });

  // celebration
  function confetti(){
    var items = ['❤️','🍝','🍷','✨','🎉','💛','🍅'];
    for(var i=0;i<70;i++){
      (function(i){
        setTimeout(function(){
          var c=document.createElement('div');
          c.className='confetti';
          c.textContent=items[Math.floor(Math.random()*items.length)];
          c.style.left=(Math.random()*100)+'vw';
          c.style.setProperty('--r',(Math.random()*720-360)+'deg');
          var dur=(2.6+Math.random()*2.2);
          c.style.animation='fall '+dur+'s linear forwards';
          c.style.fontSize=(16+Math.random()*20)+'px';
          document.body.appendChild(c);
          setTimeout(function(){c.remove();}, dur*1000+200);
        }, i*22);
      })(i);
    }
  }

  yes.addEventListener('click', function(){
    invite.style.display='none';
    reveal.classList.add('show');
    confetti();
    setTimeout(confetti, 900);
  });

  // keep the loose button on-screen if the viewport rotates/resizes
  window.addEventListener('resize', function(){ if(loose) moveNo(); });
})();
</script>
</body>
</html>
