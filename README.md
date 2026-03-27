<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>POLYVERSE — Blender Assets & Worlds</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Crimson+Pro:ital,wght@0,300;0,400;0,600;1,300;1,400&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --gold:#C9A84C;--gold-l:#E8C97A;--gold-d:#7A6130;--gold-bg:rgba(201,168,76,.07);
  --void:#060608;--void2:#0C0C0F;--void3:#111116;--void4:#16161C;
  --surf:#1A1A22;--surf2:#202028;
  --txt:#F0EDE6;--txt2:#9A9088;--txt3:#4E4A46;
  --acc:#7C5CBF;--acc2:#9B7DE0;
  --bdr:rgba(201,168,76,.13);--bdr2:rgba(201,168,76,.28);
  --red:#CF4B4B;--green:#4B9E6B;--blue:#4B7FCF;
  --fd:'Bebas Neue',sans-serif;
  --fb:'Crimson Pro',serif;
  --fm:'JetBrains Mono',monospace;
  --r:8px;--rl:14px;--rxl:22px;
}
html{scroll-behavior:smooth}
body{background:var(--void);color:var(--txt);font-family:var(--fb);font-size:17px;line-height:1.65;min-height:100vh;overflow-x:hidden;cursor:none}
::-webkit-scrollbar{width:2px}::-webkit-scrollbar-track{background:var(--void)}::-webkit-scrollbar-thumb{background:var(--gold-d)}

/* ══════════════════════════════════════
   INTRO ANIMATION
══════════════════════════════════════ */
#intro{
  position:fixed;inset:0;z-index:10000;
  background:var(--void);
  display:flex;align-items:center;justify-content:center;
  flex-direction:column;
  pointer-events:all;
}
#intro.done{pointer-events:none}
.intro-svg-wrap{
  position:relative;
  width:180px;height:180px;
  display:flex;align-items:center;justify-content:center;
}
.intro-rings{
  position:absolute;inset:0;
}
.intro-ring{
  position:absolute;border-radius:50%;border:1px solid;
  animation:ring-spin linear infinite;
  top:50%;left:50%;transform-origin:0 0;
}
.ir1{width:80px;height:80px;margin:-40px 0 0 -40px;border-color:rgba(201,168,76,.8);animation-duration:4s}
.ir2{width:120px;height:120px;margin:-60px 0 0 -60px;border-color:rgba(201,168,76,.4);animation-duration:7s;animation-direction:reverse}
.ir3{width:160px;height:160px;margin:-80px 0 0 -80px;border-color:rgba(124,92,191,.5);animation-duration:10s}
.ir4{width:200px;height:200px;margin:-100px 0 0 -100px;border-color:rgba(201,168,76,.15);animation-duration:15s;animation-direction:reverse}
@keyframes ring-spin{from{transform:rotate(0deg) translate(0,-50%) rotate(0deg)}to{transform:rotate(360deg) translate(0,-50%) rotate(-360deg)}}
/* Override — simple rotation */
.intro-ring{animation:simple-spin linear infinite}
.ir1{animation-duration:4s}
.ir2{animation-duration:7s;animation-direction:reverse}
.ir3{animation-duration:10s}
.ir4{animation-duration:15s;animation-direction:reverse}
@keyframes simple-spin{from{transform:translate(-50%,-50%) rotate(0deg)}to{transform:translate(-50%,-50%) rotate(360deg)}}
.intro-logo-center{
  position:relative;z-index:2;
  display:flex;align-items:center;justify-content:center;
}
.intro-hex{
  width:72px;height:72px;
  animation:hex-pulse 2s ease-in-out infinite;
}
@keyframes hex-pulse{0%,100%{opacity:.7;transform:scale(.95)}50%{opacity:1;transform:scale(1.05)}}
.intro-text{
  margin-top:28px;
  font-family:var(--fd);font-size:32px;letter-spacing:8px;color:var(--gold);
  animation:intro-txt-blink 1.2s ease-in-out infinite;
  text-align:center;
}
@keyframes intro-txt-blink{0%,100%{opacity:.4}50%{opacity:1}}
.intro-bar-wrap{
  margin-top:24px;width:160px;height:2px;background:rgba(201,168,76,.15);border-radius:2px;overflow:hidden;
}
.intro-bar{height:100%;width:0%;background:var(--gold);border-radius:2px;transition:width .05s linear}
.intro-sub{
  margin-top:12px;font-family:var(--fm);font-size:10px;letter-spacing:3px;color:var(--txt3);text-transform:uppercase;
}

/* Fade out intro */
#intro.fadeout{
  animation:intro-fadeout .8s ease-out forwards;
}
@keyframes intro-fadeout{to{opacity:0;transform:scale(1.04)}}

/* CURSOR */
#cur,#cur2{position:fixed;border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%)}
#cur{width:6px;height:6px;background:var(--gold);box-shadow:0 0 8px var(--gold);transition:width .15s,height .15s,background .2s}
#cur2{width:26px;height:26px;border:1px solid rgba(201,168,76,.5);opacity:.6;transition:all .25s ease-out}
body:hover #cur{opacity:1}

/* PAGES */
.page{display:none;min-height:100vh}
.page.active{display:block}

/* ══════════════════════════════════════
   NAV
══════════════════════════════════════ */
#nav{position:fixed;top:0;left:0;right:0;z-index:200;display:flex;align-items:center;justify-content:space-between;padding:14px 40px;transition:all .3s}
#nav.scrolled{background:rgba(6,6,8,.96);border-bottom:1px solid var(--bdr);backdrop-filter:blur(20px)}
.nav-logo-wrap{display:flex;align-items:center;gap:10px;cursor:pointer}
.nav-logo-svg{width:34px;height:34px;flex-shrink:0}
.nav-logo-txt{font-family:var(--fd);font-size:22px;letter-spacing:3px;color:var(--gold)}
.nav-mid{display:flex;gap:28px;list-style:none}
.nav-mid a{color:var(--txt2);text-decoration:none;font-family:var(--fm);font-size:11px;letter-spacing:1.5px;cursor:pointer;transition:color .2s;text-transform:uppercase}
.nav-mid a:hover{color:var(--gold)}
.nav-right{display:flex;gap:10px;align-items:center}

/* SEARCH BAR in nav */
.nav-search{
  display:flex;align-items:center;gap:0;
  background:var(--void3);border:1px solid var(--bdr);border-radius:var(--r);
  overflow:hidden;
}
.nav-search input{
  background:transparent;border:none;color:var(--txt);padding:7px 12px;
  font-family:var(--fm);font-size:11px;outline:none;width:180px;
  letter-spacing:.5px;
}
.nav-search input::placeholder{color:var(--txt3)}
.nav-search-btn{
  background:var(--gold-bg);border:none;border-left:1px solid var(--bdr);
  color:var(--gold);padding:7px 11px;cursor:pointer;transition:.2s;
  display:flex;align-items:center;
}
.nav-search-btn:hover{background:var(--gold);color:var(--void)}
.nav-search-btn svg{width:13px;height:13px}

/* BTN SYSTEM */
.btn{display:inline-flex;align-items:center;gap:7px;padding:9px 20px;border-radius:var(--r);font-family:var(--fm);font-size:12px;letter-spacing:.5px;cursor:pointer;transition:all .2s;border:none;text-decoration:none;white-space:nowrap}
.btn-gold{background:var(--gold);color:var(--void);font-weight:700}
.btn-gold:hover{background:var(--gold-l);transform:translateY(-1px);box-shadow:0 4px 20px rgba(201,168,76,.3)}
.btn-ghost{background:transparent;border:1px solid var(--bdr2);color:var(--gold)}
.btn-ghost:hover{background:var(--gold-bg)}
.btn-glass{background:rgba(255,255,255,.04);border:1px solid var(--bdr);color:var(--txt2)}
.btn-glass:hover{color:var(--txt);border-color:var(--bdr2)}
.btn-red{background:var(--red);color:#fff}.btn-red:hover{background:#e05555}
.btn-green{background:var(--green);color:#fff}.btn-green:hover{background:#5ab87d}
.btn-acc{background:var(--acc);color:#fff}.btn-acc:hover{background:var(--acc2)}
.btn-sm{padding:6px 14px;font-size:11px}
.btn-lg{padding:13px 32px;font-size:14px}
.btn-block{width:100%;justify-content:center}
.btn svg{width:14px;height:14px;flex-shrink:0}

/* ══════════════════════════════════════
   HERO
══════════════════════════════════════ */
#hero{min-height:100vh;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:120px 40px 80px;position:relative;overflow:hidden}
.h-grid{position:absolute;inset:0;
  background:linear-gradient(rgba(201,168,76,.025) 1px,transparent 1px),linear-gradient(90deg,rgba(201,168,76,.025) 1px,transparent 1px);
  background-size:60px 60px;
  mask-image:radial-gradient(ellipse 70% 70% at 50% 50%,#000 20%,transparent 100%)}
.h-particles{position:absolute;inset:0;pointer-events:none}
.ptcl{position:absolute;border-radius:50%;animation:pfloat var(--d) var(--dl) infinite ease-in-out alternate}
@keyframes pfloat{from{opacity:var(--oa);transform:translate(0,0)}to{opacity:var(--ob);transform:translate(var(--tx),var(--ty))}}

/* Hero geometric shapes */
.h-geo{position:absolute;pointer-events:none;opacity:.06}
.h-geo-1{top:15%;left:10%;width:200px;height:200px;border:1px solid var(--gold);border-radius:50%;animation:geo-rotate 20s linear infinite}
.h-geo-2{bottom:20%;right:8%;width:140px;height:140px;border:1px solid var(--acc);transform:rotate(45deg);animation:geo-rotate 15s linear infinite reverse}
.h-geo-3{top:40%;left:5%;width:60px;height:60px;background:var(--gold);border-radius:4px;animation:geo-rotate 8s linear infinite}
@keyframes geo-rotate{to{transform:rotate(360deg)}}
.h-geo-2{animation:geo-rotate2 15s linear infinite reverse}
@keyframes geo-rotate2{to{transform:rotate(45deg) rotate(360deg)}}

.h-eye{font-family:var(--fm);font-size:10px;letter-spacing:5px;color:var(--gold);text-transform:uppercase;margin-bottom:20px;animation:fadeup .8s .2s both;opacity:.8}
.h-title{font-family:var(--fd);font-size:clamp(72px,11vw,140px);line-height:.88;letter-spacing:4px;animation:fadeup .8s .4s both}
.h-title em{color:var(--gold);font-style:normal;position:relative}
.h-title em::after{content:'';position:absolute;bottom:-4px;left:0;right:0;height:2px;background:linear-gradient(90deg,var(--gold),transparent);border-radius:2px}
.h-sub{font-style:italic;font-size:clamp(17px,2.2vw,23px);color:var(--txt2);margin:24px 0 38px;animation:fadeup .8s .6s both;max-width:580px}
.h-cta{display:flex;gap:14px;justify-content:center;animation:fadeup .8s .8s both;flex-wrap:wrap}
.h-stats{display:flex;gap:52px;margin-top:72px;animation:fadeup .8s 1s both}
.stat .n{font-family:var(--fd);font-size:46px;color:var(--gold);line-height:1}
.stat .l{font-family:var(--fm);font-size:9px;color:var(--txt3);letter-spacing:3px;text-transform:uppercase;margin-top:4px}
.stat-divider{width:1px;background:var(--bdr);align-self:stretch;margin:4px 0}
@keyframes fadeup{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:none}}

/* ══════════════════════════════════════
   TICKER
══════════════════════════════════════ */
.ticker{background:linear-gradient(90deg,var(--gold-d),var(--gold),var(--gold-d));overflow:hidden;padding:8px 0}
.t-inner{display:flex;animation:tick 32s linear infinite}
.t-item{white-space:nowrap;font-family:var(--fd);font-size:12px;letter-spacing:2.5px;color:var(--void);padding:0 32px;display:flex;align-items:center;gap:12px}
@keyframes tick{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* ══════════════════════════════════════
   SECTION
══════════════════════════════════════ */
.sec{padding:90px 40px;max-width:1400px;margin:0 auto}
.sec-label{font-family:var(--fm);font-size:10px;letter-spacing:4px;color:var(--gold);text-transform:uppercase;margin-bottom:10px;display:flex;align-items:center;gap:10px}
.sec-label::before{content:'';width:24px;height:1px;background:var(--gold);opacity:.5}
.sec-title{font-family:var(--fd);font-size:clamp(40px,5.5vw,68px);letter-spacing:2px;line-height:1;margin-bottom:48px}
.sec-title em{color:var(--gold);font-style:normal}

/* SEARCH RESULTS BAR */
.search-bar-info{
  display:none;
  font-family:var(--fm);font-size:11px;color:var(--txt2);
  letter-spacing:.5px;margin-bottom:18px;
  padding:10px 14px;background:var(--gold-bg);border:1px solid var(--bdr);
  border-radius:var(--r);
  align-items:center;justify-content:space-between;
}
.search-bar-info.show{display:flex}

/* FILTER */
.filters{display:flex;gap:7px;flex-wrap:wrap;margin-bottom:28px}
.f-btn{background:transparent;border:1px solid var(--bdr);color:var(--txt2);padding:7px 18px;border-radius:var(--r);font-family:var(--fm);font-size:11px;letter-spacing:1px;cursor:pointer;transition:all .2s}
.f-btn:hover,.f-btn.on{background:var(--gold);color:var(--void);border-color:var(--gold)}

/* PRODUCT GRID */
.pgrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:22px}
.pcard{background:var(--surf);border:1px solid var(--bdr);border-radius:var(--rl);overflow:hidden;cursor:pointer;transition:all .3s}
.pcard:hover{border-color:var(--bdr2);transform:translateY(-5px);box-shadow:0 20px 60px rgba(0,0,0,.7),0 0 0 1px rgba(201,168,76,.1)}
.pcard-media{aspect-ratio:16/10;overflow:hidden;background:var(--void3);position:relative}
.pcard-media img,.pcard-media video{width:100%;height:100%;object-fit:cover;transition:transform .5s}
.pcard:hover .pcard-media img,.pcard:hover .pcard-media video{transform:scale(1.06)}
.pcard-no-media{width:100%;height:100%;display:flex;flex-direction:column;align-items:center;justify-content:center;color:var(--txt3);font-family:var(--fm);font-size:11px;gap:10px;background:linear-gradient(135deg,var(--void3),var(--void4))}
.pcard-no-media svg{opacity:.3}
.badge{position:absolute;top:10px;left:10px;font-family:var(--fm);font-size:9px;letter-spacing:1.5px;padding:4px 10px;border-radius:4px;font-weight:700;text-transform:uppercase}
.badge-new{background:var(--acc2);color:#fff}
.badge-hot{background:var(--red);color:#fff}
.pcard-body{padding:18px}
.pcard-cat{font-family:var(--fm);font-size:9px;letter-spacing:2.5px;color:var(--gold);text-transform:uppercase;margin-bottom:6px}
.pcard-name{font-family:var(--fd);font-size:23px;letter-spacing:.5px;margin-bottom:6px;line-height:1.1}
.pcard-desc{font-size:14px;color:var(--txt2);margin-bottom:14px;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;line-height:1.5}
.pcard-foot{display:flex;align-items:center;justify-content:space-between;border-top:1px solid var(--bdr);padding-top:14px}
.pcard-price{font-family:var(--fd);font-size:26px;color:var(--gold)}
.pcard-price.free{color:var(--green)}
.wish-btn{background:transparent;border:1px solid var(--bdr);color:var(--txt3);width:32px;height:32px;border-radius:50%;cursor:pointer;font-size:13px;transition:all .2s;display:flex;align-items:center;justify-content:center}
.wish-btn.on,.wish-btn:hover{border-color:var(--red);color:var(--red);background:rgba(207,75,75,.08)}
.buy-btn{background:var(--gold);color:var(--void);border:none;padding:8px 20px;border-radius:var(--r);font-family:var(--fm);font-size:11px;letter-spacing:.5px;cursor:pointer;font-weight:700;transition:all .2s;display:flex;align-items:center;gap:6px}
.buy-btn svg{width:11px;height:11px}
.buy-btn:hover{background:var(--gold-l);transform:translateY(-1px)}
.buy-btn.free{background:var(--green);color:#fff}

/* EMPTY */
.empty{text-align:center;padding:70px 30px;border:1px dashed var(--bdr);border-radius:var(--rl);grid-column:1/-1}
.empty svg{opacity:.2;margin-bottom:16px}
.empty h3{font-family:var(--fd);font-size:34px;color:var(--txt2);margin-bottom:10px;letter-spacing:1px}
.empty p{font-size:15px;color:var(--txt3)}

/* ══════════════════════════════════════
   MODAL
══════════════════════════════════════ */
.moverlay{position:fixed;inset:0;background:rgba(0,0,0,.9);z-index:800;display:flex;align-items:center;justify-content:center;padding:16px;opacity:0;pointer-events:none;transition:opacity .3s;backdrop-filter:blur(8px)}
.moverlay.open{opacity:1;pointer-events:all}
.modal{background:var(--void2);border:1px solid var(--bdr2);border-radius:var(--rxl);width:100%;max-width:640px;max-height:92vh;overflow-y:auto;transform:translateY(24px);transition:transform .35s cubic-bezier(.34,1.56,.64,1)}
.moverlay.open .modal{transform:none}
.modal.wide{max-width:940px}
.mhead{padding:22px 26px;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid var(--bdr);position:sticky;top:0;background:var(--void2);z-index:2}
.mhead-title{font-family:var(--fd);font-size:26px;letter-spacing:1px;color:var(--gold)}
.mclose{background:transparent;border:1px solid var(--bdr);color:var(--txt2);width:30px;height:30px;border-radius:50%;cursor:pointer;font-size:13px;display:flex;align-items:center;justify-content:center;transition:all .2s}
.mclose:hover{border-color:var(--gold);color:var(--gold);transform:rotate(90deg)}
.mbody{padding:26px}

/* DETAIL MODAL */
.dcarousel{aspect-ratio:16/9;border-radius:var(--rl);overflow:hidden;background:var(--void);margin-bottom:12px;position:relative}
.dcarousel img,.dcarousel video{width:100%;height:100%;object-fit:cover}
.dcarousel-nav{position:absolute;inset:0;display:flex;align-items:center;justify-content:space-between;padding:0 12px;pointer-events:none}
.dcarousel-nav button{pointer-events:all;background:rgba(0,0,0,.6);border:1px solid var(--bdr2);color:var(--gold);width:34px;height:34px;border-radius:50%;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:.2s;font-size:14px}
.dcarousel-nav button:hover{background:var(--gold);color:var(--void)}
.dthumbs{display:flex;gap:8px;overflow-x:auto;padding-bottom:4px}
.dthumb{width:68px;height:48px;border-radius:6px;overflow:hidden;cursor:pointer;border:2px solid transparent;flex-shrink:0;transition:.2s}
.dthumb.on{border-color:var(--gold)}
.dthumb img,.dthumb video{width:100%;height:100%;object-fit:cover;pointer-events:none}
.dprice-row{display:flex;align-items:center;justify-content:space-between;margin:20px 0;padding:18px 20px;background:var(--void3);border-radius:var(--rl);border:1px solid var(--bdr)}
.dprice{font-family:var(--fd);font-size:48px;color:var(--gold);line-height:1}
.dprice.free{color:var(--green)}
.dprice-label{font-family:var(--fm);font-size:9px;color:var(--txt3);letter-spacing:2px;text-transform:uppercase;margin-bottom:5px}
.dfile-info{background:rgba(75,158,107,.08);border:1px solid rgba(75,158,107,.2);border-radius:var(--r);padding:12px 16px;margin-top:12px;display:flex;align-items:center;gap:10px;font-family:var(--fm);font-size:11px;color:var(--green)}
.dfile-info svg{flex-shrink:0;width:16px;height:16px}
.dpurchase-note{font-family:var(--fm);font-size:10px;color:var(--txt3);text-align:center;margin-top:10px;letter-spacing:.5px}

/* ══════════════════════════════════════
   DOWNLOAD GATE MODAL
══════════════════════════════════════ */
.dgate-icon{width:60px;height:60px;border-radius:50%;background:var(--gold-bg);border:1px solid var(--bdr2);display:flex;align-items:center;justify-content:center;margin:0 auto 18px;color:var(--gold)}
.dgate-icon svg{width:28px;height:28px}

/* ══════════════════════════════════════
   FORMS
══════════════════════════════════════ */
.fg{margin-bottom:18px}
label,.lbl{display:block;font-family:var(--fm);font-size:10px;letter-spacing:2px;color:var(--txt2);text-transform:uppercase;margin-bottom:7px}
input[type=text],input[type=email],input[type=number],input[type=password],input[type=url],input[type=search],textarea,select{width:100%;background:var(--void3);border:1px solid var(--bdr);color:var(--txt);padding:11px 13px;border-radius:var(--r);font-family:var(--fb);font-size:16px;outline:none;transition:border-color .2s,box-shadow .2s;appearance:none}
input:focus,textarea:focus,select:focus{border-color:var(--gold);box-shadow:0 0 0 3px rgba(201,168,76,.08)}
select option{background:var(--void3)}
textarea{resize:vertical;min-height:80px}
.frow{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.fhint{font-family:var(--fm);font-size:10px;color:var(--txt3);margin-top:5px;letter-spacing:.3px}

/* ══════════════════════════════════════
   UPLOAD ZONE
══════════════════════════════════════ */
.uzone{border:2px dashed var(--bdr);border-radius:var(--rl);padding:28px;text-align:center;cursor:pointer;transition:all .2s;position:relative}
.uzone:hover,.uzone.drag{border-color:var(--gold);background:var(--gold-bg)}
.uzone input[type=file]{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;height:100%}
.uzone-icon{font-size:26px;opacity:.4;margin-bottom:7px}
.uzone-txt{font-family:var(--fm);font-size:11px;color:var(--txt3)}
.uzone-txt strong{color:var(--gold)}
.uprev{display:flex;flex-wrap:wrap;gap:8px;margin-top:10px}
.uprev-item{position:relative;width:76px;height:56px;border-radius:6px;overflow:hidden;border:1px solid var(--bdr)}
.uprev-item img{width:100%;height:100%;object-fit:cover}
.uprev-rm{position:absolute;top:2px;right:2px;width:16px;height:16px;background:rgba(0,0,0,.85);border:none;color:#fff;border-radius:50%;font-size:9px;cursor:pointer;display:flex;align-items:center;justify-content:center}
.fitem{display:flex;align-items:center;gap:10px;padding:10px 12px;background:var(--void3);border:1px solid var(--bdr);border-radius:var(--r);margin-top:8px;font-family:var(--fm);font-size:11px;color:var(--txt2)}
.fitem svg{width:14px;height:14px;opacity:.5;flex-shrink:0}

/* ══════════════════════════════════════
   PORTAL COMMON
══════════════════════════════════════ */
.portal-wrap{min-height:100vh;display:flex;flex-direction:column}
.portal-header{display:flex;align-items:center;justify-content:space-between;padding:14px 28px;border-bottom:1px solid var(--bdr);background:var(--void2);position:sticky;top:0;z-index:100}
.portal-logo-wrap{display:flex;align-items:center;gap:9px;cursor:pointer}
.portal-logo-svg{width:28px;height:28px}
.portal-logo-txt{font-family:var(--fd);font-size:18px;letter-spacing:2.5px;color:var(--gold)}
.portal-user{display:flex;align-items:center;gap:10px}
.avatar{width:34px;height:34px;border-radius:50%;background:linear-gradient(135deg,var(--gold-d),var(--acc));display:flex;align-items:center;justify-content:center;font-family:var(--fd);font-size:14px;color:#fff;border:1px solid var(--bdr2)}

/* ══════════════════════════════════════
   CLIENT PORTAL
══════════════════════════════════════ */
.cp-layout{display:flex;flex:1}
.cp-sidebar{width:220px;border-right:1px solid var(--bdr);padding:20px 0;flex-shrink:0;background:var(--void2)}
.cp-sidebar-item{display:flex;align-items:center;gap:10px;padding:11px 22px;font-family:var(--fm);font-size:11px;letter-spacing:.5px;color:var(--txt2);cursor:pointer;transition:all .2s;text-transform:uppercase}
.cp-sidebar-item svg{width:15px;height:15px;flex-shrink:0;opacity:.5}
.cp-sidebar-item:hover{color:var(--txt);background:var(--gold-bg)}
.cp-sidebar-item:hover svg{opacity:.8}
.cp-sidebar-item.on{color:var(--gold);background:var(--gold-bg);border-right:2px solid var(--gold)}
.cp-sidebar-item.on svg{opacity:1}
.cp-content{flex:1;padding:36px;overflow-y:auto;max-height:calc(100vh - 68px)}
.cp-section{display:none}
.cp-section.on{display:block}
.cp-title{font-family:var(--fd);font-size:36px;letter-spacing:1px;margin-bottom:24px}
.cp-title em{color:var(--gold);font-style:normal}

/* Client search */
.cp-search-wrap{
  display:flex;gap:10px;margin-bottom:20px;
}
.cp-search-wrap .nav-search{flex:1}
.cp-search-wrap .nav-search input{width:100%}

/* PURCHASES */
.phcard{background:var(--surf);border:1px solid var(--bdr);border-radius:var(--rl);padding:18px 20px;margin-bottom:12px;display:flex;align-items:center;gap:16px;transition:.2s}
.phcard:hover{border-color:var(--bdr2)}
.phcard-img{width:70px;height:52px;object-fit:cover;border-radius:var(--r);flex-shrink:0;background:var(--void3);display:flex;align-items:center;justify-content:center;color:var(--txt3)}
.phcard-info{flex:1}
.phcard-name{font-family:var(--fd);font-size:20px;margin-bottom:3px;letter-spacing:.3px}
.phcard-meta{font-family:var(--fm);font-size:10px;color:var(--txt3);letter-spacing:1px}
.phcard-price{font-family:var(--fd);font-size:24px;color:var(--gold);margin-right:12px}

/* WISHLIST */
.wgrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:16px}
.wcard{background:var(--surf);border:1px solid var(--bdr);border-radius:var(--rl);overflow:hidden;transition:.3s}
.wcard:hover{border-color:var(--bdr2);transform:translateY(-3px)}
.wcard-img{aspect-ratio:16/9;overflow:hidden;background:var(--void3);display:flex;align-items:center;justify-content:center;color:var(--txt3)}
.wcard-img img{width:100%;height:100%;object-fit:cover}
.wcard-body{padding:14px}
.wcard-name{font-family:var(--fd);font-size:19px;margin-bottom:4px}
.wcard-price{font-family:var(--fd);font-size:20px;color:var(--gold)}

/* PROFILE */
.pf-avatar-lg{width:80px;height:80px;border-radius:50%;background:linear-gradient(135deg,var(--gold-d),var(--acc));display:flex;align-items:center;justify-content:center;font-family:var(--fd);font-size:32px;color:#fff;border:2px solid var(--bdr2);margin-bottom:16px}

/* ══════════════════════════════════════
   ADMIN PORTAL
══════════════════════════════════════ */
.ap-layout{display:flex;flex:1}
.ap-sidebar{width:230px;border-right:1px solid var(--bdr);padding:20px 0;flex-shrink:0;background:var(--void2)}
.ap-nav-item{display:flex;align-items:center;gap:10px;padding:11px 22px;font-family:var(--fm);font-size:11px;letter-spacing:.5px;color:var(--txt2);cursor:pointer;transition:all .2s;text-transform:uppercase}
.ap-nav-item svg{width:14px;height:14px;flex-shrink:0;opacity:.5}
.ap-nav-item:hover{color:var(--txt);background:rgba(255,255,255,.02)}
.ap-nav-item:hover svg{opacity:.8}
.ap-nav-item.on{color:var(--gold);background:var(--gold-bg);border-left:2px solid var(--gold)}
.ap-nav-item.on svg{opacity:1}
.ap-nav-sect{font-family:var(--fm);font-size:9px;letter-spacing:3px;color:var(--txt3);text-transform:uppercase;padding:16px 22px 5px;margin-top:6px}
.ap-content{flex:1;padding:36px;overflow-y:auto;max-height:calc(100vh - 68px)}
.ap-section{display:none}
.ap-section.on{display:block}
.ap-title{font-family:var(--fd);font-size:36px;letter-spacing:1px;margin-bottom:5px}
.ap-sub{color:var(--txt3);font-family:var(--fm);font-size:11px;letter-spacing:1px;margin-bottom:28px}

/* ANALYTICS CARDS */
.stat-row{display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:16px;margin-bottom:28px}
.stat-card{background:var(--surf);border:1px solid var(--bdr);border-radius:var(--rl);padding:22px;transition:.2s;position:relative;overflow:hidden}
.stat-card::before{content:'';position:absolute;top:0;right:0;width:40%;height:100%;background:linear-gradient(90deg,transparent,rgba(201,168,76,.02));pointer-events:none}
.stat-card:hover{border-color:var(--bdr2)}
.sc-label{font-family:var(--fm);font-size:10px;letter-spacing:2px;color:var(--txt3);text-transform:uppercase;margin-bottom:10px;display:flex;align-items:center;gap:6px}
.sc-label svg{width:12px;height:12px;opacity:.6}
.sc-val{font-family:var(--fd);font-size:40px;color:var(--gold);line-height:1;margin-bottom:4px}

/* TABLE */
.tbl{width:100%;border-collapse:collapse}
.tbl th{font-family:var(--fm);font-size:10px;letter-spacing:2px;color:var(--txt3);text-transform:uppercase;padding:10px 14px;text-align:left;border-bottom:1px solid var(--bdr)}
.tbl td{padding:13px 14px;border-bottom:1px solid rgba(201,168,76,.04);vertical-align:middle;font-size:15px}
.tbl tr:hover td{background:rgba(255,255,255,.01)}
.tbl-thumb{width:52px;height:38px;object-fit:cover;border-radius:5px;background:var(--void3);display:flex;align-items:center;justify-content:center;color:var(--txt3)}
.tbl-thumb img{width:100%;height:100%;object-fit:cover;border-radius:5px}
.cat-tag{background:var(--gold-bg);color:var(--gold);font-family:var(--fm);font-size:9px;padding:3px 9px;border-radius:4px;letter-spacing:1px;text-transform:uppercase}
.status-tag{font-family:var(--fm);font-size:10px;padding:3px 9px;border-radius:4px;letter-spacing:1px;text-transform:uppercase}
.status-tag.completed{background:rgba(75,158,107,.12);color:var(--green)}

/* CHART */
.mini-chart{display:flex;align-items:flex-end;gap:5px;height:60px;margin-top:8px}
.mini-bar{flex:1;background:var(--gold-bg);border-radius:3px 3px 0 0;border-bottom:2px solid var(--gold);transition:.3s;min-height:4px;position:relative}
.mini-bar:hover::after{content:attr(title);position:absolute;bottom:calc(100% + 6px);left:50%;transform:translateX(-50%);background:var(--void2);border:1px solid var(--bdr);color:var(--txt);font-family:var(--fm);font-size:9px;padding:3px 7px;border-radius:4px;white-space:nowrap}
.chart-labels{display:flex;gap:5px;margin-top:4px}
.chart-label{flex:1;font-family:var(--fm);font-size:9px;color:var(--txt3);text-align:center}

/* SETTINGS */
.settings-block{background:var(--surf);border:1px solid var(--bdr);border-radius:var(--rl);padding:24px;margin-bottom:20px}
.settings-block-title{font-family:var(--fd);font-size:20px;letter-spacing:.5px;margin-bottom:18px;color:var(--txt);display:flex;align-items:center;gap:10px}
.settings-block-title svg{width:18px;height:18px;color:var(--gold);opacity:.7}
.divider{border:none;border-top:1px solid var(--bdr);margin:22px 0}

/* AUTH */
.auth-wrap{min-height:100vh;display:flex;align-items:center;justify-content:center;padding:20px;background:var(--void);position:relative;overflow:hidden}
.auth-bg{position:absolute;inset:0;pointer-events:none}
.auth-bg-grid{position:absolute;inset:0;background:linear-gradient(rgba(201,168,76,.02) 1px,transparent 1px),linear-gradient(90deg,rgba(201,168,76,.02) 1px,transparent 1px);background-size:50px 50px}
.auth-bg-orb{position:absolute;border-radius:50%;filter:blur(80px);opacity:.06}
.auth-bg-orb-1{width:400px;height:400px;background:var(--gold);top:-100px;right:-100px}
.auth-bg-orb-2{width:300px;height:300px;background:var(--acc);bottom:-80px;left:-80px}
.auth-box{background:var(--void2);border:1px solid var(--bdr2);border-radius:var(--rxl);padding:44px;width:100%;max-width:420px;position:relative;z-index:1}
.auth-logo-wrap{display:flex;flex-direction:column;align-items:center;margin-bottom:8px}
.auth-logo-svg{width:52px;height:52px;margin-bottom:10px}
.auth-logo-txt{font-family:var(--fd);font-size:28px;letter-spacing:5px;color:var(--gold)}
.auth-sub{font-family:var(--fm);font-size:10px;color:var(--txt3);text-align:center;letter-spacing:2px;margin-bottom:32px;text-transform:uppercase}
.auth-switch{font-family:var(--fm);font-size:11px;color:var(--txt3);text-align:center;margin-top:16px}
.auth-switch a{color:var(--gold);cursor:pointer}
.auth-error{background:rgba(207,75,75,.08);border:1px solid rgba(207,75,75,.25);color:var(--red);font-family:var(--fm);font-size:11px;padding:10px 14px;border-radius:var(--r);margin-bottom:16px;display:none;align-items:center;gap:8px}
.auth-error svg{width:14px;height:14px;flex-shrink:0}
.auth-error.show{display:flex}
.auth-tabs{display:flex;margin-bottom:28px;border:1px solid var(--bdr);border-radius:var(--r);overflow:hidden}
.auth-tab{flex:1;padding:10px;font-family:var(--fm);font-size:11px;letter-spacing:1px;cursor:pointer;color:var(--txt3);transition:.2s;background:transparent;border:none;text-transform:uppercase}
.auth-tab.on{background:var(--gold);color:var(--void);font-weight:700}

/* TOAST */
.toast{position:fixed;bottom:28px;right:28px;background:var(--surf2);border:1px solid var(--bdr2);color:var(--txt);padding:12px 18px;border-radius:var(--rl);font-family:var(--fm);font-size:12px;z-index:9001;transform:translateY(80px);opacity:0;transition:all .35s cubic-bezier(.34,1.56,.64,1);max-width:300px;display:flex;align-items:center;gap:10px}
.toast svg{width:14px;height:14px;flex-shrink:0}
.toast.show{transform:none;opacity:1}
.toast.ok{border-color:var(--green);color:var(--green)}
.toast.err{border-color:var(--red);color:var(--red)}

/* REVEAL */
.rv{opacity:0;transform:translateY(22px);transition:opacity .7s,transform .7s}
.rv.vis{opacity:1;transform:none}

/* ABOUT */
#about{max-width:800px;margin:0 auto;padding:80px 40px}

/* FOOTER */
footer{background:var(--void2);border-top:1px solid var(--bdr);padding:56px 40px 32px}
.ft-inner{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:2fr 1fr 1fr;gap:48px;margin-bottom:40px}
.ft-brand-logo{display:flex;align-items:center;gap:10px;margin-bottom:14px}
.ft-brand-svg{width:40px;height:40px}
.ft-brand-name{font-family:var(--fd);font-size:28px;letter-spacing:4px;color:var(--gold)}
.ft-brand-desc{color:var(--txt3);font-size:15px;line-height:1.7;font-style:italic}
.ft-col-title{font-family:var(--fm);font-size:10px;letter-spacing:3px;color:var(--gold);text-transform:uppercase;margin-bottom:14px}
.ft-col a{display:block;font-family:var(--fm);font-size:11px;color:var(--txt3);text-decoration:none;letter-spacing:.5px;cursor:pointer;transition:.2s;padding:4px 0}
.ft-col a:hover{color:var(--gold)}
.ft-bottom{display:flex;align-items:center;justify-content:space-between;border-top:1px solid var(--bdr);padding-top:24px;max-width:1200px;margin:0 auto}
.ft-copy{font-family:var(--fm);font-size:10px;color:var(--txt3);letter-spacing:1px}
.ft-made{font-family:var(--fm);font-size:10px;color:var(--txt3);display:flex;align-items:center;gap:6px}
.ft-made svg{width:10px;height:10px;color:var(--gold)}

/* ADMIN PASSWORD GATE */
.admin-gate{min-height:100vh;display:flex;align-items:center;justify-content:center;background:var(--void)}

/* RESPONSIVE */
@media(max-width:768px){
  #nav{padding:12px 18px}
  .nav-mid,.nav-search{display:none}
  .sec{padding:60px 18px}
  .frow{grid-template-columns:1fr}
  .cp-sidebar,.ap-sidebar{display:none}
  .h-stats{flex-wrap:wrap;gap:24px;justify-content:center}
  .h-cta{flex-direction:column;align-items:center}
  .ap-content,.cp-content{padding:20px}
  .stat-row{grid-template-columns:1fr 1fr}
  .phcard{flex-wrap:wrap}
  .ft-inner{grid-template-columns:1fr}
  .ft-bottom{flex-direction:column;gap:10px}
}

/* ════════════ UNIQUE SVG ICON SYSTEM ════════════ */
/* These are defined inline in JS */
</style>
</head>
<body>

<!-- ═══════════════════════════════════════════
   INTRO ANIMATION
═══════════════════════════════════════════ -->
<div id="intro">
  <div class="intro-svg-wrap">
    <div class="intro-rings">
      <div class="intro-ring ir1" style="top:50%;left:50%"></div>
      <div class="intro-ring ir2" style="top:50%;left:50%"></div>
      <div class="intro-ring ir3" style="top:50%;left:50%"></div>
      <div class="intro-ring ir4" style="top:50%;left:50%"></div>
    </div>
    <div class="intro-logo-center">
      <svg class="intro-hex" viewBox="0 0 72 72" fill="none">
        <!-- Hexagon logo -->
        <path d="M36 4L64 20V52L36 68L8 52V20L36 4Z" stroke="#C9A84C" stroke-width="1.5" fill="none"/>
        <path d="M36 14L56 26V50L36 62L16 50V26L36 14Z" fill="rgba(201,168,76,0.08)" stroke="rgba(201,168,76,0.3)" stroke-width="1"/>
        <!-- Inner P shape -->
        <text x="36" y="47" text-anchor="middle" font-family="'Bebas Neue',sans-serif" font-size="28" fill="#C9A84C" letter-spacing="2">PV</text>
        <!-- Corner dots -->
        <circle cx="36" cy="4" r="2.5" fill="#C9A84C"/>
        <circle cx="64" cy="20" r="2.5" fill="#C9A84C" opacity=".6"/>
        <circle cx="64" cy="52" r="2.5" fill="#C9A84C" opacity=".6"/>
        <circle cx="36" cy="68" r="2.5" fill="#C9A84C" opacity=".3"/>
        <circle cx="8" cy="52" r="2.5" fill="#C9A84C" opacity=".3"/>
        <circle cx="8" cy="20" r="2.5" fill="#C9A84C" opacity=".6"/>
      </svg>
    </div>
  </div>
  <div class="intro-text" id="intro-name">POLYVERSE</div>
  <div class="intro-bar-wrap"><div class="intro-bar" id="intro-bar"></div></div>
  <div class="intro-sub" id="intro-sub">Initializing</div>
</div>

<div id="cur"></div><div id="cur2"></div>

<!-- ═══════════════════════ STOREFRONT PAGE ═══════════════════════ -->
<div class="page active" id="page-store">
  <nav id="nav">
    <div class="nav-logo-wrap" onclick="goStore()">
      <svg class="nav-logo-svg" viewBox="0 0 40 40" fill="none">
        <path d="M20 2L36 11V29L20 38L4 29V11L20 2Z" stroke="#C9A84C" stroke-width="1.2" fill="rgba(201,168,76,0.06)"/>
        <text x="20" y="26" text-anchor="middle" font-family="'Bebas Neue',sans-serif" font-size="14" fill="#C9A84C" letter-spacing="1">PV</text>
        <circle cx="20" cy="2" r="1.5" fill="#C9A84C"/>
      </svg>
      <span class="nav-logo-txt">POLYVERSE</span>
    </div>
    <ul class="nav-mid">
      <li><a onclick="smoothTo('#shop')">Shop</a></li>
      <li><a onclick="smoothTo('#about')">About</a></li>
    </ul>
    <div class="nav-right" id="nav-right">
      <div class="nav-search">
        <input type="search" id="nav-search-inp" placeholder="Search assets…" onkeydown="if(event.key==='Enter')doSearch()">
        <button class="nav-search-btn" onclick="doSearch()" title="Search">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.8"><circle cx="6.5" cy="6.5" r="4"/><path d="M10 10l3 3"/></svg>
        </button>
      </div>
      <button class="btn btn-ghost btn-sm" onclick="showClientAuth()">Sign In</button>
      <button class="btn btn-gold btn-sm" onclick="showAdminGate()">
        <svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M7 1l1.5 4.5h4.5l-3.5 2.5 1.5 4.5L7 10l-4 2.5 1.5-4.5L1 5.5h4.5z"/></svg>
        Creator
      </button>
    </div>
  </nav>

  <div id="hero">
    <div class="h-grid"></div>
    <div class="h-particles" id="ptcls"></div>
    <div class="h-geo h-geo-1"></div>
    <div class="h-geo h-geo-2"></div>
    <div class="h-geo h-geo-3"></div>
    <div class="h-eye">
      <svg width="14" height="14" viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5" style="display:inline;vertical-align:middle;margin-right:6px"><circle cx="7" cy="7" r="2.5"/><path d="M1 7c0-3 2.5-5 6-5s6 2 6 5-2.5 5-6 5-6-2-6-5z"/></svg>
      Premium Blender Assets & Worlds
    </div>
    <h1 class="h-title" id="h-title">POLY<em>VERSE</em></h1>
    <p class="h-sub" id="h-tagline">Handcrafted 3D assets for creators who demand the extraordinary</p>
    <div class="h-cta">
      <button class="btn btn-gold btn-lg" onclick="smoothTo('#shop')">
        <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="6" width="12" height="8" rx="1"/><path d="M5 6V4a3 3 0 0 1 6 0v2"/></svg>
        Browse Collection
      </button>
      <button class="btn btn-ghost btn-lg" onclick="showClientAuth()">Join Free</button>
    </div>
    <div class="h-stats" id="h-stats"></div>
  </div>

  <div class="ticker"><div class="t-inner" id="ticker"></div></div>

  <div class="sec" id="shop">
    <div class="rv"><div class="sec-label">The Collection</div><div class="sec-title">Browse <em>Assets</em></div></div>
    <div class="search-bar-info rv" id="search-info">
      <span id="search-info-txt"></span>
      <button class="btn btn-glass btn-sm" onclick="clearSearch()">✕ Clear</button>
    </div>
    <div class="filters rv" id="filter-bar"></div>
    <div class="pgrid" id="pgrid"></div>
  </div>

  <div id="about">
    <div class="rv"><div class="sec-label">The Creator</div><div class="sec-title" style="margin-bottom:24px">About <em>Me</em></div></div>
    <p class="rv" id="about-txt" style="color:var(--txt2);font-size:20px;line-height:1.9">Welcome to my Blender asset store. Every asset is handcrafted with care for real-world projects.</p>
  </div>

  <footer>
    <div class="ft-inner">
      <div>
        <div class="ft-brand-logo">
          <svg class="ft-brand-svg" viewBox="0 0 40 40" fill="none">
            <path d="M20 2L36 11V29L20 38L4 29V11L20 2Z" stroke="#C9A84C" stroke-width="1.5" fill="rgba(201,168,76,0.06)"/>
            <text x="20" y="26" text-anchor="middle" font-family="'Bebas Neue',sans-serif" font-size="14" fill="#C9A84C" letter-spacing="1">PV</text>
            <circle cx="20" cy="2" r="1.5" fill="#C9A84C"/>
          </svg>
          <span class="ft-brand-name" id="ft-logo">POLYVERSE</span>
        </div>
        <p class="ft-brand-desc" id="ft-sub">Handcrafted Blender Assets & Worlds</p>
      </div>
      <div class="ft-col">
        <div class="ft-col-title">Navigate</div>
        <a onclick="smoothTo('#shop')">Shop</a>
        <a onclick="smoothTo('#about')">About</a>
        <a onclick="showClientAuth()">Client Portal</a>
        <a onclick="showAdminGate()">Creator Portal</a>
      </div>
      <div class="ft-col">
        <div class="ft-col-title">Policies</div>
        <a>Refund Policy</a>
        <a>License Terms</a>
        <a>Privacy Policy</a>
        <a>Contact</a>
      </div>
    </div>
    <div class="ft-bottom">
      <div class="ft-copy">&copy; <span id="yr"></span> Polyverse. All rights reserved.</div>
      <div class="ft-made">
        Made with <svg viewBox="0 0 10 10" fill="currentColor"><path d="M5 8.5C2 6.8 1 5.5 1 4a2 2 0 0 1 4 0 2 2 0 0 1 4 0c0 1.5-1 2.8-4 4.5z"/></svg> &amp; Blender
      </div>
    </div>
  </footer>
</div>

<!-- ═══════════════════════ CLIENT AUTH PAGE ═══════════════════════ -->
<div class="page" id="page-client-auth">
  <div class="auth-wrap">
    <div class="auth-bg">
      <div class="auth-bg-grid"></div>
      <div class="auth-bg-orb auth-bg-orb-1"></div>
      <div class="auth-bg-orb auth-bg-orb-2"></div>
    </div>
    <div class="auth-box">
      <div class="auth-logo-wrap">
        <svg class="auth-logo-svg" viewBox="0 0 52 52" fill="none">
          <path d="M26 3L48 15V37L26 49L4 37V15L26 3Z" stroke="#C9A84C" stroke-width="1.5" fill="rgba(201,168,76,0.06)"/>
          <path d="M26 11L42 20V38L26 47L10 38V20L26 11Z" fill="rgba(201,168,76,0.04)" stroke="rgba(201,168,76,0.2)" stroke-width="1"/>
          <text x="26" y="33" text-anchor="middle" font-family="'Bebas Neue',sans-serif" font-size="18" fill="#C9A84C" letter-spacing="2">PV</text>
          <circle cx="26" cy="3" r="2" fill="#C9A84C"/>
          <circle cx="48" cy="15" r="1.5" fill="#C9A84C" opacity=".5"/>
          <circle cx="48" cy="37" r="1.5" fill="#C9A84C" opacity=".5"/>
          <circle cx="26" cy="49" r="2" fill="#C9A84C" opacity=".3"/>
          <circle cx="4" cy="37" r="1.5" fill="#C9A84C" opacity=".5"/>
          <circle cx="4" cy="15" r="1.5" fill="#C9A84C" opacity=".5"/>
        </svg>
        <div class="auth-logo-txt">POLYVERSE</div>
      </div>
      <div class="auth-sub">Client Portal</div>
      <div class="auth-tabs">
        <button class="auth-tab on" id="ca-tab-in" onclick="switchAuthTab('in')">Sign In</button>
        <button class="auth-tab" id="ca-tab-up" onclick="switchAuthTab('up')">Create Account</button>
      </div>
      <div class="auth-error" id="ca-err">
        <svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="7" cy="7" r="6"/><path d="M7 4v3M7 10h.01"/></svg>
        <span id="ca-err-txt"></span>
      </div>
      <div id="ca-login">
        <div class="fg"><label>Email</label><input type="email" id="ca-email" placeholder="you@email.com"></div>
        <div class="fg"><label>Password</label><input type="password" id="ca-pass" placeholder="Your password" onkeydown="if(event.key==='Enter')clientLogin()"></div>
        <button class="btn btn-gold btn-block btn-lg" onclick="clientLogin()">Sign In →</button>
      </div>
      <div id="ca-signup" style="display:none">
        <div class="fg"><label>Full Name</label><input type="text" id="ca-sname" placeholder="Your name"></div>
        <div class="fg"><label>Email</label><input type="email" id="ca-semail" placeholder="you@email.com"></div>
        <div class="fg"><label>Password</label><input type="password" id="ca-spass" placeholder="Min 6 characters"></div>
        <button class="btn btn-gold btn-block btn-lg" onclick="clientSignup()">Create Account →</button>
      </div>
      <div class="auth-switch"><a onclick="goStore()">← Back to Store</a></div>
    </div>
  </div>
</div>

<!-- ═══════════════════════ CLIENT PORTAL PAGE ═══════════════════════ -->
<div class="page" id="page-client">
  <div class="portal-wrap">
    <div class="portal-header">
      <div class="portal-logo-wrap" onclick="goStore()">
        <svg class="portal-logo-svg" viewBox="0 0 28 28" fill="none">
          <path d="M14 2L26 8V20L14 26L2 20V8L14 2Z" stroke="#C9A84C" stroke-width="1.2" fill="rgba(201,168,76,0.06)"/>
          <text x="14" y="18" text-anchor="middle" font-family="'Bebas Neue',sans-serif" font-size="10" fill="#C9A84C" letter-spacing="1">PV</text>
        </svg>
        <span class="portal-logo-txt">POLYVERSE</span>
      </div>
      <div class="portal-user">
        <span style="font-family:var(--fm);font-size:11px;color:var(--txt2)" id="cp-username-nav"></span>
        <button class="btn btn-ghost btn-sm" onclick="goStore()">Store</button>
        <button class="btn btn-glass btn-sm" onclick="clientLogout()">Sign Out</button>
      </div>
    </div>
    <div class="cp-layout">
      <div class="cp-sidebar">
        <div class="cp-sidebar-item on" onclick="cpNav('browse',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="1" width="6" height="6" rx="1"/><rect x="9" y="1" width="6" height="6" rx="1"/><rect x="1" y="9" width="6" height="6" rx="1"/><rect x="9" y="9" width="6" height="6" rx="1"/></svg>
          Browse Assets
        </div>
        <div class="cp-sidebar-item" onclick="cpNav('purchases',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M3 2h10l2 9H1L3 2z"/><path d="M6 14a1 1 0 1 0 0-2 1 1 0 0 0 0 2zM10 14a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"/></svg>
          My Purchases
        </div>
        <div class="cp-sidebar-item" onclick="cpNav('wishlist',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M8 13.5C4 11 1 9 1 6a3.5 3.5 0 0 1 7 0 3.5 3.5 0 0 1 7 0c0 3-3 5-7 7.5z"/></svg>
          Wishlist
        </div>
        <div class="cp-sidebar-item" onclick="cpNav('profile',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="8" cy="5" r="3"/><path d="M2 15c0-3.3 2.7-6 6-6s6 2.7 6 6"/></svg>
          Profile
        </div>
      </div>
      <div class="cp-content">
        <!-- BROWSE -->
        <div class="cp-section on" id="cps-browse">
          <div class="cp-title">Browse <em>Assets</em></div>
          <div class="cp-search-wrap">
            <div class="nav-search" style="width:100%">
              <input type="search" id="cp-search-inp" placeholder="Search assets by name or category…" style="width:100%" onkeydown="if(event.key==='Enter')doCPSearch()">
              <button class="nav-search-btn" onclick="doCPSearch()">
                <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.8"><circle cx="6.5" cy="6.5" r="4"/><path d="M10 10l3 3"/></svg>
              </button>
            </div>
          </div>
          <div class="filters" id="cp-filter-bar"></div>
          <div class="pgrid" id="cp-pgrid"></div>
        </div>
        <!-- PURCHASES -->
        <div class="cp-section" id="cps-purchases">
          <div class="cp-title">My <em>Purchases</em></div>
          <div id="cp-purchases-list"></div>
        </div>
        <!-- WISHLIST -->
        <div class="cp-section" id="cps-wishlist">
          <div class="cp-title">My <em>Wishlist</em></div>
          <div class="wgrid" id="cp-wishlist-grid"></div>
        </div>
        <!-- PROFILE -->
        <div class="cp-section" id="cps-profile">
          <div class="cp-title">My <em>Profile</em></div>
          <div style="max-width:480px">
            <div class="pf-avatar-lg" id="cp-pf-avatar"></div>
            <div class="settings-block">
              <div class="settings-block-title">
                <svg viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="9" cy="6" r="3.5"/><path d="M2 17c0-3.9 3.1-7 7-7s7 3.1 7 7"/></svg>
                Account Info
              </div>
              <div class="fg"><label>Full Name</label><input type="text" id="cp-pf-name"></div>
              <div class="fg"><label>Email</label><input type="email" id="cp-pf-email" disabled style="opacity:.5"></div>
              <button class="btn btn-gold btn-sm" onclick="updateProfile()">Save Changes</button>
            </div>
            <div class="settings-block">
              <div class="settings-block-title">Change Password</div>
              <div class="fg"><label>New Password</label><input type="password" id="cp-pf-newpw" placeholder="New password"></div>
              <div class="fg"><label>Confirm</label><input type="password" id="cp-pf-confpw" placeholder="Confirm password"></div>
              <button class="btn btn-ghost btn-sm" onclick="changeClientPw()">Update Password</button>
            </div>
            <div class="settings-block" style="border-color:rgba(207,75,75,.25)">
              <div class="settings-block-title" style="color:var(--red)">Sign Out</div>
              <button class="btn btn-red btn-sm" onclick="clientLogout()">Sign Out of Account</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════════════ ADMIN GATE ═══════════════════════ -->
<div class="page" id="page-admin-gate">
  <div class="admin-gate">
    <div class="auth-wrap" style="min-height:unset">
      <div class="auth-bg">
        <div class="auth-bg-grid"></div>
        <div class="auth-bg-orb auth-bg-orb-1" style="background:var(--acc)"></div>
        <div class="auth-bg-orb auth-bg-orb-2" style="background:var(--gold)"></div>
      </div>
      <div class="auth-box">
        <div class="auth-logo-wrap">
          <svg class="auth-logo-svg" viewBox="0 0 52 52" fill="none">
            <path d="M26 3L48 15V37L26 49L4 37V15L26 3Z" stroke="#7C5CBF" stroke-width="1.5" fill="rgba(124,92,191,0.06)"/>
            <svg x="14" y="13" width="24" height="26" viewBox="0 0 24 26" fill="none" stroke="#9B7DE0" stroke-width="1.5">
              <path d="M12 1l1.5 4.5h4.5l-3.5 2.5 1.5 4.5L12 10l-4 2.5 1.5-4.5L5.5 5.5H10z"/>
              <rect x="6" y="14" width="12" height="9" rx="2"/>
              <path d="M9 14v-2a3 3 0 0 1 6 0v2"/>
            </svg>
            <circle cx="26" cy="3" r="2" fill="#9B7DE0"/>
          </svg>
          <div class="auth-logo-txt" style="color:var(--acc2)">CREATOR</div>
        </div>
        <div class="auth-sub">Creator Portal Access</div>
        <div class="auth-error" id="ag-err"><svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="7" cy="7" r="6"/><path d="M7 4v3M7 10h.01"/></svg><span id="ag-err-txt"></span></div>
        <div class="fg"><label>Admin Password</label><input type="password" id="ag-pass" placeholder="Enter creator password" onkeydown="if(event.key==='Enter')adminLogin()"></div>
        <button class="btn btn-acc btn-block btn-lg" onclick="adminLogin()">Enter Creator Portal →</button>
        <div class="auth-switch"><a onclick="goStore()">← Back to Store</a></div>
        <p style="font-family:var(--fm);font-size:10px;color:var(--txt3);text-align:center;margin-top:18px;letter-spacing:1px">Default: <strong style="color:var(--gold)">admin123</strong> — change in Settings</p>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════════════ ADMIN PORTAL PAGE ═══════════════════════ -->
<div class="page" id="page-admin">
  <div class="portal-wrap">
    <div class="portal-header">
      <div class="portal-logo-wrap" onclick="goStore()">
        <svg class="portal-logo-svg" viewBox="0 0 28 28" fill="none">
          <path d="M14 2L26 8V20L14 26L2 20V8L14 2Z" stroke="#9B7DE0" stroke-width="1.2" fill="rgba(124,92,191,0.08)"/>
          <text x="14" y="18" text-anchor="middle" font-family="'Bebas Neue',sans-serif" font-size="10" fill="#9B7DE0" letter-spacing="1">CP</text>
        </svg>
        <span class="portal-logo-txt" style="color:var(--acc2)">CREATOR PORTAL</span>
      </div>
      <div class="portal-user">
        <span style="font-family:var(--fm);font-size:11px;color:var(--acc2)">★ Admin</span>
        <button class="btn btn-ghost btn-sm" onclick="goStore()">View Store</button>
        <button class="btn btn-glass btn-sm" onclick="adminLogout()">Sign Out</button>
      </div>
    </div>
    <div class="ap-layout">
      <div class="ap-sidebar">
        <div class="ap-nav-sect">Overview</div>
        <div class="ap-nav-item on" onclick="apNav('analytics',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="9" width="3" height="6"/><rect x="6" y="5" width="3" height="10"/><rect x="11" y="1" width="3" height="14"/></svg>
          Analytics
        </div>
        <div class="ap-nav-sect">Products</div>
        <div class="ap-nav-item" onclick="apNav('products',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="1" width="14" height="4" rx="1"/><rect x="1" y="7" width="14" height="4" rx="1"/><rect x="1" y="13" width="8" height="2" rx="1"/></svg>
          All Products
        </div>
        <div class="ap-nav-item" onclick="apNav('add-product',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="8" cy="8" r="6.5"/><path d="M8 5v6M5 8h6"/></svg>
          Add Product
        </div>
        <div class="ap-nav-sect">Customers</div>
        <div class="ap-nav-item" onclick="apNav('customers',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="5" cy="5" r="3"/><circle cx="11" cy="5" r="3"/><path d="M1 14c0-2.2 1.8-4 4-4M10 14c0-2.2 1.8-4 4-4"/><path d="M7 14c0-2.2 1.8-4 4-4"/></svg>
          Customers
        </div>
        <div class="ap-nav-item" onclick="apNav('orders',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 3h12l-1.5 9H3.5L2 3z"/><path d="M5 3V2a3 3 0 0 1 6 0v1"/></svg>
          Orders
        </div>
        <div class="ap-nav-sect">Config</div>
        <div class="ap-nav-item" onclick="apNav('settings',this)">
          <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="8" cy="8" r="2.5"/><path d="M8 1v2M8 13v2M1 8h2M13 8h2M3 3l1.5 1.5M11.5 11.5L13 13M3 13l1.5-1.5M11.5 4.5L13 3"/></svg>
          Settings
        </div>
      </div>
      <div class="ap-content">

        <!-- ANALYTICS -->
        <div class="ap-section on" id="aps-analytics">
          <div class="ap-title">Analytics <span style="color:var(--gold)">Overview</span></div>
          <div class="ap-sub">Your store performance at a glance</div>
          <div class="stat-row" id="ap-stat-row"></div>
          <div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:24px">
            <div class="settings-block">
              <div style="font-family:var(--fm);font-size:10px;letter-spacing:2px;color:var(--txt3);text-transform:uppercase;margin-bottom:16px">Revenue — Last 7 Days</div>
              <div class="mini-chart" id="rev-chart"></div>
              <div class="chart-labels" id="rev-labels"></div>
            </div>
            <div class="settings-block">
              <div style="font-family:var(--fm);font-size:10px;letter-spacing:2px;color:var(--txt3);text-transform:uppercase;margin-bottom:14px">Top Categories</div>
              <div id="top-cats"></div>
            </div>
          </div>
          <div class="settings-block">
            <div style="font-family:var(--fm);font-size:10px;letter-spacing:2px;color:var(--txt3);text-transform:uppercase;margin-bottom:16px">Recent Orders</div>
            <div id="ap-recent-orders"></div>
          </div>
        </div>

        <!-- ALL PRODUCTS -->
        <div class="ap-section" id="aps-products">
          <div class="ap-title">All Products</div>
          <div class="ap-sub" style="display:flex;align-items:center;justify-content:space-between">
            <span id="prod-count">0 products</span>
            <button class="btn btn-gold btn-sm" onclick="apNav('add-product',document.querySelector('.ap-nav-item:nth-of-type(3)'))">+ Add New</button>
          </div>
          <div id="ap-prod-table"></div>
        </div>

        <!-- ADD/EDIT PRODUCT -->
        <div class="ap-section" id="aps-add-product">
          <div class="ap-title" id="ap-form-title">Add Product</div>
          <div class="ap-sub">Fill in all details to list your asset</div>
          <div class="frow">
            <div class="fg"><label>Product Name *</label><input type="text" id="f-name" placeholder="e.g. Forest Biome Pack"></div>
            <div class="fg"><label>Category *</label><select id="f-cat"></select></div>
          </div>
          <div class="fg"><label>Description *</label><textarea id="f-desc" rows="4" placeholder="Describe the asset, poly count, formats, what's included…"></textarea></div>
          <div class="frow">
            <div class="fg">
              <label>Price (₹ INR) *</label>
              <input type="number" id="f-price" min="0" step="1" placeholder="0 for free">
              <div class="fhint">Enter 0 to list as FREE</div>
            </div>
            <div class="fg">
              <label>Tags (comma separated)</label>
              <input type="text" id="f-tags" placeholder="e.g. nature, trees, pbr">
            </div>
          </div>
          <div class="fg">
            <label>Product Images</label>
            <div class="uzone" id="uz-img" ondragover="dov(event,'uz-img')" ondragleave="dlv('uz-img')" ondrop="ddrop(event,'img')">
              <input type="file" accept="image/*" multiple onchange="imgUp(this.files)">
              <div class="uzone-icon">
                <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2" opacity=".5"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="2"/><path d="M21 15l-5-5L5 21"/></svg>
              </div>
              <div class="uzone-txt"><strong>Click or drag images</strong><br>JPG · PNG · WEBP · GIF</div>
            </div>
            <div class="uprev" id="img-prev"></div>
          </div>
          <div class="fg">
            <label>Preview Video (optional)</label>
            <div class="uzone" id="uz-vid" ondragover="dov(event,'uz-vid')" ondragleave="dlv('uz-vid')" ondrop="ddrop(event,'vid')">
              <input type="file" accept="video/*" onchange="vidUp(this.files)">
              <div class="uzone-icon">
                <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2" opacity=".5"><rect x="2" y="4" width="20" height="16" rx="2"/><polygon points="10,8 10,16 17,12"/></svg>
              </div>
              <div class="uzone-txt"><strong>Click or drag video</strong><br>MP4 · max 80MB</div>
            </div>
            <div id="vid-prev"></div>
          </div>
          <div class="fg">
            <label>Downloadable File *</label>
            <div class="uzone" id="uz-file" ondragover="dov(event,'uz-file')" ondragleave="dlv('uz-file')" ondrop="ddrop(event,'dfile')">
              <input type="file" accept=".blend,.zip,.rar,.7z,.fbx,.obj,.glb,.gltf" onchange="dfileUp(this.files)">
              <div class="uzone-icon">
                <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.2" opacity=".5"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14,2 14,8 20,8"/><line x1="12" y1="18" x2="12" y2="12"/><polyline points="9,15 12,18 15,15"/></svg>
              </div>
              <div class="uzone-txt"><strong>Click or drag asset file</strong><br>.blend · .zip · .rar · .fbx · .obj · .glb</div>
            </div>
            <div id="dfile-prev"></div>
          </div>
          <div style="display:flex;gap:10px;margin-top:8px;flex-wrap:wrap">
            <button class="btn btn-gold" onclick="saveProd()">
              <svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 13V7h10v6M4 7V2h6v5M7 10v2"/></svg>
              Save Product
            </button>
            <button class="btn btn-ghost" onclick="cancelEdit()">Cancel</button>
            <button class="btn btn-red" id="del-btn" style="display:none;margin-left:auto" onclick="delProd()">Delete Product</button>
          </div>
        </div>

        <!-- CUSTOMERS -->
        <div class="ap-section" id="aps-customers">
          <div class="ap-title">Customers</div>
          <div class="ap-sub" id="cust-count">0 registered clients</div>
          <div id="ap-cust-table"></div>
        </div>

        <!-- ORDERS -->
        <div class="ap-section" id="aps-orders">
          <div class="ap-title">Orders</div>
          <div class="ap-sub">All completed purchases</div>
          <div id="ap-orders-table"></div>
        </div>

        <!-- SETTINGS -->
        <div class="ap-section" id="aps-settings">
          <div class="ap-title">Settings</div>
          <div class="ap-sub">Manage your store configuration</div>
          <div class="settings-block">
            <div class="settings-block-title">
              <svg viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="2" width="14" height="14" rx="2"/><path d="M6 2v14M2 9h4"/></svg>
              Store Branding
            </div>
            <div class="fg"><label>Store Name</label><input type="text" id="s-name" placeholder="POLYVERSE"></div>
            <div class="fg"><label>Tagline</label><input type="text" id="s-tag" placeholder="Handcrafted assets…"></div>
            <div class="fg"><label>About Text</label><textarea id="s-about" rows="4"></textarea></div>
            <button class="btn btn-gold btn-sm" onclick="saveSettings()">Save Branding</button>
          </div>
          <div class="settings-block">
            <div class="settings-block-title">
              <svg viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M3 3h12v3l-2 3 2 3v3H3v-3l2-3-2-3V3z"/></svg>
              Categories
            </div>
            <div id="cats-list"></div>
            <div style="display:flex;gap:10px;margin-top:12px">
              <input type="text" id="new-cat" placeholder="New category name" style="flex:1" onkeydown="if(event.key==='Enter')addCat()">
              <button class="btn btn-ghost btn-sm" onclick="addCat()">Add</button>
            </div>
          </div>
          <div class="settings-block">
            <div class="settings-block-title">
              <svg viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="5" width="14" height="11" rx="2"/><path d="M6 5V4a3 3 0 0 1 6 0v1"/><circle cx="9" cy="11" r="1.5"/></svg>
              Security
            </div>
            <div class="frow">
              <div class="fg"><label>New Admin Password</label><input type="password" id="s-npw" placeholder="New password"></div>
              <div class="fg"><label>Confirm Password</label><input type="password" id="s-cpw" placeholder="Confirm"></div>
            </div>
            <button class="btn btn-ghost btn-sm" onclick="changePw()">Update Password</button>
          </div>
          <div class="settings-block">
            <div class="settings-block-title">
              <svg viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M3 9V5l6-3 6 3v4c0 4-3 7-6 7.5C6 16 3 13 3 9z"/></svg>
              Data Management
            </div>
            <p style="font-family:var(--fm);font-size:11px;color:var(--txt3);margin-bottom:12px;letter-spacing:.3px">Export your store data as JSON backup. Import to restore on any device.</p>
            <div style="display:flex;gap:10px;flex-wrap:wrap">
              <button class="btn btn-ghost btn-sm" onclick="exportData()">
                <svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M7 2v8M4 7l3 3 3-3M2 12h10"/></svg>
                Export All Data
              </button>
              <button class="btn btn-ghost btn-sm" onclick="document.getElementById('imp-file').click()">Import Data</button>
              <input type="file" id="imp-file" accept=".json" style="display:none" onchange="importData(this)">
            </div>
          </div>
        </div>

      </div>
    </div>
  </div>
</div>

<!-- PRODUCT DETAIL MODAL -->
<div class="moverlay" id="m-detail">
  <div class="modal wide">
    <div class="mhead">
      <div class="mhead-title" id="d-title">Asset</div>
      <button class="mclose" onclick="cm('m-detail')">✕</button>
    </div>
    <div class="mbody">
      <div class="dcarousel" id="d-carousel">
        <div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;color:var(--txt3);font-family:var(--fm);font-size:11px">No preview</div>
        <div class="dcarousel-nav" id="d-car-nav" style="display:none">
          <button onclick="carNav(-1)">‹</button>
          <button onclick="carNav(1)">›</button>
        </div>
      </div>
      <div class="dthumbs" id="d-thumbs"></div>
      <div style="margin-top:18px">
        <div style="font-family:var(--fm);font-size:9px;letter-spacing:2.5px;color:var(--gold);text-transform:uppercase;margin-bottom:8px" id="d-cat-tags"></div>
        <p style="color:var(--txt2);font-size:16px;line-height:1.75" id="d-desc"></p>
      </div>
      <div id="d-file-info" class="dfile-info" style="display:none">
        <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M9 2H4a1 1 0 0 0-1 1v10a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V6z"/><path d="M9 2v4h4"/><line x1="8" y1="13" x2="8" y2="8"/><polyline points="5,11 8,13 11,11"/></svg>
        <span id="d-file-name">asset.blend</span>
      </div>
      <div class="dprice-row">
        <div>
          <div class="dprice-label">Price</div>
          <div class="dprice" id="d-price">₹0</div>
        </div>
        <div style="display:flex;flex-direction:column;gap:9px;align-items:flex-end">
          <button class="btn btn-gold btn-lg" id="d-buybtn" onclick="handleBuy()">
            <svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M1 3h12l-1.5 8H2.5L1 3z"/><circle cx="5" cy="13" r="1"/><circle cx="10" cy="13" r="1"/></svg>
            Buy Now
          </button>
          <button class="btn btn-glass btn-sm" id="d-wishbtn" onclick="toggleWishFromDetail()" style="display:none">♥ Add to Wishlist</button>
        </div>
      </div>
      <div class="dpurchase-note" id="d-purchased-note" style="display:none"></div>
    </div>
  </div>
</div>

<!-- DOWNLOAD GATE MODAL (buy confirmation) -->
<div class="moverlay" id="m-download">
  <div class="modal">
    <div class="mhead">
      <div class="mhead-title">Complete Purchase</div>
      <button class="mclose" onclick="cm('m-download')">✕</button>
    </div>
    <div class="mbody" style="text-align:center">
      <div class="dgate-icon">
        <svg viewBox="0 0 28 28" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="4" y="11" width="20" height="15" rx="2"/><path d="M8 11V8a6 6 0 0 1 12 0v3"/><circle cx="14" cy="19" r="2"/></svg>
      </div>
      <div class="ap-title" id="dg-product-name" style="font-size:26px;margin-bottom:8px">Asset Name</div>
      <div style="font-family:var(--fd);font-size:40px;color:var(--gold);margin-bottom:20px" id="dg-price">₹0</div>
      <p style="color:var(--txt2);font-size:15px;margin-bottom:24px;font-family:var(--fm);font-size:12px;letter-spacing:.3px">This is a simulated payment. In production, integrate with Razorpay, PayU, or CCAvenue for real INR payments.</p>
      <div style="background:var(--void3);border:1px solid var(--bdr);border-radius:var(--rl);padding:18px;margin-bottom:20px">
        <div class="fg" style="text-align:left">
          <label>Cardholder Name</label>
          <input type="text" id="pay-name" placeholder="Your name">
        </div>
        <div class="fg" style="text-align:left">
          <label>Card Number</label>
          <input type="text" id="pay-card" placeholder="4242 4242 4242 4242" maxlength="19" oninput="fmtCard(this)">
        </div>
        <div class="frow">
          <div class="fg" style="text-align:left"><label>Expiry</label><input type="text" placeholder="MM/YY" maxlength="5"></div>
          <div class="fg" style="text-align:left"><label>CVV</label><input type="text" placeholder="123" maxlength="3"></div>
        </div>
      </div>
      <button class="btn btn-gold btn-block btn-lg" onclick="confirmPurchase()">
        <svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 7l4 4 6-6"/></svg>
        Pay & Download
      </button>
      <p style="font-family:var(--fm);font-size:10px;color:var(--txt3);margin-top:12px;letter-spacing:.5px">🔒 Simulated secure payment · Integrate real gateway for production</p>
    </div>
  </div>
</div>

<!-- DOWNLOAD SUCCESS MODAL -->
<div class="moverlay" id="m-download-success">
  <div class="modal">
    <div class="mhead">
      <div class="mhead-title" style="color:var(--green)">Download Ready</div>
      <button class="mclose" onclick="cm('m-download-success')">✕</button>
    </div>
    <div class="mbody" style="text-align:center">
      <div style="width:70px;height:70px;border-radius:50%;background:rgba(75,158,107,.12);border:1px solid var(--green);display:flex;align-items:center;justify-content:center;margin:0 auto 20px;color:var(--green)">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20 6L9 17l-5-5"/></svg>
      </div>
      <div class="ap-title" style="font-size:30px;margin-bottom:8px;color:var(--green)">Purchase Complete!</div>
      <p style="color:var(--txt2);font-family:var(--fm);font-size:12px;margin-bottom:24px;letter-spacing:.3px">Your asset has been added to your library. Download it below.</p>
      <button class="btn btn-green btn-block btn-lg" id="dl-btn" onclick="triggerDownload()">
        <svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M7 2v7M4 6l3 3 3-3M2 12h10"/></svg>
        Download Asset
      </button>
      <div style="font-family:var(--fm);font-size:10px;color:var(--txt3);margin-top:12px" id="dl-filename"></div>
    </div>
  </div>
</div>

<div class="toast" id="toast">
  <svg id="toast-icon" viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"></svg>
  <span id="toast-msg"></span>
</div>

<script>
// ═══════════════════════════════════════════════════════
// ICONS (inline SVG strings)
// ═══════════════════════════════════════════════════════
const ICONS={
  search:`<svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.8"><circle cx="6.5" cy="6.5" r="4"/><path d="M10 10l3 3"/></svg>`,
  download:`<svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M7 2v7M4 6l3 3 3-3M2 12h10"/></svg>`,
  cart:`<svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M1 3h12l-1.5 8H2.5L1 3z"/><circle cx="5" cy="13" r="1"/><circle cx="10" cy="13" r="1"/></svg>`,
  ok:`<svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="2"><path d="M2 7l4 4 6-6"/></svg>`,
  err:`<svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="7" cy="7" r="6"/><path d="M7 4v3M7 10h.01"/></svg>`,
  cube:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/><polyline points="3.27,6.96 12,12.01 20.73,6.96"/><line x1="12" y1="22.08" x2="12" y2="12"/></svg>`,
};

// ═══════════════════════════════════════════════════════
// STORAGE
// ═══════════════════════════════════════════════════════
const DB={
  g(k,d){try{const v=localStorage.getItem('pv3_'+k);return v?JSON.parse(v):d}catch{return d}},
  s(k,v){try{localStorage.setItem('pv3_'+k,JSON.stringify(v));return true}catch{toast('Storage full','err');return false}}
};

// ═══════════════════════════════════════════════════════
// STATE
// ═══════════════════════════════════════════════════════
let S={
  products: DB.g('products',[]),
  clients: DB.g('clients',[]),
  orders: DB.g('orders',[]),
  settings: DB.g('settings',{
    name:'POLYVERSE',
    tagline:'Handcrafted 3D assets for creators who demand the extraordinary',
    about:'Welcome to my Blender asset store. Every asset is handcrafted with care for real-world projects.',
    pw:'admin123',
    cats:['3D Model','Environment','Material','World','Character','Props','Texture Pack','HDRI','Rigged']
  }),
  filter:'All',
  cpFilter:'All',
  searchQuery:'',
  cpSearchQuery:'',
  editId:null,
  pendImgs:[],
  pendVid:null,
  pendFile:null,
  curClient:null,
  detailProd:null,
  buyingProd:null,
  carIdx:0,
  adminIn:false,
};

// ═══════════════════════════════════════════════════════
// PAGE ROUTER
// ═══════════════════════════════════════════════════════
function showPage(id){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  window.scrollTo(0,0);
}
function goStore(){
  showPage('store');
  updateNavRight();
  renderStore();
}
function showClientAuth(){showPage('client-auth');resetAuthForms()}
function showAdminGate(){
  showPage('admin-gate');
  document.getElementById('ag-pass').value='';
  document.getElementById('ag-err').classList.remove('show');
}

function updateNavRight(){
  const r=document.getElementById('nav-right');
  const searchHtml=`<div class="nav-search"><input type="search" id="nav-search-inp" placeholder="Search assets…" onkeydown="if(event.key==='Enter')doSearch()"><button class="nav-search-btn" onclick="doSearch()" title="Search">${ICONS.search}</button></div>`;
  if(S.curClient){
    r.innerHTML=`${searchHtml}
      <span style="font-family:var(--fm);font-size:11px;color:var(--gold)">${S.curClient.name}</span>
      <button class="btn btn-ghost btn-sm" onclick="showClientPortal()">My Portal</button>
      <button class="btn btn-glass btn-sm" onclick="clientLogout()">Sign Out</button>
      <button class="btn btn-acc btn-sm" onclick="showAdminGate()"><svg width="11" height="11" viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M7 1l1.5 4.5h4.5l-3.5 2.5 1.5 4.5L7 10l-4 2.5 1.5-4.5L1 5.5h4.5z"/></svg>Creator</button>`;
  } else {
    r.innerHTML=`${searchHtml}
      <button class="btn btn-ghost btn-sm" onclick="showClientAuth()">Sign In</button>
      <button class="btn btn-gold btn-sm" onclick="showAdminGate()"><svg width="11" height="11" viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M7 1l1.5 4.5h4.5l-3.5 2.5 1.5 4.5L7 10l-4 2.5 1.5-4.5L1 5.5h4.5z"/></svg>Creator</button>`;
  }
}

// ═══════════════════════════════════════════════════════
// INTRO ANIMATION
// ═══════════════════════════════════════════════════════
const introSteps=['Initializing','Loading assets','Building world','Rendering'];
let introP=0;
function runIntro(){
  const bar=document.getElementById('intro-bar');
  const sub=document.getElementById('intro-sub');
  const dur=2600; // ms
  const start=Date.now();
  const tick=()=>{
    const elapsed=Date.now()-start;
    const pct=Math.min(elapsed/dur*100,100);
    bar.style.width=pct+'%';
    const stepI=Math.floor(pct/25);
    sub.textContent=introSteps[Math.min(stepI,introSteps.length-1)]+'…';
    if(pct<100){requestAnimationFrame(tick)}
    else{
      sub.textContent='Ready';
      setTimeout(()=>{
        const intro=document.getElementById('intro');
        intro.classList.add('fadeout');
        setTimeout(()=>{intro.classList.add('done');intro.style.display='none'},800);
      },400);
    }
  };
  requestAnimationFrame(tick);
}

// ═══════════════════════════════════════════════════════
// INIT
// ═══════════════════════════════════════════════════════
document.addEventListener('DOMContentLoaded',()=>{
  runIntro();
  document.getElementById('yr').textContent=new Date().getFullYear();
  applySettings();
  buildParticles();buildTicker();
  renderStore();
  updateNavRight();
  setupScroll();
  document.addEventListener('mousemove',e=>{
    document.getElementById('cur').style.cssText=`left:${e.clientX}px;top:${e.clientY}px;position:fixed;border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);width:6px;height:6px;background:var(--gold);box-shadow:0 0 8px var(--gold)`;
    setTimeout(()=>{
      const c2=document.getElementById('cur2');
      c2.style.left=e.clientX+'px';c2.style.top=e.clientY+'px';
    },60);
  });
  document.querySelectorAll('.moverlay').forEach(m=>m.addEventListener('click',e=>{if(e.target===m)cm(m.id)}));
  window.addEventListener('scroll',()=>{
    document.getElementById('nav').classList.toggle('scrolled',window.scrollY>30);
  });
});

// ═══════════════════════════════════════════════════════
// SETTINGS
// ═══════════════════════════════════════════════════════
function applySettings(){
  const s=S.settings;
  document.title=s.name+' — Blender Assets';
  const ht=document.getElementById('h-title');
  if(ht){
    const n=s.name;const sp=Math.max(4,n.length-4);
    ht.innerHTML=n.slice(0,sp)+'<em>'+n.slice(sp)+'</em>';
  }
  const htag=document.getElementById('h-tagline');if(htag)htag.textContent=s.tagline;
  const abt=document.getElementById('about-txt');if(abt)abt.textContent=s.about;
  const fl=document.getElementById('ft-logo');if(fl)fl.textContent=s.name;
  const fs=document.getElementById('ft-sub');if(fs)fs.textContent=s.tagline;
}
function populateSettingsForm(){
  const s=S.settings;
  document.getElementById('s-name').value=s.name;
  document.getElementById('s-tag').value=s.tagline;
  document.getElementById('s-about').value=s.about;
  renderCatsList();
}
function saveSettings(){
  S.settings.name=document.getElementById('s-name').value.trim()||'POLYVERSE';
  S.settings.tagline=document.getElementById('s-tag').value.trim();
  S.settings.about=document.getElementById('s-about').value.trim();
  DB.s('settings',S.settings);applySettings();toast('Settings saved','ok');
}
function changePw(){
  const np=document.getElementById('s-npw').value,cp=document.getElementById('s-cpw').value;
  if(!np){toast('Enter a new password','err');return}
  if(np!==cp){toast('Passwords do not match','err');return}
  S.settings.pw=np;DB.s('settings',S.settings);
  document.getElementById('s-npw').value='';document.getElementById('s-cpw').value='';
  toast('Password updated','ok');
}
function renderCatsList(){
  const el=document.getElementById('cats-list');
  el.innerHTML=S.settings.cats.map((c,i)=>`<div style="display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--bdr)">
    <span style="flex:1;font-family:var(--fm);font-size:12px">${c}</span>
    <button class="btn btn-glass btn-sm" onclick="rmCat(${i})">Remove</button>
  </div>`).join('');
  const sel=document.getElementById('f-cat');
  if(sel){const cv=sel.value;sel.innerHTML='<option value="">Select Category</option>';S.settings.cats.forEach(c=>{const o=document.createElement('option');o.value=o.textContent=c;if(c===cv)o.selected=true;sel.appendChild(o)});}
}
function addCat(){
  const v=document.getElementById('new-cat').value.trim();
  if(!v||S.settings.cats.includes(v))return;
  S.settings.cats.push(v);DB.s('settings',S.settings);
  document.getElementById('new-cat').value='';renderCatsList();
}
function rmCat(i){S.settings.cats.splice(i,1);DB.s('settings',S.settings);renderCatsList()}

// ═══════════════════════════════════════════════════════
// SEARCH
// ═══════════════════════════════════════════════════════
function doSearch(){
  const q=(document.getElementById('nav-search-inp')||{}).value||'';
  S.searchQuery=q.trim().toLowerCase();
  S.filter='All';
  renderStore();
  smoothTo('#shop');
}
function clearSearch(){
  S.searchQuery='';
  const inp=document.getElementById('nav-search-inp');if(inp)inp.value='';
  renderStore();
}
function doCPSearch(){
  S.cpSearchQuery=(document.getElementById('cp-search-inp')||{}).value.trim().toLowerCase();
  renderCPBrowse();
}
function matchProduct(p,q){
  if(!q)return true;
  return p.name.toLowerCase().includes(q)||
    (p.desc||'').toLowerCase().includes(q)||
    (p.cat||'').toLowerCase().includes(q)||
    (p.tags||'').toLowerCase().includes(q);
}

// ═══════════════════════════════════════════════════════
// CLIENT AUTH
// ═══════════════════════════════════════════════════════
function switchAuthTab(t){
  document.getElementById('ca-tab-in').classList.toggle('on',t==='in');
  document.getElementById('ca-tab-up').classList.toggle('on',t==='up');
  document.getElementById('ca-login').style.display=t==='in'?'block':'none';
  document.getElementById('ca-signup').style.display=t==='up'?'block':'none';
  document.getElementById('ca-err').classList.remove('show');
}
function resetAuthForms(){
  ['ca-email','ca-pass','ca-sname','ca-semail','ca-spass'].forEach(id=>{const el=document.getElementById(id);if(el)el.value=''});
  document.getElementById('ca-err').classList.remove('show');
  switchAuthTab('in');
}
function clientLogin(){
  const email=document.getElementById('ca-email').value.trim().toLowerCase();
  const pass=document.getElementById('ca-pass').value;
  const client=S.clients.find(c=>c.email===email&&c.pw===pass);
  if(!client){showAuthErr('ca-err','ca-err-txt','Invalid email or password');return}
  S.curClient=client;
  updateNavRight();showClientPortal();
}
function clientSignup(){
  const name=document.getElementById('ca-sname').value.trim();
  const email=document.getElementById('ca-semail').value.trim().toLowerCase();
  const pass=document.getElementById('ca-spass').value;
  if(!name||!email||!pass){showAuthErr('ca-err','ca-err-txt','Fill in all fields');return}
  if(pass.length<6){showAuthErr('ca-err','ca-err-txt','Password must be at least 6 characters');return}
  if(S.clients.find(c=>c.email===email)){showAuthErr('ca-err','ca-err-txt','Email already registered');return}
  const client={id:Date.now().toString(),name,email,pw:pass,wishlist:[],purchases:[],createdAt:new Date().toISOString()};
  S.clients.push(client);DB.s('clients',S.clients);
  S.curClient=client;
  updateNavRight();showClientPortal();toast('Welcome, '+name+'!','ok');
}
function clientLogout(){S.curClient=null;updateNavRight();goStore();toast('Signed out')}
function showAuthErr(wrapId,txtId,msg){
  const el=document.getElementById(wrapId);
  document.getElementById(txtId).textContent=msg;
  el.classList.add('show');
}

// ═══════════════════════════════════════════════════════
// CLIENT PORTAL
// ═══════════════════════════════════════════════════════
function showClientPortal(){
  showPage('client');
  document.getElementById('cp-username-nav').textContent=S.curClient.name;
  renderCPBrowse();renderCPPurchases();renderCPWishlist();renderCPProfile();
  cpNav('browse',document.querySelector('.cp-sidebar-item'));
}
function cpNav(section,el){
  document.querySelectorAll('.cp-sidebar-item').forEach(i=>i.classList.remove('on'));
  document.querySelectorAll('.cp-section').forEach(s=>s.classList.remove('on'));
  if(el)el.classList.add('on');
  document.getElementById('cps-'+section).classList.add('on');
}
function renderCPBrowse(){
  const cats=['All',...new Set(S.products.map(p=>p.cat))];
  document.getElementById('cp-filter-bar').innerHTML=cats.map(c=>`<button class="f-btn${c===S.cpFilter?' on':''}" onclick="setCPFilter('${c}')">${c}</button>`).join('');
  let filtered=S.cpFilter==='All'?S.products:S.products.filter(p=>p.cat===S.cpFilter);
  if(S.cpSearchQuery)filtered=filtered.filter(p=>matchProduct(p,S.cpSearchQuery));
  document.getElementById('cp-pgrid').innerHTML=filtered.length?filtered.map(p=>prodCard(p,true)).join('')
    :`<div class="empty">${ICONS.cube}<h3>No Assets Found</h3><p>Try a different search or category.</p></div>`;
}
function setCPFilter(c){S.cpFilter=c;renderCPBrowse()}
function renderCPPurchases(){
  const el=document.getElementById('cp-purchases-list');
  const myOrders=S.orders.filter(o=>o.clientId===S.curClient.id);
  if(!myOrders.length){el.innerHTML=`<div class="empty">${ICONS.cube}<h3>No Purchases Yet</h3><p>Browse assets and buy one to see it here.</p></div>`;return}
  el.innerHTML=myOrders.slice().reverse().map(o=>{
    const prod=S.products.find(p=>p.id===o.productId);
    const thumbSrc=prod&&prod.imgs&&prod.imgs[0]?prod.imgs[0].dataUrl:null;
    const thumb=thumbSrc?`<img src="${thumbSrc}" style="width:70px;height:52px;object-fit:cover;border-radius:var(--r)">`:`<div class="phcard-img">${ICONS.cube}</div>`;
    return `<div class="phcard">
      ${thumb}
      <div class="phcard-info">
        <div class="phcard-name">${prod?prod.name:o.productName||'Unknown Product'}</div>
        <div class="phcard-meta">Purchased ${new Date(o.date).toLocaleDateString('en-IN')} · Order #${o.id.slice(-8).toUpperCase()}</div>
      </div>
      <div class="phcard-price">${o.price===0?'FREE':'₹'+o.price.toLocaleString('en-IN')}</div>
      ${prod&&prod.file?`<button class="btn btn-green btn-sm" onclick="downloadFile('${prod.id}')">${ICONS.download}Download</button>`:''}
    </div>`;
  }).join('');
}
function renderCPWishlist(){
  const el=document.getElementById('cp-wishlist-grid');
  const wl=S.curClient.wishlist||[];
  const items=wl.map(id=>S.products.find(p=>p.id===id)).filter(Boolean);
  if(!items.length){el.innerHTML=`<div class="empty" style="grid-column:1/-1">${ICONS.cube}<h3>Wishlist Empty</h3><p>Heart any asset to save it here.</p></div>`;return}
  el.innerHTML=items.map(p=>{
    const thumb=p.imgs&&p.imgs[0]?`<img src="${p.imgs[0].dataUrl}">`:`<div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;color:var(--txt3)">${ICONS.cube}</div>`;
    return `<div class="wcard">
      <div class="wcard-img">${thumb}</div>
      <div class="wcard-body">
        <div class="pcard-cat">${p.cat}</div>
        <div class="wcard-name">${p.name}</div>
        <div style="display:flex;align-items:center;justify-content:space-between;margin-top:10px">
          <div class="wcard-price">${p.price===0?'FREE':'₹'+p.price.toLocaleString('en-IN')}</div>
          <div style="display:flex;gap:8px">
            <button class="btn btn-gold btn-sm" onclick="openDetail('${p.id}')">Buy</button>
            <button class="btn btn-glass btn-sm" onclick="removeWish('${p.id}')">Remove</button>
          </div>
        </div>
      </div>
    </div>`;
  }).join('');
}
function toggleWish(prodId,btn){
  if(!S.curClient){showClientAuth();return}
  const wl=S.curClient.wishlist||[];
  const idx=wl.indexOf(prodId);
  if(idx>=0){wl.splice(idx,1);toast('Removed from wishlist')}
  else{wl.push(prodId);toast('Added to wishlist','ok')}
  S.curClient.wishlist=wl;
  const ci=S.clients.findIndex(c=>c.id===S.curClient.id);
  if(ci>=0){S.clients[ci]=S.curClient;DB.s('clients',S.clients)}
  if(btn)btn.classList.toggle('on',idx<0);
  if(document.getElementById('cps-wishlist').classList.contains('on'))renderCPWishlist();
}
function removeWish(id){
  const wl=S.curClient.wishlist||[];
  const i=wl.indexOf(id);if(i>=0)wl.splice(i,1);
  S.curClient.wishlist=wl;
  const ci=S.clients.findIndex(c=>c.id===S.curClient.id);
  if(ci>=0){S.clients[ci]=S.curClient;DB.s('clients',S.clients)}
  renderCPWishlist();toast('Removed from wishlist');
}
function toggleWishFromDetail(){
  if(!S.detailProd)return;
  const btn=document.getElementById('d-wishbtn');
  toggleWish(S.detailProd.id,null);
  const inWish=S.curClient&&(S.curClient.wishlist||[]).includes(S.detailProd.id);
  btn.textContent=inWish?'♥ In Wishlist':'♥ Add to Wishlist';
  btn.style.color=inWish?'var(--red)':'';
}
function renderCPProfile(){
  if(!S.curClient)return;
  document.getElementById('cp-pf-name').value=S.curClient.name;
  document.getElementById('cp-pf-email').value=S.curClient.email;
  document.getElementById('cp-pf-avatar').textContent=S.curClient.name.charAt(0).toUpperCase();
}
function updateProfile(){
  const name=document.getElementById('cp-pf-name').value.trim();
  if(!name){toast('Name required','err');return}
  S.curClient.name=name;
  const ci=S.clients.findIndex(c=>c.id===S.curClient.id);
  if(ci>=0){S.clients[ci]=S.curClient;DB.s('clients',S.clients)}
  document.getElementById('cp-username-nav').textContent=name;
  renderCPProfile();toast('Profile updated','ok');
}
function changeClientPw(){
  const np=document.getElementById('cp-pf-newpw').value;
  const cp=document.getElementById('cp-pf-confpw').value;
  if(!np||np.length<6){toast('Password must be 6+ characters','err');return}
  if(np!==cp){toast('Passwords do not match','err');return}
  S.curClient.pw=np;
  const ci=S.clients.findIndex(c=>c.id===S.curClient.id);
  if(ci>=0){S.clients[ci]=S.curClient;DB.s('clients',S.clients)}
  document.getElementById('cp-pf-newpw').value='';document.getElementById('cp-pf-confpw').value='';
  toast('Password changed','ok');
}

// ═══════════════════════════════════════════════════════
// ADMIN AUTH
// ═══════════════════════════════════════════════════════
function adminLogin(){
  const pw=document.getElementById('ag-pass').value;
  if(pw===S.settings.pw){
    S.adminIn=true;
    document.getElementById('ag-err').classList.remove('show');
    showPage('admin');
    renderAdminAll();
  } else {
    showAuthErr('ag-err','ag-err-txt','Incorrect password');
    document.getElementById('ag-pass').value='';
  }
}
function adminLogout(){S.adminIn=false;goStore()}

// ═══════════════════════════════════════════════════════
// ADMIN NAVIGATION
// ═══════════════════════════════════════════════════════
function apNav(sec,el){
  document.querySelectorAll('.ap-nav-item').forEach(i=>i.classList.remove('on'));
  document.querySelectorAll('.ap-section').forEach(s=>s.classList.remove('on'));
  if(el)el.classList.add('on');
  document.getElementById('aps-'+sec).classList.add('on');
  if(sec==='analytics')renderAnalytics();
  if(sec==='products')renderAdminProducts();
  if(sec==='add-product'){renderCatsList();if(!S.editId)resetForm()}
  if(sec==='customers')renderCustomers();
  if(sec==='orders')renderOrders();
  if(sec==='settings')populateSettingsForm();
}
function renderAdminAll(){
  renderAnalytics();renderAdminProducts();renderCustomers();renderOrders();populateSettingsForm();renderCatsList();
}

// ═══════════════════════════════════════════════════════
// ANALYTICS
// ═══════════════════════════════════════════════════════
function renderAnalytics(){
  const totalRev=S.orders.reduce((s,o)=>s+o.price,0);
  document.getElementById('ap-stat-row').innerHTML=[
    {l:'Total Revenue',v:'₹'+totalRev.toLocaleString('en-IN'),icon:'<svg viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="6" cy="6" r="5"/><path d="M6 3v6M4 5h3a1 1 0 0 1 0 2H4"/></svg>'},
    {l:'Total Orders',v:S.orders.length,icon:'<svg viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M1 2h10l-1 7H2L1 2z"/><circle cx="4" cy="11" r=".8"/><circle cx="8" cy="11" r=".8"/></svg>'},
    {l:'Products',v:S.products.length,icon:'<svg viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="1" width="4" height="4" rx=".5"/><rect x="7" y="1" width="4" height="4" rx=".5"/><rect x="1" y="7" width="4" height="4" rx=".5"/><rect x="7" y="7" width="4" height="4" rx=".5"/></svg>'},
    {l:'Clients',v:S.clients.length,icon:'<svg viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="4" cy="4" r="2.5"/><circle cx="8.5" cy="4" r="2.5"/><path d="M0 11c0-2.2 1.8-4 4-4M8.5 7c2.2 0 3.5 1.5 3.5 4"/></svg>'},
  ].map(s=>`<div class="stat-card"><div class="sc-label">${s.icon}${s.l}</div><div class="sc-val">${s.v}</div></div>`).join('');
  const days=[];for(let i=6;i>=0;i--){const d=new Date();d.setDate(d.getDate()-i);days.push(d)}
  const dayRevs=days.map(d=>{const ds=d.toDateString();return S.orders.filter(o=>new Date(o.date).toDateString()===ds).reduce((s,o)=>s+o.price,0)});
  const mx=Math.max(...dayRevs,1);
  document.getElementById('rev-chart').innerHTML=dayRevs.map(v=>`<div class="mini-bar" style="height:${Math.max(4,(v/mx)*58)}px" title="₹${v.toLocaleString('en-IN')}"></div>`).join('');
  document.getElementById('rev-labels').innerHTML=days.map(d=>`<div class="chart-label">${d.toLocaleDateString('en',{weekday:'short'})}</div>`).join('');
  const catMap={};S.products.forEach(p=>{catMap[p.cat]=(catMap[p.cat]||0)+1});
  const sorted=Object.entries(catMap).sort((a,b)=>b[1]-a[1]).slice(0,5);
  const total=S.products.length||1;
  document.getElementById('top-cats').innerHTML=sorted.map(([c,n])=>`<div style="margin-bottom:10px">
    <div style="display:flex;justify-content:space-between;font-family:var(--fm);font-size:11px;margin-bottom:4px"><span>${c}</span><span style="color:var(--gold)">${n}</span></div>
    <div style="height:3px;background:var(--void3);border-radius:2px"><div style="height:100%;width:${(n/total)*100}%;background:linear-gradient(90deg,var(--gold-d),var(--gold));border-radius:2px"></div></div>
  </div>`).join('')||'<p style="font-family:var(--fm);font-size:11px;color:var(--txt3)">No products yet</p>';
  const recent=S.orders.slice(-5).reverse();
  document.getElementById('ap-recent-orders').innerHTML=recent.length?`<table class="tbl">
    <thead><tr><th>Product</th><th>Client</th><th>Date</th><th>Amount</th><th>Status</th></tr></thead>
    <tbody>${recent.map(o=>{
      const prod=S.products.find(p=>p.id===o.productId);
      const client=S.clients.find(c=>c.id===o.clientId);
      return `<tr>
        <td><span style="font-family:var(--fd);font-size:16px">${prod?prod.name:o.productName||'—'}</span></td>
        <td style="font-family:var(--fm);font-size:11px;color:var(--txt2)">${client?client.name:'—'}</td>
        <td style="font-family:var(--fm);font-size:10px;color:var(--txt3)">${new Date(o.date).toLocaleDateString('en-IN')}</td>
        <td style="font-family:var(--fd);font-size:18px;color:var(--gold)">${o.price===0?'FREE':'₹'+o.price.toLocaleString('en-IN')}</td>
        <td><span class="status-tag completed">Completed</span></td>
      </tr>`;
    }).join('')}</tbody>
  </table>`:'<p style="font-family:var(--fm);font-size:11px;color:var(--txt3)">No orders recorded yet</p>';
}

// ═══════════════════════════════════════════════════════
// ADMIN PRODUCTS
// ═══════════════════════════════════════════════════════
function renderAdminProducts(){
  document.getElementById('prod-count').textContent=S.products.length+' product'+(S.products.length!==1?'s':'');
  const el=document.getElementById('ap-prod-table');
  if(!S.products.length){el.innerHTML=`<div class="empty">${ICONS.cube}<h3>No Products</h3><p>Add your first asset using the Add Product tab.</p></div>`;return}
  el.innerHTML=`<table class="tbl">
    <thead><tr><th>Preview</th><th>Name</th><th>Category</th><th>Price</th><th>File</th><th>Actions</th></tr></thead>
    <tbody>${S.products.map(p=>{
      const thumb=p.imgs&&p.imgs[0]?`<img src="${p.imgs[0].dataUrl}" style="width:52px;height:38px;object-fit:cover;border-radius:5px">`:`<div class="tbl-thumb">${ICONS.cube}</div>`;
      return `<tr>
        <td>${thumb}</td>
        <td><span style="font-family:var(--fd);font-size:18px">${p.name}</span></td>
        <td><span class="cat-tag">${p.cat}</span></td>
        <td><span style="font-family:var(--fd);font-size:20px;color:var(--gold)">${p.price===0?'FREE':'₹'+p.price.toLocaleString('en-IN')}</span></td>
        <td style="font-family:var(--fm);font-size:10px;color:${p.file?'var(--green)':'var(--red)'}">${p.file?'✓ '+p.file.name:'✗ Missing'}</td>
        <td><button class="btn btn-ghost btn-sm" onclick="editProd('${p.id}')">Edit</button></td>
      </tr>`;
    }).join('')}</tbody>
  </table>`;
}

// ═══════════════════════════════════════════════════════
// PRODUCT CRUD
// ═══════════════════════════════════════════════════════
function saveProd(){
  const name=document.getElementById('f-name').value.trim();
  const cat=document.getElementById('f-cat').value;
  const desc=document.getElementById('f-desc').value.trim();
  const price=parseFloat(document.getElementById('f-price').value)||0;
  const tags=document.getElementById('f-tags').value.trim();
  if(!name||!cat||!desc){toast('Fill in all required fields','err');return}
  if(!S.pendFile&&!S.editId){toast('Please upload a downloadable file','err');return}
  const prod={
    id:S.editId||Date.now().toString(),
    name,cat,desc,price,tags,
    imgs:S.pendImgs.map(i=>({dataUrl:i.dataUrl,name:i.name})),
    vid:S.pendVid,
    file:S.pendFile,
    isNew:!S.editId,
    createdAt:S.editId?(S.products.find(p=>p.id===S.editId)||{}).createdAt:new Date().toISOString(),
    updatedAt:new Date().toISOString()
  };
  if(S.editId){const i=S.products.findIndex(p=>p.id===S.editId);if(i>=0)S.products[i]={...S.products[i],...prod}}
  else S.products.unshift(prod);
  DB.s('products',S.products);
  toast(S.editId?'Product updated!':'Product added!','ok');
  cancelEdit();renderAdminProducts();
  apNav('products',document.querySelectorAll('.ap-nav-item')[1]);
}
function editProd(id){
  const p=S.products.find(x=>x.id===id);if(!p)return;
  S.editId=id;S.pendImgs=[...(p.imgs||[])];S.pendVid=p.vid||null;S.pendFile=p.file||null;
  document.getElementById('f-name').value=p.name;
  document.getElementById('f-cat').value=p.cat;
  document.getElementById('f-desc').value=p.desc;
  document.getElementById('f-price').value=p.price;
  document.getElementById('f-tags').value=p.tags||'';
  renderCatsList();renderImgPrev();renderVidPrev();renderFilePrev();
  document.getElementById('ap-form-title').textContent='Edit Product';
  document.getElementById('del-btn').style.display='flex';
  apNav('add-product',document.querySelectorAll('.ap-nav-item')[2]);
}
function delProd(){
  if(!S.editId||!confirm('Delete this product permanently?'))return;
  S.products=S.products.filter(p=>p.id!==S.editId);
  DB.s('products',S.products);toast('Deleted','ok');
  cancelEdit();renderAdminProducts();
  apNav('products',document.querySelectorAll('.ap-nav-item')[1]);
}
function cancelEdit(){
  S.editId=null;S.pendImgs=[];S.pendVid=null;S.pendFile=null;
  ['f-name','f-desc','f-price','f-url','f-tags'].forEach(id=>{const el=document.getElementById(id);if(el)el.value=''});
  const fc=document.getElementById('f-cat');if(fc)fc.value='';
  document.getElementById('img-prev').innerHTML='';
  document.getElementById('vid-prev').innerHTML='';
  document.getElementById('dfile-prev').innerHTML='';
  document.getElementById('ap-form-title').textContent='Add Product';
  document.getElementById('del-btn').style.display='none';
}
function resetForm(){cancelEdit();renderCatsList()}

// ═══════════════════════════════════════════════════════
// FILE UPLOADS
// ═══════════════════════════════════════════════════════
function dov(e,z){e.preventDefault();document.getElementById(z).classList.add('drag')}
function dlv(z){document.getElementById(z).classList.remove('drag')}
function ddrop(e,t){
  e.preventDefault();
  const z=t==='img'?'uz-img':t==='vid'?'uz-vid':'uz-file';
  dlv(z);
  if(t==='img')imgUp(e.dataTransfer.files);
  else if(t==='vid')vidUp(e.dataTransfer.files);
  else dfileUp(e.dataTransfer.files);
}
function imgUp(files){
  Array.from(files).forEach(f=>{
    if(!f.type.startsWith('image/'))return;
    const r=new FileReader();r.onload=e=>{S.pendImgs.push({dataUrl:e.target.result,name:f.name});renderImgPrev()};r.readAsDataURL(f);
  });
}
function vidUp(files){
  const f=files[0];if(!f||!f.type.startsWith('video/'))return;
  if(f.size>85*1024*1024){toast('Video too large (max 80MB)','err');return}
  const r=new FileReader();r.onload=e=>{S.pendVid={dataUrl:e.target.result,name:f.name};renderVidPrev()};r.readAsDataURL(f);
}
function dfileUp(files){
  const f=files[0];if(!f)return;
  const r=new FileReader();r.onload=e=>{S.pendFile={dataUrl:e.target.result,name:f.name,size:f.size};renderFilePrev();toast('File ready: '+f.name,'ok')};r.readAsDataURL(f);
}
function renderImgPrev(){
  document.getElementById('img-prev').innerHTML=S.pendImgs.map((img,i)=>`<div class="uprev-item"><img src="${img.dataUrl}" alt=""><button class="uprev-rm" onclick="S.pendImgs.splice(${i},1);renderImgPrev()">✕</button></div>`).join('');
}
function renderVidPrev(){
  document.getElementById('vid-prev').innerHTML=S.pendVid?`<div class="fitem"><svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="2" width="12" height="10" rx="1"/><polygon points="5,5 5,9 10,7"/></svg>${S.pendVid.name}<button class="btn btn-glass btn-sm" onclick="S.pendVid=null;renderVidPrev()" style="margin-left:auto">Remove</button></div>`:'';
}
function renderFilePrev(){
  document.getElementById('dfile-prev').innerHTML=S.pendFile?`<div class="fitem" style="border-color:rgba(75,158,107,.3);color:var(--green)"><svg viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M8 1H3a1 1 0 0 0-1 1v10a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V5z"/><path d="M8 1v4h4"/></svg>${S.pendFile.name} (${(S.pendFile.size/1024/1024).toFixed(2)} MB)<button class="btn btn-glass btn-sm" onclick="S.pendFile=null;renderFilePrev()" style="margin-left:auto">Remove</button></div>`:'';
}

// ═══════════════════════════════════════════════════════
// CUSTOMERS & ORDERS (ADMIN)
// ═══════════════════════════════════════════════════════
function renderCustomers(){
  document.getElementById('cust-count').textContent=S.clients.length+' registered client'+(S.clients.length!==1?'s':'');
  const el=document.getElementById('ap-cust-table');
  if(!S.clients.length){el.innerHTML=`<div class="empty">${ICONS.cube}<h3>No Clients Yet</h3><p>Clients appear here when they register.</p></div>`;return}
  el.innerHTML=`<table class="tbl"><thead><tr><th>Name</th><th>Email</th><th>Joined</th><th>Purchases</th><th>Wishlist</th></tr></thead><tbody>
    ${S.clients.map(c=>{
      const orders=S.orders.filter(o=>o.clientId===c.id).length;
      return `<tr>
        <td><div style="display:flex;align-items:center;gap:10px">
          <div style="width:32px;height:32px;border-radius:50%;background:linear-gradient(135deg,var(--gold-d),var(--acc));display:flex;align-items:center;justify-content:center;font-family:var(--fd);font-size:14px;color:#fff;flex-shrink:0">${c.name.charAt(0).toUpperCase()}</div>
          <span style="font-family:var(--fd);font-size:18px">${c.name}</span>
        </div></td>
        <td style="font-family:var(--fm);font-size:11px;color:var(--txt2)">${c.email}</td>
        <td style="font-family:var(--fm);font-size:10px;color:var(--txt3)">${new Date(c.createdAt).toLocaleDateString('en-IN')}</td>
        <td style="font-family:var(--fd);font-size:18px;color:var(--gold)">${orders}</td>
        <td style="font-family:var(--fm);font-size:11px;color:var(--txt2)">${(c.wishlist||[]).length}</td>
      </tr>`;
    }).join('')}</tbody></table>`;
}
function renderOrders(){
  const el=document.getElementById('ap-orders-table');
  if(!S.orders.length){el.innerHTML=`<div class="empty">${ICONS.cube}<h3>No Orders Yet</h3><p>Orders appear here after clients purchase assets.</p></div>`;return}
  el.innerHTML=`<table class="tbl"><thead><tr><th>Order ID</th><th>Product</th><th>Client</th><th>Date</th><th>Amount</th><th>Status</th></tr></thead><tbody>
    ${S.orders.slice().reverse().map(o=>{
      const prod=S.products.find(p=>p.id===o.productId);
      const client=S.clients.find(c=>c.id===o.clientId);
      return `<tr>
        <td style="font-family:var(--fm);font-size:10px;color:var(--txt3)">#${o.id.slice(-8).toUpperCase()}</td>
        <td><span style="font-family:var(--fd);font-size:17px">${prod?prod.name:o.productName||'Unknown'}</span></td>
        <td style="font-family:var(--fm);font-size:11px;color:var(--txt2)">${client?client.name:'—'}</td>
        <td style="font-family:var(--fm);font-size:10px;color:var(--txt3)">${new Date(o.date).toLocaleDateString('en-IN')}</td>
        <td style="font-family:var(--fd);font-size:20px;color:var(--gold)">${o.price===0?'FREE':'₹'+o.price.toLocaleString('en-IN')}</td>
        <td><span class="status-tag completed">Completed</span></td>
      </tr>`;
    }).join('')}</tbody></table>`;
}

// ═══════════════════════════════════════════════════════
// STOREFRONT RENDER
// ═══════════════════════════════════════════════════════
function renderStore(){
  const stats=document.getElementById('h-stats');
  if(stats){
    const cats=[...new Set(S.products.map(p=>p.cat))].length;
    stats.innerHTML=[
      {n:S.products.length,l:'Assets'},
      {},
      {n:cats||0,l:'Categories'},
      {},
      {n:S.clients.length,l:'Clients'},
    ].map(s=>s.n===undefined?'<div class="stat-divider"></div>':`<div class="stat"><div class="n">${s.n}</div><div class="l">${s.l}</div></div>`).join('');
  }
  const cats=['All',...new Set(S.products.map(p=>p.cat))];
  const fb=document.getElementById('filter-bar');
  if(fb)fb.innerHTML=cats.map(c=>`<button class="f-btn${c===S.filter?' on':''}" onclick="setFilter('${c}')">${c}</button>`).join('');
  let filtered=S.filter==='All'?S.products:S.products.filter(p=>p.cat===S.filter);
  if(S.searchQuery)filtered=filtered.filter(p=>matchProduct(p,S.searchQuery));
  // Search info bar
  const si=document.getElementById('search-info');
  if(si){
    if(S.searchQuery){
      si.classList.add('show');
      document.getElementById('search-info-txt').textContent=`${filtered.length} result${filtered.length!==1?'s':''} for "${S.searchQuery}"`;
    } else si.classList.remove('show');
  }
  const pg=document.getElementById('pgrid');
  if(pg)pg.innerHTML=filtered.length?filtered.map(p=>prodCard(p,false)).join('')
    :`<div class="empty">${ICONS.cube}<h3>No Assets Yet</h3><p>The creator hasn't added any products yet.</p></div>`;
  setTimeout(()=>{const els=document.querySelectorAll('.rv');els.forEach(el=>{if(rvObs)rvObs.observe(el)})},50);
}
function setFilter(c){S.filter=c;renderStore()}

function prodCard(p,inPortal){
  const thumb=p.imgs&&p.imgs[0]?`<img src="${p.imgs[0].dataUrl}" alt="${p.name}" loading="lazy">`
    :p.vid?`<video src="${p.vid.dataUrl}" muted loop playsinline style="width:100%;height:100%;object-fit:cover"></video>`
    :`<div class="pcard-no-media">${ICONS.cube}No Preview</div>`;
  const price=p.price===0?'FREE':`₹${p.price.toLocaleString('en-IN')}`;
  const inWish=S.curClient&&(S.curClient.wishlist||[]).includes(p.id);
  const hasPurchased=S.curClient&&S.orders.some(o=>o.clientId===S.curClient.id&&o.productId===p.id);
  return `<div class="pcard rv" onclick="openDetail('${p.id}')">
    <div class="pcard-media">${thumb}${p.isNew?'<div class="badge badge-new">New</div>':''}</div>
    <div class="pcard-body">
      <div class="pcard-cat">${p.cat}</div>
      <div class="pcard-name">${p.name}</div>
      <div class="pcard-desc">${p.desc||''}</div>
      <div class="pcard-foot">
        <div class="pcard-price${p.price===0?' free':''}">${hasPurchased?'<span style="color:var(--green);font-size:14px;font-family:var(--fm)">✓ Owned</span>':price}</div>
        <div style="display:flex;gap:7px;align-items:center">
          <button class="wish-btn${inWish?' on':''}" id="wb-${p.id}" onclick="event.stopPropagation();toggleWish('${p.id}',this)" title="Wishlist">♥</button>
          ${hasPurchased?
            `<button class="buy-btn" style="background:var(--green)" onclick="event.stopPropagation();downloadFile('${p.id}')">${ICONS.download}Download</button>`:
            `<button class="buy-btn${p.price===0?' free':''}" onclick="event.stopPropagation();handleBuyDirect('${p.id}')">${ICONS.cart}${p.price===0?'Get Free':'Buy'}</button>`
          }
        </div>
      </div>
    </div>
  </div>`;
}

// ═══════════════════════════════════════════════════════
// DETAIL MODAL
// ═══════════════════════════════════════════════════════
function openDetail(id){
  const p=S.products.find(x=>x.id===id);if(!p)return;
  S.detailProd=p;S.carIdx=0;
  document.getElementById('d-title').textContent=p.name;
  // Category + tags
  const tags=(p.tags||'').split(',').map(t=>t.trim()).filter(Boolean);
  document.getElementById('d-cat-tags').innerHTML=`<span class="cat-tag">${p.cat}</span>${tags.map(t=>`<span style="font-family:var(--fm);font-size:9px;color:var(--txt3);padding:2px 8px;border:1px solid var(--bdr);border-radius:4px;margin-left:5px">${t}</span>`).join('')}`;
  document.getElementById('d-desc').textContent=p.desc;
  const priceEl=document.getElementById('d-price');
  priceEl.textContent=p.price===0?'FREE':'₹'+p.price.toLocaleString('en-IN');
  priceEl.className='dprice'+(p.price===0?' free':'');
  // file info
  const fileInfo=document.getElementById('d-file-info');
  if(p.file){fileInfo.style.display='flex';document.getElementById('d-file-name').textContent=p.file.name}
  else fileInfo.style.display='none';
  // buy button
  const hasPurchased=S.curClient&&S.orders.some(o=>o.clientId===S.curClient.id&&o.productId===p.id);
  const bb=document.getElementById('d-buybtn');
  if(hasPurchased){
    bb.textContent='';bb.innerHTML=`${ICONS.download}Download Asset`;
    bb.className='btn btn-green btn-lg';
    bb.onclick=()=>{downloadFile(p.id)};
    document.getElementById('d-purchased-note').style.display='block';
    document.getElementById('d-purchased-note').textContent='✓ You already own this asset';
  } else {
    bb.innerHTML=p.price===0?`${ICONS.download}Get Free`:`${ICONS.cart}Buy Now — ${p.price===0?'Free':'₹'+p.price.toLocaleString('en-IN')}`;
    bb.className='btn btn-lg'+(p.price===0?' btn-green':' btn-gold');
    bb.onclick=handleBuy;
    document.getElementById('d-purchased-note').style.display='none';
  }
  // wishlist button
  const wb=document.getElementById('d-wishbtn');
  wb.style.display=S.curClient?'flex':'none';
  if(S.curClient){
    const inWish=(S.curClient.wishlist||[]).includes(p.id);
    wb.textContent=inWish?'♥ In Wishlist':'♥ Add to Wishlist';
    wb.style.color=inWish?'var(--red)':'';
  }
  // media carousel
  buildDetailMedia(p);
  om('m-detail');
}
function buildDetailMedia(p){
  const media=[];
  if(p.imgs)p.imgs.forEach(img=>media.push({type:'img',src:img.dataUrl}));
  if(p.vid)media.push({type:'vid',src:p.vid.dataUrl});
  window._dm=media;S.carIdx=0;
  if(!media.length){
    document.getElementById('d-carousel').innerHTML='<div style="width:100%;height:100%;display:flex;align-items:center;justify-content:center;color:var(--txt3);font-family:var(--fm);font-size:11px">No preview available</div>';
    document.getElementById('d-thumbs').innerHTML='';
    document.getElementById('d-car-nav').style.display='none';
    return;
  }
  document.getElementById('d-car-nav').style.display=media.length>1?'flex':'none';
  setDMedia(0);
}
function setDMedia(i){
  const media=window._dm||[];if(!media.length)return;
  i=((i%media.length)+media.length)%media.length;
  S.carIdx=i;
  const m=media[i];
  const car=document.getElementById('d-carousel');
  const nav=document.getElementById('d-car-nav');
  car.innerHTML=(m.type==='img'?`<img src="${m.src}" style="width:100%;height:100%;object-fit:cover">`:`<video src="${m.src}" controls autoplay muted style="width:100%;height:100%;object-fit:cover"></video>`)+(media.length>1?nav.outerHTML:'');
  // Re-attach nav after innerHTML reset
  if(media.length>1){
    document.getElementById('d-car-nav').style.display='flex';
  }
  document.getElementById('d-thumbs').innerHTML=media.map((md,j)=>`<div class="dthumb${j===i?' on':''}" onclick="setDMedia(${j})">${md.type==='img'?`<img src="${md.src}">`:`<video src="${md.src}" muted></video>`}</div>`).join('');
}
function carNav(dir){setDMedia(S.carIdx+dir)}

// ═══════════════════════════════════════════════════════
// BUY / DOWNLOAD
// ═══════════════════════════════════════════════════════
function handleBuy(){
  if(!S.detailProd)return;
  handleBuyDirect(S.detailProd.id);
}
function handleBuyDirect(prodId){
  const p=S.products.find(x=>x.id===prodId);if(!p)return;
  if(!S.curClient){
    cm('m-detail');
    toast('Sign in to purchase','err');
    setTimeout(showClientAuth,400);
    return;
  }
  const hasPurchased=S.orders.some(o=>o.clientId===S.curClient.id&&o.productId===p.id);
  if(hasPurchased){downloadFile(p.id);return}
  if(p.price===0){completePurchase(p);return}
  S.buyingProd=p;
  document.getElementById('dg-product-name').textContent=p.name;
  document.getElementById('dg-price').textContent='₹'+p.price.toLocaleString('en-IN');
  om('m-download');
}
function confirmPurchase(){
  const name=document.getElementById('pay-name').value.trim();
  const card=document.getElementById('pay-card').value.trim();
  if(!name||card.length<14){toast('Fill in payment details','err');return}
  if(!S.buyingProd)return;
  completePurchase(S.buyingProd);
  cm('m-download');
}
function completePurchase(prod){
  const order={id:Date.now().toString(),clientId:S.curClient.id,productId:prod.id,productName:prod.name,date:new Date().toISOString(),price:prod.price};
  S.orders.push(order);DB.s('orders',S.orders);
  renderAnalytics();
  // Show success modal
  document.getElementById('dl-filename').textContent=prod.file?prod.file.name:'asset';
  document.getElementById('dl-btn').onclick=()=>{downloadFile(prod.id);cm('m-download-success')};
  cm('m-detail');
  om('m-download-success');
  toast('Purchase successful! 🎉','ok');
  if(document.getElementById('cps-purchases').classList.contains('on'))renderCPPurchases();
  renderStore();
}
function downloadFile(prodId){
  const p=S.products.find(x=>x.id===prodId);
  if(!p||!p.file){toast('File not found — admin must upload the asset file','err');return}
  // Create download link from dataUrl
  const a=document.createElement('a');
  a.href=p.file.dataUrl;
  a.download=p.file.name;
  document.body.appendChild(a);a.click();document.body.removeChild(a);
  toast('Downloading: '+p.file.name,'ok');
}
function fmtCard(inp){
  let v=inp.value.replace(/\D/g,'').slice(0,16);
  inp.value=v.replace(/(.{4})/g,'$1 ').trim();
}

// ═══════════════════════════════════════════════════════
// MODALS
// ═══════════════════════════════════════════════════════
function om(id){document.getElementById(id).classList.add('open')}
function cm(id){document.getElementById(id).classList.remove('open')}

// ═══════════════════════════════════════════════════════
// EXPORT / IMPORT
// ═══════════════════════════════════════════════════════
function exportData(){
  const data={products:S.products,clients:S.clients.map(c=>({...c,pw:'[hidden]'})),orders:S.orders,settings:{...S.settings,pw:'[hidden]'}};
  const b=new Blob([JSON.stringify(data,null,2)],{type:'application/json'});
  const a=document.createElement('a');a.href=URL.createObjectURL(b);a.download='polyverse-backup.json';a.click();
  toast('Exported!','ok');
}
function importData(input){
  const f=input.files[0];if(!f)return;
  const r=new FileReader();
  r.onload=e=>{
    try{
      const d=JSON.parse(e.target.result);
      if(d.products){S.products=d.products;DB.s('products',S.products)}
      if(d.settings&&d.settings.pw==='[hidden]')d.settings.pw=S.settings.pw;
      if(d.settings){S.settings={...S.settings,...d.settings};DB.s('settings',S.settings)}
      applySettings();renderAdminAll();toast('Imported!','ok');
    }catch{toast('Invalid file','err')}
  };r.readAsText(f);input.value='';
}

// ═══════════════════════════════════════════════════════
// SCROLL & PARTICLES & TICKER
// ═══════════════════════════════════════════════════════
let rvObs;
function setupScroll(){
  rvObs=new IntersectionObserver(es=>es.forEach(e=>{if(e.isIntersecting)e.target.classList.add('vis')}),{threshold:.08});
  document.querySelectorAll('.rv').forEach(el=>rvObs.observe(el));
}
function smoothTo(sel){
  const el=document.querySelector(sel);if(el)el.scrollIntoView({behavior:'smooth'});
}
function buildParticles(){
  const c=document.getElementById('ptcls');if(!c)return;
  const sizes=[1.5,2,3,1,2.5];
  for(let i=0;i<34;i++){
    const p=document.createElement('div');p.className='ptcl';
    const tx=(Math.random()-.5)*100,ty=-(40+Math.random()*90);
    const size=sizes[Math.floor(Math.random()*sizes.length)];
    const isAccent=Math.random()>.8;
    p.style.cssText=`left:${Math.random()*100}%;top:${Math.random()*100}%;width:${size}px;height:${size}px;background:${isAccent?'var(--acc2)':'var(--gold)'};--tx:${tx}px;--ty:${ty}px;--d:${5+Math.random()*10}s;--dl:${-Math.random()*12}s;--oa:${.05+Math.random()*.2};--ob:${.4+Math.random()*.5}`;
    c.appendChild(p);
  }
}
function buildTicker(){
  const items=[
    {txt:'BLENDER ASSETS',icon:'◈'},
    {txt:'3D WORLDS',icon:'◈'},
    {txt:'INSTANT DOWNLOAD',icon:'◈'},
    {txt:'INR PAYMENTS',icon:'◈'},
    {txt:'HIGH QUALITY',icon:'◈'},
    {txt:'GAME READY',icon:'◈'},
    {txt:'CINEMATIC',icon:'◈'},
    {txt:'PROCEDURAL',icon:'◈'},
  ];
  const rep=[...items,...items];
  const t=document.getElementById('ticker');
  if(t)t.innerHTML=rep.map(i=>`<span class="t-item"><span style="font-size:10px;opacity:.5">${i.icon}</span> ${i.txt}</span>`).join('');
}

// ═══════════════════════════════════════════════════════
// TOAST
// ═══════════════════════════════════════════════════════
let tt;
function toast(msg,type=''){
  const t=document.getElementById('toast');
  const icon=document.getElementById('toast-icon');
  const msgEl=document.getElementById('toast-msg');
  msgEl.textContent=msg;
  t.className='toast'+(type?' '+type:'');
  if(type==='ok')icon.innerHTML='<path d="M2 7l4 4 6-6" stroke-width="2"/>';
  else if(type==='err')icon.innerHTML='<circle cx="7" cy="7" r="6"/><path d="M7 4v3M7 10h.01"/>';
  else icon.innerHTML='<circle cx="7" cy="7" r="6"/>';
  t.classList.add('show');clearTimeout(tt);
  tt=setTimeout(()=>t.classList.remove('show'),3200);
}
</script>
</body>
</html>
