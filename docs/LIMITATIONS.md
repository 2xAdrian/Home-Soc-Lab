# Scope and limitations

- **Single host:** All components were on one Windows VM; there was no enterprise telemetry aggregation.
- **Limited test set:** Five controlled Atomic Red Team scenarios were used. ATT&CK technique IDs describe categories much larger than these individual tests.
- **Parsing:** The source build log describes a field extraction problem and leaves its final persistent configuration incomplete; searches should be tested against current ingestion behavior.
- **False positives:** Individual benign examples were tuned; the planned 1–2 day normal-use test is not marked completed.
- **Safety / Defender:** Some simulations were blocked or needed temporary lab-only exclusions. No such exclusion is recommended for a production endpoint.
- **No production promises:** Detections and source code here are educational examples, not deployable production controls.
- **Public-source privacy:** Screenshot assets must be reviewed for personal names, hostnames, IPs, secrets, keys and usernames before publication. Original DOCX reports and raw logs are intentionally not included.
- **Attribution:** Source files contain a conflicting author credit; ownership and permission to publish must be confirmed first.
