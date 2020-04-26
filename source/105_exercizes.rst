================
Esercizi di base
================


In questa prima sequenza di esempi ed esercizi prenderemo confidenza con le widgets più semplici, senza preoccuparci più di tanto del layout, ma solo cercando
di seguire bene le regole della OOP, stare attenti a utilizzare correttamente la libreria wxPython e di prendere confidenza con la documentazione, che bisognerà forzatamente consultare per alcuni degli esercizi proposti.

Iniziamo!



**Esercizio 001 (Button)**

Creare una applicazione con una finestra con titolo *Ciccio* che contiene un pulsante. Quando clicchi il pulsante, il titolo
diventa *Pippo*, quando lo clicchi di nuovo ritorna ad essere *Ciccio* e così via.



**Esercizio 002 (Button, StaticText, TextCtrl)**

Creare una applicazione con una finestra che contiene una StaticText, inizialmente vuota, una TextCtrl e un pulsante. Quando l'utente
clicca sul pulsante, il testo contenuto nella TextCtrl viene copiato nella StaticText e la TextCtrl ripulita.



**Esercizio 003 (Button)**

Creare una applicazione con un pulsante *CHIUDI*. Quando lo clicchi, l'applicazione si chiude.



**Esercizio 004 (RadioButton, StaticText)**

Testare il codice precedente, cambiando la domanda iniziale in *Dimmi come vieni a scuola*, nell'elenco delle opzioni ci devono essere una serie
di mezzi di trasporto con cui è possibile si venga a scuola. Nella stringa in basso, alla selezione del mezzo di trasporto, deve apparire la scritta:
*vieni a scuola in MEZZODITRASPORTO*.



**Esercizio 005 (TextCtrl, RadioButton, Button, StaticText)**

Applicazione con una TextCtrl per inserire il nome e un RadioButton per selezionare il sesso (opzioni *Maschio*, *Femmina*) più un pulsante e una StaticText.
Al click sul pulsante va visualizzata nella StaticText la scritta *Buongiorno signor NOME* oppure *Buongiorno signora NOME* a seconda del sesso selezionato.

Come ulteriore difficoltà si può aggiungere il controllo dell'ora: se il pulsante viene cliccato fra le 6 e le 14, si utilizza *Buongiorno*, fra le 14 e le 22
si scrive *Buonasera*, fra le 22 e le 6 si scrive *Buonanotte*.



**Esercizio 006 (TextCtrl, RadioButton, Button)**

Applicazione con una TextCtrl e un pulsante. L'utente scrive una serie di parole separate da virgola nella TextCtrl e quando preme il pulsante appare
un RadioButton con le opzioni indicate nella TextCtrl e separate da virgole.



**Esercizio 007 (Text, CheckBox)**

Reimplementa lo stesso esercizio dell'esempio, partendo però da una tupla che contiene l'elenco dei cibi da controllare e da un dizionario
inizialmente vuoto, che in ogni elemento conterrà come chiave il nome del cibo e come valore la CheckBox abbinata ad esso.



**Esercizio 008 (Text, CheckBox)**

Identico all'esercizio precedente, ma la StaticText non visualizza il testo delle CheckBox selezionate ma il numero di queste. Ad esempio all'inizio
vi sarà scritto "0 CheckBox selezionate" e il numero crescerà o diminuirà a seconda che vengono attivate o no le CheckBox.



**Esercizio 009 (Button, CheckBox)**

la finestra contiene 3 pulsanti: il primo massimizza la finestra, il secondo la iconizza sulla barra delle applicazioni, il terzo la chiude.
Sotto i pulsanti ci sono 3 CheckBox che corrispondono ognuna ad un pulsante: se la CheckBox è spuntata, il pulsante corrispondente è abilitato,
altrimenti è disabilitato. Fate attenzione a sincronizzare la spunta sulla CheckBox con l'abilitazione del pulsante corrispondente e viceversa.



**Esercizio 010 (TextCtrl, Button, Combo)**

La finestra presenta una TextCtrl, un pulsante e una Combo, inizialmente con un'unica opzione (un testo a piacere). L'utente inserisce una stringa nella TextCtrl
e se non è vuota, quando clicca il pulsante quella stringa viene aggiunta come opzione alla Combo e la TextCtrl ripulita.



**Esercizio 011 (App, Combo)**

la finestra presenta una Combo con opzioni '600x400', '800x600', 'massimizza'. Quando l'utente seleziona una delle opzioni la finestra si ridimensiona secondo quanto
indicato.



**Esercizio 012 (App, Combo, CheckBox)**

Dichiarate una tupla di valori qualsiasi e con essa create sia una Combo che elenca tutti gli elementi della tupla, sia una serie di CheckBox, una per ogni valore
della tupla. Quando l'utente seleziona uno dei valori della Combo la CheckBox corrispondente cambia stato, venendo spuntata oppure no a seconda del suo stato
precedente.



**Esercizio 013 (ListBox, Button, StaticText)**

Inserite nella App una ListBox con una sequenza di voci e la possibilità di selezionarne contemporaneamente più di una. Quando l'utente clicca il pulsante
nella StaticText vengono visualizzate tutte le voci selezionate.



**Esercizio 014 (ListBox, TextCtrl, Button)**

Inserite nella App una ListBox inizialmente vuota, una TextCtrl e un Button. L'utente digita qualcosa nella TextCtrl e quando clicca il pulsante, se la TextCtrl
non è vuota, aggiunge la parola alla ListBox e pulisce la TextCtrl.



**Esercizio 015 (ListBox, Button)**

Inserite nella App una ListBox vuota e un pulsante. Quando l'utente clicca il pulsante, il programma carica dal file *dati.txt* presente nella stessa cartella
(dovete crearlo voi, con una parola ogni riga: ogni riga del file diventerà una voce nella ListBox). 



**Esercizio 016 (App, Slider, StaticText)**

Inserite nella App uno Slider che va da 1 a 10 e aggiungete una StaticText che visualizza il suo valore aggiornato in tempo reale.



**Esercizio 017 (App, TextCtrl, Button, Slider)**

Inserite nella App due coppie TextCtrl/Button. La prima coppia decide il valore minimo dello Slider, la seconda coppia il valore massimo. I pulsanti aggiornano
lo stato dello Slider.



**Esercizio 018 (App, Slider, Button)**

Inserite nella App due Slider, uno che va da 200 a 800 per la larghezza e uno che va da 100 a 500 per l'altezza. L'utente muove gli slider a piacimento e quando
clicca il pulsante si modifica la dimensione della finestra.

