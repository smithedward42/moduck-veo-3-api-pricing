# Veo 3 API Pricing: Current Access and Per-Video Cost Math

![An obsolete video API route is disconnected beside a documented route, with a clock leading to a cost estimate.](cover.png)

*Check the active model route before turning output seconds into a per-video planning cost.*

A Veo 3 price row can still appear in a pricing table even though the API model ID behind it has been retired. Google’s [Gemini API deprecations page](https://ai.google.dev/gemini-api/docs/deprecations) lists `veo-3.0-generate-001` and `veo-3.0-fast-generate-001` as shut down on June 30, 2026. For a new integration, check the exact platform and model ID before using any quoted “Veo 3” rate; a retired ID cannot serve the planned workload.

For a new Google Cloud Veo budget, the useful comparison is a currently documented Veo 3.1 GA model at a fixed resolution and audio setting. Multiply its public output-second rate by the seconds and number of generated videos, then allow for the proportion your application actually accepts. That produces a **list-rate planning equivalent**, not a confirmed account invoice: availability, quota and consumption terms still need checking.

This guide uses public Google documentation checked on October 29, 2026. It explains why old Veo 3 search results can mislead, compares four like-for-like 1080p Veo 3.1 rates, and shows what turns an eight-second clip price into a usable-output budget. No video was generated for this article.

## Check the model ID before the rate

“Veo 3 API” can refer to a model family, a particular version, or an access platform. Those are different purchasing questions. Google’s Gemini API retirement schedule applies to its 3.0 model IDs; its [Veo guide](https://ai.google.dev/gemini-api/docs/veo) labels Veo 3 and Veo 3 Fast deprecated and says the Veo 3.1 preview IDs were shut down on October 22, 2026. A quote copied from a 2025 Veo 3 announcement therefore cannot establish that a new Gemini API request will work today.

The current Google Cloud price page still has Veo 3 rows. Read those as published rows, not proof that a retired ID is available. Google's [Cloud Veo 3.1 model page](https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/veo/3-1-generate) instead lists the GA IDs `veo-3.1-generate-001` and `veo-3.1-fast-generate-001`. It documents 4-, 6- and 8-second outputs and up to four output videos per prompt for these models. It lists `us-central1` as the supported region for these GA entries; confirm feature and account eligibility for that route.

One billing caveat matters before the price table: the Cloud model page marks Provisioned Throughput and fixed quota as supported, but Batch inference and Pay-as-you-go as not supported for those GA entries. The public unit-price rows below are therefore a consistent comparison tool; they are not evidence that every account can buy a clip on a simple self-service, pay-per-second basis. Confirm the applicable Cloud consumption arrangement and its commercial terms before forecasting an invoice. A provider or aggregator quoting “Veo 3” also needs to name its own model ID, route and contract.

## Compare one video specification at a time

Google Cloud’s [Veo pricing page](https://cloud.google.com/model-garden/pricing) lists USD rates per `count` by model, resolution and whether the output includes audio. Google’s [supported-models documentation](https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/provisioned-throughput/supported-models?hl=en) also describes Veo output usage in video seconds. The table converts selected **1080p, eight-second, one-output** Veo 3.1 rates into comparable list-rate equivalents. It is not a quote for the retired 3.0 Gemini API IDs or for a reseller.

| Google Cloud GA option, 1080p | Listed rate per output second | Eight-second list-rate equivalent |
| --- | ---: | ---: |
| Veo 3.1, video + audio | $0.40 | $3.20 |
| Veo 3.1, video only | $0.20 | $1.60 |
| Veo 3.1 Fast, video + audio | $0.12 | $0.96 |
| Veo 3.1 Fast, video only | $0.10 | $0.80 |

Each last-column value is simply **8 × listed rate**. Audio is a material cost choice: for the same standard Veo 3.1 row, the public video-plus-audio rate is twice the video-only rate. Fast has lower listed rates for these 1080p rows, but the table does not measure visual quality, speed, acceptance or feature parity for your prompts. Pick the cheapest option only after it passes the output requirements of the application.

The comparison deliberately holds duration and resolution constant. A four-second 720p clip, a 4K clip, or multiple videos from one prompt belongs in a new calculation using its own supported configuration and rate row. Do not compare a per-video reseller quote with a Google per-output-second row until the quote says how many outputs, seconds, retries, audio tracks and other charges it covers.

## Budget for generated outputs, then accepted clips

For a selected rate, start with the generated output:

**List-rate equivalent = generated output videos × seconds per video × listed rate per output second.**

At the $0.40 standard Veo 3.1 video-plus-audio rate above, one eight-second output is $3.20 on that basis. If a request produces three eight-second outputs, the equivalent is **3 × 8 × $0.40 = $9.60** before any separate terms or costs. Count outputs, not just prompts; the Cloud model page allows up to four output videos per prompt. This is still planning arithmetic, not a claim about your account's exact invoice or whether a failed operation is charged.

![Five generated video clips each carry a cost marker; three pass a review gate and two go to revision.](generated-vs-accepted.png)

*Conceptual example: generated clips and accepted clips are different counts. The illustration is not a measured acceptance rate or billing rule.*

Next ask how many generated clips actually meet the product’s bar. Suppose, purely as a budgeting scenario, that 80% of generated eight-second outputs meet the app’s acceptance bar and that each output is charged at the list-rate equivalent. At a $3.20 list-rate equivalent for each generated clip, the expected cost per accepted clip is **$3.20 ÷ 0.80 = $4.00**. At 50% acceptance, it would be $6.40. Neither acceptance rate was measured here; replace the assumption with your own evaluation data. A lower listed second rate can lose its apparent advantage if the accepted-output yield is materially lower.

This method also exposes what the published unit rate does not answer. Your bill may depend on a fixed-quota or reserved-throughput arrangement, any separate storage or workflow charges, and how your agreement treats unsuccessful, filtered or repeated jobs. The comparison should therefore have two columns in your own budget: a public list-rate equivalent for model alternatives, and an account-specific invoice estimate confirmed from applicable terms.

## Choose the route that survives the access and cost checks

Use the published Veo 3.1 numbers to shortlist a configuration, then check the route itself before committing. A direct Google Cloud route is a sensible first candidate when its GA model, supported region, feature set and consumption arrangement fit the app. An intermediary is worth evaluating when its actual model access, billing and integration terms solve a need you have; its public description alone does not prove the same output or price.

For each candidate, record five items for one representative video task:

1. Exact platform and model ID, including whether the endpoint is active for your account.
2. Requested duration, resolution, aspect ratio, number of outputs and whether audio is required.
3. Listed charge unit and all chargeable output seconds; check any provider-specific minimums or bundled charges.
4. Actual quota, throughput or contract path, plus treatment of failed and repeated jobs.
5. Accepted-output share from your own permitted evaluation, and the maximum cost per accepted clip your product can carry.

The choice changes if an ID retires, a model or region is unavailable, your audio or resolution requirement changes, or the measured acceptance rate differs from the scenario above. Recheck the current Google pages and account terms at purchase time. A rate table cannot replace those checks.

Moduck publishes this article and is an AI API aggregator for developers and product teams. Its stated goal is to make model discovery and pricing information easier to understand; this article does not establish that Veo 3.1 is callable through Moduck, that its rate matches Google Cloud's, or that it will lower your effective cost. If an aggregator is still on your shortlist, look in Moduck’s documentation for the exact Veo model and billing terms you need before requesting a key. [Read the documentation](https://docs.moduck.ai/). Check model and pricing details before signing in or requesting a key.

All numerical examples here are derived from public list rows checked on October 29, 2026. No account, API key, generated video, invoice or payment was involved.
