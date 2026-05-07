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
