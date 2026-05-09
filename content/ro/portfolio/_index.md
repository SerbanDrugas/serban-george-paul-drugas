---
title: "Portfolio"
---

{{< rawhtml >}}
<style>
    .portfolio-grid {
        display: grid;
        grid-template-columns: 1fr 2fr; /* Proporția 1/3 și 2/3 */
        gap: 20px;
        width: 100%;
        min-height: auto;
    }

    .portfolio-column {
        padding: 10px;
    }

    /* Stilul titlurilor de coloană */
    .col-title {
        font-family: "Bookman Old Style", serif;
        font-weight: bold;
        color: red;
        text-align: center;
        display: block;
        margin-bottom: 20px;
        font-size: 1.5rem;
    }

    /* Stilul paragrafelor și hiperlink-urilor */
    .portfolio-item {
        margin-bottom: 15px;
        font-family: "Book Antiqua", serif;
    }

    .portfolio-link {
        color: darkblue !important;
        text-decoration: none;
        font-weight: bold;
    }

    .portfolio-link:hover {
        text-decoration: underline;
    }

    /* Ajustare pentru ecrane mici (mobile) */
    @media screen and (max-width: 768px) {
        .portfolio-grid {
            grid-template-columns: 1fr;
        }
    }
</style>

<div class="portfolio-grid">
    
    <!-- COLOANA STÂNGA (1/3): Cărţi -->
    <div class="portfolio-column">
        <span class="col-title">Cărţi</span>
        
        <div class="portfolio-item">
            <a href="LINK_GOOGLE_DRIVE_CARTE_1" target="_blank" class="portfolio-link">Titlu Carte 1</a>
            <p>Scurtă descriere dacă este cazul (opțional).</p>
        </div>

        <div class="portfolio-item">
            <a href="LINK_GOOGLE_DRIVE_CARTE_2" target="_blank" class="portfolio-link">Titlu Carte 2</a>
        </div>
    </div>

    <!-- COLOANA DREAPTA (2/3): Articole -->
    <div class="portfolio-column">
        <span class="col-title">Articole</span>
        
        <div class="portfolio-item">
            <a href="LINK_GOOGLE_DRIVE_ARTICOL_1" target="_blank" class="portfolio-link">Titlu Articol 1 - Eseu despre cultură</a>
            <p>Publicat în Revista X, data Y.</p>
        </div>

        <div class="portfolio-item">
            <a href="LINK_GOOGLE_DRIVE_ARTICOL_2" target="_blank" class="portfolio-link">Titlu Articol 2 - Analiză literară</a>
        </div>
    </div>

</div>
{{< /rawhtml >}}
