# Utvärdering av AI-granskningen

Fyll i efter varje PR. En rad per punkt i AI-kommentaren. **Träff** = rätt och värt att åtgärda · **Miss** = fel, eller rätt men oviktigt (brus) · **Oavgjord** = kräver kunskap modellen inte har (domänen, servern, vad som är testdata) – en människa måste avgöra.

Läs diffen själva först och skriv ner vad _ni_ hade anmärkt på. Det ni hittade men modellen missade hör hemma i sista kolumnen.

| PR                                      | Punkt (citat ur kommentaren, kort)                            | Träff / miss / oavgjord | Varför                                                                                                                                        | Det modellen missade                                                                                               |
| --------------------------------------- | ------------------------------------------------------------- | ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| A – Visa kundnummer och senaste faktura | kundnummer från URL:en styr vilken kund som hämtas            | Träff                   | Det stämmer att med ändringen kan användaren bestämma vilket customerNo som visas                                                             | Tyckte det var klockrent                                                                                           |
| A – Visa kundnummer och senaste faktura | customerNo och id läggs in i sökvägen utan encodeURIComponent | Träff                   | Samma problem som ovan, andra kan enkelt komma åt någon annans customerNo                                                                     | Den hade kunnat blanda denna med den tidigare kommentaren eftersom det bara är en annan synvinkel på samma problem |
| A – Visa kundnummer och senaste faktura | v-html="latestInvoice.message" ger XSS-risk.                  | Träff/Oavgjort          | Det stämmer att v-html används och att detta är en risk för XSS-attacker                                                                      | AI:ns lösningar är lite komplicerade, t.ex använd DOMPurify—det går bra att byta ut v-html mot {{}}                |
| A – Visa kundnummer och senaste faktura | fakturan laddas bara i onMounted.                             | Miss                    | Detta är ett icke-problem som egentligen bara distraherar från det egentliga problemet: att customerNo syns i URL:en. Inte värt att lösa.     | Den missade kontexten kring detta fel.                                                                             |
| A – Visa kundnummer och senaste faktura | felet i catch sväljs helt.                                    | Oavgjort                | Det är bra praxis att ha med felmeddelande, men detta bygger också på att kolla efter customerNo i själva länken, vilket inte är att föredra. | kontext.                                                                                                           |
| B – Snabbare fakturalista               |                                                               |                         |                                                                                                                                               |                                                                                                                    |
| C – Städa testdata                      |                                                               |                         |                                                                                                                                               |                                                                                                                    |

## Summering

|                | Antal |
| -------------- | ----- |
| Punkter totalt |       |
| Träff          |       |
| Miss           |       |
| Oavgjord       |       |

## Prompten (steg 5)

Regeln vi ändrade i systemprompten:

Blev den falska positiven i PR C kvar efter ändringen? Vad sa modellen nu?

## Vår regel

När litar vi på kommentaren, och vad gör vi när vi inte håller med?
