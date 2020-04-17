============
Installation
============

La libreria wxPython è una libreria OOP Python in tutto e per tutto. La trovate
come tantissime altre sul **Python Package Index** e per installarla, se sapete
quello che state facendo, basta un semplicissimo:

.. code:: bash
    
    $ pip3 install wxpython


Se invece volete la messa lunga, allora sappiate che dovete per prima cosa aprire `Thonny <https://thonny.org>`_ e accedere al suo gestore dei pacchetti:

.. image:: images/wxpython_install_0.jpg

Da lì digitate la stringa **wxpython** e cliccate su *Trova una pacchetto PyPi* (Ma chi ha fatto la traduzione di Thonny???)

.. image:: images/wxpython_install_1.jpg

A questo punto vi basta semplicemente cliccare **INSTALLA** e aspettare :)

.. image:: images/wxpython_install_2.jpg


Quando il download e l'installazione sono finiti è possibile provare direttamente l'Hello World Program della prima pagina. Lo riscrivo qui per comodità:


.. code:: python

    import wx
    
    app = wx.App()

    window = wx.Frame(None, title="Hello, World!")
    window.Show()

    app.MainLoop()

    
Ecco qua! Siete ufficialmente pronti per studiare la libreria **wxPython**!

