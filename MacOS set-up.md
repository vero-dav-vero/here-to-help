# MacOS set-up 

This guide shows how to create an appropriate workplace in order to program in Physics (by using c++ language).

- [MacOS set-up](#macos-set-up)
  - [Mandatory: XCode Command Line Tools ](#mandatory-xcode-command-line-tools)
  - [Installazione delle componenti di base](#installazione-delle-componenti-di-base)
  - [Installazione di Visual Studio Code](#installazione-di-visual-studio-code)
  - [Installazione di componenti aggiuntivi](#installazione-di-componenti-aggiuntivi)
  - [Aggiornamenti dei software installati](#aggiornamenti-dei-software-installati)
- [Risoluzione dei problemi](#risoluzione-dei-problemi)
  - [Non è possibile lanciare VSCode da terminale](#non-è-possibile-lanciare-vscode-da-terminale)

> **Nota alla riga di comando**
>
> Quando indicato nel testo, potrebbe essere necessario inserire un comando da un'applicazione detta _Terminale_. In
> questa guida i comandi sono preceduti da un simbolo detto `prompt`, che può variare in base al terminale utilizzato o
> al sistema operativo. Tipicamente su Windows il simbolo è `>`, su Linux `$` e su MacOs `%` (oppure `$`).
>
> È possibile individuare il prompt all'inizio della linea di comando quando il terminale è in attesa di istruzioni.
> Seppur riportato, non si deve inserire il simbolo di prompt nello scrivere i comandi presentati in questa guida.
>
> Dopo aver inserito un comando è possibile eseguirlo battendo il tasto _Invio_.

## Prerequisito: i Command Line Tools di Xcode

I _Command Line Tools (CLT) di Xcode_ sono necessari per procedere con l'installazione di tutti gli strumenti di lavoro.

Puoi ottenere i CLT in uno dei seguenti modi (le opzioni sono esclusive, basta seguire uno solo degli approcci):

- apri l'applicazione Terminale (o Terminal) che si trova in Applicazioni -> Utiliy (o Applications -> Utility)
  - una volta aperta, esegui il comando `xcode-select --install` (premi invio dopo aver copiato la riga)
  - questo avvia una finestra di dialogo che ti permette di effettuare l'installazione
- scarica il prodotto da [https://developer.apple.com/downloads](https://developer.apple.com/downloads)
- come parte di [Xcode](https://itunes.apple.com/us/app/xcode/id497799835) stesso

A seconda dell'opzione scelta e delle risorse (ad es. connessione) disponibili, il processo può richiedere abbastanza
tempo (anche alcune decine di minuti o più). Questo vale sia per un'installazione completa di Xcode, sia in caso ci si
limiti all'installazione dei CLT.

Pertanto __raccomandiamo di effettuare questa parte dell'installazione già a casa, prima di presentarsi in
laboratorio__, dove sarà poi completato il resto dell'installazione e configurazione.

## Installazione delle componenti di base

Per l'installazione dei prodotti software necessari useremo principalmente il _package manager_ [`brew`](https://brew.sh/).

Per l'uso di _brew_ sono richiesti alcuni prerequisiti:

- macOS High Sierra (10.13) o superiore
- i cosiddetti Command Line Tools (CLT) per Xcode, la cui installazione è discussa [poco
  sopra](#prerequisito-i-command-line-tools-di-xcode)

Una volta installati i CLT, installa `brew` eseguendo, sempre sul Terminale, il seguente comando

```zsh
% /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Se, durante l'installazione di `brew`, vedi errori relativi al comando `curl` che si lamenta di verifica di certificati,
prova ad aprire l'URL corrispondente dentro Safari, visualizza il certificato e accettalo "fidandoti sempre". Poi
riprova il comando indicato sopra.

Per verificare se l'installazione di `brew` è andata a buon fine, eseguite il comando

```zsh
% brew
```

Caso il Terminale si lamenti dell'assenza del comando `brew` (es. `zsh: command 
not found: brew`), per terminare l'installazione potrebbe essere necessario 
eseguire alcuni comandi aggiuntivi. Le istruzioni esatte **sono riportate, sul 
Terminale, nelle ultime righe dell'output del comando installazione**.

Una volta terminata l'installazione di `brew`, puoi installare gli strumenti software necessari per il corso.

Innanzitutto verifica la versione più recente disponibile di `gcc`

```zsh
% brew search gcc
```

E individua la versione maggiore disponibile. Supponendo sia la versione 11, installa i pacchetti con

```zsh
% brew install git gcc@11 clang-format
```

Questo, nell'ordine, installa

- il _version control system_ [git](https://git-scm.com/)
- il compilatore [gcc](https://gcc.gnu.org/)
- [clang-format](https://www.kernel.org/doc/html/latest/translations/it_IT/process/clang-format.html), uno strumento che
  verifica la buona formattazione del codice

Il comando da utilizzare per la compilazione del codice C++ in macOS è `g++-11` (tutto attaccato), non `g++`, come verrà
di solito indicato nel materiale di questo corso. Nota che il comando `g++` è probabilmente disponibile, ma è un _alias_
per un altro compilatore e potrebbe essere necessario specificare esplicitamente delle opzioni di compilazione
aggiuntive, in particolare `-std=c++14`; il comando quindi diventerebbe `g++ -std=c++14`.

Per verificare la corretta installazione dei pacchetti menzionati, eseguire i seguenti comandi

```zsh
% git --version
git version 2.33.0
```

```zsh
g++-11 --version
g++-11 (Homebrew GCC 11.2.0) 11.2.0
Copyright (C) 2021 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

```zsh
% clang-format --version
clang-format version 12.0.1
```

I numeri di versione riportati sopra sono solo indicativi, e possono variare nel
tempo, quello che è importante è che nessuno dei tentativi di esecuzione termini
con un errore del tipo `zsh: command not found:`.

## Installazione di Visual Studio Code

Per l'installazione di _Visual Studio Code_ (VSCode) scarica il pacchetto dalla 
[pagina](https://code.visualstudio.com/) corrispondente.

Alcune note in merito all'installazione:

- ricorda di copiare l'applicazione `Visual Studio Code.app` dentro la cartella Applicazioni (Applications) come
  descritto [qui](https://code.visualstudio.com/docs/setup/mac#_installation)
- abilita l'esecuzione dell'applicazione da Terminale seguendo le istruzioni riportate
    [qui](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line) 

Per verificare la corretta installazione di VSCode, provare ad aprirlo eseguendo
il seguente comando

```zsh
% code
```

## Installazione di componenti aggiuntivi

Nella seconda parte del corso, si farà uso di strumenti aggiuntivi, quali:

- [CMake](https://cmake.org/): un software libero multipiattaforma che automatizza la compilazione di progetti complessi
- [SFML](https://www.sfml-dev.org/): una libreria multimediale (che utilizzeremo per lo sviluppo di applicazioni
  grafiche)

Nel caso di macOS, è possibile installare anche queste componenti aggiuntive tramite `brew`:

```zsh
% brew install cmake sfml
```

## Aggiornamenti dei software installati

È buona norma aggiornare periodicamente, indicativamente una volta alla settimana, tutti i pacchetti software
installati.

Nel caso delle componenti installate tramite `brew`, l'aggiornamento si effettua [eseguendo i seguenti
comandi](https://docs.brew.sh/FAQ#how-do-i-update-my-local-packages)

```zsh
% brew update
% brew upgrade
```

Il primo comando aggiorna il programma `brew` e la lista dei pacchetti (detti _formulae_) disponibili. Il secondo
effettua l'aggiornamento dei pacchetti installati. Prima di eseguire il comando `brew upgrade`, puoi controllare la
lista dei pacchetti che verranno aggiornati col comando

```zsh
% brew outdated
```

# Risoluzione dei problemi

## Non è possibile lanciare VSCode da terminale

Qualora, lanciando il comando `code` da terminale, si incorra in un errore simile a:

```zsh
% code
zsh: command not found: code
```

procedere come segue:

1. si apra la _Command Palette_ di VSCode utilizzando i tasti di scelta rapida 
   `Cmd + Shift + P` e si esegua il comando che si trova digitando  'uninstall 
   code from path';
1. si provi di nuovo ad abilitare l'esecuzione dell'applicazione da Terminale 
   seguendo le istruzioni riportate [qui](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).

> __NOTA__: qualora venga richiesto di digitare la propria password, o di confermare 
> il comando utilizzando il lettore di impronte digitali, lo si faccia.

A questo punto, si provi di nuovo ad eseguire il comando `code` da terminale:

```zsh
% code
```
