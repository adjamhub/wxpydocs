=====================
Gestione degli eventi
=====================


Una volta iniziato il Main Event Loop le applicazioni wxPython sono in grado di intercettare gli eventi utente, come ad esempio un click su un pulsante o sulla
tastiera o un movimento del mouse. Tutte questi eventi sono catalogati negli oggetti, ovvero ogni widget sa quali eventi intercettare: ad esempio un pulsante
saprà intercettare un click su di esso, una linea di testo sarà in grado di capire quando ci scrivi dentro, etc...

Deciso l'evento a cui rispondere (click su pulsante) è possibile abbinare a questo una funzione, in modo che quando l'evento accade, la funzione viene eseguita!

Per farlo dobbiamo utilizzare la funzione **Bind**:

.. code:: python

    widget.Bind ( EVENTO, FUNZIONE )
    

Vediamo un esempio di codice di una Finestra con un grosso pulsante dentro: al click sul pulsante viene eseguita una funzione e... provate a copiare il codice 
e ad eseguirlo per vedere cosa succede!

.. code:: python

    import wx

    class Esempio(wx.Frame):
        
        def __init__(self):
            super().__init__(None, title="Cliccami")
            self.pulsante = wx.Button(self, label="Chiudi tutto")
            self.pulsante.Bind(wx.EVT_BUTTON, self.chiudi)
            
        def chiudi(self, event):
            self.Close(True)

    # ----------------------------------------
    app = wx.App()

    window = Esempio()
    window.Show()

    app.MainLoop()


Ok... con questo esempio abbiamo capito che un pulsante, ovvero la widget **wx.Button** intercetta il click con l'evento **wx.EVT_BUTTON**. Vediamo un altro esempio
con una finestra che intercetta i suoi spostamenti e tramite una funzione scrive le coordinate della sua posizione.


.. code:: python

    import wx

    class Esempio(wx.Frame):
        
        def __init__(self):
            super().__init__(None, title="Muovimi")
            self.etichetta = wx.StaticText(self, label="x: 0\ny: 0")
            self.Bind(wx.EVT_MOVE, self.aggiornaPosizione)
            
        def aggiornaPosizione(self, event):
            # pos è una tupla (x,y) della posizione
            pos = event.GetPosition()
            info = "x: " + str(pos[0]) + "\ny: " + str(pos[1])
            self.etichetta.SetLabel(info)

    # ----------------------------------------
    app = wx.App()

    window = Esempio()
    window.Show()

    app.MainLoop()


Anche qui vi propongo di copiare il codice e testarlo prima di andare avanti... L'oggetto in questione stavolta è la finestra principale, la widget **wx.Frame**,
l'evento da intercettare si chiama **wx.EVT_MOVE**, la funzione da eseguire in risposta ad esso è implementata sotto e si chiama *aggiornaPosizione*.

Cerchiamo adesso di mettere in evidenza alcune cose che avete intuito osservando questi esempi:

#. Le funzioni che rispondono agli eventi hanno tutte la struttura **funzione (self, event)**.
   Questo per fare in modo che la funzione possa trarre informazioni dall'evento occorso, come nel caso
   della funzione *aggiornaPosizione* che tramite esso acquisisce la nuova posizione della finestra.
   
#. Come la widget pulsante, che si chiama wxButton ha un evento predefinito (il click su di esso) che si chiama wx.EVT_BUTTON, quasi tutte le widget
   che vedremo hanno l'evento predefinito che si chiama come loro stesse. Quindi ad esempio la ipotetica widget *wx.Banana* ha un evento predefinito
   (ad esempio qualcuno che inizia a sbucciarla) che si chiama wx.EVT_BANANA.
   
#. Come si fa a sapere quali altri eventi può gestire una widget? Beh... bisogna leggere la documentazione. Nella sezione apposita ci sono i link diretti
   a tutte le classi che studieremo e scorrendola troverete la sezione che elenca gli eventi a cui ognuna di esse può reagire
   e che possono essere collegati tramite **binding** (ovvero con la funzione Bind)

   
Vediamo altre due cose importantissime sugli eventi prima di passare in rassegna tutte le widget disponibili.



Identificare le widgets
=======================

Immaginate una applicazione con tanti pulsanti (una tastiera virtuale, una calcolatrice, etc...). Capita spesso in questi casi di collegare più oggetti
alla stessa funzione. Ma come si può distinguere quale pulsante (o più in generale quale widget) ha scatenato l'evento. Provo con un esempio:


.. code:: python

  import wx

  class Esempio(wx.Frame):
      
      def __init__(self):
          super().__init__(None, title="2 pulsanti, 1 funzione")
          self.pulsante1 = wx.Button(self, label="pulsante1", pos=(5,5), size=(100,30))
          self.pulsante2 = wx.Button(self, label="pulsante2", pos=(120,5), size=(100,30))
          self.pulsante1.Bind(wx.EVT_BUTTON, self.faiQualcosa)
          self.pulsante2.Bind(wx.EVT_BUTTON, self.faiQualcosa)
          
      def chiudi(self, event):
          # ok... chi mi ha cliccato?

  # ----------------------------------------
  app = wx.App()
  window = Esempio()
  window.Show()
  app.MainLoop()


Bene... la soluzione in questo e molti altri casi è quella di identificare le widgets con un **ID**. Questo significa praticamente assegnare ad ogni widget
un numero in modo da poterle distinguere tra di loro (se te li ricordi... ovviamente!).

La libreria wxPython fa già questo lavoro di default, ovvero assegna automaticamente ad ogni widget un numero **negativo**: la prima widget creata sarà quella
con ID -1, la seconda quella con ID -2 e così via... invece di contare all'impazzata, sappiate che è possibile assegnare manualmente un ID (magari solo alle widget per cui vi interessa farlo). 

La regola d'oro per i programmatori è quella di **usare per gli ID solo numeri positivi diversi fra loro**, magari partendo da 1, poi 2, etc... Questo ovviamente
per evitare a priori alcun conflitto con gli ID selezionati automaticamente dalla libreria wxPython. A questo punto sarà possibile identificare le widget 
e quello che fanno da ogni punto della tua applicazione!

Il codice nel nostro esempio specifico diventa il seguente:


.. code:: python

  import wx

  class Esempio(wx.Frame):
      
      def __init__(self):
          super().__init__(None, title="2 pulsanti, 1 funzione")
          
          # i due pulsanti sono identificati con ID 1 e 2
          self.pulsante1 = wx.Button(self, label="pulsante 1", pos=(5,5), size=(100,30), id=1)
          self.pulsante2 = wx.Button(self, label="pulsante 2", pos=(120,5), size=(100,30), id=2)
          self.pulsante1.Bind(wx.EVT_BUTTON, self.faiQualcosa)
          self.pulsante2.Bind(wx.EVT_BUTTON, self.faiQualcosa)
          
      def faiQualcosa(self, event):
          # la funzione GetId ci dice l'ID della widget che ha scatenato l'evento
          id = event.GetId()
          print("Hai cliccato il pulsante con ID =", id)
          return

  # ----------------------------------------
  app = wx.App()
  window = Esempio()
  window.Show()
  app.MainLoop()





Bloccare gli eventi
===================

Può essere utile sapere che in alcuni casi possiamo bloccare gli eventi e le naturali risposte delle applicazioni ad essi: il caso tipico in programmazione
per questa problematica è quando l'utente prova a chiudere un editor con il file non ancora salvato!  In quel caso l'applicazione blocca la chiusura suggerendo
di salvare prima il file! Nella libreria wxPython è possible bloccare un evento con la funzione **Veto()**, da applicare all'evento da bloccare.

Nell'esempio che segue la finestra che appare è chiudibile dall'utente (con scorciatoia, cliccando sulla x in alto, etc..) solo se massimizzata.


.. code:: python

    import wx

    class Esempio(wx.Frame):
        
        def __init__(self):
            super().__init__(None, title="Massimizza per chiudere")        
            self.Bind(wx.EVT_CLOSE, self.chiudi)
            
        def chiudi(self, event):
            if (self.IsMaximized()):
                self.Destroy()
            else:
                # blocca l'evento
                event.Veto()

    # ----------------------------------------
    app = wx.App()

    window = Esempio()
    window.Show()

    app.MainLoop()
    

Come al solito... copiate e provate!

.. note::
    In questo unico caso, in cui si intercetta l'evento **wx.EVT_CLOSE** è necessario chiudere la finestra utilizzando *Destroy()* invece di *Close(True)*.
    Infatti la funzione *Close()* genera un evento EVT_CLOSE che di solito chiama la funzione di chiusura predefinita. Se in questo caso usassimo Close(True)
    dentro la funzione chiudi() si genererebbe un nuovo evento wx.EVT_CLOSE, che richiamerebbe la funzioni chiudi(), che richiamerebbe la funzione Close()...
    dando vita ad un ciclo infinito.
    

Ok, definiti gli eventi più semplici e capito come collegarli alle widget, vediamo le widgets e i layout per creare delle applicazioni con un look consistente.
