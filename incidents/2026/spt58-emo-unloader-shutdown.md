# SPT#58 – EMO Triggered Shutdown at Unloader

## 1. Basic Information
- Date: 2026-07-01
- Station: Sputter
- Model: C10.5
- Machine: EQSPT00058

## 2. Issue
Emergency alarm triggered → machine shut down completely.

## 3. Impact
- 2 sputter trays affected
- 336 pcs
- Customer impact: No impact

## 4. Timeline
- 30-Jun 20:20 → Perform FAI
- 1-Jul 04:43 → Machine shut down
- 1-Jul 05:00 → Check power & condition
- 1-Jul 06:10 → Detect EMO pressed at Unloader
- 1-Jul 07:30 → Machine recovery

## 5. Failure Analysis
1. Machine stopped due to emergency condition
2. Front cabinet power appeared disconnected
3. Rear power sources (380V / 220V) normal
4. Checked all EMO buttons
5. Found EMO pressed at Unloader position

## 6. Root Cause (CONFIRMED)
Operator pressed EMO button at Unloader.

## 7. Failure Mechanism
Operator presses EMO  
→ Safety circuit opens  
→ PLC detects unsafe condition  
→ All motion & power cut  
→ Machine enters emergency shutdown

## 8. Corrective Actions
- Restart machine → Done
- Run test with X-out tray → Done
- Remove 2 trays → PD visual + X-ray → wait ME confirm

## 9. Preventive Actions
- Check CCTV to confirm operator action
- Reinforce EMO usage training
- Consider EMO protection cover (avoid accidental press)

## 10. Risk Assessment
- Repeat risk: Medium (human-related)
- Equipment risk: Low
- Process risk: Low
- Safety: Normal function

## 11. Key Learning
EMO trigger is safety response, not equipment failure.

## 12. Next Step
Confirm via CCTV and feedback to production team
