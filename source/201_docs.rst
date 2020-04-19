
.. |br| raw:: html

    <br>

==============
Documentazione
==============

La documentazione ufficiale della libreria **wxPython** è disponibile online (in versione integrale) all'indirizzo https://docs.wxpython.org/.

In questo capitolo troverete riferimenti organizzati alla stessa a partire dalle classi che durante il corso abbiamo studiato. Se avete già installato wxPython
potete scaricare una copia locale della documentazione intera senza faticare semplicemente eseguendo il software **wxdocs**. Questo aprirà sul vostro browser di 
default la copia locale della documentazione, scaricandola prima se non la trova disponibile.

In maniera analoga, se volete vedere esempi di codice e vedere il risultato di quello che riescono a produrre potete eseguire lo script chiamato **wxdemo**.
Lo screenshot sotto è relativo ad esso.

.. image:: images/wxdemo.jpg

Cliccate su uno dei gruppi che vi interessano, date un occhio al codice e assolutamente eseguitelo per vederne il risultato!




Modulo wx
=========

Il modulo wx rappresenta il modulo principale della libreria wxPython e quello che contiene le classi sicuramente necessarie per implementare una GUI.
L'elenco completo delle classi presenti nel modulo si trova al link: https://docs.wxpython.org/wx.1moduleindex.html. |br|
Sotto trovate le classi che abbiamo utilizzato.


`wx.App <https://docs.wxpython.org/wx.App.html>`_
    Classe che gestisce le applicazioni con GUI implementate tramite wxPython.
    
`wx.Frame <https://docs.wxpython.org/wx.Frame.html>`_
    Classe che implementa una generica finestra vuota, ma perfettamente funzionante.

`wx.Button <https://docs.wxpython.org/wx.Button.html>`_
    Classe che implementa un pulsante cliccabile.

`wx.ToggleButton <https://docs.wxpython.org/wx.ToggleButton.html>`_
    Classe che implementa un pulsante con due stati: cliccato e non cliccato.
    
`wx.StaticText <https://docs.wxpython.org/wx.StaticText.html>`_
    Classe che implementa una etichetta dove il programmatore può inserire un testo da visualizzare all'utente.

`wx.StaticLine <https://docs.wxpython.org/wx.StaticLine.html>`_
    Classe che implementa una linea decorativa, orizzontale o verticale.
    
`wx.StaticBox <https://docs.wxpython.org/wx.StaticBox.html>`_
    Classe che implementa una decorazione per raggruppare le widget. Utile per organizzare il layout.
    
`wx.ComboBox <https://docs.wxpython.org/wx.ComboBox.html>`_
    Classe che implementa un menù a tendina
    
`wx.CheckBox <https://docs.wxpython.org/wx.CheckBox.html>`_
    Classe che implementa una casella di spunta.
    
`wx.RadioButton <https://docs.wxpython.org/wx.RadioButton.html>`_
    Classe che implementa un pulsante selezionabile in maniera mutualmente esclusiva.
    
`wx.Gauge <https://docs.wxpython.org/wx.Gauge.html>`_
    Classe che implementa una barra di avanzamento.
    
`wx.Slider <https://docs.wxpython.org/wx.Slider.html>`_
    Classe che implementa un cursore ad avanzamento lineare.

`wx.SpinCtrl <https://docs.wxpython.org/wx.SpinCtrl.html>`_
    Classe che implementa un selettore numerico con pulsanti di avanzamento.


Modulo wx.adv
=============

Il modulo wx.adv contiene classi più avanzate rispetto a quelle presenti nel modulo wx ma meno utilizzate e quindi relegate in un modulo alternativo
L'elenco completo delle classi presenti nel modulo si trova al link: https://docs.wxpython.org/wx.adv.1moduleindex.html. |br|
Sotto trovate le classi che abbiamo utilizzato.




Modulo wx.RichTextCtrl
======================

Il modulo wx.RichTextCtrl contiene l'implementazione di un controllo Rich Text utile per l'implementazione di un editor di testo con funzionalità avanzate.
L'elenco completo delle classi presenti nel modulo si trova al link: https://docs.wxpython.org/wx.richtext.1moduleindex.html. |br|
Sotto trovate le classi che abbiamo utilizzato.


`wx.richtext.RichTextCtrl <https://docs.wxpython.org/wx.richtext.RichTextCtrl.html>`_
    Classe che implementa una widget per implementare un editor di testo.
    
