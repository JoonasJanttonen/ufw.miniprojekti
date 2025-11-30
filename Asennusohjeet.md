## Asennusohjeet: 

1. Asennetaan ensin UFW:


Voidaan käyttää komentoa *sudo apt install ufw*

Tämän jälkeen laitetaan se päälle. 

<img width="424" height="103" alt="image" src="https://github.com/user-attachments/assets/bfddf2e9-52d9-40bd-a968-a5c95da1afb6" />


2. Seuraavana tarkistamme sen tilan komennolla *sudo ufw status* tai yksityiskohtaisemmin *sudo ufw status verbose*, jotta näämme mitä portteja on avattuna. 


<img width="437" height="127" alt="image" src="https://github.com/user-attachments/assets/ef50444a-a505-4385-8578-de44591227d0" />



Huomaamme, että portteja ei ole auki sisään tulevalle liikenteelle. 


3. Jotta voimme avata portteja saltilla on meidän luotava salt kansio. 

<img width="301" height="85" alt="image" src="https://github.com/user-attachments/assets/14181d84-b409-41f0-ba72-375b4c99ce78" />


4. Luomme saltille lisähakemiston UFW, jotta lopputulos ei ole hujan hajan kaikkialla. 


<img width="301" height="85" alt="image" src="https://github.com/user-attachments/assets/daff0c25-a7c4-4151-a176-bdd5db9c3332" />


Kansiossa luomme init.sls tiedoston, johon pääsemme kirjoittamaan koodimme ja laittamaan läpi Salt-komentomme. Käytämme tässä vaiheessa komentoa *sudoedit init.sls*



<img width="720" height="263" alt="image" src="https://github.com/user-attachments/assets/90a3dd2c-3b89-4c99-9a7e-f7900d86b11b" />




5. Ajamme tämän läpi saltilla paikallisesti komennon läpi, jotta portit saadaan auki:



<img width="493" height="104" alt="image" src="https://github.com/user-attachments/assets/b36f880f-c819-48cd-9908-ffe530584759" />


Kuten huomaamme, salt toimii idempotenttisesti ja se ajoi portit auki. 



<img width="689" height="387" alt="image" src="https://github.com/user-attachments/assets/a407da97-0944-4e86-b213-3e1b4cac69fb" />


<img width="493" height="326" alt="image" src="https://github.com/user-attachments/assets/f88c3a3a-2f75-4bca-97d6-30733e85e536" />


6. Tämän jälkeen testaamme taas lopputulosta aiemmalla komennolla *sudo ufw status verbose* 

<img width="500" height="199" alt="image" src="https://github.com/user-attachments/assets/77a50146-356d-426b-86bc-a2ac1b22ec6b" />



Ja näämme, että portit ovat avattu sisääntulevalle liikenteelle. Mikäli palomuurin haluaa palauttaa oletusasetuksiin, niin voi käyttää komentoa *sudo ufw reset* 

Palomuuri sulkee taas sisääntulevalle liikenteelle portit 22, 80, 443. 
