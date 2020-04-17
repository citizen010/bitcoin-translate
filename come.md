[indice](README.md)
## Come funziona
Il modo migliore per comprenderne il funzionamento è analizzare ogni passaggio a cui è sottoposta una tipica [transazione](glossario.md#transazione) - __dalla sua generazione nel [wallet](glossario.md#wallet) del mittente  (Alice), al suo arrivo nel [wallet](glossario.md#wallet) del destinatario (Bob)__ - ciò ti permetterà di avere una panoramica di tutti gli elementi che concorrono al funzionamento del network globale.

> Nell'esempio sottostante non si fa riferimento ad un particolare [wallet](glossario.md#wallet) in quanto ognuno di essi ha almeno due funzionalità : __INVIA__ e __RICEVI__. Le reali modalità operative variano in funzione del [wallet](glossario.md#wallet) scelto, ma la sostanza - cioè i risultati delle operazioni sottostanti - non cambia.

> Alice e Bob posseggono ognuno un loro [wallet](glossario.md#wallet), __ma non necessariamente lo stesso__. Non è altresì necessario che Alice e Bob si conoscano. Le motivazioni alla base della transazione sono irrilevanti.

> __INVIA__ = utilizzare la funzionalità __INVIA__ del proprio [wallet](glossario.md#wallet)

> __RICEVI__ = utilizzare la funzionalità __RICEVI__ del proprio [wallet](glossario.md#wallet)

- [ ] Alice decide di inviare a Bob 1 BTC (__INVIA__)
- [ ] Bob (__RICEVI__) genera un [indirizzo bitcoin](glossario.md#address) e lo fornisce (via mail, web, tel, msg, etc.) ad Alice 
- [ ] Alice specifica l'[indirizzo bitcoin](glossario.md#address) di Bob e l'importo (1 BTC) nella trasfazione sul suo [wallet](glossario.md#wallet) e conferma l'invio
- [ ] Il [wallet](glossario.md#wallet) di Alice trasmette la [transazione](glossario.md#transazione) (firmata con la sua [chiave privata](glossario.md#pkey)) sulla [blockchain](glossario.md#blockchain) affinchè venga processata dai [nodi](glossario.md#fullnode) del network
- [ ] I [nodi](glossario.md#fullnode) (sianmo essi __full node__ oppure __mining node__) verificano che la [transazione](glossario.md#transazione) rispetti tutte le regole del consenso imposte dal protocollo bitcoin e, solo a questo punto, la trasmettono ai nodi a cui a loro volta sono collegati - così via fino a propagarsi per tutto il network globale
- [ ] Quando la transazione raggiunge un [mining node](glossario.md#miningnode), quest'ultimo la aggiunge nella sua [mempool](glossario.md#mempool) - ovvero un contenitore di tutte le transazioni in attesa di conferma
- [ ] Il [mining node](glossario.md#miningnode) genera un nuovo blocco candidato 


"Can you explain the lifecycle of a transaction,
from the point someone sends it from their wallet
until it is confirmed on the Bitcoin
blockchain?" That is a great question, Mario.

Your wallet constructs a transaction
by accumulating bitcoin in your wallet,

assigning it one or multiple destination 
addresses, and then signing that transaction.

Your wallet will transmit the [signed transaction] to
nodes it is connected to, perhaps eight different nodes.

These other nodes may be other wallets or mining
nodes; nodes belonging to exchanges or merchants,

people [conducting] e-commerce
or just running a node for fun.

They will each receive this transaction from your node.
The first thing they will do is validate it.

Every node validates every transaction. 
When they receive a transaction from your node,

they don't know if your node created this 
transaction, or if you were just forwarding it.

They are receiving transactions from nodes around them
all the time. That is how transactions are propagated.

When they receive this transaction, they validate it.
If it is valid, all of the amounts are correct,

it has the necessary fee, and is not trying to
spend something that has already been spent, etc.

[It must follow] all the rules of consensus. 
The signatures must all be valid.

It must fulfill certain criteria regarding the size of the
transaction and scripts within the transaction, etc.

Everything is validated by each of the 
nodes that receives your transaction.

Only then will those nodes send it
to the nodes they are connected to.

You send it to the nodes you are connected to, they
validate it, then they send it to nodes they connect to...

which then send it out to all nodes they 
are connected to, but always after validating.

Eventually, through this process of flood propagation,
the transaction is sent to every node in the network.

Some of those nodes will be miners.
Let's talk about what happens then.

When the transaction is validated by each node
that receives it, whether a full node or a mining node,

each one maintains a pool of unconfirmed transactions.

Think of [the mempool] as a giant bucket where 
unconfirmed transactions wait to be confirmed.

Nodes keep track of what transactions they
have seen which have not yet been confirmed.

They store them in this pool of 
transactions called the mempool.

Of course, it is important to understand 
that there isn't [just one] mempool.

There is a mempool on every node.

Because of differences in timing [during] propagation,
mempools will not have an identical set of transactions,

although there will probably be a 99% overlap.

Perhaps the same transactions
were received in a different order.

But [the unconfirmed transactions]
will be in most of the node mempools.

For mining nodes, the mempool
serves a very important purpose.

It provides transactions for
the miner to add to a new block.

If you are looking at this from the perspective of
a mining node, and a new block has just been found,

that means the race is on for the next block.

In order to participate in that competition as a miner,
they must construct a [candidate] block.

Then they will try to solve the proof-of-work.
But first they will construct an empty block.

That empty block has a link to
the most recent previous block,

which will establish its position on the chain.

It also has a timestamp and some
other information in the header.

It will have at least one transaction, which is the
coinbase transaction that pays [the block reward].

When miners construct their block, the miners
put their own bitcoin address as the destination.

This block is not valid if it doesn't have proof-of-work.
At this point, it doesn't have any transactions.

They will send that block to their mining 
equipment to find a proof-of-work.

They will also [construct a block] with transactions.

They will reach into the mempool of unconfirmed
transactions, looking for ones that pay the most fee.

They are looking for transactions that pay the
most satoshi per byte, to maximize their profit.

They will pull transactions out of the 
mempool based on maximum fee.

These transactions have already been validated,
which is they are in the mempool.

They don't get into the mempool
unless they have been validated.

They will put them into this candidate block. We call it
"candidate" because it hasn't yet been proven as valid.

As they add transactions, the block gets bigger.
[Then they] send it to the mining equipment,

which will try to find a proof for the block.

If they're lucky, after [generating] billions of hashes,
their mining equipment will find a nonce that creates...

a block hash below the difficulty target.

Therefore, it is a valid proof-of-work. It will tell
the node of the miner, "We found a [valid] block!"

The mining node then propagates that block out
to every node it is connected to, in the same way...

that transactions reach the mining nodes.

The block leaves the mining node and is 
propagated to all the other nodes on the network.

Both transactions and blocks are propagated
through this flooding [broadcast] process.

When other miners receive this block, 
they validate it as quickly as possible...

so they can immediately [start] trying to find
[another] block, with this new block as the parent.

They know they lost the previous round of 
the [mining] competition. Somebody else won.

Therefore, they need to start again.

All the nodes [between the miner and] 
your wallet will receive this new block.

As they receive the block, they validate it 
just like they validate every transaction.

They validate it and look at the transactions in there.

They see, 'Ah, this transaction is in my mempool.
But I see that it is now in a block, so I will take it out...

of my mempool and consider it confirmed.'

Eventually, this block will propagate all
the way back until it reaches your wallet.

Your wallet will know that this transaction has
one confirmation, and then the process continues.

So that is the entire lifecycle of a transaction.

