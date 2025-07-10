# Firewall_project

## VERSIONE IN ITALIANO

### Scopo del Progetto

Questo progetto nasce dalla volontà di approfondire la conoscenza del networking al livello di sistema operativo. Il mio scopo è quello di appronfondire:
  1) catturare pacchetti di rete in modalità promiscua;
  2) parsare le intestazioni dei principali protocolli (Ethernet, IP, TCP/UDP);
  3) implementare logiche di filtro basate su regole definite (es. indirizzi IP, porte, protocolli);
  4) eventualmente, gestire lo stato delle connessioni (firewall stateful).

### Utilizzo

Per avviare il firewall compilare con 
    <gcc main.c -o EXEC>
e avviare con
    <sudo ./EXEC <nome_interfaccia> >

L'utilizzo dei privilegi da amministratore sono necessari in quanto stiamo comunicando direttamente con il sistema operativo (quindi attenzione!!!).
Per chiudere il firewall usare ctrl^C da terminale oppure impartire il comando <sudo kill -2 PID > (<ps -a> per trovare il PID del processo).
Il non funzionamento dell'interfaccia di rete usata per avviare il firewall è un comportamento normale, dovuto al fatto che in ogni caso la socket
viene chiusa e non re-impostata allo stato precedente all'avvio del firewall. Disattivando la rete e ri-attivandola ci pensa il SO del sistema a
ripristinare il normale utilizzo dell'interfaccia.

Nota: si consiglia comunque di utilizzare i sorgenti in un ambiente sicuro ed isolato come una VM.


## ENGLISH VERSION

### Goal of the project

This project comes from my desire to increase my understanding of OS-level networking. My primary goals are to explore:
  1) sniffing network packets in promiscuous mode;
  2) parsing the headers of most important protocols (Ethernet, IP, TCP/UDP);
  3) implementing filtering logic based on defined rules (for example IP addresses, ports, protocols);
  4) eventually, managing connection states (stateful firewall).

### Usage

To start the firewall compile with
  <gcc main.c -o EXEC>
and exec with
  <sudo ./EXEC <interface_name> >

Root privileges are required because this program interacts directly with the operating system's network (use it with caution!).
To stop the firewall press ctrl^C or execute the following command <sudo kill -2 PID > in another terminal (<ps -a> to find PID of the process).
If the specified network interface doesn't work anymore after the firewall closes, it's 'cause the OS didn't fully restore the socket to its previous state.
To fix this, de-activate network interface (through your system's network settings menu).
Simply re-activating it, OS will handle the correct restore of the interface. 
