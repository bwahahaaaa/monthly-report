Key Test Scenarios for EOD Reports (June 18 vs June 25 – Before vs After Fix)

1. Missing Exposure Validation
Test Case 1.1 – Missing exposure is shown for limit codes that didn’t have exposures saved in Sandra (Before Fix)
•	Dates: June 18, June 25
•	Expected Before Fix: Some exposure lines not flagged as missing even when exposures were not saved.
•	Expected After Fix: Same exposures now appear in Missing Exposure section.
•	Verify for:
o	GLOBAL OIL (INTRA_FICC_128, INTRA_FICC_129)
o	GAS & POWER (INTRA_FICC_126, INTRA_FICC_127)
o	Check if these VTDs appear in Missing Exposures Table in the after-fix EOD reports for June 25th.
Test Case 1.2 – Missing exposures are NOT reported on holidays
•	June 19 is a holiday for AMRS desks like xva_flow, americas_abs, etc.
•	Expected: No missing exposures reported for these desks on this date.
•	Verify in both EOD and Monthly reports that these VTDs don’t show up. (not directly verifiable via June 18/25 but confirm logic holds).

2. Breach Reporting Validation
Test Case 2.1 – All breaches saved in Sandra should appear in EOD
•	Before Fix: Global Oil Delta breach for INTRA_FICC_128 had multiple breaches on 18th — unacknowledged.
•	After Fix: June 25th – these breaches for same snaps (09:01 BST, 12:01 EDT, 16:30 EDT) are missing, but are correctly moved to Missing Exposure section instead.
•	Expected: Delta/Vega breaches should not appear if exposure is missing; they should be reported under Missing Exposure table.

3. Exclusion of Snapshots
Test Case 3.1 – Weekend snaps should not appear in reports
•	Expected: All snapshot times should be Mon–Fri only.
•	Check: Snap times in EOD reports are only business days (confirmed – no weekend snaps present in current data).
Test Case 3.2 – Early close handling (June has no early close)
•	Expected: All relevant snaps for VTDs present up to market close.
•	No early close to test here – skip this for June.

4. Measure Column Validation
Test Case 4.1 – EOD and Upload reports include “Measure” column
•	Expected: All breach entries should include Measure column (e.g., “Delta”, “Vega”)
•	Verified: Present in all 4 reports before and after fix for both Delta and Vega limits.

5. System-Approved vs No Approver Breach Review
Test Case 5.1 – System marks "No breach" records as System Approved
•	Expected: Non-breach records should have commentor = system and reviewed = Y
•	Before Fix: Present
•	After Fix: Present
•	Validated: Confirmed in both June 18th and 25th EOD reports — no-breach rows show “System Approved”.


