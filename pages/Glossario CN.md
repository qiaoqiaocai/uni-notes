---
title: Glossario Calcolo Numerico
layout: page
share: true
tags:
  - flashcards
  - review
---
In particolare  
- perturbazioni dati sistemi lineari  
- [lemma contrazioni](Glossario%2520CN.md##11.%2520Punti%2520fissi,%2520lemma%2520delle%2520contrazioni%2520con%2520dimostrazione.)  
- formule degli integrali  
  
##### 1. Sistema binario e sistema floating-point IEEE754 dei numeri macchina  
?  
Il sistema binario è un sistema di numerazione posizionale in base 2. Un numero intero x può essere rappresentato in base 2 come:  
$$x=\text{sign}(x)\sum\limits_{i=-\infty}^{+\infty}d_{i}\cdot2^{i}$$dove $$d_{i}\in\{0,1\}$$ sono le cifre binarie e $$\text{sign}(x)\in\{-1,+1\}$$ è il segno.  
  
Lo standard IEEE754 rappresenta i numeri reali in virgola mobile nella forma normalizzata: $$x=(-1)^{s}\cdot m\cdot2^{e}$$dove  
- $$s\in\{0,1\}$$ è il bit di segno  
- $$m=1.f_{1}f_{2}…f_{t}$$ è la mantissa normalizzata con $$1\leq m<2$$  
- e è l’esponente con $$e_{\min}\leq e\leq e_{\max}$$  
- t è il numero di bit per la mantissa frazionaria  
  
Per lo standard IEEE754 double precision:  
- 1 bit per il segno  
- 11 bit per l’esponente ($$e_{\min}=-1022,e_{\max}=1023$$)  
- 52 bit per la parte frazionaria della mantissa  
+++  
  
##### 2. Errori assoluto e relativo, errore di rappresentazione  
?  
Dato un $$x\in\mathbb{R}^{n}$$ e una norma fissata $$\|\cdot\|$$ per $$\mathbb{R}^{n}$$, l'errore assoluto è$$err_{ass}(\tilde{x}):=\|x-\tilde{x}\|$$mentre l'errore relativo è$$err_{rel}(\tilde{x}):=\frac{\|x-\tilde{x}\|}{\|x\|}\qquad\text{se }\|x\|\neq0$$Gli errori di rappresentazione sono gli errori causati dalla rappresentazione dei numeri in un sistema limitato. In particolare, prendiamo in considerazione i floating point durante troncamento e arrotondamento.  
L'errore assoluto di rappresentazione è$$err_{ass}(fl(x))=|x-fl(x)|\leq\frac{\varepsilon_\text{MACH}}{2}|x|$$mentre l'errore relativo di rappresentazione è$$err_{rel}(fl(x)):=\frac{|x-fl(x)|}{|x|}\qquad\forall|x|\neq0$$Stimiamo l'errore di rappresentazione $$fl^{Tr/Ar}$$  
- Troncamento  
- Arrotondamento  
+++  
  
##### 3. Operazioni macchina, loro (non) proprietà, precisione macchina  
?  
Per ogni operazione reale $$\ast$$, viene associata una operazione macchina $$\circledast$$ definita come$$x\circledast y=fl(fl(x)\ast fl(y))$$Alle operazioni macchina, non valgono le normali proprietà delle operazioni  
- non è commutativa  
- non è associativa  
- non distribuisce rispetto a $$\oplus$$  
- gli elementi neutri $$\oplus,\odot$$ non sono unici  
- non vale la proprietà di cancellazione  
  
Def. La **precisione macchina** è il più piccolo numero floating point positivo $$\varepsilon_{MACH}$$ per cui$$fl(1+\varepsilon_\text{MACH})\neq1$$è calcolato $$\varepsilon_\text{MACH}=2^{-t}=2^{1-t}/2$$  
(t è il numero di bit per mantissa frazionaria)  
+++  
  
##### 4. Stabilità di un algoritmo, stabilità delle operazioni macchina e cancellazione numerica  
?  
Un algoritmo si dice **stabile** se "non amplifica in modo incontrollato gli errori presenti sui dati". Vogliamo una stima di stabilità $$err_{rel}(output)\leq C_{STAB}\cdot err_{rel}(input)$$  
La **cancellazione numerica** avviene quando sottraendo due numeri molto vicini tra loro $$x-y$$ si ha che $$x\approx y$$.  
  
La stabilità della somma:  
Siano $$x_{1},x_{2},…,x_{n}$$ numeri floating-point. L’errore relativo nel calcolare la somma $$S_{n}=\sum_{i=1}^{n}$$ è limitato da $$\frac{|S_{n}-\tilde{S}_{n}|}{|S_{n}|}\leq \frac{n\cdot\varepsilon_\text{MACH}}{1-n\cdot\varepsilon_{\text{MACH}}}\approx n\cdot\varepsilon_\text{MACH}$$per $$n\cdot\varepsilon_\text{MACH}<<1$$  
+++  
  
##### 5. Problema matematico, buona posizione  
?  
Gli problemi matematici che affronteremo sono nella forma  
"Trovare $$\underset{\text{dominio}}{x\in X}:F(x,d)=0,\  \underset{\text{dati ammissibili}}{d\in D}$$"  
  
Un problema matematico è detto *ben posto* quando  
- ha la definizione del suo dominio e dei dati ammissibili  
- $$\forall d\in D,\quad\exists! x\in X:F(x,d)=0$$, soluzione unica  
- $$d\longmapsto x(d)$$ soluzione del problema è continua  
+++  
  
##### 6. Condizionamento numerico assoluto e relativo di un problema ben posto  
?  
Un problema si dice ben condizionato se "una piccola variazione dei dati corrisponde a piccole variazioni della soluzione".  
  
CONDIZIONAMENTO ASSOLUTO  
*locale* (di ordine $$\alpha$$) in $d\in D$$$\lim_{\tilde{d}\rightarrow d}\sup\frac{|x(\tilde{d})-x(d)|}{|\tilde{d}-d|^{\alpha}}\leq k_{\alpha}(d)\qquad0<\alpha\leq1$$*globale* (di ordine $$\alpha$$) in D$$\sup_{d\in D}k_{\alpha}(d)\leq k_{\alpha}<+\infty$$  
CONDIZIONAMENTO RELATIVO  
$$\limsup_{\tilde{d}\rightarrow d}\frac{|x(\tilde{d})-x(d)|}{x(d)}\left(\frac{|d|}{|\tilde{d}-d|}\right)=k_{\alpha}^{rel}(d)$$  
  
Osservazione: Il buon condizionamento è una proprietà del problema, non del metodo di soluzione.  
+++  
  
##### 7. Numero di condizionamento di una matrice e stima dell'errore relativo della soluzione di un sistema lineare con termine noto affetto da errore (con dimostrazione). Cosa succede se perturbiamo anche la matrice (no dimostrazione).  
?  
Per una matrice invertibile $$A\in\mathbb{R}^{n\times m}$$, il numero di condizionamento rispetto alla norma $$\|\cdot\|$$ è $$K(A)=\text{Cond}(A)=\|A\|\cdot\|A^{-1}\|$$Per la norma 2, $$K_{2}(A)=\frac{\sigma_{\max}(A)}{\sigma_{\min}(A)}$$ dove $$\sigma$$ sono i valori singoli.  
  
(Stima dell'errore, perturbazione del termine noto)  
Sia Ax=b un sistema lineare con A invertibile. Se $$\tilde{b}=b+\Delta b\text{ e }A\tilde{x}=\tilde{b}$$, allora$$\frac{\|x-\tilde{x}\|}{\|x\|}\leq K(A)\frac{\|\Delta b\|}{\|b\|}$$  
*Dimostrazione*  
In un sistema lineare $$Ax=b$$ con termine noto $$b$$ affetto da errore.  
$$\tilde{b}\approx b\qquad A\tilde{x}=\tilde{b}$$  
$$\tilde{b}=b+\Delta b\qquad\tilde{x}=x+\Delta x\qquad$$ voglio stimare l'errore relativo $$\dfrac{\|\Delta_{x}\|}{\|x\|}$$  
$$\begin{rcases}A(x+\Delta x)=b+\Delta b\\ Ax=b\end{rcases}\Rightarrow A(\Delta x)=\Delta b$$  
A è invertibile quindi $$\Delta x=A^{-1}\Delta b$$  
e in particolare $$\|\Delta x\|=\|A^{-1}\Delta b\|\leq\|A^{-1}\|\|\Delta b\|$$   
Da Ax=b abbiamo $$\|A\|\|x\|\geq\|b\|$$ quindi $\|x\|\leq\frac{\|b\|}{\|A\|}$$$\frac{\|\Delta x\|}{\|x\|}\leq\frac{\|A^{-1}\|\|\Delta b\|}{\|b\|/\|A\|}=\|A\|\|A^{-1}\|\frac{\|\Delta b\|}{\|b\|}=K(A)\frac{\|\Delta b\|}{\|b\|}$$  
In un sistema lineare $$Ax=b$$ dove sia A che b sono affetti da errore.  
$$(A+\Delta_{A})(x+\Delta x)=b+\Delta b$$  
$$(A+\Delta A)\Delta x=\cancel{b}+\Delta b-\cancel{Ax}-\Delta Ax$$  
+++  
  
##### 8. Algoritmi di sostituzione avanti e sostituzione indietro, condizioni per l'applicabilità.  
Usabile solo se A è triangolare superiore o inferiore.  
$$x(n)=b(n)/A(n,n)$$  
  
##### 9. Fattorizzazione LU senza pivoting: algoritmo, limitazioni alla sua applicabilità e problematiche numeriche  
?  
Data una matrice $$A\in\mathbb{R}^{n\times n}$$, la fattorizzazione LU consiste nel decomporre $$A=LU$$ dove L è triangolare inferiore con diagonale unitaria e U è triangolare superiore.  
  
Sia $$A\in\mathbb{R}^{n\times n}$$, la fattorizzazione A=LU esiste ed è unica se e solo se tutte le sottomatrici principali $$A_{k}$$ (formate dalle prime k righe e colonne) sono non singolari per k=1,2,...,n-1  
```  
Input: A R^(n*n)  
Output: L, U tali che A=LU  
  
A^(0) = A  
L^(0) = I_n  
per k = 1,2,...,n-1:  
	per i = k+1,...,n:  
		m_ik = a_ik^(k) / a_kk^(k)  
	u^(k) = [0,...,0, m_(k+1,k),...,m_nk]^T  
	L^(k) = L^(k-1) + u^(k)e_k^T  
	A^(k) = (1- u^(k)e_k^T)A^(k-1)  
U = A^(n-1)  
L = L^(n-1)  
```  
+++  
  
##### 10. Algoritmo LU con pivoting parziale per righe "idea" del pivoting e sua motivazione, output dell'algoritmo (no dettagli dell'algoritmo)  
?  
Per migliorare la stabilità numerica, ad ogni passo k si sceglie come pivot. L'elemento di modulo massimo nella colonna k (dalla riga k in poi) quindi $$PA=LU$$  
dove P è la matrice delle permutazioni.  
+++  
  
##### 11. Punti fissi, lemma delle contrazioni con dimostrazione.  
?  
Lemma delle contrazioni di Banach  
Sia $$F:\mathbb{R}^{n}\rightarrow\mathbb{R}^{n}$$ una contrazione, ovvero esiste $$L<1$$ tale che  
$$\|F(x)-F(y)\|\leq L\|x-y\|\quad\forall x,y\in\mathbb{R}^{n}$$  
allora:  
1. esiste un unico punto fisso $$x^{*}\in\mathbb{R}^{n}$$ tale che $$F(x^{*})=x^{*}$$  
2. per ogni $$x^{(0)}\in\mathbb{R}^{n}$$, la successione $$x^{(k+1)}=F(x^{(k)})$$ converge a $$x^{*}$$  
3. vale la stima dell'errore: $$\|x^{(k)}-x^{*}\|\leq L^{k}\|x^{(0)}-x^{*}\|$$  
  
*Dimostrazione*  
1. La successione è di Cauchy.  
Dato $$s^{(k)}=s^{(k+1)}-x^{(k)}$$ allora  
$$x^{(k+1)}-x^{(k)}=\sum\limits_{j=0}^{\ell-1}s^{(k+1)}\\\|s^{(k)}\|=\|F(x^{(k)})-F(x^{(k-1)})\|\leq L\|x^{(k)}-x^{(k-1)}\|=L\|s^{(k-1)}\|$$  
per induzione $$\|s^{(k)}\|\leq L^{k}\|s^{(0)}\|$$. Quindi  
$$\|x^{(k-1)}-x^{(k)}\|\leq\sum\limits_{j=0}^{\ell-1}\|s^{(k-1)}\|\leq\sum\limits_{j=0}^{\ell-1}L^{k+j}\|s^{(0)}\|\frac{1-L^{\ell}}{1-L}$$  
Poiché L<1, per k sufficientemente grande abbiamo $$\|x^{(k-\ell)}-x^{(k)}\|<\epsilon\quad\forall\epsilon>0,\ \forall\ell\geq0$$. Quindi la successione è di Cauchy.   
  
2. Il limite è punto fisso.  
Dato che $$\mathbb{R}^{n}$$ è completo, esiste $$x^{*}=\lim_{k\rightarrow\infty}x^{(k)}$$. Per continuità di F  
$$x^{*}=\lim_{k\rightarrow\infty}x^{(k+1)}=\lim_{k\rightarrow\infty}F(x^{(k)})=F(\lim_{k\rightarrow\infty}x^{(k)})=F(x^{*})$$  
  
3. Il punto fisso è unico.  
Siano $$x^{*},y^{*}$$ due punti fissi. Allora  
$$\|x^{*}-y^{*}\|=\|F(x^{*})-F(y^{*})\|\leq L\|x^{*}-y^{*}\|$$  
Poiché L<1, necessariamente $$\|x^{*}-y^{*}\|=0\text{ quindi }x^{*}=y^{*}$$.  
  
4. Stima dell'errore  
$$\|x^{(k+1)}-x^{*}\|=\|F(x^{(k)})-F(x^{*})\|\leq L\|x^{(k)}-x^{*}\|$$  
Per induzione: $$\|x^{(k)}-x^{*}\|\leq L^{k}\|x^{(0)}-x^{*}\|$$  
+++  
  
##### 12. Metodi iterativi lineari stazionari per soluzione di Ax=b: idea generale, condizioni per la consistenza, possibili vantaggi, risultato di convergenza generale che si deduce dal lemma delle contrazioni  
?  
Idea: Creare una successione di approssimazione della soluzione in modo iterativo con basso costo computazionale della singola iterazione.  
  
Per risolvere Ax=b, un metodo iterativo lineare stazionario ha la forma $$x^{(k+1)}=Ex^{(k)}+q$$dove E è la matrice di iterazione e q è un vettore costante.  
  
$$\exists x^{*}\in\mathbb{R}^{n}:x^{(k)}\rightarrow x^{*}$$  
  
Questo metodo converge alla soluzione di Ax=b per ogni $$x^{(0)}$$ se e solo se il raggio spettale p(E) < 1.  
+++  
  
##### 13. Metodo di Richardson: definizione, analisi della convergenza tramite norma e tramite proprietà spettrali (serie di Neumann).  
?  
Il metodo di Richardson per Ax=b è $$x^{(k+1)}=x^{(k)}+\alpha(b-Ax^{(k)})$$con parametro $$\alpha>0$$. La matrice di iterazione è $$E=1-\alpha A$$.  
  
Il metodo di Richardson converge se e solo se $$p(1-\alpha A)<1$$. Per matrici simmetriche definite positive con autovalori $$0<\lambda_{\min}\leq\lambda_{\max}$$, la scelta ottimale è $$\alpha_{opt}\frac{2}{\lambda_{\min}+\lambda_{\max}}$$  
+++  
  
##### 14. Precondizionamento del metodo di Richardson e metodi di Jacobi e di Gauss Seidel  
?  
Decomponendo la matrice A=L+D+U (triangolare inferiore, diagonale e superiore), il metodo di Jacobi è $$x^{(k+1)}=-D^{-1}(L+U)x^{(k)}+D^{-1}b$$  
Il metodo Gauss-Seidel è $$x^{(k+1)}=-(D+L)^{-1}Ux^{(k)}+(D+L)^{-1}b$$  
+++  
  
##### 15. Lemma dei cerchi di Gerschgorin e matrici strettamente diagonalmente dominanti, applicazione alla convergenza di Jacobi.  
?  
Gli autovalori di una matrice $$A=(a_{ij})$$ sono contenuti nell'unione dei cerchi $$G=\bigcup_{i=1}^{n}B(a_{ii},\sum\limits_{j\neq1}|a_{ij}|)$$dove $$B(c,r)=\{z\in\mathbb{C}:|z-c|\leq r\}$$.  
  
Se A è strettamente diagonalmente dominante per righe $$|a_{n}|>\sum\limits_{j\neq1}|a_{ij}|\qquad\forall i$$allora il metodo di Jacobi converge.  
+++  
  
##### 16. Criteri di arresto per metodi iterativi per la soluzione di sistemi lineari: residuo relativo e step  
?  
Per il criterio del residuo relativo si arrestano le iterazioni quando $$r_{rel}^{(k)}=\frac{\|Ax^{(k)}-b\|}{\|b\|}<\text{toll}$$  
Per il criterio dello scarto si arrestano le iterazioni quando $$\|x^{(k+1)}-x^{(k)}\|<\text{toll}$$  
Per il criterio del residuo vale che $$\frac{\|x^{*}-x^{(k)}\|}{x^{*}}\leq K(A)\cdot r_{rel}^{(k)}$$  
+++  
  
##### 17. Sistemi sovradeterminati esistenza e unicità della soluzione, minimi quadrati come generalizzazione del concetto di soluzione  
?  
Un sistema Ax=b con $$A\in\mathbb{R}^{m\times n},\ m>n$$, è sovradeterminato. In generale non ammette soluzione esatta.  
La soluzione ai minimi quadrati di Ax=b è $$x^{*}=\arg\min_{x\in\mathbb{R}^{n}}\|Ax-b\|_{2}^{2}$$  
+++  
  
##### 18. Teorema delle proiezioni ortogonali ed equazioni normali con dimostrazione  
?  
Sia $$V_{n}$$ un sottospazio di dimensione finita di uno spazio con prodotto scalare. Per ogni f, esiste un unico $$p^{*}\in V_{n}$$ tale che $$\|f-p^{*}\|=\min_{p\in V_{n}}\|f-p\|$$Inoltre $$p^{*}$$ è caratterizzato dalla condizione di ortogonalità$$\langle f-p^*,v\rangle=0$$  
*Dimostrazione*  
Esistenza.  
Unicità.  
Caratterizzazione.  
+++  
\[Fine primo appello\]  
  
##### 19. Metodo QR per la soluzione delle eq normali  
++  
  
##### 20. Radici di un eq non lineare: condizioni per l'unicità, condizioni per l'esistenza e metodo di bisezione (con dimostrazione)  
##### 21. Radici semplici e radici di molteplicità maggiore di 1, condizionamento del calcolo di radici  
Def "Molteplicità di una radice"  
  
  
##### 22. Metodo di Newton: euristica e definizione. Teorema di convergenza locale per radici semplici con dimostrazione  
Teorema: "convergenza locale per radici semplici"  
Dato un $$f\in\mathcal{C}^{2}([a,b])$$ e un $$x^{*}$$ radice semplice di $$f\in[a,b]$$, esiste un intorno I di $$x^{*}$$ tale che il metodo di Newton inizializzato con $$x_{0}\in I$$ converge a $$x^{*}$$. Inoltre si ha$$\lim_{k\rightarrow+\infty}\frac{|e_{k+1}|}{|e_{k+1}|^{2}}=\left|\frac{f''(x^{*})}{2f'(x^{*})}\right|$$  
23. Test di arresto per il metodo di Newton  
24. Newton come metodo iterativo: mappa di iterazione, versione del lemma delle contrazioni con g: [a,b]---->R, e applicazione alla convergenza di Newton per radici semplici  
25. Caso di radici multiple: convergenza lineare locale del metodo di Newton  
26. Problema generale dell'interpolazione di dati e funzioni su uno spazio lineare di funzioni continue: linearità e sistema di Vandermonde  
27.  Invertibilità della matrice di Vandermonde (con dimostrazione nel caso algebrico e base monomiale)  
28.  Base dei polinomi di Lagrange definizione uso derivazione e calcolo  
29.  Stabilità dell'interpolazione rispetto a perturbazioni in norma uniforme: costante di Lebesgue  
30.  Convergenza del polinomio interpolante: teoremi di Wierstrass e di Jackson, stima di Lebesgue considerazioni qualitative che ne discendono    
      
31. Nodi di Chebyshev e di Chebyshev lobatto vs nodi equispaziati  
32. Calcolo della base di Lagrange e sua valutazione con algoritmi di algebra lineare  
33. Base dei polinomi di Chebyshev, qualche proprietà utile  
34. formula di rappresentazione dell'errore di interpolazione  
35. Approssimzione ai minimmi quadrati condizioni per poter applicare il teorema delle proiezioni ortogonali  
36. Prodotti scalari e matrici simmetriche definite (o semidefinite positive) matrice Gramiana e teorema di pitagora  
37. Calcolo di basi ortogonali e identità di Parseval  
38. Versione generale del teorema delle proiezioni ortogonali (no dim perchè uguale a qualla già fatta)  
39. Approssimazione prodotta con il teorema delle proiezioni ortogonali, nucleo di riproduzione  
40. Stima alla Lebesgue dell'errore di approssimazione prodotta con il teorema delle proiezioni ortogonali  
41. Quadratura numerica: idea generale, quadratura interpolatoria, grado si esattezza, equazione dei momenti e pol di Lagrange    
      
42. Formule del trapezio e della parabola: calcolo dei pesi  
43. Rappresentazione dell'errore per formule del trapezio e della parabola semplici  
44. Stabilità della quadratura, importanza dei pesi positivi e conseguente necessità delle formule composte  
45. Formule composte dei trapezi e delle parabole (Cavalieri Simpson) definizione e rappresentazione dell'errore