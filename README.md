# A dekani hivatal „mukodo” kapcsolati urlapja – hibariport

Repo: https://github.com/95HNR/umfst-bh01-kapcsolati-urlap
Keszitette: Sandor Hunor, INFO 3.EV

## 1. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Kepernyoolvasoval (NVDA, Chrome) az urlapmezokre fokuszalva a segedtechnologia csak a placeholder szoveget olvassa fel („szerkesztes, Teljes nev”), gepeles kozben pedig elveszik a kontextus, mivel a mezoknek nincs programozottan tarsitott cimkekjuk.
- **Gyokerok (melyik sor, melyik szabaly serul):** Az  index.html  15-22. soraban az  <input> ,  <select>  es  <textarea>  elemekhez nincsenek  <label>  elemek rendelve. Serul a WCAG 1.3.1 (Info and Relationships) es 3.3.2 (Labels or Instructions) kriterium.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit:  javitas(a11y) cimkek es azonosetok hozzaadasa az urlapmezokhoz 
  - *Elotte:*
       html
    <input type="text" name="nev" placeholder="Teljes nev" required>
       
  - *Utana:*
       html
    <label for="nev">Teljes nev</label>
    <input type="text" id="nev" name="nev" placeholder="Teljes nev" required>
       
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Kepernyoolvaso (NVDA) es billentyuzetes fokuszteszt.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** Szemantika elobb, stilus kesobb; minden urlapmezohoz kotelezo egyertelmu, programozottan osszekapcsolt  <label>  elemet biztositani.

## 2. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Bongeszoben (pl. Chrome) megnyitva az oldalt a focim fekete szinun marad, holott a vizualis elvaras szerint zoldnek kellene lennie.
- **Gyokerok (melyik sor, melyik szabaly serul):** A  style.css  3. soraban eliras talalhato:  .cim { colour: #0e7c66; ... } . A brit helyesirasu  colour  nem ervenyes CSS tulajdonsag, a helyes a  color .
- **Javitas (commit link, elotte/utana kodreszlet):** Commit:  javitas(css) colour eliras javitasa color-re a cim osztalynal 
  - *Elotte:*
       css
    .cim { colour: #0e7c66; font-size: 2rem; }
       
  - *Utana:*
       css
    .cim { color: #0e7c66; font-size: 2rem; }
       
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Vizualis ellenorzes bongeszoben (Chrome DevTools).
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** A CSS szintaktikai helyessegenek es tulajdonsagneveinek pontos ellenorzese fejlesztoi eszkozokkel.

## 3. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Mobilos bongeszoben (pl. iOS Safari / Android Chrome) az e-mail mezore fokuszalva a sima szoveges billentyuzet jelenik meg (hianyzik a  @  gyorsbillentyu), es barmilyen ervenytelen szoveg (pl. „alma”) is elfogadott bekuldes elott.
- **Gyokerok (melyik sor, melyik szabaly serul):** Az  index.html  16. soraban az e-mail mezohoz  type="text"  lett megadva a szabvanyos  type="email"  helyett.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit:  javitas(html) email input tipus modositasa text-rol email-re 
  - *Elotte:*
       html
    <input type="text" name="email" placeholder="E-mail cim" required>
       
  - *Utana:*
       html
    <input type="email" id="email" name="email" placeholder="E-mail cim" required>
       
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Mobilbongeszo / emulator virtualis billentyuzetenek vizsgalata es beepitett input validacio tesztelese.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** HTML5 szemantikus input tipusok hasznalata a jobb mobilos felhasznaloi elmeny (UX) es a nativ validacio erdekeben.

## 4. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Billentyuzettel (Tab) navigalva egyaltalan nem latszik, hogy eppen melyik urlapmezoben all a fokusz, mert a keret teljesen ki lett kapcsolva.
- **Gyokerok (melyik sor, melyik szabaly serul):** A  style.css  6. soraban az  outline: none;  teljesen eltavolitotta a fokuszkeretet alternativa nelkul ( input:focus, select:focus, textarea:focus, button:focus { outline: none; } ). Serul a WCAG 2.4.7 (Focus Visible) kriterium.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit:  javitas(a11y-w3c) ervenytelen a elem eltavolitasa es lathato fokuszstilus hozzaadasa 
  - *Elotte:*
       css
    input:focus, select:focus, textarea:focus, button:focus { outline: none; }
       
  - *Utana:*
       css
    input:focus, select:focus, textarea:focus, button:focus { outline: 2px solid #0e7c66; outline-offset: 2px; }
       
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Tab-bejaras tesztelese billentyuzettel.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** WCAG 2.4.7 (Focus Visible) – soha ne tavolitsuk el a fokuszjelzest lathato, akadalymentes alternativa nelkul.

## 5. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Kepernyoolvasoval (NVDA, Chrome) megnyitva az oldalt a segedtechnologia angol kiejtesi szaballyal probalja olvasni a magyar szoveget.
- **Gyokerok (melyik sor, melyik szabaly serul):** Az  index.html  2. soraban a  <html>  nyitoelembol hianyzik a  lang="hu"  attributum. Serul a WCAG 3.1.1 (Language of Page) kriterium.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit:  javitas(a11y) lang=hu attributum es logo alt szoveg hozzaadasa 
  - *Elotte:*
       html
    <html>
       
  - *Utana:*
       html
    <html lang="hu">
       
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Kepernyoolvaso (NVDA) tesztelese magyar nyelvi kornyezetben.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** WCAG 3.1.1 – a weboldalakon mindig kotelezo megadni a fo nyelvet a helyes felolvasas erdekeben.

## 6. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** Kepernyoolvasoval (NVDA) az oldal megtekintesekor a logo kepenel a nyers „logo.png” fajlnevet olvassa be a segedtechnologia.
- **Gyokerok (melyik sor, melyik szabaly serul):** Az  index.html  9. soraban levo logo  <img>  elemébol hianyzik az  alt  attributum. Serul a WCAG 1.1.1 (Non-text Content) kriterium.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit:  javitas(a11y) lang=hu attributum es logo alt szoveg hozzaadasa 
  - *Elotte:*
       html
    <img src="logo.png" width="120" height="40">
       
  - *Utana:*
       html
    <img src="logo.png" width="120" height="40" alt="UMFST Dekani Hivatal logo">
       
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** Kepernyoolvaso (NVDA) es vizualis ellenorzes.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** WCAG 1.1.1 – minden informaciot hordozo kephez kotelezoertelmu leiro helyettesito szoveget ( alt ) adni.

## 7. hiba
- **Hiba leirasa es reprodukalasa (lepesek, bongeszo, segedtechnologia):** A W3C Markup Validation Service futtatasakor szintaktikai hiba jelentkezik a form vegen, es a Kuldes gomb eleresehez ketto darab Tab lepes szukseges.
- **Gyokerok (melyik sor, melyik szabaly serul):** Az  index.html  24. soraban interaktiv elem ( <a> ) lett agyazva egy masik interaktiv elembe ( <button> ), ami HTML szabvanysertes es duplikalt fokuszpontot okoz.
- **Javitas (commit link, elotte/utana kodreszlet):** Commit:  javitas2(a11y-w3c) ervenytelen a elem eltavolitasa es lathato fokuszstilus hozzaadasa 
  - *Elotte:*
       html
    <a href="#"><button>Kuldes</button></a>
       
  - *Utana:*
       html
    <button type="submit">Kuldes</button>
       
- **Hogyan tesztelted (W3C validator, Lighthouse, Tab-bejaras, kepernyoolvaso):** W3C Markup Validation Service es Tab-bejaras.
- **Tanulsag / erintett alapelv (pl. Szemantika elobb, stilus kesobb; WCAG-kriterium):** Szemantikus HTML validitas biztositasa; interaktiv elemeket tilos egymasba agyazni.
