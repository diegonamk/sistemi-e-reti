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
## **10.20.255.0**
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
    ### *__FabbLAB__* = 84
    <p>&nbsp;</p>
1. ### Calcolo *h* della subnet
    1. ### Subnet **SEG**
        <p>&nbsp;</p>
        
        ![](https://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D-2%3Ehost%2844%29)

        ![](http://latex.codecogs.com/svg.latex?2^{h}>&space;host(44)&space;&plus;2)

        ![](http://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D%20%3E%2046%20%5CRightarrow%20%2064%20%5Cxrightarrow%5B%5D%7Bh%7D%206)
        <p>&nbsp;</p>
    1. ### Subnet **LAB**
        <p>&nbsp;</p>

        ![](http://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D%20-2%20%3E%20host(84))

        ![](http://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D%20%3E%20host(84)%20&plus;2)

        ![](http://latex.codecogs.com/svg.latex?\bg_white&space;2^{h}&space;>&space;86&space;\Rightarrow&space;128&space;\xrightarrow[]{h}&space;7)

        <p>&nbsp;</p>
    ### Subnet **SEG** = 6 --> 32-6 = /26
    ### Subnet **LAB** = 7 --> 32-7 = /25
    <p>&nbsp;</p>    
1.  ### Calcolo spazio allocato totale(*Sall*)

    ![](http://latex.codecogs.com/svg.latex?%5Cbg_white%20S_all%20=%20%202%5E%7B7%7D%20&plus;%202%5E%7B6%7D%20=%20192)

    <p>&nbsp;</p>

2. ### Calcolo *h* Sall 
    
    ![](http://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D%20-2%20%3E%20192)

    ![](http://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D%20%3E%20194)

    ![](http://latex.codecogs.com/svg.latex?%5Cbg_white%202%5E%7Bh%7D%20%3E%20194%20%5CRightarrow%20256%20%5Cxrightarrow%5B%5D%7Bh%7D%208)

    ### Supernet h = 8 --> 32-8 = /24

    <p>&nbsp;</p>


## Calcolo indirizzi
<p>&nbsp;</p>

| 24 | 25 | 26 | 27 | 28 | 29 | 30 | 31 | CIDR | RETE |
|:--:|----|----|----|----|----|----|----|------| ----|
|  *__0__* |  *__0__* |  0 |  0 |  0 |  0 |  0 |  0 |  /25 |  LAB |
|  0 |  *__0__* |  *__0__* |  0 |  0 |  0 |  0 |  0 |  /26 |  SEG |

<p>&nbsp;</p>

| 24 | 25 | 26 | 27 | 28 | 29 | 30 | 31 | CIDR | RETE |
|:--:|----|----|----|----|----|----|----|------| ----|
|  *__0__* |  *__0__* |  0 |  0 |  0 |  0 |  0 |  0 |  /25 |  LAB |
|  0 |  *__~~0~~__* |  *__0__* |  0 |  0 |  0 |  0 |  0 |  /26 |  SEG |

<p>&nbsp;</p>

| 24 | 25 | 26 | 27 | 28 | 29 | 30 | 31 | CIDR | RETE |
|:--:|----|----|----|----|----|----|----|------| ----|
|  *__0__* |  *__0__* |  0 |  0 |  0 |  0 |  0 |  0 |  /25 |  LAB |
|  0 |  *__1__* |  *__0__* |  0 |  0 |  0 |  0 |  0 |  /26 |  SEG |
<br>
##### *da 25(compreso) in poi siamo al quarto byte dell'IP*

<p>&nbsp;</p>

| RETI | CIDR |    THIS NET   |              HOST              |    GATEWAY    | BROADCAST     |
|:----:|:----:|:-------------:|:------------------------------:|:-------------:|---------------|
|  LAB |  /25 |  10.20.255.0  |   10.20.255.1 - 10.20.255.83   |  10.20.255.84 | 10.20.255.85  |
|  SEG |  /26 | 10.20.255.128 | 10.20.255.129 - 10.20.255.171  | 10.20.255.172 | 10.20.255.173 |

<p>&nbsp;</p>

### Per calcolare gli host il primo indirizzo parte da THIS NET + 1 e l'ultimo host é il fabbisogno -1
### Il Gateway é l'ultimo host +1
### Il Broadcast é Gateway +1

<p>&nbsp;</p>








        




    



    




