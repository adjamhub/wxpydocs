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


Dir Dialogs
===========

Servono per selezionare una cartella (presente o no) nel proprio computer. 

.. code:: python

    # seleziona una dir e poi visualizza la scelta
    dlg = DirDialog(None, 'Seleziona la cartella delle immagini')
    if dlg.ShowModal() == wx.ID_CANCEL:
        return
    
    #... il percorso scelto si ottiene con dlg.GetPath()


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

    

Colour Dialogs
==============

Font Dialogs
============

