# Bitcoin-layer3 concept
A decentralised peer-to-party fiat-Bitcoin Nostr-like protocol

#Bitcoin
## Preamble:
As of today, most Bitcoin buy and sell orders are being routed via a small number of Bitcoin exchanges like Binance, Kraken, and so on. This doesn't help to decentralise capital.

1st: While using such centralised trading platforms is common practice, it doesn't fully serve the idea of not having to trust large single entities and banks - and thus still blocks general de- banking, where money, power, as well as control over inflation, is taken away from banks/big entities. Also buying from such single big entities includes the risk of one single player going offline / out of business (see FTX / SBF, etc) and by that losing capital, parked there.

2nd: Still, there needs to be a fast, secure, usable, portable, convenient, reliable, cheap, cost- efficient, and compatible way to convert fiat currency into Bitcoin and back.

3rd: Meanwhile, there are some decentralised peer-to-peer alternatives like Bisq. However, there seem to be some blocking security measures for people who want to buy bitcoin for the first time (e.g., the need for already having Bitcoin in an escrow - but this requires a solution with the features of the previous point (2)). HodlHodl is a good alternative for this, where the buyer doesn't need to have Bitcoin in the first place. Meanwhile, this is not heavily automated, not decentralised and in risk of being shut down by regulations. The user needs to avoid scammers by trusting reviews, which often results in higher fees for users.

4th: Thus, there needs to be a Bitcoin onramp/entry point for new users, which combines the original idea of Satoshi Nakamoto (point 1 / decentralised capital) and, at the same time, combines the quality standards mentioned in point 2.
Note: This is, in some ways, similar to HodlHodl / Bisq but tries to solve some of their structural / systematical problems.

## Solution: A decentralised peer-to-party fiat-Bitcoin protocol.

### Preconditions:
Every user has their Bank API and their Wallet connected to their open-source program.

### Scenario 1 - Seller-view: 
User S wants to sell Bitcoin, while User D, E, and F (here summarised as “B”) want to buy Bitcoin. S sends a sell request on a Nostr-like protocol with a taker-fee for all potential buyers. B gets notified as soon as a new sell request arrives on their watching Nostr- like nodes. B sends their bank information (suggestion: bank information = IBAN or IBAN + Name) to S. S sends the amount of Bitcoin (via the Bitcoin Lightning Network) split up into P parts, equally distributed to the buyers and waits for T time. If, after T, the money from the mentioned bank information hasn’t arrived at the bank account of S, or if B hasn’t sent the agreed amount, S automatically marks their bank information on the Nostr-like protocol as delayed/red-flag, so future users won’t get scammed. Alternatively/Additionally, if preferred, the buyers' bank information can also get green-flagged on the Nostr-like protocol.
 
The higher P, the more buyer-participants are needed, but also the more secure in case one buyer acts in a bad way. To figure out which transaction has been sent by whom, the bank subject line can be used.

### Scenario 2 - Buyer-view:
Now, B stands for one buyer, and S stands for many sellers. B sends a buy request on the Nostr-like protocol together with a giver-fee for all potential sellers. S awaits such buy request on their watching node. S sends its banking information. B sends its public wallet address and marks the IBAN of S as pending on the protocol. The same wait/red-flag/ green-flag logic as in Scenario 1 applies.

Depending on the user's settings, certain buyers/sellers with more green flags/less pending transactions can be chosen.
If there are many buyers/sellers, a random selection out of them should be implemented, so a single entity can’t fake green flags by making transactions with itself.

If a certain bank number (by analysing the IBAN) has particularly many red flags on the protocol, it would indicate a bank trying to interrupt it and should be generally red-flagged.

If there aren’t many buyers/sellers online and a part-transaction happens to work very fast (maybe because buyer and seller share the same bank) - the buy/sell transaction can be split up into many send/receive transactions with one person but in very small amounts. This essentially represents a split up, automated HodlHodl buy/sell logic, but isn’t implemented on HodlHodl yet and reduces needed trust in each other's reviews, as well as reducing the risk of having this possibility shut down by regulations.
  
