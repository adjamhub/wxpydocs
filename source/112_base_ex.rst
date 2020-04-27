================
Esercizi di base
================


In questa prima sequenza di esempi ed esercizi prenderemo confidenza con le widgets più semplici, senza preoccuparci più di tanto del layout, ma solo cercando
di seguire bene le regole della OOP, stare attenti a utilizzare correttamente la libreria wxPython e di prendere confidenza con la documentazione, che bisognerà forzatamente consultare per alcuni degli esercizi proposti.

Iniziamo!

.. i numeri degli esercizi sono 1xx

**Esercizio 101 (ToggleButton)**

Creare una applicazione con una finestra con titolo *Ciccio* che contiene un pulsante \"Toggle\". Quando clicchi il pulsante, il titolo
diventa *Pippo*, quando lo clicchi di nuovo ritorna ad essere *Ciccio* e così via.



**Esercizio 102 (Button, StaticText, TextCtrl)**

Creare una applicazione con una finestra che contiene una StaticText, inizialmente vuota, una TextCtrl e un pulsante. Quando l'utente
clicca sul pulsante, il testo contenuto nella TextCtrl viene copiato nella StaticText e la TextCtrl ripulita.



**Esercizio 103 (Button)**

Creare una applicazione con un pulsante *CHIUDI*. Quando lo clicchi, l'applicazione si chiude.



**Esercizio 104 (RadioButton, StaticText)**

Implementare un testo con domanda: *Dimmi come vieni a scuola* e un elenco di opzioni a vostra scelta, tra cui ad esempio auto, moto, bici, bus, etc..
Sotto a questo, un'altra StaticText, che alla selezione di un mezzo di trasporto selezionerà la scritta: *vieni a scuola in MEZZODITRASPORTO*.



**Esercizio 105 (TextCtrl, RadioButton, Button, StaticText)**

Applicazione con una TextCtrl per inserire il nome e un RadioButton per selezionare il sesso (opzioni *Maschio*, *Femmina*) più un pulsante e una StaticText.
Al click sul pulsante va visualizzata nella StaticText la scritta *Buongiorno signor NOME* oppure *Buongiorno signora NOME* a seconda del sesso selezionato.

Come ulteriore difficoltà si può aggiungere il controllo dell'ora: se il pulsante viene cliccato fra le 6 e le 14, si utilizza *Buongiorno*, fra le 14 e le 22
si scrive *Buonasera*, fra le 22 e le 6 si scrive *Buonanotte*.



**Esercizio 106 (TextCtrl, RadioButton, Button)**

Applicazione con una TextCtrl e un pulsante. L'utente scrive una serie di parole separate da virgola nella TextCtrl e quando preme il pulsante appare
un RadioButton con le opzioni indicate nella TextCtrl e separate da virgole.



**Esercizio 107 (StaticText, CheckBox)**

Serie di 5 CheckBox con una selezione di cibi (es: pasta, pizza, etc...). Man mano che l'utente seleziona cibi la StaticText sotto alle CheckBox si aggiorna
mostrando tutti i cibi selezionati.



**Esercizio 108 (StaticText, CheckBox)**

Identico all'esercizio precedente, ma la StaticText non visualizza il testo delle CheckBox selezionate ma il numero di queste. Ad esempio all'inizio
vi sarà scritto "0 CheckBox selezionate" e il numero crescerà o diminuirà a seconda che vengono attivate o no le CheckBox.



**Esercizio 109 (Button, CheckBox)**

la finestra contiene 3 pulsanti: il primo massimizza la finestra, il secondo la iconizza sulla barra delle applicazioni, il terzo la chiude.
Sotto i pulsanti ci sono 3 CheckBox che corrispondono ognuna ad un pulsante: se la CheckBox è spuntata, il pulsante corrispondente è abilitato,
altrimenti è disabilitato. Fate attenzione a sincronizzare la spunta sulla CheckBox con l'abilitazione del pulsante corrispondente e viceversa.



**Esercizio 110 (TextCtrl, Button, ComboBox)**

La finestra presenta una TextCtrl, un pulsante e una ComboBox, inizialmente con un'unica opzione (un testo a piacere). L'utente inserisce una stringa nella TextCtrl
e se non è vuota, quando clicca il pulsante quella stringa viene aggiunta come opzione alla ComboBox e la TextCtrl ripulita.



**Esercizio 111 (Frame, ComboBox)**

la finestra presenta una ComboBox con opzioni '600x400', '800x600', 'massimizza'. Quando l'utente seleziona una delle opzioni la finestra si ridimensiona secondo quanto indicato.



**Esercizio 112 (Frame, ComboBox, CheckBox)**

Dichiarate una tupla di valori qualsiasi e con essa create sia una ComboBox che elenca tutti gli elementi della tupla, sia una serie di CheckBox, una per ogni valore
della tupla. Quando l'utente seleziona uno dei valori della ComboBox, la CheckBox corrispondente cambia stato, venendo spuntata oppure no a seconda del suo stato
precedente.

PS: se non avete pensato ad usare un dizionario... beh... ricominciate a pensare!



**Esercizio 113 (SpinCtrl, Button, StaticText)**

Inserite nella finestra una SpinCtrl per inserire un intero fra 1 e 10. Quando si clicca il pulsante nella StaticText sotto appare il countdown dal numero selezionato
fino a zero.

PS: Se avete capito come funziona la classe *wx.Timer* potete fare in modo che i numeri appaiano uno ogni secondo!!!



**Esercizio 114 (ComboBox, TextCtrl, Button)**

Inserite nella finestra una ComboBox inizialmente vuota, una TextCtrl e un Button. L'utente digita qualcosa nella TextCtrl e quando clicca il pulsante, se la TextCtrl
non è vuota, aggiunge la parola alla ComboBox e pulisce la TextCtrl.



**Esercizio 115 (TextCtrl, Button)**

Inserite nella Finestra una TextCtrl vuota e un pulsante. Quando l'utente clicca il pulsante, il programma carica dal file *dati.txt* presente nella stessa cartella
il contenuto e lo visualizza nella TextCtrl. 



**Esercizio 116 (Slider, StaticText)**

Inserite nella finestra uno Slider che va da 1 a 10 e aggiungete una StaticText che visualizza il suo valore aggiornato in tempo reale.



**Esercizio 117 (TextCtrl, Button, Slider)**

Inserite nella finestra due coppie TextCtrl/Button. La prima coppia decide il valore minimo dello Slider, la seconda coppia il valore massimo. I pulsanti aggiornano
lo stato dello Slider.



**Esercizio 118 (Slider, Button)**

Inserite nella finestra due Slider, uno orizzontale che va da 200 a 800 per la larghezza e uno verticale che va da 100 a 500 per l'altezza. 
L'utente muove gli slider a piacimento e quando clicca il pulsante si modifica la dimensione della finestra.



**Esercizio 119 (ListBox, Button, StaticText)**

Inserite nella finestra una ListBox con una sequenza di voci e la possibilità di selezionarne contemporaneamente più di una. Quando l'utente clicca il pulsante
nella StaticText vengono visualizzate tutte le voci selezionate, separate da virgola.


**Esercizio 120 (ListBox, TextCtrl, Button)**

Inserite nella finestra una ListBox inizialmente vuota, una TextCtrl e un pulsante. L'utente digita qualcosa nella TextCtrl e quando clicca il pulsante, 
se la TextCtrl non è vuota, aggiunge la parola alla ListBox e pulisce la TextCtrl.


**Esercizio 121 (ListBox, PushButton)**

Inserite nella finestra una ListBox vuota e un pulsante. Quando l'utente clicca il pulsante, il programma carica dal file *dati.txt* presente nella stessa cartella
(dovete crearlo voi, con una parola ogni riga: ogni riga del file diventerà una voce nella ListBox). 

