---
title: Evidence vratných obalů | Microsoft Docs
description: Návod jak správně evidovat vratné obaly
author: Makowka-Tomas
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: klicova slova, 
ms.date: 11/29/2024
ms.author: Makowka-Tomas
---
# Vratné obaly
## Nový standard v efektivitě obalového hospodářství

Představte si, že každý obal, paleta či přepravka má svůj příběh, který můžete jednoduše sledovat a spravovat. Modul Vratné obaly v systému Dynamics 365 Business Central je vaším klíčem k dokonalé kontrole nad obalovým hospodářstvím. 

V dnešní době, kdy je udržitelnost prioritou a efektivní řízení zdrojů nezbytností, vám tento modul umožní **optimalizovat oběh vratných obalů** a přinést do vaší společnosti **přehlednost** a **úspory**. Ať už sledujete salda obchodních partnerů, spravujete nákupní a prodejní transakce, nebo potřebujete **detailní reporting**, Vratné obaly vás nikdy nezklamou.

Dejte sbohem zbytečnému chaosu ve skladovém hospodářství a přivítejte systém, který **šetří váš čas**, **peníze** i **životní prostředí**. Přesvědčte se sami, jak jednoduše lze zvládnout komplexní evidenci vratných obalů a vytvořit udržitelnější budoucnost.

![karta vrat obalu](media/karta%20vrat.%20obalu.jpg)

Abychom vám usnadnili práci, přinášíme přehled nejčastějších scénářů, se kterými se můžete v běžné praxi setkat:
- **Zavedení nového obalu**
- **Nastavení počátečního množství obalu**
- **Nákup zboží zahrnující vratné obaly**
- **Prodej zboží zahrnující vratné obaly** 
- **Reporty**

## Zavedení nového obalu
1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Přehled vrat. Obalů** a poté vyberte související odkaz.
2. Na stránce **Přehled vrat. Obalů** vyberte akci **Nový**.

![prehled vrat. obalu](media/prehled%20vrat.%20obalu.jpg)

3. Po vybrání akce **Nový** se otevře **Karta vrat. obalu**.

![karta vrat obalu](media/karta%20vrat.%20obalu.jpg)

Každá Karta vratného obalu obsahuje tato pole: 

- **Číslo** – zvolte číselnou řadu vratných obalů 
    
- **Popis** – název vratného obalu 
    
- **Kód kategorie vrat. obalu** – identifikace kategorie vratného obalu 
    
- **Vyhledávací popis** 
    
- **Pohyb** – needitovatelné pole s odkazem do tabulky „**Položky vrat. Obalu**“. Zde zobrazená hodnota udává stav salda vratných obalů 
    
- **Vzorec data platnosti v prodeji** – zadejte dobu, do kdy má zákazník povinnost vratný obal vrátit 
    
- **Vzorec data platnosti v nákupu** – zadejte dobu, do kdy máte povinnost vratný obal vrátit dodavateli 
    
- **Uzavřeno** – pole pro uzavření(zamezení) dalšího použití dané karty vratného obalu

Nastavené hodnoty mají v případě, že jsou vyplněny, přednost před obecným nastavením. 

Z karty je dále možnost s pomocí akce **Související** zobrazit **Položky vrat. Obalu** a **Poznámky**.

Jelikož každý Vratný obal je zbožím, je také nutno vytvořit kartu zboží daného vratného obalu a přiřadit jí číslo Vratného obalu. Volba „dvojité“ evidence je z důvodu oddělení sledování expirace vratných obalů od účetních operací. 

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Zboží** a poté vyberte související odkaz.
2. Na stránce **Zboží** vyberte akci **Nový**.
    - Jestliže máte nastavené **Šablony zboží**, objeví se tabulka **Vybrat šablonu pro nové zboží**, kde vyberete možnost **Zboží**.
3. Otevře se **Karta zboží**. Zde zadáte informace o vratném obalu a přiřadíte **Číslo vrat. obalu.**

![Karta zboží](media/karta%20zbozi.jpg)

## Nastavení počátečního množství obalu
Pro nastavení počátečních stavů salda obalů využijeme deníky vratných obalů, které slouží dále také k provádění oprav a korekcí.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Deník vratných obalů** a poté vyberte související odkaz.
2. Na stránce **Deník vratných obalů** vyplňte následující pole.

![Deník vratných obalů](media/denik%20vratnych%20obalu.jpg)

Deník vratných obalů obsahuje tyto pole:  

- **Typ položky –** vyberte, zda se jedná o Nákup, Prodej, Příjem, Výdej  
    
- **Číslo dokladu –** vyplňte číslo dokladu  
    
- **Číslo vratného obalu –** vyberte číslo související karty vratného obalu  
    
- **Číslo zboží –** vyberte číslo souvisejícího karty zboží  
    
- **Typ původu –** needitovatelné pole vyplněné automaticky na základě pole Typ položky  
    
- **Číslo původu** – vyberte číslo konkrétního dodavatele  
    
- **Popis** – název vratného obalu  
    
- **Množství** – zadejte počet kusů vratného obalu  
    
- **Vyrovnává položku –** vyberte položku k vyrovnání

3. Po vyplnění požadovaných polí vyberte akci **Tisk**, kde můžete zkontrolovat správnost vyplnění.
4. Na základě preferencí vyberte akci **Účto**, nebo **Účto a tisk**.

> [!WARNING]
> Při použití volby Oprava v deníku vratných obalů není při účtování prováděno párování položek dle nastavených kritérií. 

## Nákup zboží zahrnující vratné obaly
Při nákupu zboží obsahující vratné obaly je nutné zajistit, aby tyto obaly byly správně evidovány v systému. Vratné obaly jsou často používány pro přepravu zboží, a proto je důležité je uvést na nákupní objednávce, aby bylo možné sledovat jejich stav a salda.

### Scénář
Oddělení nákupu se na základě zvýšené poptávky rozhodlo objednat nové zboží od dodavatele Wide World Importers. Nákupní objednávka zahrnuje 5x **Stůl ATÉNY (1896-S)** a 20x **Křeslo PAŘÍŽ, černé (1900-S)**. Na základě informací od dodavatele víme, že zboží dorazí na 6 paletách, které budou evidovány jako vratné obaly. Správná evidence těchto obalů umožní jejich efektivní správu a sledování salda.

### Řešení
1. Vytvoříme novou **nákupní objednávku**
2. Vyplníme detaily dodavatele na záložce **Obecné**
3. Na řádcích objednávky vybereme požadované zboží a množství
4. Navíc ručně přidáme zboží vytvořené pro vratný obal

![nákupní objednávka](media/nakupni%20objednavka.png)

> [!IMPORTANT]
> Pro správné fungování je nutné, aby byla karta zboží propojena s kartou vratného obalu viz. **Zavedení nového obalu**.

## Prodej zboží zahrnující vratné obaly
Při prodeji zboží obsahujícího vratné obaly je nutné zajistit, aby tyto obaly byly správně evidovány v systému. Vratné obaly jsou často využívány k přepravě prodaného zboží, a proto je důležité je uvést na prodejní objednávce. To umožní přesné sledování jejich stavu a salda.

### Scénář
Zákazník si objednal 1x **Stůl ATÉNY (1896-S)** a 4x **Křeslo PAŘÍŽ, černé (1900-S)**. Pro splnění této objednávky je nutné vytvořit prodejní objednávku, do které kromě samotného zboží přidáme také položku vratného obalu – paletu, na které bude zboží přepraveno. 

### Řešení
1. Vytvoříme novou **prodejní objednávku**
2. Vyplníme informace o zákazníkovi na záložce **Obecné**
3. Na řádcích objednávky vyplníme objednané zboží a množství
4. Navíc ručně přidáme zboží vytvořené pro vratný obal

![prodejni objednavka](media/prodejni%20objednavka.png)

> [!IMPORTANT]
> Pro správné fungování je nutné, aby byla karta zboží propojena s kartou vratného obalu viz. **Zavedení nového obalu**.

## Reporting
Pro efektivní správu vratných obalů máte k dispozici různé reporty, které naleznete na příslušných kartách modulu. Tyto reporty vám umožní získat přehled o pohybech, saldu a dalších detailech vratných obalů.

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte požadovaný report a poté vyberte související odkaz na tiskovou sestavu.
 - **Podklad pro výkaz obalů:** Slouží k přípravě podkladů pro výkaznictví.
 - **Účtování vratných obalů – test:** Umožňuje otestovat správnost účtování vratných obalů.  
 - **Žurnály vrat. obalů:** Při každém účtování položky vratného obalu je vytvořen záznam v Žurnálu vratného obalu (obdoba Žurnálu zboží)
![Žurnály vratných obalů](media/zurnaly%20vrat.%20obalu.png)
- **Žurnál vratných obalů – množství:** Nabízí detail množstevních pohybů jednotlivých žurnálů vratných obalů.
    - Na řádku číslo zvolíme konkrétní žurnál, u kterého chceme znát detail
![Žurnál vratných obalů - množství](media/zurnal%20vrat.%20obalu%20-%20mnozstvi.png)

- Jestliže necháme řádek prázdný, sestava vytiskne detail všech žurnálů viz. Foto níže

![Žurnál vrat. obalů - množství tisk](media/zurnal%20vrat.%20obalu%20-%20mnozstvi%20tisk.png)

- **Detailní pohyby vratných obalů:** Poskytuje detailní historii všech pohybů vratných obalů. 
- **Přesun vratných obalů:** Přehled přesunů vratných obalů mezi sklady či zákazníky.  
- **Saldo vratných obalů zákazníka:** Ukazuje aktuální stav salda vratných obalů u jednotlivých zákazníků.
    - Je třeba zadat číslo zákazníka a období (datum), pro které chceme zjistit stav salda 
    - Sestavu můžeme spustit za **Zákazníka** nebo za **Plátce**

![Saldo vratných obalů zákazníka](media/saldo%20vrat.%20obalu%20zákazníka.png)

![Saldo vratných obalů zákazníka tisk](media/saldo%20vrat.%20obalu%20zákazníka%20detail.png)

- **Saldo vratných obalů dodavatele:** Zobrazuje stav salda vratných obalů u vašich dodavatelů.
    - Je třeba zadat číslo dodavatele a období (datum) pro které chceme zjistit stav salda 
    - Sestavu můžeme spustit za **Dodavatele** nebo za **Věřitele**

![Saldo vratných obalů dodavatele](media/saldo%20vrat.%20obalu%20dodavatele.png)

![Saldo vratných obalů dodavatele tisk](media/saldo%20vrat.%20obalu%20dodavatele%20detail.png)

**Viz také**

[Nastavení - Evidence vratných obalů (Vratné obaly)](pack-tracking-return-packing-setup.md)  
[Financial Pack](finance-pack.md)  
