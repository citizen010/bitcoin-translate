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
- [ ] Quando la transazione raggiunge un [mining node](glossario.md#miningnode), quest'ultimo la salva nella sua [memmpool](glossario.md#mempool) insieme a tutte le altre transazioni rievute. 
