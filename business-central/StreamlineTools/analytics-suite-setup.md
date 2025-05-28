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

![Hledání rozšíření v Appsource](media/analytics-suite-app-source.png)

3. Vyberte rozšíření **Analytics Suite for Business Central** a klikněte na **Nainstalovat aplikaci**.

![Instalace rozšíření](media/analytics-suite-app-install.png)

4. Dokončete instalaci dle průvodce.

![Instalace rozšíření - průvodce](media/analytics-suite-app-install2.png)

## Nastavení Analytics Suite v Business Central

1. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Nastavení Analytics Suite** a poté vyberte související odkaz.
2. Na stránce **Nastavení Analytics Suite** aktivujte modul zaškrtnutím políčka **Povoleno**.

![Nastavení Analytics Suite](media/analytics-suite-setup-bc.png)

3. Vyberte ikonu ![Žárovky, která otevře funkci Řekněte mi](media/ui-search/search_small.png "Řekněte mi, co chcete dělat"), zadejte **Informace o společnosti** a poté vyberte související odkaz.
4. Na stránce **Informace o společnosti** a u dalších společností, které chcete analyzovat v Analytics Suite, aktivujte možnost **Zahrnout do Analytics Suite**.

![Povolení Analytics Suite](media/analytics-suite-company-information.png)

## Připojení Power BI aplikace k datům

Pro správné zobrazení reportů a dashboardů je nutné propojit Power BI aplikaci s vaším prostředím Business Central:

1. Přejděte na [powerbi.com](https://powerbi.com) a přihlaste se.
2. V levém panelu zvolte **Aplikace**.

![Aplikace](media/analytics-suite-apps.png)

3. Klikněte na **Získat aplikace**.

![Získat aplikace](media/analytics-suite-get-apps.png)

4. Do vyhledávacího pole zadejte **Analytics Suite** a vyberte aplikaci od společnosti **Aricoma**.

![Aplikace Power BI](media/analytics-suite-application.png)

5. Klikněte na **Získat hned** a nainstalujte aplikaci.

![Získat hned](media/analytics-suite-get-it-now.png)

6. Otevřete aplikaci **Analytics Suite** v příslušném workspace.

![Aplikace](media/analytics-suite-app-list.png)

7. Klikněte na **Připojit data**.

![Připojit data](media/analytics-suite-connect-data.png)

8. Do pole **EnvironmentName** zadejte název prostředí vaší instance Business Central.

## Viz také

[Analytics Suite – Přehled](analytics-suite.md)  
[Streamline Tools](../StreamlineTools/streamlinetools.md)