# Pracuj.pl Scraper: export to CSV or JSON with Python, Node.js or curl

Scrape Polish job postings from pracuj.pl: title, company, workplaces and address, salary per contract type, gross or net, position level, contract, schedule, remote or hybrid, category, technologies, requirements, benefits and dates. Search by keyword and city or paste URLs.

This repository has ready scripts for the [Pracuj.pl Scraper: Poland Jobs and Salaries | $0.50 per 1,000](https://apify.com/v0iddo/pracuj-pl-scraper) Actor on Apify. The Actor does the
fetching, paging and cleaning; the scripts here run it with your input and save the results as a CSV or JSON file.

## Quick start

1. Create an Apify account and copy your API token from
   [Console > Settings > Integrations](https://console.apify.com/settings/integrations).
2. Install the client and run the script with the example input:

```bash
pip install "apify-client>=2"
export APIFY_TOKEN=your_token
python run.py input.json -o results.csv --max-items 50
```

Edit `input.json` for your own run. You can also run the Actor in the browser on its
[Apify page](https://apify.com/v0iddo/pracuj-pl-scraper), schedule it there, and connect its output to Google Sheets, Slack, Zapier or Make.

## Input

The example input (`input.json`):

```json
{
  "keywords": [
    "księgowa"
  ],
  "location": "Warszawa",
  "includeDetails": true,
  "maxItems": 20
}
```

| Field | Type | What it does |
| --- | --- | --- |
| `keywords` | array | Job titles or words such as księgowa, kierowca or Java developer. |
| `location` | string | Optional city or town such as Warszawa, Kraków or Gdańsk. |
| `distanceKm` | integer | How far from the city postings may be. |
| `postedWithin` | string | Only postings published in that period. |
| `positionLevels` | array | Optional. Only these levels; empty means all. |
| `contractTypes` | array | Optional. Only these contract types; empty means all. |
| `workSchedules` | array | Optional. Only these schedules; empty means all. |
| `workModes` | array | Optional. Only these work modes; empty means all. |
| `salaryOnly` | boolean | Only postings that show a salary. |
| `searchUrls` | array | Search result pages copied from your browser, for example https://www.pracuj.pl/praca/kierowca;kw/gdansk;wp?rd=30 . |
| `includeDetails` | boolean | Read each posting's page for the salary per contract type, the workplace address, category, technologies, responsibilities, requirements, benefits and the de... |
| `maxItems` | integer | The run stops after this many result rows. |

## Output

One row per result. A real row from a run of the example input (more in
[`examples/sample-output.json`](examples/sample-output.json)):

```json
{
  "jobId": 1005204616,
  "groupId": "241c0000-56be-0050-38b6-08df3b78c449",
  "title": "Główna Księgowa/Główny Księgowy",
  "company": "CONTIGATE sp. z o.o.",
  "companyId": 1074173705,
  "companyUrl": "https://pracodawcy.pracuj.pl/company/1074173705",
  "companyLogo": "https://logos.gpcdn.pl/loga-firm/1074173705/7c4e0000-56be-0050-6bb0-08ddcf670837_280x280.png",
  "location": "Warszawa",
  "locations": [
    "Warszawa"
  ],
  "wholePoland": false,
  "city": "Warszawa",
  "region": "mazowieckie",
  "postalCode": null,
  "street": null,
  "latitude": null,
  "longitude": null,
  "salaryText": null,
  "salaryMin": null,
  "salaryMax": null,
  "salaryCurrency": null,
  "salaryInterval": null,
  "salaryKind": null,
  "salaries": [],
  "positionLevels": [
    "team leader",
    "manager"
  ],
  "contractTypes": [
    "employment contract",
    "B2B"
  ],
  "workSchedules": [
    "full time"
  ],
  "workModes": [
    "hybrid"
  ],
  "remote": false,
  "category": "Księgowość",
  "parentCategory": "Finanse / Ekonomia",
  "technologies": [],
  "responsibilities": [
    "nadzór nad procesami księgowymi realizowanymi przez zewnętrzne biuro rachunkowe; docelowo – prowadzenie rozliczeń i dokumentacji księgowej wewnątrz firmy",
    "weryfikacja poprawności dokumentów i rozliczeń księgowych",
    "zarządzanie płynnością finansową i monitorowanie cash flow",
    "przygotowywanie raportów, zestawień i analiz dla Zarządu",
    "koordynacja rozliczeń pomiędzy spółkami w grupie"
  ],
  "requirements": [
    "wykształcenie wyższe kierunkowe (rachunkowość, finanse, ekonomia)",
    "minimum 5 lat doświadczenia w pełnej księgowości",
    "doświadczenie na stanowisku głównej księgowej/głównego księgowego lub zastępcy",
    "doświadczenie w zarządzaniu zespołem",
    "bardzo dobra znajomość przepisów podatkowych i ustawy o rachunkowości"
  ],
  "niceToHave": [
    "doświadczenie we współpracy z zewnętrznym biurem rachunkowym"
  ],
  "benefits": [
    "realny wpływ na organizację procesów finansowo-księgowych",
    "samodzielne stanowisko z bezpośrednią współpracą z zarządem",
    "stabilne zatrudnienie w rozwijającej się grupie spółek",
    "możliwość uporządkowania i budowania procesów adekwatnie do skali biznesu"
  ],
  "immediateStart": true,
  "oneClickApply": true,
  "directEmployer": true,
  "promoted": false,
  "postedAt": "2026-11-05T20:14:01Z",
  "firstPostedAt": "2026-11-05T20:14:01Z",
  "expiresAt": "2026-12-05T22:59:59Z",
  "summary": "- Masz minimum 5 lat w pełnej księgowości i doświadczenie na stanowisku głównej księgowej/zastępcy.\n- Potrafisz nadzorować i docelowo prowadzić procesy księgowe oraz weryfikować rozliczenia i dokumenty.\n- Masz doświadczenie w przygotowywaniu sprawozdań finansowych i raportów z...",
  "descriptionText": "Twój zakres obowiązków\n\n- nadzór nad procesami księgowymi realizowanymi przez zewnętrzne biuro rachunkowe; docelowo – prowadzenie rozliczeń i dokumentacji księgowej wewnątrz firmy\n- weryfikacja poprawności dokumentów i rozliczeń księgowych\n- zarządzanie płynnością finansową i...",
  "language": "pl",
  "url": "https://www.pracuj.pl/praca/glowna-ksiegowa-glowny-ksiegowy-warszawa,oferta,1005204616",
  "scrapedAt": "2026-11-06T02:40:59Z"
}
```

Fields: `jobId`, `groupId`, `title`, `company`, `companyId`, `companyUrl`, `companyLogo`, `location`, `locations`, `wholePoland`, `city`, `region`, `postalCode`, `street`, `latitude`, `longitude`, `salaryText`, `salaryMin`, `salaryMax`, `salaryCurrency`, `salaryInterval`, `salaryKind`, `salaries`, `positionLevels`, `contractTypes`, `workSchedules`, `workModes`, `remote`, `category`, `parentCategory`, `technologies`, `responsibilities`, `requirements`, `niceToHave`, `benefits`, `immediateStart`, `oneClickApply`, `directEmployer`, `promoted`, `postedAt`, `firstPostedAt`, `expiresAt`, `summary`, `descriptionText`, `language`, `url`, `scrapedAt`.

## Node.js

```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: process.env.APIFY_TOKEN });
const run = await client.actor('v0iddo/pracuj-pl-scraper').call({"keywords": ["księgowa"], "location": "Warszawa", "includeDetails": true, "maxItems": 20});
const { items } = await client.dataset(run.defaultDatasetId).listItems();
```

Full example: [`examples/node/run.mjs`](examples/node/run.mjs).

## Any language: one HTTP request

```bash
curl -X POST "https://api.apify.com/v2/acts/v0iddo~pracuj-pl-scraper/run-sync-get-dataset-items" \
  -H "Authorization: Bearer $APIFY_TOKEN" -H 'Content-Type: application/json' \
  -d '{"keywords": ["księgowa"], "location": "Warszawa", "includeDetails": true, "maxItems": 20}'
```

The response is the JSON array of results.

## Cost

The Actor is paid per result: **$0.50 per 1,000 results**, nothing per run. `maxItems` caps the rows, and so the cost, of one run. A new Apify account gets $5 of platform credit every month.

## License

MIT for the code in this repository. Made by [vøiddo](https://voiddo.com).
