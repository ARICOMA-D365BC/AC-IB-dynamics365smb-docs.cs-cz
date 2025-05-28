---
title: Analytics Suite – Nastavení
description: Návod pro nastavení modulu Analytics Suite pro Dynamics 365 Business Central
author: Makowka-Tomas
date: 28/05/2025
reviewer: janousek
ms.service: dynamics-365-business-central
ms.search.keywords: Analytics Suite, Power BI, data, business intelligence
---

# Analytics Suite – Nastavení

> Aktualizace: 28.05.2025

Modul **Analytics Suite** rozšiřuje možnosti analýzy dat a vizualizace klíčových ukazatelů v prostředí Dynamics 365 Business Central. Pro správné fungování je nutné provést následující nastavení:

- **Instalace rozšíření v Business Central**
- **Nastavení Analytics Suite v Business Central**
- **Připojení Power BI aplikace k vlastním datům**

## Instalace rozšíření v Business Central

1. Přihlaste se do prostředí Business Central.
2. Otevřete **AppSource** a vyhledejte **Analytics Suite**.

![Instalace rozšíření](media/analytics-suite-app-source.png)

3. Vyberte rozšíření **Analytics Suite for Business Central** a klikněte na **Get it now** (Instalovat).

![Instalace rozšíření](media/analytics-suite-app-install.png)

4. Dokončete instalaci dle průvodce.

![Instalace rozšíření](media/analytics-suite-app-install2.png)

## Nastavení Analytics Suite v Business Central

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Analytics Suite Setup** a poté vyberte související odkaz.
2. Na stránce **Analytics Suite Setup** aktivujte modul zaškrtnutím políčka **Enabled**.
3. Přejděte na stránku **Informace o společnosti** a u společností, které chcete analyzovat v Analytics Suite, aktivujte možnost **Enabled**.

![Nastavení Analytics Suite](media/analytics-suite-setup-bc.png)

## Připojení Power BI aplikace k datům

Pro správné zobrazení reportů a dashboardů je nutné propojit Power BI aplikaci s vaším prostředím Business Central:

1. Přejděte na [powerbi.com](https://powerbi.com) a přihlaste se.
2. V levém panelu zvolte **Apps**.
3. Klikněte na **Get Apps**.
4. Do vyhledávacího pole zadejte **Analytics Suite** a vyberte aplikaci od společnosti Aricoma.
5. Klikněte na **Get it now** a nainstalujte aplikaci.
6. Otevřete report **Analytics Suite** v příslušném workspace.
7. Klikněte na **Connect your data**.
8. Do pole **Environment** zadejte název prostředí vaší instance Business Central (část URL před ".dynamics.com").

![Připojení Power BI](media/analytics-suite-setup-powerbi.png)

## Viz také

[Analytics Suite – Přehled](analytics-suite.md)  
[Streamline Tools](../StreamlineTools/streamlinetools.md)
