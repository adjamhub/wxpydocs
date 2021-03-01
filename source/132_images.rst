========
Immagini
========

.. i numeri degli esercizi sono 36x

Per imparare a gestire, visualizzare, modificare immagini con wxPython abbiamo bisogno di discutere alcune caratteristiche della libreria e 
di chiarire alcuni concetti relativi alla OOP.

Vedremo come sia possibile in maniera semplice individuare alcune modalità di lavoro con le immagini con wxPython a seconda che si voglia:

* Visualizzare una semplice immagine di un certo formato nella propria applicazione

* Visualizzare una icona da abbinare ad un pulsante o come presto vedremo ad una voce di menù o ad una barra degli strumenti

* Creare un software per elaborare le immagini, in maniera temporanea (solo durante la visualizzazione) o in maniera permanente, salvando quindi le modifiche fatte  all'immagine.


.. warning:: 
    Per elaborare le immagini e supportare il numero più alto possibile di formati per le immagini, la libreria wxPython si appoggia sulla libreria *Pillow* (Python Image Library). Questa dovrebbe essere stata installata durante l'installazione di wxPython. Se vi accorgete di qualche problema legato ad essa e pensate che
    per qualche motivo manchi nel vostro sistema, potete installarla con un bel:
    
    .. code:: bash
    
        $ pip3 install -U pillow
        

Cominciamo la nostra disamina sulle classi wxPython per la visualizzazione e la manipolazione delle immagini. Le prime classi che voglio introdurvi a proposito
sono quelle che permettono di gestire le immagini: badate bene, *NON* quelle con cui potrete visualizzarle sulla vostra applicazione, ma quelle tramite le quali
potrete gestire un **Oggetto Immagine** eventualmente manipolarlo (ad esempio, modificare la dimensione, il colore, il livello di trasparenza, etc..) e affidarlo
ad un oggetto per la visualizzazione all'interno della nostra applicazione!

Se avete un file immagine (ad esempio ne conoscete il percorso nel vostro sistema) potete gestirlo con la classe **wx.Bitmap**. Il suo costruttore più utilizzato è quello che segue:


.. code:: python

    wx.Bitmap(self, filepath, type=BITMAP_TYPE_ANY)

    
Quindi immaginiamo di avere una immagine nella stessa cartella dove è presente il nostro script Python, ad esempio il file \"foto.jpg\":


.. code:: python

    bmp = wx.Bitmap("foto.jpg")
    
Se vuoi semplicemente visualizzare l'immagine, per gestirla non ti serve altro! Ti manca solo una classe per posizionare l'immagine nella tua GUI: 
la classe **wx.StaticBitmap**


.. code:: python

    # ...
    panel = wx.Panel(self)
    bmp = wx.Bitmap("foto.jpg")
    viewer = wx.StaticBitmap(panel, bitmap=bmp) 
    # ...
    

Nel mio esempio l'ho fatta un pò semplice, ma la realtà non è molto diversa da così. Ovviamente questo codice funziona bene se già sapete all'inizio dove si
trova l'immagine e volete visualizzarla all'avvio. Se volete visualizzare un'immagine selezionata dall'utente dopo che il vostro programma è stato lanciato,
allora create la Bitmap quando sapete il percorso e lo abbinate alla StaticBitmap nel layout tramite la funzione `SetBitmap()`.


Se hai propositi bellicosi nei confronti della tua immagine (ovvero se pensi di modificarne dimensione, colore, trasparenza etc...), allora hai bisogno 
della classe **wx.Image**. In essa troverai tutte le funzionalità presenti in wxPython per la modifica delle immagini. 
Non ce la faccio a spiegare tutto in questo testo: per darvi un'idea delle funzionalità della classe wx.Image vi invito a curiosare sul tool **wxdemo** citato nell'ultima pagina della dispensa e a consultare la documentazione della classe `wx.Image <https://wxpython.org/Phoenix/docs/html/wx.Image.html>`_.

Per ottenere un oggetto della classe wx.Image basta partire da un oggetto wx.Bitmap ed estrarlo da questo, come nell'esempio con la solita immagine:


.. code:: python

    bmp = wx.Bitmap("foto.jpg")
    img = bmp.ConvertToImage()
    # img è un oggetto della classe wx.Image
    

Se fate delle modifiche all'oggetto wx.Image poi per visualizzare il risultato dovete ricreare una wx.Bitmap e riapplicarla (ad esempio) all'oggetto wx.StaticBitmap
per la visualizzazione. Nel pezzo di codice sotto modifico l'immagine impostandola a *Disabled* ovvero con i colori trasformati in scala di grigi e poi la riapplico
alla StaticBitmap:

.. code:: python

    # ...
    DisabledImg = img.ConvertToDisabled()
    newBmp = wx.Bitmap(DisabledImg)
    viewer.SetBitmap(newBmp)
    # ...


Spero sia chiaro. Adesso comunque arriva qualche esercizio ad aiutarvi :)


**Esercizio 361**

Crea una semplice interfaccia con un pannello e un StaticBitmap per visualizzare una immagine presente nella stessa cartella ove salverete il codice dell'esercizio.


.. line::


**Esercizio 362**

Crea una applicazione con 2 pulsanti allineati sopra e una StaticBitmap sotto. Con il primo pulsante si apre una finestra di selezione file per selezionare
una immagine che andrà mostrata nella StaticBitmap. Il secondo pulsante è un ToggleButton che abilita/disabilita l'immagine selezionata.


.. line::


Icone
=====

Se la necessità relativa alle immagini è quella di visualizzare le icone nei pulsanti (e nei menù e nelle barre degli strumenti, come impareremo fra breve) oltre
a caricare le immagini direttamente tramite le Bitmap, come abbiamo appena visto, c'è un'altra interessante soluzione: la classe **wx.ArtProvider**. Lungi da 
me tediarvi sull'idea dietro la realizzazione di una tale classe e come essa possa essere derivata per creare il proprio personale set di icone...
sappiate semplicemente quello che serve: per ogni icona abbinata ad una azione comune abbiamo un ID e tramite quello possiamo creare automaticamente una Bitmap.


.. code:: python

    # la variabile "bitmap" è un oggetto della classe wx.Bitmap
    bitmap = wx.ArtProvider.GetBitmap(wx.UN_ID_FRA_QUELLI_ELENCATI_SOTTO)
    

Vediamo l'elenco delle icone automaticamente supportate (in rigoroso ordine alfabetico):


=========================== ===========================
Descrizione                 Art Provider ID
=========================== ===========================
Aggiungi Bookmark           wx.ART_ADD_BOOKMARK
CDRom                       wx.ART_CDROM
Chiudi                      wx.ART_CLOSE
Copia                       wx.ART_COPY
Una grossa X                wx.ART_CROSS_MARK
Taglia                      wx.ART_CUT
Cancella Bookmark           wx.ART_DEL_BOOKMARK
Cancella                    wx.ART_DELETE
Errore                      wx.ART_ERROR
File eseguibile             wx.ART_EXECUTABLE_FILE
Apri (file)                 wx.ART_FILE_OPEN
Salva (file)                wx.ART_FILE_SAVE
Salva come                  wx.ART_FILE_SAVE_AS
Trova                       wx.ART_FIND
Trova e sostituisci         wx.ART_FIND_AND_REPLACE
Floppy                      wx.ART_FLOPPY
Cartella                    wx.ART_FOLDER
Apri Cartella               wx.ART_FOLDER_OPEN
Torna Indietro              wx.ART_GO_BACK
Vai alla cartella superiore wx.ART_GO_DIR_UP
Vai giù                     wx.ART_GO_DOWN
Vai avanti                  wx.ART_GO_FORWARD
Torna a casa (Lassie)       wx.ART_GO_HOME
Vai dal genitore            wx.ART_GO_TO_PARENT
Vai su                      wx.ART_GO_UP
Torna al primo              wx.ART_GOTO_FIRST
Vai all'ultimo              wx.ART_GOTO_LAST
Hard Disk                   wx.ART_HARDDISK
Aiuto                       wx.ART_HELP
Aiuto (libro)               wx.ART_HELP_BOOK
Aiuto (cartella)            wx.ART_HELP_FOLDER
Aiuto (pagina)              wx.ART_HELP_PAGE
Aiuto (impostazioni)        wx.ART_HELP_SETTINGS
Auto (pannello laterale)    wx.ART_HELP_SIDE_PANEL
Informazioni                wx.ART_INFORMATION
Vista elenco                wx.ART_LIST_VIEW
Meno                        wx.ART_MINUS
Immagine mancante           wx.ART_MISSING_IMAGE
Nuovo                       wx.ART_NEW
Nuova cartella              wx.ART_NEW_DIR
File normale                wx.ART_NORMAL_FILE
Incolla                     wx.ART_PASTE
Più                         wx.ART_PLUS
Stampa                      wx.ART_PRINT
Domanda                     wx.ART_QUESTION
Termina l'applicazione      wx.ART_QUIT
Ripristina                  wx.ART_REDO
Vista riassuntiva           wx.ART_REPORT_VIEW
Un grosso tick              wx.ART_TICK_MARK
Suggerimento                wx.ART_TIP
Annulla                     wx.ART_UNDO
Attenzione                  wx.ART_WARNING
=========================== ===========================


Per adesso basta così! Ma ricordatevi di questo elenco quando parleremo di menù e barre degli strumenti...
