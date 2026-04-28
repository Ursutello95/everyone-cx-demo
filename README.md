<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MODO — CX Training Center · Demo</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500;9..40,600&display=swap" rel="stylesheet">
<style>
:root{
  --g0:#061a0d;--g1:#0d2e18;--g2:#164023;--g3:#1e5c32;--g4:#2d7a4f;--g5:#4aab72;--g6:#6fcf97;
  --amber:#f7c948;--red:#e05252;
  --cream:#f5f3ee;--cd:rgba(245,243,238,.65);--cm:rgba(245,243,238,.32);
  --r:10px;--rs:6px;
  --fh:'Syne',sans-serif;--fb:'DM Sans',sans-serif;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
body{font-family:var(--fb);background:var(--g0);color:var(--cream);line-height:1.6;overflow-x:hidden;}

/* NAV */
nav{position:fixed;inset:0 0 auto 0;z-index:300;display:flex;align-items:center;justify-content:space-between;padding:.7rem 2rem;background:rgba(6,26,13,.96);backdrop-filter:blur(16px);border-bottom:1px solid rgba(111,207,151,.1);}
.logo{font-family:var(--fh);font-weight:800;font-size:1.25rem;background:var(--cream);color:var(--g0);padding:.18rem .6rem;border-radius:4px;}
.logo-sub{font-size:.63rem;font-weight:500;color:var(--g6);margin-left:.6rem;letter-spacing:.09em;text-transform:uppercase;}
.nav-l{display:flex;align-items:center;}
.nl{display:flex;gap:2px;align-items:center;}
.nl button{background:none;border:none;cursor:pointer;font-family:var(--fb);font-size:.78rem;font-weight:500;color:var(--cd);padding:.38rem .75rem;border-radius:var(--rs);transition:all .18s;white-space:nowrap;}
.nl button:hover{color:var(--cream);background:rgba(111,207,151,.1);}
.nl button.active{color:var(--g6);}
.ncta{background:var(--g6)!important;color:var(--g0)!important;font-weight:700!important;margin-left:.35rem!important;}
.ncta:hover{background:var(--g5)!important;}
.dbadge{background:rgba(247,201,72,.14);color:var(--amber);border:1px solid rgba(247,201,72,.28);border-radius:999px;font-size:.62rem;font-weight:700;padding:.16rem .6rem;letter-spacing:.06em;text-transform:uppercase;margin-left:.7rem;}

/* PAGES */
.page{display:none;min-height:100vh;padding-top:54px;}
.page.active{display:block;}

/* SLIDES */
.slide{display:none;min-height:calc(100vh - 54px);}
.slide.active{display:flex;}
.snav{position:fixed;bottom:1.4rem;left:50%;transform:translateX(-50%);z-index:200;display:flex;align-items:center;gap:.55rem;background:rgba(6,26,13,.96);backdrop-filter:blur(14px);border:1px solid rgba(111,207,151,.22);border-radius:999px;padding:.48rem .95rem;}
.snav button{background:none;border:none;color:var(--cd);cursor:pointer;font-size:.88rem;padding:.13rem .38rem;border-radius:4px;transition:all .15s;font-family:var(--fb);}
.snav button:hover{color:var(--g6);}
.sc{font-size:.72rem;color:var(--cm);min-width:38px;text-align:center;}
.sdots{display:flex;gap:4px;align-items:center;}
.sdot{width:6px;height:6px;border-radius:50%;background:var(--cm);cursor:pointer;transition:all .2s;}
.sdot.active{width:18px;border-radius:999px;background:var(--g6);}

/* SHARED */
.w{padding:3.2rem 5vw 6.5rem;max-width:1120px;margin:0 auto;width:100%;}
.ey{font-size:.65rem;font-weight:700;letter-spacing:.16em;text-transform:uppercase;color:var(--g6);margin-bottom:.45rem;}
.sh{font-family:var(--fh);font-weight:800;font-size:clamp(1.45rem,3.5vw,2.4rem);line-height:1.1;}
.sh em{color:var(--g6);font-style:normal;}
.sd{font-size:.86rem;color:var(--cd);margin-top:.5rem;max-width:600px;line-height:1.75;}
.chip{display:inline-block;font-size:.65rem;font-weight:700;letter-spacing:.09em;text-transform:uppercase;color:var(--g6);padding:.18rem .6rem;border-radius:999px;border:1px solid rgba(111,207,151,.28);margin-bottom:1.1rem;}

/* PORTADA S1 */
.s1{display:grid!important;grid-template-columns:38% 62%;align-items:stretch;}
.s1l{background:var(--g4);padding:4rem 2.5rem 6rem;display:flex;flex-direction:column;justify-content:space-between;border-right:1px solid rgba(111,207,151,.2);}
.s1logo{font-family:var(--fh);font-weight:800;font-size:2.4rem;background:var(--cream);color:var(--g0);display:inline-block;padding:.22rem .85rem;border-radius:5px;margin-bottom:.6rem;}
.s1sub{font-size:.7rem;color:rgba(245,243,238,.48);letter-spacing:.12em;text-transform:uppercase;}
.s1r{background:var(--g2);padding:4rem 3.5rem 6rem;display:flex;flex-direction:column;justify-content:center;}
.s1t{font-family:var(--fh);font-weight:800;font-size:clamp(2rem,5vw,3.8rem);line-height:1.0;margin-bottom:.7rem;}
.s1t em{color:var(--g6);font-style:normal;}
.s1a{font-family:var(--fh);font-weight:700;font-size:.9rem;color:var(--amber);margin-bottom:1.5rem;}
.s1b{font-size:.86rem;color:var(--cd);line-height:1.8;max-width:460px;}

/* PERFILES S2 */
.ptabs{display:flex;gap:.38rem;margin:1.6rem 0 1rem;}
.ptab{background:rgba(111,207,151,.07);border:1px solid rgba(111,207,151,.15);border-radius:999px;padding:.3rem .95rem;font-size:.76rem;font-weight:600;color:var(--cd);cursor:pointer;transition:all .18s;font-family:var(--fb);}
.ptab.active{background:var(--g4);color:var(--cream);border-color:var(--g6);}
.pgrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(145px,1fr));gap:.85rem;}
.pcard{background:var(--g2);border-radius:var(--r);border:1px solid rgba(111,207,151,.1);padding:1.2rem .95rem 1rem;text-align:center;cursor:pointer;transition:all .2s;}
.pcard:hover{border-color:rgba(111,207,151,.4);transform:translateY(-3px);}
.pcard.sel{border-color:var(--g6);background:var(--g3);}
.pe{font-size:2rem;margin-bottom:.4rem;display:block;}
.pbadge{display:inline-block;font-size:.59rem;font-weight:700;padding:.13rem .48rem;border-radius:999px;margin-bottom:.38rem;}
.bp{background:rgba(91,155,213,.2);color:#7ab3e0;}
.be{background:rgba(224,82,82,.2);color:#e88;}
.bv{background:rgba(247,201,72,.18);color:var(--amber);}
.bi{background:rgba(150,100,200,.2);color:#c4a0e8;}
.bpa{background:rgba(224,82,82,.2);color:#e88;}
.bn2{background:rgba(111,207,151,.18);color:var(--g6);}
.bd{background:rgba(91,155,213,.18);color:#7ab3e0;}
.bit{background:rgba(180,130,60,.2);color:#d4a84b;}
.pname{font-family:var(--fh);font-weight:700;font-size:.9rem;margin-bottom:.28rem;}
.pdesc{font-size:.68rem;color:var(--cd);line-height:1.5;}
.pdet{background:var(--g2);border-radius:var(--r);border:1px solid rgba(111,207,151,.2);padding:1.3rem 1.65rem;margin-top:1.2rem;display:none;align-items:center;gap:1.6rem;flex-wrap:wrap;}
.pdet.vis{display:flex;}
.pde{font-size:3rem;}
.pdi{flex:1;min-width:170px;}
.pdn{font-family:var(--fh);font-weight:800;font-size:1.25rem;margin-bottom:.18rem;}
.pdc{font-size:.8rem;color:var(--cd);line-height:1.65;}
.pdtip{background:rgba(247,201,72,.07);border:1px solid rgba(247,201,72,.17);border-radius:var(--rs);padding:.75rem .9rem;font-size:.76rem;color:rgba(245,243,238,.75);line-height:1.6;min-width:190px;}
.pdtip strong{color:var(--amber);}
.bsim{background:var(--g6);color:var(--g0);border:none;border-radius:var(--rs);padding:.58rem 1.2rem;font-weight:700;font-size:.79rem;cursor:pointer;font-family:var(--fb);transition:background .18s;white-space:nowrap;}
.bsim:hover{background:var(--g5);}

/* EVALUACIÓN SLIDE S3 */
.elayout{display:grid;grid-template-columns:168px 1fr;gap:1.3rem;margin-top:1.65rem;}
.esbox{background:var(--g3);border-radius:var(--r);display:flex;flex-direction:column;align-items:center;justify-content:center;padding:1.9rem 1rem;border:1px solid rgba(111,207,151,.2);text-align:center;}
.esn{font-family:var(--fh);font-weight:800;font-size:4rem;line-height:1;color:var(--amber);}
.esd{font-size:.86rem;color:var(--cd);}
.esl{font-size:.6rem;font-weight:700;letter-spacing:.12em;text-transform:uppercase;color:var(--cm);margin-top:.5rem;}
.ess{font-size:.68rem;color:var(--cm);margin-top:.55rem;line-height:1.5;}
.cgrid{display:grid;grid-template-columns:1fr 1fr;gap:.78rem;}
.cc{background:var(--g2);border-radius:var(--rs);padding:1rem 1.15rem;border:1px solid rgba(111,207,151,.1);}
.cctop{display:flex;align-items:center;justify-content:space-between;margin-bottom:.58rem;}
.ccn{font-size:.8rem;font-weight:500;}
.ccv{font-family:var(--fh);font-weight:700;font-size:.85rem;}
.ccbar{height:4px;background:rgba(0,0,0,.3);border-radius:999px;overflow:hidden;}
.ccfill{height:100%;border-radius:999px;transition:width .8s cubic-bezier(.4,0,.2,1);}
.enote{margin-top:1.2rem;padding:.85rem 1.3rem;background:rgba(111,207,151,.06);border:1px solid rgba(111,207,151,.12);border-radius:var(--r);font-size:.79rem;color:var(--cd);line-height:1.65;}

/* ARQUITECTURA S4 */
.agrid{display:grid;grid-template-columns:1fr 1fr;gap:.95rem;margin-top:1.65rem;}
.ac{background:var(--g2);border-radius:var(--r);border:1px solid rgba(111,207,151,.1);padding:1.3rem 1.5rem;display:flex;gap:.85rem;align-items:flex-start;transition:all .2s;}
.ac:hover{border-color:rgba(111,207,151,.3);transform:translateY(-2px);}
.ac.ext{border-color:rgba(247,201,72,.17);}
.ac.ext .at{color:var(--amber);}
.aico{font-size:1.5rem;flex-shrink:0;margin-top:.06rem;}
.at{font-size:.61rem;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--g6);margin-bottom:.16rem;}
.an{font-family:var(--fh);font-weight:700;font-size:.94rem;margin-bottom:.28rem;}
.adesc{font-size:.74rem;color:var(--cd);line-height:1.6;}

/* CRONOGRAMA S5 */
.blocks{display:grid;grid-template-columns:repeat(4,1fr);margin-top:1.65rem;border-radius:var(--r);overflow:hidden;border:1px solid rgba(111,207,151,.1);}
.blk{padding:1.5rem 1.2rem;border-right:1px solid rgba(111,207,151,.08);transition:background .2s;}
.blk:last-child{border-right:none;}
.blk:hover{background:rgba(111,207,151,.05);}
.bln{font-family:var(--fh);font-weight:800;font-size:2.6rem;color:rgba(111,207,151,.11);line-height:1;margin-bottom:.28rem;}
.blt{display:inline-block;background:rgba(247,201,72,.13);color:var(--amber);font-size:.64rem;font-weight:700;padding:.14rem .5rem;border-radius:999px;margin-bottom:.55rem;}
.blname{font-family:var(--fh);font-weight:700;font-size:.88rem;margin-bottom:.55rem;}
.bllist{list-style:none;display:flex;flex-direction:column;gap:.3rem;}
.bllist li{font-size:.71rem;color:var(--cd);padding-left:.75rem;position:relative;line-height:1.5;}
.bllist li::before{content:'·';position:absolute;left:0;color:var(--g6);}
.selrow{display:grid;grid-template-columns:repeat(3,1fr);gap:.85rem;margin-top:1.2rem;}
.selc{background:var(--g2);border-radius:var(--r);padding:1.1rem 1.2rem;border:1px solid rgba(111,207,151,.1);}
.scn{font-family:var(--fh);font-weight:800;font-size:2.2rem;color:var(--g6);}
.sct{font-weight:600;font-size:.84rem;margin:.16rem 0 .25rem;}
.scd{font-size:.71rem;color:var(--cd);}

/* IMPACTO S6 */
.bign{font-family:var(--fh);font-weight:800;font-size:clamp(4.5rem,11vw,8rem);color:var(--g6);line-height:1;}
.bigl{font-size:.9rem;color:var(--cd);margin-bottom:2.5rem;}
.igg{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:.85rem;width:100%;max-width:740px;}
.ig{background:var(--g3);border-radius:var(--r);padding:1.3rem;border:1px solid rgba(111,207,151,.1);}
.ign{font-family:var(--fh);font-weight:800;font-size:2rem;color:var(--amber);}
.igl{font-size:.74rem;color:var(--cd);margin-top:.16rem;line-height:1.5;}

/* ══ SIMULADOR ══ */
.simwrap{padding:3.2rem 5vw 6.5rem;max-width:1080px;margin:0 auto;}
.simshell{border-radius:var(--r);border:1px solid rgba(111,207,151,.2);overflow:hidden;box-shadow:0 20px 60px rgba(0,0,0,.5);background:var(--g1);margin-top:1.65rem;}
.stimbar{background:var(--g4);padding:.72rem 1.3rem;display:flex;align-items:center;justify-content:space-between;}
.stbt{font-family:var(--fh);font-weight:700;font-size:.86rem;}
.livd{width:7px;height:7px;border-radius:50%;background:var(--g6);animation:pulse 2s infinite;}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.5;transform:scale(.8)}}
.livt{font-size:.69rem;color:var(--cd);display:flex;align-items:center;gap:.3rem;}
.sctabs{background:rgba(0,0,0,.2);padding:.55rem 1.05rem;display:flex;gap:.38rem;overflow-x:auto;border-bottom:1px solid rgba(111,207,151,.09);}
.sctab{white-space:nowrap;background:rgba(111,207,151,.07);border:1px solid rgba(111,207,151,.12);border-radius:999px;padding:.28rem .78rem;font-size:.71rem;font-weight:500;color:var(--cd);cursor:pointer;transition:all .18s;font-family:var(--fb);}
.sctab:hover,.sctab.active{background:var(--g3);color:var(--cream);border-color:var(--g6);}
.simbody{display:grid;grid-template-columns:1fr 300px;min-height:460px;}
.chatcol{border-right:1px solid rgba(111,207,151,.09);display:flex;flex-direction:column;}
.msgs{flex:1;padding:1.05rem;display:flex;flex-direction:column;gap:.75rem;overflow-y:auto;max-height:380px;scroll-behavior:smooth;}
.bw{display:flex;flex-direction:column;}
.bw.u{align-items:flex-end;}
.bn{font-size:.61rem;color:var(--cm);margin-bottom:.14rem;}
.bb{max-width:86%;padding:.62rem .9rem;font-size:.81rem;line-height:1.6;border-radius:4px 12px 12px 12px;}
.bb.bot{background:rgba(0,0,0,.28);}
.bb.usr{background:var(--g4);border-radius:12px 4px 12px 12px;}
.inputbar{padding:.85rem 1rem;border-top:1px solid rgba(111,207,151,.09);display:flex;gap:.4rem;}
.si{flex:1;background:rgba(0,0,0,.22);border:1px solid rgba(111,207,151,.16);border-radius:var(--rs);padding:.52rem .88rem;color:var(--cream);font-family:var(--fb);font-size:.81rem;outline:none;transition:border-color .18s;}
.si:focus{border-color:var(--g6);}
.si::placeholder{color:var(--cm);}
.sbtn{background:var(--g6);color:var(--g0);border:none;border-radius:var(--rs);padding:.52rem .95rem;font-weight:700;font-size:.8rem;cursor:pointer;font-family:var(--fb);transition:background .18s;}
.sbtn:hover{background:var(--g5);}
.sbtn:disabled{opacity:.38;cursor:not-allowed;}
.panel{padding:1.1rem;display:flex;flex-direction:column;gap:.95rem;}
.plbl{font-size:.61rem;font-weight:700;letter-spacing:.13em;text-transform:uppercase;color:var(--cm);margin-bottom:.28rem;}
.meter{display:flex;align-items:center;gap:.5rem;margin-bottom:.3rem;}
.ml{font-size:.69rem;width:68px;color:var(--cd);}
.mt{flex:1;height:5px;background:rgba(0,0,0,.32);border-radius:999px;overflow:hidden;}
.mf{height:100%;border-radius:999px;transition:width .6s cubic-bezier(.4,0,.2,1);}
.mv{font-size:.69rem;font-weight:700;width:22px;text-align:right;}
.tip{background:rgba(247,201,72,.07);border:1px solid rgba(247,201,72,.16);border-radius:var(--rs);padding:.75rem .9rem;font-size:.76rem;color:rgba(245,243,238,.76);line-height:1.65;}
.tip strong{color:var(--amber);}
.dots span{animation:db 1.3s infinite;font-size:1.1rem;line-height:1;}
.dots span:nth-child(2){animation-delay:.22s;}
.dots span:nth-child(3){animation-delay:.44s;}
@keyframes db{0%,80%,100%{opacity:.1}40%{opacity:1}}
.typing-cursor::after{content:'|';animation:blink .6s step-end infinite;color:var(--g6);margin-left:1px;}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

/* EVALUACIÓN PAGE */
.evalwrap{padding:3.2rem 5vw 6.5rem;max-width:880px;margin:0 auto;}
.evalshell{background:var(--g1);border-radius:var(--r);border:1px solid rgba(111,207,151,.2);overflow:hidden;margin-top:1.65rem;}
.evalhead{background:var(--g4);padding:.72rem 1.3rem;display:flex;align-items:center;justify-content:space-between;}
.evalheadt{font-family:var(--fh);font-weight:700;font-size:.86rem;}
.evalsel{display:flex;gap:.6rem;align-items:center;font-size:.75rem;color:var(--cd);}
.evalsel select{background:var(--g3);border:1px solid rgba(111,207,151,.17);color:var(--cream);border-radius:var(--rs);padding:.26rem .6rem;font-family:var(--fb);font-size:.73rem;outline:none;cursor:pointer;}
.evalbody{display:grid;grid-template-columns:150px 1fr;gap:0;}
.evalsc{background:var(--g3);padding:1.8rem 1rem;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;border-right:1px solid rgba(111,207,151,.13);}
.evalscore{font-family:var(--fh);font-weight:800;font-size:3.6rem;line-height:1;color:var(--amber);transition:all .4s;}
.evalsden{font-size:.84rem;color:var(--cd);}
.evalslbl{font-size:.59rem;font-weight:700;letter-spacing:.12em;text-transform:uppercase;color:var(--cm);margin-top:.5rem;}
.evalssess{font-size:.66rem;color:var(--cm);margin-top:.55rem;line-height:1.5;}
.evalcrit{padding:1.25rem;display:grid;grid-template-columns:1fr 1fr;gap:.72rem;}
.ec{background:var(--g2);border-radius:var(--rs);padding:.95rem 1.1rem;border:1px solid rgba(111,207,151,.09);}
.ectop{display:flex;align-items:center;justify-content:space-between;margin-bottom:.55rem;}
.ecn{font-size:.78rem;font-weight:500;}
.ecv{font-family:var(--fh);font-weight:700;font-size:.83rem;transition:color .4s;}
.ecbar{height:4px;background:rgba(0,0,0,.3);border-radius:999px;overflow:hidden;}
.ecfill{height:100%;border-radius:999px;transition:width .8s cubic-bezier(.4,0,.2,1);}
.evalnote{padding:.8rem 1.35rem;background:rgba(111,207,151,.05);border-top:1px solid rgba(111,207,151,.09);font-size:.77rem;color:var(--cd);line-height:1.65;}
.evalact{padding:.85rem 1.3rem;display:flex;gap:.6rem;border-top:1px solid rgba(111,207,151,.09);}
.bout{background:transparent;color:var(--cream);border:1px solid rgba(245,243,238,.17);border-radius:var(--rs);padding:.5rem .95rem;font-weight:500;font-size:.77rem;cursor:pointer;font-family:var(--fb);transition:all .2s;}
.bout:hover{border-color:var(--g6);color:var(--g6);}

/* API page */
.apiwrap{padding:3.2rem 5vw 6.5rem;max-width:1080px;margin:0 auto;}
.apigrid{display:grid;grid-template-columns:245px 1fr;gap:1.55rem;margin-top:1.65rem;align-items:start;}
.eplist{display:flex;flex-direction:column;gap:.5rem;}
.ep{background:var(--g2);border-radius:var(--rs);border:1px solid rgba(111,207,151,.1);padding:.78rem .95rem;cursor:pointer;transition:all .18s;}
.ep:hover,.ep.active{border-color:var(--g6);background:var(--g3);}
.em{display:inline-block;font-size:.62rem;font-weight:700;letter-spacing:.06em;padding:.09rem .36rem;border-radius:3px;margin-right:.3rem;}
.get{background:rgba(111,207,151,.17);color:var(--g6);}
.post{background:rgba(247,201,72,.17);color:var(--amber);}
.epath{font-family:'Courier New',monospace;font-size:.77rem;}
.epd{font-size:.68rem;color:var(--cm);margin-top:.14rem;}
.ccrd{background:#030f07;border-radius:var(--r);border:1px solid rgba(111,207,151,.11);overflow:hidden;}
.chead{background:rgba(45,122,79,.2);padding:.6rem 1.1rem;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid rgba(111,207,151,.08);font-size:.71rem;color:var(--cd);}
.cpb{background:none;border:1px solid rgba(111,207,151,.18);color:var(--cd);border-radius:3px;padding:.15rem .46rem;font-size:.66rem;cursor:pointer;font-family:var(--fb);transition:all .15s;}
.cpb:hover{background:rgba(111,207,151,.1);color:var(--cream);}
pre{padding:1.3rem;font-family:'Courier New',monospace;font-size:.76rem;line-height:1.75;overflow-x:auto;color:#8fcca0;max-height:400px;}
.k{color:#6fcf97}.s{color:#f7c948}.c{color:#3a6645}.n{color:#a8d8b4}
.apiinfo{display:grid;grid-template-columns:1fr 1fr;gap:.85rem;margin-top:1.3rem;}
.ib{background:var(--g2);border-radius:var(--r);padding:1.2rem 1.3rem;border:1px solid rgba(111,207,151,.1);}
.ib.w{border-color:rgba(247,201,72,.19);}
.ibl{font-size:.63rem;font-weight:700;letter-spacing:.12em;text-transform:uppercase;color:var(--g6);margin-bottom:.36rem;}
.ibl.a{color:var(--amber);}
.ib p{font-size:.77rem;color:var(--cd);line-height:1.6;}
code{font-family:'Courier New',monospace;font-size:.75rem;color:var(--g6);background:rgba(111,207,151,.08);padding:.06rem .27rem;border-radius:3px;}

@media(max-width:900px){
  .s1{grid-template-columns:1fr!important;}
  .simbody{grid-template-columns:1fr;}
  .panel{display:none;}
  .agrid,.apigrid,.evalbody,.evalcrit,.cgrid{grid-template-columns:1fr;}
  .blocks{grid-template-columns:1fr 1fr;}
  .nl .hs{display:none;}
}
@media(max-width:600px){
  .blocks,.selrow,.igg{grid-template-columns:1fr;}
  nav{padding:.6rem 1rem;}
  .pgrid{grid-template-columns:repeat(auto-fill,minmax(128px,1fr));}
}
</style>
</head>
<body>

<nav>
  <div class="nav-l">
    <div class="logo">MODO</div>
    <span class="logo-sub">CX Training Center</span>
    <span class="dbadge">Demo</span>
  </div>
  <div class="nl">
    <button onclick="goPage('slides')" class="active" id="nb-slides">Presentación</button>
    <button onclick="goPage('sim')"    id="nb-sim"    class="hs">Simulador IA</button>
    <button onclick="goPage('eval')"   id="nb-eval"   class="hs">Evaluación</button>
    <button onclick="goPage('api')"    id="nb-api"    class="hs">API</button>
    <button onclick="goPage('sim')" class="ncta">Friction Chamber →</button>
  </div>
</nav>

<!-- ══ SLIDES ══ -->
<div class="page active" id="page-slides">

  <div class="slide active" id="sl-1">
    <div class="s1">
      <div class="s1l">
        <div><div class="s1logo">MODO</div><div class="s1sub">CX Training Center</div></div>
        <div style="font-size:2.8rem">🎯</div>
        <div style="font-size:.79rem;color:rgba(245,243,238,.56);line-height:1.7">Una herramienta de IA para que los Moders practiquen y mejoren antes de atender contactos reales.</div>
      </div>
      <div class="s1r">
        <div class="chip">Plataforma de</div>
        <h1 class="s1t">Entrenamiento<br><em>CX</em></h1>
        <div class="s1a">APEX Córdoba — MODO · 2025</div>
        <p class="s1b">Una herramienta de IA para que los Moders practiquen y mejoren antes de atender contactos reales. Entrenamiento inmersivo, evaluación automática y cultura CX sostenible.</p>
      </div>
    </div>
  </div>

  <div class="slide" id="sl-2">
    <div class="w">
      <div class="ey">02 · The Friction Chamber</div>
      <h2 class="sh">Perfiles de <em>Simulación</em></h2>
      <p class="sd">8 perfiles reales divididos en Usuarios y Comercios. Cada uno replica un tipo de fricción distinto que los Moders enfrentan en producción.</p>
      <div class="ptabs">
        <button class="ptab active" onclick="switchTab('usuarios')">👤 Usuarios</button>
        <button class="ptab" onclick="switchTab('comercios')">🏪 Comercios</button>
      </div>
      <div class="pgrid" id="pgrid"></div>
      <div class="pdet" id="pdet"></div>
    </div>
  </div>

  <div class="slide" id="sl-3">
    <div class="w">
      <div class="ey">03 · Calidad Automática</div>
      <h2 class="sh">Evaluación automática <em>con IA</em></h2>
      <p class="sd">Al finalizar cada sesión, la IA evalúa al agente en 6 criterios — los mismos que usa el equipo de calidad de MODO.</p>
      <div class="elayout">
        <div class="esbox">
          <div class="esn">84</div><div class="esd">/100</div>
          <div class="esl">Puntuación General</div>
          <div class="ess">Sesión con Gonza<br>Usuario Enojado</div>
        </div>
        <div class="cgrid">
          <div class="cc"><div class="cctop"><span class="ccn">Completeness</span><span class="ccv" style="color:var(--g6)">8/10</span></div><div class="ccbar"><div class="ccfill" style="width:80%;background:var(--g6)"></div></div></div>
          <div class="cc"><div class="cctop"><span class="ccn">Actitudinal</span><span class="ccv" style="color:var(--g6)">9/10</span></div><div class="ccbar"><div class="ccfill" style="width:90%;background:var(--g6)"></div></div></div>
          <div class="cc"><div class="cctop"><span class="ccn">Voz y tono MODO</span><span class="ccv" style="color:var(--g6)">8/10</span></div><div class="ccbar"><div class="ccfill" style="width:80%;background:var(--g6)"></div></div></div>
          <div class="cc"><div class="cctop"><span class="ccn">Estructura del mensaje</span><span class="ccv" style="color:var(--amber)">7/10</span></div><div class="ccbar"><div class="ccfill" style="width:70%;background:var(--amber)"></div></div></div>
          <div class="cc"><div class="cctop"><span class="ccn">Conversacional</span><span class="ccv" style="color:var(--g6)">9/10</span></div><div class="ccbar"><div class="ccfill" style="width:90%;background:var(--g6)"></div></div></div>
          <div class="cc"><div class="cctop"><span class="ccn">Liderazgo de contacto</span><span class="ccv" style="color:var(--amber)">7/10</span></div><div class="ccbar"><div class="ccfill" style="width:70%;background:var(--amber)"></div></div></div>
        </div>
      </div>
      <div class="enote">💡 Al cerrar una sesión, se envía la transcripción completa a Claude con el rubric de calidad de MODO. La IA devuelve los 6 puntajes + feedback específico. Todo queda disponible en el panel de supervisores.</div>
    </div>
  </div>

  <div class="slide" id="sl-4">
    <div class="w">
      <div class="ey">04 · Stack Técnico</div>
      <h2 class="sh">Arquitectura <em>Técnica</em></h2>
      <p class="sd">Stack pensado para equipo interno y externo. Acceso seguro y con pentest antes del go live.</p>
      <div class="agrid">
        <div class="ac"><div class="aico">⚛️</div><div><div class="at">Frontend</div><div class="an">React</div><div class="adesc">Interfaz web con branding MODO. Login, chat, evaluación y panel supervisor.</div></div></div>
        <div class="ac"><div class="aico">🟢</div><div><div class="at">Backend</div><div class="an">Node.js</div><div class="adesc">API REST que gestiona autenticación, historial de sesiones y comunicación con la IA. La API key nunca se expone al frontend.</div></div></div>
        <div class="ac"><div class="aico">🐘</div><div><div class="at">Base de datos</div><div class="an">PostgreSQL</div><div class="adesc">Guarda usuarios, transcripciones de sesiones y resultados de evaluación.</div></div></div>
        <div class="ac"><div class="aico">🤖</div><div><div class="at">IA</div><div class="an">Anthropic Claude</div><div class="adesc">Motor de simulación y evaluación. Gestionado de forma segura en el servidor Node.js.</div></div></div>
        <div class="ac ext"><div class="aico">🔐</div><div><div class="at">Autenticación · Acceso corporativo</div><div class="an">JumpCloud SSO</div><div class="adesc">Los expertos ingresan con sus credenciales corporativas de MODO. Sin usuarios propios adicionales.</div></div></div>
        <div class="ac ext"><div class="aico">🛡️</div><div><div class="at">Acceso de red · Seguridad</div><div class="an">Warp / ZTNA</div><div class="adesc">App privada, accesible solo con VPN corporativa. Pentest por Red Team antes del go live.</div></div></div>
      </div>
    </div>
  </div>

  <div class="slide" id="sl-5">
    <div class="w">
      <div class="ey">05 · Operativa</div>
      <h2 class="sh">Los 4 Bloques de <em>Cada Sesión</em></h2>
      <p class="sd">3 horas intensivas. Cada "Jueves de HX" genera tensión real, aprendizaje profundo y cultura CX sostenible.</p>
      <div class="blocks">
        <div class="blk" style="background:var(--g2)"><div class="bln">01</div><div class="blt">30 min</div><div class="blname">Contexto HX</div><ul class="bllist"><li>Datos de mercado y E-book HX</li><li>Semaforización de pains</li><li>Importancia CX y el negocio</li></ul></div>
        <div class="blk" style="background:rgba(45,122,79,.17)"><div class="bln">02</div><div class="blt" style="background:rgba(224,82,82,.13);color:var(--red)">45 min</div><div class="blname">Friction Chamber · IA</div><ul class="bllist"><li>Moder vs 8 perfiles de fricción</li><li>Métricas en tiempo real</li><li>Evaluación automática al cerrar</li></ul></div>
        <div class="blk" style="background:var(--g2)"><div class="bln">03</div><div class="blt">120 min</div><div class="blname">Shadowing Real</div><ul class="bllist"><li>Mano a mano con el experto</li><li>Co-resolución de casos reales</li><li>QR para reportar mejoras</li></ul></div>
        <div class="blk" style="background:var(--g2)"><div class="bln">04</div><div class="blt" style="background:rgba(111,207,151,.12);color:var(--g6)">45 min</div><div class="blname">Cierre & Reconocimiento</div><ul class="bllist"><li>Puesta en común con el squad</li><li>Pin Arquitecto de Experiencia</li><li>Premio a la Innovación</li></ul></div>
      </div>
      <div class="selrow">
        <div class="selc"><div class="scn">50%</div><div class="sct">Onboarding</div><div class="scd">Participación obligatoria para nuevos Moders</div></div>
        <div class="selc"><div class="scn" style="color:#7ab3e0">30%</div><div class="sct">Squads Críticos</div><div class="scd">Áreas con mayor fricción detectada</div></div>
        <div class="selc"><div class="scn" style="color:var(--amber)">20%</div><div class="sct">Invitación Abierta</div><div class="scd">Al azar — genera hype y cultura transversal</div></div>
      </div>
    </div>
  </div>

  <div class="slide" id="sl-6">
    <div class="w" style="display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;min-height:calc(100vh - 54px)">
      <div class="ey">06 · El Impacto</div>
      <h2 class="sh" style="text-align:center;margin-bottom:.65rem">¿Por qué <em>vale la pena?</em></h2>
      <div class="bign">+16%</div>
      <div class="bigl">en lealtad y LTV al priorizar la Conexión Humana</div>
      <div class="igg">
        <div class="ig"><div class="ign">75%</div><div class="igl">de usuarios prefieren más interacción humana (PwC)</div></div>
        <div class="ig"><div class="ign">8</div><div class="igl">perfiles reales de fricción en el simulador</div></div>
        <div class="ig"><div class="ign">6</div><div class="igl">criterios de calidad evaluados automáticamente</div></div>
        <div class="ig"><div class="ign">3h</div><div class="igl">de inmersión intensiva cada Jueves de HX</div></div>
      </div>
      <div style="display:flex;gap:.75rem;flex-wrap:wrap;justify-content:center;margin-top:2.2rem">
        <button onclick="goPage('sim')" style="background:var(--g6);color:var(--g0);border:none;border-radius:var(--rs);padding:.68rem 1.65rem;font-weight:700;font-size:.84rem;cursor:pointer;font-family:var(--fb)">Probar Friction Chamber →</button>
        <button onclick="goPage('eval')" style="background:transparent;color:var(--cream);border:1px solid rgba(245,243,238,.19);border-radius:var(--rs);padding:.68rem 1.65rem;font-weight:500;font-size:.84rem;cursor:pointer;font-family:var(--fb)">Ver Evaluación IA →</button>
      </div>
    </div>
  </div>

  <div class="snav">
    <button onclick="prevSlide()">←</button>
    <div class="sdots" id="sdots"></div>
    <span class="sc" id="scount">1 / 6</span>
    <button onclick="nextSlide()">→</button>
  </div>
</div>

<!-- ══ SIMULADOR ══ -->
<div class="page" id="page-sim">
  <div class="simwrap">
    <div class="ey">Bloque 02 · Simulador en Vivo</div>
    <h2 class="sh">The Friction <em>Chamber</em></h2>
    <p class="sd">Seleccioná un perfil, escribí tu respuesta y observá cómo reacciona el usuario. Al finalizar, evaluación automática con los 6 criterios de MODO.</p>
    <div class="simshell">
      <div class="stimbar">
        <div style="display:flex;align-items:center;gap:.58rem"><span style="font-size:.92rem">⚡</span><span class="stbt">CX Trainer — Friction Chamber</span></div>
        <div class="livt"><div class="livd"></div>Simulador Activo</div>
      </div>
      <div class="sctabs" id="simtabs"></div>
      <div class="simbody">
        <div class="chatcol">
          <div class="msgs" id="smsgs">
            <div class="bw"><div class="bn">Sistema</div><div class="bb bot">Seleccioná un perfil en las tabs para comenzar la sesión de entrenamiento.</div></div>
          </div>
          <div class="inputbar">
            <input class="si" id="simin" placeholder="Escribí tu respuesta como Moder CX..." onkeydown="if(event.key==='Enter'&&!event.shiftKey){event.preventDefault();sendMsg();}">
            <button class="sbtn" id="sbtn" onclick="sendMsg()">Enviar</button>
          </div>
        </div>
        <div class="panel">
          <div>
            <div class="plbl">Indicadores de sesión</div>
            <div class="meter"><div class="ml">Empatía</div><div class="mt"><div class="mf" id="m-em" style="width:30%;background:#6fcf97"></div></div><div class="mv" id="mv-em" style="color:#6fcf97">30</div></div>
            <div class="meter"><div class="ml">Resolución</div><div class="mt"><div class="mf" id="m-re" style="width:20%;background:#f7c948"></div></div><div class="mv" id="mv-re" style="color:#f7c948">20</div></div>
            <div class="meter"><div class="ml">Tensión</div><div class="mt"><div class="mf" id="m-te" style="width:80%;background:#e05252"></div></div><div class="mv" id="mv-te" style="color:#e05252">80</div></div>
          </div>
          <div class="tip" id="simtip"><strong>💡 Tip HX:</strong> Validá la emoción antes de proponer soluciones. "Entiendo tu situación" baja la tensión inicial.</div>
          <div><div class="plbl">Perfil activo</div><p style="font-size:.71rem;color:var(--cd);line-height:1.6" id="scdesc">Seleccioná un perfil para ver el contexto.</p></div>
          <button class="bsim" onclick="endSession()" style="margin-top:auto">Finalizar y Evaluar →</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ══ EVALUACIÓN ══ -->
<div class="page" id="page-eval">
  <div class="evalwrap">
    <div class="ey">Cierre de Sesión · IA Evaluadora</div>
    <h2 class="sh">Evaluación automática <em>con IA</em></h2>
    <p class="sd">Los 6 criterios que usa el equipo de calidad de MODO, evaluados automáticamente al finalizar cada sesión.</p>
    <div class="evalshell">
      <div class="evalhead">
        <div class="evalheadt">Resultado de Sesión</div>
        <div class="evalsel">
          <span>Ejemplo:</span>
          <select id="evalsel" onchange="loadEvalSess(this.value)">
            <option value="gonza">Gonza — Usuario Enojado</option>
            <option value="lorena">Lorena — Usuario Paciente</option>
            <option value="sofia">Sofía — Nueva Integración</option>
            <option value="paula">Paula — Integración Técnica</option>
          </select>
        </div>
      </div>
      <div class="evalbody">
        <div class="evalsc">
          <div class="evalscore" id="evsc">84</div>
          <div class="evalsden">/100</div>
          <div class="evalslbl">Puntuación General</div>
          <div class="evalssess" id="evsess">Sesión con Gonza<br>Usuario Enojado</div>
        </div>
        <div class="evalcrit" id="evalcrit"></div>
      </div>
      <div class="evalnote" id="evalnote">Buen manejo de la tensión emocional. Mejorá la estructura del mensaje: terminá siempre con una pregunta de confirmación o un siguiente paso claro.</div>
      <div class="evalact">
        <button class="bsim" onclick="goPage('sim')">Volver al simulador</button>
        <button class="bout" onclick="resetSim()">Nueva sesión</button>
      </div>
    </div>
  </div>
</div>

<!-- ══ API ══ -->
<div class="page" id="page-api">
  <div class="apiwrap">
    <div class="ey">Integración · REST JSON</div>
    <h2 class="sh">API · MODO <em>CX Trainer</em></h2>
    <p class="sd">Compatible con Lovable, Bubble, Webflow. Bearer auth · CORS habilitado. La API key de Anthropic se gestiona en el backend Node.js — nunca expuesta al browser.</p>
    <div class="apigrid">
      <div class="eplist" id="eplist"></div>
      <div class="ccrd">
        <div class="chead"><span id="eplbl">POST /api/simulate</span><button class="cpb" onclick="copyCode()">Copiar</button></div>
        <pre id="epcode"></pre>
      </div>
    </div>
    <div class="apiinfo">
      <div class="ib"><div class="ibl">Lovable · Bubble · Webflow</div><p>En Lovable usá <code>VITE_API_KEY</code> como env var. El backend Node.js inyecta la Anthropic key — nunca expuesta al browser. Endpoint REST puro, integración en minutos.</p></div>
      <div class="ib w"><div class="ibl a">⚠️ Si la API está bloqueada</div><p><code>401</code>: verificar <code>Authorization: Bearer TOKEN</code>. <code>403</code>: agregar créditos en console.anthropic.com. <code>429</code>: rate limit — agregar debounce 500ms.</p></div>
    </div>
  </div>
</div>

<script>
/* ══════════════════════════════════════════════
   PERFILES — motor de respuesta contextual
   Cada respuesta tiene "triggers" (palabras clave
   que el Moder puede escribir) + métricas asociadas
══════════════════════════════════════════════ */
const PROFILES = {
  usuarios:[
    { id:'lorena', emoji:'👵', badge:'Paciente', bc:'bp', name:'Lorena',
      desc:'Mayor, poca experiencia con tecnología',
      tension:30,
      init:'Hola, buen día. Necesito ayuda porque no sé cómo usar bien la aplicación. Mi nieta me la instaló pero no entiendo cómo funciona exactamente.',
      flow:[
        { triggers:['paso','paso a paso','cómo','como','explica','explicá','instruccion','instrucción','ayuda','empezamos'],
          reply:'Ah, re bien. Pero cuando toco ese botón me sale otra pantalla. ¿Eso está bien o me equivoqué en algo?',
          em:48, re:38, te:24 },
        { triggers:['pantalla','botón','boton','tocar','tocá','ícono','icono','menú','menu'],
          reply:'Mmm, sí creo que lo veo... ¿y tengo que hacer eso cada vez que uso la app o solo la primera vez?',
          em:58, re:50, te:18 },
        { triggers:['una vez','primera','solo','siempre','cada','automático','automatico'],
          reply:'Perfecto. Y si me olvido la contraseña, ¿qué hago? Porque a veces me pasa eso.',
          em:66, re:60, te:13 },
        { triggers:['contraseña','clave','recuperar','recuperá','olvidé','olvide','resetear','cambiar'],
          reply:'Ah, me manda un mensaje al celular. Lo acabo de recibir. ¿Qué número pongo ahí?',
          em:74, re:68, te:9 },
        { triggers:['número','numero','código','codigo','ingresá','ingresa','escribí','escribe','ponés','pones'],
          reply:'¡Funcionó! Muchas gracias. Sos muy amable. ¿Y si me vuelve a pasar puedo llamarlos de nuevo?',
          em:82, re:76, te:5 },
        { triggers:['sí','si','claro','siempre','cuando quieras','disponible','acá','aca','contacto'],
          reply:'Qué bueno saberlo. Muy buena la atención, la verdad. Que tengas un lindo día.',
          em:90, re:88, te:2 },
      ],
      fallback:['Disculpe, no entendí bien. ¿Me podría explicar de otra manera?','¿Y eso cómo lo hago exactamente?','Ajá... ¿y después qué?'],
      fallbackM:{em:52,re:44,te:18}
    },

    { id:'gonza', emoji:'😤', badge:'Enojado', bc:'be', name:'Gonza',
      desc:'Cobro duplicado, exige solución YA',
      tension:90,
      init:'¡No puedo creer lo que me pasó! Me cobraron dos veces el mismo pago y nadie me da una solución. ¡Quiero que me devuelvan mi plata YA!',
      flow:[
        { triggers:['entiendo','comprendo','lamento','disculpá','disculpa','inconveniente','situación','situacion','molestia'],
          reply:'¿Y cuánto tarda eso? Porque ya me prometieron lo mismo ayer y no pasó nada. Necesito una fecha concreta.',
          em:42, re:32, te:76 },
        { triggers:['horas','dias','días','plazo','24','48','72','hoy','mañana','lunes','martes','miércoles','jueves','viernes'],
          reply:'Bueno, si me lo confirman por escrito acepto. Pero que no me vengan con más vueltas.',
          em:55, re:48, te:60 },
        { triggers:['mail','correo','email','escrito','constancia','número de caso','numero de caso','confirmacion','confirmación','referencia'],
          reply:'Bien. ¿Y el reintegro es automático a mi cuenta o tengo que hacer algo de mi parte?',
          em:62, re:58, te:46 },
        { triggers:['automático','automatico','cuenta','acredita','deposita','transfiere','directo','sin hacer nada'],
          reply:'Ok, ¿y si en ese plazo no aparece el dinero, a quién llamo directamente? No quiero hablar con un bot.',
          em:70, re:66, te:34 },
        { triggers:['llama','llamá','contacto','número','numero','directo','supervisor','persona','humano','agente'],
          reply:'Está bien. Lo anoto. La atención estuvo bien, el problema fue del sistema. Gracias.',
          em:80, re:76, te:20 },
        { triggers:['gracias','ok','listo','perfecto','entendido','de acuerdo','bien'],
          reply:'Ok. Quedo a la espera del mail y del reintegro. Si llega en tiempo y forma no tengo más nada que decir.',
          em:86, re:82, te:12 },
      ],
      fallback:['Eso no me soluciona nada. ¿Hay algo concreto que puedan hacer HOY?','¿Cuánto más voy a tener que esperar?','Necesito hechos, no palabras.'],
      fallbackM:{em:38,re:28,te:85}
    },

    { id:'horacio', emoji:'👴', badge:'Vulnerable', bc:'bv', name:'Horacio',
      desc:'Jubilado, cuenta bloqueada, angustiado',
      tension:70,
      init:'Por favor, necesito ayuda urgente. Mi cuenta quedó bloqueada y soy jubilado, necesito ese dinero para vivir. No sé qué hice mal.',
      flow:[
        { triggers:['entiendo','comprendo','ayudar','ayudarte','ayudarlo','tranquilo','tranquilícese','tranquilicese','vamos','revisamos'],
          reply:'Ay, gracias. ¿Y cuánto tarda en desbloquearse? Es que tengo que pagar el remedio mañana.',
          em:54, re:42, te:54 },
        { triggers:['horas','minutos','pronto','rápido','rapido','inmediato','ya','ahora'],
          reply:'Bien, bien. ¿Y qué tengo que hacer yo? ¿Hay que apretar algo en el teléfono?',
          em:62, re:55, te:42 },
        { triggers:['código','codigo','mensaje','sms','celular','teléfono','telefono','recibió','recibio','llegó','llego'],
          reply:'Me llegó un mensajito. Dice unos números. ¿Los escribo en la aplicación?',
          em:68, re:62, te:32 },
        { triggers:['sí','si','escribí','escriba','ingresá','ingrese','exactamente','eso','correcto','ponelo','ponés'],
          reply:'Dice "token inválido". Ay, me puse nervioso y capaz lo escribí mal.',
          em:65, re:58, te:38 },
        { triggers:['nueva','otro','reenvío','reenvio','volvemos','otra vez','de nuevo','mandamos','mandá'],
          reply:'Ya me llegó otro. Ahora sí entró. ¿Ya está desbloqueada la cuenta?',
          em:76, re:70, te:20 },
        { triggers:['sí','si','desbloqueada','activa','lista','puede','acceder','funciona','ingresá','ingrese'],
          reply:'Sí, veo el saldo. Qué alivio enorme. Muchas gracias por la paciencia, en serio. Muy buena atención.',
          em:90, re:86, te:6 },
      ],
      fallback:['No entiendo. ¿Me podría explicar más despacio?','¿Y eso es seguro? No quisiera hacer algo mal.','¿Cuánto más tarda? Es que estoy muy angustiado.'],
      fallbackM:{em:58,re:48,te:52}
    },

    { id:'zulema', emoji:'👩', badge:'Insatisfecha', bc:'bi', name:'Zulema',
      desc:'Evalúa irse a la competencia',
      tension:65,
      init:'Miren, estoy pensando en pasarme a otra app porque acá el servicio no me convence. ¿Qué me pueden ofrecer que no tenga la competencia?',
      flow:[
        { triggers:['beneficio','beneficios','ventaja','ventajas','cashback','descuento','descuentos','oferta','ofertas','promocion','promoción'],
          reply:'Mmm, pero la otra app me da cashback en todas las compras, no solo en algunas. ¿Ustedes tienen algo así?',
          em:44, re:40, te:58 },
        { triggers:['comercios','supermercado','todos','amplio','amplia','red','donde','cuántos','cuantos','categorias','categorías'],
          reply:'Me interesa. ¿Y eso ya está activo o es algo que viene próximamente?',
          em:52, re:48, te:48 },
        { triggers:['activo','ya','disponible','ahora','funciona','podés','puedes','usarlo','hoy'],
          reply:'¿Y si tengo algún problema con el cashback, cómo lo reclamo? ¿Hay alguien para hablar?',
          em:60, re:56, te:38 },
        { triggers:['chat','atención','atencion','soporte','contacto','persona','humano','whatsapp','llamar','escribe'],
          reply:'Ok, eso cambia las cosas. Si me mandan los detalles por mail lo evalúo esta semana.',
          em:68, re:64, te:28 },
        { triggers:['mail','correo','email','mando','mandamos','enviamos','detalle','detalles','información','informacion'],
          reply:'Bien. La atención estuvo buena. Le doy una oportunidad más. Pero si el cashback no funciona como dicen, ahí sí me voy.',
          em:76, re:72, te:18 },
        { triggers:['gracias','ok','entendido','perfecto','bien','listo'],
          reply:'De acuerdo. Pruebo esta semana y les aviso. Chau.',
          em:80, re:76, te:12 },
      ],
      fallback:['Y eso, ¿en qué me beneficia a mí concretamente?','La competencia también promete eso. ¿Qué tienen de diferente?','Necesito algo concreto, no argumentos de venta.'],
      fallbackM:{em:40,re:36,te:62}
    },
  ],

  comercios:[
    { id:'martin', emoji:'🛒', badge:'Pagos no integrados', bc:'bpa', name:'Martín',
      desc:'Amenaza dejar de operar',
      tension:85,
      init:'Tenemos un problema grave. Los pagos con MODO no están procesando bien y estamos perdiendo ventas. Si no lo resuelven hoy, dejamos de operar con ustedes.',
      flow:[
        { triggers:['entiendo','comprendo','revisamos','escalamos','prioridad','urgente','técnico','tecnico','caso','derivamos'],
          reply:'El error que me sale dice "timeout en el gateway". ¿Es un problema de su lado o del mío?',
          em:40, re:36, te:74 },
        { triggers:['nuestro lado','su lado','servidor','proveedor','infraestructura','técnico','identificado','detectamos'],
          reply:'¿Y cuánto tiempo estimado para resolverlo? Perdí tres ventas esta mañana.',
          em:50, re:48, te:62 },
        { triggers:['horas','minutos','pronto','ya','trabajando','resolviendo','equipo'],
          reply:'¿Hay algo que pueda hacer yo mientras tanto para no seguir perdiendo ventas?',
          em:58, re:56, te:50 },
        { triggers:['alternativa','alternativo','modo','QR','link de pago','forma alternativa','mientras'],
          reply:'Activo el modo alternativo. ¿Y cuando resuelvan el problema me avisan directamente?',
          em:66, re:64, te:38 },
        { triggers:['avisamos','notificamos','mail','notificación','notificacion','al mail','te avisamos'],
          reply:'Bien. Quiero que quede registrado el tiempo de caída para el historial del comercio.',
          em:74, re:72, te:26 },
        { triggers:['registro','registrado','caso','número','numero','historial','constancia'],
          reply:'Ok. La gestión estuvo bien. Si pasa de nuevo espero que lo resuelvan igual de rápido.',
          em:80, re:78, te:14 },
      ],
      fallback:['¿Y eso cuándo lo van a resolver concretamente?','Necesito una solución HOY, no mañana.','Cada hora que pasa son ventas que perdemos.'],
      fallbackM:{em:36,re:32,te:82}
    },

    { id:'sofia', emoji:'🏪', badge:'Nueva integración', bc:'bn2', name:'Sofía',
      desc:'Dudas sobre el proceso de cobro',
      tension:35,
      init:'Hola, recién integré MODO en mi local pero no estoy segura de cómo funciona el proceso de cobro. ¿El dinero llega el mismo día?',
      flow:[
        { triggers:['día','dia','hábil','habil','24','48','plazo','acreditación','acreditacion','tiempo','demora'],
          reply:'Ah, entendible. ¿Y si el cliente cancela el pago después de que ya me acreditaron, qué pasa?',
          em:55, re:50, te:28 },
        { triggers:['devolución','devolucion','contracargo','chargeback','retiene','descuenta','proceso'],
          reply:'Ok, tiene sentido. ¿Y los reportes de cada cobro los veo en el panel o me llegan por mail?',
          em:62, re:58, te:22 },
        { triggers:['panel','dashboard','plataforma','sistema','mail','correo','ambos','también','tambien'],
          reply:'¿Puedo filtrar los reportes por fecha o por tipo de pago?',
          em:68, re:65, te:16 },
        { triggers:['filtrar','filtros','fecha','tipo','categoría','categoria','búsqueda','busqueda','exportar'],
          reply:'Perfecto. ¿Y tienen soporte técnico disponible los fines de semana? Mi local abre sábados.',
          em:74, re:72, te:12 },
        { triggers:['sábado','sabado','fin de semana','finde','domingo','24/7','guardia','chat','disponible'],
          reply:'Excelente, eso es importante. ¿El chat de soporte también funciona los fines de semana?',
          em:80, re:78, te:8 },
        { triggers:['sí','si','también','tambien','chat','soporte','funciona','disponible'],
          reply:'Perfecto, me queda todo muy claro. Gracias por la explicación tan completa.',
          em:88, re:85, te:4 },
      ],
      fallback:['¿Y eso aplica a todos los tipos de pago o solo a algunos?','¿Me pueden dar un ejemplo concreto?','¿Hay algo más que debería saber sobre el proceso?'],
      fallbackM:{em:60,re:55,te:22}
    },

    { id:'roberto', emoji:'🏬', badge:'Devoluciones', bc:'bd', name:'Roberto',
      desc:'Contracargos, desconfiado',
      tension:60,
      init:'Tuve varios contracargos este mes y no entiendo el proceso. Siento que MODO no nos da el soporte que necesitamos.',
      flow:[
        { triggers:['entiendo','comprendo','ayudarte','proceso','explicarte','guiarte','revisamos','juntos'],
          reply:'¿Y cuánto tarda ese proceso? El banco me da 10 días para apelar y ya pasó una semana.',
          em:42, re:40, te:52 },
        { triggers:['días','dias','horas','plazo','rápido','rapido','urgente','antes','tiempo'],
          reply:'¿Me pueden mandar eso por escrito? Porque verbalmente ya me dijeron cosas antes que después no se cumplieron.',
          em:50, re:48, te:44 },
        { triggers:['escrito','mail','correo','constancia','documentado','documento','confirmación','confirmacion'],
          reply:'¿Y qué documentación necesito presentar de mi parte para la apelación?',
          em:56, re:54, te:36 },
        { triggers:['factura','comprobante','captura','evidencia','documentación','documentacion','adjuntar','subir'],
          reply:'Bien. ¿Tienen algún porcentaje de resolución favorable para comercios? Necesito saber si vale la pena pelear.',
          em:62, re:60, te:28 },
        { triggers:['porcentaje','estadística','estadistica','favorable','exitoso','ganamos','resolvemos','mayoría','mayoria'],
          reply:'Con eso puedo trabajar. ¿El proceso lo manejo yo desde el panel o lo hace MODO por mí?',
          em:70, re:67, te:20 },
        { triggers:['panel','vos','yo','ustedes','desde el sistema','herramienta','guía','guia'],
          reply:'Bien. Si me mandan esa guía lo hago yo. Prefiero tener el control. Gracias.',
          em:78, re:75, te:12 },
      ],
      fallback:['¿Y eso queda documentado de alguna manera?','Necesito algo más concreto. ¿Cuáles son los pasos exactos?','¿Y si el cliente igual gana el contracargo?'],
      fallbackM:{em:44,re:40,te:52}
    },

    { id:'paula', emoji:'💼', badge:'Integración técnica', bc:'bit', name:'Paula',
      desc:'IT lead, consultas sobre la API',
      tension:40,
      init:'Hola, soy la IT lead del comercio. Tenemos preguntas técnicas sobre la API de MODO para una integración con nuestro sistema interno.',
      flow:[
        { triggers:['webhook','evento','callback','notificación','notificacion','tiempo real','real time','endpoint','dispara'],
          reply:'¿El webhook de confirmación dispara en tiempo real o hay algún delay promedio documentado?',
          em:55, re:53, te:32 },
        { triggers:['real time','tiempo real','delay','latencia','milisegundos','segundos','instantáneo','instantaneo','promedio'],
          reply:'¿Tienen sandbox environment y los datos de prueba son persistentes entre sesiones?',
          em:62, re:60, te:24 },
        { triggers:['sandbox','ambiente','pruebas','test','staging','environment','persistente','datos de prueba'],
          reply:'¿La autenticación es OAuth2 o API key por header? ¿Y rotan las keys automáticamente?',
          em:68, re:66, te:18 },
        { triggers:['oauth','api key','header','autenticación','autenticacion','bearer','token','rotan','refresh'],
          reply:'¿Qué rate limit tienen en el endpoint de pagos? Lo necesito para diseñar el retry logic.',
          em:74, re:72, te:14 },
        { triggers:['rate limit','límite','limite','requests','rpm','rps','reintentos','retry','throttle'],
          reply:'¿Los errores siguen RFC 7807 o tienen schema propio para los error codes?',
          em:78, re:76, te:10 },
        { triggers:['rfc','schema','error codes','formato','estructura','json','respuesta','errors'],
          reply:'Perfecto. Con eso puedo armar el plan de integración. ¿Tienen documentación en Swagger o Postman?',
          em:84, re:82, te:6 },
      ],
      fallback:['¿Tienen eso documentado en algún lugar accesible?','¿Cuál es el comportamiento exacto en caso de error?','¿Eso aplica también a los endpoints de consulta?'],
      fallbackM:{em:62,re:60,te:28}
    },
  ]
};

const TIPS = [
  '💡 <strong>Tip HX:</strong> Validá la emoción antes de proponer soluciones. "Entiendo tu situación" baja la tensión inicial.',
  '💡 <strong>Tip HX:</strong> Usá el nombre del usuario — personaliza completamente la experiencia.',
  '💡 <strong>Tip HX:</strong> Un timeline concreto ("en 2 horas te confirmamos") reduce la ansiedad.',
  '💡 <strong>Tip HX:</strong> Evitá "no se preocupe". Decí "me encargo personalmente de esto".',
  '💡 <strong>Tip HX:</strong> Con comercios: cerrá siempre con un próximo paso accionable y una fecha.',
  '💡 <strong>Tip HX:</strong> Reconocé el historial antes de dar soluciones — el usuario se siente escuchado.',
  '💡 <strong>Tip HX:</strong> Un buen mensaje: empatía → diagnóstico → solución → siguiente paso.',
];

const EVAL_DATA = {
  gonza:{score:84,sess:'Sesión con Gonza\nUsuario Enojado',criteria:[{n:'Completeness',v:8,c:'#6fcf97'},{n:'Actitudinal',v:9,c:'#6fcf97'},{n:'Voz y tono MODO',v:8,c:'#6fcf97'},{n:'Estructura del mensaje',v:7,c:'#f7c948'},{n:'Conversacional',v:9,c:'#6fcf97'},{n:'Liderazgo de contacto',v:7,c:'#f7c948'}],fb:'Buen manejo de la tensión emocional. Mejorá la estructura del mensaje: terminá siempre con una pregunta de confirmación o un siguiente paso claro.'},
  lorena:{score:91,sess:'Sesión con Lorena\nUsuaria Paciente',criteria:[{n:'Completeness',v:9,c:'#6fcf97'},{n:'Actitudinal',v:10,c:'#6fcf97'},{n:'Voz y tono MODO',v:9,c:'#6fcf97'},{n:'Estructura del mensaje',v:9,c:'#6fcf97'},{n:'Conversacional',v:9,c:'#6fcf97'},{n:'Liderazgo de contacto',v:8,c:'#6fcf97'}],fb:'Excelente atención para perfil vulnerable. Lenguaje claro, empático y paso a paso. El liderazgo puede mejorar — proponé el siguiente paso antes de que el usuario lo pida.'},
  sofia:{score:76,sess:'Sesión con Sofía\nNueva Integración',criteria:[{n:'Completeness',v:7,c:'#f7c948'},{n:'Actitudinal',v:8,c:'#6fcf97'},{n:'Voz y tono MODO',v:8,c:'#6fcf97'},{n:'Estructura del mensaje',v:7,c:'#f7c948'},{n:'Conversacional',v:8,c:'#6fcf97'},{n:'Liderazgo de contacto',v:6,c:'#e05252'}],fb:'Para comercios nuevos, la completitud es clave. Faltó cubrir el proceso completo de cobro. Liderazgo bajo — tomá más la iniciativa para guiar al comercio.'},
  paula:{score:88,sess:'Sesión con Paula\nIntegración Técnica',criteria:[{n:'Completeness',v:9,c:'#6fcf97'},{n:'Actitudinal',v:9,c:'#6fcf97'},{n:'Voz y tono MODO',v:8,c:'#6fcf97'},{n:'Estructura del mensaje',v:9,c:'#6fcf97'},{n:'Conversacional',v:9,c:'#6fcf97'},{n:'Liderazgo de contacto',v:8,c:'#6fcf97'}],fb:'Muy buen manejo de perfil técnico. Respuestas precisas. Podés mejorar la Voz MODO — con perfiles IT hay tendencia a sonar demasiado formal.'},
};

const EP_DATA={
  simulate:{lbl:'POST /api/simulate',code:`<span class="c">// Enviar respuesta del Moder al simulador</span>
<span class="k">fetch</span>(<span class="s">'https://api.modocx.com/v1/simulate'</span>, {
  <span class="n">method</span>: <span class="s">'POST'</span>,
  <span class="n">headers</span>: { <span class="s">'Authorization'</span>: <span class="s">'Bearer YOUR_KEY'</span> },
  <span class="n">body</span>: <span class="k">JSON.stringify</span>({
    <span class="n">profile_id</span>: <span class="s">'gonza'</span>,
    <span class="n">moder_message</span>: <span class="s">'Entiendo tu frustración...'</span>,
    <span class="n">session_id</span>: <span class="s">'sess_abc123'</span>
  })
})<span class="c"> // → { ai_response, metrics, tip }</span>`},
  evaluate:{lbl:'POST /api/evaluate',code:`<span class="k">fetch</span>(<span class="s">'https://api.modocx.com/v1/evaluate'</span>, {
  <span class="n">method</span>: <span class="s">'POST'</span>,
  <span class="n">headers</span>: { <span class="s">'Authorization'</span>: <span class="s">'Bearer YOUR_KEY'</span> },
  <span class="n">body</span>: <span class="k">JSON.stringify</span>({
    <span class="n">session_id</span>: <span class="s">'sess_abc123'</span>,
    <span class="n">transcript</span>: messages
  })
})
<span class="c">// → { score:84, criteria:{...}, feedback:"..." }</span>`},
  sessions:{lbl:'GET /api/sessions',code:`{
  <span class="s">"sessions"</span>: [{
    <span class="s">"id"</span>: <span class="s">"sess_20250501"</span>,
    <span class="s">"type"</span>: <span class="s">"jueves_hx"</span>,
    <span class="s">"experts"</span>: [<span class="s">"sebastian"</span>, <span class="s">"romina"</span>],
    <span class="s">"capacity"</span>: 6, <span class="s">"enrolled"</span>: 4
  }]
}`},
  metrics:{lbl:'GET /api/metrics/{id}',code:`{
  <span class="s">"avg_criteria"</span>: {
    <span class="s">"completeness"</span>: 8.2, <span class="s">"actitudinal"</span>: 9.0,
    <span class="s">"voz_tono"</span>: 7.8,    <span class="s">"estructura"</span>: 7.1,
    <span class="s">"conversacional"</span>: 8.9, <span class="s">"liderazgo"</span>: 7.5
  },
  <span class="s">"overall"</span>: 8.1, <span class="s">"sessions"</span>: 3, <span class="s">"trend"</span>: <span class="s">"improving"</span>
}`},
  profiles:{lbl:'GET /api/profiles',code:`{ <span class="s">"profiles"</span>: [
  {<span class="s">"id"</span>:<span class="s">"gonza"</span>, <span class="s">"type"</span>:<span class="s">"usuario"</span>, <span class="s">"tension"</span>:90},
  {<span class="s">"id"</span>:<span class="s">"lorena"</span>,<span class="s">"type"</span>:<span class="s">"usuario"</span>, <span class="s">"tension"</span>:30},
  {<span class="s">"id"</span>:<span class="s">"sofia"</span>, <span class="s">"type"</span>:<span class="s">"comercio"</span>,<span class="s">"tension"</span>:35},
  {<span class="s">"id"</span>:<span class="s">"martin"</span>,<span class="s">"type"</span>:<span class="s">"comercio"</span>,<span class="s">"tension"</span>:85}
]}`}
};

/* ══ SLIDES ══ */
let cur=1; const TOTAL=6;
function buildDots(){const d=document.getElementById('sdots');d.innerHTML='';for(let i=1;i<=TOTAL;i++){const s=document.createElement('div');s.className='sdot'+(i===cur?' active':'');s.onclick=()=>goSlide(i);d.appendChild(s);}}
function goSlide(n){document.getElementById('sl-'+cur).classList.remove('active');cur=Math.max(1,Math.min(TOTAL,n));document.getElementById('sl-'+cur).classList.add('active');document.getElementById('scount').textContent=cur+' / '+TOTAL;buildDots();window.scrollTo(0,0);}
function nextSlide(){goSlide(cur+1);}function prevSlide(){goSlide(cur-1);}
document.addEventListener('keydown',e=>{if(document.getElementById('page-slides').classList.contains('active')){if(e.key==='ArrowRight'||e.key===' '){e.preventDefault();nextSlide();}if(e.key==='ArrowLeft'){e.preventDefault();prevSlide();}}});
buildDots();

/* ══ PAGES ══ */
function goPage(id){document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));document.querySelectorAll('.nl button[id^="nb-"]').forEach(b=>b.classList.remove('active'));document.getElementById('page-'+id).classList.add('active');const nb=document.getElementById('nb-'+id);if(nb)nb.classList.add('active');window.scrollTo(0,0);}

/* ══ PERFILES SLIDE ══ */
let activeTab='usuarios', selProf=null;
function switchTab(t){activeTab=t;document.querySelectorAll('.ptab').forEach(b=>b.classList.toggle('active',b.textContent.toLowerCase().includes(t)));renderProfiles();document.getElementById('pdet').classList.remove('vis');selProf=null;}
function renderProfiles(){document.getElementById('pgrid').innerHTML=PROFILES[activeTab].map(p=>`<div class="pcard${selProf&&selProf.id===p.id?' sel':''}" onclick="selProfile('${activeTab}','${p.id}')"><span class="pe">${p.emoji}</span><span class="pbadge ${p.bc}">${p.badge}</span><div class="pname">${p.name}</div><div class="pdesc">${p.desc}</div></div>`).join('');}
function selProfile(tab,id){selProf=PROFILES[tab].find(p=>p.id===id);renderProfiles();const det=document.getElementById('pdet');det.innerHTML=`<div class="pde">${selProf.emoji}</div><div class="pdi"><div class="pdn">${selProf.name} <span class="pbadge ${selProf.bc}" style="font-size:.62rem;vertical-align:middle">${selProf.badge}</span></div><div class="pdc" style="margin-top:.25rem">${selProf.desc}</div></div><div class="pdtip"><strong>Primer mensaje:</strong><br><em style="color:var(--cd);font-style:normal">"${selProf.init}"</em></div><button class="bsim" onclick="startWithProfile()">Simular con ${selProf.name} →</button>`;det.classList.add('vis');}
function startWithProfile(){if(!selProf)return;goPage('sim');loadProfile(selProf.id);}
renderProfiles();

/* ══ SIMULADOR ══ */
let simProf=null, em=30, re=20, te=80, msgCount=0, isTyping=false, usedFlowIdx=new Set();

function buildSimTabs(){
  const t=document.getElementById('simtabs');t.innerHTML='';
  ['usuarios','comercios'].forEach(cat=>PROFILES[cat].forEach(p=>{
    const b=document.createElement('button');
    b.className='sctab'+(simProf&&simProf.id===p.id?' active':'');
    b.textContent=p.emoji+' '+p.name;
    b.onclick=()=>loadProfile(p.id);
    t.appendChild(b);
  }));
}

function loadProfile(id){
  const all=[...PROFILES.usuarios,...PROFILES.comercios];
  simProf=all.find(p=>p.id===id);
  em=30; re=20; te=simProf.tension; msgCount=0; isTyping=false; usedFlowIdx=new Set();
  applyM();
  document.getElementById('smsgs').innerHTML=`<div class="bw"><div class="bn">${simProf.name} — ${simProf.badge}</div><div class="bb bot">${simProf.init}</div></div>`;
  document.getElementById('scdesc').textContent=simProf.desc;
  document.getElementById('simtip').innerHTML=TIPS[0];
  buildSimTabs();
  document.getElementById('simin').focus();
}

function applyM(){
  setM('em',em,'#6fcf97');
  setM('re',re,'#f7c948');
  setM('te',te,te>65?'#e05252':te>35?'#f7c948':'#6fcf97');
}
function setM(id,v,c){
  document.getElementById('m-'+id).style.cssText=`width:${v}%;background:${c}`;
  const el=document.getElementById('mv-'+id);el.textContent=v;el.style.color=c;
}

/* Motor de respuesta contextual */
function pickReply(msg){
  const txt=msg.toLowerCase()
    .normalize('NFD').replace(/[\u0300-\u036f]/g,'') // quitar acentos
    .replace(/[^a-z0-9 ]/g,' ');

  // 1. Buscar la mejor coincidencia en el flow (no usada aún)
  let bestIdx=-1, bestScore=0;
  simProf.flow.forEach((step,i)=>{
    if(usedFlowIdx.has(i)) return;
    const score=step.triggers.reduce((acc,t)=>acc+(txt.includes(t.toLowerCase().normalize('NFD').replace(/[\u0300-\u036f]/g,''))?1:0),0);
    if(score>bestScore){bestScore=score;bestIdx=i;}
  });

  if(bestScore>=1 && bestIdx>=0){
    usedFlowIdx.add(bestIdx);
    return {reply:simProf.flow[bestIdx].reply, em:simProf.flow[bestIdx].em, re:simProf.flow[bestIdx].re, te:simProf.flow[bestIdx].te};
  }

  // 2. Buscar en flow ya usados como segunda opción
  let anyIdx=-1, anyScore=0;
  simProf.flow.forEach((step,i)=>{
    const score=step.triggers.reduce((acc,t)=>acc+(txt.includes(t.toLowerCase().normalize('NFD').replace(/[\u0300-\u036f]/g,''))?1:0),0);
    if(score>anyScore){anyScore=score;anyIdx=i;}
  });
  if(anyScore>=1 && anyIdx>=0){
    const step=simProf.flow[anyIdx];
    // Avanzar métricas ligeramente desde el actual
    return {reply:step.reply, em:Math.min(em+8,92), re:Math.min(re+6,90), te:Math.max(te-8,4)};
  }

  // 3. Fallback: si la respuesta es muy corta o genérica
  const fbs=simProf.fallback;
  const fb=fbs[msgCount % fbs.length];
  return {reply:fb, em:simProf.fallbackM.em, re:simProf.fallbackM.re, te:simProf.fallbackM.te};
}

function typeText(element, text, cb){
  element.textContent='';
  element.classList.add('typing-cursor');
  let i=0;
  const speed=Math.max(15,Math.min(35,Math.floor(1100/text.length)));
  const t=setInterval(()=>{
    if(i<text.length){element.textContent+=text[i++];document.getElementById('smsgs').scrollTop=99999;}
    else{clearInterval(t);element.classList.remove('typing-cursor');if(cb)cb();}
  },speed);
}

function sendMsg(){
  if(!simProf){alert('Seleccioná un perfil primero');return;}
  if(isTyping)return;
  const inp=document.getElementById('simin');
  const msg=inp.value.trim(); if(!msg)return;
  inp.value='';
  const btn=document.getElementById('sbtn');
  const msgs=document.getElementById('smsgs');

  msgs.innerHTML+=`<div class="bw u"><div class="bn">Moder CX</div><div class="bb usr">${msg}</div></div>`;
  msgs.scrollTop=99999;
  msgCount++;

  const loadId='ld'+Date.now();
  msgs.innerHTML+=`<div class="bw" id="${loadId}"><div class="bn">${simProf.name}</div><div class="bb bot"><span class="dots"><span>·</span><span>·</span><span>·</span></span></div></div>`;
  msgs.scrollTop=99999;
  btn.disabled=true; isTyping=true;

  const picked=pickReply(msg);
  const delay=800+Math.random()*600;

  setTimeout(()=>{
    const loadEl=document.getElementById(loadId);
    if(!loadEl){btn.disabled=false;isTyping=false;return;}
    typeText(loadEl.querySelector('.bb'), picked.reply, ()=>{
      em=picked.em; re=picked.re; te=picked.te;
      applyM();
      document.getElementById('simtip').innerHTML=TIPS[Math.floor(Math.random()*TIPS.length)];
      btn.disabled=false; isTyping=false;
    });
  }, delay);
}

function endSession(){
  if(!simProf||msgCount<1){alert('Completá al menos una respuesta antes de evaluar.');return;}
  const evalKey=['gonza','lorena','sofia','paula'].includes(simProf.id)
    ? simProf.id
    : (PROFILES.comercios.find(p=>p.id===simProf.id)?'sofia':'gonza');
  const base=EVAL_DATA[evalKey];
  // Score basado en tensión final: menos tensión = mejor puntaje
  const bonus=Math.round((80-te)/8);
  const finalScore=Math.max(58,Math.min(98,base.score+bonus));
  goPage('eval');
  const scoreEl=document.getElementById('evsc');
  scoreEl.textContent='0';
  document.getElementById('evsess').innerHTML=`Sesión con ${simProf.name}<br>${simProf.badge}`;
  let count=0;
  const counter=setInterval(()=>{count=Math.min(count+3,finalScore);scoreEl.textContent=count;if(count>=finalScore)clearInterval(counter);},32);
  const tc=v=>v>=8?'#6fcf97':v>=6?'#f7c948':'#e05252';
  const criteria=base.criteria.map(c=>({...c,v:Math.max(4,Math.min(10,c.v+Math.round((Math.random()-.35)*1.5)))}));
  renderCritAnimated(criteria);
  document.getElementById('evalnote').textContent=base.fb;
  document.getElementById('evalsel').value=evalKey;
}

function resetSim(){
  simProf=null; msgCount=0; em=30; re=20; te=80;
  goPage('sim');
  document.getElementById('smsgs').innerHTML='<div class="bw"><div class="bn">Sistema</div><div class="bb bot">Seleccioná un perfil en las tabs para comenzar una nueva sesión.</div></div>';
  buildSimTabs();
}

/* ══ EVAL ══ */
function renderCrit(c){document.getElementById('evalcrit').innerHTML=c.map(x=>`<div class="ec"><div class="ectop"><span class="ecn">${x.n}</span><span class="ecv" style="color:${x.c}">${x.v}/10</span></div><div class="ecbar"><div class="ecfill" style="width:${x.v*10}%;background:${x.c}"></div></div></div>`).join('');}
function renderCritAnimated(crit){
  document.getElementById('evalcrit').innerHTML=crit.map(c=>`<div class="ec"><div class="ectop"><span class="ecn">${c.n}</span><span class="ecv" id="ev-${c.n.replace(/\s/g,'-')}" style="color:${c.c}">0/10</span></div><div class="ecbar"><div class="ecfill" id="ef-${c.n.replace(/\s/g,'-')}" style="width:0%;background:${c.c}"></div></div></div>`).join('');
  setTimeout(()=>{crit.forEach((c,i)=>setTimeout(()=>{const k=c.n.replace(/\s/g,'-');const f=document.getElementById('ef-'+k);const v=document.getElementById('ev-'+k);if(f)f.style.width=c.v*10+'%';if(v)v.textContent=c.v+'/10';},i*110));},180);
}
function loadEvalSess(id){const d=EVAL_DATA[id];document.getElementById('evsc').textContent=d.score;document.getElementById('evsess').innerHTML=d.sess.replace('\n','<br>');document.getElementById('evalnote').textContent=d.fb;renderCrit(d.criteria);}
loadEvalSess('gonza');

/* ══ API DOCS ══ */
function buildApiList(){
  const eps=[{k:'simulate',m:'post',p:'/api/simulate',d:'Simular interacción con perfil IA'},{k:'evaluate',m:'post',p:'/api/evaluate',d:'Evaluar sesión — 6 criterios MODO'},{k:'sessions',m:'get',p:'/api/sessions',d:'Listar sesiones y cupos'},{k:'metrics',m:'get',p:'/api/metrics/{id}',d:'Métricas de desempeño del Moder'},{k:'profiles',m:'get',p:'/api/profiles',d:'Listar los 8 perfiles de simulación'}];
  document.getElementById('eplist').innerHTML=eps.map((e,i)=>`<div class="ep${i===0?' active':''}" onclick="showEp(event,'${e.k}')"><span class="em ${e.m}">${e.m.toUpperCase()}</span><span class="epath">${e.p}</span><div class="epd">${e.d}</div></div>`).join('');
  showEpD('simulate');
}
function showEp(ev,k){document.querySelectorAll('.ep').forEach(e=>e.classList.remove('active'));ev.currentTarget.classList.add('active');showEpD(k);}
function showEpD(k){document.getElementById('eplbl').textContent=EP_DATA[k].lbl;document.getElementById('epcode').innerHTML=EP_DATA[k].code;}
function copyCode(){navigator.clipboard.writeText(document.getElementById('epcode').innerText).then(()=>{const b=document.querySelector('.cpb');b.textContent='✓ Copiado';setTimeout(()=>b.textContent='Copiar',1800);});}
buildApiList(); buildSimTabs();
</script>
</body>
</html>
