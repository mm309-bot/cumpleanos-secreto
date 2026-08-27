[index.html](https://github.com/user-attachments/files/31533262/index.html)
<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>❤️</title>
<style>
body{margin:0;background:#fff4f6;color:#3d2930;font-family:Georgia,serif;min-height:100vh;display:grid;place-items:center}
.card{width:min(88vw,480px);background:#fff;border-radius:28px;padding:38px 26px;box-shadow:0 15px 50px #5b26351c;text-align:center}
.number{font-size:82px;color:#a64d67;margin:5px 0 28px}
input{width:88%;padding:16px;border:1px solid #dfc2ca;border-radius:14px;font-size:19px;text-align:center;outline:none}
button{margin-top:12px;border:0;border-radius:14px;padding:14px 28px;background:#a64d67;color:#fff;font-size:17px;cursor:pointer}
.msg{margin-top:18px;display:none;font-size:17px}
.word{font-size:36px;color:#a64d67;font-weight:bold;margin:12px}
.final{font-size:40px;line-height:1.2;color:#a64d67;font-weight:bold}
</style>
</head>
<body>
<main class="card" id="app"></main>
<script>
const d={
s14:{n:"14",correct:"día",word:"ALGÚN"},
s31:{n:"31",correct:"año",word:"DÍA"},
s11:{n:"11",correct:"mes",word:"QUIERO"},
w1:{word:"QUE"},w2:{word:"SEAS"},w3:{word:"MI"},w4:{word:"ESPOSA"},w5:{word:"EN"},w6:{word:"2031"}
};
const key=new URLSearchParams(location.search).get("c")||"home";
const app=document.getElementById("app");
function norm(s){return s.trim().toLowerCase().normalize("NFD").replace(/[\u0300-\u036f]/g,"")}
function special(x){
app.innerHTML=`<div class="number">${x.n}</div><input id="a" autocomplete="off" autocapitalize="none" placeholder=""><br><button onclick="check()">OK</button><div class="msg" id="m"></div>`;
window.check=()=>{
let m=document.getElementById("m");m.style.display="block";
if(norm(document.getElementById("a").value)==norm(x.correct)){
localStorage.setItem(key,"1");
m.innerHTML=`<div class="word">${x.word}</div>`;
finalCheck();
}else m.innerHTML="";
}
}
function show(w){app.innerHTML=`<div class="word">${w}</div>`}
function finalCheck(){
if(["s14","s31","s11"].every(k=>localStorage.getItem(k)))
setTimeout(()=>app.innerHTML=`<div class="final">CÁSATE<br>CONMIGO</div><p><b>14 · 11 · 2031</b></p><p><i>No ahora. Algún día.</i></p>`,700)
}
if(d[key]&&d[key].correct)special(d[key]);else if(d[key])show(d[key].word);else app.innerHTML="";
</script>
</body>
</html>
