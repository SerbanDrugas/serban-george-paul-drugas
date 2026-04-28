---
title: "Gânduri, însemnări şi eseuri"
description: " "
---

<div class="blog-container">
<aside class="blog-form-col">
<div id="status-message" style="color: #2c2c2c; font-size: 0.8rem; margin-bottom: 5px; min-height: 1.2rem;">* Obligatoriu dacă introduci email sau nr. tel.</div>
<form id="main-comment-form">
<input type="text" id="nick" placeholder="Nume / Nickname" required style="width:100%; border:1px solid #4a323c; margin-bottom:10px;">
<div class="input-group" style="margin-bottom:10px;">
<input type="email" id="email" placeholder="Email (opțional)" style="width:100%; border:1px solid #4a323c;">
<div class="btn-toggle" style="display:flex; gap:5px; margin-top:2px;">
<button type="button" onclick="setPrivacy('email', 'public')" style="font-size:0.7rem; cursor:pointer;">Public</button>
<button type="button" onclick="setPrivacy('email', 'admin')" style="font-size:0.7rem; cursor:pointer;">Doar Admin</button>
</div>
</div>
<div class="input-group" style="margin-bottom:10px;">
<input type="tel" id="phone" placeholder="Telefon (opțional)" style="width:100%; border:1px solid #4a323c;">
<div class="btn-toggle" style="display:flex; gap:5px; margin-top:2px;">
<button type="button" onclick="setPrivacy('phone', 'public')" style="font-size:0.7rem; cursor:pointer;">Public</button>
<button type="button" onclick="setPrivacy('phone', 'admin')" style="font-size:0.7rem; cursor:pointer;">Doar Admin</button>
</div>
</div>
<div class="input-group" style="margin-bottom:10px;">
<input type="text" id="title" maxlength="20" placeholder="Titlu comentariu (opțional)" style="width:100%; border:1px solid #4a323c;">
<small style="font-size:0.7rem; display:block;">max. 20 caractere</small>
</div>
<div class="input-group" style="margin-bottom:10px;">
<textarea id="comment" maxlength="2500" placeholder="Scrie comentariul aici...&#10;(sau comentează la ceva existent, în dreapta)" style="width:100%; height:100px; border:1px solid #4a323c; resize:none; overflow-y:scroll; white-space:pre-wrap;"></textarea>
<div style="display:flex; justify-content:space-between; align-items:center;">
<small style="font-size:0.7rem;">max. 2500 caractere</small>
<button type="submit" style="background:#4a323c; color:white; padding:5px 15px; border:none; cursor:pointer; font-weight:bold;">Trimite</button>
</div>
</div>
</form>
</aside>
<main class="blog-comments-col" id="comments-display" style="display:flex; flex-direction:column; gap:5mm;">
<!-- Exemplu Calup Comentarii -->
<div class="comment-block-red" style="border:1px solid red; height:50mm; overflow-y:scroll; padding:2mm; background:transparent; position:relative;">
<!-- Comentariu fix sus -->
<div class="comment-main-fixed" style="border:1px solid blue; width:100%; background:white; margin-bottom:2mm; padding:5px;">
<span class="nick-red" style="color:red; font-weight:bold;">Nume/Nick</span> -- <span class="date-blue" style="color:darkblue;">data și ora</span> -- <span class="title-italic" style="color:red; font-style:italic;">Titlu</span>
<p style="margin:5px 0; white-space:pre-wrap;">Textul comentariului principal...</p>
<button class="btn-reply-small" onclick="openReply()" style="height:7mm; width:12mm; font-size:0.6rem; background:#4a323c; color:white; border:none; cursor:pointer;">Comentează</button>
</div>
<!-- Comentariu relativ -->
<div class="comment-reply" style="border:1px solid blue; margin-left:36mm; width:calc(100% - 36mm); background:white; padding:5px; margin-top:2mm;">
<span class="nick-red" style="color:red; font-weight:bold;">@Nume/Nick</span> -- <span class="date-blue" style="color:darkblue;">data și ora</span>
<p style="margin:5px 0;">Răspuns relativ...</p>
<button class="btn-reply-small" style="height:7mm; width:12mm; font-size:0.6rem; background:#4a323c; color:white; border:none; cursor:pointer;">Comentează</button>
</div>
</div>
</main>
</div>
<dialog id="reply-popup" style="border:1px solid #4a323c; padding:20px; background:#fdf5e6; max-width:90%;">
<div id="popup-content"></div>
<button onclick="document.getElementById('reply-popup').close()" style="margin-top:10px;">Închide</button>
</dialog>

<script>
const gUrl = "https://script.google.com/macros/s/AKfycbyus6US7dTTeNXVPtii1PFZcZb2jnlzGvf_I2DoLBjEkgJmfl7b8Y3ArisKEm6A9lriXw/exec"; // PUNE URL-UL AICI
let priv = {email:null, phone:null};
function setPrivacy(t, v) { priv[t] = v; document.getElementById('status-message').innerText = ""; }

// Încărcare automată comentarii
async function loadComments() {
const res = await fetch(gUrl);
const data = await res.json();
const display = document.getElementById('comments-display');
display.innerHTML = ""; 
// Aici vom genera HTML-ul pentru fiecare calup bazat pe data.parent
// Logica va grupa comentariile "Principal" în calupuri roșii
}

window.onload = loadComments;

document.getElementById('main-comment-form').onsubmit = async function(e) {
e.preventDefault();
const nick = document.getElementById('nick').value;
const em = document.getElementById('email').value;
const ph = document.getElementById('phone').value;
if ((em && !priv.email) || (ph && !priv.phone)) {
document.getElementById('status-message').innerText = "Selectează public / doar admin!";
document.getElementById('status-message').style.color = "red";
return;
}
await fetch(gUrl, { method: "POST", mode: "no-cors", body: JSON.stringify({
nick: nick, email: em, phone: ph, title: document.getElementById('title').value,
comment: document.getElementById('comment').value, privEmail: priv.email, privPhone: priv.phone
})});
alert("Trimis!");
location.reload(); 
};

function openReply(pNick, pDate, pTitle) {
const dialog = document.getElementById('reply-popup');
const content = document.getElementById('popup-content');
const tA = "textarea"; const pT = "p"; const iN = "input";
content.innerHTML = '<' + pT + ' style="color:red; font-size:0.8rem;">@' + pNick + ' -- ' + pDate + ' -- ' + pTitle + '</' + pT + '>' +
'<' + iN + ' type="text" id="rNick" placeholder="Nume/Nick" style="width:100%; margin-bottom:5px;">' +
'<' + tA + ' id="rComm" style="width:100%; height:80px; border:1px solid #4a323c;" placeholder="Răspunsul tău..."></' + tA + '>' +
'<button onclick="sendReply(\'' + pNick + '\')" style="background:#4a323c; color:white; border:none; padding:5px 20px; cursor:pointer; margin-top:5px;">Trimite Răspuns</button>';
dialog.showModal();
}
</script>
