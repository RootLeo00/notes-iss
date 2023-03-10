lez 1:

Domande da fare per i requisiti:

-   Chiedere che cos’è ogni parola che il committente dice. Ad esempio, cos’è il DDR ? Non basta il linguaggio naturale, serve avere del codice. Inoltre siccome è un robot, chiedere al cliente se ce l’ha lui.
    
-   Transport trolley: fa azioni in automatico ? oppure prende richieste di alto livello ? Quando comincia a muoversi? Che tipo di segnale lo fa muovere ? (SISTEMA DISTRIBUITO c/s)
  

lez 2:

le websocket vanno in maniera asincrona, mentre http in maniera sincrona.

Differenze risposta sync e async:

se gli do un cpmando sync di muoversi per 5 secondi ottengo per prima la risposta async che ah sbattuto.

![](https://lh4.googleusercontent.com/2bxUonyCpQBxhUTQ1u8gRZ8lZaIa3z7wN1d9LiHuwv2rcZ396aPdH678fMNFosJRRqqdyJ1vt9WNL2XwTeG-uBpyjrv_mPzlxtIwajJLnyRECqGl2o9kTOOksda6RVtisX4Y4xm609asAMEUQnE__pY)

Successivamente mi arriva la risposta sync:

![](https://lh3.googleusercontent.com/I9_leLXLbujPAsHC6RqBDe_2MD_HWzpguifZ9ExjzJoayC9ikCoXmwF7r2A2gMGaWQGBHdTRfudiBYFnF0fKOtMMdllu6vl02QWAoRK0cq0l_bItA0Xow42dYY-WnFOftvL1-JbX6Aw0AdW5kj1Ne5w)

  

Il sonar emette messaggi: è una entità attiva

  
  

Se mando più comandi async, ne cattura solo uno, perchè poi mi segnala:

![](https://lh6.googleusercontent.com/2MzBrf7f6FNtECI6fXJ5SMK9wGAbU-fpdVS-81as0tddALl8J6fInbpDw5Msei_AtZlTqh1HhE2FKuWc_km7zuRhsFiebLbUGyTA3c-YeQU9IpDhZsNcCse8QckGYiUwSM1f12LqLb_8SmOxgiNDFdI)

  
  

Gradle è domain specific: questo vuol dire che è stato inventato nel dominio della costruzione automatizzata del sw. Gradle vuol dire che io voglio che il sistema venga costruito automaticamente da gradle. Non è un linguaggio general purpose

  

lez 3:

todo:

-   input field con localhost parametrizzato dal cliente + bottone “CONNETTI”. Così viene modificato il localhost alla riga 8 del file node/clients/NaiveGui.html
    
-   scrivere test per webSocket in cartella test
    
-   nel template incollare i requirements che ci sono già nella repo
    
-   nel requirements analys mettere tu 
    
-   problem analysys capire cosa i req ti dicono di fare
    
-   in test plans mettere piani di test scritti in linguaggio formale (junit o pseudocodice)?
    

  
  

lez 4:

ANALISI DEI REQUISITI (Template23.html#l-analisi-dei-requisiti):

sicuramente non userò un pojo, perché come fai a interagire con un pojo? Per interagire con un pojo si deve chiamare un suo metodo. Ma non si può fare una interfaccia in cui chiami un metodo ? NO. Inoltre a noi serve un’entità che sappia inviare E ricevere messaggi. Un POJO riesce a inviare messaggi, ma non è fatto così bene per ricevere i messaggi.

“Leggendo la documentazione fornita dal committente (si veda VirtualRobot23.html), si evince che il virtual robot sarà implementato con un servizio (server), in quanto per interagire con esso bisognerà inviargli dei messaggi”

“il sistema è distribuito e avrà almeno 2 componenti: il virtual robot (VirtualRobot23.html, che poi tecnicamente è il server) e l’applicazione (Applicazione1.html#appl1-natura-dei-componenti, che sarà il client di virtual robot)”

Ci sono dei vincoli tecnologici? SI: il committente ha scritto che bisogna utilizzare interazioni http ([#vincolo tecnologico]). Quindi le interazioni saranno sincrone.

Il disegno dell'architettura a due componenti è:

![](https://lh3.googleusercontent.com/AGomX0YJJBwDW_CXxTt29QTs9H8K9U7aTeVy3pQh-YZ-XHIaoGh57PF9bhL4aByVeYLionlFeO7LM46BfQPeqL6zySfupceRVW8OVAMFfjJFm7s36Nz58kd_7dsLbtvM3R6IBq6m_eH59OQ0q8xwDRs)![](https://lh4.googleusercontent.com/6g0ElkAqLU_Aao97PkVlfo-PdJ4eZ9rDWHdDap6eWwYTX1mTVOrMNHg3FN3arojhYM5wB1MsvezCW-BITYXq_tr4pMddnUKvUy9h1w7ghmN7zHFsyPutqG8MtgmKZn4wJ4Mt7HtZKf3ZdlbYWAkQ5Kw)

Ho tolto WS, perchè ci è stato imposto come vincolo che dobbiamo utilizzare una interazione http.

  

ANALISI DEL PROBLEMA (Template23.html#l-analisi-del-problema):

chiarire le problematiche implicate dai requisiti: capisco le problematiche che quei requisiti mi impongono.

In Boundary Walk bisogna capire quali tipi di comandi bisogna dare con l’interazione http.

E’ fattibile? SI

Quali sono i problemi? Si riesce a fargli fare il perimetro, ma è molto molto difficile capire se il virtual robot ha fatto tutto il perimetro.

fornire informazioni su costi/tempi/risorse:capisco le problematiche che quei requisiti mi impongono e soprattutto quali tempi e quali risorse mi impongono.

Quanto ci metto a fare il progetto? Nella mia analisi temporale, ci metto x ore per fare il programma per fargli fare il giro (SPRINT A= implementazione), e tot x ore per fare il testing automatizzato (SPRINT B= testing).

Perché dividiamo in due sprint? Perchè bisogna prima avere un prodotto finito che funziona da fare vedere (è una piccola strategia di mercato)

Per sprint, vedi: [https://pm.stackexchange.com/questions/22510/sprint-vs-milestone-vs-release](https://pm.stackexchange.com/questions/22510/sprint-vs-milestone-vs-release)

Architettura logica: NATURA= iconcine; 

Ogni componente segue il principio di responsabilità: vuol dire che ogni componente ha delle specifiche responsabilità. Ad esempio, il componente applicazione ha la responsabilità di inviare i messaggi.

NB: nell’analisi possiamo mettere del codice o pseudocodice (deve essere capito dalla macchina). Ma non scriveremo mai “Io farei così: <codice>”, bensì “va fatto così:<codice>”.

  

PROGETTAZIONE (Template23.html#progettazione-e-sviluppo-evolutivo):

  

Problema: due protocolli => due codifiche. Vorremmo scrivere le soluzioni protocol independent. Quidni se un giorno un domani volessi utilizzare WS al posto di http? Dovrei cambiare il codice… bleah 🙁

Non esiste un’astrazione che non sia protocol independent?

  
  
  
  
  

parte di lab:  
in application1/build.gradle c’è “id 'eclipse' //crea i .classpath e .project

”

id 'jacoco' : plugin per fare i test in automatico (bellissimo)

  
  
  

lez6:

coding semplice

sistema distribuito

esiste abstraction gap

testing non semplice: perchè le chiamate http non ci danno molte info, ad esempio quando il robot collide, ci dice che collide ma non contro cosa. Inoltre questo tipo di test non è una somma di test sulle piccole singole mosse. infatti il test del perimetro nel complesso ha 2 problematiche maggiori: 1) capire che è in home in ogni momento. 2) capire che il robot ha fatto tutto il giro 1 volta. Analisi del problema: per capire che è in home, il robot ha il muro dietro e alla sua destra. Come conseguenza si ha che al termine del giro il robot non solo deve essere nella cella di home, ma anche direzionato nel verso giusto.

Abstraction gap: non abbiamo modo di verificare la direzione del robot.

Se a una certa mi accorgo che sto scrivendo le classi dell’app solo per far funzionare il testing poi succede CASINO. Obiettivo: perturbare la logica applicativa il meno possibile.

Idea di testing per sapere se il robot ha fatto il giro: posso usare un file di log che riesca a segnare ogni comando/messaggio del robot. Problema: sublimare questa idea. Ciò evitare si cablare contenuti tecnologici in essa del tipo “file di log”, perchè questo farebbe inserire nel codice delle indicazioni di salvataggio di info nel file che poi fa schifo.

Facciamo un modello matematico della scena: vedi “Appl1-HTTPSprint1.html#modello-della-stanza”. Ci vuole anche l’unità di misura.

Qualcuno ha anche pensato di dover usare la formula fisica s=v*t. Problema: se faccio girare il robot più volte scopro che non ha velocità costante. 

Chiedere al committente se il robot rimane sulla terra.

Non serve considerare il tempo e la velocità, ma utilizziamo come unità di misura la distanza: infatti in VirtualRobot23.html c’è scritto “Il robot virtuale (e in futuro anche quelli reali) viene considerato un oggetto inscrivibile in un cerchio di raggio R”. Quindi faccio diventare il robot stesso, l’unità di misura delle mie distanze.

#TODO: modellare la stanza con un pojo.

Sento necessità di sapere momento per momento la posizione del robot.

Obiettivo futuro: far fare il percorso al robot da A a B nella stanza anche se ci sono ostacoli. 

  

il request sync (classe che  è un’astrazione che abbiamo dovuto aggiungere perchè c’è un abstraction gap tra 

  

#todo: nuovo progetto App1-HttpSprint2 (Appl1-HTTPSprint2.html) in cui faccio tutto il template completo. Fare i test da soli anche se ci sono già nelle dispense. 

  

NB: fare la console, ma non distribuita, bensì in locale.

Fare test di walkbysteppingwithstop

Il sistema ha nel main solo la configurazione di cmdConsole e ApplCore1

Concepisco l’applicazione come una entità osservabile come dice il GOF. Cioè bisogna rilevare tutti i design pattern. Ad esempio il POJO è un pattern e quindi una entità osservabile.

Farò quindi tanti observer che sono accessori: uno che fa i log, uno i test, etc etc…

Vedi pattern observer

Vuol dire che aggancio tanti observer alla applicazione, così posso farle emettere informazioni.