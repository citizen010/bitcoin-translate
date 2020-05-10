[indice](README.md)
## Come funziona
Il modo migliore per comprenderne il funzionamento è analizzare ogni passaggio a cui è sottoposta una tipica [transazione](glossario.md#transazione) - __dalla sua generazione nel [wallet](glossario.md#wallet) del mittente, al suo arrivo nel [wallet](glossario.md#wallet) del destinatario__ - ciò ti permetterà di avere una panoramica di tutti gli elementi che concorrono al funzionamento del network globale.

> Nell'esempio sottostante non si fa riferimento ad un particolare [wallet](glossario.md#wallet). Le reali modalità operative possono variare in funzione del [wallet](glossario.md#wallet) scelto, ma la sostanza - cioè i risultati delle operazioni sottostanti - non cambia.

> Il mittente ed il destinatario controllano ognuno le chiavi prviate del rispettivo [wallet](glossario.md#wallet), __che non deve essere necessariamente lo stesso__. Le motivazioni alla base della transazione sono irrilevanti.

> Il tempo medio di conferma per una [transazione](glossario.md#transazione) è funzione del [fee](glossario.md#fee) che si è disposti a pagare. Maggiore è il [fee](glossario.md#fee), più rapida è la conferma.

### Genesi di una transazione

- [ ] Il [wallet](glossario.md#wallet) costruisce una [transazione](glossario.md#transazione) accumulando bitcoin al suo interno, assegnandoli poi ad uno o più [indirizzi](glossario.md#address) di destinazione ed infine firmandola con la sua [chiave privata](gloassario.md#pkey).

- [ ] Il [wallet](glossario.md#wallet) del __mittente__ trasmette la [transazione](glossario.md#transazione) ai nodi del network a cui è collegato affinchè venga processata.

- [ ] Ognuno di questi nodi (siano essi [full node](glossario.md#fullnode) oppure [mining node](glossario.md#miningnode)), come prima cosa, verifica che la [transazione](glossario.md#transazione) rispetti tutte le regole del consenso imposte dal protocollo bitcoin (ad esempio):

    * gli importi sono corretti
    * il [fee](glossario.md#fee) è adeguato
    * non si sta cercando di spendere qualcosa che è già stato speso
    * le firme sono valide
    * la dimensione della [transazione](glossario.md#transazione) rientra nei criteri
    * etc.

- [ ] Solo a questo punto, trasmette la [transazione](glossario.md#transazione) ai nodi a cui è a sua volta collegato i quali, a loro volta, ripetono il processo di verifica e di trasmissione - così via fino a propagarsi nell'intero network.

- [ ] Quando la [transazione](glossario.md#transazione) raggiunge un [mining node](glossario.md#miningnode), dopo essere stata validata viene aggiunta nella sua [mempool](glossario.md#mempool) - ovvero un contenitore di tutte le [transazioni](glossario.md#transazione) in attesa di conferma (non esiste un'unica [mempool](glossario.md#mempool), ma ne esiste una per ogni nodo del network).

- [ ] Per i [mining node](glossario.md#miningnode), la [mempool](glossario.md#mempool) riveste uno scopo importante: fornisce al miner le [transazioni](glossario.md#transazione) da aggiungere ad un nuovo [blocco candidato](glossario.md#cblock). Dalla sua prosepttiva, è aperta la "__gara__" per trovare il [blocco](glossario.md#blocco) successivo e per parteciparvi deve costruire un cosiddetto [blocco candidato](glossario.md#cblock) e cercare di risolvere la [proof-of-work](glossario.md#pow) al fine di aggiudicarsi la ricompensa ([block reward](glossario.md#blockreward)).

- [ ] Il [blocco candidato](glossario.md#cblock) è (inizialmente) un [blocco](glossario.md#blocco) vuoto con un link al più recente [blocco](glossario.md#blocco) precedente - il che stabilisce la sua posizione nella [blockchain](glossario.md#blockchain) - una indicazione cronologica (__timestamp__) nella sua header ed una speciale [transazione](glossario.md#transazione) (detta __coinbase transaction__) che contiene l'[indirizzo](glossario.md#adress) bitcoin del miner stesso come destinazione dell'eventuale [block reward](glossario.md#blockreward). Questo [blocco](glossario.md#blocco) non verrà considerato valido dal network finchè non riporterà la (eventuale) [proof-of-work](glossario.md#pow) ed al momento non contiene nessuna [transazione](glossario.md#transazione).

- [ ] Il miner manda il [blocco candidato](glossario.md#cblock) ai sui apparati hardware di calcolo ([ASIC](glossario.md#asic)) per trovare la [proof-of-work](glossario.md#pow) mentre riempie il [blocco](glossario.md#blocco) con [transazioni](glossario.md#transazione) presenti nella sua [mempool](glossario.md#mempool) partendo da quelle con i [fee](glossario.md#fee) più alti per massimizzare i sui profitti.
Il [blocco](glossario.md#blocco) viene chiamato "__candidato__" in quanto non è stata ancora provata la sua validità.

- [ ] La dimensione del [blocco](glossario.md#blocco) cresce all'aumentare delle [transazioni](glossario.md#transazione) aggiunte allo stesso e, se il miner è fortunato, dopo aver generato miliardi di __hash__ i suoi [ASIC](glossario.md#asic) troveranno un __nonce__ in grado di creare un __block hash__ minore della difficoltà imposta.

- [ ] A questo punto esiste una [proof-of-work](glossario.md#pow) valida, il miner ne è a conoscenza ed il suo nodo propaga questo [blocco](glossario.md#blocco) a tutti i nodi a cui è connesso, allo stesso modo in cui si propagano le [transazioni](glossario.md#transazione), fino a raggiungere tutto il network.

- [ ] Quando gli altri miners ricevono questo [blocco](glossario.md#blocco), lo validano il più in fretta possibile in modo tale da partire immediatamente alla ricerca di un nuovo [blocco](glossario.md#blocco), definendo il [blocco](glossario.md#blocco) appena ricevuto come l'ultimo valido della [blockchain](glossario.md#blockchain). Ora sono a conoscenza che la  precedente "__gara__" è stata vinta da qualcun'altro e quindi iniziano una nuova "__gara__".

- [ ] Tutti i nodi - compresi quelli in contatto con il [wallet](glossario.md#wallet) del __destinatario__ - ricevono questo nuovo [blocco](glossario.md#blocco) e, non appena succede, validano tutte le [transazioni](glossario.md#transazione) in esso contenute e le confrontano con quelle contenute nella loro [mempool](glossario.md#mempool). Quando trovano una corrispondenza, cioè una delle [transazioni](glossario.md#transazione) è contenuta nel [blocco](glossario.md#blocco), la eliminano dalla [mempool](glossario.md#mempool) e la considerano confermata. 

- [ ] Il [wallet](glossario.md#wallet) del __destinatario__ è ora a conoscenza che la [transazione](glossario.md#transazione) ha 1 conferma, ed il processo continua.
