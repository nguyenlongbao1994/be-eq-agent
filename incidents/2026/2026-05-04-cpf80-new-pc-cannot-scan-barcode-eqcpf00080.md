---
id: INC-2026-05-04-CPF80-NEW-PC-CANNOT-SCAN-BARCODE-EQCPF00080
date: 2026-05-04
station: CPF
machine: EQCPF00080
model: C10.5
issue_type:
  - IT
  - Communication
  - Scanner
  - RS232
  - PC
status: Production restored / RS232-to-USB backup ongoing
owner: EQ / ME / IT
tags:
  - cpf80
  - new-pc
  - cannot-scan-barcode
  - rs232
  - scanner
  - fmxp
  - eqcpf00080
---

# N243 | CPF80_New PC cannot scan barcode

## Issue Description
- Issue: New PC cannot scan barcode
- Model: C10.5
- Station: Cpfilling
- Machine: EQCPF00080
- Impact: Output production
- Customer Impact: No impacts
- Containment Actions: N/A

## Timeline
- 03:00 25/04/2026
  - Machine stop, no production
- 20:50 02/05/2026
  - Turn on PC but fan is broken
- 20:30 04/05/2026
  - EQ installed new PC to replace
- 21:00 04/05/2026
  - New PC cannot scan barcode
- 02:40 04/05/2026
  - Replace PC CPF92 to restore production
  - New PC scan barcode normal

## Symptom
- New PC could not scan barcode.
- Production output was affected.
- The new PC was installed successfully, but scanner data could not be received correctly.

## FA & RC
1. Check lot packing program version, FmXP program and shared folder
   - Correct version and parameters
2. Check COM port connection
   - OK
3. Check sensor stop PCB
   - Detect normal
   - OK
4. Try using an RS232-to-USB converter for scanner
   - Scan barcode normal

### Conclusion
- The new PC’s RS232 port does not support transmitting scan data to the PC.

## Root Cause
- Program version, FmXP program, shared folder, COM port connection, and conveyor output sensor were all checked and found normal.
- The scanner worked normally when using an RS232-to-USB converter.
- Therefore, the issue was not caused by software setup, sensor, or standard COM-port connection setting.
- Root cause was identified as:
  - the new PC’s RS232 port did not support scanner data transmission to the PC.

## Failure Mechanism
- Barcode scanning on CPF80 depends on the scanner sending data to the lot-packing PC through RS232 communication.
- The newly installed PC could power on and run the correct software, but its built-in RS232 port did not properly receive / support scanner data transmission.
- Because the scanner data could not reach the PC, the barcode could not be scanned in normal production flow.
- When EQ replaced the lot-packing PC temporarily and later verified scanning through an RS232-to-USB converter, the barcode scan became normal again.
- This confirms the problem was specific to the RS232 hardware compatibility / support of the new PC.

## Corrective Actions
### Short term corrective action
1. Replace the lot packing PC from CPF92 to CPF80 machine to ensure production

### Long term corrective action
1. Using an RS232-to-USB converter for scanner of new PC → OK
2. Install new PC for CPF92 machine

## Next Steps
- Order additional RS232-to-USB converters as backup for future repair and replacement → On going

## Current Status
- Production was restored after replacing the lot packing PC from CPF92 to CPF80.
- New PC scanning was confirmed normal with RS232-to-USB converter.
- Backup converter ordering is on going.

## Impact
- Quality: no customer impact stated
- Production: output production affected until temporary PC replacement restored the line
- Safety: not stated in the slide
- Repeat risk: possible if future replacement PCs use RS232 ports with the same compatibility limitation and no converter backup is prepared

## Open Risk / Follow-up
- Need to ensure additional RS232-to-USB converters are available as backup
- Need to verify compatibility of future replacement PCs before installation
- Need to confirm stable operation of CPF92 after new PC installation

## Evidence
- Slide title: N243 | CPF80_New PC cannot scan barcode
- Description confirms:
  - Model: C10.5
  - Station: Cpfilling
  - Machine: EQCPF00080
  - Impact: Output production
  - Customer Impact: No impacts
- FA & RC confirms:
  - program version / FmXP / shared folder correct
  - COM port connection OK
  - sensor stop PCB detect normal
  - RS232-to-USB converter makes scan barcode normal
  - conclusion: new PC RS232 port does not support transmitting scan data to PC
- Corrective action confirms:
  - replace lot packing PC from CPF92 to CPF80
  - use RS232-to-USB converter
  - install new PC for CPF92
  - order additional converters as backup
