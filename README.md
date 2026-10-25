# A dekani hivatal „mukodo” kapcsolati urlapja – hibariport

Repo: https://github.com/95HNR/umfst-bh01-kapcsolati-urlap
Keszitette: Sandor Hunor, INFO 3.EV

## 1. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Kepernyoolvasoval (NVDA, Chrome) az urlapmezokre fokuszalva a segedtechnologia csak a placeholder szoveget olvassa fel („szerkesztes, Teljes nev”), gepeles kozben pedig elveszik a kontextus, mivel a mezoknek nincs programozottan tarsitott cimkekjuk.
- **Gyokerok (melyik sor, melyik szabaly serul):** Az index.html 15-22. soraban az <input>, <select> es <textarea> elemekhez nincsenek <label> elemek rendelve. Serul a WCAG 1.3.1 (Info and Relationships) es 3.3.2 (Labels or Instructions) kriterium.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit: javitas(a11y) cimkek es azonosetok hozzaadasa az urlapmezokhez
  - *Elotte:*
    html
    <input type="text" name="nev" placeholder="Teljes nev" required>
  - *Utana:*
    html
    <label for="nev">Teljes nev</label>
    <input type="text" id="nev" name="nev" placeholder="Teljes nev" required>
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Kepernyoolvaso (NVDA) es billentyuzetes fokuszteszt.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** Szemantika elobb, stilus kesobb; minden urlapmezohoz kotelezo egyertelmu, programozottan osszekapcsolt <label> elemet biztositani.

## 2. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Bongeszoben (pl. Chrome) megnyitva az oldalt a focim fekete szinun marad, holott a vizualis elvaras szerint zoldnek kellene lennie.
- **Gyokerok (melyik sor, melyik szabaly serul):** A style.css 3. soraban eliras talalhato: .cim { colour: #0e7c66; ... }. A brit helyesirasusagu colour nem ervenyes CSS tulajdonsag, a helyes a color.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit: javitas(css) colour eliras javitasa color-re a cim osztalynal
  - *Elotte:*
    css
    .cim { colour: #0e7c66; font-size: 2rem; }
  - *Utana:*
    css
    .cim { color: #0e7c66; font-size: 2rem; }
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Vizualis ellenorzes bongeszoben (Chrome DevTools).
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** A CSS szintaktikai helyessegenek es tulajdonsagneveinek pontos ellenorzese fejlesztoi eszkozokkel.

## 3. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Mobilos bongeszoben (pl. iOS Safari / Android Chrome) az e-mail mezore fokuszalva a sima szoveges billentyuzet jelenik meg (hianyzik a @ gyorsbillentyu), es barmilyen ervenytelen szoveg (pl. „alma”) is elfogadott bekuldes elott.
- **Gyokerok (melyik sor, melyik szabaly serul):** Az index.html 16. soraban az e-mail mezohoz type="text" lett megadva a szabvanyos type="email" helyett.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit: javitas(html) email input tipus modositasa text-rol email-re
  - *Elotte:*
    html
    <input type="text" name="email" placeholder="E-mail cim" required>
    
  - *Utana:*
    html
    <input type="email" id="email" name="email" placeholder="E-mail cim" required>
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Mobilbongeszo / emulator virtualis billentyuzetenek vizsgalata es beepitett input validacio tesztelese.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** HTML5 szemantikus input tipusok hasznalata a jobb mobilos felhasznaloi elmeny (UX) es a nativ validacio erdekeben.

## 4. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Billentyuzettel (Tab) navigalva egyaltalan nem latszik, hogy eppen melyik urlapmezoben all a fukusz, a Kuldes gomb eleresehez pedig ketszer kell Tab-olni.
- **Gyokerok (melyik sor, melyik szabaly serul):** 
  1. A style.css 6. soraban az outline: none; teljesen eltavolitotta a fukuszkeretet alternativa nelkul (input:focus, select:focus, textarea:focus, button:focus { outline: none; }).
  2. Az index.html 24. soraban a gomb egy <a> elemen belulre lett agyazva (<a href="#"><button>Kuldes</button></a>). Serul a WCAG 2.4.7 (Focus Visible) es 2.1.1 (Keyboard) kriterium.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit: javitas(a11y-w3c) ervenytelen a elem eltavolitasa es lathato fukuszstilus hozzaadasa
  - *Elotte (CSS):*
    css
    input:focus, select:focus, textarea:focus, button:focus { outline: none; }
    
  - *Utana (CSS):*
    css
    input:focus, select:focus, textarea:focus, button:focus { outline: 2px solid #0e7c66; outline-offset: 2px; }
    
  - *Elotte (HTML):*
    html
    <a href="#"><button>Kuldes</button></a>
    
  - *Utana (HTML):*
    html
    <button type="submit">Kuldes</button>
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Tab-bejaras tesztelese billentyuzettel.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** WCAG 2.4.7 (Focus Visible) – soha ne tavolitsuk el a fukuszjelzest lathato, akadalymentes alternativa nelkul.

## 5. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Kepernyoolvasoval (NVDA) az oldal megtekintesekor a logo kepenel a „logo.png” fajlnevet olvassa be, az oldal többi szoveget pedig angol kiejtesi szaballyal probalja ertelmezni.
- **Gyokerok (melyik sor, melyik szabaly serul):** 
  1. Az index.html 2. soraban a <html> elembol hianyzik a lang="hu" attributum.
  2. Az index.html 9. soraban levo logo <img> elemébol hianyzik az alt attributum. Serul a WCAG 1.1.1 (Non-text Content) es 3.1.1 (Language of Page) kriterium.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit: javitas(a11y) lang=hu attributum es logo alt szoveg hozzaadasa
  - *Elotte:*
    html
    <html>
    
    <img src="logo.png" width="120" height="40">
    
  - *Utana:*
    html
    <html lang="hu">
    
    <img src="logo.png" width="120" height="40" alt="UMFST Dekani Hivatal logo">
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Kepernyoolvaso (NVDA) tesztelese magyar nyelvi kornyezetben.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** WCAG 3.1.1 es 1.1.1 – mindig allitsuk be a dokumentum nyelvet es adjunk meg leiro alt szoveget a kepekhez.

## 6. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** A W3C Markup Validation Service futtatásakor szintaktikai hiba jelentkezik a form vegen az elemek helytelen beagyazasa miatt.
- **Gyokerok (melyik sor, melyik szabaly serul):** Az index.html 24. soraban interaktiv elem (<a>) lett agyazva egy masik interaktiv elembe (<button>), ami HTML szabvanysertes.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit: Lasd a 4. hibanal (az <a> burkolat eltavolitasa).
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** W3C Markup Validation Service.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** Szemantikus HTML validitas biztositasa; interaktiv elemeket tilos egymasba agyazni.
