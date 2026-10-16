# Čeština pro Hermes

Instalovatelný český jazykový balíček pro Hermes Agent / Hermes Desktop.

Balíček používá nativní rozhraní jazykových pluginů zavedené v Hermes 0.22. Základem je ručně revidovaný český katalog v `apps/desktop/src/i18n/cs.ts`; nové řetězce přidané do aktuálního Hermesu jsou doplněny v `locales/cs.desktop.yaml`.

## Aktuální stav

- ID pluginu: `hermes-czech-locale`
- Jazyk: `cs` — **Čeština**
- Aktuální sada klíčů Hermes Desktop: **5 105**
- Pokrytí aktuální sady Desktopu: **5 105 / 5 105**
- Ručně revidovaný základ: **4 564** položek
- Nově doplněné položky pro současný Hermes: **616**
- Neznámé klíče v doplňku: **0**
- Chybějící aktuální klíče Desktopu: **0**
- 75 starších položek v původním katalogu je zachováno pro zpětnou kompatibilitu; současný Hermes je jednoduše nepoužije.

Plugin nepřepisuje soubory Hermesu a přežije běžné aktualizace aplikace.

## Instalace

```powershell
hermes plugins install https://github.com/zionzangar/hermes-czech-locale
hermes config set display.language cs
```

Potom restartujte Hermes Desktop a běžící gateway/TUI. Pokud je desktopová část pluginu po instalaci vypnutá, zapněte ji v **Nastavení → Pluginy**.

Návrat do angličtiny:

```powershell
hermes config set display.language en
```

Odinstalace:

```powershell
hermes plugins uninstall hermes-czech-locale
```

## Struktura

```text
hermes-czech-locale/
├── plugin.yaml
├── locales/
│   ├── cs.yaml
│   └── cs.desktop.yaml
├── desktop/
│   └── plugin.js
└── apps/desktop/src/i18n/cs.ts
```

- `plugin.yaml` registruje jazyk `cs` v nativním systému Hermes.
- `desktop/plugin.js` převádí ručně revidovaný katalog do runtime Desktop pluginu.
- `locales/cs.desktop.yaml` doplňuje nové řetězce aktuální verze Hermesu.
- `locales/cs.yaml` obsahuje základní překlady sdílené Python/gateway vrstvou.
- `apps/desktop/src/i18n/cs.ts` zůstává zdrojovým ručně revidovaným katalogem.

## Rozsah překladu

Desktopové statické rozhraní je proti aktuálnímu exportu `locales/_keys.desktop.json` pokryto celé. Python/gateway katalog je zatím částečný a TUI bez vlastního českého souboru používá pro nepřeložené řetězce anglický fallback.

Odpovědi modelu, výstupy nástrojů, protokoly a názvy lomítkových příkazů jazykový balíček nemění — to je vlastnost systému jazykových balíčků Hermes.

## Údržba

Při nové verzi Hermesu:

1. porovnat `locales/_keys.desktop.json` s českým základem a doplňkem,
2. přeložit nové klíče,
3. zachovat poziční placeholdery `{0}`, `{1}` u funkčních Desktop řetězců,
4. spustit `hermes plugins validate` nad nainstalovaným balíčkem,
5. zvýšit verzi pluginu, pokud se mění distribuovaný balíček.

## License

MIT License, stejně jako upstream Hermes Agent.
