# CNC & Laser nástroje

Sada jednoduchých webových nástrojů pro přípravu podkladů pro laserové značení a řezání — hlavně pro převod grafiky z **CorelDRAW** do **DXF** a pro úpravu obrázků. Vše jsou samostatné HTML soubory, které běží **offline přímo v prohlížeči**. Nic se nenahrává na server, není potřeba žádná instalace ani připojení k internetu.

Nástroje vznikly pro workflow **CorelDRAW → DXF → ACI Magic Mark V3** (vláknový značkovací laser), ale hodí se i pro jiné řezací a značkovací programy.

## Jak to použít

Stáhněte příslušný `.html` soubor a otevřete ho dvojklikem v prohlížeči (Chrome, Edge, Firefox). To je vše — žádná instalace. Soubory můžete mít na ploše, na USB, kdekoliv.

## Nástroje

### svg2dxf.html — převodník SVG → DXF

Hlavní nástroj. Převede vektorovou grafiku vyexportovanou z CorelDRAW (formát SVG) na DXF vhodný pro řezací a značkovací software.

- Přetáhnete SVG, nastavíte šířku dokumentu (měřítko 1:1 v mm) a jemnost převodu křivek
- **Výběr v náhledu**: tažením rámečku označíte, co chcete exportovat (protne = vybere); pravé tlačítko posouvá, kolečko zoomuje
- **Vrstvy**: rozpozná vrstvy z Corelu (např. `OREZ`, `TEXT`) a zapíše je do DXF jako pojmenované vrstvy — v laserovém softwaru jim pak přiřadíte různé nástroje (řez / značení)
- Vrstvy lze zapínat/vypínat (pomocné vrstvy typu FreeCAD se vypnou samy)
- **Export**: jeden DXF s vrstvami, nebo každá vrstva zvlášť (ZIP)
- Vlastní název souboru
- **Přepínač Základní / Rozšířené**: rozšířený režim navíc umí výplně (HATCH, DXF R2000), export skupin jako bloky a export po jednotlivých křivkách

Výstup je standardně **DXF R12** s entitami POLYLINE — nejkompatibilnější formát pro řezací software.

> **Poznámka:** Text v Corelu před exportem převeďte na křivky (`Ctrl+Q`), jinak se nepřenese. Zaoblené rohy, které Corel občas exportuje deformovaně, také vyřeší převod na křivky.

### dxf_viewer.html — prohlížeč DXF

Kontrola hotového DXF před posláním do stroje.

- Přetáhnete DXF, zobrazí se na milimetrové mřížce
- Zoom, posun, rozměry výkresu, rozsahy souřadnic, souřadnice kurzoru
- Vrstvy barevně odlišené, lze je skrývat/zobrazovat
- Podporuje POLYLINE, LWPOLYLINE (i s oblouky), LINE, CIRCLE, ARC, POINT

### image_tool.html — výřez a konverze obrázků

Úprava rastrových obrázků, včetně přípravy pro laserové gravírování.

- Formáty: **JPG, PNG, BMP, WEBP, GIF** na vstupu; **PNG, JPG, BMP, WEBP** na výstupu
- **Výřez** tažením rámečku nebo přesně čísly
- Otočení (±90°), překlopení, zvětšení/zmenšení v procentech
- Volba kvality u JPG/WEBP, průhlednost u PNG/WEBP
- **Černobílý režim pro laser**: převod na čistě 2 barvy (černá + bílá) s nastavitelným prahem, možností invertování a rozptylu (dithering) pro fotky

### step-iges-viewer-offline.html — prohlížeč 3D modelů

Prohlížeč 3D CAD souborů ve formátech **STEP** a **IGES**. (Větší soubor, protože obsahuje 3D knihovnu.)

## Soukromí

Všechny nástroje pracují **výhradně lokálně ve vašem prohlížeči**. Žádný soubor se nikam neodesílá, nic se neukládá mimo váš počítač, nepoužívá se žádné připojení k internetu.

## Doporučený postup (CorelDRAW → laser)

1. V Corelu rozdělte objekty do vrstev podle účelu (např. `OREZ`, `TEXT`)
2. Text převeďte na křivky (`Ctrl+Q`)
3. Exportujte do SVG
4. V **svg2dxf.html** načtěte SVG, zkontrolujte měřítko a vrstvy, stáhněte DXF
5. Volitelně zkontrolujte výsledek v **dxf_viewer.html**
6. Naimportujte DXF do laserového softwaru a přiřaďte vrstvám nástroje

## Kompatibilita

Funguje v moderních prohlížečích (Chrome, Edge, Firefox). Nevyžaduje internet ani instalaci. Testováno pro import do ACI Magic Mark V3.

## Licence

[MIT](LICENSE) — volně k použití, úpravám i šíření. Nástroje vznikly jako hobby projekt pro vlastní potřebu.
