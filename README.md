# Plinko Pocket Sensemaker

A static workshop learning board built from one validated transcript graph. Start with five guided paths; explore the WebGL concept panels, drag to pin them, orbit/pan/zoom, or switch to readable 2D. Enable the separately sourced current-worldmap overlay for all 15 proposed SKU prices and gates. Selection reveals source/timestamp/quote and distinguishes transcript claims, interpretations and proposals.

## Run and reuse

Serve this directory as static files. No build, backend, database, credentials or model calls. Replace/import graph.json for a new bounded transcript, following ingestion.md and graph.schema.json. Source graph stays unchanged during layout changes. Session pins reset with Reset layout.

WebGL libraries: Three.js 0.183.2 and 3d-force-graph 1.80.1, MIT licensed, loaded through pinned jsDelivr/esm.sh URLs. The 2D renderer remains available if packages or WebGL fail. This public version requires network for those packages; the earlier standalone offline viewer remains a separate artifact.

The input contains 29 transcript concepts and 50 labeled propositions; a separate worldmap adds 15 SKU proposals and two analyst mappings. Quotes were validated upstream against the transcript. “Up to 30%” is a proposed promise, not measured savings; growth without breaking operations is prototype wording. The transcript has no named speaker attribution. Hash scope is Library-rendered source text, not original upload bytes. Layout distance and perspective do not establish causality or confidence.

Frameworks: https://cmap.ihmc.us/docs/theory-of-concept-maps and https://enterprise.design/wiki/Enterprise_Design_Facets . Worldmap source: https://worldmap.plinkosolutions.com/growth-map.js . No full raw transcript or internal account metadata is published.
