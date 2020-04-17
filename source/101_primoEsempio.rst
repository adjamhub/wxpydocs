============================
Primi Concetti, primi Esempi
============================


wxPython è un toolkit Python cross-platform per la creazione di interfacce grafiche che si basa su 5 moduli:

#. **Windows**: le widgets che saranno finestre delle applicazioni basate su wxPython.

#. **GDI (Graphic Device Interface)**: Un insieme di classi per disegnare oggetti.

#. **Core**: classi elementari da cui derivano tutte le altre (per sfruttare al meglio l'ereditarietà)

#. **Misc**: classi miste di utilità.

#. **Controls**: fornisce le widgets più comuni. Pulsanti, radiobutton, Toolbars...


Capisco che arrivato a questo punto, prima di andare avanti, è necessario che io faccia una pausa e spieghi una serie di termini che ho utilizzato qua e là e che probabilmente ancora non conoscete.

*toolkit*
    Letteralmente "cassetta degli attrezzi", rappresenta l'insieme di strumenti necessari per eseguire un compito. Il compito del toolkit wxPython è la creazione
    di applicazioni grafiche, gli strumenti che utilizza sono classi Python.
    
*cross-platform*
    Rappresenta la capacità di alcuni software di essere utilizzati su vari sistemi operativi. Per quanto riguarda wxPython essa è disponibile su tutti i sistemi
    operativi desktop, in particolare sicuramente disponibile su Windows, Mac OS e Linux.
    
*Widget*
    Si tratta di un generico oggetto grafico. Nel contesto wxPython si tratta di una classe wxPython che implementa un oggetto grafico, ad esempio un pulsante, una 
    finestra, una checkbox, etc...
    

Oggetti wx disponibili
======================

Gli oggetti disponibili nella libreria wxPython sono numerosi e catalogati a seconda del loro utilizzo. Almeno all'inizio devo elencarvi i più importanti, introducendo i gruppi ove si trovano per permettere una prima categorizzazione:

Base Widgets
    Widget da cui derivano le altre, solitamente poco usate in maniera diretta
    
    * wx.Window
    * wx.Control
    * wx.ControlWithItem 

Top level Widgets
    Finestre e widgets di riferimento per un gruppo di widgets

    * wx.Frame
    * wx.MDIParentFrame
    * wx.MDIChildFrame
    * wx.Dialog
    * wx.PopupWindow 

Containers
    Widgets contenitrici per organizzare il layout della finestra

    * wx.Panel
    * wx.Notebook
    * wx.ScrolledWindow
    * wx.SplitterWindow 

Dynamic Widgets
    Widgets con cui l'utente può interagire in maniera diretta (scrivendo, cliccando, etc...)

    * wx.Button
    * wx.BitmapButton
    * wx.Choice
    * wx.ComboBox
    * wx.CheckBox
    * wx.Grid
    * wx.ListBox
    * wx.RadioBox
    * wx.RadioButton
    * wx.ScrollBar
    * wx.SpinButton
    * wx.SpinCtrl
    * wx.Slider
    * wx.TextCtrl
    * wx.ToggleButton 
    
Static Widgets
    Widgets per la visualizzazione delle informazioni

    * wx.Gauge
    * wx.StaticText
    * wx.StaticBitmap
    * wx.StaticLine
    * wx.StaticBox 

Other Widgets
    Widgets che non appartengono ai gruppi precedenti

    * wx.MenuBar
    * wx.ToolBar
    * wx.StatusBar


Esempio 0: ancora "Hello, World!"
=================================

Riguardiamo per un attimo il solito esempio iniziale alla luce delle nuove cose che abbiamo imparato:

.. code:: python

    # si importa il modulo wx, che contiene tutte le classi wxPython 
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
    

.. tip::
    Il **Main Event Loop** o *ciclo principale degli eventi* è uno stato di grazia in cui si pone ogni applicazione grafica dopo aver disegnato le proprie widgets. 
    
    In questo particolare stato di colloquio perenne tra il sistema operativo, l'utente e l'applicazione stessa, quest'ultima diventa in grado di intercettare gli eventi che accadono nel sistema (un click su un pulsante, un movimento del mouse, la carta della stampante che finisce, la rete che si sconnette, etc...) e di rispondere (eventualmente) eseguendo una funzione tra quelle disponibili fra gli oggetti che la compongono.


Esempio 1: "Hello, World!" per l'ultima volta
=============================================

In questa ultima versione di "Hello, World!" invece di inserire la scritta sul titolo della finestra la inseriremo in una etichetta al centro della stessa.
Inoltre produrremo una nuova classe che deriva da wx.Frame per inserirvi l'etichetta.


.. code:: python

    import wx

    # creazione classe derivata da wx.Frame
    class LaMiaPrimaFinestra(wx.Frame):
        
        def __init__(self):
            wx.Frame.__init__(self, None, title="La mia prima finestra")
            self.control = wx.StaticText(self, label="Hello, World!")
            self.Show(True)
    
    # non dovrebbe essere difficilissimo, ormai..
    app = wx.App()
    windows = LaMiaPrimaFinestra()
    app.MainLoop()


In questo modo impareremo a strutturare ogni finestra in una classe e se necessario a strutturare i nostri progetti dividendo ogni classe in un file diverso, in
modo da favorire al massimo l'organizzazione fortemente orientata agli oggetti e tutti le buone cose che ne derivano (organizzazione del codice, chiara divisione dei compiti fra le classi, semplicità nel riutilizzare il codice, etc..)

Adesso avanti! Il prossimo step è quello di interagire un pò con l'applicazione! Inserire un pulsante e fargli fare qualcosa!
    
