---
layout: page
title: Tecnologie Web
share: true
---
html, css, php, javascript  
slide possono avere informazioni sforvianti  
  
*Digital Divide* = il divario nell'accesso delle nuove tecnologie presenti nel mondo  
  
| Prima cifra | Categoria         |  
| ----------- | ----------------- |  
| 1           | Informatica       |  
| 2           | Successo          |  
| 3           | Reinderizzo       |  
| 4           | Errore del client |  
| 5           | Errore del server |  
Codici di stato HTTP (es. 404 error)  
  
## Standard HTML5  
Costruito da WHATWG (Web Hypertext Application Technology) mentre W3G era fissato con XTML 2.0  
  
> "In case of conflict, consider user over authors over implementers over specifiers over theoretical purity."  
> - HTML5 Working Group  
  
Ha introdotto:  
- canvas, area di disegno iterattiva  
- video, audio senza bisogno di plug-in  
- iterazione con le API  
- GeoLocation API di W3C  
- Javascript multithread  
- pagine/applicazioni anche offline  
- non più elementi deprecati ma obsoleti  
  
HTML gestisce gli errori ma, la giusta sintassi è ancora importante.  
  
| Struttura    | Presentazione | Comportamento            |  
| ------------ | ------------- | ------------------------ |  
| testo (html) | grafica (css) | codice (javascript, php) |  
  
è importante la loro separazione (file diversi).  
  
### Sintassi  
La sintassi XHTML  
- i tag e gli attributi sono case sensitive (minuscolo)  
- i tag devono essere sempre chiusi (tranne i tag in linea)  
- i tag devono essere aperti e chiusi nell'ordine giusto  
- i valori degli attributi sono tra "virgolette doppie"  
- tutti gli attributi devono avere valore (tranne quelli il cui valore è nome dell'attributo)  
- un elemento in linea non può contenere un elemento di blocco  
  
I tag META  
Fondamentali in ogni pagina sono  
```html  
<meta charset="utf-8">  
<meta name="description" >  
<meta name="keywords" >  
```  
  
*http-equiv* condizionano la manipolazione del documento  
```html  
<meta http-equiv="refresh" content="1;URL=nuovaURL">  
<meta http-equiv="expires" content="5L">  
```  
  
*name*  
- description: breve descrizione dei contenuti della pagina web  
- keywords: lista di parole chiavi separate da una virgola  
- copyright  
- author  
- robots: utilizzato per prevenire l'indicizzazione di una pagina  
- rating: ranking del contenuto  
  
```html  
<meta name="viewport" content="width=device-width" />  
```  
  
Attributi  
- core: id, class, title e style  
- i18n (internalisation): lang e dir  
- evento: onclick, ontap, etc  
  
`id` si riferisce un a un singolo elemento nella pagina e può essere puntato da un link.  
In css, id ha maggiore specificità di class.  
  
Definire nomi `class` generali prevedendo modifiche future.  
  
Ogni pagina deve avere  
- `<header>, <footer>`  
- `<main>` contenuto principale  
- `<nav>` barra di navigazione  
- `<h1>` titolo principale  
  
Si possono poi usare   
`<aside>` ovvero contenuti che, se rimossi, non tolgono informazioni,  
`<section>` sezioni con ordine,  
`<article>` sezioni indipendenti dagli altri  
  
L'unico caso in cui il `<br>` è consentito è nella gestione dei form.  
`<pre>` mantiene la formattazione scritta.  
  
| carattere | codice   |  
| --------- | -------- |  
| spazio    | `&nbsp;` |  
| "         | `&quot;` |  
| <         | `&lt;`   |  
| >         | `&gt;`   |  
| &         | `&amp;`  |  
| €         | `&euro;` |  
  
Non usare la cosmesi del testo `<i>, <b>` ma  
`<em>`: enfasi  
`<strong>`: forte enfasi  
  
Le *intestazioni* devono essere *usate seguendo l'ordine*. Modifica l'aspetto con il css.  
  
Per citare si devono usare i tag `<blockquote>`, `<q>` in linea o `<cite>` per indicare l'autore e source  
`<abbr>` abbreviazioni dove nel title mettere la lettura se è acronimo  
`<time>` con attributo datatime scritto in formato americano  
`<figure>` per immagini con caption `<figcaption>`  
`<picture>` per immagini con differenze per dispositivo  
  
```html  
<dl> <!-- Definition List -->  
	<dt>Mammifero</dt>  
	<dd>I mammiferi sono una classe di vertebrati a diffusione cosmopolita caratterizzata dall'allattamento della prole.</dd>  
```  
  
`alt` sono obbligatori alle immagini.  
La definizione del `width` e `height` dipende dalla quantità di immagini per favorire il caricamento della pagine agli utenti.  
Lazy loading tramite l'attributo loading per caricare l'immagine solo quando visibile. (loading=eager/lazy)  
  
```html  
<picture>  
	<source media="min-width:650px" srcset="img_pink.jpg">  
	<source media="min-width:465px" srcset="img_white.jpg">  
	<img src="img_orange.jpg" alt="Flowers">  
</picture>  
```  
  
Ancora dei link devono essere significativi a dove portano.  
Mai aprire link allo stesso sito in altre schede.  
No ai link circolari, ovvero che riportano alla stessa pagina.  
  
`tabindex` per portare il focus con tab e determinare l'ordine di tabulazione. `tabindex="-1"` per essere inaccessibili da tab, utile per elementi nascosti.  
  
`accesskey` indica il carattere per portare il focus all'elemento. Meglio non usarli perché possono andare in conflitto con altre scorciatoie da tastiera.  
  
Il tag caption dopo il tag table mette un titolo sopra alla tabella.  
Nell'aria-describedby viene messo il riferimento id alla descrizione della struttura della tabella.   
```html  
<table area-describedby="">  
	<caption>Tabella 1</caption>  
	<thead>  
		<tr><th></th>...</tr>  
	</thead>  
	<tfoot><!-- Uguale a thead --></tfoot>  
	<tbody>...</tbody>  
</table>  
```  
  
#### Form  
```html  
<form action="file.php" method="post">  
</form>  
```  
*get* inserisce informazioni all'url dopo ?parametro=valore; ha un limite di lunghezza  
*post* non mette le informazioni in chiaro e permette di mandare file  
  
`name` indica la chiave associata ai valori inseriti da mandare al server  
`readonly` per i campi non editabili dall'utente  
`disabled` per campi non editabili dall'utente e che non vengono inviati al server  
  
Il tag `<input>` può essere di diversi type  
- text, password, checkbox, radio, submit, reset, hidden, file, button  
- html5 aggiunge i tag: number (range e inserisce frecce alla quale si possono definire il passo), color, email, url, tel, search, datatime  
Descritti da `<label for="id_input">`. Per input cliccabili, la zona di label fa parte dell'input.  
html5 aggiunge gli attributi di controllo: required, formvalidate, placeholder, autocomplete, autofocus, spellcheck, multiple (per più file), pattern (espressione di validazione input)  
  
Per il `<textarea>`, gli attributi rows e cols sono obbligatori.  
Il tag `<select>` non sono preferibili per accessibilità.  
  
Al `<form>` si possono dare i seguenti attributi:  
- `target` indica dove visualizzare la risposta  
- `autocomplete` per permettere l'autocomplete dal browser  
- `Novalidate`  
  
Tag `<canvas>` è un riquadro dove si disegna in grafica vettoriale con Javascript  
```html  
<audio controls="control">  
	<source src="song.ogg" type="audio/ogg" />  
	<source src="song.mp3" type="audio/mp3" /> <!-- Richiede royalties -->  
	<p>Testo sostitutivo dell'audio.</p>  
</audio>  
<p>Testo sostitutivo dell'audio.</p> <!-- Utile nei browser che non supportano <audio> -->  
```  
  
html5 permette di lavorare con database in locale  
- Web Storage offre sessionStorage e localStorage che memorizzano in <nome, valore>  
- Web SQL Database  
- IndexedDB è memorizzazione basata su oggetti  
  
html5 permette di lavorare offline con il file .manifest  
```  
CACHE MANIFEST  
# versione 0.1  
  
CACHE:  
pagina1.html  
pagina2.html  
  
NETWORK: (pagine usabili solo con rete)  
pagina.cgi  
  
FALLBACK:  
online.html offline.html  
```  
  
## CSS (Cascading Style Sheets)  
La versione attuale è CSS3.  
Animazioni e transizioni non sono sempre supportati ([caniuse.com](https://caniuse.com/)).  
  
> selettore { blocco di dichiarazioni separati da ; }  
  
Sui dispositivi elettronici si usano i font sans-serif, in quelli stampati quelli serif.  
  
Evitare style come attributo (vietato) e CSS embedded.   
Usare i fogli di style esterni diversi. Importante definire quello di stampa.  
```html  
<head>  
	<link ref="stylesheet" media="screen" href="screen.css" type="text/css" />  
	<link ref="stylesheet" media="print" href="print.css" type="text/css" />  
</head>  
```  
  
Per distinguere i dispositivi a cui imporre lo style, usare screen con larghezza imposta  
```  
media="screen and (max-width:480px), only screen and (max-device-width:480px)"  
```  
Si applica anche sulle finestre.  
  
```html  
	<head>  
		<style type="text/css">  
			@import url("file.css") print;  
		</style>  
	</head>  
```  
Usare import solo per importare stili esterni particolari.  
  
Ordine di priorità dello stile  
1. Impostazioni personali dell'utente  
2. dichiarazioni definite *!important* (da evitare, rallenta)  
3. stile *inline* definiti dall'autore (non usare)  
4. stile *embedded* definiti dall'autore (solo per test)  
5. fogli di stile *esterni* definite dall'autore  
6. Impostazioni predefinite del browser  
L'ordine di applicazione è inverso.  
  
Selettore di tipo, .id o \#class  
- possono essere raggruppati separati da ,  
- possono selezionare tutti i discendenti (`p em {...}` seleziona tutti gli em in p)  
- possono selezionare solo i figli diretti `div1 > p` (i p contenuti in altri tag dentro div1 non sono selezionati)  
- possono selezionare solo il suo adiacente h1 + h2 {...}  
  
Selettore di attributo `elementname[attributename=attribute=value]`  
  
selettore:pseudoclasse { dichiarazioni }  
pseudoclasse è uno stato dell'elemento  
pseudoelementi sono posizioni relativo all'elemento  
  
**Specificità** (# id, # attributi, # tag html)  
Le class vengono contati come attributo.  
```css  
pre{  
	color: green;  
	background-color: black;                        /* 0, 0, 1 */  
}  
div.exception pre{ color: red; }                    /* 0, 1, 2 */  
div#error pre{ color: orange; }                     /* 1, 0, 2 */  
ol[id="debug_list"] li div > pre { color: white; }  /* 0, 0, 4 (usa sel attr) */  
```  
  
| tipo     | unità      | definizione                           |  
| -------- | ---------- | ------------------------------------- |  
| relative | em         | altezza di M del font                 |  
|          | rem        | root em                               |  
|          | vh, vw     | viewport height e width               |  
|          | %          | relativo all'elemento princ           |  
| assolute | cm, mm, in | centimetri, millimetri, inch (2,54cm) |  
|          | px         | numeri pixel a schermo                |  
|          | pt         | punti (1/72 inch)                     |  
|          | pc         | pica (12 punti)                       |  
  
Evitare di usare sistemi di misura assoluti (eccezione col border)  
  
Colori definiti con nome, rgb e \#rrggbb  
Font con grazie e testo giustificato in stampa, senza grazie e alineato a sinistra su schermo.  
  
```css  
@font-face{ /* descrizione font */  
	font-family: "nome", sans-serif;  
	src:  
		local("local_path"),  
		url("url");  
}  
```  
Importa una sola versione del font. Si può usare direttamente l'import. Fare attenzione che le licenze dei font siano redistribuibili.  
  
z-index indica chi sta sopra quando ci sono sovrapposizioni  
  
Immagini che portano contenuti devono essere definiti su html e descritti da alt.  
Quelli decorativi possono essere aggiunti da css, ricordare di mettere un colore di fall-back nel caso l'immagine non carica.  
```css  
div { background: #fff url("img/cover.png") top fixed norepeat;}  
```  
  
width e height di div definiscono solo il contenuto. Il padding è lo spazio tra il contenuto e il bordo del div. Il background-image copre solo questi due.  
![](./img/Pasted%20image%2020251014112901.png)  
La definizione delle misure di padding, border e margin avviene in senso anti-orario.  
Quando viene in contatto con un altro margine, il margine più piccolo collassa.  
  
Display possono essere inline, block e none. None è utile per rimuovere oggetti non utili nella stampa.  
  
Block centrato con margin: auto  
float non sposta l'elemento ma il suo contenuto.  
  
Nella stampa togliamo elementi di navigazione. Serve interlinea 1.5  
```css  
a:link:after, a:visited:after {  
	content: " ["attr(href)"] ";  
}  
a:[href^="/"]:after { /* link relativi */  
	content: " [http://www.sito.it"attr(href)"] ";  
}  
```  
  
css3 selettori  
\[attr\] seleziona elemento con attributo su cui possono essere applicati equazioni (=, -=, |=, etc)  
  
:target agisce sulla destinazione del link  
:nth-child(n/odd/even)   
  
Variabili `--nomeVar` usate con `var(--nomeVar)`. Rende il codice più mantenibile: un singolo luogo per cambiare valori che vengono riutilizzati nella pagina.  
```css  
:root {  
	--colorText: black;  
	--colorBack: white;  
}  
body {  
	color: var(--colorText);  
	background-color: var(--colorBack);  
}  
```  
  
@media queries usati per dare stili differenti per usi e dispositivi differenti.  
  
column-count, column-width  
- inline-block, gli elementi sono blocchi in linea  
- display-table rende un elemento in una tabella, da evitare  
  
**Flexbox**  
```css  
.cards { /* contenitore */  
	display: flex;  
	flex-wrap: wrap; /* permette di andare a capo */  
	align-items: <flex-start / flex-end / center / stretch>;  
}  
  
.cards li {  
	flex: <grow> <shrink> <width>;  
}  
```  
flex-direction, righe o colonne  
  
**Grid**, richiede un grande costo di rendering  
```css  
.section {  
	display: grid;  
	grid-template-columns: 1fr 1fr 1fr;  
	grid-gap: 10px;  
	grid-template-areas:   
		"h h h"  
		"b b b"  
		"m c n";  
}  
header { grid-area: h; } breadcrumb { grid-area: b; }  
.menu { grid-area: m; } .content { grid-area: c; }  
.news { grid-area: c; }  
```  
Si consiglia usarle per la struttura generale della pagina non per contenuto.  
  
Con questi layout, l'ordine del contenuto può, quindi, essere qualsiasi.  
Deve essere ordinato a seconda dell'ordine di tab o importanza al browser.  
  
## Accessibilità  
Contrasto appropriato nella pagina  
  
Solitamente ci si aspetta che le persone siano soggettivi e fallibili ma le macchine come imparziali. Aumenta il grado di insoddisfazione dei clienti quando incontrano bias tecnologici.  
  
2004, 2010 Legge Stanca  
La legge Accessibility Act si impone su tutti i prodotti volti ai privati.  
Obbligo di Dichiarazione di Accessibilità dopo 28 giugno 2025. Gli altri devono essere accessibili entro 2030.  
  
Linea guida   
Priorità è basato sull'impatto che un elemento possiede sull'accessibilità.  
1. priorità 1, sviluppatore *deve* conformarsi al punto di controllo; è un requisito base  
2. priorità 2, sviluppatore *dovrebbe* conformarsi al punto di controllo; rimuove barriere significative  
3. priorità 3, sviluppatore *può* migliorare  
  
Conformità A conforme a tutte le priorità 1  
	AA conforme a tutte le priorità 1 e 2  
	AAA conforme a tutte le priorità 1, 2 e 3  
  
E' obbligatorio arrivare a conformità AA. La conformità AAA è troppo oneroso e spesso sono soggettive a una sola parte dell'utenza mentre possono anche danneggiare l'altra.  
  
Principi dell'accessibilità PURO  
1. *Perceivable*  
2. *Understandable*, comprensibile e navigabile  
3. *Robust* su tutte le piattaforme  
4. *Operable*, controllo su tutto quello che c'è su schermo  
  
Principi di progettazione  
- trasformazione elegante  
	separazione da struttura dalla presentazione  
	alternativa testuale, alternativa a mouse  
- rendere il contenuto comprensibile e navigabile  
	strumenti di navigazione e orientamento (breadcrumb)  
  
Lampeggiare non più di 3 secondi.   
Si può aggiungere una mappa di navigazione.  
  
WCAG  
- Mostra sempre la posizione del focus.  
- Focus percepibile da tutti  
- Dimensione minima degli elementi di interazione  
- Autocompletamento delle informazioni già chieste  
- Drag&Drop accessibile  
- Aiuti consistenti  
- Autenticazione accessibile  
  
Evitare testi con effetti di movimento e font troppo elaborati.  
I font con più distanza tra x-factor all'altezza della rig totale e più spazio nell'apertura dei caratteri sono più accessibili. Spessore aiuta i contrasti.  
Usare `qp, db, 0O, iI1l, rn m` per testare l'accessibilità dei font.  
  
Titolazione corretta, navigazione per screen-reader.  
  
Numeri molto grandi devono essere scritti a parole (10 milioni), semplificare numeri frazionari ove possibile. Evitare percentuali.  
  
Evitare timeout tranne se strettamente necessario. Aiutare con autocomplete e reminders.  
  
```html  
<input type="password" name="pin"  
	required="required" aria-required="true"  
	data-msg-required="Per favore, inserisci la tua password"  
	data-msg-invalid="Formato non corretto" >  
```  
  
Se un elemento è sottolineato, deve essere un link. I link devono essere riconoscibili. Deve esserci una differenza visiva tra link visitati e non (3:1). Indicare la dimensione del file in caso di download.  
Per aiutare gli screen-reader si può usare un attributo `title=""` nei link.   
Devono essere accessibili con tab-index. `tabindex=0` fa switch della loro accessibilità tramite tab.  
  
Le immagini che non portano informazioni o che hanno descrizione in testo usano `alt=""`.  
  
Errore 404, rassicurare l'utente e riportarli alle pagine corrette.  
  
html  
```html  
<nav aria-label="aiuti alla navigazione" class="listHelp">  
	<ul>  
		<li><a class="navHelp" href="#contenuto">Vai al contenuto</a></li>  
		<li><a class="navHelp" href="#breakingNews">Vai alle <span lang="en">news</span></a></li>  
	</ul>  
</nav>  
<main tabindex="-1"> <!-- non è selezionabile da tab --!>  
```  
css  
```css  
.navHelp {  
    position: absolute;  
    text-indent: -999em;  
}  
  
.navHelp:focus {  
    position: static;  
    text-indent: 0em;  
}  
```  
Per fare in modo che al cambio di pagina, lo screenreader non debba rileggersi l'header e il menù.  
  
height:0 non si usa, declassato dai motori di ricerca.  
  
Per fare in modo di mostrare un'immagine che rappresenti il testo ma che rimani comunque leggibile dallo screen-reader:  
```css  
.hidden1 {  
	font-size: 6em; /* dimensione immagine */  
	text-indent: -999em;  
}  
  
h1.hidden2 { /* preferibile */  
	background-image: url(...);  
}  
  
.hidden2 {  
	text-indent: 100%;  
	white-space: nowrap;  
	overflow: hidden;  
}  
```  
  
Per bottoni usare button e input type="submit".  
  
**Tabelle**  
Preferibilmente non usarle per layout. Usa la bidimensionalità, difficile da spiegare da screen-reader.  
- associare una descrizione (*aria-describedby*)  
- definire abbreviazioni per le intestazioni (*abbr*)  
- associare le intestazioni alle celle (*scope*, preferibile)  
  
```html  
<!-- SCOPE -->  
<table aria-describedby="descr">  
	<caption>Libri della biblioteca</caption>  
	<tr><th scope="col">Titolo</th>  
		<th scope="col">Editore</th>...  
	</tr>  
	<tr><td scope="row">Il bastino di <span lang="en">Basketville</span></td>  
		<td>Feltrinelli</td>...  
	</tr>  
</table>  
<p id="descr">La tabella contiene l'elenco dei libri in libreria. Ogni riga descrive un libro con titolo, autore, editore, costo.</p>  
```  
  
- associare le celle alle intestazioni (*headers*), quando sono necessari è possibile che la tabella non è ben strutturata  
  
```html  
<!-- HEADERS -->  
<table>  
	<tr><th id="c1" abbr="Lun" axis="giorno">Lunedì</th>  
		<th id="c2" abbr="Mar" axis="giorno">Martedì</th>...  
	</tr>  
	<tr><th id="m1" axis="materia" colspan="7">Italiano</th></tr>  
	<tr><th id="o1" axis="ora">8.00</th>  
		<td headers="m1 r1 o1">1D</td>  
		<td headers="m1 r2 o1">1D</td>...  
	</tr>  
	<tr><th id="o2" axis="ora">9.00</th>  
		<td headers="m1 r1 o2"></td>...  
	</tr>  
</table>  
```  
  
Per renderle capibili visualmente al mobile, usare *data-title*.  
```css  
/* CSS per mobile */  
thead, tfoot { display: none; }  
  
tr, th, td { display: block; }  
  
th[data-title]:before, td[data-title]:before {  
	content: attr(data-title) ":\00A0";  
	font-weight: bold;  
}  
```  
  
**Form**  
placeholder sparisce alla prima iterazione, non usarlo come etichetta  
- corredare i campi dei form con label  
- raggruppare le voci con optgroup o fieldset  
- utilizzare title per informazioni aggiuntive  
- rendere gli errori reversibili, comprensibili  
  
```html  
<input type="text" id="name" required autocomplete="name">  
```  
  
**Colori** (1.4.3 liv AA)  
Tinta + Saturazione + Luminosità  
Contrasto tra testo con il background.  
Tinta diversa con contrasto uguale possono sembrare le stesse per i daltonici. Controllare sempre in bianco e nero.  
Link visitato e non visitato sono di colori diversi e possibilmente in contrasto.  
  
(4.5 : 1) testo normale  
(3 : 1) testo grande e tra link visitati e non  
Color Universal Design Organisation (CUDO)  
  
Non usare contrasti troppo forti, possono stancare l'utente.  
Attenzione alle immagini di background, dare un colore di sfondo in cui ricadere quando non carica.  
  
Animazioni (2.2.2 e 2.3.3)  
```css  
@media(prefers-reduced-motion: reduce) {  
	/* CSS per disabilitare le animazione */  
}  
  
@media (prefers-reduced-motion: no-preference) {  
	/* CSS che definiscono le animazioni */  
}  
```  
  
**WAI-ARIA**   
(Web Accessibility Initiative - Accessible Rich Internet Applications)  
Definiscono ruoli, stati e proprietà definendo una semantica a un elemento della pagina. Da usare solo quando non ci sono alternative.   
  
Sempre preferibile tag e attributi specifici prima dei role.  
- alert: indica un contenuto segnalato subito all'utente  
  alertdialog: stesso di alert ma è un elemento nel suo interno  
- presentation: per evitare che lo screenreader legga l'elemento  
  
Stati sono proprietà speciali che descrivono le condizioni correnti degli elementi, modificabile da Javascript.  
Proprietà usati per aggiungere significato a un elemento.  
  
Regole ARIA  
1. Se si può usare un elemento o attributo html5 usare quello invece di questi. Evitare di dare informazioni doppioni.  
2. Non cambiare la semantica se possibile.  
3. Tutti i controlli ARIA devono essere usabili da tastiera. `role="button"` raggiungibile da tab  
4. Non usare `role="presentation", aria-hidden="true"` su elementi che possono ricevere focus.  
5. Tutti gli elementi interattivi devono avere un'etichetta accessibile.  
  
I nomi accessibili   
lkj.-  
Contenuto  
I video e audio devono avere sottotitoli e/o trascrizioni.  
Evitare i CAPTCHA il più possibile.  
  
Ciechi e ipovedenti  
Ipovedenti hanno una vista parziale per cui non possono guidare mezzi. Hanno un grande range non definibile.  
  
## SEO (Search Engine Optimisation)  
SERP: Search Engine Response Page, pagine ritornate da un motore di ricerca  
Obiettivo: <= 30 posizioni, meglio nelle <=10 (prima pagina)  
Tecnica + Marketing = SEO  
  
**Fattori Interni**  
- keywork nel tag title (max 55 caratteri)  
- meta tag description (max 145 caratteri, con call to action)  
- uso corretto delle intestazioni  
- attributo alt  
- velocità di caricamento  
- qualità del codice, no link errati (404 gestita)  
- alberatura facilmente navigabile  
- mai contenuti duplicati  
- ancora link attinente al testo  
- social sign, abilità di condividere etc.  
  
**Fattori esterni**  
- inbound link, link esterni  
  crescita deve essere organica, avere una motivazione  
- link baiting  
- link popularity  
  
Progettazione dei siti web  
Da ordine di importanza:  
1. Analisi dei requisiti, casi d'uso   
2. Dati e informazioni  
3. Applicazioni e servizi  
4. Accessibilità e usabilità  
5. Interfaccia e stile  
6. Strumenti e manutenzione  
Si devono avere le licenze di distribuzione.  
  
Modello mentale  
- modalità di interazione  
- aspettattive dell'utente  
struttura del documento, strumenti di navigazione e strategia di browsing  
  
Fare attenzione a rompere le aspettative esterne per non disturbare quelle interne.  
Globalizzato o localizzato? Differenze in iconografia, colori e contenuti.  
  
Il tag `description` non influenza molto il posizionamento in una SERP, ma come viene visualizzato in esso.  
  
## Architettura dell'informazione  
archiviazione, organizzamento e ricerca dei siti web  
Contesto + Contenuto + Utenti  
  
Disorientamento  
1. di cosa tratta la pagina  
2. dove mi trovo  
3. dove posso andare  
  
Sovraccarico cognitivo = troppi elementi (di qualsiasi dei sensi)  
  
Modello informativo too-simple  
domanda -> ricerca/navigazione -> risposta -> fine  
Spesso termina con insuccesso, contesto ignorato.  
  
> **Metafora della pesca**  
> - *tiro perfetto*: utente sa cosa cercare  
> - *trappola per aragoste*: utente non sa precisamente cosa cercare ma si aspetta di imparare durante la ricerca per aiutarli alla prossima ricerca  
> - *pesca con la rete*: utente non sa cosa cercare e vuole esaminare un po' tutto di un certo argomento  
> - *boa di segnalazione*: utenti vogliono ritrovare un elemento informativo utile  
  
3 step: classificazione, navigazione, etichettatura  
  
Problema dell'organizzazione  
- Ambiguità  
- Eterogeneità  
- Differenza di prospettiva  
- Diversità politiche  
  
Schemi organizzativi esatti  
L'informazione è suddivisa in sezioni mutualmente esclusivi. Progettazione e manutenzione facile.  
Problema: devi sapere cosa stai cercando.   
  
Schemi organizzativi ambigui  
- {::nomarkdown} <u>schemi per argomento (topic)</u> {:/nomarkdown}  
  problema: difficile quando ci sono troppi argomenti  
- {::nomarkdown} <u>schemi orientati al compito (task)</u> {:/nomarkdown}  
  funzionalità organizzati come collezioni  
- {::nomarkdown} <u>schemi metaforici</u> {:/nomarkdown}  
  connettere concetti virtuali con le sue controparti reali  
  problema: non sempre comprensibile, inconsistente  
  
La soluzione migliore è usare uno schema ibrido.  
  
Strutture organizzative della navigazione  
- sequenza  
- gerarchia (menu)  
  albero ampio e poco profondo: meglio non superare 4-5 livelli, 7 per cose specifiche; massima ampiezza 10  
  Legge di Hick = il tempo necessario per compiere una scelta non dipende dal numero di scelte (quantità) ma nel modo in cui sono presentate (qualità)  
- a faccette, anche detto a matrice  
  ogni informazione può essere vista da diversi punti perché ha diversi attributi filtrabili  
- ipertesto  
  
Web Designer  
1. progettazione del layout  
2. organizzazione dell'informazione  
  
Interfacce consistenti  
se si vuole modificare le convenzioni, guidare gli utenti  
  
Above the fold (area sicura) = area visualizzata senza alcun scroll, non sempre la stessa  
  
Risolvere il problema di disorientamento.  
Altre informazioni utili:  
- come sono arrivato qui?  
- da chi è gestita questa pagina?  
- dove posso trovare informazioni più approfondite? etc..  
  
Titolo dal particolare al generale  
L'arancio sprona a prendere decisioni (es. acquisto).  
  
Schema a schede con menù che porta alle diverse pagine.  
  
LSD (Logo Search Directory)  
Directory presentano categorie con le loro sottocategorie  
Considerare la dimensione della casella di ricerca: una casella lunga suggerisce la possibilità di digitare frasi  
  
Il design fluido nei diversi dispositivi varia  
- dimensione (%)  
- caratteri supportati  
- colori supportati  
- formati immagini supportati  
per non perdere la sua usabilità.  
  
Layout a variabilità controllata / Responsive: le dimensioni possono variare all'interno di certi intervalli.  
  
| media-screen |                              |  
| ------------ | ---------------------------- |  
| 480px        | telefoni vecchi in landscape |  
| 600px        | tablet piccoli in portrait   |  
| 768px        | telefoni, tablet in portrait |  
| 1024px       | tablet in landscape          |  
| 1200px       | schermi grandi               |  
  
Strategia creare per far funzionare al caso peggiore e poi migliorare.  
1. i contenuti alla base  
2. markup semantico  
3. design visivo  
4. interazione  
  
Design sui telefoni cellulari  
Bottoni AA(24x24), AAA(44x44)  
Tenere conto delle zone più facilmente raggiungibili con la singola mano.  
  
Regole per il rendering veloci  
- Salvare più immagini sullo stesso file e poi visualizzarne una parte  
- Un solo file CSS e uno Javascript che siano minificati  
- Evitare librerie Javascript pesanti  
- Se possibile usare cache.manifest e canvas  
- Limitare uso di grid  
- Limitare l'uso di immagini di decorazione  
  
Fornire feedback, risultato dell'azione eseguita  
e feedforward, informazioni su cosa accadrà eseguendo una azione  
  
Funzionale(efficace e efficiente) > Robusta > Usabile > Accattivante  
  
*Design emozionale*  
Le emozioni aiutano gli utenti a interessarsi e ricordarsi informazioni, es. contrasto  
Attenzione a non usarne troppo, confonde.  
  
Contenuto non interessante o presentato male porta apatia.  
Verifica  
- personalità corretta per il brand  
- non troppo simile al competitor  
- interviste e utenti reali  
- evitare tecnicismi e abbreviazioni  
- usare la forma attiva e personale  
- evitare verbi nascosti  
Nei form mettere gli esem3pi sotto invece che nella casella.  
area-live per gli errori, non solo il colore rosso  
  
## PHP  
Personal Home Page, ora PHP Hypertext Processor  
Linguaggio di scripting interpretato (costruito al momento dell'esecuzione)  
  
PHP permette di mescolare codice PHP con HTML; da evitare. Usiamo invece dei segnaposto o echo dei txt dell'html della pagina.  
  
**Operazione di sostituzione**  
```php  
preg_replace($pattern, $sostituzione, $stringa); //cerca in$pattern nella $stringa e   
str_replace($dasostituire, $sostituzione, $stringa); //no espressioni solo stringa  
```  
  
| simbolo  | funzionalità                                               |  
| -------- | ---------------------------------------------------------- |  
| .        | qualsiasi carattere                                        |  
| \[abc]   | qualsiasi a, b o c                                         |  
| \[^abc]  | non a, b o c                                               |  
| \[a-g]   | caratteri da a a g                                         |  
| \d \w \s | carattere numerico, alfanumerico, spazio o tabulazione     |  
| \D \W \S | carattere non numerico, alfanumerico, spazio o tabulazione |  
| ...\|... | or                                                         |  
| (...)    | gruppo                                                     |  
| ^        | all'inizio                                                 |  
| $        | alla fine                                                  |  
  
MySQLi  
  
## Javascript  
Si deve usare con degrado aggraziato, ovvero il sito deve mantenere le proprie funzionalità anche quando il javascript non funziona.   
  
Finestre modali (da usare solo per comunicazioni urgenti)  
`alert("Errore")`  
  
```javascript  
var lista = new Array(1,2,"pane");  
var lista_spesa = ["pane", "latte"];  
lista_spesa[1]->"latte";  
lista.length->4;  
  
var voti = ["Marcus":"7", "Charles":"10"];  
```  
  
*BOM (Browser Object Model)* è un modello ad oggetti {::nomarkdown} <u>non standardizzato</u> {:/nomarkdown} che consente di interagire con il browser.  
  
| Elemento        | Oggetto  |  
| --------------- | -------- |  
| Finestra        | window   |  
| Barra indirizzi | location |  
| Barra status    | status   |  
  
Per una completa separazione tra presentazione e funzionalità, gli script sono chiamati con `window.onload`.  
  
Per selezionare un particolare elemento con  
Proprietà  
- `x.innerHTML`, il testo contenuto da x  
- `x.nodeName, x.nodeValue`, nome/valore del nodo x  
- `x.parentNode, x.firstChild, x.lastChild`, nodo padre, primo/ultimo figlio di x  
- `x.childNodes`, array con i nodi figli di x  
Metodi  
- `x.getElementById(id)`  
  
Non si deve definire quale browser l'utente sta usando ma quale funzionalità sono disponibili.  
  
Si possono fornire aiuti alla compilazioni ad hover  
```javascript  
var aiuti = ["Inserisci il nome in questo modo:\n\t nome cognome",  
	"L'email deve avere questa forma:\n\t login@dominio"];  
function messages(n_messaggio) {  
	document.getElementById("aiuti").value = aiuti[n_messaggio];  
}  
```  
  
I *cookies* sono piccoli file di testo memorizzati sul computer dell'utente e possibilmente scambiati tra client e server. Contengono informazioni salvati dai siti web.  
```javascript  
function setCookie(nome, valore, giorni) {  
	var oggi = new Date();  
	var scadenza = new Date();  
	scadenza.setTime(oggi.getTime()+24*giorni*3600000);  
	document.cookie = nome+"="+escape(valore)+"; expires="+scadenza.toGMTString();  
}  
  
function delCookie(nome) {  
	setCookie(nome, "");  
}  
```  
La loro grandezza massima è 4093kb; per poter salvare più informazioni, usare localStorage, sessionStorage o indexedDB.  
  
**AJAX (Asynchronous Javascript and XML)** realizza uno scambio asincrono di dati. Usata per mandare e ricevere dati evitando modifiche al lato client.   
  
19 marzo (accattivante e accessibile)  
  
| Requisiti progetto |                                                                                 |  
| ------------------ | ------------------------------------------------------------------------------- |  
| Accessibilità      | img decorativi hanno alt=""                                                     |  
| Leggero            | contenuti leggeri (evita png etc.)                                              |  
| Usabile            | controlli in diversi browser e risoluzioni                                      |  
| Trovabile          | SEO e leggibilità da crawlers (Javascript off)                                  |  
| CSS puro           | non usare framework css                                                         |  
| Funzionalità       | login php con controlli di input<br>schema di ricerca ibrido (esatto + ambiguo) |  
| Relazione          | tutte le decisioni di design, SEO                                               |  
| Testato            | verificato dopo ogni modifica                                                   |  
