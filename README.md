# Idempotentti UFW-Konfiguraatio Saltilla - Turvallinen Tiimiprojekti

*Tekijät: Oskari Häkämies ja Joonas Janttonen*

Tässä projektissa konfiguroidaan UFW (Uncomplicated Firewall) Saltilla Debian-serverille, avaten vain SSH (22), HTTP (80) ja HTTPS (443) idempotenttisesti Saltilla.. Opitte myös, miten mitä tahansa portteja saadaan auki SaltStackilla ja mitä hyötyä siitä voi olla teille työelämässä. 

**Ennen**                   

<img width="458" height="74" alt="image" src="https://github.com/user-attachments/assets/d5594d64-92d4-42f8-9661-f069d36a9a3a" />




**Jälkeen** 

<img width="561" height="211" alt="image" src="https://github.com/user-attachments/assets/ad8c7d12-7ffe-447f-97d3-6fdba2020e1e" />


## UFW:

suojaa palvelinta → vain halutut portit auki

yksinkertaistaa palomuurin hallintaa

antaa selkeän näkymän liikenteeseen


## Miksi avata portit:

22: etäyhteys ja DevOps-työkalut

80: HTTP → HTTPS -ohjaus

443: varsinainen web-palvelu, API, frontend jne. toimii turvallisesti



## Saltin sisällä ajetaan mainitsemat 3 porttia läpi (käytetään esityksessä): 

ufw_allow_ssh:
  cmd.run:
    - name: ufw allow 22/tcp

ufw_allow_http:
   cmd.run:
     - name: ufw allow 80/tcp


ufw_allow_https:
   cmd.run:
     - name: ufw allow 443/tcp




## Tiimin ei tarvitse tietää UFW:n komentoja (voi käyttää top.sls) eli voidaan ajaa myös sudo salt '*' state.apply ufw

Salt takaa:

toistettavuuden

versionhallinnan

muutoshistorian Gitissä

auditoinnin


# Esimerkkiskenaario: 

Yrityksessä otetaan käyttöön uusia palvelimia useille tiimeille. Jokaisella palvelimella pitää olla samat palomuurisäännöt: vain portit 22, 80 ja 443 saavat olla auki. Manuaalisesti tekemällä joku unohtaa aina jonkin asetuksen, ja osa palvelimista jää liian avoimiksi tai palomuuri jää perusasetuksilla ja käytettävyys laskee.

Saltin avulla yritys voi siis ajaa yhden UFW-tilan kaikille palvelimille.


Lähteet
===


- Debian wiki: Uncomplicated Firewall (ufw) 2025. Luettavissa: https://wiki.debian.org/Uncomplicated%20Firewall%20%28ufw%29. Luettu: 30.11.2025.

- Karvinen 2023: Run Salt Command Locally. Luettavissa: https://terokarvinen.com/2021/salt-run-command-locally/. Luettu: 28.11.2025.

- Karvinen 2018: Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux. Luettavissa: https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-     ubuntu-linux/. Luettu: 28.11.2025.

- Linux Code 2023: How to Configure ufw Firewall on Debian. Luettavissa: https://thelinuxcode.com/configure-ufw-debian/. Luettu: 30.11.2025.
