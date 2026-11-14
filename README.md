# Invoice totals check — free n8n workflow (demo)

Loupe & Lettres — créé avec l'aide de l'IA (created with AI assistance). This repository was published by an AI assistant for the Loupe & Lettres brand.

A free, MIT-licensed n8n workflow that checks the totals of ONE invoice with integer arithmetic before you send it: line amounts, VAT per rate, totals, a comparison with the total you expected, a suggested next number and a printable HTML page. It is manual, adds no node that sends or stores data, and needs no account, credential, API, PDF service or AI model.

## Why it exists

The same fictional invoice gives a total of **60.30** when VAT is rounded once per rate and **60.31** when VAT is rounded on each line. Pick the rule your accounting system uses, then let the check tell you when a generated total disagrees with the one you expected.

## Try it in 2 minutes

1. Import `invoice-totals-check.json` into a fresh n8n workflow.
2. Execute it manually and open the output of `Compute invoice`.
3. Compare with `expected/per_group.json` (net 50.28, VAT 10.02, total 60.30, `check.matches: true`). Set `vatRounding` to `per_line` and you get 60.31 (`expected/per_line.json`).
4. Replace the object returned by the `Example invoice` node with your own invoice (`fixtures/example.json` shows the fields).

## Limits, stated plainly

- **No counter is stored.** `suggestedNextNumber` only increments the trailing digits of the number you give it (`F-2026-0007` gives `F-2026-0008`). It does not reserve a number or guarantee uniqueness.
- A mismatch with `declaredTotal` is reported in the JSON field `check`, not blocked automatically. The HTML page does not show that check.
- The HTML is a printable layout, not a legal invoice validator. Not accounting or tax advice. EUR, USD, GBP and CHF only.
- Tested by command-line import and execution in n8n 2.14.2 (the example, the alternative rounding mode, an invalid input). Not tested: interface import, n8n Cloud, other n8n versions, browser PDF printing.
- Your n8n instance may keep inputs and outputs in its execution history; keep your first run fictional.

## More

- French product page (free, pay-what-you-want): https://loupeetlettres.gumroad.com/l/solzpy
- Paid pack of administrative n8n workflows for freelancers (French): https://loupeetlettres.gumroad.com/l/ynqrgw

MIT license (see `LICENSE.txt`). No endorsement by n8n is claimed.
