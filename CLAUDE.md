# CLAUDE.md – birkirg.com

## Um verkefnið
Persónuleg vefsíða Birkis á birkirg.com. Hún sýnir verkefni, námsdagbók og
framtíðarplan. Seinna bætast við gagnasíður (t.d. /fotbolti og /hagtolur)
sem uppfærast sjálfkrafa.

Ég er að læra Git, GitHub og Cloudflare í gegnum þetta verkefni. **Útskýrðu stuttlega
hvað þú gerir og af hverju**, sérstaklega þegar þú notar skipanir eða hugtök
sem ég hef líklega ekki séð áður.

## Tækni
- Hreint HTML og CSS. Ekkert framework og ekkert build-skref (í bili).
- JavaScript aðeins ef nauðsyn krefur, og þá vanilla JS í sér skrá.
- Hýst á **Cloudflare Workers (static assets)**. Allar skrár sem birtast eru í `public/`.
- Sjálfvirk birting: push á `main` → Cloudflare birtir síðuna.

## Uppbygging
```
public/
  index.html          # forsíða
  plan/index.html     # framtíðarplan, áfangar 0–5
  dagbok/index.html   # námsdagbók, nýjasta færsla efst
  css/style.css       # eitt sameiginlegt stílblað fyrir allar síður
wrangler.jsonc        # stillingar fyrir Cloudflare
```
Hver undirsíða er mappa með `index.html`, svo slóðirnar verði hreinar (`/plan`, ekki `/plan.html`).

## Skipanir
- Keyra síðuna á tölvunni: `npx wrangler dev`, opnast á http://localhost:8787
- Birta handvirkt (yfirleitt óþarfi, push á main sér um það): `npx wrangler deploy`

## Reglur um efni og útlit
- Allt efni á **íslensku**. Kóði, skráarheiti og athugasemdir í kóða á ensku.
- Slóðir án séríslenskra stafa: `/dagbok`, ekki `/dagbók`.
- `<html lang="is">` og `<meta charset="utf-8">` á öllum síðum.
- Hönnun fyrir síma fyrst (mobile-first). Prófa í breiddinni 375px.
- Einfalt og læsilegt: svart á hvítu, letrið IBM Plex Mono hýst í `public/fonts/` (engar letur-tengingar við þriðja aðila), nóg bil, enginn óþarfi.
- Sami haus og valmynd á öllum síðum.
- Engar vafrakökur og engin þriðja aðila rakning.

## Vinnulag
- **Byrjaðu í plan mode** við allar breytingar sem snerta fleiri en eina skrá og bíddu eftir samþykki.
- Litlar breytingar, eitt commit fyrir hverja rökrétta breytingu.
- Commit-skilaboð á ensku, í boðhætti: `Add diary page`, `Fix menu on mobile`.
- Stærri breytingar fara á sér branch og inn með pull request.
- Ekki eyða skrám eða endurskipuleggja möppur án þess að spyrja fyrst.

## Öryggi
- **Aldrei** setja lykla, lykilorð eða tókena í kóða eða commit.
- Leyndarmál fara í `.env`, og `.env` er í `.gitignore`.
- Ef þú sérð eitthvað sem lítur út eins og lykill í skrá sem á að commit-a: stoppaðu og láttu mig vita.
