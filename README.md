• Išbandyti 4 baitų duomenų persiuntimą, naudojant SPI sąsają, atliekant sekančius veiksmus:
- Sukonfigūruoti SPI4 sąsają: Full Duplex Master režime; Hardware NSS Signal –
nenaudosime. Frame Format – Motorola; Data Size – 8 bits; Prescale (for Baud rate) – 8;
Clock Polerity – Low; Clock Phase – 1 Edge; NSS Signal Type – Software.
- Susikurti reikalingus kintamuosius duomenų perdavimui ir priėmimui. Perduoti reikės
reikšmes 8, 12, 13, 15.
- Tarpusavyje sujunkite reikalingus išvadus duomenų perdavimui iš SPI4_MOSI (PE6) į
SPI4_MISO (PE5) kanalus. Duomenis išsiųsime ir priimsime į tą patį SPI4. SPI4_SCK
išvadas yra PE2.
- Užduočiai įgyvendinti naudokite HAL_SPI_TransmitReceive funkciją, kuri dirba CPU
blokavimo režime (angl. CPU blocking/pooling mode).
- Demonstracijai naudokite konfigūravimo „Debug“ režimą, stebėdami kintamųjų reikšmes
„Live Expressions“ lange, ir papildomai parodykite perduotus bei priimtus baitus TFT
ekrane.

• Sukonfigūruoti projektą, siekiant panaudoti SPI4 ir SPI3 ryšio kanalus. Konfigūruojant reikia
pasirinkti sekančius darbo režimus:
- SPI4 dirbtų – Full Duplex Master režime; Hardware NSS Signal – nenaudosime. Frame
Format – Motorola; Data Size – 8 bits; Prescale (for Baud rate) – 8; Clock Polerity – Low;
Clock Phase – 1 Edge; NSS Signal Type – Software.
- SPI3 dirbtų – Receive Only Slave režime; Hardware NSS Signal – nenaudosime. Frame
Format – Motorola; Data Size – 8 bits; Prescale (for Baud rate) – 8; Clock Polerity – Low;

Clock Phase – 1 Edge; NSS Signal Type – Software. NVIC Settgings -> SPI3 Global
Interrupt – enable.

- TIM2 sukonfigūruokite taip, kad galėtumėte fiksuoti 1 sekundės laiko intervalus. Sisteminį
dažnį ir kitus reikalingus parametrus pasirinkite taip, kad gautumėte 1 s periodą.

• Sujunkite reikalingus SPI4 ir SPI3 išvadus laideliais. Kadangi SPI3 dirba Receive Only Slave
režimu, privaloma sujungti SPI4_SCK (PE2) su SPI3_SCK (PB3) ir SPI4_MOSI (PE6) su
SPI3_MOSI (PC12). Jei norite pilnos simetrijos bandymams, papildomai galite sujungti
SPI4_MISO (PE5) su SPI3_MISO (PC11).

• Parašykite programą, kad kas 1 sekundę iš laikmačio skaitiklio pertraukties funkcijos
galėtumėte per SPI4 išsiųsti 1 baitą duomenų į SPI3. SPI3 naudoti pertraukčių mechanizmą, tai
yra CPU Non Blocking Mode. Iš SPI4 turi būti periodiškai siunčiamos reikšmės 1, 3, 7 ir 12.
Gautus rezultatus į SPI3 atvaizduokite TFT ekrane, o PG13 ir PG14 šviesos diodus naudokite
siunčiamo ir priimamo baito aktyvumo indikacijai.
