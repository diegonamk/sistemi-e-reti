# **LEGGERE IL FILE CON NIGHTMODE OFF**

# Ripasso sistemi compito giovedí 18 e sabato 20
#### non si accerta la correttezza dei passaggi effettuati

# rete
Si ipotizza la creazione di due sottoreti
- Segreteria **SEG** 
- Laboratorio **LAB**

>**SEG** ha al suo interno 33 host

>**LAB** ha al suo interno 63 host

## L'Indirizzo di partenza é da scegliere a propia discrezione
<br>

##  POOL INDIRIZZI PRIVATI

Indirizzi Iniziali | Indirizzi finali | Host disponibili | Classi | CIDR MAX
--- | --- | --- | --- | --- |
10.0.0.0 | 10.255.255.255 | 16.777.216 | Singola classe A |              /8  
172.16.0.0 | 172.31.255.255 | 1.048.576 | 16 classi B contigue | /12  
192.168.0.0 | 192.168.255.255 | 65.536 | 256 classi C contigue  | /16

Per questo esempio useremo l'indirizzo 
## **10.20.30.10**
<br>

## Determinazione del CIDR(*/n*)

1. ### Calcolo **fabbisogno** della singola subnet
    1. ### Calcolo fabbisogno rete **SEG**
        **Fabb** = host(33)+gateway(1)+esp(10) 
        <br>
        **Fabb** = 44

    1. ### Calcolo fabbisogno rete **LAB**
        **Fabb** = host(63)+gateway(1)+esp(20)
        <br>
        **Fabb** = 84

    ### *__FabbSEG__* = 44
    ### *__FabbLAB__* = 44
    <p>&nbsp;</p>
1. ### Calcolo *h* della subnet
    1. ### Subnet **SEG**

    ![](https://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D-2%3Ehost%2844%29)

    ![](http://latex.codecogs.com/svg.latex?2^{h}>&space;host(44)&space;&plus;2)

    ![](http://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D%3E%20host(44)%20&plus;2)

    



    




