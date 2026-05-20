# BSP-
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BSP Nancy – Fidélité</title>
<link href="https://fonts.googleapis.com/css2?family=Pinyon+Script&family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=Jost:wght@300;400;500;600&display=swap" rel="stylesheet">

<style>
:root{
  --g1:#C9A84C; --g2:#E8C96A; --g3:#8B6B1A; --g4:#F5DFA0;
  --marble:#F8F6F2; --marble2:#EDE9E0; --marble3:#DDD8CC;
  --dark:#1A1408; --muted:#9A8A6A; --text:#3A2E1A;
  --green:#4A9A5A; --red:#C05050;
  --border:rgba(201,168,76,.3);
}
*{box-sizing:border-box;margin:0;padding:0;}
body{
  background: var(--marble);
  background-image:
    radial-gradient(ellipse at 20% 10%, rgba(201,168,76,.08) 0%, transparent 50%),
    radial-gradient(ellipse at 80% 90%, rgba(201,168,76,.06) 0%, transparent 50%),
    url("data:image/svg+xml,%3Csvg width='400' height='400' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='400' height='400' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
  color: var(--text);
  font-family:'Jost',sans-serif;
  min-height:100vh;
  overflow-x:hidden;
}

/* ── MARBLE VEINS ── */
body::after{
  content:'';
  position:fixed;inset:0;
  background-image:
    linear-gradient(125deg, transparent 30%, rgba(201,168,76,.04) 50%, transparent 70%),
    linear-gradient(60deg, transparent 20%, rgba(201,168,76,.03) 40%, transparent 60%);
  pointer-events:none;z-index:0;
}

/* ── HEADER ── */
header{
  position:sticky;top:0;z-index:200;
  background:linear-gradient(135deg, #1A1408 0%, #2A2010 50%, #1A1408 100%);
  border-bottom:2px solid var(--g1);
  padding:0 20px;
  height:72px;
  display:flex;align-items:center;justify-content:space-between;
  box-shadow:0 4px 30px rgba(139,107,26,.4);
}

.hlogo{display:flex;align-items:center;gap:14px;}

/* Ornement SVG doré */
.ornement{
  width:54px;height:54px;
  border:2px solid var(--g1);
  border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  background:linear-gradient(135deg,rgba(201,168,76,.15),rgba(201,168,76,.05));
  flex-shrink:0;
}
.ornement svg{width:36px;height:36px;}

.bname{font-family:'Pinyon Script',cursive;font-size:28px;color:var(--g2);line-height:1;}
.bsub{font-size:9px;text-transform:uppercase;letter-spacing:4px;color:var(--muted);margin-top:2px;}

.hpills{display:flex;gap:10px;}
.hp{
  background:rgba(201,168,76,.1);
  border:1px solid rgba(201,168,76,.25);
  border-radius:8px;padding:5px 14px;
  font-size:11px;color:var(--muted);text-align:center;
}
.hp strong{display:block;font-family:'Playfair Display',serif;font-size:20px;color:var(--g2);line-height:1.1;}

/* ── TABS ── */
nav.tabs{
  display:flex;gap:0;
  background:var(--dark);
  border-bottom:2px solid var(--g1);
  padding:0 16px;
  position:sticky;top:72px;z-index:190;
}
.tab{
  padding:13px 18px;background:none;border:none;cursor:pointer;
  font-family:'Jost',sans-serif;font-size:11px;font-weight:600;
  text-transform:uppercase;letter-spacing:2px;
  color:var(--muted);
  border-bottom:3px solid transparent;
  margin-bottom:-2px;
  transition:all .2s;
}
.tab:hover{color:var(--g2);}
.tab.on{color:var(--g1);border-bottom-color:var(--g1);}

/* ── LAYOUT ── */
.page{max-width:1080px;margin:0 auto;padding:28px 16px;position:relative;z-index:1;}
.sec{display:none;}.sec.on{display:block;}

/* ── DECORATIVE DIVIDER ── */
.sh{
  display:flex;align-items:center;gap:14px;
  margin-bottom:24px;
}
.sh-txt{
  font-family:'Playfair Display',serif;
  font-style:italic;font-size:22px;
  color:var(--g3);white-space:nowrap;
}
.sh-line{flex:1;height:1px;background:linear-gradient(to right,var(--g1),rgba(201,168,76,.1));}
.sh-orn{color:var(--g1);font-size:14px;white-space:nowrap;}

/* ── QUICK ADD PANEL ── */
.qa{
  background:white;
  border:1px solid rgba(201,168,76,.35);
  border-radius:20px;
  padding:24px;
  margin-bottom:24px;
  box-shadow:0 4px 24px rgba(139,107,26,.1);
  position:relative;overflow:hidden;
}
.qa::before{
  content:'';
  position:absolute;top:0;left:0;right:0;height:4px;
  background:linear-gradient(90deg,var(--g3),var(--g1),var(--g2),var(--g1),var(--g3));
}

.row{display:flex;gap:12px;flex-wrap:wrap;}
.fg{flex:1;min-width:160px;}
label{display:block;font-size:10px;text-transform:uppercase;letter-spacing:2px;color:var(--muted);margin-bottom:6px;}
input,select{
  width:100%;
  background:var(--marble);
  border:1px solid rgba(201,168,76,.3);
  border-radius:10px;padding:10px 14px;
  color:var(--text);font-family:'Jost',sans-serif;font-size:14px;
  outline:none;transition:all .2s;
}
input:focus,select:focus{border-color:var(--g1);box-shadow:0 0 0 3px rgba(201,168,76,.12);background:white;}
input::placeholder{color:var(--muted);}
.qa-bot{display:flex;align-items:center;gap:10px;margin-top:14px;flex-wrap:wrap;}
.pts-hint{font-size:13px;color:var(--g3);margin-left:auto;font-style:italic;font-family:'Playfair Display',serif;}

/* ── BUTTONS ── */
.btn{padding:10px 22px;border-radius:10px;border:none;font-family:'Jost',sans-serif;font-size:13px;font-weight:600;cursor:pointer;transition:all .2s;letter-spacing:.5px;}
.bg{background:linear-gradient(135deg,var(--g1),var(--g3));color:white;box-shadow:0 4px 14px rgba(139,107,26,.3);}
.bg:hover{transform:translateY(-2px);box-shadow:0 8px 24px rgba(139,107,26,.4);}
.bo{background:white;border:1.5px solid var(--g1);color:var(--g3);}
.bo:hover{background:rgba(201,168,76,.08);border-color:var(--g3);}
.bgr{background:rgba(74,154,90,.12);border:1.5px solid rgba(74,154,90,.4);color:var(--green);}
.bgr:hover{background:rgba(74,154,90,.22);}
.bwa{background:linear-gradient(135deg,#25D366,#128C7E);color:white;box-shadow:0 4px 14px rgba(37,211,102,.3);}
.bwa:hover{transform:translateY(-2px);box-shadow:0 8px 24px rgba(37,211,102,.35);}
.bsm{padding:7px 14px;font-size:12px;}
.bgh{background:transparent;border:none;color:var(--muted);font-size:16px;cursor:pointer;padding:4px 8px;border-radius:6px;transition:color .2s;}
.bgh:hover{color:var(--red);}

/* ── FILTERS ── */
.frow{display:flex;gap:8px;align-items:center;flex-wrap:wrap;margin-bottom:18px;}
.chip{padding:6px 16px;border-radius:20px;border:1.5px solid rgba(201,168,76,.3);background:white;color:var(--muted);font-size:11px;cursor:pointer;font-family:'Jost',sans-serif;font-weight:500;transition:all .2s;}
.chip.on,.chip:hover{border-color:var(--g1);color:var(--g3);background:rgba(201,168,76,.08);}
.sw{flex:1;min-width:200px;position:relative;}
.sw span{position:absolute;left:12px;top:50%;transform:translateY(-50%);color:var(--muted);pointer-events:none;}
.sw input{padding-left:36px;}

/* ── CLIENT GRID ── */
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:14px;}

.cc{
  background:white;
  border:1px solid rgba(201,168,76,.25);
  border-radius:18px;padding:20px;
  transition:all .25s;position:relative;overflow:hidden;
  box-shadow:0 2px 12px rgba(139,107,26,.07);
}
.cc:hover{border-color:rgba(201,168,76,.55);transform:translateY(-3px);box-shadow:0 10px 32px rgba(139,107,26,.15);}
.cc::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:linear-gradient(90deg,var(--g3),var(--g1),var(--g2));}
.cc.hr{border-color:rgba(74,154,90,.35);}
.cc.hr::before{background:linear-gradient(90deg,#2A7A3A,#5EBA7D,#2A7A3A);}

.cctop{display:flex;align-items:flex-start;gap:12px;margin-bottom:14px;}
.av{
  width:46px;height:46px;border-radius:50%;flex-shrink:0;
  background:linear-gradient(135deg,var(--g3),var(--g1));
  display:flex;align-items:center;justify-content:center;
  font-family:'Playfair Display',serif;font-size:17px;font-weight:700;color:white;
  box-shadow:0 3px 10px rgba(139,107,26,.3);
}
.ci{flex:1;}
.cn{font-weight:600;font-size:15px;color:var(--text);margin-bottom:2px;}
.cp{font-size:12px;color:var(--muted);}

/* CIRCLES fidélité style original BSP */
.circles-row{
  display:flex;gap:7px;flex-wrap:wrap;
  margin:12px 0 10px;
  justify-content:center;
}
.circ{
  width:32px;height:32px;border-radius:50%;
  border:2px solid rgba(201,168,76,.4);
  background:var(--marble);
  transition:all .3s;
  position:relative;overflow:hidden;
}
.circ.filled{
  background:linear-gradient(135deg,var(--g3),var(--g1));
  border-color:var(--g3);
  box-shadow:0 2px 6px rgba(139,107,26,.3);
}
.circ.filled::after{
  content:'✦';
  position:absolute;inset:0;
  display:flex;align-items:center;justify-content:center;
  color:white;font-size:12px;
}

.pb{margin:8px 0;}
.pbl{display:flex;justify-content:space-between;font-size:11px;color:var(--muted);margin-bottom:5px;}
.pbl strong{color:var(--g3);font-size:13px;font-family:'Playfair Display',serif;}
.pbar{height:6px;background:var(--marble2);border-radius:3px;overflow:hidden;border:1px solid rgba(201,168,76,.2);}
.pbf{height:100%;background:linear-gradient(to right,var(--g3),var(--g2));border-radius:3px;transition:width .7s cubic-bezier(.4,0,.2,1);}

.rtag{
  display:inline-flex;align-items:center;gap:6px;
  background:linear-gradient(135deg,rgba(74,154,90,.12),rgba(74,154,90,.06));
  border:1.5px solid rgba(74,154,90,.4);
  color:var(--green);font-size:11px;padding:5px 12px;border-radius:20px;
  margin-top:8px;font-weight:600;text-transform:uppercase;letter-spacing:.5px;
  animation:pg 2s ease-in-out infinite;
}
@keyframes pg{0%,100%{box-shadow:0 0 0 0 rgba(74,154,90,0);}50%{box-shadow:0 0 10px 2px rgba(74,154,90,.2);}}

.cmeta{font-size:11px;color:var(--muted);margin-top:10px;}
.cact{display:flex;gap:8px;margin-top:12px;flex-wrap:wrap;}

.empty{text-align:center;padding:60px 20px;color:var(--muted);grid-column:1/-1;}
.eico{font-size:48px;margin-bottom:14px;}

/* ── MODALS ── */
.overlay{display:none;position:fixed;inset:0;background:rgba(26,20,8,.75);backdrop-filter:blur(6px);z-index:500;align-items:center;justify-content:center;padding:16px;}
.overlay.on{display:flex;}
.modal{background:white;border:2px solid rgba(201,168,76,.4);border-radius:22px;padding:28px;width:100%;max-width:420px;animation:mi .25s ease;position:relative;overflow:hidden;}
.modal::before{content:'';position:absolute;top:0;left:0;right:0;height:4px;background:linear-gradient(90deg,var(--g3),var(--g1),var(--g2));}
@keyframes mi{from{opacity:0;transform:scale(.95) translateY(-8px);}to{opacity:1;transform:none;}}
.modal h2{font-family:'Playfair Display',serif;font-style:italic;font-size:22px;color:var(--g3);margin-bottom:6px;margin-top:4px;}
.modal p{font-size:13px;color:var(--muted);margin-bottom:16px;}
.mbtns{display:flex;gap:10px;justify-content:flex-end;margin-top:20px;}

/* ══════════════════════════════════
   CARTE CLIENT VISUELLE (screenshot)
══════════════════════════════════ */
#card-wrap{
  position:fixed;left:-9999px;top:0;
  width:700px;z-index:-1;
  background:white;
}

.ccard{
  width:700px;
  font-family:'Jost',sans-serif;
  position:relative;overflow:hidden;
  background:white;
}

/* Fond marbre */
.ccard-bg{
  position:absolute;inset:0;
  background:
    radial-gradient(ellipse at 10% 15%, rgba(201,168,76,.12) 0%, transparent 40%),
    radial-gradient(ellipse at 90% 85%, rgba(201,168,76,.1) 0%, transparent 40%),
    linear-gradient(160deg, #FDFBF7 0%, #F5F0E8 40%, #EDE6D6 100%);
}
/* Veines marbre SVG */
.ccard-marble{
  position:absolute;inset:0;
  opacity:.18;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='700' height='420'%3E%3Cpath d='M0 80 Q 150 60 300 100 T 700 80' stroke='%23C9A84C' fill='none' stroke-width='1.5'/%3E%3Cpath d='M0 180 Q 200 160 350 200 T 700 170' stroke='%23C9A84C' fill='none' stroke-width='1'/%3E%3Cpath d='M0 300 Q 250 280 500 320 T 700 300' stroke='%23C9A84C' fill='none' stroke-width='1.5'/%3E%3Cpath d='M100 0 Q 120 150 80 300 T 150 420' stroke='%23C9A84C' fill='none' stroke-width='.8'/%3E%3Cpath d='M550 0 Q 530 200 560 380 T 600 420' stroke='%23C9A84C' fill='none' stroke-width='.8'/%3E%3C/svg%3E");
}

/* Ornements coins */
.ccard-corner{
  position:absolute;
  width:100px;height:100px;
}
.ccard-corner svg{width:100%;height:100%;}
.cc-tl{top:0;left:0;}
.cc-tr{top:0;right:0;transform:scaleX(-1);}
.cc-bl{bottom:0;left:0;transform:scaleY(-1);}
.cc-br{bottom:0;right:0;transform:scale(-1);}

/* Ornement haut centre */
.ccard-top-orn{
  position:absolute;top:8px;left:50%;transform:translateX(-50%);
  white-space:nowrap;
}

.ccard-inner{position:relative;z-index:2;padding:28px 36px 24px;}

/* Header carte */
.cv-hdr{
  display:flex;align-items:center;justify-content:space-between;
  margin-bottom:20px;
  padding-bottom:16px;
  border-bottom:1.5px solid rgba(201,168,76,.3);
}
.cv-hdr-logo{text-align:center;}
.cv-bsp{font-family:'Pinyon Script',cursive;font-size:44px;color:var(--g3);line-height:.9;}
.cv-nancy{font-size:10px;text-transform:uppercase;letter-spacing:5px;color:var(--muted);margin-top:4px;}
.cv-fidelite{
  font-family:'Playfair Display',serif;
  font-style:italic;font-size:15px;
  color:var(--muted);text-align:center;
}
.cv-client-name{
  font-family:'Playfair Display',serif;
  font-style:italic;font-size:26px;
  color:var(--g3);text-align:right;
}
.cv-card-label{font-size:10px;text-transform:uppercase;letter-spacing:3px;color:var(--muted);text-align:right;margin-bottom:4px;}

/* Points gros */
.cv-pts-zone{
  display:flex;align-items:center;justify-content:space-between;
  margin-bottom:16px;
}
.cv-pts-main{text-align:center;}
.cv-pts-big{
  font-family:'Playfair Display',serif;
  font-size:72px;font-weight:700;
  color:var(--g1);line-height:1;
  text-shadow:2px 2px 0 rgba(139,107,26,.2);
}
.cv-pts-lbl{font-size:11px;text-transform:uppercase;letter-spacing:2px;color:var(--muted);margin-top:2px;}
.cv-pts-info{text-align:right;}
.cv-pts-info p{font-size:13px;color:var(--muted);margin-bottom:4px;}
.cv-pts-info span{color:var(--g3);font-weight:600;font-size:16px;}

/* Cercles style BSP original */
.cv-circles{
  display:flex;gap:8px;justify-content:center;flex-wrap:wrap;
  margin:16px 0 14px;
}
.cv-circ{
  width:38px;height:38px;border-radius:50%;
  border:2px solid rgba(201,168,76,.35);
  background:rgba(201,168,76,.06);
  position:relative;overflow:hidden;transition:all .3s;
}
.cv-circ.f{
  background:linear-gradient(135deg,var(--g3),var(--g1));
  border-color:var(--g3);
  box-shadow:0 2px 8px rgba(139,107,26,.3);
}
.cv-circ.f::after{
  content:'✦';
  position:absolute;inset:0;
  display:flex;align-items:center;justify-content:center;
  color:white;font-size:14px;font-weight:bold;
}

/* Progress */
.cv-prog-lbl{display:flex;justify-content:space-between;font-size:11px;color:var(--muted);margin-bottom:6px;}
.cv-prog{height:8px;background:rgba(201,168,76,.15);border-radius:4px;overflow:hidden;border:1px solid rgba(201,168,76,.25);}
.cv-prog-f{height:100%;background:linear-gradient(to right,var(--g3),var(--g2));border-radius:4px;}

/* Reward block */
.cv-rew{
  background:linear-gradient(135deg,rgba(74,154,90,.1),rgba(74,154,90,.04));
  border:1.5px solid rgba(74,154,90,.4);
  border-radius:12px;padding:12px 18px;
  display:flex;align-items:center;gap:12px;margin-top:14px;
}
.cv-rew-ico{font-size:28px;}
.cv-rew-t{color:var(--green);font-weight:700;font-size:15px;}
.cv-rew-s{color:var(--muted);font-size:12px;margin-top:2px;}

/* Next block */
.cv-next{
  background:rgba(201,168,76,.08);border:1px solid rgba(201,168,76,.2);
  border-radius:10px;padding:10px 16px;margin-top:12px;
  font-size:13px;color:var(--muted);text-align:center;
}
.cv-next b{color:var(--g3);}

/* Jërëjëf section */
.cv-jerejef{
  text-align:center;
  margin-top:18px;padding-top:14px;
  border-top:1px solid rgba(201,168,76,.25);
}
.cv-jerejef-word{
  font-family:'Pinyon Script',cursive;
  font-size:42px;color:var(--g1);
  line-height:1;
  text-shadow:1px 1px 0 rgba(139,107,26,.15);
}
.cv-jerejef-sub{font-size:11px;text-transform:uppercase;letter-spacing:2px;color:var(--muted);margin-top:4px;}

/* Footer */
.cv-footer{
  display:flex;align-items:center;justify-content:space-between;
  margin-top:16px;padding-top:12px;
  border-top:1px solid rgba(201,168,76,.2);
}
.cv-social{font-size:11px;color:var(--muted);}
.cv-social strong{color:var(--g3);}
.cv-date{font-size:10px;color:rgba(201,168,76,.5);}
.cv-tagline{font-family:'Playfair Display',serif;font-style:italic;font-size:12px;color:var(--g3);}

/* ── HISTORY ── */
.hlist{display:flex;flex-direction:column;gap:8px;}
.hitem{background:white;border:1px solid rgba(201,168,76,.2);border-radius:10px;padding:12px 16px;display:flex;align-items:center;gap:12px;font-size:13px;box-shadow:0 1px 4px rgba(139,107,26,.05);}
.hdot{width:9px;height:9px;border-radius:50%;flex-shrink:0;}
.da{background:var(--g1)}.dr{background:var(--green)}.dx{background:var(--red)}
.htime{margin-left:auto;font-size:11px;color:var(--muted);white-space:nowrap;}

/* ── STATS ── */
.sg{display:grid;grid-template-columns:repeat(auto-fill,minmax(190px,1fr));gap:14px;margin-bottom:28px;}
.sc{background:white;border:1px solid rgba(201,168,76,.25);border-radius:16px;padding:22px;text-align:center;box-shadow:0 2px 12px rgba(139,107,26,.07);position:relative;overflow:hidden;}
.sc::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:linear-gradient(90deg,var(--g3),var(--g1),var(--g2));}
.sc .si{font-size:26px;margin-bottom:8px;}
.sc .sv{font-family:'Playfair Display',serif;font-size:36px;color:var(--g3);line-height:1;}
.sc .sl{font-size:11px;text-transform:uppercase;letter-spacing:1.5px;color:var(--muted);margin-top:5px;}

/* ── SETTINGS ── */
.ss{background:white;border:1px solid rgba(201,168,76,.25);border-radius:16px;padding:22px;margin-bottom:18px;box-shadow:0 2px 12px rgba(139,107,26,.07);}
.ss h3{font-family:'Playfair Display',serif;font-style:italic;font-size:18px;color:var(--g3);margin-bottom:16px;padding-bottom:10px;border-bottom:1px solid rgba(201,168,76,.2);}
.sr{display:flex;align-items:center;justify-content:space-between;padding:11px 0;border-bottom:1px solid rgba(201,168,76,.08);gap:14px;}
.sr:last-child{border:none;}
.stitle{font-size:13px;color:var(--text);}.sdesc{font-size:11px;color:var(--muted);margin-top:2px;}
.sr input{width:110px;text-align:center;}
.sr input[type="text"]{width:190px;text-align:left;}

/* ── TOAST ── */
.toast{position:fixed;bottom:20px;right:20px;background:linear-gradient(135deg,var(--dark),#2A2010);border:1px solid rgba(201,168,76,.4);border-radius:10px;padding:12px 18px;font-size:13px;color:var(--g2);box-shadow:0 8px 30px rgba(139,107,26,.3);transform:translateY(80px);opacity:0;transition:all .3s ease;z-index:9999;max-width:280px;}
.toast.on{transform:none;opacity:1;}

/* CARTE PREVIEW MODAL */
#m-card .modal{max-width:750px;background:var(--marble);}
#card-preview-img{width:100%;border-radius:14px;display:block;margin-bottom:16px;border:1px solid rgba(201,168,76,.3);box-shadow:0 4px 20px rgba(139,107,26,.15);}
.share-btns{display:flex;gap:10px;flex-wrap:wrap;justify-content:center;}

@media(max-width:580px){.row{flex-direction:column;}.hpills{display:none;}.page{padding:16px 12px;}.sr{flex-direction:column;align-items:flex-start;}.sr input{width:100%;}}
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="hlogo">
    <div class="ornement">
      <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
        <defs><linearGradient id="og" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#F0D080"/><stop offset="100%" stop-color="#8B6B1A"/></linearGradient></defs>
        <circle cx="48" cy="50" r="36" fill="none" stroke="url(#og)" stroke-width="2.5"/>
        <text x="14" y="58" font-family="Georgia,serif" font-style="italic" font-weight="bold" font-size="34" fill="url(#og)" letter-spacing="-1">BSP</text>
        <text x="28" y="72" font-family="Georgia,serif" font-size="9" fill="url(#og)" letter-spacing="3">NANCY</text>
        <g transform="translate(75,62) scale(.5)">
          <ellipse cx="0" cy="-20" rx="9" ry="18" fill="none" stroke="url(#og)" stroke-width="2" transform="rotate(0)"/>
          <ellipse cx="0" cy="-20" rx="9" ry="18" fill="none" stroke="url(#og)" stroke-width="2" transform="rotate(72)"/>
          <ellipse cx="0" cy="-20" rx="9" ry="18" fill="none" stroke="url(#og)" stroke-width="2" transform="rotate(144)"/>
          <ellipse cx="0" cy="-20" rx="9" ry="18" fill="none" stroke="url(#og)" stroke-width="2" transform="rotate(216)"/>
          <ellipse cx="0" cy="-20" rx="9" ry="18" fill="none" stroke="url(#og)" stroke-width="2" transform="rotate(288)"/>
          <circle cx="0" cy="0" r="3.5" fill="url(#og)"/>
        </g>
      </svg>
    </div>
    <div>
      <div class="bname">BSP Nancy</div>
      <div class="bsub">Programme Fidélité · Jërëjëf</div>
    </div>
  </div>
  <div class="hpills">
    <div class="hp"><strong id="h-c">0</strong>Clients</div>
    <div class="hp"><strong id="h-r">0</strong>🎁 Dispo</div>
  </div>
</header>

<!-- TABS -->
<nav class="tabs">
  <button class="tab on" onclick="go('clients',this)">👥 Clients</button>
  <button class="tab" onclick="go('histo',this)">📋 Historique</button>
  <button class="tab" onclick="go('stats',this)">📊 Stats</button>
  <button class="tab" onclick="go('config',this)">⚙️ Réglages</button>
</nav>

<div class="page">

<!-- ═══ CLIENTS ═══ -->
<div id="s-clients" class="sec on">
  <div class="qa">
    <div class="sh"><div class="sh-txt">✨ Ajouter ou créditer</div><div class="sh-line"></div><div class="sh-orn">❧</div></div>
    <div class="row">
      <div class="fg"><label>Prénom & Nom *</label><input type="text" id="i-name" placeholder="ex : Fatou Diallo" autocomplete="off"/></div>
      <div class="fg"><label>Téléphone</label><input type="tel" id="i-phone" placeholder="06 XX XX XX XX"/></div>
      <div class="fg" style="max-width:150px;"><label>Montant (€)</label><input type="number" id="i-amt" placeholder="ex : 10" min="0" step="0.5" oninput="pp()"/></div>
    </div>
    <div class="qa-bot">
      <button class="btn bg" onclick="doAdd()">＋ Valider</button>
      <button class="btn bo" onclick="clearF()">Effacer</button>
      <span class="pts-hint" id="pth"></span>
    </div>
  </div>
  <div class="frow">
    <button class="chip on" onclick="setF('all',this)">Tous</button>
    <button class="chip" onclick="setF('reward',this)">🎁 Récompense dispo</button>
    <button class="chip" onclick="setF('top',this)">⭐ Top clients</button>
    <div class="sw"><span>🔍</span><input type="text" id="srch" placeholder="Rechercher…" oninput="render()"/></div>
  </div>
  <div class="grid" id="grid"></div>
</div>

<!-- ═══ HISTORIQUE ═══ -->
<div id="s-histo" class="sec">
  <div class="sh"><div class="sh-txt">📋 Historique</div><div class="sh-line"></div></div>
  <div class="hlist" id="hlist"></div>
</div>

<!-- ═══ STATS ═══ -->
<div id="s-stats" class="sec">
  <div class="sh"><div class="sh-txt">📊 Vue d'ensemble</div><div class="sh-line"></div></div>
  <div class="sg" id="sg"></div>
</div>

<!-- ═══ CONFIG ═══ -->
<div id="s-config" class="sec">
  <div class="sh"><div class="sh-txt">⚙️ Paramètres</div><div class="sh-line"></div></div>
  <div class="ss">
    <h3>Règles de fidélité</h3>
    <div class="sr"><div><div class="stitle">Points par euro</div><div class="sdesc">1€ = X points crédités</div></div><input type="number" id="c-ppp" value="1" min="1" max="10" onchange="saveCfg()"/></div>
    <div class="sr"><div><div class="stitle">Seuil récompense (pts)</div><div class="sdesc">Points pour déclencher le cadeau</div></div><input type="number" id="c-thr" value="35" min="1" onchange="saveCfg()"/></div>
    <div class="sr"><div><div class="stitle">Récompense offerte</div><div class="sdesc">Texte sur la carte client</div></div><input type="text" id="c-rew" value="1 Bissap 33cl offert !" onchange="saveCfg()"/></div>
    <div class="sr"><div><div class="stitle">Nombre de cercles affichés</div><div class="sdesc">Cercles sur la carte (style BSP)</div></div><input type="number" id="c-circ" value="12" min="5" max="20" onchange="saveCfg()"/></div>
  </div>
  <div class="ss">
    <h3>Données</h3>
    <div class="sr"><div><div class="stitle">Exporter CSV</div><div class="sdesc">Compatible Excel / Google Sheets</div></div><button class="btn bo bsm" onclick="exportCSV()">📥 Exporter</button></div>
    <div class="sr"><div><div class="stitle">Réinitialiser</div><div class="sdesc">⚠️ Irréversible</div></div><button class="btn bsm" style="background:white;border:1.5px solid rgba(192,80,80,.4);color:var(--red)" onclick="askReset()">🗑 Effacer</button></div>
  </div>
</div>

</div><!-- /page -->

<!-- ══════════════ CARTE CACHÉE (screenshot) ══════════════ -->
<div id="card-wrap">
<div class="ccard" id="ccard">
  <div class="ccard-bg"></div>
  <div class="ccard-marble"></div>

  <!-- Coins ornements -->
  <div class="ccard-corner cc-tl">
    <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" opacity=".5">
      <path d="M5,5 Q40,5 40,40 M5,5 Q5,40 40,40" fill="none" stroke="#C9A84C" stroke-width="1.5"/>
      <circle cx="5" cy="5" r="3" fill="#C9A84C" opacity=".6"/>
      <path d="M15,5 Q20,10 15,15 Q10,20 5,15" fill="none" stroke="#C9A84C" stroke-width="1"/>
      <path d="M5,25 Q15,20 25,25 Q20,35 5,35" fill="none" stroke="#C9A84C" stroke-width="1"/>
      <circle cx="30" cy="10" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/>
      <circle cx="10" cy="30" r="2" fill="none" stroke="#C9A84C" stroke-width="1"/>
    </svg>
  </div>
  <div class="ccard-corner cc-tr">
    <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" opacity=".5">
      <path d="M5,5 Q40,5 40,40 M5,5 Q5,40 40,40" fill="none" stroke="#C9A84C" stroke-width="1.5"/>
      <circle cx="5" cy="5" r="3" fill="#C9A84C" opacity=".6"/>
      <path d="M15,5 Q20,10 15,15 Q10,20 5,15" fill="none" stroke="#C9A84C" stroke-width="1"/>
      <path d="M5,25 Q15,20 25,25 Q20,35 5,35" fill="none" stroke="#C9A84C" stroke-width="1"/>
    </svg>
  </div>
  <div class="ccard-corner cc-bl">
    <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" opacity=".5">
      <path d="M5,5 Q40,5 40,40 M5,5 Q5,40 40,40" fill="none" stroke="#C9A84C" stroke-width="1.5"/>
      <circle cx="5" cy="5" r="3" fill="#C9A84C" opacity=".6"/>
      <path d="M15,5 Q20,10 15,15 Q10,20 5,15" fill="none" stroke="#C9A84C" stroke-width="1"/>
    </svg>
  </div>
  <div class="ccard-corner cc-br">
    <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg" opacity=".5">
      <path d="M5,5 Q40,5 40,40 M5,5 Q5,40 40,40" fill="none" stroke="#C9A84C" stroke-width="1.5"/>
      <circle cx="5" cy="5" r="3" fill="#C9A84C" opacity=".6"/>
      <path d="M15,5 Q20,10 15,15 Q10,20 5,15" fill="none" stroke="#C9A84C" stroke-width="1"/>
    </svg>
  </div>

  <!-- Ornement haut centre -->
  <div class="ccard-top-orn">
    <svg width="200" height="20" viewBox="0 0 200 20" xmlns="http://www.w3.org/2000/svg">
      <path d="M10,10 Q50,2 100,10 Q150,18 190,10" fill="none" stroke="#C9A84C" stroke-width="1" opacity=".5"/>
      <circle cx="100" cy="10" r="3" fill="#C9A84C" opacity=".6"/>
      <circle cx="80" cy="10" r="1.5" fill="#C9A84C" opacity=".4"/>
      <circle cx="120" cy="10" r="1.5" fill="#C9A84C" opacity=".4"/>
      <path d="M40,10 L60,6 M160,10 L140,6" stroke="#C9A84C" stroke-width=".8" opacity=".4"/>
    </svg>
  </div>

  <div class="ccard-inner">
    <!-- Header -->
    <div class="cv-hdr">
      <div class="cv-hdr-logo">
        <div class="cv-bsp">BSP</div>
        <div class="cv-nancy">Nancy</div>
      </div>
      <div style="text-align:center;">
        <div class="cv-fidelite">✦ Programme Fidélité ✦</div>
        <div style="font-size:10px;color:#9A8A6A;text-transform:uppercase;letter-spacing:2px;margin-top:4px;">Bissap Artisanal · 100% Naturel</div>
      </div>
      <div>
        <div class="cv-card-label">Carte de</div>
        <div class="cv-client-name" id="cv-name">—</div>
      </div>
    </div>

    <!-- Points -->
    <div class="cv-pts-zone">
      <div class="cv-pts-main">
        <div class="cv-pts-big" id="cv-pts">0</div>
        <div class="cv-pts-lbl">points acquis</div>
      </div>
      <div class="cv-pts-info">
        <p>Objectif : <span id="cv-thr">30</span> pts</p>
        <p>Manquants : <span id="cv-left">—</span> pts</p>
        <p>Récompenses : <span id="cv-ru">0</span> 🎁</p>
      </div>
    </div>

    <!-- Cercles style BSP -->
    <div class="cv-circles" id="cv-circles"></div>

    <!-- Progress bar -->
    <div>
      <div class="cv-prog-lbl"><span>Progression</span><span id="cv-pct">0%</span></div>
      <div class="cv-prog"><div class="cv-prog-f" id="cv-fill" style="width:0%"></div></div>
    </div>

    <!-- Reward / Next -->
    <div id="cv-rew-block" style="display:none" class="cv-rew">
      <div class="cv-rew-ico">🎁</div>
      <div><div class="cv-rew-t" id="cv-rew-t">Récompense disponible !</div><div class="cv-rew-s">Présentez cette carte lors de votre prochain achat</div></div>
    </div>
    <div id="cv-next-block" class="cv-next">
      Encore <b id="cv-next-n">—</b> pts pour : <b id="cv-next-r">—</b> 🌺
    </div>

    <!-- Jërëjëf -->
    <div class="cv-jerejef">
      <div class="cv-jerejef-word">Jërëjëf</div>
      <div class="cv-jerejef-sub">Merci pour votre confiance · Thank you</div>
    </div>

    <!-- Footer -->
    <div class="cv-footer">
      <div class="cv-social">📸 <strong>@bsp54_</strong> &nbsp;·&nbsp; 👻 <strong>bsp_54</strong></div>
      <div class="cv-tagline">Rafraîchis ta journée 🌺</div>
      <div class="cv-date" id="cv-date">—</div>
    </div>
  </div>
</div>
</div><!-- /card-wrap -->

<!-- MODAL CRÉDITER -->
<div class="overlay" id="m-cred">
  <div class="modal">
    <h2 id="mc-t">Créditer</h2><p id="mc-s">—</p>
    <div class="fg"><label>Montant de l'achat (€)</label><input type="number" id="mc-a" placeholder="ex: 15" min="0" step="0.5" oninput="mcp()"/></div>
    <p id="mc-h" style="margin-top:8px;font-size:13px;color:var(--g3);font-style:italic;font-family:'Playfair Display',serif;margin-bottom:0;"></p>
    <div class="mbtns"><button class="btn bo" onclick="closeM('m-cred')">Annuler</button><button class="btn bg" onclick="submitCred()">Valider ✓</button></div>
  </div>
</div>

<!-- MODAL RÉCOMPENSE -->
<div class="overlay" id="m-red">
  <div class="modal">
    <h2>🎁 Utiliser la récompense</h2><p id="mr-t">—</p>
    <div class="mbtns"><button class="btn bo" onclick="closeM('m-red')">Annuler</button><button class="btn bgr" onclick="doRedeem()">Confirmer ✓</button></div>
  </div>
</div>

<!-- MODAL CARTE -->
<div class="overlay" id="m-card">
  <div class="modal" style="max-width:750px;">
    <h2>📲 Carte prête !</h2>
    <p style="background:rgba(201,168,76,.12);border:1px solid rgba(201,168,76,.3);border-radius:8px;padding:10px 14px;color:#8B6B1A;font-size:13px;">📸 Appuie sur <strong>Plein écran</strong> puis fais un <strong>screenshot iPhone</strong> (bouton latéral + volume haut en même temps) → la carte va dans ta galerie !</p>
    <img id="card-preview-img" src="" alt="Carte client BSP" style="margin-top:12px;"/>
    <div class="share-btns">
      <button class="btn bg" onclick="downloadCard()">📸 Plein écran</button>
      <button class="btn bwa" onclick="shareWA()">📲 WhatsApp</button>
      <button class="btn bo" onclick="closeM('m-card')">Fermer</button>
    </div>
  </div>
</div>

<div id="fullscreen-card" style="display:none;position:fixed;inset:0;z-index:9000;background:#000;flex-direction:column;align-items:center;justify-content:center;">
  <div style="position:absolute;top:0;left:0;right:0;background:linear-gradient(135deg,#1A1408,#2A2010);padding:14px 20px;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid rgba(201,168,76,.3);z-index:1;">
    <span style="color:#C9A84C;font-size:14px;">📸 <strong>Screenshot maintenant !</strong></span>
    <button onclick="document.getElementById('fullscreen-card').style.display='none'" style="background:rgba(201,168,76,.2);border:1px solid rgba(201,168,76,.4);color:#C9A84C;padding:8px 18px;border-radius:8px;font-size:14px;cursor:pointer;">✕ Fermer</button>
  </div>
  <img id="fullscreen-img" src="" style="width:100%;max-height:calc(100vh - 110px);object-fit:contain;margin-top:56px;display:block;"/>
  <div style="position:absolute;bottom:0;left:0;right:0;padding:12px 20px;text-align:center;background:linear-gradient(to top,rgba(0,0,0,.9),transparent);">
    <span style="color:#C9A84C;font-size:13px;">Bouton latéral + Volume haut simultanément 📱 → galerie Photos</span>
  </div>
</div>

<!-- MODAL RESET -->
<div class="overlay" id="m-rst">
  <div class="modal">
    <h2 style="color:var(--red)">⚠️ Confirmer</h2>
    <p>Toutes les données clients seront supprimées définitivement.</p>
    <div class="mbtns"><button class="btn bo" onclick="closeM('m-rst')">Annuler</button><button class="btn bsm" style="background:var(--red);color:white;border:none;" onclick="doReset()">Tout effacer</button></div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
/* ═══ STATE ═══ */
let C=JSON.parse(localStorage.getItem('bsp4_c')||'[]');
let H=JSON.parse(localStorage.getItem('bsp4_h')||'[]');
let S=JSON.parse(localStorage.getItem('bsp4_s')||'{"ppp":1,"thr":35,"rew":"1 Bissap 33cl offert !","circ":12}');
let aid=null,cardUrl=null,cardName='';

function init(){
  document.getElementById('c-ppp').value=S.ppp;
  document.getElementById('c-thr').value=S.thr;
  document.getElementById('c-rew').value=S.rew;
  document.getElementById('c-circ').value=S.circ||12;
  render();
}

/* ═══ TABS ═══ */
function go(n,el){
  document.querySelectorAll('.sec').forEach(s=>s.classList.remove('on'));
  document.querySelectorAll('.tab').forEach(b=>b.classList.remove('on'));
  document.getElementById('s-'+n).classList.add('on');el.classList.add('on');
  if(n==='histo')rH();if(n==='stats')rS();
}

/* ═══ FILTER ═══ */
let cf='all';
function setF(f,el){cf=f;document.querySelectorAll('.chip').forEach(c=>c.classList.remove('on'));el.classList.add('on');render();}

function pp(){const v=parseFloat(document.getElementById('i-amt').value)||0;const p=Math.floor(v*S.ppp);document.getElementById('pth').textContent=p>0?`= ${p} point${p>1?'s':''}`:''; }
function mcp(){const v=parseFloat(document.getElementById('mc-a').value)||0;const p=Math.floor(v*S.ppp);document.getElementById('mc-h').textContent=p>0?`+ ${p} point${p>1?'s':''}`:'';}

/* ═══ ADD/CREDIT ═══ */
function doAdd(){
  const name=document.getElementById('i-name').value.trim();
  const phone=document.getElementById('i-phone').value.trim();
  const amt=parseFloat(document.getElementById('i-amt').value)||0;
  if(!name){toast('❌ Entrez un nom');return;}
  const pts=Math.floor(amt*S.ppp);
  const ex=C.find(c=>c.n.toLowerCase()===name.toLowerCase());
  if(ex){ex.p+=pts;ex.spent=(ex.spent||0)+amt;ex.last=now();if(phone)ex.ph=phone;addH('a',`${ex.n} — +${pts}pts (${amt}€)`);toast(`✓ +${pts} pts → ${ex.n}`);}
  else{C.push({id:Date.now(),n:name,ph:phone,p:pts,spent:amt,ru:0,joined:now(),last:now()});addH('a',`Nouveau : ${name} — +${pts}pts`);toast(`✓ ${name} ajouté`);}
  save();clearF();render();
}
function clearF(){['i-name','i-phone','i-amt'].forEach(id=>document.getElementById(id).value='');document.getElementById('pth').textContent='';}

/* ═══ MODAL CREDIT ═══ */
function openCred(id){aid=id;const c=C.find(x=>x.id===id);document.getElementById('mc-t').textContent=`Créditer ${c.n}`;document.getElementById('mc-s').textContent=`Points actuels : ${c.p}`;document.getElementById('mc-a').value='';document.getElementById('mc-h').textContent='';document.getElementById('m-cred').classList.add('on');}
function submitCred(){const amt=parseFloat(document.getElementById('mc-a').value)||0;if(amt<=0){toast('❌ Montant invalide');return;}const c=C.find(x=>x.id===aid);const pts=Math.floor(amt*S.ppp);c.p+=pts;c.spent=(c.spent||0)+amt;c.last=now();addH('a',`${c.n} — +${pts}pts (${amt}€)`);save();render();closeM('m-cred');toast(`✓ +${pts} pts → ${c.n}`);}

/* ═══ REDEEM ═══ */
function openRed(id){aid=id;const c=C.find(x=>x.id===id);document.getElementById('mr-t').textContent=`${c.n} — "${S.rew}"`;document.getElementById('m-red').classList.add('on');}
function doRedeem(){const c=C.find(x=>x.id===aid);c.p-=S.thr;c.ru=(c.ru||0)+1;addH('r',`${c.n} — Récompense : ${S.rew}`);save();render();closeM('m-red');toast(`🎁 Récompense validée pour ${c.n} !`);}

/* ═══ DELETE ═══ */
function del(id){const c=C.find(x=>x.id===id);if(!confirm(`Supprimer ${c.n} ?`))return;addH('x',`Supprimé : ${c.n}`);C=C.filter(x=>x.id!==id);save();render();toast('Client supprimé');}

/* ═══ RENDER ═══ */
function render(){
  const g=document.getElementById('grid');
  const q=(document.getElementById('srch').value||'').toLowerCase();
  let list=[...C];
  if(q)list=list.filter(c=>c.n.toLowerCase().includes(q)||(c.ph||'').includes(q));
  if(cf==='reward')list=list.filter(c=>c.p>=S.thr);
  if(cf==='top')list=[...list].sort((a,b)=>(b.spent||0)-(a.spent||0));
  else list=list.sort((a,b)=>b.p-a.p);
  document.getElementById('h-c').textContent=C.length;
  document.getElementById('h-r').textContent=C.filter(c=>c.p>=S.thr).length;
  if(!list.length){g.innerHTML=`<div class="empty"><div class="eico">🌺</div><p>${q?'Aucun résultat':'Aucun client — ajoutez-en un !'}</p></div>`;return;}
  const nc=S.circ||12;
  g.innerHTML=list.map(c=>{
    const pct=Math.min(100,Math.round(c.p/S.thr*100));
    const hasR=c.p>=S.thr;
    const ini=c.n.split(' ').map(w=>w[0]||'').join('').slice(0,2).toUpperCase();
    const d=c.last?new Date(c.last).toLocaleDateString('fr-FR'):'—';
    const filled=Math.min(nc,Math.floor(c.p/(S.thr/nc)));
    const circs=Array.from({length:nc},(_,i)=>`<div class="circ${i<filled?' filled':''}"></div>`).join('');
    return `<div class="cc${hasR?' hr':''}">
      <div class="cctop">
        <div class="av">${ini}</div>
        <div class="ci"><div class="cn">${c.n}</div><div class="cp">${c.ph||'—'}</div></div>
        <button class="bgh" onclick="del(${c.id})" title="Supprimer">✕</button>
      </div>
      <div class="circles-row">${circs}</div>
      <div class="pb">
        <div class="pbl"><span>Fidélité</span><strong>${c.p} / ${S.thr} pts</strong></div>
        <div class="pbar"><div class="pbf" style="width:${pct}%"></div></div>
      </div>
      ${hasR?`<div class="rtag">🎁 ${S.rew}</div>`:''}
      <div class="cmeta">Dernier achat : ${d} · Total : ${(c.spent||0).toFixed(2)}€ · 🎁 ×${c.ru||0}</div>
      <div class="cact">
        <button class="btn bg bsm" onclick="openCred(${c.id})">＋ Achat</button>
        <button class="btn bo bsm" onclick="genCard(${c.id})">📲 Envoyer carte</button>
        ${hasR?`<button class="btn bgr bsm" onclick="openRed(${c.id})">🎁 Utiliser</button>`:''}
      </div>
    </div>`;
  }).join('');
}

/* ═══ GÉNÉRATION CARTE — Canvas natif (compatible iOS Safari) ═══ */
function genCard(id){
  const c=C.find(x=>x.id===id);
  const pct=Math.min(100,Math.round(c.p/S.thr*100));
  const hasR=c.p>=S.thr;
  const left=Math.max(0,S.thr-c.p);
  const nc=S.circ||12;
  const filled=Math.min(nc,Math.floor(c.p/(S.thr/nc)));
  cardName=c.n;
  toast('Génération en cours…');

  const W=700, H=480;
  const canvas=document.createElement('canvas');
  canvas.width=W*2; canvas.height=H*2;
  const ctx=canvas.getContext('2d');
  ctx.scale(2,2);

  // ── FOND MARBRE ──
  const bg=ctx.createLinearGradient(0,0,W,H);
  bg.addColorStop(0,'#FDFBF7');
  bg.addColorStop(0.5,'#F5F0E8');
  bg.addColorStop(1,'#EDE6D6');
  ctx.fillStyle=bg; ctx.fillRect(0,0,W,H);

  // Veines marbre
  ctx.save();ctx.globalAlpha=0.12;
  ctx.strokeStyle='#C9A84C';ctx.lineWidth=1.2;
  [[0,70,200,55,700,75],[0,180,250,165,700,175],[0,300,300,285,700,305]].forEach(([x1,y1,cx,cy,x2,y2])=>{
    ctx.beginPath();ctx.moveTo(x1,y1);ctx.quadraticCurveTo(cx,cy,x2,y2);ctx.stroke();
  });
  ctx.restore();

  // ── BORDURE DORÉE ──
  ctx.strokeStyle='#C9A84C';ctx.lineWidth=2.5;
  roundRect(ctx,8,8,W-16,H-16,16);ctx.stroke();
  ctx.strokeStyle='rgba(201,168,76,0.35)';ctx.lineWidth=1;
  roundRect(ctx,14,14,W-28,H-28,13);ctx.stroke();

  // ── ORNEMENTS COINS ──
  drawCorner(ctx,22,22,1,1);
  drawCorner(ctx,W-22,22,-1,1);
  drawCorner(ctx,22,H-22,1,-1);
  drawCorner(ctx,W-22,H-22,-1,-1);

  // ── BANDE TOP DORÉE ──
  const topGrad=ctx.createLinearGradient(0,0,W,0);
  topGrad.addColorStop(0,'#8B6B1A');
  topGrad.addColorStop(0.5,'#C9A84C');
  topGrad.addColorStop(1,'#8B6B1A');
  ctx.fillStyle=topGrad;
  roundRectTop(ctx,8,8,W-16,52,16);ctx.fill();

  // ── BSP (logo texte) ──
  ctx.fillStyle='#FDF0C0';
  ctx.font='bold italic 32px Georgia,serif';
  ctx.fillText('BSP Nancy',24,44);

  // ── LIGNE SÉPARATRICE ──
  ctx.strokeStyle='rgba(201,168,76,0.4)';ctx.lineWidth=1;
  ctx.beginPath();ctx.moveTo(24,68);ctx.lineTo(W-24,68);ctx.stroke();

  // ── PROGRAMME FIDÉLITÉ ──
  ctx.fillStyle='#9A8A6A';
  ctx.font='500 11px Jost,sans-serif';
  ctx.textAlign='center';
  ctx.fillText('✦  PROGRAMME FIDÉLITÉ  ✦',W/2,84);
  ctx.textAlign='left';

  // ── NOM DU CLIENT ──
  ctx.fillStyle='#8B6B1A';
  ctx.font='bold italic 26px Georgia,serif';
  ctx.textAlign='right';
  ctx.fillText(c.n, W-28, 44);
  ctx.font='11px Jost,sans-serif';
  ctx.fillStyle='rgba(139,107,26,0.7)';
  ctx.fillText('Carte de fidélité',W-28,58);
  ctx.textAlign='left';

  // ── POINTS GROS ──
  ctx.font='bold 68px Georgia,serif';
  const goldG=ctx.createLinearGradient(0,90,0,160);
  goldG.addColorStop(0,'#E8C96A');goldG.addColorStop(1,'#8B6B1A');
  ctx.fillStyle=goldG;
  ctx.fillText(String(c.p),30,165);

  ctx.fillStyle='#9A8A6A';
  ctx.font='500 12px Jost,sans-serif';
  ctx.fillText('POINTS ACQUIS',32,182);

  // ── INFOS DROITE ──
  ctx.textAlign='right';
  ctx.fillStyle='#9A8A6A';ctx.font='12px Jost,sans-serif';
  ctx.fillText(`Objectif : ${S.thr} pts`, W-28, 105);
  ctx.fillText(`Manquants : ${hasR?0:left} pts`, W-28, 124);
  ctx.fillText(`Récompenses obtenues : ${c.ru||0} 🎁`, W-28, 143);
  ctx.textAlign='left';

  // ── CERCLES STYLE BSP ──
  const circY=205, circR=15, circSpacing=38;
  const totalW=nc*circSpacing-8;
  const startX=(W-totalW)/2;
  for(let i=0;i<nc;i++){
    const cx=startX+i*circSpacing+circR;
    if(i<filled){
      const cg=ctx.createRadialGradient(cx-4,circY-4,2,cx,circY,circR);
      cg.addColorStop(0,'#E8C96A');cg.addColorStop(1,'#7A5B10');
      ctx.fillStyle=cg;
      ctx.beginPath();ctx.arc(cx,circY,circR,0,Math.PI*2);ctx.fill();
      ctx.fillStyle='white';ctx.font='bold 14px serif';
      ctx.textAlign='center';ctx.fillText('✦',cx,circY+5);ctx.textAlign='left';
      ctx.strokeStyle='#8B6B1A';ctx.lineWidth=1.5;
      ctx.beginPath();ctx.arc(cx,circY,circR,0,Math.PI*2);ctx.stroke();
    } else {
      ctx.strokeStyle='rgba(201,168,76,0.35)';ctx.lineWidth=1.5;
      ctx.fillStyle='rgba(201,168,76,0.06)';
      ctx.beginPath();ctx.arc(cx,circY,circR,0,Math.PI*2);ctx.fill();ctx.stroke();
    }
  }

  // ── BARRE DE PROGRESSION ──
  const barY=238, barH=8, barX=28, barW=W-56;
  ctx.fillStyle='rgba(201,168,76,0.15)';
  roundRect(ctx,barX,barY,barW,barH,4);ctx.fill();
  ctx.strokeStyle='rgba(201,168,76,0.25)';ctx.lineWidth=1;
  roundRect(ctx,barX,barY,barW,barH,4);ctx.stroke();
  if(pct>0){
    const pg=ctx.createLinearGradient(barX,0,barX+barW,0);
    pg.addColorStop(0,'#8B6B1A');pg.addColorStop(1,'#F0D080');
    ctx.fillStyle=pg;
    roundRect(ctx,barX,barY,Math.max(8,barW*(pct/100)),barH,4);ctx.fill();
  }
  ctx.fillStyle='#9A8A6A';ctx.font='10px Jost,sans-serif';
  ctx.textAlign='right';ctx.fillText(pct+'%',W-28,barY-4);ctx.textAlign='left';
  ctx.fillText('Progression',barX,barY-4);

  // ── BLOC RÉCOMPENSE / NEXT ──
  if(hasR){
    ctx.fillStyle='rgba(74,154,90,0.1)';
    roundRect(ctx,28,255,W-56,48,10);ctx.fill();
    ctx.strokeStyle='rgba(74,154,90,0.4)';ctx.lineWidth=1.5;
    roundRect(ctx,28,255,W-56,48,10);ctx.stroke();
    ctx.font='bold 14px Jost,sans-serif';ctx.fillStyle='#4A9A5A';
    ctx.fillText('🎁  '+S.rew,44,275);
    ctx.font='11px Jost,sans-serif';ctx.fillStyle='#9A8A6A';
    ctx.fillText('Présentez cette carte lors de votre prochain achat',44,292);
  } else {
    ctx.fillStyle='rgba(201,168,76,0.08)';
    roundRect(ctx,28,255,W-56,44,10);ctx.fill();
    ctx.strokeStyle='rgba(201,168,76,0.2)';ctx.lineWidth=1;
    roundRect(ctx,28,255,W-56,44,10);ctx.stroke();
    ctx.font='13px Jost,sans-serif';ctx.fillStyle='#9A8A6A';
    ctx.textAlign='center';
    ctx.fillText(`Encore ${left} pts pour : "${S.rew}" 🌺`,W/2,281);
    ctx.textAlign='left';
  }

  // ── JËRËJËF ──
  ctx.strokeStyle='rgba(201,168,76,0.25)';ctx.lineWidth=1;
  ctx.beginPath();ctx.moveTo(28,312);ctx.lineTo(W-28,312);ctx.stroke();

  ctx.font='italic 38px Georgia,serif';
  const jg=ctx.createLinearGradient(0,315,0,355);
  jg.addColorStop(0,'#E8C96A');jg.addColorStop(1,'#8B6B1A');
  ctx.fillStyle=jg;
  ctx.textAlign='center';
  ctx.fillText('Jërëjëf',W/2,350);
  ctx.font='10px Jost,sans-serif';ctx.fillStyle='#9A8A6A';
  ctx.fillText('MERCI POUR VOTRE CONFIANCE  ·  THANK YOU',W/2,367);
  ctx.textAlign='left';

  // ── FOOTER ──
  ctx.strokeStyle='rgba(201,168,76,0.2)';ctx.lineWidth=1;
  ctx.beginPath();ctx.moveTo(28,378);ctx.lineTo(W-28,378);ctx.stroke();

  ctx.font='11px Jost,sans-serif';ctx.fillStyle='#8B6B1A';
  ctx.fillText('📸 @bsp54_   ·   👻 bsp_54',30,398);
  ctx.textAlign='center';
  ctx.font='italic 12px Georgia,serif';ctx.fillStyle='#C9A84C';
  ctx.fillText('Bissap Artisanal · 100% Naturel 🌺',W/2,398);
  ctx.textAlign='right';
  ctx.font='10px Jost,sans-serif';ctx.fillStyle='rgba(201,168,76,0.5)';
  ctx.fillText('Mis à jour le '+new Date().toLocaleDateString('fr-FR'),W-28,398);
  ctx.textAlign='left';

  cardUrl=canvas.toDataURL('image/png');
  document.getElementById('card-preview-img').src=cardUrl;
  document.getElementById('m-card').classList.add('on');
}

/* Helpers Canvas */
function roundRect(ctx,x,y,w,h,r){
  ctx.beginPath();ctx.moveTo(x+r,y);ctx.lineTo(x+w-r,y);ctx.arcTo(x+w,y,x+w,y+r,r);
  ctx.lineTo(x+w,y+h-r);ctx.arcTo(x+w,y+h,x+w-r,y+h,r);ctx.lineTo(x+r,y+h);
  ctx.arcTo(x,y+h,x,y+h-r,r);ctx.lineTo(x,y+r);ctx.arcTo(x,y,x+r,y,r);ctx.closePath();
}
function roundRectTop(ctx,x,y,w,h,r){
  ctx.beginPath();ctx.moveTo(x+r,y);ctx.lineTo(x+w-r,y);ctx.arcTo(x+w,y,x+w,y+r,r);
  ctx.lineTo(x+w,y+h);ctx.lineTo(x,y+h);ctx.lineTo(x,y+r);ctx.arcTo(x,y,x+r,y,r);ctx.closePath();
}
function drawCorner(ctx,x,y,sx,sy){
  ctx.save();ctx.translate(x,y);ctx.scale(sx,sy);
  ctx.strokeStyle='rgba(201,168,76,0.5)';ctx.lineWidth=1;
  ctx.beginPath();ctx.moveTo(0,-18);ctx.lineTo(0,0);ctx.lineTo(18,0);ctx.stroke();
  ctx.fillStyle='rgba(201,168,76,0.6)';
  ctx.beginPath();ctx.arc(0,0,3,0,Math.PI*2);ctx.fill();
  ctx.restore();
}

function downloadCard(){
  if(!cardUrl)return;
  document.getElementById('fullscreen-img').src=cardUrl;
  document.getElementById('fullscreen-card').style.display='flex';
}

function shareWA(){
  const msg=encodeURIComponent(`🌺 *BSP Nancy* — Voici ta carte de fidélité, ${cardName} !\n\nJërëjëf pour ta confiance 🙏\n📸 @bsp54_ | 👻 bsp_54`);
  window.open('https://wa.me/?text='+msg,'_blank');
}

/* ═══ HISTORY ═══ */
function addH(t,txt){H.unshift({t,txt,ts:new Date().toISOString()});if(H.length>300)H.pop();localStorage.setItem('bsp4_h',JSON.stringify(H));}
function rH(){const el=document.getElementById('hlist');if(!H.length){el.innerHTML='<div class="empty"><div class="eico">📋</div><p>Aucune action</p></div>';return;}el.innerHTML=H.slice(0,60).map(h=>{const dc={a:'da',r:'dr',x:'dx'}[h.t];const d=new Date(h.ts);return `<div class="hitem"><div class="hdot ${dc}"></div><span style="flex:1">${h.txt}</span><span class="htime">${d.toLocaleDateString('fr-FR')} ${d.toLocaleTimeString('fr-FR',{hour:'2-digit',minute:'2-digit'})}</span></div>`;}).join('');}

/* ═══ STATS ═══ */
function rS(){const tp=C.reduce((s,c)=>s+c.p,0),ts=C.reduce((s,c)=>s+(c.spent||0),0),tr=C.reduce((s,c)=>s+(c.ru||0),0),wr=C.filter(c=>c.p>=S.thr).length;document.getElementById('sg').innerHTML=[['👥',C.length,'Clients'],['🌟',tp,'Points actifs'],['🎁',tr,'Récompenses utilisées'],['⚡',wr,'Récompenses disponibles'],['💰',ts.toFixed(2)+'€','CA suivi'],['📈',C.length?(ts/C.length).toFixed(2)+'€':'0€','Panier moyen']].map(([ico,v,l])=>`<div class="sc"><div class="si">${ico}</div><div class="sv">${v}</div><div class="sl">${l}</div></div>`).join('');}

/* ═══ CONFIG ═══ */
function saveCfg(){S.ppp=parseInt(document.getElementById('c-ppp').value)||1;S.thr=parseInt(document.getElementById('c-thr').value)||30;S.rew=document.getElementById('c-rew').value||'1 Bissap 33cl offert !';S.circ=parseInt(document.getElementById('c-circ').value)||12;localStorage.setItem('bsp4_s',JSON.stringify(S));render();toast('Réglages sauvegardés ✓');}

/* ═══ EXPORT ═══ */
function exportCSV(){const rows=[['Nom','Téléphone','Points','Total (€)','Récompenses','Dernière visite']];C.forEach(c=>rows.push([c.n,c.ph||'',c.p,(c.spent||0).toFixed(2),c.ru||0,c.last?new Date(c.last).toLocaleDateString('fr-FR'):'']));const csv=rows.map(r=>r.map(v=>`"${v}"`).join(',')).join('\n');const a=document.createElement('a');a.href='data:text/csv;charset=utf-8,\uFEFF'+encodeURIComponent(csv);a.download=`bsp_fidelite_${new Date().toLocaleDateString('fr-FR').replace(/\//g,'-')}.csv`;a.click();toast('📥 Export lancé !');}

/* ═══ RESET ═══ */
function askReset(){document.getElementById('m-rst').classList.add('on');}
function doReset(){C=[];H=[];localStorage.removeItem('bsp4_c');localStorage.removeItem('bsp4_h');save();render();closeM('m-rst');toast('Données effacées');}

/* ═══ UTILS ═══ */
function save(){localStorage.setItem('bsp4_c',JSON.stringify(C));}
function now(){return new Date().toISOString();}
function closeM(id){document.getElementById(id).classList.remove('on');}
document.querySelectorAll('.overlay').forEach(o=>o.addEventListener('click',function(e){if(e.target===o)o.classList.remove('on');}));
function toast(msg){const t=document.getElementById('toast');t.textContent=msg;t.classList.add('on');clearTimeout(t._t);t._t=setTimeout(()=>t.classList.remove('on'),3200);}

init();
</script>
</body
