============================
Primi Concetti, primi Esempi
============================


wxPython è un toolkit Python cross-platform per la creazione di applicazioni con GUI e che espone una lunga lista di widgets per i compiti più disparati.
Le sue classi sono organizzate in moduli che pian piano andremo a studiare: per adesso ci basterà sapere che le classi principali sono disponibili nel modulo
**wx**, lo stesso che abbiamo importato nell'esempio *Hello, World!*.

Capisco che arrivato a questo punto, prima di andare avanti, è necessario che io faccia una pausa e spieghi una serie di termini che ho utilizzato qua e là e che probabilmente ancora non conoscete.

*toolkit*
    Letteralmente "cassetta degli attrezzi", rappresenta l'insieme di strumenti necessari per eseguire un compito. Il compito del toolkit wxPython è la creazione
    di applicazioni grafiche, gli strumenti che utilizza sono classi Python.

*GUI*
    Acronimo di *Graphical User Interface*, indica la capacità di alcune applicazioni di interagire con gli utenti tramite la modalità WIMP (e adesso spiego WIMP...)
    
*WIMP*
    Acronimo di *Windows Icon Mouse Pointer*. Rappresenta una modalità tramite la quale interagire con il sistema operativo e le applicazioni, alternativa a quella
    testuale, tipica delle linee di comando.
    
*cross-platform*
    Rappresenta la capacità di alcuni software di essere utilizzati su vari sistemi operativi. Per quanto riguarda wxPython essa è disponibile su tutti i sistemi
    operativi desktop, in particolare è sicuramente disponibile su Windows, Mac OS e Linux.
    
*Widget*
    Si tratta di un generico oggetto grafico. Nel contesto wxPython si tratta di una classe wxPython che implementa un oggetto grafico, ad esempio la classe che 
    implementa un pulsante (e quindi il pulsante), la classe che implementa una finestra, una checkbox, etc...
    

Benissimo! Detto questo passiamo a reimplementare l'unico esempio che abbiamo finora visto e ragioniamoci un pò sù


Esempio 0: ancora "Hello, World!"
=================================

Riguardiamo per un attimo il solito esempio iniziale alla luce delle nuove cose che abbiamo imparato:

.. code:: python

    # si importa il modulo wx, che contiene le classi wxPython principali
    import wx

    # si crea un oggetto Applicazione.
    # Ce ne sarà sempre uno (e solo uno) in ogni applicazione.
    # Gestisce l'interazione con l'esterno (l'utente e il sistema operativo)
    app = wx.App()

    # si crea una widget, un oggetto grafico. 
    # Una finestra non collegata a nessun altra con titolo "Hello, World!"
    # Gi oggetti Top Level vengono creati nascosti e quindi devono essere mostrati
    window = wx.Frame(None, title="Hello, World!")
    window.Show()

    # si avvia il "Main Event Loop"
    # sotto spiego cosa è
    app.MainLoop()
    

.. note::
    Il **Main Event Loop** o *ciclo principale degli eventi* è uno stato di grazia in cui si pone ogni applicazione grafica dopo aver disegnato le proprie widgets. 
    
    In questo particolare stato di colloquio perenne tra il sistema operativo, l'utente e l'applicazione stessa, quest'ultima diventa in grado di intercettare gli eventi che accadono nel sistema (un click su un pulsante, un movimento del mouse, la carta della stampante che finisce, la rete che si sconnette, etc...) e di rispondere (eventualmente) eseguendo una funzione tra quelle disponibili fra gli oggetti che la compongono.


Esempio 1: "Hello, World!" per l'ultima volta
=============================================

In questa ultima versione di "Hello, World!" invece di inserire la scritta sul titolo della finestra la inseriremo in una etichetta al centro della stessa.
Inoltre produrremo una nuova classe che deriva da wx.Frame per inserirvi l'etichetta.


.. code:: python

    import wx

    # classe che deriva da wx.Frame
    class LaMiaPrimaFinestra(wx.Frame):
        
        def __init__(self):
            super().__init__(None, title="La mia prima finestra")
            self.etichetta = wx.StaticText(self, label="Hello, World!")
    
    # spero sia chiaro ormai
    app = wx.App()
    windows = LaMiaPrimaFinestra()
    windows.Show(True)
    app.MainLoop()


In questo modo impareremo a strutturare ogni finestra in una classe e se necessario a strutturare i nostri progetti dividendo ogni classe in un file diverso, in
modo da favorire al massimo l'organizzazione fortemente orientata agli oggetti e tutti le buone cose che ne derivano (organizzazione del codice, chiara divisione dei compiti fra le classi, semplicità nel riutilizzare il codice, etc..)

Adesso avanti! Il prossimo step è quello di interagire un pò con l'applicazione! Inserire un pulsante e fargli fare qualcosa!
    
