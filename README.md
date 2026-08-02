<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta http-equiv="cache-control" content="no-cache, no-store, must-revalidate">
<meta http-equiv="expires" content="0">
<meta http-equiv="pragma" content="no-cache">
<title>PreTUS 7. Cilt · Deneme 01 (PART 5)</title>
<style>
  :root{
    --bg:#0d1117; --panel:#161b22; --panel2:#1c2330; --line:#2a3444;
    --text:#e6edf3; --muted:#9aa7b5; --accent:#4c9aff; --accent2:#7c5cff;
    --green:#2ea043; --green-bg:#12341c; --red:#e5484d; --red-bg:#3a1518;
    --star:#f5c451; --hint:#3fb6a8; --trap:#ff5b5b; --exp:#b487ff;
  }
  *{box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
  html,body{margin:0;padding:0;background:var(--bg);color:var(--text);
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
    line-height:1.6;-webkit-text-size-adjust:100%;}
  mark{background:none;color:var(--trap);font-weight:800;}
  b{color:#fff;font-weight:700;}

  header{position:fixed;top:0;left:0;right:0;z-index:50;background:var(--panel);
    border-bottom:1px solid var(--line);padding:env(safe-area-inset-top) 0 0 0;
    box-shadow:0 4px 18px rgba(0,0,0,.35);}
  .hbar{display:flex;align-items:center;justify-content:space-between;gap:10px;
    padding:11px 16px 10px;}
  .htitle{font-size:15px;font-weight:800;letter-spacing:.3px;}
  .htitle span{color:var(--accent);}
  .stats{display:flex;gap:8px;}
  .chip{display:flex;align-items:center;gap:5px;background:var(--panel2);
    border:1px solid var(--line);border-radius:999px;padding:5px 11px;
    font-size:13px;font-weight:700;}
  .chip.correct{color:var(--green);} .chip.star{color:var(--star);}
  .progress{height:5px;background:var(--panel2);width:100%;}
  .progress > i{display:block;height:100%;width:0;
    background:linear-gradient(90deg,var(--accent),var(--accent2));
    transition:width .35s ease;}

  main{max-width:720px;margin:0 auto;padding:16px 16px 120px;}

  .qmeta{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px;}
  .qnum{font-size:13px;font-weight:800;color:var(--muted);letter-spacing:.5px;}
  .star-btn{background:none;border:none;cursor:pointer;font-size:26px;line-height:1;
    filter:grayscale(1) opacity(.45);transition:transform .15s,filter .15s;padding:2px 4px;}
  .star-btn.on{filter:none;transform:scale(1.12);}

  .year-tags{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:10px;}
  .brans-tag{font-size:11.5px;font-weight:800;letter-spacing:.3px;color:var(--accent2);
    background:rgba(124,92,255,.12);border:1px solid rgba(124,92,255,.35);
    border-radius:6px;padding:3px 9px;}
  .gsec{grid-column:1/-1;font-size:11.5px;font-weight:800;letter-spacing:.5px;
    color:var(--accent2);text-transform:uppercase;padding:8px 2px 2px;
    border-top:1px solid var(--line);margin-top:4px;}
  .gsec:first-child{border-top:none;margin-top:0;padding-top:2px;}
  .brans-break{display:flex;flex-direction:column;gap:7px;width:100%;margin:14px 0 4px;}
  .bb-row{display:flex;align-items:center;gap:10px;background:var(--panel);
    border:1px solid var(--line);border-radius:11px;padding:9px 12px;}
  .bb-name{flex:1;font-size:13.5px;font-weight:800;text-align:left;}
  .bb-score{font-size:13.5px;font-weight:800;color:var(--text);}
  .bb-bar{height:6px;border-radius:4px;background:var(--panel2);overflow:hidden;
    width:76px;border:1px solid var(--line);}
  .bb-fill{height:100%;background:linear-gradient(90deg,var(--green),var(--accent));}
  .bb-row.weak .bb-name{color:var(--red);}
  .bb-title{font-size:12px;font-weight:800;letter-spacing:.5px;color:var(--muted);
    text-transform:uppercase;margin-top:16px;}
  .year-tag{font-size:11.5px;font-weight:700;letter-spacing:.3px;color:var(--accent);
    background:rgba(76,154,255,.1);border:1px solid rgba(76,154,255,.3);
    border-radius:6px;padding:3px 9px;}

  .qcard{background:var(--panel);border:1px solid var(--line);border-radius:16px;
    padding:18px 17px;margin-bottom:14px;font-size:16.5px;}

  .opts{display:flex;flex-direction:column;gap:10px;margin-bottom:14px;}
  .opt{display:flex;align-items:flex-start;gap:12px;background:var(--panel);
    border:1.5px solid var(--line);border-radius:13px;padding:13px 14px;cursor:pointer;
    font-size:16px;transition:border-color .15s,background .15s,transform .05s;
    text-align:left;color:var(--text);width:100%;}
  .opt:active{transform:scale(.995);}
  .opt .k{flex:0 0 26px;height:26px;border-radius:50%;background:var(--panel2);
    border:1px solid var(--line);display:flex;align-items:center;justify-content:center;
    font-weight:800;font-size:14px;color:var(--muted);}
  .opt .t{flex:1;padding-top:1px;}
  .opt:not(.locked):hover{border-color:var(--accent);}
  .opts.locked .opt{cursor:default;}
  .opt.correct{border-color:var(--green);background:var(--green-bg);}
  .opt.correct .k{background:var(--green);border-color:var(--green);color:#fff;}
  .opt.wrong{border-color:var(--red);background:var(--red-bg);}
  .opt.wrong .k{background:var(--red);border-color:var(--red);color:#fff;}
  .opt.dim{opacity:.55;}
  .opt .mark{flex:0 0 24px;height:26px;display:flex;align-items:center;justify-content:center;
    font-weight:900;font-size:18px;line-height:1;}
  .opt.correct .mark::after{content:"✓";color:var(--green);}
  .opt.wrong .mark::after{content:"✗";color:var(--red);}

  .hintbtn{display:inline-flex;align-items:center;gap:7px;background:var(--panel2);
    color:var(--hint);border:1px solid var(--line);border-radius:11px;padding:11px 15px;
    font-size:14.5px;font-weight:700;cursor:pointer;margin-bottom:14px;}
  .hintbtn:hover{border-color:var(--hint);}

  .box{border-radius:13px;padding:13px 15px;margin-bottom:11px;font-size:15.5px;
    border:1px solid var(--line);animation:fade .35s ease;}
  @keyframes fade{from{opacity:0;transform:translateY(6px);}to{opacity:1;transform:none;}}
  .box .bt{display:flex;align-items:center;gap:8px;font-weight:800;margin-bottom:6px;
    font-size:14px;letter-spacing:.3px;}
  .box.ip{background:rgba(63,182,168,.08);border-color:rgba(63,182,168,.35);}
  .box.ip .bt{color:var(--hint);}
  .box.tz{background:rgba(255,91,91,.07);border-color:rgba(255,91,91,.32);}
  .box.tz .bt{color:var(--trap);}
  .box.ac{background:rgba(180,135,255,.08);border-color:rgba(180,135,255,.32);}
  .box.ac .bt{color:var(--exp);}

  /* ===== AYIRICI TANI: gizli ok + eğlenceli flip + yeşil ipucu ===== */
  .qcard{position:relative;}
  .qcard.has-ddx{cursor:pointer;padding-right:46px;}
  .qcard .cue{transition:all .3s;border-radius:4px;}
  .qcard.flash .cue{background:rgba(46,160,67,.3);color:#fff;box-shadow:0 0 0 3px rgba(46,160,67,.3);padding:0 2px;}
  .ddx-ok{position:absolute;top:12px;right:12px;width:28px;height:28px;display:grid;place-items:center;
    color:var(--accent);cursor:pointer;animation:ddxpulse 2.2s ease-in-out infinite;z-index:3;}
  .ddx-ok svg{width:23px;height:23px;fill:none;stroke:currentColor;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;}
  @keyframes ddxpulse{0%,100%{opacity:.5;transform:translateY(0)}50%{opacity:1;transform:translateY(-2px)}}

  .cueMsg{position:fixed;left:0;right:0;top:0;z-index:400;background:#0f2a1e;
    border-bottom:2px solid var(--green);color:#b6f0d4;font-weight:700;font-size:15.5px;
    padding:15px 18px;text-align:center;box-shadow:0 8px 30px rgba(0,0,0,.5);
    transform:translateY(-110%);transition:transform .35s cubic-bezier(.34,1.56,.64,1);pointer-events:none;}
  .cueMsg.show{transform:translateY(0);animation:cuewiggle .5s ease .35s;}
  @keyframes cuewiggle{0%,100%{transform:translateY(0)}25%{transform:translateY(0) rotate(-.4deg)}75%{transform:translateY(0) rotate(.4deg)}}

  .ddx-ov{position:fixed;inset:0;z-index:300;display:none;align-items:center;justify-content:center;
    padding:20px;background:rgba(6,10,15,.55);backdrop-filter:blur(9px);-webkit-backdrop-filter:blur(9px);perspective:1800px;}
  .ddx-ov.show{display:flex;}
  .ddx-card{width:100%;max-width:440px;max-height:88vh;overflow-y:auto;
    background:linear-gradient(160deg,#1a2230 0%,#141a24 100%);
    border:1px solid rgba(76,154,255,.4);border-radius:22px;padding:22px;
    box-shadow:0 24px 70px rgba(0,0,0,.6),0 0 40px rgba(76,154,255,.12);
    cursor:pointer;}
  .ddx-ov.show .ddx-card{animation:dealIn .5s cubic-bezier(.2,.8,.22,1) both;}
  @keyframes dealIn{0%{opacity:0;transform:translateY(60vh) rotate(14deg) scale(.8)}100%{opacity:1;transform:none}}
  .ddx-ov.closing .ddx-card{animation:dealOut .4s cubic-bezier(.5,0,.75,.4) both;}
  @keyframes dealOut{0%{opacity:1;transform:none}100%{opacity:0;transform:translateY(60vh) rotate(14deg) scale(.8)}}
  .ddx-card h3{margin:0 0 14px;display:flex;align-items:center;gap:9px;font-size:16px;font-weight:800;
    background:linear-gradient(90deg,#4c9aff,#7ee7c7);-webkit-background-clip:text;background-clip:text;color:transparent;}
  .ddx-key{font-size:14.5px;color:var(--text);background:rgba(76,154,255,.1);
    border-left:3px solid var(--accent);border-radius:0 10px 10px 0;padding:10px 13px;margin-bottom:14px;}
  .ddx-cards{display:flex;flex-direction:column;gap:10px;}
  .dc{display:flex;gap:12px;align-items:flex-start;border:1px solid var(--line);border-radius:14px;
    padding:12px 13px;background:rgba(255,255,255,.025);position:relative;overflow:hidden;
    opacity:0;transform:translateX(-90px) rotate(-7deg);animation:ddxslide .45s cubic-bezier(.2,.85,.28,1.25) forwards;}
  .dc:nth-child(1){animation-delay:.12s} .dc:nth-child(2){animation-delay:.20s}
  .dc:nth-child(3){animation-delay:.28s} .dc:nth-child(4){animation-delay:.36s}
  .dc:nth-child(5){animation-delay:.44s} .dc:nth-child(6){animation-delay:.52s}
  .ddx-ov.closing .dc{animation:dcOut .28s cubic-bezier(.5,0,.75,.4) forwards;}
  @keyframes dcOut{to{opacity:0;transform:translateX(-90px) rotate(-7deg)}}
  .ddx-ov.closing .dc:nth-child(5){animation-delay:.02s}
  .ddx-ov.closing .dc:nth-child(4){animation-delay:.06s}
  .ddx-ov.closing .dc:nth-child(3){animation-delay:.10s}
  .ddx-ov.closing .dc:nth-child(2){animation-delay:.14s}
  .ddx-ov.closing .dc:nth-child(1){animation-delay:.18s}
  @keyframes ddxslide{to{opacity:1;transform:none}}
  .dc .emo{font-size:24px;flex:none;line-height:1.1;}
  .dc .txt .dn{font-weight:800;font-size:15px;margin-bottom:2px;color:var(--text);}
  .dc .txt .dv{font-size:13.5px;color:var(--muted);} .dc .txt .dv b{color:var(--text);font-weight:600;}
  .dc.hit{border-color:var(--green);background:linear-gradient(120deg,rgba(46,160,67,.2),rgba(46,160,67,.06));
    box-shadow:0 0 20px rgba(46,160,67,.25);}
  .dc.hit .dn{color:#7ee7a8;}
  .dc.hit::after{content:"⭐";position:absolute;top:8px;right:10px;font-size:15px;animation:ddxtwinkle 1.4s ease-in-out infinite;}
  @keyframes ddxtwinkle{0%,100%{opacity:.4;transform:scale(.9)}50%{opacity:1;transform:scale(1.15)}}
  .nav{position:fixed;bottom:0;left:0;right:0;z-index:40;background:var(--panel);
    border-top:1px solid var(--line);padding:12px 16px calc(12px + env(safe-area-inset-bottom));
    display:flex;gap:10px;max-width:720px;margin:0 auto;align-items:stretch;}
  .nav button{border:1px solid var(--line);border-radius:12px;padding:14px;
    font-size:15.5px;font-weight:800;cursor:pointer;background:var(--panel2);color:var(--text);}
  .nav .prev,.nav .next{flex:1;}
  .nav .list{flex:0 0 auto;min-width:66px;color:var(--muted);font-size:13px;
    display:flex;flex-direction:column;align-items:center;justify-content:center;gap:2px;line-height:1.1;}
  .nav .list .lc{font-size:16px;}
  .nav .next{background:linear-gradient(90deg,var(--accent),var(--accent2));
    color:#fff;border-color:transparent;}
  .nav button:disabled{opacity:.4;cursor:not-allowed;}
  /* nav dokunma/focus fix: buton basılı kalıp beyazlaşmaz */
  .nav button{-webkit-tap-highlight-color:transparent;}
  .nav button:focus{outline:none;}
  .nav .prev:focus,.nav .prev:active{background:var(--panel2);color:var(--text);border-color:var(--line);}
  .nav .list:focus,.nav .list:active{background:var(--panel2);color:var(--muted);border-color:var(--line);}
  .nav .next:focus,.nav .next:active{background:linear-gradient(90deg,var(--accent),var(--accent2));color:#fff;border-color:transparent;}


  /* Question-list modal (bottom sheet) */
  .modal-ov{position:fixed;inset:0;z-index:60;background:rgba(0,0,0,.55);
    display:none;align-items:flex-end;justify-content:center;}
  .modal-ov.show{display:flex;animation:fade .2s ease;}
  .modal{width:100%;max-width:720px;background:var(--panel);
    border-top-left-radius:20px;border-top-right-radius:20px;
    border:1px solid var(--line);border-bottom:none;padding:16px 16px 26px;
    max-height:72vh;overflow:auto;animation:slideup .28s ease;}
  @keyframes slideup{from{transform:translateY(30px);opacity:.6;}to{transform:none;opacity:1;}}
  .modal-h{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px;}
  .modal-h span{font-size:15px;font-weight:800;letter-spacing:.3px;}
  .modal-h .close{background:var(--panel2);border:1px solid var(--line);color:var(--text);
    border-radius:9px;width:34px;height:34px;font-size:16px;cursor:pointer;font-weight:800;}
  .qgrid{display:grid;grid-template-columns:repeat(6,1fr);gap:9px;}
  .gbtn{aspect-ratio:1/1;border-radius:10px;border:1.5px solid var(--line);
    background:var(--panel2);color:var(--text);font-size:14px;font-weight:800;cursor:pointer;
    display:flex;align-items:center;justify-content:center;position:relative;}
  .gbtn.ok{background:var(--green-bg);border-color:var(--green);color:var(--green);}
  .gbtn.no{background:var(--red-bg);border-color:var(--red);color:var(--red);}
  .gbtn.cur{outline:2px solid var(--accent);outline-offset:1px;}
  .gbtn.star::after{content:"";position:absolute;top:3px;right:3px;width:7px;height:7px;
    border-radius:50%;background:var(--star);}

  /* Result */
  .result{display:none;}
  .result.show{display:block;animation:fade .4s ease;}
  .score-ring{display:flex;flex-direction:column;align-items:center;justify-content:center;
    width:170px;height:170px;margin:8px auto 6px;border-radius:50%;
    background:conic-gradient(var(--accent) var(--pct,0%),var(--panel2) 0);}
  .score-ring .inner{width:138px;height:138px;border-radius:50%;background:var(--bg);
    display:flex;flex-direction:column;align-items:center;justify-content:center;}
  .score-ring .big{font-size:34px;font-weight:900;}
  .score-ring .sub{font-size:13px;color:var(--muted);font-weight:700;}
  .pctline{text-align:center;font-size:20px;font-weight:900;margin:2px 0 4px;}
  .fb{text-align:center;color:var(--muted);font-size:15px;margin-bottom:14px;}
  .result-stats{display:flex;gap:10px;justify-content:center;margin-bottom:22px;flex-wrap:wrap;}
  .rstat{background:var(--panel);border:1px solid var(--line);border-radius:11px;
    padding:9px 15px;font-size:13.5px;font-weight:800;}
  .rstat.g{color:var(--green);} .rstat.r{color:var(--red);} .rstat.s{color:var(--star);}
  .review-h{font-size:14px;font-weight:800;color:var(--muted);letter-spacing:.4px;
    margin:6px 0 10px;}
  .rev{display:flex;align-items:center;gap:11px;background:var(--panel);
    border:1px solid var(--line);border-radius:12px;padding:11px 13px;margin-bottom:9px;
    cursor:pointer;transition:border-color .15s;}
  .rev:hover{border-color:var(--accent);}
  .rev .badge{flex:0 0 auto;width:24px;height:24px;border-radius:6px;font-size:15px;
    display:flex;align-items:center;justify-content:center;font-weight:900;}
  .rev .badge.ok{background:var(--green-bg);color:var(--green);}
  .rev .badge.no{background:var(--red-bg);color:var(--red);}
  .rev .badge.blank{background:var(--panel2);color:var(--muted);}
  .rev .rq{flex:1;font-size:14px;}
  .rev .ra{font-size:12.5px;color:var(--muted);margin-top:2px;}
  .rev .ra b{color:var(--green);}
  .result-actions{display:flex;flex-direction:column;gap:10px;margin-top:16px;}
  .ract{width:100%;padding:15px;border-radius:13px;border:1px solid var(--line);
    background:var(--panel2);color:var(--text);font-size:15px;font-weight:800;cursor:pointer;}
  .ract:hover{border-color:var(--accent);}
  .ract.primary{background:linear-gradient(90deg,var(--accent),var(--accent2));
    color:#fff;border-color:transparent;}
  .ract:disabled{opacity:.4;cursor:not-allowed;}

  /* Resume prompt */
  .resume-ov{position:fixed;inset:0;z-index:70;background:rgba(0,0,0,.6);
    display:none;align-items:center;justify-content:center;padding:20px;}
  .resume-ov.show{display:flex;animation:fade .2s ease;}
  .resume-box{width:100%;max-width:420px;background:var(--panel);border:1px solid var(--line);
    border-radius:18px;padding:22px 20px;text-align:center;box-shadow:0 10px 40px rgba(0,0,0,.5);}
  .resume-t{font-size:18px;font-weight:900;margin-bottom:8px;}
  .resume-s{font-size:14px;color:var(--muted);margin-bottom:18px;line-height:1.5;}
  .resume-btns{display:flex;flex-direction:column;gap:10px;}
  .resume-btn{width:100%;padding:14px;border-radius:12px;border:1px solid var(--line);
    background:var(--panel2);color:var(--text);font-size:15px;font-weight:800;cursor:pointer;}
  .resume-btn:hover{border-color:var(--accent);}
  .resume-btn.primary{background:linear-gradient(90deg,var(--accent),var(--accent2));
    color:#fff;border-color:transparent;}


  /* ================= EĞLENCE KATMANI ================= */
  #fxCanvas{position:fixed;inset:0;width:100%;height:100%;pointer-events:none;z-index:90;}
  .emoji-pop{position:fixed;font-size:36px;pointer-events:none;z-index:95;
    will-change:transform,opacity;animation:floatUp 1.7s cubic-bezier(.2,.7,.3,1) forwards;}
  @keyframes floatUp{
    0%{opacity:0;transform:translate(0,0) scale(.4) rotate(0deg);}
    12%{opacity:1;transform:translate(0,-14px) scale(1.25) rotate(0deg);}
    100%{opacity:0;transform:translate(var(--dx,0px),-190px) scale(1.05) rotate(var(--rot,25deg));}
  }
  .emoji-drop{position:fixed;font-size:30px;pointer-events:none;z-index:95;
    animation:dropDown 1.5s ease-in forwards;}
  @keyframes dropDown{
    0%{opacity:0;transform:translateY(-30px) scale(.6) rotate(0deg);}
    15%{opacity:1;}
    100%{opacity:0;transform:translateY(150px) scale(1) rotate(var(--rot,-20deg));}
  }
  .shake{animation:shakeX .55s cubic-bezier(.36,.07,.19,.97) both;}
  @keyframes shakeX{
    10%,90%{transform:translateX(-2px);} 20%,80%{transform:translateX(4px);}
    30%,50%,70%{transform:translateX(-8px);} 40%,60%{transform:translateX(8px);}
  }
  .opt.correct{animation:popOk .55s cubic-bezier(.2,1.4,.4,1);
    box-shadow:0 0 22px rgba(46,160,67,.45);}
  @keyframes popOk{0%{transform:scale(1);}35%{transform:scale(1.035);}100%{transform:scale(1);}}
  .opt.wrong{animation:wobbleNo .5s;}
  @keyframes wobbleNo{
    0%,100%{transform:translateX(0);}20%{transform:translateX(-6px);}
    40%{transform:translateX(6px);}60%{transform:translateX(-4px);}80%{transform:translateX(4px);}
  }
  .mascot{position:absolute;right:12px;top:50%;font-size:26px;line-height:1;
    transform:translateY(-50%);animation:mascotDance .7s ease-in-out infinite alternate;
    pointer-events:none;filter:drop-shadow(0 2px 6px rgba(0,0,0,.4));}
  @keyframes mascotDance{
    from{transform:translateY(-42%) rotate(-12deg) scale(1);}
    to{transform:translateY(-62%) rotate(12deg) scale(1.18);}
  }
  .streak{position:fixed;left:50%;top:22%;transform:translateX(-50%) scale(.6);
    font-size:22px;font-weight:900;color:var(--star);z-index:96;opacity:0;
    text-shadow:0 3px 14px rgba(0,0,0,.6);pointer-events:none;
    animation:streakPop 1.5s ease-out forwards;white-space:nowrap;}
  @keyframes streakPop{
    0%{opacity:0;transform:translateX(-50%) scale(.5);}
    20%{opacity:1;transform:translateX(-50%) scale(1.15);}
    75%{opacity:1;transform:translateX(-50%) scale(1);}
    100%{opacity:0;transform:translateX(-50%) scale(1) translateY(-24px);}
  }
  .score-ring{animation:ringIn .8s cubic-bezier(.2,1.2,.3,1);}
  @keyframes ringIn{from{transform:scale(.75) rotate(-12deg);opacity:0;}to{transform:none;opacity:1;}}


  /* Cevap mesaji: son sik ile ipucu kutusu arasinda YUZEN baloncuk.
     Yuksekligi 0 -> icerigi itmez; birkac saniyede kaybolur. */
  .fxfloat{position:relative;height:0;overflow:visible;}
  .fxfloat .pill{position:absolute;left:50%;top:-4px;
    transform:translateX(-50%);
    background:var(--panel2);border:1px solid var(--line);color:var(--text);
    padding:11px 18px;border-radius:11px;font-size:14px;font-weight:700;
    white-space:nowrap;z-index:80;pointer-events:none;
    box-shadow:0 6px 20px rgba(0,0,0,.45);
    animation:pillIn .25s ease both, pillOut .45s ease 1.55s forwards;}
  @keyframes pillIn{
    from{opacity:0;transform:translateX(-50%) translateY(12px);}
    to{opacity:1;transform:translateX(-50%) translateY(0);}
  }
  @keyframes pillOut{
    to{opacity:0;transform:translateX(-50%) translateY(-8px);}
  }

  /* Toast */
  .toast{position:fixed;left:50%;bottom:96px;transform:translateX(-50%) translateY(20px);
    background:var(--panel2);border:1px solid var(--line);color:var(--text);
    padding:11px 18px;border-radius:11px;font-size:14px;font-weight:700;z-index:80;
    opacity:0;pointer-events:none;transition:opacity .25s,transform .25s;box-shadow:0 6px 20px rgba(0,0,0,.4);}
  .toast.show{opacity:1;transform:translateX(-50%) translateY(0);}
</style>
</head>
<body>
<header id="hdr">
  <div class="hbar">
    <div class="htitle">PreTUS · 7. Cilt · Deneme 01 · PART 5 <span>TUS</span></div>
    <div class="stats">
      <div class="chip correct">✓ <span id="cCount">0</span></div>
      <div class="chip star">⭐ <span id="sCount">0</span></div>
    </div>
  </div>
  <div class="progress"><i id="bar"></i></div>
</header>

<main id="main">
  <div id="quiz"></div>
  <div class="cueMsg" id="cueMsg"></div>
  <div class="ddx-ov" id="ddxOv" onclick="closeDdx()"></div>

  <div class="result" id="result">
    <div class="score-ring" id="ring">
      <div class="inner">
        <div class="big" id="scoreBig">0/0</div>
        <div class="sub">DOĞRU</div>
      </div>
    </div>
    <div class="pctline" id="pctLine">%0</div>
    <div class="fb" id="fbText"></div>
    <div class="result-stats" id="rStats"></div>
    <div class="bb-title" id="bbTitle" style="display:none">BRANŞ DÖKÜMÜ</div>
    <div class="brans-break" id="bransBreak"></div>
    <div class="result-actions">
      <button class="ract primary" onclick="restart()">↺ Tüm Soruları Yeniden Çöz</button>
      <button class="ract" id="retryWrongBtn" onclick="retryWrong()">✗ Yanlışları Tekrar Çöz</button>
      <button class="ract" id="retryStarBtn" onclick="retryStar()">⭐ Yıldızlıları Tekrar Çöz</button>
    </div>
    <div class="review-h">SORU İNCELEMESİ</div>
    <div id="reviewList"></div>
    
  </div>
</main>

<div class="nav" id="nav">
  <button class="prev" id="prevBtn" onclick="go(-1)">← Önceki</button>
  <button class="list" id="listBtn" onclick="openModal()"><span class="lc">☰</span><span id="navCounter">0/0</span></button>
  <button class="next" id="nextBtn" onclick="go(1)">Sonraki →</button>
</div>

<div class="modal-ov" id="modalOv" onclick="modalBg(event)">
  <div class="modal">
    <div class="modal-h"><span>Sorular</span><button class="close" onclick="closeModal()">✕</button></div>
    <div class="qgrid" id="qGrid"></div>
  </div>
</div>

<div class="resume-ov" id="resumeOv">
  <div class="resume-box">
    <div class="resume-t">↩ Kaldığın yerden devam?</div>
    <div class="resume-s" id="resumeSub"></div>
    <div class="resume-btns">
      <button class="resume-btn primary" onclick="resumeYes()">Kaldığım yerden devam et</button>
      <button class="resume-btn" onclick="resumeNo()">Baştan başla</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
/* =========================================================
   QUESTIONS — SADECE BU DİZİ DEĞİŞİR.
   Her obje: { yil?, soru, siklar[5], dogru(0-4), ipucu, tuzak, aciklama }
   ========================================================= */
const QUESTIONS = [
 {
  "brans": "Dahiliye",
  "soru": "Trafik kazası nedeniyle hastaneye getirilen genç bir hastaya <b>splenektomi</b> yapılıyor.<br><br>Aşağıdakilerden hangisi bu hastada cerrahi sonrası beklenen periferik yayma bulgularından birisi <mark class=\"cue\">değildir</mark>?",
  "siklar": [
   {
    "k": "A",
    "t": "Polikromazi"
   },
   {
    "k": "B",
    "t": "Hedef hücreler"
   },
   {
    "k": "C",
    "t": "Trombosit sayısında artış"
   },
   {
    "k": "D",
    "t": "Howell-Jolly cisimcikleri"
   },
   {
    "k": "E",
    "t": "Pappenheimer cisimcikleri"
   }
  ],
  "dogru": 0,
  "cue": "🎯 Dalak yokken temizlenemeyen kalıntıları listele; geriye kalan bulgu kemik iliği yanıtını mı anlatıyor?",
  "ipucu": "Dalak, eritrositlerin içindeki artıkları söküp alan bir filtredir. Bu filtre kalkınca hangi cisimcikler dolaşımda kalır?",
  "tuzak": "<mark>Polikromazi retikülositozun göstergesidir</mark>, yani kemik iliğinin artmış üretim yanıtını yansıtır — splenektominin doğrudan sonucu değildir. Aksine dalak alındıktan sonra retikülosit havuzlanması ortadan kalkar.",
  "aciklama": "Splenektomi sonrası periferik yaymada dalağın filtrasyon (pitting) işlevinin kaybına bağlı olarak <b>Howell-Jolly cisimcikleri</b> (nükleer DNA artığı), <b>Pappenheimer cisimcikleri</b> (demir granülleri), <b>hedef hücreler</b>, akantositler, poikilositoz ve anizositoz görülür. Ayrıca dalağın trombosit havuzlaması kalktığı için <b>trombositoz</b> gelişir. <b>Polikromazi</b> ise artmış eritrosit üretiminin (retikülositoz) göstergesidir ve splenektominin beklenen bulgusu değildir."
 },
 {
  "brans": "Dahiliye",
  "soru": "Altmış beş yaşında erkek hasta altı aydır olan halsizlik, yorgunluk, <b>aralıklı burun kanaması</b> ve 5 kg istemsiz kilo kaybı şikâyetleri nedeniyle başvuruyor. Hasta ayaklarında karıncalanma ve uyuşma, <mark class=\"cue\">bulanık görme ve kulak çınlaması</mark> şikâyetleri de olduğunu belirtiyor. Fizik muayenede karaciğer kostal marjin altından palpe edilebiliyor. Boyun, aksilla ve kasık bölgesinde ağrısız büyümüş lenf nodları palpe ediliyor.<br>Laboratuvarda hemoglobin 8,8 g/dL, lökosit 6.300/mm³, trombosit 98.000/mm³, sedimentasyon 70 mm/saat, kreatinin 0,9 mg/dL, kan üre azotu 10 mg/dL, kalsiyum 8,6 mg/dL. Serum protein elektroforezinde <b>keskin ve dar tabanlı monoklonal immünglobülin bandı</b> izleniyor.<br><br>Bu hastada en olası tanı aşağıdakilerden hangisidir?",
  "siklar": [
   {
    "k": "A",
    "t": "Kronik lenfositik lösemi"
   },
   {
    "k": "B",
    "t": "Hairy cell lösemi"
   },
   {
    "k": "C",
    "t": "Multipl miyelom"
   },
   {
    "k": "D",
    "t": "Waldenström makroglobülinemisi"
   },
   {
    "k": "E",
    "t": "Mantle cell lenfoma"
   }
  ],
  "dogru": 3,
  "cue": "🎯 Monoklonal band var ama böbrek, kalsiyum ve kemik normal; bulanık görme ve çınlama hangi fizyopatolojiyi anlatır?",
  "ipucu": "Bulanık görme, kulak çınlaması, burun kanaması ve nörolojik bulgular birlikte hiperviskozite sendromunu düşündürür. Hangi immünglobülin en viskozdur?",
  "tuzak": "Monoklonal band görünce refleks olarak <mark>multipl miyelom</mark> seçilir. Ancak miyelomun CRAB kriterleri (hiperKalsemi, Renal yetmezlik, Anemi, Bone/kemik lezyonu) burada yok: kalsiyum ve kreatinin normal, kemik ağrısı tarif edilmiyor. Buna karşılık miyelomda görülmeyen <b>lenfadenopati, hepatomegali ve hiperviskozite</b> tablosu var.",
  "aciklama": "<b>Waldenström makroglobülinemisi</b> (lenfoplazmasitik lenfoma), <b>monoklonal IgM</b> üretimi ile seyreder. IgM pentamerik ve yüksek moleküler ağırlıklı olduğu için <b>hiperviskozite sendromu</b> yapar: bulanık görme (retinal ven dilatasyonu, “sosis” görünümü), kulak çınlaması, baş ağrısı, mukozal kanamalar ve nöropati. Miyelomdan farklı olarak <b>litik kemik lezyonu, hiperkalsemi ve böbrek yetmezliği tipik değildir</b>; buna karşın lenfadenopati ve hepatosplenomegali görülür. MYD88 L265P mutasyonu karakteristiktir; acil tedavi plazmaferezdir.",
  "ddx": {
   "baslik": "Monoklonal Gammopati ile Seyreden Hastalıklar",
   "ok": "İmmünglobülin tipini ve eşlik eden bulguyu birlikte oku: kemik mi, LAP mi, hiperviskozite mi?",
   "satirlar": [
    {
     "emo": "👁️",
     "ad": "Waldenström makroglobülinemisi",
     "bulgu": "Monoklonal <b>IgM</b>. <b>Hiperviskozite</b> (bulanık görme, çınlama, kanama), LAP + hepatosplenomegali. Kemik lezyonu ve hiperkalsemi <b>yok</b>. MYD88 L265P.",
     "hit": true
    },
    {
     "emo": "🦴",
     "ad": "Multipl miyelom",
     "bulgu": "Monoklonal <b>IgG/IgA</b>. <b>CRAB</b>: hiperkalsemi, böbrek yetmezliği, anemi, litik kemik lezyonu. LAP tipik <b>değil</b>."
    },
    {
     "emo": "🩸",
     "ad": "Kronik lenfositik lösemi",
     "bulgu": "Belirgin <b>lenfositoz</b> (>5000), smudge hücreleri, CD5+/CD23+. Otoimmün hemolitik anemi/ITP eşlik edebilir."
    },
    {
     "emo": "🌾",
     "ad": "Hairy cell lösemi",
     "bulgu": "<b>Pansitopeni + masif splenomegali</b>, LAP genelde yok. TRAP pozitif, kuru aspirasyon, BRAF V600E."
    },
    {
     "emo": "🧬",
     "ad": "Mantle cell lenfoma",
     "bulgu": "CD5+/CD23−, <b>t(11;14)</b> siklin D1. Yaygın LAP, sık GİS tutulumu (lenfomatoid polipozis)."
    }
   ]
  }
 },
 {
  "brans": "Dahiliye",
  "soru": "Otuz beş yaşında kadın hasta halsizlik, yorgunluk ve <b>bilinç bulanıklığı</b> ile getiriliyor. Vücut sıcaklığı 38,4 °C. Laboratuvarda lökosit 4.400/mm³, hemoglobin 10,5 g/dL, trombosit <b>11.000/mm³</b>, <mark class=\"cue\">D-dimer 0,2 µg/L (normal < 0,5)</mark>, kreatinin 1,8 mg/dL. Periferik yaymada çekirdekli eritrositler ile <b>fragmente eritrositler</b> görülüyor.<br><br>Bu hastada en uygun yaklaşım aşağıdakilerden hangisidir?",
  "siklar": [
   {
    "k": "A",
    "t": "İntravenöz immünglobülin tedavisi başlanmalıdır."
   },
   {
    "k": "B",
    "t": "Trombosit transfüzyonu yapılmalıdır."
   },
   {
    "k": "C",
    "t": "Trombosit ve eritrosit transfüzyonu yapılmalıdır."
   },
   {
    "k": "D",
    "t": "Plazmaferez ile acil plazma değişimi yapılmalıdır."
   },
   {
    "k": "E",
    "t": "Antibiyotik tedavisi başlanmalıdır."
   }
  ],
  "dogru": 3,
  "cue": "🎯 Şistositli mikroanjiyopatide normal D-dimer bir ayırıcıdır; pıhtılaşma tüketilmiyorsa sorumlu ne?",
  "ipucu": "Ateş + nörolojik bulgu + trombositopeni + mikroanjiyopatik hemolitik anemi + böbrek fonksiyon bozukluğu = klasik pentad.",
  "tuzak": "<mark>Trombosit transfüzyonu bu hastalıkta kontrendikedir</mark> — “yakıta benzin dökmek” gibi mikrotrombüs oluşumunu artırır ve tabloyu ağırlaştırır. Ayrıca normal D-dimer ve fibrinojen DİK'i dışlar; ADAMTS13 eksikliği ile giden TTP'de koagülasyon testleri normaldir.",
  "aciklama": "Tablo <b>trombotik trombositopenik purpura (TTP)</b> ile uyumludur: ateş, nörolojik bulgular, ağır trombositopeni, şistositlerle giden mikroanjiyopatik hemolitik anemi ve böbrek fonksiyon bozukluğu. <b>Normal D-dimer</b> DİK'ten ayırt ettirir. Patogenezde <b>ADAMTS13</b> eksikliği/inhibisyonu sonucu ultra-büyük von Willebrand multimerlerinin birikmesi vardır. Tanıdan şüphelenildiği anda mortaliteyi %90'dan %10-20'ye indiren <b>acil plazma değişimi (plazmaferez)</b> başlanmalıdır; steroid ve kaplasizumab eklenir.",
  "ddx": {
   "baslik": "Trombositopeni + Şistosit Ayırımı",
   "ok": "Koagülasyon testleri (D-dimer, fibrinojen, PT/aPTT) normal mi bozuk mu — ilk ayırıcı budur.",
   "satirlar": [
    {
     "emo": "🧠",
     "ad": "TTP",
     "bulgu": "<b>ADAMTS13</b> eksikliği. Ateş, nörolojik bulgu, böbrek, MAHA, trombositopeni. <b>D-dimer ve fibrinojen normal</b>. Tedavi: plazma değişimi.",
     "hit": true
    },
    {
     "emo": "💧",
     "ad": "DİK",
     "bulgu": "<b>D-dimer yüksek, fibrinojen düşük, PT/aPTT uzun</b>. Sepsis, malignite, obstetrik neden. Tedavi altta yatan nedene yöneliktir."
    },
    {
     "emo": "🫘",
     "ad": "HÜS",
     "bulgu": "Çocukta kanlı ishal sonrası (STEC-O157:H7). <b>Böbrek yetmezliği baskın</b>, nörolojik bulgu siliktir. Destek tedavi."
    },
    {
     "emo": "🟣",
     "ad": "İTP",
     "bulgu": "İzole trombositopeni; <b>şistosit yok</b>, hemoliz yok. Tedavi: steroid, İVİG."
    },
    {
     "emo": "💉",
     "ad": "Heparin ilişkili trombositopeni",
     "bulgu": "Heparin sonrası 5-10. gün; trombositopeni + <b>tromboz</b>. Heparin kesilir, direkt trombin inhibitörü başlanır."
    }
   ]
  }
 },
 {
  "brans": "Dahiliye",
  "soru": "<b>Febril nötropenisi</b> olan bir hastaya <mark class=\"cue\">ampirik antibiyotik tedavi planlaması öncesinde</mark> aşağıdaki parametrelerden hangisi dikkate alınır?",
  "siklar": [
   {
    "k": "A",
    "t": "Hastanın cinsiyeti"
   },
   {
    "k": "B",
    "t": "Astım öyküsü"
   },
   {
    "k": "C",
    "t": "Hastanın yaşı"
   },
   {
    "k": "D",
    "t": "Aldığı kemoterapi protokolü"
   },
   {
    "k": "E",
    "t": "Nötropeni derinliği"
   }
  ],
  "dogru": 2,
  "cue": "🎯 Ampirik tedaviyi yönlendiren şey risk sınıflamasıdır; kullanılan skorda hangi demografik değişken puan alıyor?",
  "ipucu": "Febril nötropenide düşük/yüksek risk ayrımı MASCC skoru ile yapılır; bu skorda hastanın demografik bir özelliği doğrudan puanlanır.",
  "tuzak": "Nötropeninin derinliği ve süresi <mark>enfeksiyon riskini belirler</mark> ancak ampirik rejimin seçiminde MASCC skorunda yer alan parametre değildir; kemoterapi protokolü de rejim seçimini doğrudan belirlemez. MASCC'de puanlanan demografik değişken <b>yaştır</b>.",
  "aciklama": "Febril nötropenide ampirik tedavi kararı <b>MASCC risk indeksi</b> ile verilir; bu skorda semptom yükü, hipotansiyon olmaması, KOAH olmaması, solid tümör/fungal enfeksiyon öyküsü olmaması, dehidratasyon olmaması, ayaktan başvuru ve <b>60 yaşın altında olmak</b> puanlanır. Skor ≥21 ise düşük risk kabul edilir ve oral/ayaktan tedavi düşünülebilir; düşük skorda antipsödomonal beta-laktam ile hastane içi intravenöz tedavi başlanır."
 },
 {
  "brans": "Dahiliye",
  "soru": "Aşağıdaki hedefe yönelik ilaçlardan hangisi <mark class=\"cue\">DNA tamirini engelleyerek</mark> etki gösterir?",
  "siklar": [
   {
    "k": "A",
    "t": "Palbosiklib"
   },
   {
    "k": "B",
    "t": "Panitumumab"
   },
   {
    "k": "C",
    "t": "Pembrolizumab"
   },
   {
    "k": "D",
    "t": "İpilimumab"
   },
   {
    "k": "E",
    "t": "Olaparib"
   }
  ],
  "dogru": 4,
  "cue": "🎯 Diğer dördü ya siklusu ya da reseptör/kontrol noktasını hedefliyor; tek başına tamir yolunu kesen hangisi?",
  "ipucu": "Sonu “-parib” ile biten ilaçların ortak hedefi tek zincir DNA kırıklarının onarımında görevli bir enzimdir.",
  "tuzak": "<mark>Pembrolizumab ve ipilimumab immün kontrol noktası inhibitörleridir</mark> (PD-1 ve CTLA-4); DNA ile ilgileri yoktur. Palbosiklib CDK4/6, panitumumab ise EGFR hedeflidir.",
  "aciklama": "<b>Olaparib</b> bir <b>PARP inhibitörüdür</b>. PARP enzimi tek zincir DNA kırıklarının baz eksizyon tamirinde görev alır; inhibe edildiğinde bu kırıklar çift zincir kırığına dönüşür. <b>BRCA1/2 mutant</b> hücrelerde homolog rekombinasyon zaten bozuk olduğu için hücre onarım yapamaz ve ölür — buna <b>sentetik letalite</b> denir. Over, meme, prostat ve pankreas kanserlerinde BRCA mutasyonu varlığında kullanılır."
 },
 {
  "brans": "Dahiliye",
  "soru": "Aşağıdaki klinik durumlardan hangisinde <mark class=\"cue\">potasyum kaybına bağlı</mark> hipokalemi beklenmez?",
  "siklar": [
   {
    "k": "A",
    "t": "İshal"
   },
   {
    "k": "B",
    "t": "Bartter sendromu"
   },
   {
    "k": "C",
    "t": "Salbutamol kullanımı"
   },
   {
    "k": "D",
    "t": "Furosemid kullanımı"
   },
   {
    "k": "E",
    "t": "Hiperaldosteronizm"
   }
  ],
  "dogru": 2,
  "cue": "🎯 Hipokaleminin iki yolu var: vücuttan kaybetmek ya da hücre içine kaçırmak. Hangisi ikinci gruba giriyor?",
  "ipucu": "Beta-2 agonistler Na⁺/K⁺-ATPaz pompasını uyarır.",
  "tuzak": "Salbutamol gerçekten hipokalemi yapar; ancak soru <mark>mekanizmayı sorgular</mark>: burada potasyum vücuttan atılmaz, <b>hücre içine kayar (redistribüsyon)</b>. Toplam vücut potasyumu değişmez. İnsülin, alkaloz ve beta-2 agonistler bu grubun klasik örnekleridir.",
  "aciklama": "<b>Salbutamol</b> beta-2 reseptörleri üzerinden Na⁺/K⁺-ATPazı aktive ederek potasyumu <b>hücre içine kaydırır</b>; bu bir transselüler şifttir, kayıp değildir. Diğerlerinde ise gerçek potasyum kaybı vardır: ishalde gastrointestinal, Bartter sendromunda (Henle çıkan kalın kolunda NKCC2 defekti), furosemid kullanımında ve hiperaldosteronizmde ise renal yoldan kayıp olur."
 },
 {
  "brans": "Dahiliye",
  "soru": "<b>Cockcroft-Gault formülü</b> ile kreatinin klirensi hesaplanırken aşağıdaki parametrelerden hangisine <mark class=\"cue\">ihtiyaç duyulmaz</mark>?",
  "siklar": [
   {
    "k": "A",
    "t": "Serum kreatinin değeri"
   },
   {
    "k": "B",
    "t": "24 saatlik idrar volümü"
   },
   {
    "k": "C",
    "t": "Cinsiyet"
   },
   {
    "k": "D",
    "t": "Vücut ağırlığı"
   },
   {
    "k": "E",
    "t": "Yaş"
   }
  ],
  "dogru": 1,
  "cue": "🎯 Bu formülün pratik avantajı ne? Hastadan bir şey toplamaya gerek kalmaması.",
  "ipucu": "Cockcroft-Gault formülü: [(140 − yaş) × ağırlık] / (72 × serum kreatinin), kadınlarda × 0,85.",
  "tuzak": "<mark>Klasik kreatinin klirensi hesabı 24 saatlik idrar toplamayı gerektirir</mark> ((idrar kreatinini × idrar volümü) / (serum kreatinini × 1440)) ve bu iki formül karıştırılır. Cockcroft-Gault'un tüm değeri, idrar toplamadan tahmin yapabilmesidir.",
  "aciklama": "<b>Cockcroft-Gault formülü</b> yalnızca <b>yaş, vücut ağırlığı, cinsiyet ve serum kreatinini</b> kullanır: [(140 − yaş) × ağırlık(kg)] / (72 × serum kreatinin), kadınlarda sonuç 0,85 ile çarpılır. <b>24 saatlik idrar volümü gerekmez</b>; bu parametre ölçülmüş kreatinin klirensi hesabında kullanılır. Formül özellikle ilaç doz ayarlamasında tercih edilir."
 },
 {
  "brans": "Dahiliye",
  "soru": "Kronik böbrek hastalığı nedeni ile takip edilen bir hastada fosfor düzeyi yüksek saptanıyor. Diyette fosfor kısıtlanmasına rağmen fosfor düzeyi yüksek seyreden hastaya <b>oral fosfor bağlayıcı</b> başlanması planlanıyor.<br><br>Bu hastada aşağıdaki preparatlardan hangisi <mark class=\"cue\">tercih edilmez</mark>?",
  "siklar": [
   {
    "k": "A",
    "t": "Kalsiyum asetat"
   },
   {
    "k": "B",
    "t": "Kalsiyum glukonat"
   },
   {
    "k": "C",
    "t": "Sevelamer"
   },
   {
    "k": "D",
    "t": "Lantanum karbonat"
   },
   {
    "k": "E",
    "t": "Magnezyum karbonat"
   }
  ],
  "dogru": 1,
  "cue": "🎯 Fosfor bağlayıcı olmak için ilacın bağırsakta fosfata bağlanması gerekir; hangisi bunun için üretilmemiş?",
  "ipucu": "Kalsiyum tuzlarının hepsi fosfor bağlayıcı değildir; bağlayıcı olarak kullanılanlar asetat ve karbonat tuzlarıdır.",
  "tuzak": "“Kalsiyum içeriyorsa fosfor bağlar” varsayımı yanlıştır. <mark>Kalsiyum glukonat parenteral bir kalsiyum preparatıdır</mark>; hiperkalemi ve semptomatik hipokalsemide intravenöz kullanılır, bağırsakta fosfat bağlama özelliği yoktur.",
  "aciklama": "Kronik böbrek hastalığında hiperfosfatemi tedavisinde kullanılan oral fosfor bağlayıcılar: kalsiyum içerenler (<b>kalsiyum asetat</b>, kalsiyum karbonat) ve kalsiyum içermeyenler (<b>sevelamer</b>, <b>lantanum karbonat</b>, sükroferrik oksihidroksit, magnezyum tuzları). <b>Kalsiyum glukonat</b> ise bir fosfor bağlayıcı değildir; parenteral kalsiyum replasmanı ve hiperkalemide membran stabilizasyonu amacıyla kullanılır."
 },
 {
  "brans": "Dahiliye",
  "soru": "I. Akut pulmoner emboli<br>II. Serebrovasküler olay<br>III. Anstabil anjina<br><br>Yukarıdaki klinik durumlardan hangisinde/hangilerinde elektrokardiyografide <mark class=\"cue\">ST segment yükselmesi</mark> görülür?",
  "siklar": [
   {
    "k": "A",
    "t": "Yalnız I"
   },
   {
    "k": "B",
    "t": "Yalnız II"
   },
   {
    "k": "C",
    "t": "I ve II"
   },
   {
    "k": "D",
    "t": "II ve III"
   },
   {
    "k": "E",
    "t": "I, II ve III"
   }
  ],
  "dogru": 2,
  "cue": "🎯 Bir tanesinin tanımı zaten “ST yükselmesiz” olmak üzerine kurulu; onu ele.",
  "ipucu": "Anstabil anjina, NSTEMI ile birlikte ST yükselmesiz akut koroner sendrom başlığı altında yer alır.",
  "tuzak": "<mark>Anstabil anjinada ST yükselmesi görülmez</mark>; ST depresyonu veya T negatifliği beklenir. Buna karşın koroner dışı nedenler (PE'de sağ prekordiyal derivasyonlar, SVO'da özellikle subaraknoid kanamada) ST yükselmesi yapabilir — “ST elevasyonu = MI” refleksi bu soruda tuzaktır.",
  "aciklama": "<b>Akut pulmoner emboli</b>de sağ ventrikül gerilimine bağlı olarak V1-V3'te ST yükselmesi, S1Q3T3 paterni, sağ dal bloğu ve sinüs taşikardisi görülebilir. <b>Serebrovasküler olayda</b> (özellikle subaraknoid kanama) masif katekolamin deşarjına bağlı nörojenik ST-T değişiklikleri, uzun QT ve derin T negatifliği ile birlikte ST yükselmesi izlenebilir. <b>Anstabil anjina</b> ise tanımı gereği ST yükselmesiz akut koroner sendromdur."
 },
 {
  "brans": "Dahiliye",
  "soru": "Elli altı yaşında kadın hasta 5 gündür devam eden ve giderek artan nefes darlığı ile başvuruyor. Öyküsünden <b>meme kanseri</b> nedeniyle opere edildiği, adjuvan kemoterapi aldığı öğreniliyor. Ateş 36,5 °C, nabız 130/dk, kan basıncı 80/65 mmHg. <mark class=\"cue\">Bilateral juguler venöz dolgunluk</mark> saptanıyor. Akciğer sesleri normal. Akciğer grafisinde <b>kardiyomegali</b> gözlenirken plevral efüzyon ve infiltrasyon saptanmıyor.<br><br>Bu hastada en olası tanı aşağıdakilerden hangisidir?",
  "siklar": [
   {
    "k": "A",
    "t": "Vena kava superior sendromu"
   },
   {
    "k": "B",
    "t": "Pnömotoraks"
   },
   {
    "k": "C",
    "t": "Pulmoner emboli"
   },
   {
    "k": "D",
    "t": "Perikardiyal tamponad"
   },
   {
    "k": "E",
    "t": "Doksorubisine bağlı kardiyomiyopati"
   }
  ],
  "dogru": 3,
  "cue": "🎯 Hipotansiyon + boyun venlerinde dolgunluk + temiz akciğer üçlüsü hangi klasik triadı oluşturuyor?",
  "ipucu": "Beck triadı: hipotansiyon, juguler venöz dolgunluk ve derinden gelen kalp sesleri. Grafide su şişesi kalp görünümü eşlik eder.",
  "tuzak": "Meme kanseri öyküsü <mark>doksorubisin kardiyomiyopatisini</mark> akla getirir, ancak kardiyomiyopatide akciğerde konjesyon (raller, plevral efüzyon) beklenir — burada akciğer tamamen temiz. VKSS'de ise juguler dolgunluk <b>tek yönlü basınç artışıyla</b> birlikte yüz-boyun ödemi ve kollateral venler olur, hipotansiyon ve kardiyomegali tipik değildir.",
  "aciklama": "Meme kanseri perikardiyal metastazın en sık nedenlerindendir. Tabloda <b>Beck triadı</b> (hipotansiyon, juguler venöz dolgunluk, derinden gelen kalp sesleri) ile birlikte taşikardi, akciğerin temiz olması ve grafide kardiyomegali (su şişesi kalp) bulunması <b>perikardiyal tamponadı</b> düşündürür. Ayrıca pulsus paradoksus ve EKG'de düşük voltaj/elektriksel alternans görülebilir. Tanı ekokardiyografi ile konur, tedavi acil perikardiyosentezdir.",
  "ddx": {
   "baslik": "Ani Dispne + Juguler Venöz Dolgunluk",
   "ok": "Akciğer sesleri ve kan basıncı iki temel ayırıcıdır; grafi tanıyı büyük ölçüde netleştirir.",
   "satirlar": [
    {
     "emo": "💧",
     "ad": "Perikardiyal tamponad",
     "bulgu": "<b>Beck triadı</b> + pulsus paradoksus. Akciğer <b>temiz</b>, grafide <b>su şişesi kalp</b>, EKG'de düşük voltaj/elektriksel alternans.",
     "hit": true
    },
    {
     "emo": "🫁",
     "ad": "Pulmoner emboli",
     "bulgu": "Ani dispne, plöretik ağrı, hipoksemi. Akciğer sesleri sıklıkla normal; grafi <b>normal</b> (kardiyomegali beklenmez), D-dimer yüksek."
    },
    {
     "emo": "🎈",
     "ad": "Tansiyon pnömotoraks",
     "bulgu": "<b>Tek taraflı</b> ses yokluğu, hipersonorite, trakeal deviasyon. Grafide kollabe akciğer."
    },
    {
     "emo": "🧣",
     "ad": "Vena kava superior sendromu",
     "bulgu": "Yüz-boyun ödemi, göğüs duvarında kollateral venler, pletore. <b>Hipotansiyon ve kardiyomegali yok</b>."
    },
    {
     "emo": "❤️",
     "ad": "Antrasiklin kardiyomiyopatisi",
     "bulgu": "Doza bağımlı dilate KMP. <b>Akciğerde konjesyon</b>, raller, plevral efüzyon, S3 galo."
    }
   ]
  }
 },
 {
  "brans": "Dahiliye",
  "soru": "I. Valsalva manevrası<br>II. Trendelenburg pozisyonu<br>III. Çömelme<br>IV. Yumruk sıkma<br><br><b>Hipertrofik kardiyomiyopati</b> tanılı hastada yukarıdaki manevralardan hangisinde/hangilerinde <mark class=\"cue\">kardiyak üfürümün artması</mark> beklenir?",
  "siklar": [
   {
    "k": "A",
    "t": "Yalnız I"
   },
   {
    "k": "B",
    "t": "I ve II"
   },
   {
    "k": "C",
    "t": "II ve III"
   },
   {
    "k": "D",
    "t": "III ve IV"
   },
   {
    "k": "E",
    "t": "II, III ve IV"
   }
  ],
  "dogru": 0,
  "cue": "🎯 Bu üfürümün şiddeti sol ventrikül hacmiyle ters orantılı; hacmi AZALTAN manevrayı bul.",
  "ipucu": "HKMP'de obstrüksiyon, sol ventrikül boşluğu küçüldükçe ve afterload azaldıkça artar.",
  "tuzak": "Çoğu üfürümün aksine HKMP üfürümü <mark>ön yükü artıran manevralarda AZALIR</mark>. Trendelenburg (bacak kaldırma) ve çömelme venöz dönüşü artırır, yumruk sıkma ise afterload'u artırır — üçü de ventrikülü doldurup obstrüksiyonu azaltır, üfürüm hafifler.",
  "aciklama": "Hipertrofik obstrüktif kardiyomiyopatide üfürüm, sol ventrikül çıkım yolu obstrüksiyonundan kaynaklanır ve <b>ventrikül hacmi azaldıkça artar</b>. <b>Valsalva manevrasının ıkınma fazı</b> intratorasik basıncı artırıp venöz dönüşü azaltır; ventrikül küçülür ve üfürüm <b>şiddetlenir</b> (ayağa kalkma da aynı etkiyi yapar). Trendelenburg pozisyonu ve çömelme ön yükü, yumruk sıkma ise ard yükü artırarak üfürümü azaltır. Aynı mantık mitral valv prolapsusu için de geçerlidir."
 },
 {
  "brans": "Dahiliye",
  "soru": "Aşağıdakilerden hangisi <b>mitral stenozda</b> duyulan <mark class=\"cue\">“Durozie ritmi”</mark> komponentlerinden biri <b>değildir</b>?",
  "siklar": [
   {
    "k": "A",
    "t": "Presistolik şiddetlenme"
   },
   {
    "k": "B",
    "t": "Açılma sesi (opening snap)"
   },
   {
    "k": "C",
    "t": "S1 şiddetlenmesi"
   },
   {
    "k": "D",
    "t": "Geç sistolik üfürüm"
   },
   {
    "k": "E",
    "t": "Mid-diyastolik rulman"
   }
  ],
  "dogru": 3,
  "cue": "🎯 Mitral stenoz bir diyastolik kapak hastalığı; sistolde bir bulgu üretmesi beklenir mi?",
  "ipucu": "Durozie ritmi mitral stenozun dört bileşenli klasik oskültasyon bütünüdür ve tamamı diyastol ile S1'e aittir.",
  "tuzak": "<mark>Geç sistolik üfürüm mitral valv prolapsusuna aittir</mark> (mid-sistolik klik ile birlikte). Mitral stenozda sistolik üfürüm duyulması ancak eşlik eden bir yetmezlik ya da triküspit patolojisi varsa beklenir; Durozie ritminin parçası değildir.",
  "aciklama": "<b>Durozie ritmi</b>, mitral stenozun klasik oskültasyon bulgularının bütünüdür: <b>şiddetli S1</b>, <b>açılma sesi (opening snap)</b>, <b>mid-diyastolik rulman (yuvarlanma tarzı üfürüm)</b> ve sinüs ritmindeki hastalarda atriyal kontraksiyona bağlı <b>presistolik şiddetlenme</b>. Atriyal fibrilasyon gelişince presistolik şiddetlenme kaybolur. Açılma sesinin S2'ye yakınlaşması darlığın ağırlaştığını gösterir."
 },
 {
  "brans": "Dahiliye",
  "soru": "Aşağıdakilerden hangisi <b>astım kontrol skalasında</b> değerlendirilen parametrelerden biri <mark class=\"cue\">değildir</mark>?",
  "siklar": [
   {
    "k": "A",
    "t": "Gece semptomu varlığı"
   },
   {
    "k": "B",
    "t": "Kısa etkili beta-2 agonist kullanım sıklığı"
   },
   {
    "k": "C",
    "t": "Günlük aktivite"
   },
   {
    "k": "D",
    "t": "FEV1 düzeyi"
   },
   {
    "k": "E",
    "t": "Vücut kitle indeksi"
   }
  ],
  "dogru": 4,
  "cue": "🎯 Kontrol değerlendirmesi son 4 haftadaki semptomlara bakar; hangi seçenek semptomla ilgisi olmayan bir ölçüm?",
  "ipucu": "GINA'nın astım kontrol değerlendirmesinde dört soru vardır: gündüz semptomu, gece uyanması, kurtarıcı ilaç ihtiyacı ve aktivite kısıtlılığı.",
  "tuzak": "Obezite astım için bir <mark>risk faktörü ve kötü kontrol nedenidir</mark>, ancak kontrol skalasının bir parametresi değildir. Bu ayrım (risk faktörü ≠ kontrol parametresi) sorunun kilit noktasıdır.",
  "aciklama": "Astım <b>kontrol düzeyi</b> son 4 hafta içindeki dört ölçütle değerlendirilir: <b>gündüz semptomları</b> (haftada ikiden fazla), <b>gece semptomu/uyanma</b>, <b>kurtarıcı (kısa etkili beta-2 agonist) ihtiyacı</b> (haftada ikiden fazla) ve <b>aktivite kısıtlılığı</b>. Solunum fonksiyonu (FEV1) da değerlendirmeye dâhil edilir. <b>Vücut kitle indeksi</b> ise kontrol parametresi değil, kötü kontrolle ilişkili bir risk faktörüdür."
 },
 {
  "brans": "Dahiliye",
  "soru": "<b>Diffüz alveoler hemorajili</b> bir hastada <mark class=\"cue\">bronkoalveoler lavaj örneğinde</mark> görülmesi beklenen en olası bulgu aşağıdakilerden hangisidir?",
  "siklar": [
   {
    "k": "A",
    "t": "Eozinofil oranının %20'den fazla olması"
   },
   {
    "k": "B",
    "t": "Ferrüginöz cisimcik"
   },
   {
    "k": "C",
    "t": "Hemosiderin yüklü makrofajlar"
   },
   {
    "k": "D",
    "t": "CD4/CD8 oranında artışın eşlik ettiği lenfositoz"
   },
   {
    "k": "E",
    "t": "Süt benzeri görünüm ve köpüksü makrofajlar"
   }
  ],
  "dogru": 2,
  "cue": "🎯 Alveole dökülen kan birkaç gün içinde ne hâle gelir? Makrofajın içinde biriken pigmenti düşün.",
  "ipucu": "Alveollere geçen eritrositler makrofajlarca fagosite edilir ve hemoglobin demiri hemosiderine dönüşür (Prusya mavisi ile boyanır).",
  "tuzak": "Diğer seçeneklerin her biri <mark>başka bir hastalığın BAL imzasıdır</mark> ve bir arada verilerek karıştırma amaçlanmıştır. Ayrıca DAH'ta ardışık BAL örneklerinde kanlı görünümün <b>giderek koyulaşması</b> tanı koydurucudur — berraklaşması beklenmez.",
  "aciklama": "<b>Diffüz alveoler hemorajide</b> BAL'da ardışık alikotlarda giderek daha hemorajik sıvı gelir ve tipik olarak <b>hemosiderin yüklü makrofajlar</b> (siderofajlar) görülür; bunlar kanamanın 48-72 saatten eski olduğunu gösterir. Diğer BAL bulguları: eozinofil >%25 → akut/kronik eozinofilik pnömoni; <b>ferrüginöz (asbest) cisimcik</b> → asbestozis; <b>CD4/CD8 oranında artış ile lenfositoz</b> → sarkoidoz; <b>süt benzeri görünüm ve PAS(+) köpüksü materyal</b> → pulmoner alveoler proteinozis.",
  "ddx": {
   "baslik": "BAL Bulgusu → Hastalık",
   "ok": "BAL soruları neredeyse her zaman doğrudan eşleştirmedir; her bulgunun tek bir sahibi vardır.",
   "satirlar": [
    {
     "emo": "🩸",
     "ad": "Hemosiderin yüklü makrofaj",
     "bulgu": "<b>Diffüz alveoler hemoraji</b>. Ardışık alikotlarda koyulaşan hemorajik sıvı; ANCA vaskülitleri, Goodpasture, SLE.",
     "hit": true
    },
    {
     "emo": "🧬",
     "ad": "Lenfositoz + CD4/CD8 ↑",
     "bulgu": "<b>Sarkoidoz</b>. Oran >3,5 ise oldukça spesifik. Hipersensitivite pnömonisinde ise CD8 baskındır (oran düşer)."
    },
    {
     "emo": "🌸",
     "ad": "Eozinofil >%25",
     "bulgu": "<b>Eozinofilik pnömoni</b> (akut/kronik), ilaç reaksiyonu, ABPA, Churg-Strauss."
    },
    {
     "emo": "🪨",
     "ad": "Ferrüginöz cisimcik",
     "bulgu": "<b>Asbestozis</b>. Demir-protein kaplı asbest lifi; plevral plak ve mezotelyoma riski."
    },
    {
     "emo": "🥛",
     "ad": "Süt benzeri, PAS(+) materyal",
     "bulgu": "<b>Pulmoner alveoler proteinozis</b>. Anti-GM-CSF antikoru; tedavi tüm akciğer lavajı."
    }
   ]
  }
 },
 {
  "brans": "Dahiliye",
  "soru": "Aşağıdakilerden hangisi <b>KOAH gelişimi</b> için bir risk faktörü <mark class=\"cue\">değildir</mark>?",
  "siklar": [
   {
    "k": "A",
    "t": "Havayolu aşırı duyarlılığı"
   },
   {
    "k": "B",
    "t": "Kömür tozu maruziyeti"
   },
   {
    "k": "C",
    "t": "Pasif sigara dumanı maruziyeti"
   },
   {
    "k": "D",
    "t": "Yetişkinde rekürren solunum yolu enfeksiyonları"
   },
   {
    "k": "E",
    "t": "Biyokütle yakıtlarının kullanılması"
   }
  ],
  "dogru": 3,
  "cue": "🎯 Enfeksiyonların KOAH riski yarattığı dönem hangisi? Akciğer gelişiminin tamamlandığı yaşı düşün.",
  "ipucu": "KOAH riski, akciğerin ulaşabileceği en yüksek fonksiyon düzeyinin düşük kalmasıyla ilişkilidir; bu düzey ergenlik sonunda belirlenir.",
  "tuzak": "<mark>Çocuklukta geçirilen solunum yolu enfeksiyonları risk faktörüdür</mark> — akciğer gelişimini bozarak zirve akciğer fonksiyonunu düşürürler. Yetişkinde tekrarlayan enfeksiyonlar ise KOAH'ın <b>sonucu ve alevlenme nedenidir</b>, gelişim nedeni değildir; soru bu yön farkını sınamaktadır.",
  "aciklama": "KOAH risk faktörleri: sigara (aktif ve <b>pasif</b>), <b>biyokütle yakıtı</b> ve iç ortam hava kirliliği, mesleki maruziyetler (<b>kömür tozu</b>, silika, kadmiyum), alfa-1 antitripsin eksikliği, <b>havayolu aşırı duyarlılığı</b> (Dutch hipotezi), düşük sosyoekonomik düzey ve <b>çocuklukta geçirilen solunum yolu enfeksiyonları</b>. <b>Yetişkinde rekürren solunum yolu enfeksiyonu</b> ise mevcut KOAH'ın alevlenmesine yol açar, hastalığın gelişim nedeni değildir."
 },
 {
  "brans": "Dahiliye",
  "soru": "Hipertansiyon ve hipokalemi nedeni ile araştırılan bir hastada <mark class=\"cue\">renin düşük, aldosteron yüksek</mark> saptanıyor.<br><br>I. Salin infüzyon testi<br>II. Adrenal bilgisayarlı tomografi çekilmesi<br>III. Adrenal venöz örnekleme yapılması<br><br>Bu hastaya tanısal yaklaşımda yukarıdaki incelemelerin uygun sırası, aşağıdaki seçeneklerin hangisinde doğru olarak verilmiştir?",
  "siklar": [
   {
    "k": "A",
    "t": "II – III – I"
   },
   {
    "k": "B",
    "t": "I – II – III"
   },
   {
    "k": "C",
    "t": "II – I – III"
   },
   {
    "k": "D",
    "t": "I – III – II"
   },
   {
    "k": "E",
    "t": "III – II – I"
   }
  ],
  "dogru": 1,
  "cue": "🎯 Önce hastalığın var olduğunu kanıtla, sonra yerini bul, en son taraf tayini yap.",
  "ipucu": "Primer hiperaldosteronizmde algoritma üç aşamalıdır: tarama → doğrulama → lateralizasyon.",
  "tuzak": "<mark>Görüntülemeye doğrulama testinden önce geçilmemelidir.</mark> Adrenal insidentalomalar sıktır; BT'de nodül görmek aldosteronun oradan salgılandığını kanıtlamaz. Aynı şekilde adrenal venöz örnekleme en invaziv ve en son basamaktır.",
  "aciklama": "Düşük renin–yüksek aldosteron (yüksek ARO) primer hiperaldosteronizm için taramanın pozitif olduğunu gösterir. Sıra şöyledir: <b>1) Doğrulama</b> — aldosteron baskılanmasını gösteren <b>salin infüzyon testi</b> (veya oral tuz yükleme, fludrokortizon supresyon, kaptopril testi). <b>2) Görüntüleme</b> — <b>adrenal BT</b> ile adenom/hiperplazi ayrımı. <b>3) Lateralizasyon</b> — cerrahi düşünülen hastalarda <b>adrenal venöz örnekleme</b>, tek taraflı aşırı salgıyı kanıtlar. Doğru sıra I – II – III'tür."
 },
 {
  "brans": "Dahiliye",
  "soru": "Epilepsi tanısı nedeniyle 10 yıldır <b>antikonvülzan</b> kullanan 45 yaşında kadın hasta yaygın kemik ağrıları nedeni ile başvuruyor. Laboratuvarda 25-hidroksi vitamin D düşük, parathormon (PTH) yüksek, <mark class=\"cue\">kalsiyum ve fosfor düzeyi düşük</mark> saptanıyor.<br><br>Bu hastaya çekilen grafide aşağıdaki bulgulardan hangisinin görülme olasılığı en yüksektir?",
  "siklar": [
   {
    "k": "A",
    "t": "Brown tümörü"
   },
   {
    "k": "B",
    "t": "Osteitis fibroza sistika"
   },
   {
    "k": "C",
    "t": "Milkman fraktürü"
   },
   {
    "k": "D",
    "t": "Subperiostal resorpsiyon"
   },
   {
    "k": "E",
    "t": "Osteoporoz"
   }
  ],
  "dogru": 2,
  "cue": "🎯 PTH yüksek ama bu primer değil sekonder; asıl hastalık mineralizasyon kusuru. Ona özgü radyolojik bulguyu ara.",
  "ipucu": "Hem kalsiyumun hem fosforun düşük olması ve D vitamini eksikliği erişkinde osteomalaziyi gösterir. Osteomalazinin patognomonik radyolojik bulgusu nedir?",
  "tuzak": "PTH yüksekliğini görünce refleks olarak <mark>primer hiperparatiroidi bulguları</mark> (brown tümörü, osteitis fibroza sistika, subperiostal rezorpsiyon) seçilir. Ancak primer hiperparatiroidide kalsiyum <b>yüksek</b>, fosfor düşüktür; burada kalsiyum da düşük olduğu için tablo <b>sekonder</b> hiperparatiroididir.",
  "aciklama": "Fenitoin, fenobarbital ve karbamazepin gibi enzim indükleyici antikonvülzanlar D vitamini katabolizmasını hızlandırarak <b>osteomalaziye</b> yol açar. Laboratuvarda 25(OH)D düşük, kalsiyum ve fosfor düşük, ALP ve PTH yüksektir (sekonder hiperparatiroidi). Radyolojik olarak osteomalazinin karakteristik bulgusu <b>Looser zonları (psödofraktür / Milkman fraktürü)</b>dır: femur boynu, pubis kolları, skapula ve kaburgalarda kortekse dik uzanan bantlar. Tedavi D vitamini ve kalsiyum replasmanıdır.",
  "ddx": {
   "baslik": "Metabolik Kemik Hastalıklarında Laboratuvar",
   "ok": "Kalsiyum–fosfor–ALP–PTH dörtlüsünü birlikte oku; tanı bu tablodan çıkar.",
   "satirlar": [
    {
     "emo": "🦴",
     "ad": "Osteomalazi",
     "bulgu": "Ca <b>↓</b>, P ↓, ALP ↑, PTH ↑, 25(OH)D ↓. Grafide <b>Looser zonu / Milkman fraktürü</b>. Antikonvülzan, malabsorpsiyon, güneşsizlik.",
     "hit": true
    },
    {
     "emo": "🔺",
     "ad": "Primer hiperparatiroidi",
     "bulgu": "Ca <b>↑</b>, P ↓, ALP ↑, PTH ↑. <b>Subperiostal rezorpsiyon</b>, brown tümörü, osteitis fibroza sistika, tuz-biber kafatası."
    },
    {
     "emo": "🫘",
     "ad": "Sekonder hiperparatiroidi (KBH)",
     "bulgu": "Ca ↓/normal, P <b>↑</b>, PTH ↑↑. Renal osteodistrofi; fosfor <b>yüksektir</b> — osteomalaziden ayıran nokta."
    },
    {
     "emo": "🕸️",
     "ad": "Osteoporoz",
     "bulgu": "Ca, P, ALP, PTH <b>normal</b>. Kemik kütlesi azalmış ama mineralizasyon normal. Tanı DEXA ile."
    },
    {
     "emo": "🔥",
     "ad": "Paget hastalığı",
     "bulgu": "Ca ve P normal, <b>ALP çok yüksek</b>. Kemikte genişleme, pamuk yumağı görünümü, işitme kaybı."
    }
   ]
  }
 },
 {
  "brans": "Dahiliye",
  "soru": "Aşağıdaki <b>“tiroidit – ilişkili olduğu klinik tablo”</b> eşleştirmelerinden hangisi <mark class=\"cue\">yanlıştır</mark>?",
  "siklar": [
   {
    "k": "A",
    "t": "Hashimoto tiroiditi — hipotiroidi"
   },
   {
    "k": "B",
    "t": "Hashimoto tiroiditi — tirotoksikoz"
   },
   {
    "k": "C",
    "t": "Riedel tiroiditi — tirotoksikoz"
   },
   {
    "k": "D",
    "t": "Subakut tiroidit — hipotiroidi"
   },
   {
    "k": "E",
    "t": "Postpartum tiroidit — tirotoksikoz"
   }
  ],
  "dogru": 2,
  "cue": "🎯 Bir tiroidit bezi hormon salmak yerine taşa çevirir; onda geçici hormon fazlalığı olur mu?",
  "ipucu": "Destrüktif tiroiditlerde depolanmış hormonun kana boşalmasıyla geçici tirotoksikoz görülür. Hangi tiroiditte hasar destrüksiyon değil fibrozistir?",
  "tuzak": "Diğer dört eşleştirme <mark>ilk bakışta çelişkili görünse de doğrudur</mark>: Hashimoto hem başlangıçta geçici tirotoksikoz (hashitoksikoz) hem de kalıcı hipotiroidi yapabilir; subakut tiroidit tirotoksikoz fazından sonra hipotiroidi fazına geçer.",
  "aciklama": "<b>Riedel tiroiditi</b>, tiroid dokusunun yoğun fibröz doku ile yer değiştirdiği, IgG4 ilişkili hastalık spektrumunda yer alan nadir bir tiroidittir. Bez tahta sertliğinde, çevre dokulara yapışıktır; bası bulguları (disfaji, ses kısıklığı, stridor) ön plandadır ve ilerleyen olgularda <b>hipotiroidi</b> gelişir — <b>tirotoksikoz beklenmez</b>. Diğer eşleştirmeler doğrudur: Hashimoto'da hashitoksikoz ve sonrasında hipotiroidi, subakut (De Quervain) tiroiditte tirotoksikoz → hipotiroidi → ötiroidi seyri, postpartum tiroiditte ise önce tirotoksik faz görülür.",
  "ddx": {
   "baslik": "Tiroiditler",
   "ok": "Ağrılı mı ağrısız mı, RAİ tutulumu artmış mı azalmış mı — iki soru neredeyse tanıyı verir.",
   "satirlar": [
    {
     "emo": "❌",
     "ad": "Riedel tiroiditi",
     "bulgu": "Tahta sertliğinde bez, <b>fibrozis</b>, bası bulguları. IgG4 ilişkili. <b>Tirotoksikoz beklenmez</b> → eşleştirme yanlış.",
     "hit": true
    },
    {
     "emo": "🧊",
     "ad": "Hashimoto tiroiditi",
     "bulgu": "Ağrısız guatr, anti-TPO/anti-Tg (+). Başlangıçta <b>hashitoksikoz</b>, sonra kalıcı <b>hipotiroidi</b>."
    },
    {
     "emo": "🔥",
     "ad": "Subakut (De Quervain)",
     "bulgu": "<b>Ağrılı</b> tiroid, viral enfeksiyon sonrası, sedimentasyon çok yüksek, <b>RAİ tutulumu düşük</b>. Tirotoksikoz → hipotiroidi → ötiroidi."
    },
    {
     "emo": "🤱",
     "ad": "Postpartum tiroidit",
     "bulgu": "Doğumdan sonraki 1 yıl içinde, <b>ağrısız</b>. Tirotoksik faz → hipotiroid faz; genellikle düzelir, anti-TPO (+)."
    },
    {
     "emo": "🦠",
     "ad": "Süpüratif (akut) tiroidit",
     "bulgu": "Bakteriyel, <b>çok ağrılı</b>, ateş ve lökositoz. Tiroid fonksiyonları genellikle normaldir."
    }
   ]
  }
 },
 {
  "brans": "Dahiliye",
  "soru": "<b>Anti-nötrofilik sitoplazmik antikorların (ANCA)</b> hedef aldıkları antijenler aşağıdaki seçeneklerin hangisinde doğru eşleştirilmiştir?<br><br><b>Sıra → <mark class=\"cue\">p-ANCA · c-ANCA</mark></b>",
  "siklar": [
   {
    "k": "A",
    "t": "Sentromer · ds-DNA"
   },
   {
    "k": "B",
    "t": "Miyeloperoksidaz · Proteinaz-3"
   },
   {
    "k": "C",
    "t": "ds-DNA · Kardiyolipin"
   },
   {
    "k": "D",
    "t": "Miyeloperoksidaz · Sentromer"
   },
   {
    "k": "E",
    "t": "ss-DNA · Proteinaz-3"
   }
  ],
  "dogru": 1,
  "cue": "🎯 İki antijen de nötrofil granülünde; DNA ve sentromer içeren seçenekleri hemen ele.",
  "ipucu": "p = perinükleer boyanma, c = sitoplazmik boyanma. Her birinin tek bir hedef antijeni vardır.",
  "tuzak": "<mark>Sentromer, ds-DNA, ss-DNA ve kardiyolipin ANCA hedefi değildir</mark>: sentromer sınırlı sistemik sklerozun (CREST), ds-DNA SLE'nin, kardiyolipin ise antifosfolipid sendromunun antikorlarıdır. Karışıklık yaratmak için araya serpiştirilmişlerdir.",
  "aciklama": "<b>c-ANCA</b> sitoplazmik boyanma paterni gösterir ve hedefi <b>proteinaz-3 (PR3)</b>'tür; granülomatöz polianjiit (Wegener) ile güçlü ilişkilidir. <b>p-ANCA</b> perinükleer boyanma yapar ve hedefi <b>miyeloperoksidaz (MPO)</b>'dır; mikroskopik polianjiit ve eozinofilik granülomatöz polianjiit (Churg-Strauss) ile ilişkilidir. Bu vaskülitlerin ortak özelliği biyopside <b>immün kompleks birikiminin izlenmemesidir</b> (pauci-immün)."
 },
 {
  "brans": "Dahiliye",
  "soru": "Altmış yedi yaşındaki kadın hasta iki aydır yaygın ağrı ile başvuruyor. Ağrıların en fazla <mark class=\"cue\">boyun, omuz ve kalçalarda</mark> olduğunu söyleyen hasta; gece yatakta dönerken ağrı nedeniyle uyandığını ve ağrılarının öğleden sonra azaldığını ifade ediyor. Muayenede sistem bulguları normal, <b>eklemlerde şişlik saptanmıyor</b>, <b>kas kuvveti normal</b>, proksimal adalelerde hassasiyet tespit ediliyor.<br>Laboratuvarda hemoglobin 11 g/dL, sedimentasyon <b>76 mm/saat</b>, CRP 55 mg/L, romatoid faktör negatif, ANA negatif, idrar tetkiki normal.<br><br>Bu hasta için en olası tanı aşağıdakilerden hangisidir?",
  "siklar": [
   {
    "k": "A",
    "t": "Romatoid artrit"
   },
   {
    "k": "B",
    "t": "Spondiloartrit"
   },
   {
    "k": "C",
    "t": "Sistemik lupus eritematozus"
   },
   {
    "k": "D",
    "t": "Polimiyozit"
   },
   {
    "k": "E",
    "t": "Polimiyaljia romatika"
   }
  ],
  "dogru": 4,
  "cue": "🎯 Ağrı proksimal kaslarda ama kuvvet normal; bu iki bulgunun bir arada olması hangi tanıyı işaret eder?",
  "ipucu": "İleri yaş + omuz ve kalça kuşağında ağrı ve sabah tutukluğu + çok yüksek akut faz yanıtı + normal kas enzimleri.",
  "tuzak": "Proksimal kas tutulumu görünce <mark>polimiyozit</mark> seçilir; ancak polimiyozitte belirgin <b>kas güçsüzlüğü</b> ve CK yüksekliği olur — bu hastada kas kuvveti normaldir. Romatoid artritte ise sinovit/eklem şişliği bulunur, burada yok; RF ve ANA da negatiftir.",
  "aciklama": "<b>Polimiyaljia romatika</b>, 50 yaş üzerinde görülen, omuz ve pelvik kuşakta simetrik ağrı ve <b>sabah tutukluğu</b> (>45 dk) ile seyreden inflamatuvar bir hastalıktır. Kas kuvveti korunmuştur ve <b>CK normaldir</b>; sedimentasyon ve CRP belirgin yüksektir, normokrom normositer anemi eşlik edebilir. Düşük doz glukokortikoide (15-20 mg/gün prednizon) dramatik yanıt tanıyı destekler. Hastaların yaklaşık %15-20'sinde <b>dev hücreli arterit</b> eşlik ettiğinden baş ağrısı, çene kladikasyosu ve görme kaybı sorgulanmalıdır.",
  "ddx": {
   "baslik": "Yaygın Kas-İskelet Ağrısı Ayırımı",
   "ok": "Üç soru yeter: eklemde şişlik var mı, kas kuvveti düşük mü, akut faz yanıtı yüksek mi?",
   "satirlar": [
    {
     "emo": "🎯",
     "ad": "Polimiyaljia romatika",
     "bulgu": ">50 yaş, omuz-kalça kuşağı ağrısı, sabah tutukluğu. <b>Kuvvet normal, CK normal</b>, sedim/CRP çok yüksek. Steroide dramatik yanıt.",
     "hit": true
    },
    {
     "emo": "💪",
     "ad": "Polimiyozit",
     "bulgu": "<b>Simetrik proksimal kas güçsüzlüğü</b>, <b>CK yüksek</b>, EMG miyopatik, biyopside endomisyal inflamasyon."
    },
    {
     "emo": "🤲",
     "ad": "Romatoid artrit",
     "bulgu": "<b>Simetrik küçük eklem sinoviti</b> (MKF, PİF), şişlik ve eritem. RF ve anti-CCP genellikle pozitif, erozyon gelişir."
    },
    {
     "emo": "🦋",
     "ad": "SLE",
     "bulgu": "Genç kadın, <b>ANA pozitif</b>, döküntü, serozit, sitopeniler, böbrek tutulumu. İdrar tetkiki anormaldir."
    },
    {
     "emo": "🧍",
     "ad": "Spondiloartrit",
     "bulgu": "Genç erişkin, <b>inflamatuvar bel ağrısı</b>, sakroiliit, entezit, HLA-B27. Omuz-kalça kuşağı ağrısı ana bulgu değildir."
    }
   ]
  }
 },
 {
  "brans": "Dahiliye",
  "soru": "Siroz seyrinde görülen aşağıdaki komplikasyonlardan hangisinin <mark class=\"cue\">portal hipertansiyona bağlı olarak</mark> gelişmesi beklenmez?",
  "siklar": [
   {
    "k": "A",
    "t": "Asit"
   },
   {
    "k": "B",
    "t": "Trombositopeni"
   },
   {
    "k": "C",
    "t": "Spider anjiyom"
   },
   {
    "k": "D",
    "t": "Splenomegali"
   },
   {
    "k": "E",
    "t": "Özofagus varisleri"
   }
  ],
  "dogru": 2,
  "cue": "🎯 Basınç artışıyla mı, yoksa karaciğerin bir maddeyi yıkamamasıyla mı açıklanıyor? Ayrım burada.",
  "ipucu": "Sirozun bulguları iki gruba ayrılır: portal hipertansiyona bağlı olanlar ve hepatoselüler yetmezliğe (sentez/detoksifikasyon kaybı) bağlı olanlar.",
  "tuzak": "Sirozun bulguları hep bir arada görüldüğü için <mark>hepsi portal hipertansiyona bağlanır</mark>. Oysa spider anjiyom, palmar eritem ve jinekomasti <b>hepatoselüler yetmezliğe</b> bağlıdır: karaciğerin östrojeni yıkayamaması sonucu hiperestrojenemi gelişir.",
  "aciklama": "<b>Spider anjiyom</b>, palmar eritem, jinekomasti ve testis atrofisi karaciğerin <b>östrojen metabolizmasını yapamamasına</b> bağlı bulgulardır; portal hipertansiyonun sonucu değildir. Portal hipertansiyona bağlı gelişenler ise: <b>asit</b>, <b>splenomegali</b> ve buna bağlı hipersplenizm ile <b>trombositopeni</b>, <b>özofagus/mide varisleri</b>, kaput medusa ve hepatik hidrotoraks."
 },
 {
  "brans": "Dahiliye",
  "soru": "Aşağıdakilerden hangisi <mark class=\"cue\">ekstrahepatik kolestaz</mark> nedenlerinden biri <b>değildir</b>?",
  "siklar": [
   {
    "k": "A",
    "t": "Askaris enfeksiyonu"
   },
   {
    "k": "B",
    "t": "Primer sklerozan kolanjit"
   },
   {
    "k": "C",
    "t": "Kronik pankreatit"
   },
   {
    "k": "D",
    "t": "Mirizzi sendromu"
   },
   {
    "k": "E",
    "t": "Konjestif hepatopati"
   }
  ],
  "dogru": 4,
  "cue": "🎯 Ekstrahepatik kolestaz demek safra yolunun mekanik olarak tıkanması demek; hangisinde tıkanma değil, akım sorunu var?",
  "ipucu": "Ekstrahepatik nedenlerde büyük safra yollarında obstrüksiyon vardır ve görüntülemede safra yolları genişler.",
  "tuzak": "<mark>Primer sklerozan kolanjit hem intrahepatik hem ekstrahepatik</mark> safra yollarını tutar; “primer” kelimesine bakıp intrahepatik sanmak hatadır (intrahepatik ve tipik olarak duktopenik olan primer biliyer kolanjittir).",
  "aciklama": "<b>Konjestif hepatopati</b> (kardiyak siroz), sağ kalp yetmezliğine bağlı venöz konjesyondan kaynaklanır; safra yollarında mekanik tıkanma yoktur, dolayısıyla <b>intrahepatik</b> bir tablodur. Ekstrahepatik kolestaz nedenleri: koledok taşı, safra yolu ve pankreas başı tümörleri, <b>kronik pankreatit</b>, <b>Mirizzi sendromu</b> (sistik kanal taşının koledoka bası yapması), <b>primer sklerozan kolanjit</b>, biliyer striktür ve <b>Ascaris lumbricoides</b> gibi parazitlerin safra yoluna göçüdür."
 },
 {
  "brans": "Dahiliye",
  "soru": "Yirmi dokuz yaşında kadın hasta karın ağrısı ile başvuruyor. Ağrının farklı bölgelerde ve şiddette olduğu, daha çok ishal olmak üzere ishal ve kabızlık atakları yaşadığı öğreniliyor. Yemek ve stresin semptomlarını artırdığını, dışkılama ile rahatladığını ifade ediyor.<br>Laboratuvarda lökosit 8.000/mm³, <b>hematokrit %30</b>, trombosit 210.000/mm³, <b>sedimentasyon 54 mm/saat</b>. Dışkı örneğinde <mark class=\"cue\">laktoferrin pozitif</mark> olmasına rağmen kan görülmüyor.<br><br>Bu aşamada en uygun yaklaşım aşağıdakilerden hangisidir?",
  "siklar": [
   {
    "k": "A",
    "t": "Antidepresan ilaç başlanması"
   },
   {
    "k": "B",
    "t": "Antibiyotik verilmesi"
   },
   {
    "k": "C",
    "t": "Kolonoskopi yapılması"
   },
   {
    "k": "D",
    "t": "Psikolojik destek verilmesi"
   },
   {
    "k": "E",
    "t": "Antidiyareik ilaç verilmesi"
   }
  ],
  "dogru": 2,
  "cue": "🎯 Semptomlar fonksiyonel görünüyor ama laboratuvar öyle demiyor; üç alarm bulgusunu say.",
  "ipucu": "İrritabl bağırsak sendromu bir dışlama tanısıdır; alarm bulgusu varsa organik hastalık dışlanmadan bu tanı konulamaz.",
  "tuzak": "Öykü tam <mark>irritabl bağırsak sendromunu taklit ediyor</mark> (dışkılama ile rahatlama, stresle artma). Ancak <b>anemi, yüksek sedimentasyon ve dışkıda laktoferrin pozitifliği</b> alarm bulgularıdır ve mukozal inflamasyonu gösterir. Bu durumda semptomatik tedaviye geçmek yanlıştır.",
  "aciklama": "Hastada <b>anemi (Hct %30)</b>, <b>yüksek akut faz yanıtı (sedimentasyon 54)</b> ve <b>dışkıda laktoferrin pozitifliği</b> vardır. Laktoferrin nötrofil kaynaklı bir belirteçtir ve fekal kalprotektin gibi intestinal inflamasyonu gösterir; irritabl bağırsak sendromunda beklenmez. Bu alarm bulguları inflamatuvar bağırsak hastalığı başta olmak üzere organik patolojileri düşündürür ve en uygun yaklaşım <b>kolonoskopi ile mukozal değerlendirme ve biyopsi</b>dir."
 },
 {
  "brans": "Dahiliye",
  "soru": "<b>Alkol kullanımına bağlı tekrarlayan pankreatit</b> atakları olan hasta son altı aydır olan karın ağrısı ve ishal yakınması ile başvuruyor. Hasta dışkının <mark class=\"cue\">suda yüzdüğünü ve yapışkan olduğunu</mark> ifade ediyor.<br><br>Bu hastadaki en olası tanı düşünüldüğünde, aşağıdaki testlerden hangisinin bozulmuş olması <b>en az olasıdır</b>?",
  "siklar": [
   {
    "k": "A",
    "t": "Kalitatif yağ tayini"
   },
   {
    "k": "B",
    "t": "D-Ksiloz testi"
   },
   {
    "k": "C",
    "t": "Fekal elastaz testi"
   },
   {
    "k": "D",
    "t": "Bentiromid testi"
   },
   {
    "k": "E",
    "t": "Sekretin testi"
   }
  ],
  "dogru": 1,
  "cue": "🎯 Sorun enzimde mi, yoksa emen yüzeyde mi? Testlerden biri tamamen mukozayı ölçüyor.",
  "ipucu": "D-ksiloz emilimi pankreas enzimlerine ihtiyaç duymaz; doğrudan ince bağırsak mukozasının bütünlüğünü gösterir.",
  "tuzak": "Malabsorpsiyon testlerinin hepsi bir arada verilerek <mark>“hepsi bozulur” izlenimi</mark> yaratılmıştır. Oysa kronik pankreatit bir <b>maldigesyon</b> (sindirim) sorunudur, mukoza sağlamdır; D-ksiloz testi <b>normal</b> kalır. Bu test çölyak gibi mukozal hastalıklarda bozulur.",
  "aciklama": "Tablo <b>kronik pankreatite bağlı ekzokrin pankreas yetmezliği</b> ile uyumludur; steatore (suda yüzen, yağlı, yapışkan dışkı) tipiktir. Pankreas enzim eksikliğini gösteren testler bozulur: <b>kalitatif/kantitatif dışkı yağ tayini</b>, <b>fekal elastaz-1</b> (düşük), <b>bentiromid testi</b> (kimotripsin aktivitesi ölçer) ve <b>sekretin uyarı testi</b> (en duyarlı direkt test). <b>D-ksiloz testi</b> ise pasif emilen bir monosakkaritin ince bağırsak mukozasından emilimini ölçer; pankreas enzimlerinden bağımsız olduğu için kronik pankreatitte <b>normaldir</b>."
 },
 {
  "brans": "Dahiliye",
  "soru": "Aşağıdakilerden hangisi yaşlanma ile birlikte <b>üriner inkontinans</b> gelişme riskini artıran faktörler arasında <mark class=\"cue\">yer almaz</mark>? (BPH: Benign prostat hiperplazisi)",
  "siklar": [
   {
    "k": "A",
    "t": "Mesane kapasitesinde azalma"
   },
   {
    "k": "B",
    "t": "Menopoz sonucu üretral basınçta azalma"
   },
   {
    "k": "C",
    "t": "Multiparite sonucu pelvik kaslarda gevşeme"
   },
   {
    "k": "D",
    "t": "BPH sonucunda rezidüel volümde azalma"
   },
   {
    "k": "E",
    "t": "BPH sonucunda mesanede istemsiz kasılma"
   }
  ],
  "dogru": 3,
  "cue": "🎯 Bir seçenekteki değişimin yönü ters yazılmış; tıkanıklık artıkta ne yapar?",
  "ipucu": "Mesane çıkım tıkanıklığı, mesanenin tam boşalmasını engeller.",
  "tuzak": "Seçenek <mark>doğru mekanizmayı ters yönde</mark> vermektedir: BPH rezidüel volümü azaltmaz, <b>artırır</b>. Artan rezidüel volüm taşma inkontinansına yol açar. Aynı soruda BPH'nin diğer (doğru) etkisi de verilerek dikkat dağıtılmıştır.",
  "aciklama": "Yaşlanma ile inkontinans riskini artıran faktörler: <b>mesane kapasitesi ve kompliyansında azalma</b>, detrusor aşırı aktivitesi, <b>menopozda östrojen azalmasına bağlı üretral kapanma basıncının düşmesi</b> ve üretral atrofi, <b>multiparite ve pelvik taban kaslarında gevşeme</b>, ayrıca BPH'ye bağlı olarak <b>mesanede istemsiz (detrusor) kasılmalar</b> ile <b>rezidüel volümde ARTIŞ</b> ve taşma inkontinansı. Rezidüel volümün azalması ise inkontinans riskini artırmaz."
 }
];

/* ================= STATE ================= */
let order = QUESTIONS.map(function(_,i){return i;});
let idx = 0;
const answered = new Array(QUESTIONS.length).fill(null);
const starred  = new Array(QUESTIONS.length).fill(false);
const cueUsed  = new Array(QUESTIONS.length).fill(false);
let finished = false;

/* ================= PERSISTENCE (localStorage) ================= */
const STORAGE_KEY = 'tusquiz::' + (document.title || 'quiz') + '::' + QUESTIONS.length;
function saveState(){
  try{
    localStorage.setItem(STORAGE_KEY, JSON.stringify({
      answered:answered, starred:starred, idx:idx, order:order, finished:finished, v:1
    }));
  }catch(e){}
}
function loadSavedState(){
  try{ const r=localStorage.getItem(STORAGE_KEY); return r?JSON.parse(r):null; }catch(e){ return null; }
}
function clearSavedState(){ try{ localStorage.removeItem(STORAGE_KEY); }catch(e){} }
function hasProgress(s){
  if(!s) return false;
  const a = s.answered && s.answered.some(function(x){return x!==null;});
  return a || (s.idx>0) || s.finished;
}
function applyState(s){
  for(let i=0;i<QUESTIONS.length;i++){
    answered[i] = (s.answered && i<s.answered.length && s.answered[i]!==undefined) ? s.answered[i] : null;
    starred[i]  = (s.starred  && i<s.starred.length)  ? !!s.starred[i] : false;
  }
  order = (s.order && s.order.length) ? s.order.slice() : QUESTIONS.map(function(_,i){return i;});
  idx = (typeof s.idx==='number') ? Math.max(0,Math.min(order.length-1,s.idx)) : 0;
  finished = !!s.finished;
}

function qid(){ return order[idx]; }
function curQ(){ return QUESTIONS[order[idx]]; }

/* ========== HEADER SPACING (JS-measured) ========== */
const hdr = document.getElementById('hdr');
const main = document.getElementById('main');
function syncHeader(){
  const h = hdr.offsetHeight;
  main.style.paddingTop = (h + 14) + 'px';
  document.documentElement.style.setProperty('--hdrH', h + 'px');
}
window.addEventListener('load', syncHeader);
window.addEventListener('resize', syncHeader);
syncHeader();

/* ================= RENDER ================= */
const quizEl = document.getElementById('quiz');
const resultEl = document.getElementById('result');
const navEl = document.getElementById('nav');

function render(){
  if(finished){ renderResult(); return; }
  resultEl.classList.remove('show');
  quizEl.style.display='block';
  navEl.style.display='flex';

  const q = curQ();
  const id = qid();
  const chosen = answered[id];
  const isAns = chosen !== null;

  let html = '';
  html += '<div class="qmeta">';
  html += '<div class="qnum">SORU '+(idx+1)+' / '+order.length+'</div>';
  html += '<button class="star-btn '+(starred[id]?'on':'')+'" onclick="toggleStar()" aria-label="Yıldızla">⭐</button>';
  html += '</div>';

  if((q.yil && q.yil.length) || q.brans){
    html += '<div class="year-tags">';
    if(q.brans){ html += '<span class="brans-tag">'+q.brans+'</span>'; }
    if(q.yil){ q.yil.forEach(function(y){ html += '<span class="year-tag">'+y+'</span>'; }); }
    html += '</div>';
  }

  html += '<div class="qcard'+(q.ddx?' has-ddx':'')+'"'+(q.ddx?' onclick="openDdx(event)"':'')+'>'+q.soru
        + (q.ddx?'<span class="ddx-ok"><svg viewBox="0 0 24 24"><path d="M17 4l3 3-3 3"/><path d="M20 7H8a4 4 0 0 0-4 4"/><path d="M7 20l-3-3 3-3"/><path d="M4 17h12a4 4 0 0 0 4-4"/></svg></span>':'')
        + '</div>';

  html += '<div class="opts '+(isAns?'locked':'')+'" id="opts">';
  q.siklar.forEach(function(s,i){
    let cls='opt';
    if(isAns){
      if(i===q.dogru) cls+=' correct';
      else if(i===chosen) cls+=' wrong';
      else cls+=' dim';
    }
    html += '<button class="'+cls+'" '+(isAns?'':'onclick="answer('+i+')"')+'>'
          + '<span class="k">'+s.k+'</span><span class="t">'+s.t+'</span><span class="mark"></span></button>';
  });
  html += '</div>';

  if(!isAns){
    html += '<button class="hintbtn" id="preHint" onclick="showPreHint()">💡 İpucu göster</button>';
    html += '<div id="revealZone"></div>';
  } else {
    html += '<div id="revealZone">'+revealHTML(q)+'</div>';
  }

  quizEl.innerHTML = html;

  document.getElementById('prevBtn').disabled = (idx===0);
  document.getElementById('nextBtn').textContent = (idx===order.length-1) ? 'Bitir ✓' : 'Sonraki →';
  document.getElementById('navCounter').textContent = (idx+1)+'/'+order.length;

  updateBars();
}

function ddxCardHTML(d){
  if(!d) return '';
  var rows='';
  (d.satirlar||[]).forEach(function(r){
    rows += '<div class="dc'+(r.hit?' hit':'')+'">'
          + '<div class="emo">'+(r.emo||'🔹')+'</div>'
          + '<div class="txt"><div class="dn">'+r.ad+'</div><div class="dv">'+r.bulgu+'</div></div></div>';
  });
  return '<div class="ddx-card" onclick="closeDdx()">'
       + '<h3>🩺 '+(d.baslik||'Ayırıcı Tanı')+'</h3>'
       + (d.ok?'<div class="ddx-key">'+d.ok+'</div>':'')
       + '<div class="ddx-cards">'+rows+'</div></div>';
}
function openDdx(e){
  if(e){ e.stopPropagation(); }
  var q=curQ();
  if(!q.ddx) return;
  var ov=document.getElementById('ddxOv');
  if(ov.classList.contains('show')){ closeDdx(); return; }
  ov.classList.remove('closing');
  ov.innerHTML = ddxCardHTML(q.ddx);
  void ov.offsetWidth;
  ov.classList.add('show');
}
function closeDdx(){
  var ov=document.getElementById('ddxOv');
  if(!ov.classList.contains('show') || ov.classList.contains('closing')) return;
  ov.classList.add('closing');
  setTimeout(function(){ ov.classList.remove('show','closing'); ov.innerHTML=''; }, 430);
}

function revealHTML(q){
  return ''
   + '<div class="box ip"><div class="bt">💡 İPUCU</div><div>'+q.ipucu+'</div></div>'
   + '<div class="box tz"><div class="bt">⚠️ TUZAK</div><div>'+q.tuzak+'</div></div>'
   + '<div class="box ac"><div class="bt">📖 AÇIKLAMA</div><div>'+q.aciklama+'</div></div>';
}

function showPreHint(){
  const q = curQ();
  const btn = document.getElementById('preHint');
  if(btn) btn.style.display='none';
  document.getElementById('revealZone').innerHTML =
    '<div class="box ip"><div class="bt">💡 İPUCU</div><div>'+q.ipucu+'</div></div>';
  scrollToReveal();
}

/* ================= ACTIONS ================= */
function answer(i){
  const id = qid();
  if(answered[id]!==null) return;
  const q=curQ();

  // İlk yanlışta: cevabı vermeyen yeşil ipucu + kilit ifade parlaması, tek seferlik → tekrar dene
  if(i!==q.dogru && q.cue && !cueUsed[id]){
    cueUsed[id]=true;
    const m=document.getElementById('cueMsg');
    m.textContent=q.cue;
    m.classList.add('show');
    const qc=document.querySelector('.qcard');
    if(qc) qc.classList.add('flash');
    setTimeout(function(){ m.classList.remove('show'); if(qc) qc.classList.remove('flash'); },5000);
    return; // cevap KİLİTLENMEZ
  }

  answered[id]=i;

  const opts=document.getElementById('opts');
  opts.classList.add('locked');
  const btns=opts.querySelectorAll('.opt');
  btns.forEach(function(b,k){
    b.setAttribute('onclick','');
    if(k===q.dogru) b.classList.add('correct');
    else if(k===i) b.classList.add('wrong');
    else b.classList.add('dim');
  });

  const pre=document.getElementById('preHint');
  if(pre) pre.style.display='none';

  document.getElementById('revealZone').innerHTML = revealHTML(q);
  updateBars();
  saveState();
  if(i === q.dogru){ celebrate(btns[q.dogru]); } else { commiserate(); }
  scrollToReveal();
}

function scrollToReveal(){
  requestAnimationFrame(function(){
    const zone=document.getElementById('revealZone');
    const first=zone && zone.firstElementChild;
    if(!first) return;
    const offset = hdr.offsetHeight + 10;
    const y = first.getBoundingClientRect().top + window.pageYOffset - offset;
    window.scrollTo({top:y, behavior:'smooth'});
  });
}

function toggleStar(){
  const id=qid();
  starred[id]=!starred[id];
  saveState();
  render();
}

function go(dir){
  if(dir===1 && idx===order.length-1){ finished=true; saveState(); render(); window.scrollTo({top:0,behavior:'smooth'}); return; }
  idx=Math.max(0,Math.min(order.length-1, idx+dir));
  saveState();
  render();
  window.scrollTo({top:0,behavior:'smooth'});
}

/* ================= MODAL ================= */
function openModal(){
  const grid=document.getElementById('qGrid');
  let h='';
  let lastB=null;
  order.forEach(function(id,p){
    const b=QUESTIONS[id].brans;
    if(b && b!==lastB){ h += '<div class="gsec">'+b+'</div>'; lastB=b; }
    let cls='gbtn';
    if(answered[id]!==null){ cls += (answered[id]===QUESTIONS[id].dogru)?' ok':' no'; }
    if(p===idx) cls+=' cur';
    if(starred[id]) cls+=' star';
    h += '<button class="'+cls+'" onclick="jump('+p+')">'+(p+1)+'</button>';
  });
  grid.innerHTML=h;
  document.getElementById('modalOv').classList.add('show');
  document.body.style.overflow='hidden';
}
function closeModal(){
  document.getElementById('modalOv').classList.remove('show');
  document.body.style.overflow='';
}
function modalBg(e){ if(e.target.id==='modalOv') closeModal(); }
function jump(p){ idx=p; finished=false; closeModal(); saveState(); render(); window.scrollTo({top:0,behavior:'smooth'}); }

/* ================= COUNTERS / PROGRESS ================= */
function correctCount(){
  let c=0;
  answered.forEach(function(a,i){ if(a!==null && a===QUESTIONS[i].dogru) c++; });
  return c;
}
function starCount(){ return starred.filter(Boolean).length; }
function updateBars(){
  document.getElementById('cCount').textContent = correctCount();
  document.getElementById('sCount').textContent = starCount();
  const pos = finished ? order.length : (idx+1);
  document.getElementById('bar').style.width = Math.round((pos/order.length)*100)+'%';
}

/* ================= RESULT ================= */
function renderResult(){
  quizEl.style.display='none';
  navEl.style.display='none';
  resultEl.classList.add('show');

  const total=order.length;
  let correct=0, wrong=0, blank=0, starHere=0;
  order.forEach(function(id){
    const a=answered[id];
    if(a===null) blank++;
    else if(a===QUESTIONS[id].dogru) correct++;
    else wrong++;
    if(starred[id]) starHere++;
  });
  const pct=Math.round((correct/total)*100);

  document.getElementById('scoreBig').textContent = correct+'/'+total;
  document.getElementById('pctLine').textContent = '%'+pct;
  document.getElementById('ring').style.setProperty('--pct', pct+'%');

  let fb;
  if(pct>=90) fb='Mükemmel! Bu konulara hâkimsin. 🎯';
  else if(pct>=70) fb='Çok iyi. Birkaç tuzak dışında sağlamsın. 👏';
  else if(pct>=50) fb='Fena değil; yanlışları ve tuzakları tekrar et. 📚';
  else fb='Bu blokları tekrar çalışmakta fayda var. Devam! 💪';
  document.getElementById('fbText').textContent = fb;

  document.getElementById('rStats').innerHTML =
      '<div class="rstat g">✓ Doğru '+correct+'</div>'
    + '<div class="rstat r">✗ Yanlış '+wrong+'</div>'
    + '<div class="rstat s">⭐ Yıldızlı '+starHere+'</div>';

  let rev='';
  order.forEach(function(id,p){
    const q=QUESTIONS[id];
    const a=answered[id];
    let badge, cls, label;
    if(a===null){ badge='–'; cls='blank'; label='Boş'; }
    else if(a===q.dogru){ badge='✓'; cls='ok'; label='Doğru'; }
    else { badge='✗'; cls='no'; label='Yanlış'; }
    const ds=q.siklar[q.dogru];
    rev += '<div class="rev" onclick="jump('+p+')">'
         + '<div class="badge '+cls+'">'+badge+'</div>'
         + '<div style="flex:1">'
         + '<div class="rq">Soru '+(p+1)+' — '+label+(starred[id]?' ⭐':'')+'</div>'
         + '<div class="ra">Doğru cevap: <b>'+ds.k+') '+ds.t+'</b></div>'
         + '</div></div>';
  });
  document.getElementById('reviewList').innerHTML = rev;

  // ---- BRANŞ DÖKÜMÜ ----
  const bMap={}; const bOrder=[];
  order.forEach(function(id){
    const b=QUESTIONS[id].brans; if(!b) return;
    if(!bMap[b]){ bMap[b]={d:0,t:0}; bOrder.push(b); }
    bMap[b].t++;
    if(answered[id]!==null && answered[id]===QUESTIONS[id].dogru) bMap[b].d++;
  });
  const bbEl=document.getElementById('bransBreak');
  const bbT=document.getElementById('bbTitle');
  if(bOrder.length){
    let bh='';
    bOrder.forEach(function(b){
      const o=bMap[b]; const bp=o.t?Math.round(o.d/o.t*100):0;
      bh += '<div class="bb-row'+(bp<50?' weak':'')+'">'
          + '<div class="bb-name">'+b+'</div>'
          + '<div class="bb-bar"><div class="bb-fill" style="width:'+bp+'%"></div></div>'
          + '<div class="bb-score">'+o.d+'/'+o.t+'</div></div>';
    });
    bbEl.innerHTML=bh; bbT.style.display='';
  } else { bbEl.innerHTML=''; bbT.style.display='none'; }

  document.getElementById('retryWrongBtn').disabled = (wrong===0);
  document.getElementById('retryStarBtn').disabled = (starCount()===0);
  setTimeout(function(){ finaleShow(pct); }, 250);

  updateBars();
}

/* ================= RETRY MODES ================= */
function startSubset(ids){
  fxStreak = 0;
  order = ids.slice();
  ids.forEach(function(id){ answered[id]=null; });
  idx=0; finished=false;
  saveState();
  render();
  window.scrollTo({top:0,behavior:'smooth'});
}
function restart(){
  fxStreak = 0;
  order = QUESTIONS.map(function(_,i){return i;});
  for(let i=0;i<QUESTIONS.length;i++){ answered[i]=null; }
  idx=0; finished=false;
  clearSavedState();
  render();
  window.scrollTo({top:0,behavior:'smooth'});
}
function retryWrong(){
  const ids = order.filter(function(id){ return answered[id]!==null && answered[id]!==QUESTIONS[id].dogru; });
  if(!ids.length){ toast('Yanlış soru yok 🎉'); return; }
  startSubset(ids);
}
function retryStar(){
  const ids = [];
  starred.forEach(function(s,i){ if(s) ids.push(i); });
  if(!ids.length){ toast('Yıldızlı soru yok ⭐'); return; }
  startSubset(ids);
}

/* ================= TOAST ================= */
let toastT=null;
function toast(msg){
  const el=document.getElementById('toast');
  el.textContent=msg; el.classList.add('show');
  clearTimeout(toastT);
  toastT=setTimeout(function(){ el.classList.remove('show'); },1800);
}

/* ================= RESUME ================= */
function showResumePrompt(saved){
  const ov = document.getElementById('resumeOv');
  const sub = document.getElementById('resumeSub');
  const ord = (saved.order && saved.order.length) ? saved.order : QUESTIONS.map(function(_,i){return i;});
  const total = ord.length;
  const pos = saved.finished ? total : Math.min((saved.idx||0)+1, total);
  const ansCount = saved.answered ? saved.answered.filter(function(x){return x!==null;}).length : 0;
  sub.textContent = saved.finished
    ? ('Testi bitirmiştin — sonuç ekranına dönebilirsin. (' + ansCount + ' soru işaretlenmiş)')
    : ('Soru ' + pos + ' / ' + total + ' — ' + ansCount + ' soru cevaplanmış.');
  window._savedState = saved;
  ov.classList.add('show');
}
function resumeYes(){
  applyState(window._savedState);
  document.getElementById('resumeOv').classList.remove('show');
  render();
  window.scrollTo({top:0,behavior:'smooth'});
}
function resumeNo(){
  clearSavedState();
  document.getElementById('resumeOv').classList.remove('show');
  render();
}


/* ================= EĞLENCE MOTORU ================= */
const fxCanvas = document.createElement('canvas');
fxCanvas.id = 'fxCanvas';
document.body.appendChild(fxCanvas);
const fxCtx = fxCanvas.getContext('2d');
let fxParts = [], fxRaf = null;

function fxResize(){
  fxCanvas.width = window.innerWidth;
  fxCanvas.height = window.innerHeight;
}
window.addEventListener('resize', fxResize);
fxResize();

const FX_COLORS = ['#4c9aff','#7c5cff','#2ea043','#f5c451','#ff5b5b','#3fb6a8','#ffffff','#ff9de2'];

function confettiBurst(n, originY){
  const oy = (typeof originY === 'number') ? originY : window.innerHeight * 0.38;
  for(let i=0;i<n;i++){
    fxParts.push({
      x: window.innerWidth/2 + (Math.random()-0.5)*160,
      y: oy,
      vx: (Math.random()-0.5)*13,
      vy: Math.random()*-13 - 4,
      g: 0.34,
      w: Math.random()*8 + 5,
      h: Math.random()*5 + 3,
      c: FX_COLORS[Math.floor(Math.random()*FX_COLORS.length)],
      rot: Math.random()*6.28,
      vr: (Math.random()-0.5)*0.35,
      life: 130
    });
  }
  if(!fxRaf) fxRaf = requestAnimationFrame(fxTick);
}

function fxTick(){
  fxCtx.clearRect(0,0,fxCanvas.width,fxCanvas.height);
  fxParts = fxParts.filter(function(p){ return p.life > 0 && p.y < window.innerHeight + 60; });
  fxParts.forEach(function(p){
    p.x += p.vx; p.y += p.vy; p.vy += p.g; p.vx *= 0.995;
    p.rot += p.vr; p.life--;
    fxCtx.save();
    fxCtx.translate(p.x, p.y);
    fxCtx.rotate(p.rot);
    fxCtx.globalAlpha = Math.max(0, Math.min(1, p.life/45));
    fxCtx.fillStyle = p.c;
    fxCtx.fillRect(-p.w/2, -p.h/2, p.w, p.h);
    fxCtx.restore();
  });
  if(fxParts.length){ fxRaf = requestAnimationFrame(fxTick); }
  else { fxRaf = null; fxCtx.clearRect(0,0,fxCanvas.width,fxCanvas.height); }
}

function emojiFloat(list, count){
  for(let i=0;i<count;i++){
    const e = document.createElement('div');
    e.className = 'emoji-pop';
    e.textContent = list[Math.floor(Math.random()*list.length)];
    e.style.left = (window.innerWidth/2 + (Math.random()-0.5)*240) + 'px';
    e.style.top  = (window.innerHeight*0.58) + 'px';
    e.style.setProperty('--dx', ((Math.random()-0.5)*140) + 'px');
    e.style.setProperty('--rot', ((Math.random()-0.5)*90) + 'deg');
    e.style.animationDelay = (Math.random()*0.28) + 's';
    document.body.appendChild(e);
    setTimeout(function(){ if(e.parentNode) e.remove(); }, 2200);
  }
}

function emojiRain(list, count){
  for(let i=0;i<count;i++){
    const e = document.createElement('div');
    e.className = 'emoji-drop';
    e.textContent = list[Math.floor(Math.random()*list.length)];
    e.style.left = (window.innerWidth*0.15 + Math.random()*window.innerWidth*0.7) + 'px';
    e.style.top  = (window.innerHeight*0.30) + 'px';
    e.style.setProperty('--rot', ((Math.random()-0.5)*70) + 'deg');
    e.style.animationDelay = (Math.random()*0.25) + 's';
    document.body.appendChild(e);
    setTimeout(function(){ if(e.parentNode) e.remove(); }, 2000);
  }
}

const GOOD_EMO = ['🎉','🥳','😄','👏','⭐','💪','🔥','✨','🏆','😎','💚','🩺'];
const BAD_EMO  = ['😢','😞','💔','😵','🙈','😬','🥲'];
const MASCOTS  = ['🐵','🦉','🐣','🦊','🐼','🚀'];

const GOOD_MSG = ['Harika! 🎉','Bravo! 👏','Tam isabet! 🎯','Süpersin! 🥳','İşte bu! 💪',
                  'Mükemmel! ⭐','Doğru cevap! 🔥','Efsanesin! 🏆','Aferin doktor! 🩺',
                  'Nefes kesici! 😮‍💨','Çok iyisin! 💚'];
const BAD_MSG  = ['Olsun, tekrar bakalım 💪','Tuzağa düştün ⚠️','Yanlış ama öğrendik 📚',
                  'Boş ver, devam! 🙌','Bir dahakine 😉','Not al, unutma 📝',
                  'Açıklamayı oku, kaçırma 👀','Nefesini topla, devam 🫁'];
const STREAK_MSG = {3:'🔥 3 ÜST ÜSTE!',5:'⚡ 5 SERİ! HARİKA!',8:'🏆 8 SERİ! EFSANE!',
                    10:'👑 10 SERİ! ŞAMPİYON!',15:'🚀 15 SERİ! DURDURULAMAZ!',
                    20:'🌟 20 SERİ! İNANILMAZ!'};

let fxStreak = 0;

function showStreak(msg){
  const s = document.createElement('div');
  s.className = 'streak';
  s.textContent = msg;
  document.body.appendChild(s);
  setTimeout(function(){ if(s.parentNode) s.remove(); }, 1700);
}

let fxMsgT = null;
function showInlineMsg(msg, ok){
  const zone = document.getElementById('revealZone');
  if(!zone) return;
  const old = zone.querySelector('.fxfloat');
  if(old) old.remove();
  clearTimeout(fxMsgT);
  const wrap = document.createElement('div');
  wrap.className = 'fxfloat';
  const pill = document.createElement('div');
  pill.className = 'pill ' + (ok ? 'good' : 'bad');
  pill.textContent = msg;
  wrap.appendChild(pill);
  zone.insertBefore(wrap, zone.firstChild);
  fxMsgT = setTimeout(function(){ if(wrap.parentNode) wrap.remove(); }, 2100);
}

function celebrate(btn){
  confettiBurst(95);
  emojiFloat(GOOD_EMO, 8);
  showInlineMsg(GOOD_MSG[Math.floor(Math.random()*GOOD_MSG.length)], true);
  if(btn){
    const m = document.createElement('span');
    m.className = 'mascot';
    m.textContent = MASCOTS[Math.floor(Math.random()*MASCOTS.length)];
    btn.style.position = 'relative';
    btn.appendChild(m);
  }
  fxStreak++;
  if(STREAK_MSG[fxStreak]){
    showStreak(STREAK_MSG[fxStreak]);
    setTimeout(function(){ confettiBurst(70, window.innerHeight*0.30); }, 220);
  }
  try{ if(navigator.vibrate) navigator.vibrate(35); }catch(e){}
}

function commiserate(){
  const m = document.getElementById('main');
  if(m){
    m.classList.remove('shake');
    void m.offsetWidth;
    m.classList.add('shake');
    setTimeout(function(){ m.classList.remove('shake'); }, 700);
  }
  emojiRain(BAD_EMO, 6);
  showInlineMsg(BAD_MSG[Math.floor(Math.random()*BAD_MSG.length)], false);
  fxStreak = 0;
  try{ if(navigator.vibrate) navigator.vibrate([60,50,60,50,50]); }catch(e){}
}

function finaleShow(pct){
  if(pct >= 90){
    [0,300,600,900].forEach(function(d){
      setTimeout(function(){ confettiBurst(110, window.innerHeight*0.30); }, d);
    });
    emojiFloat(['🏆','👑','🎉','🥳','⭐'], 12);
  } else if(pct >= 70){
    confettiBurst(110, window.innerHeight*0.32);
    setTimeout(function(){ confettiBurst(80, window.innerHeight*0.30); }, 350);
    emojiFloat(GOOD_EMO, 8);
  } else if(pct >= 50){
    confettiBurst(60, window.innerHeight*0.34);
    emojiFloat(['💪','📚','✨'], 5);
  } else {
    emojiFloat(['📚','💪','🩺'], 4);
  }
}

/* ================= INIT ================= */
render();
window.addEventListener('pagehide', function(){ try{ saveState(); }catch(e){} });
window.addEventListener('visibilitychange', function(){ if(document.visibilityState==='hidden'){ try{ saveState(); }catch(e){} } });
(function(){ const s=loadSavedState(); if(hasProgress(s)) showResumePrompt(s); })();
window.addEventListener('load', function(){ syncHeader(); updateBars(); });

/* nav focus fix */
try{['prevBtn','listBtn','nextBtn'].forEach(function(id){var el=document.getElementById(id);if(el){el.addEventListener('mousedown',function(e){e.preventDefault();});el.addEventListener('focus',function(){var s=this;setTimeout(function(){try{s.blur();}catch(e){}},0);});el.addEventListener('click',function(){var s=this;setTimeout(function(){try{s.blur();}catch(e){}},0);});}});}catch(e){}
</script>
</body>
</html>
