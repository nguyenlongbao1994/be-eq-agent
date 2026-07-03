# BE EQ Incident Register

This folder stores all validated incidents captured from BE EQ line follow-up, training, and troubleshooting history.

## Rule
- One incident = one markdown file
- Use only validated information
- If a date is not confirmed, do not force a date
- Update status when the issue is closed or monitoring is completed

---

## Master Incident Register

| Incident ID | Date | Station | Machine / Area | Issue | Issue Type | Status | File |
|---|---|---|---|---|---|---|---|
| INC-2026-06-01-LASER232-PANELDROP | 2026-06-01 | Laser / Lift interface | #232 | Panel dropped due to missing lift abnormal signal transfer | Sensor / Control / Transfer | Open learning / follow-up | [View](./2026/2026-06-01-laser232-panel-drop.md) |
| INC-2026-06-18-LASER222-COLDJET | 2026-06-18 | Laser | #222 | Cold Jet out of spec, recovered after adjustment, FAI OK | Process / Dry Ice | Monitoring complete at check point | [View](./2026/2026-06-18-laser222-coldjet-out-of-spec.md) |
| INC-2026-06-18-WC-CARRIERQR | 2026-06-18 | Water Clean | Carrier / scanner | Carrier QR code inconsistency, scanner replacement not yet available | Detection / Scanner / Process | Open | [View](./2026/2026-06-18-wc-carrier-qr-inconsistency.md) |
| INC-2026-06-18-JIGSAW-CODEREAD | 2026-06-18 | Jigsaw | Product code reading | Product code read NG, note points to surface / DIC cleanliness | Detection / Surface / Process | Open | [View](./2026/2026-06-18-jigsaw-code-read-ng.md) |
| INC-2026-06-22-LASER-DUSTHOSE | 2026-06-22 | Laser Cutting | Dust collector line | Dust collector hose bent | Utility / Exhaust | Open | [View](./2026/2026-06-22-laser-dust-collector-hose-bent.md) |
| INC-2026-06-22-SPUTTER-LOOSESCREW | 2026-06-22 | Sputter | Reassembled part | Screw loose after reassembly | Mechanical | Closed by later screw replacement | [View](./2026/2026-06-22-sputter-loose-screw-after-reassembly.md) |
| INC-2026-06-23-WC79-SCANNERCONN | 2026-06-23 | Water Clean | WC79 | Scanner connection abnormality | Sensor / Connection / Detection | Open | [View](./2026/2026-06-23-wc79-scanner-connection.md) |
| INC-2026-06-23-SAW58-HANDLING | 2026-06-23 | Saw / Jigsaw | Saw 58 | Handling / output-side issue noted | Mechanical / Transfer | Open | [View](./2026/2026-06-23-saw58-output-handling-issue.md) |
| INC-2026-06-24-MOLD146-PINDROP | 2026-06-24 | Molding | Mold 146 | Pin dropped, risk to mold chase | Mechanical / Mold | Monitoring | [View](./2026/2026-06-24-mold146-pin-drop.md) |
| INC-2026-06-24-CPF-ZAXIS | 2026-06-24 | CPF | Z-axis | Z-axis abnormality | Mechanical / Control | Open | [View](./2026/2026-06-24-cpf-z-axis-abnormal.md) |
| INC-2026-06-24-LASERCB-PCBMARK | 2026-06-24 | Laser CB / Hades auto line | Laser CB | Cannot detect PCB mark | Vision / Detection / Automation | Open | [View](./2026/2026-06-24-hades-lasercb-pcb-mark-detect-ng.md) |
| INC-2026-06-24-TDIC43-VACUUM | 2026-06-24 | TDIC | #43 | Vacuum / dust filter issue | Utility / Vacuum / Cleaning | Open | [View](./2026/2026-06-24-tdic43-vacuum-dustfilter.md) |
| INC-2026-06-25-PLASMA2-BASE | 2026-06-25 | Plasma 2 Automation | Base / machine install | Base orientation reversed and required modification | Mechanical / Installation / Automation | Open until modification completed | [View](./2026/2026-06-25-plasma2-base-reverse-direction.md) |
| INC-2026-06-25-WC37-PRESSUREDROP | 2026-06-25 | Water Clean | WC37 | Pressure drop observed, nozzle not clogged | Utility / Flow / Pressure | Open | [View](./2026/2026-06-25-wc37-pressure-drop.md) |
| INC-2026-06-25-LASER-COOLINGCONNECTOR | 2026-06-25 | Laser | Cooling water connection | Cooling water connector broken by handling, replaced and recovered | Human / Mechanical / Utility | Closed after replacement | [View](./2026/2026-06-25-laser-cooling-water-connector-broken.md) |
| INC-2026-06-26-COLDJET22-UNSTABLE | 2026-06-26 | TDIC / Dry Ice | Cold Jet #22 | Output / weight drops below spec without HW/SW change | Process / Utility / Intermittent | Open monitoring | [View](./2026/2026-06-26-coldjet22-output-instability.md) |
| INC-2026-06-26-LASERCB-HIGHCT | 2026-06-26 | Laser CB | One unit | High CT contribution by one machine | Process / Vision / Throughput | Open | [View](./2026/2026-06-26-lasercb-high-ct.md) |
| INC-2026-06-26-PLASMA3-SFIS | 2026-06-26 | Plasma 3 | SFIS integration | SFIS software not fully fixed / not ready | IT / Integration / Traceability | Open | [View](./2026/2026-06-26-plasma3-sfis-not-ready.md) |
| INC-2026-06-29-MOLD147-P2 | 2026-06-29 | Molding | Mold 147 / Press 2 | Abnormal during cleaning while preparing for Automation Hades FRB | Mechanical / Mold / Cleaning | Open investigation | [View](./2026/2026-06-29-mold147-press2-cleaning-abnormal.md) |
| INC-2021-11-04-MOLDING-EQMLD00147-TABLE-ROTATION-DAMAGE | 2021-11-04 | Molding | EQMLD00147 / Table rotation | Table rotation move error caused 1 panel damage after lift position / panel detection abnormality | Mechanical / Sensor / Transfer / Control | Monitoring | ./2021/2021-11-04-molding-eqmld00147-table-rotation-panel-damage.md |
---

## Notes
- Incidents listed here are based on validated issue history from the chat.
- Training-only knowledge should stay in `knowledge_db.md` and `troubleshooting.md`, not inside this incident register unless it became a real issue.
