# CAPITOLO 1: base

## Python's mantras

* Un linguaggio pratico
* La leggibilità conta
* Un solo modo ovvio per fare una cosa
* Imperativo, ad oggetti e funzionale
* I miglioramenti vengono inseriti dai PEP
* [La libreria python sempre sotto il cuscino!](http://docs.python.org/lib/) TODO

## WARNING

* Non c'entra nulla con il serpente
* Ma deriva dal Monthy Python Flying Circus
* TODO Ad esempio:
  - aaaaa
  - bbbbb
  - ccccc


## E ora... "The hello tour!"

### Il mio primo codice python

    1 # This is hello_who.py
    2
    3 def hello(who):
    4     print("Hello {}!".format(who))
    5
    6 if __name__ == "__main__":
    7     hello("mamma")

### IPython compagno di sviluppo

    $ ipython

    Python 2.7.12 (default, Jun 28 2016, 08:31:05)
    Type "copyright", "credits" or "license" for more information.

    IPython 5.0.0 -- An enhanced Interactive Python.
    ?         -> Introduction and overview of IPython's features.
    %quickref -> Quick reference.
    help      -> Python's own help system.
    object?   -> Details about 'object', use 'object??' for extra details.

    In [1]: %run hello_who.py
    Hello mamma!

    In [2]: !cat src/hello_who.py
    #!/usr/bin/python2


    def hello(who):
        print("Hello {}!".format(who))

        if __name__ == "__main__":
            hello("mamma")


## Tip: scopri lo Zen di Python [PEP 20](https://www.python.org/dev/peps/pep-0020/)

    In [1]: import this


### Inspect!

    1 # This is hello_who.py                # <-- i commenti iniziano con `#`
    2                                       #     possono essere all'inizio o a fine riga
    3 def hello(who):                       # <-- la funzione di definisce con `def`
    4     print("Hello {}!".format(who))    # <-- la stampa con `print` e le stringhe con `format`
    5
    6 if __name__ == "__main__":            # <-- [verifica di esecuzione e non di import](https://docs.python.org/2/library/__main__.html)
    7     hello("mamma")                    # <-- invoco la funzione con il valore

### Utilizzo come modulo

    $ ipython

    In [1]: import hello_who
    <nda: notate ... nessun output>

    In [2]: hello_who.__name__
    Out[2]: 'hello_who'

    In [3]: hello_who.hello("team")
    Hello team!

    In [4]: from hello_who import hello

    In [5]: hello("system")
    Hello system!


### La leggibilità conta

* Le linee guida di stile sono nel [PEP 8](https://www.python.org/dev/peps/pep-0008/)
  * ogni azienda può averne di differenti

Le classiche sono:

* Indentazione con 4 spazi, e non <TAB>: settate il vostro editor!
* Lunghezza della riga <= 79 caratteri
* Spazi intorno agli operatori

Le convenzioni per le `docstring` sono descritte nel [PEP 257](https://www.python.org/dev/peps/pep-0257)
in particolare:

* Se monolinea scrivere tutto su una riga
* Se multilinea il separatore finale (""") deve essere su una linea separata.

Mie convenzioni:

* classi CamelCase e funzioni + variabili minuscole con _
* il codice è scritto in inglese, in particolare i nomi delle variabili

### YAPF e Iflake8 i compagni "stilosi"

* YAPF: Yet Another Python Formatter
* IFlake8: verifica stile secondo PEP 8 (configurabile)

### Il mio secondo codice python

Aggiungiamo encoding del file e documentazione della funzione

     1 # -*- coding: utf-8 -*-               # <-- specifica dell'encoding del file se != ASCII
     2
     3 # This is hello_who.py
     4
     5 def hello(who):
     6     """                               # <-- `docstring` della funzione. Attributo `__doc__`
     7     Say hello to someone.
     8
     9        :param str who: The person to say Hello  # <-- [notazione parametri python in sphinx](http://www.sphinx-doc.org/en/stable/domains.html#python-signatures)
    10    """                               # <-- chiusura della docstring su linea dedicata (PEP 257)
    11    print("Hello {}!".format(who)
    12
    13 if __name__ == "__main__":
    14     hello("mamma")


### Il mio terzo codice python

Poi separiamo le funzioni, inseriamo le eccezioni, e un controllo:

    `../src/hello/hello_who_3.py`

### E testiamo con il compagno "testardo"

* py.test

### Fiato alle trombe: sequenze di hello!

Parametri di input, random, liste e cicli

    ../src/hello/hello_who_4.py

## Sintetizziamo con il tutorial python

* [Control Flow](https://docs.python.org/2/tutorial/controlflow.html)
* [Data Structures](https://docs.python.org/2/tutorial/datastructures.html)

### Tipi di dati semplici

* interi
* float
* Sequenze (mutabili o immutabili):
    * stringhe
    * liste: mutabile, slice, stringhe sono liste di caratteri
    * tuple: lista immutabile (usualmente eterogenea)
* set: immutabile non ordinato e senza ripetizioni
* dizionari

### Tipi di dati complessi

* decimal.Decimal
* datetime
    * datetime
    * date
    * timedelta
* collections
    * namedtuple
    * OrderedDict
* queue

### Funzione: passaggio per riferimento

La differenza sta nel mutable o immutable
