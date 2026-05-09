---
title: "Portfolio"
---

{{< rawhtml >}}
<style>
    .portfolio-grid {
        display: grid;
        grid-template-columns: 1fr 1fr; /* Proporția 1/2 și 1/2 */
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
            <a href="https://www.pdfcoffee.ro/crestinismul-in-dacia-in-secolele-i-vi/" target="_blank" class="portfolio-link">2021: Creştinismul în Dacia, în secolele I-VI</a>
            <p>Cartea Crestinismul in Dacia in secolele I-VI PDF este scrisă de autorul Serban Drugas, sub egida editurii THEOSIS. Publicată în 2021, cartea are 218 de pagini, iar dimensiunile sale sunt 210 x 145 x 15 mm.</p>
        </div>

        <div class="portfolio-item">
            <a href="https://www.amazon.com/Mapping-Ptolemaic-Serban-George-Drugas/dp/6156405178" target="_blank" class="portfolio-link">2020: Mapping Ptolemaic Dacia</a>
            <p>Trivent. / This volume is a contribution to the decipherment of Ptolemy's universal map, with focus on the territory known as Dacia.</p>
        </div>

        <div class="portfolio-item">
            <a href="https://archive.org/details/DrugasSerbanCuvntul" target="_blank" class="portfolio-link">2017: Cuvântul care iese din gura lui Dumnezeu (Argonaut, Cluj-Napoca).</a>
            <p>Disponibil: PDF complet. / Available: Full PDF.</p>
        </div>

        <div class="portfolio-item">
            <a href="https://www.agaton.ro/editura/334/editura-argonaut" target="_blank" class="portfolio-link">2013: Antropologia în lumina Revelaţie şi a ştiinţei (Argonaut, Cluj-Napoca).</a>
            <a href="https://ef35210f-3098-419c-b288-dddb25960284.filesusr.com/ugd/033281_981f1c17326f446e84fc8d1c20f1b551.pdf" target="_blank" class="portfolio-link">PDF parţial pag. 1-80 (1).</a>
            <a href="https://45be3ac8fa.cbaul-cdnwnd.com/51c8c356da4a711d3819b9ce00e4f011/200000002-4df0f4df12/DRUGAS_SERBAN_DOCTORAT_ANTROPOLOGIA_PAG_1_80.pdf" target="_blank" class="portfolio-link">PDF parţial pag. 1-80 (2).</a>
            <p>See also, Publisher's site. / Vezi şi: Site editură.</p>
        </div>

    </div>

    <!-- COLOANA DREAPTA (2/3): Articole -->
    <div class="portfolio-column">
        <span class="col-title">Articole</span>
        
        <div class="portfolio-item">
            <a href="https://serbangpdrugas.wixsite.com/burebistas/publications" target="_blank" class="portfolio-link">Cărţi şi articole pe Wix</a>
            <p>Vezi pe site-ul respectiv, în josul paginii.</p>
        </div>

        <div class="portfolio-item">
             <a href="https://serban-george-paul-drugas.webnode.ro/despre-noi/" target="_blank" class="portfolio-link">Cărţi şi articole pe Webnode</a>
             <p>Vezi pe site-ul respectiv, în josul paginii.</p>
        </div>
    </div>

</div>
{{< /rawhtml >}}
