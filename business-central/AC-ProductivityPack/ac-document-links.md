---
title: AUTOCONT SOLUTIONS - Připojené dokumenty | Microsoft Docs
description: Document links
author: ac-kunes
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: Czech, document links, additional functions
ms.author: v-makune
---
# Připojené dokumenty
> Aktualizace 16.06.2023

Modul Připojené dokumenty umožnuje k libovolné entitě v D365 Business Central (BC) tzv. **připojit** dokumenty uložené v Sharepoint online. Umožňuje rovněž využít naplno potenciálu takového propojení v možnosti automatického doplňování sloupců Sharepoint dle kontextu získaného právě z konkrétní entity v BC, ke které uživatel dokument připojí.  

A nejen to, při ukládání souborů jsou velmi užitečné i možnosti v oblasti pojmenování ukládaných souborů na Sharepoint (typicky kvůli zamezení přepsání souboru jiným se stejným názvem).  

Obdobným způsobem lze i řídit umístění uložených dokumentů v knihovně. Někdy je vhodné např. ukládat soubory vždy do nové složky podle aktuálního měsíce či roku, jindy může být požadavkem ukládat do složky vytvořené právě pro konkrétní hodnotu entity (např. pro konkrétního zákazníka, zboží, apod).

Oproti dříve používanému modulu *Publikování SharePoint* není řešeno:
- Typy dokumentů/Hlavní dokument
- Výběr hodnot atributu z číselníku (tabulky)
- Vyhledávání dokumentů podle atributů
- Umístění dokumentu podle masky názvu/přípony souboru
- Podpora práce se SharePoint seznamy pro zákaznický vývoj

## Nahrání dokumentu do knihovny BC
Chci bez vazby nahrát dokument.

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Knihovny dokumentů** a poté vyberte související odkaz.
2.	Na stránce Knihovna dokumentu klikněte na čárkovaně orámovaný obdélník v informačním okně nazvaném Nahrát dokument.
3.	Vyberte ze souborového systému příslušný soubor a potvrďte stiskem tlačítka Otevřít.
4.	Variantně je možné soubor pomocí Drag&Drop přetáhnout myší na obdélník z bodu 2.
5.	Ověřte, že byla navýšena hodnota pole Počet položek.
6.	Zavřete stránku. 

> [!NOTE]
> Pro automatické přidávání položek knihovny v BC pro nové soubory/složky přidané přímo na SharePoint (synchronizace obsahu) je možné na knihovně dokumentů zapnout volbu **Automatická synchronizace SharePoint**.

## Vytvoření složky v knihovně BC
Kromě nahrání souboru je rovněž možné přímo v BC knihovně vytvořit složku, která se automaticky založí i v SharePoint.

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Knihovny dokumentů** a poté vyberte související odkaz..
2.	Spusťte akci Položky pro otevření seznamu položek knihovny evidovaných v BC.
3.	Pomocí prokliku do existujících složek přejděte na požadovanou úroveň v knihovně (zpět pomocí tlačítka Nahoru).
4.	Spusťte akci Nová složka, zadejte její název a potvrďte OK.
5.	Ověřte, že objevil nový řádek s Typem položky Složka a zadanou hodnotou v poli Název.

![Příklad struktury](media/ac-document-links-sample.png)


## Připojené dokumenty
Pokud chcete zjistit, ke kterým všem entitám v BC je příslušný dokument připojen, postupujte takto:

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Knihovny dokumentů** a poté vyberte související odkaz.
2.	Spusťte akci Položky pro otevření seznamu položek knihovny evidovaných v BC.
3.	Přejděte na požadovaný dokument a spusťte akci Detail položky.
4.	Na stránce Detail položky knihovny dokumentu spusťte akci Připojené dokumenty pro zobrazení všech entit v BC, ke kterým je vybraný dokument připojen.
5.	Zavřete stránku. 


## Přejmenování položky
Pokud chcete přejmenovat soubor či složku, postupujte takto:

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Knihovny dokumentů** a poté vyberte související odkaz.
2.	Spusťte akci Položky pro otevření seznamu položek knihovny evidovaných v BC.
3.	Přejděte na požadovaný dokument a spusťte akci Detail položky.
4.	Na stránce Detail položky knihovny dokumentu spusťte akci Přejmenovat položku, zadejte nový název položky a potvrďte stiskem OK.
5.	Zavřete stránku. 

> [!NOTE]
> Ve výchozím zobrazení je viditelný sloupec Hodnota pole 1 primárního klíče. V případě potřeby je možné si pomocí Přizpůsobení stránky zobrazit až 2 další úrovně primárního klíče

## Odstranění souboru z knihovny
Pokud chcete odstranit soubor z knihovny, je to možné provést více způsoby. Jedním z nich je odstranění přímo z položek knihovny dokumentů.

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Knihovny dokumentů** a poté vyberte související odkaz.
2.	Spusťte akci Položky pro otevření seznamu položek knihovny evidovaných v BC.
3.	Přejděte na požadovaný dokument a spusťte akci Odstranit.
4.	Potvrďte dotaz, který se objeví v případě, že je soubor připojen k alespoň jedné entitě v BC.
5.	Zavřete stránku. 

Při běžném používání je možnost smazat dokument přímo z jednotlivých částí BC.

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Zákazníci** a poté vyberte související odkaz.
2.	Přejděte na záznam s vybraným zákazníkem.
3.	V okně s fakty Připojené dokumenty přejděte na řádek s připojeným souborem a spusťte funkci Detail dokumentu.
4.	Na stránce Detail položky knihovny dokumentů klikněte nahoře na tlačítko Odstranit.

## Nahrání souboru a jeho připojení ke konkrétní entitě v BC
V převážné většině soubory přidávají právě takto, tedy uložení nového souboru s vazbou na konkrétní záznam v BC. Takto se přidá ke kartě zákazníka (viz Přidání Připojených dokumentů k vybrané funkcionalitě BC).

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Zákazníci** a poté vyberte související odkaz.
2.	Přejděte na záznam s vybraným zákazníkem.
3.	V okně s fakty Připojené dokumenty klikněte na název okna a spusťte akci Nahrát dokument.
4.	Vyberte ze souborového systému příslušný soubor a potvrďte stiskem tlačítka Otevřít.
5.	Variantně je možné soubor pomocí Drag&Drop přetáhnout myší na čárkovaný obdélník.
6.	Ověřte, že se soubor objevil v seznamu v okně s fakty.

> [!NOTE]
> V případě více platných šablon pro danou entitu je uživatel vyzván i k výběru požadované šablony publikování, podle které má být soubor uložen a zaevidován.

## Připojení již existujícího souboru k další entitě v BC
Někdy se jeden soubor týká více záznamů (např. Rámcová smlouva s holdingem se týká více zákazníků). V takovém případě je vhodné soubor nahrát k prvnímu záznamu a k dalším již jen vytvořit propojení.

1.	Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Zákazníci** a poté vyberte související odkaz.
2.	Přejděte na záznam s vybraným zákazníkem.
3.	V okně s fakty Připojené dokumenty klikněte na název okna a spusťte akci Připojit dokument.
4.	Na stránce Položky knihovny dokumentů vyberte požadovaný dokument a potvrďte OK.
5.	Ověřte, že se soubor objevil v seznamu v okně s fakty.

> [!NOTE]
> V případě více platných šablon pro danou entitu je uživatel vyzván i k výběru požadované šablony publikování, podle které má být soubor zaevidován.

## Zrušení připojení souboru k entitě v BC
Následující postup pouze zruší propojení souboru s entitou v BC, soubor i nadále zůstává uložen v knihovně.

1.	Vyberte ikonu  , zadejte Zákazníci a poté vyberte související odkaz.
2.	Přejděte na záznam s vybraným zákazníkem.
3.	V okně s fakty Připojené dokumenty přejděte na řádek s připojeným souborem a spusťte funkci Odstranit řádek.

## Rychlé zobrazení připojeného souboru 
K zobrazení souboru v stačí pouhé kliknutí na název souboru v okně s fakty Připojené dokumenty.

## Atributy knihovny dokumentů
Pokud máte na knihovně nastaveny atributy (viz Nastavení atributů knihovny dokumentů), z pohledu uživatelů je nejvýhodnější nastavit jejich automatické vyplňování v průběhu nahrávání souboru (viz Nastavení automatického doplňování atributů knihovny dokumentů). V takovém případě probíhá totiž vše na pozadí, jinak je uživateli zobrazena stránka Úpravy – Atributy dokumentů pro doplnění hodnoty povinného atributu.

Pro zobrazení volitelných atributů v průběhu nahrávání je třeba mít na šabloně nastaveno alespoň jedno z následujících:
- povinný atribut bez automatické doplňování
- pole **Zobrazovat dialog** s hodnotou „Vždy“


## Viz také

[Odesílání elektronických dokladů - nastavení](ac-document-links-setup.md)  
[Productivity Pack](ac-productivity-pack.md)
