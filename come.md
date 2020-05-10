[indice](README.md)
## Come funziona
Il modo migliore per comprenderne il funzionamento è analizzare ogni passaggio a cui è sottoposta una tipica [transazione](glossario.md#transazione) - __dalla sua generazione nel [wallet](glossario.md#wallet) del mittente, al suo arrivo nel [wallet](glossario.md#wallet) del destinatario__ - ciò ti permetterà di avere una panoramica di tutti gli elementi che concorrono al funzionamento del network globale.

> Nell'esempio sottostante non si fa riferimento ad un particolare [wallet](glossario.md#wallet). Le reali modalità operative possono variare in funzione del [wallet](glossario.md#wallet) scelto, ma la sostanza - cioè i risultati delle operazioni sottostanti - non cambia.

> Il mittente ed il destinatario controllano ognuno le chiavi prviate del rispettivo [wallet](glossario.md#wallet), __che non deve essere necessariamente lo stesso__. Le motivazioni alla base della transazione sono irrilevanti.

- [ ] Il [wallet](glossario.md#wallet) costruisce una [transazione](glossario.md#transazione) accumulando bitcoin al suo interno, assegnandoli poi ad uno o più [indirizzi](glossario.md#address) di destinazione ed infine firmandola con la sua [chiave privata](gloassario.md#pkey).

- [ ] Il [wallet](glossario.md#wallet) del mittente trasmette la [transazione](glossario.md#transazione) ai nodi del network a cui è collegato affinchè venga processata.

- [ ] Ognuno di questi nodi (siano essi [full node](glossario.md#fullnode) oppure [mining node](glossario.md#miningnode)), come prima cosa, verifica che la [transazione](glossario.md#transazione) rispetti tutte le regole del consenso imposte dal protocollo bitcoin (ad esempio):

    * gli importi sono corretti
    * il [fee](glossario.md#fee) è adeguato
    * non si sta cercando di spendere qualcosa che è già stato speso
    * le firme sono valide
    * la dimensione della transazione rientra nei criteri
    * etc.

- [ ] Solo a questo punto, trasmette la [transazione](glossario.md#transazione) ai nodi a cui è a sua volta collegato i quali, a loro volta, ripetono il processo di verifica e di trasmissione - così via fino a propagarsi nell'intero network.

- [ ] Quando la [transazione](glossario.md#transazione) raggiunge un [mining node](glossario.md#miningnode), dopo essere stata validata viene aggiunta nella sua [mempool](glossario.md#mempool) - ovvero un contenitore di tutte le [transazioni](glossario.md#transazione) in attesa di conferma (non esiste un'unica [mempool](glossario.md#mempool), ma ne esiste una per ogni nodo del network).

- [ ] Per i [mining node](glossario.md#miningnode), la [mempool](glossario.md#mempool) riveste uno scopo importante: fornisce al miner le [transazioni](glossario.md#transazione) da aggiungere ad un nuovo [blocco candidato](glossario.md#cblock). Dalla sua prosepttiva, è aperta la "__gara__" per trovare il [blocco](glossario.md#blocco) successivo e per parteciparvi deve costruire un cosiddetto [blocco candidato](glossario.md#cblock) e cercare di risolvere la [proof-of-work](glossario.md#pow) al fine di aggiudicarsi la ricompensa ([block reward](glossario.md#blockreward)).

- [ ] Il [blocco candidato](glossario.md#cblock) è (inizialmente) un blocco vuoto con un link al più recente blocco precedente - il che stabilisce la sua posizione nella [blockchain](glossario.md#blockchain) - una indicazione cronologica (__timestamp__) nella sua header ed una speciale [transazione](glossario.md#transazione) (detta __coinbase transaction__) che contiene l'[indirizzo](glossario.md#adress) bitcoin del miner stesso come destinazione dell'eventuale [block reward](glossario.md#blockreward). Questo blocco non verrà considerato valido dal network finchè non riporterà la (eventuale) [proof-of-work](glossario.md#pow) ed al momento non contiene nessuna [transazione](glossario.md#transazione).

- [ ] Il miner manda il [blocco candidato](glossario.md#cblock) ai sui apparati hardware di calcolo ([ASIC](glossario.md#asic)) per trovare la [proof-of-work](glossario.md#pow) mentre riempie il blocco con [transazioni](glossario.md#transazione) presenti nella sua [mempool](glossario.md#mempool) partendo da quelle con i [fee](glossario.md#fee) più alti per massimizzare i sui profitti.
Il blocco viene chiamato "__candidato__" in quanto non è stata ancora provata la sua validità.

- [ ] La dimensione del blocco cresce all'aumentare delle [transazioni](glossario.md#transazione) aggiunte allo stesso e, se il miner è fortunato, dopo aver generato miliardi di __hash__ i suoi [ASIC](glossario.md#asic) troveranno un __nonce__ in grado di creare un __block hash__ minore della difficoltà imposta.

- [ ] A questo punto esiste una [proof-of-work](glossario.md#pow) valida, il miner ne è a conoscenza ed il suo nodo propaga questo blocco a tutti i nodi a cui è connesso, allo stesso modo in cui si propagano le [transazioni](glossario.md#transazione), fino a raggiungere tutto il network.


When other miners receive this block, they validate it as quickly as possible so they can immediately start trying to find another block, with this new block as the parent.

They know they lost the previous round of the [mining] competition. Somebody else won.

Therefore, they need to start again.

All the nodes [between the miner and] your wallet will receive this new block.

As they receive the block, they validate it just like they validate every transaction.

They validate it and look at the transactions in there.

They see, 'Ah, this transaction is in my mempool. But I see that it is now in a block, so I will take it out of my mempool and consider it confirmed.'

Eventually, questo blocco si propagherà fino a raggiungere il wallet di Bob.

Il wallet di Bob ora è a conoscenza che la transazione ha 1 conferma, ed il processo continua. Questo è l'intero cicla di vita di una transazione.




***
"Can you explain the lifecycle of a transaction,
from the point someone sends it from their wallet
until it is confirmed on the Bitcoin
blockchain?" That is a great question, Mario.

Your wallet constructs a transaction by accumulating bitcoin in your wallet,
assigning it one or multiple destination addresses, and then signing that transaction.
Your wallet will transmit the [signed transaction] to nodes it is connected to, perhaps eight different nodes.
These other nodes may be other wallets or mining nodes; nodes belonging to exchanges or merchants, people conducting e-commerce or just running a node for fun.
They will each receive this transaction from your node. The first thing they will do is validate it.
Every node validates every transaction. When they receive a transaction from your node, they don't know if your node created this 
transaction, or if you were just forwarding it.
They are receiving transactions from nodes around them all the time. That is how transactions are propagated.
When they receive this transaction, they validate it.
If it is valid, all of the amounts are correct, it has the necessary fee, and is not trying tospend something that has already been spent, etc.
It must follow all the rules of consensus. 
The signatures must all be valid.
It must fulfill certain criteria regarding the size of the transaction and scripts within the transaction, etc.
Everything is validated by each of the nodes that receives your transaction.
Only then will those nodes send it to the nodes they are connected to.
You send it to the nodes you are connected to, they validate it, then they send it to nodes they connect to...
which then send it out to all nodes they are connected to, but always after validating.
Eventually, through this process of flood propagation, the transaction is sent to every node in the network.
Some of those nodes will be miners. Let's talk about what happens then.
When the transaction is validated by each node that receives it, whether a full node or a mining node, each one maintains a pool of unconfirmed transactions.
Think of [the mempool] as a giant bucket where unconfirmed transactions wait to be confirmed.
Nodes keep track of what transactions they have seen which have not yet been confirmed.
They store them in this pool of transactions called the mempool.
Of course, it is important to understand that there isn't [just one] mempool. There is a mempool on every node.
Because of differences in timing [during] propagation, mempools will not have an identical set of transactions, although there will probably be a 99% overlap.
Perhaps the same transactions were received in a different order.
But [the unconfirmed transactions] will be in most of the node mempools.
For mining nodes, the mempool serves a very important purpose.
It provides transactions for the miner to add to a new block.
If you are looking at this from the perspective of a mining node, and a new block has just been found, that means the race is on for the next block.
In order to participate in that competition as a miner, they must construct a [candidate] block.
Then they will try to solve the proof-of-work. But first they will construct an empty block.
That empty block has a link to the most recent previous block, which will establish its position on the chain.
It also has a timestamp and some other information in the header.
It will have at least one transaction, which is the coinbase transaction that pays [the block reward].
When miners construct their block, the miners put their own bitcoin address as the destination.
This block is not valid if it doesn't have proof-of-work. At this point, it doesn't have any transactions.
They will send that block to their mining equipment to find a proof-of-work.
They will also [construct a block] with transactions.
They will reach into the mempool of unconfirmed transactions, looking for ones that pay the most fee.
They are looking for transactions that pay the most satoshi per byte, to maximize their profit.
They will pull transactions out of the mempool based on maximum fee.
These transactions have already been validated, which is they are in the mempool.
They don't get into the mempool unless they have been validated.
They will put them into this candidate block. We call it "candidate" because it hasn't yet been proven as valid.
As they add transactions, the block gets bigger.
[Then they] send it to the mining equipment, which will try to find a proof for the block.
If they're lucky, after [generating] billions of hashes, their mining equipment will find a nonce that creates a block hash below the difficulty target.
Therefore, it is a valid proof-of-work. It will tell the node of the miner, "We found a [valid] block!"
The mining node then propagates that block out to every node it is connected to, in the same way that transactions reach the mining nodes.
The block leaves the mining node and is propagated to all the other nodes on the network.
Both transactions and blocks are propagated through this flooding [broadcast] process.

---------------------------------------

When other miners receive this block, they validate it as quickly as possible so they can immediately start trying to find another block, with this new block as the parent.

They know they lost the previous round of the [mining] competition. Somebody else won.

Therefore, they need to start again.

All the nodes [between the miner and] your wallet will receive this new block.

As they receive the block, they validate it just like they validate every transaction.

They validate it and look at the transactions in there.

They see, 'Ah, this transaction is in my mempool. But I see that it is now in a block, so I will take it out of my mempool and consider it confirmed.'

Eventually, questo blocco si propagherà fino a raggiungere il wallet di Bob.

Il wallet di Bob ora è a conoscenza che la transazione ha 1 conferma, ed il processo continua. Questo è l'intero cicla di vita di una transazione.