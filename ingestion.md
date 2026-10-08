# Plinko Pocket Sensemaker — bounded ingestion

One transcript produces one graph. Never merge with earlier transcripts. The browser performs no extraction, enrichment, API calls or billing operations. No billing cap is configured. Keep confidential inputs and artifacts offline unless their owner authorizes a Library upload.

## Deterministic preparation

Accept UTF-8 text, Markdown, VTT or SRT. Hash original bytes with SHA-256; retain filename, byte count and hash. Normalize CRLF to LF for segmentation but retain original bytes. VTT/SRT: one segment per cue, timestamp from cue, remove cue markup as text only. Text/Markdown: one segment per nonempty paragraph; record start/end line numbers and null timestamps unless timestamps are explicitly present. Assign `seg-000001` onward in source order. Preserve literal speaker labels; when absent use null, never infer names. The source hash identifies a single input, not truth or confidence.

Proposed workflow controls: default ceiling 20,000 input tokens (count using the selected model's tokenizer before extraction), 100,000 characters and 2,000 segments; at most 40 transcript concept nodes and 60 transcript relationships; exactly five narrative stops. A separately sourced overlay may add at most 15 SKU nodes and two analyst mappings. Renderer safety limits are 60 total nodes, 100 total edges, 160 evidence records, 600 characters per evidence quote, 180 characters per label and 1.5 MB JSON. Stop and ask the owner to narrow scope or explicitly approve chunking on overflow. Do not silently summarize away missing parts, truncate, or automate repeated batches. These proposed controls are not an implemented API or global account billing cap.

## Reusable extraction prompt

You are Plinko Pocket Sensemaker. Use only the supplied transcript segments to create one bounded consultant-readable concept map under the supplied JSON schema. Do not browse, call external APIs, infer unnamed speakers, or analyze other transcripts. Extract meaningful propositions: node label + edge linking phrase + node label must form a readable sentence. Prefer a small core map with meaningful cross-links; group related nodes into named clusters. Optional EDGY lenses are Identity, Experience and Architecture, not mandatory categories. Use frontstage/backstage service-blueprint tags only where supported.

Separate statuses: `explicit` means directly supported by the transcript; `interpretation` means analyst inference and must explain its inference; `proposal` means suggested future design, not an implemented result. Every explicit node/edge requires evidence IDs. Evidence must be a short exact contiguous quote, source ID, deterministic segment ID, source timestamp (or null), and speaker label (or null). Preserve disagreement and uncertainty in assumptions and contradictions. Do not convert predictions or estimates into outcomes. Worldmap overlays, if explicitly supplied, have their own source and cluster; preserve exact names/stages/estimates. Connections from transcript concepts to SKUs are proposals unless directly stated. Do not use a worldmap source as transcript evidence.

Create exactly five succinct guided stops for Nate: claim, selected ordered edge IDs, supporting evidence IDs, and a practical question. Explain the two or three central paths before optional proposals. Mark illustrative inputs as illustrative. Output JSON only. If overflow or insufficient source support prevents compliance, stop and report the blocker instead of fabricating data.

## One evidence validation

Run one evidence-review pass after source extraction over saved graph and supplied segments: schema, unique IDs, references, one transcript ID/hash, quote exactness, timestamp agreement, explicit proposition support, interpretation/proposal distinctions, contradictions, and tour claim support. Record validation results, checked evidence IDs and unresolved issues. Allow at most one bounded schema repair, then stop/ask if unresolved. No model escalation or web enrichment by default. Preserve the cached dataset for layout changes instead of reextracting. Static rendering begins only after owner-approved validation. All later navigation, filtering, layout, import/export and rendering are deterministic.

## Files and use

Open `explorer.html` directly in a modern browser. Import the validated JSON; use Guided presentation first, then Explorer. JSON export preserves the dataset. Excalidraw export creates editable concept boxes, relationship arrows and text from that same graph; its diagram is a reading aid and does not encode evidence depth or causality. A new import replaces the current graph; there is no cumulative database.

Framework references: [IHMC concept-map theory](https://cmap.ihmc.us/docs/theory-of-concept-maps) for linking phrases and propositions; [EDGY facets](https://enterprise.design/wiki/Enterprise_Design_Facets) for optional overlapping lenses. Perspective geometry is only a navigation aid and provides no proof of analytical depth or simulated causality.