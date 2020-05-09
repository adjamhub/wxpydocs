=======
Dialogs
=======

.. i numeri degli esercizi sono 3xx

Le finestre di dialogo sono strumenti indispensabili della programmazione con GUI attuale. Esse permettono una comunicazione bidirezionale fra
l'applicazione e l'utente con la prima che tramite esse mostra all'ultimo informazioni ritenute importanti o richiede scelte senza le quali non si può 
procedere oltre.

.. tip::
    La caratteristica delle finestre che le porta ad essere considerate finestre di dialogo è quella di essere finestre **modali**, ovvero finestre che si
    sovrappongono alle finestre principali e non possono in alcun modo essere ignorate.
    
    Questa condizione si ottiene utilizzando in una finestra la funzione **ShowModal()** al posto della classica funzione **Show()**.
    
    
Esempi banali di finestre di dialogo sono la finestra di errore, la finestra di selezione file, quella per selezionare i font oppure i colori. Vediamole una per una,
con un piccolo esempio per comprenderne al meglio il funzionamento.


Message Dialogs
===============

Sevono per inviare un messaggio esclamativo, di avvertimento, di richiesta o di errore. Tramite la selezione di pulsanti sotto, si può ottenere un feedback
dall'utente per assicurarsi abbia recepito il messaggio.


.. code:: python

    MessageDialog( parent , message , caption=TITOLO , style=STILE )


Lo stile può contenere alcuni fra i seguenti valori, sovrapponibili con la tecnica del `pipe |`, come per i flag dei Sizer.

=================== ======================================
Stile               Descrizione
=================== ======================================
wx.OK               Mostra il pulsante OK
wx.CANCEL           Mostra il pulsante CANCEL
wx.YES_NO           Mostra i pulsanti Sì e No
wx.HELP             Mostra il pulsante AIUTO
wx.ICON_EXCLAMATION	Mostra un icona di allerta
wx.ICON_ERROR	    Mostra una icona di errore
wx.ICON_HAND	    Come wx.ICON_ERROR
wx.ICON_INFORMATION	Mostra una icona informativa
wx.ICON_QUESTION	Mostra una icona a un punto di domanda
=================== ======================================


Vediamo qualche esempio semplice semplice:


.. code:: python

    #  Messaggio informativo
    dial = wx.MessageDialog(None, "Ora della merenda", "Info", wx.OK)
    dial.ShowModal()

    # Messaggio di errore
    dial = wx.MessageDialog(None, "Biscotti non disponibili", "Errore", wx.OK | wx.ICON_ERROR)
    dial.ShowModal()

    # Messaggio di domanda
    dial = wx.MessageDialog(None, "Ti andrebbe un mandarino?", "Domanda", wx.YES_NO | wx.ICON_QUESTION)
    dial.ShowModal()

    # Messaggio di avvertimento
    dial = wx.MessageDialog(None, "Troppa nutella all'orizzonte", "Esclamazione", wx.OK | wx.ICON_EXCLAMATION)
    dial.ShowModal()
        

Ovviamente va individuato il giusto momento per visualizzare una MessageDialog: abusare di finestre modali è considerato fastidioso e maleducato.


**Esercizio 301**

Visualizzate una finestra con un pulsante che quando premuto visualizza un messaggio informativo a vostro piacere.


.. line::


**Esercizio 302**

Visualizzate una finestra vuota. Quando si clicca per chiuderla appare il messaggio di domanda \"Sicuro di voler chiudere?\". Se l'utente risponde No, la 
finestra non si chiude.


.. line::


**Esercizio 303**

Visualizzare una finestra con una SpinCtrl con valori da -10 a +10. Se l'utente seleziona 0, appare un messaggio di avvertimento.



Dir Dialogs
===========

Servono per selezionare una cartella (presente o no) nel proprio computer. 

.. code:: python

    # seleziona una dir e poi visualizza la scelta
    dlg = DirDialog(None, 'Seleziona la cartella delle immagini')
    if dlg.ShowModal() == wx.ID_CANCEL:
        return
    
    #... il percorso scelto si ottiene con dlg.GetPath()



**Esercizio 311**

Visualizzare una finestra con un pulsante ed una etichetta di testo inizialmente vuota. Cliccando il pulsante si apre la DirDialog che permette di selezionare
la cartella. Se l'utente preme OK nella etichetta di testo si visualizzi il percorso selezionato.


.. line::


**Esercizio 312**

Visualizzare una finestra con un pulsante. Cliccando il pulsante si apre una DirDialog con la possibilità di selezionare cartelle non esistenti. Se l'utente ne 
seleziona una non esistente, il programma la crea (Sugg: ricordate il modulo Pathlib???)



    
File Dialogs
============

Analogamente alle DirDialog, servono per selezionare un file (esistente o no) nel proprio computer.


.. code:: python

    # ESEMPIO 1: SELEZIONA FILE DA APRIRE
    dlg = FileDialog(None, "Apri File", style=FD_OPEN)
    if dlg.ShowModal() == wx.ID_CANCEL:
        return
        
    #... il percorso scelto si ottiene con dlg.GetPath()
    #...
    
    # ESEMPIO 2: SELEZIONA PERCORSO FILE SU CUI SALVARE
    dlg = FileDialog(None, "Salva File", style=FD_SAVE)
    if dlg.ShowModal() == wx.ID_CANCEL:
        return
    
    #... il percorso scelto si ottiene con dlg.GetPath()

    
    
**Esercizio 321**

Visualizzare una finestra con un pulsante ed una etichetta di testo inizialmente vuota. Cliccando il pulsante si apre la FileDialog che permette di selezionare
un file per l'apertura. Se l'utente preme OK nella etichetta di testo si visualizzi il percorso del file selezionato.


.. line::


**Esercizio 322**

Visualizzare una finestra con un pulsante. Cliccando il pulsante si apre una FileDialog in modalità salva. Se l'utente ne seleziona uno non esistente, 
il programma lo crea vuoto (Sugg: ricordate il modulo Pathlib???)


.. line::


**Esercizio 323**

Visualizzare una finestra con un pulsante ed una etichetta di testo inizialmente vuota. Cliccando il pulsante si apre una FileDialog in modalità apri. 
Se l'utente seleziona un file di testo e preme OK, il contenuto del file viene visualizzato nell'etichetta.



Colour Dialogs
==============

Le finestre di dialogo per la selezione dei colori si utilizzano tramite la loro classe ausiliaria `wx.ColourData`
che mantiene le informazioni iniziali necessarie per la selezione dei colori e (dopo l'esecuzione della dialog) il colore selezionato dall'utente.

.. code:: python

    # ...
    datiIniziali = wx.ColourData()
    dialog = wx.ColourDialog(self, datiIniziali)
    if dialog.ShowModal() == wx.ID_OK:
        datiFinali = dialog.GetColourData()
        coloreSelezionato = datiFinali.GetColour()
        # ...

        

**Esercizio 331**

Visualizzare una finestra con un pulsante ed una etichetta di testo inizialmente vuota. Cliccando il pulsante si apre una ColourDialog che permette
di selezionare un colore. Visualizzarlo come stringa nella etichetta.


.. line::


**Esercizio 332**

Visualizzare una finestra con un pulsante ed una etichetta di testo inizialmente vuota. Cliccando il pulsante si apre una ColourDialog che permette
di selezionare un colore. Colorare lo sfondo dell'etichetta del colore selezionato.


.. line::


**Esercizio 333**

Visualizzare una finestra con un pulsante ed una etichetta di testo con la scritta "Colore selezionato". Cliccando il pulsante si apre una ColourDialog che permette
di selezionare un colore. Colorare il testo dell'etichetta con il colore selezionato.



Font Dialogs
============

Le finestre di dialogo per la selezione dei font si utilizzano tramite la loro classe ausiliaria `wx.FontData`
che mantiene le informazioni iniziali necessarie per la selezione dei font e (dopo l'esecuzione della dialog) il colore selezionato dall'utente.
(Questa frase mi sembra di averla già sentita...)

.. code:: python

    # ...
    datiIniziali = wx.FontData()
    dialog = wx.FontDialog(self, datiIniziali)
    if dialog.ShowModal() == wx.ID_OK:
        datiFinali = dialog.GetFontData()
        fontSelezionato = datiFinali.GetFont()
        # ...


        
**Esercizio 341**

Visualizzare una finestra con un pulsante ed una etichetta di testo inizialmente vuota. Cliccando il pulsante si apre una FontDialog che permette
di selezionare un font. Visualizzarlo come stringa nella etichetta.


.. line::


**Esercizio 342**

Visualizzare una finestra con un pulsante ed una etichetta di testo con la scritta "Font selezionato". Cliccando il pulsante si apre una FontDialog che permette
di selezionare un font. Utilizzarlo come font dell'etichetta.



.. tip::

    Se volete una presentazione generica di tutte le finestre di dialogo comuni presenti nella libreria `wxPython` ecco il
    link che fa per voi: https://docs.wxpython.org/common_dialogs_overview.html.
    
    
