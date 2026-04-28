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
const gUrl = "https://script.google.com/macros/s/AKfycbyus6US7dTTeNXVPtii1PFZcZb2jnlzGvf_I2DoLBjEkgJmfl7b8Y3ArisKEm6A9lriXw/exec"; // ASIGURĂ-TE CĂ E URL-UL NOU DE DUPĂ DEPLOY
let priv = {email:null, phone:null};
let isAdmin = localStorage.getItem('isBlogAdmin') === 'true';

function setPrivacy(t, v) { priv[t] = v; document.getElementById('status-message').innerText = ""; }

async function loadComments() {
const display = document.getElementById('comments-display');
display.innerHTML = "Se încarcă comentariile...";
try {
const res = await fetch(gUrl);
const allData = await res.json();
display.innerHTML = "";

// Separăm principalele de răspunsuri
const principals = allData.filter(c => c.parent === "Principal" || !c.parent);
const replies = allData.filter(c => c.parent !== "Principal" && c.parent);

principals.forEach(p => {
let calup = document.createElement('div');
calup.className = 'comment-block-red';
let html = '<div class="comment-main-fixed ' + (p.nick === "Admin" ? "bg-admin" : "bg-visitor") + '" style="border:1px solid blue; padding:5px; margin-bottom:2mm;">';
if(isAdmin) html += '<button class="admin-delete-btn" onclick="deleteComm(' + p.id + ')">Șterge</button>';
html += '<span class="nick-red">' + p.nick + '</span> -- <span class="date-blue">' + new Date(p.date).toLocaleString() + '</span>' + (p.title ? ' -- <span class="title-italic">' + p.title + '</span>' : '');
html += '<p style="white-space:pre-wrap; margin:5px 0;">' + p.comment + '</p>';
html += '<button class="btn-reply-small" onclick="openReply(\''+p.nick+'\',\''+p.date+'\',\''+p.title+'\')">Comentează</button></div>';

// Adăugăm răspunsurile acestui calup
const theseReplies = replies.filter(r => r.parent === p.nick + "_" + p.date);
theseReplies.forEach(r => {
html += '<div class="comment-reply ' + (r.nick === "Admin" ? "bg-admin" : "bg-visitor") + '" style="border:1px solid blue; margin-left:36mm; padding:5px; margin-top:2mm;">';
if(isAdmin) html += '<button class="admin-delete-btn" onclick="deleteComm(' + r.id + ')">Șterge</button>';
html += '<span class="reply-intro">@' + r.parent.split('_')[0] + ' -- ' + r.title + '</span>';
html += '<span class="nick-red">' + r.nick + '</span> -- <span class="date-blue">' + new Date(r.date).toLocaleString() + '</span>';
html += '<p style="margin:5px 0;">' + r.comment + '</p>';
html += '<button class="btn-reply-small" onclick="openReply(\''+r.nick+'\',\''+r.date+'\',\''+r.title+'\')">Comentează</button></div>';
});

calup.innerHTML = html;
display.appendChild(calup);
});
} catch(e) { display.innerHTML = "Eroare la încărcare."; }
}

async function deleteComm(id) {
if(!confirm("Ștergi definitiv?")) return;
await fetch(gUrl, { method: "POST", mode: "no-cors", body: JSON.stringify({action: "delete", id: id})});
location.reload();
}

// Sistem Admin: Dacă scrii parola secretă la Nickname, devii Admin
document.getElementById('main-comment-form').onsubmit = async function(e) {
e.preventDefault();
const nick = document.getElementById('nick').value;
if(nick === "ParolaTaSecreta") { // Schimbă "ParolaTaSecreta" cu ce vrei tu
localStorage.setItem('isBlogAdmin', 'true');
alert("Salut, Admin!");
location.reload();
return;
}
// ... restul codului de trimitere de dinainte ...
};
</script>
