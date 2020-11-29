======================
widget inspection tool
======================

La libreria wxPython fornisce uno strumento molto interessante per l'analisi delle widget in fase di creazione: lo **Widget Inspection Tool**. Questo strumento può essere utilizzato per analizzare il layout definito in una widget e le funzionalità grafiche implementate in essa (eventi, main loop, etc...).

Per utilizzarlo è necessario aggiungere semplicemente 2 righe di codice al main di una applicazione e rieseguire il suo codice:

.. code:: python

    import wx.lib.inspection
    wx.lib.inspection.InspectionTool.Show()
    

Come vedete non è nulla di complicato. Cerchiamo però di capire quale può essere l'utilità di utilizzare uno strumento del genere, come al solito partendo
da un esempio.

Questo stupido esempio qui sotto non funziona bene. Perché? Il Widget Inspection Tool potrebbe aiutarci a capirlo...

.. code:: python

    
