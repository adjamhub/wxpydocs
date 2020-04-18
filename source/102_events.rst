=====================
Gestione degli Eventi
=====================


.. code:: python

    import wx

    class Esempio(wx.Frame):
        
        def __init__(self):
            super().__init__(None, title="Cliccami")
            self.pulsante = wx.Button(self, label="Chiudi tutto")
            self.pulsante.Bind(wx.EVT_BUTTON, self.chiudi)
            
        def chiudi(self, e):
            self.Close(True)

    # ----------------------------------------

    app = wx.App()

    window = Esempio()
    window.Show()

    app.MainLoop()


