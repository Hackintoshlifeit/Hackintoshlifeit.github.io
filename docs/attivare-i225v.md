---
layout: page
title: Attivare Intel I225V
permalink: /attivarei225v/
---

La scheda Intel I225-V è da considere come la I225LM nativa nel kext AppleIntelI210Ethernet.kext
per cui necessita solo di un fake

- Includere in EFI [FakePCIID.kext](../files/FakePCIID.kext.zip) 
- Includere [FakePCIID_Intel_I225-V.kext](../files/FakePCIID_Intel_I225-V.kext.zip)

Identificare in Ioreg la posizione della scheda di rete
![ioreg](../images/i225v-ioreg.png)

In questo caso in RP05
Con id dispositivo che deve essere cambiato da 15F3 a 15F2 invertendo i byte e diventando f215 Inseriamo la device sul con g di opencore con 1C,4 come visto su ioreg
![configplist](../images/i225v-config.png)

E verifichiamo che Info.plist all’interno del Kext FakePCIID_Intel_I225-V sia coerente
![infoplist](../images/i225v-info.png)