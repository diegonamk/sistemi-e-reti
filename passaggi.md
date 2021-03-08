
# Ripasso sistemi compito giovedí 18 e sabato 20
#### non si accerta la correttezza dei passaggi effettuati

# rete
Si ipotizza la creazione di due sottoreti
- Segreteria **SEG** 
- Laboratorio **LAB**

>**SEG** ha al suo interno 33 host

>**LAB** ha al suo interno 63 host

## L'Indirizzo di partenza é da scegliere a propia discrezione
###  POOL INDIRIZZI PRIVATI

Indirizzi Iniziali | Indirizzi finali | Host disponibili | Classi | CIDR MAX
--- | --- | --- | --- | --- |
10.0.0.0 | 10.255.255.255 | 16.777.216 | Singola classe A |              /8  
172.16.0.0 | 172.31.255.255 | 1.048.576 | 16 classi B contigue | /12  
192.168.0.0 | 192.168.255.255 | 65.536 | 256 classi C contigue  | /16

