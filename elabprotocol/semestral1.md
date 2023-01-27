# Semestrální práce KI/PZS - zpracování EKG a EMG

Datum: TODO

Kolaborace: TODO


## 1. Výpočet tepové frekvence z EKG signálu

### Zadání

Ve zdrojové databázi najdete celkem 17 měření EKG signálu. Signál je již filtrován a
centralizován kolem podélné osy. EKG signál obsahuje dominantní peaky, které se nazývají R
vrcholy. Vzdálenost těchto vrcholů určuje dobu mezi jednotlivými tepy. Počet tepů za minutu
je tedy počet R vrcholů v signálu o délce jedné minuty. Navrhněte algoritmus, který bude
automaticky detekovat počet R vrcholů v EKG signálech a prezentujte tepovou frekvenci při
jednotlivých jízdách/měřeních. Vás algoritmus následně otestujte na databázi MIT-BIH
https://physionet.org/content/nsrdb/1.0.0/ a prezentujte jeho úspěšnost vzhledem
k anotovaným datům z databáze.

### Postup řešení

Signál nejdříve projde okénkovou fourierovou transformací, poté se detekuje dominantní frekvence podle Ntého percentilu a vytváří se regiony s potenciálním R peakem. Dané regiony se poté prozkoumají a porovnává se maximální hodnota daného regionu s hodnotou Ntého percentilu celého signálu. Pokud daná maximální hodnota regionu přesáhne práh, označí se jako R peak. Nakonec se z počtu detekovaných R peaku vypočítá tepová frekvence.

### Výsledky

