---
title: "Gânduri, însemnări şi eseuri"
description: " "
---

<div class="blog-container">
<!-- COLOANA STÂNGĂ: FORMULARUL (Trimite pe email prin Formspree) -->
<aside class="blog-form-col">
<div id="status-message" style="color: #2c2c2c; font-size: 0.8rem; margin-bottom: 10px;">
Trimite-mi un gând sau un comentariu. Îl voi citi pe email și, dacă dorești, îl voi posta în dreapta.
</div>

<form action="https://formspree.io/f/xjglaagz" method="POST">
<input type="text" name="Nickname" placeholder="Nume / Nickname" required style="width:100%; border:1px solid #4a323c; margin-bottom:10px; padding:5px;">

<div class="input-group" style="margin-bottom:10px;">
<input type="email" name="Email" placeholder="Emailul tău (ca să-ți pot răspunde)" style="width:100%; border:1px solid #4a323c; padding:5px;">
<small style="font-size:0.7rem; color:#666;">* Emailul tău rămâne privat, doar eu îl voi vedea.</small>
</div>

<div class="input-group" style="margin-bottom:10px;">
<input type="text" name="Titlu" maxlength="20" placeholder="Titlu mesaj (opțional)" style="width:100%; border:1px solid #4a323c; padding:5px;">
</div>

<div class="input-group" style="margin-bottom:10px;">
<textarea name="Mesaj" maxlength="2500" required placeholder="Scrie aici mesajul tău..." style="width:100%; height:150px; border:1px solid #4a323c; resize:none; padding:5px;"></textarea>
<div style="display:flex; justify-content:space-between; align-items:center; margin-top:5px;">
<small style="font-size:0.7rem;">max. 2500 caractere</small>
<button type="submit" style="background:#4a323c; color:white; padding:8px 20px; border:none; cursor:pointer; font-weight:bold;">Trimite pe Mail</button>
</div>
</div>

<!-- Câmp ascuns pentru a preveni spam-ul -->
<input type="text" name="_gotcha" style="display:none">
</form>
</aside>

<!-- COLOANA DREAPTĂ: POSTĂRILE TALE (Le adaugi manual aici) -->
<main class="blog-comments-col" id="comments-display" style="display:flex; flex-direction:column; gap:5mm;">

{{< rawhtml >}}
<!-- CALUP EXEMPLU (Copiază acest bloc de la <div class="comment-block-red"> până la </div> pentru fiecare postare nouă) -->
<div class="comment-block-red" style="border:1px solid red; max-height:80mm; overflow-y:auto; padding:2mm; position:relative;">
    
    <!-- Postarea Ta (Administrator) -->
    <div class="comment-main-fixed bg-admin" style="border:1px solid blue; width:100%; padding:5px; margin-bottom:2mm;">
        <span class="nick-red">Serban</span> -- <span class="date-blue">23 Mai 2024</span> -- <span class="title-italic">Primul Eseu</span>
        <p style="margin:5px 0; white-space:pre-wrap;">Bine ați venit pe blogul meu! Aceasta este o postare adăugată manual în cod. Pentru a adăuga altele, doar copiez acest format în fișierul _index.md.</p>
</div>

<!-- Răspuns de la un vizitator (Adăugat manual de tine după ce primești mailul) -->
<div class="comment-reply bg-visitor" style="border:1px solid blue; margin-left:36mm; width:calc(100% - 36mm); padding:5px; margin-top:2mm;">
<span class="nick-red">@Vizitator</span> -- <span class="date-blue">24 Mai 2024</span>
<p style="margin:5px 0;">O idee foarte bună să postezi manual! Succes!</p>
</div>

</div>
<!-- SFÂRȘIT CALUP -->
{{< /rawhtml >}}

</main>
</div>
