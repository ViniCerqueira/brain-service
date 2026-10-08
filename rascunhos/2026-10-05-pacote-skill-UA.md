## Design clarifications — confirmed corrections

Each item was established against a primary source during the Ukraine build and support cycle
(tickets HRBS-12181, HRBS-12631, HRBS-14331, SR-160/162/163, SR-414 and a research chat of
2026-10-01). `(engine)` means it changes a calculated amount. Source of this pack: the Brain
Service hub for Ukraine and its corrections register; no country skill existed when it was written.
Artefact versions in force when written: WTC V4.1, CCG V1.5, DD V3.10 (highest version cited).

1. **Life insurance is subject to USC/ESV; only medical and pension insurance are exempt. (engine)**
   Resolution/Poryadok No. 1170, para. 2, section II exempts from ESV only medical and
   pension insurance.
   **The mistake:** USC = No for life insurance (answered that way in HRBS-12181). Correct: USC =
   Yes. Origin: HRBS-14331 (also touches HRBS-12181).

2. **Benefit-in-kind gross-up (coefficient 1.219512) applies to the PIT base only. (engine)**
   Art. 164.5 PKU; Military Levy and USC on BIK are computed on the gross value, with no coefficient
   (para. 16-1, sub-para. 10, section XX PKU). Worked example: value 2,000 -> PIT base 2,439.02,
   PIT 18% = 439.02, Military Levy 100 on 2,000.
   **The mistake:** a PIT base of 2,360 (PIT 439.03) in the earlier example; and a separate "PIT without
   Military Tax" wage-type series, which has no legal basis (it is a difference of base, not of
   incidence). The PIT/Military split is an engine rule, not a Formula-column entry. Origin: HRBS-12181.

3. **Gross-up scope is non-monetary benefits only, limited to 20 pay elements. (engine)**
   Subpara. 164.2.17 PKU; subparas. 14.1.47/14.1.48 PKU. A cash payment tied to remuneration is
   salary (4DF 101), not BIK.
   **The mistake:** applying the gross-up to all 109 codes with 4DF = 126. Origin: HRBS-12181 (WTC v3.8).

4. **WT 65894 (grossed-up PIT) does not exist and must not be created.**
   The difference is one of base (PIT x 1.219512; Military/USC gross value), not of flags.
   **The mistake:** the changelog stated the line had been created. New pay elements enter the WTC
   without a code; the code is assigned afterwards. Origin: HRBS-14331.

5. **Monthly bonus compensation (62209) divides by 0.82, not 0.77. (engine)**
   Reasoning on Art. 164.5 PKU. A requested 0.77 was rejected. Origin: HRBS-14331.

6. **Salary proration uses working days of the schedule, not calendar days. (engine)**
   Labour-authority letter (Держпраці) of 27.05.2019 No. 4340 and Ministry of Social Policy
   letter (Мінсоцполітики) of 15.04.2019 No. 553.
   **The mistake:** calendar-day proration citing Art. 115 (which governs payment timing, not
   proration). A worked holiday or weekend counts as a full day in the bonus proration
   (Poryadok 100 p. 3; LC Art. 107). Origin: HRBS-12631 (CCG v1.2), HRBS-14331.

7. **The ESV minimum base does NOT apply pro rata in the month of hire or termination. (engine)**
   Instruction 449, section III: ESV is levied on actual pay.
   **The mistake:** a prorated minimum base (8,647 x 21/31). Origin: HRBS-12631 (CCG v1.2).

8. **Employees with disability: ESV 8.41% on actual pay, with no top-up to the minimum base. (engine)**
   Instruction 449, section III; State Tax Service answer of 04.02.2026.
   **The mistake:** pseudo-code and dev note completed the minimum base for disabled employees; the
   pseudo-code must exclude is_disabled. Origin: HRBS-12631 (CCG v1.2).

9. **PDFO/Military Levy deadline is the time of transfer for bank-paid salary.**
   TCU Art. 168.1, confirmed by the tax authority. Three banking days applies only to cash or
   non-monetary income.
   **The mistake:** presenting "3 banking days" as universal. Origin: HRBS-12631 (CCG v1.2).

10. **Average earnings are two calculations (12 months and 2 months), and sick leave is a third regime. (engine)**
    Vacation: 12 months (Poryadok 100 p. 2); donor leave and business trip: 2 months, trip pays
    the higher of the average and the month's daily rate (Poryadok 100 section 8; LC Art. 121 para. 4;
    LC Art. 124); sick leave: Postanova 1266 (not the vacation formula); indexation: Procedure
    1078 (base month plus cumulative index, not an average).
    **The mistake:** one 12-month formula for all. Origin: HRBS-12631 (CCG v1.1); see Open items for the
    sick-leave period.

11. **The vacation exclusion list is separate from the sick-leave one. (engine)**
    Poryadok 100, p. 3, sub-p. 4: childcare leave up to 3 years, unpaid leave, suspension of the
    contract due to war, military service without retained average, months without data.
    Sick leave and maternity leave stay in the vacation average.
    **The mistake:** CCG 8.2 applied the 1266 exclusion list to vacation. Origin: HRBS-14331.

12. **Compensation for unused leave (79401) recalculates a fresh 12-month average at termination. (engine)**
    Poryadok 100, p. 2, second paragraph.
    **The mistake:** citing it as "sub-para. 3". Origin: HRBS-14331.

13. **Birthday gifts: PIT/Military = No, 4DF 160; the excess over the limit is reported as 126. (engine)**
    Para. 165.1.39 PKU; non-taxable part = 25% of the minimum wage as of 1 January.
    **The mistake:** PIT/Military = Yes/Yes. Origin: HRBS-14331 (and HRBS-12181 for 160/126).

14. **Civil contractors (FOP with registration proof): PIT/Military/USC = No, 4DF 157, WT 62942. (engine)**
    Para. 177.8 PKU.
    **The mistake:** Yes/Yes/Yes. Origin: HRBS-14331.

15. **Per diem: the amount inside the cap is not taxable; the cap was not applied. (engine)**
    Subpara. 170.9.1 PKU. 2026 caps: UAH 864.70 per day domestic (0.1 x minimum wage of 1 January,
    8,647); EUR 80 per day foreign at the NBU rate of the day. Excess is taxed with PIT/Military and
    the 1.219512 gross-up.
    **The mistake:** a fixed PIT/ML = Yes with no cap. The cap logic belongs in the Formula column.
    Origin: WTC research chat of 2026-10-01 and HRBS-14331.

16. **Stock options: 4DF 101 with ESV = No is invalid in any scenario. (engine)**
    PKU and Law 2464. Treatment depends on recharge: with recharge, 4DF 101, ESV Yes, gross-up 1.219512
    on PIT, Military Levy on the nominal. Origin: WTC research chat of 2026-10-01.

17. **Documented representation expenses and advertising costs are exempt from PIT.**
    Art. 170.9 PKU. Both 65806 and 65808 were PIT = Yes as configured; whether either is documented
    advertising spend was put to the client. Origin: HRBS-12181 (still open, see Open items).

18. **The Pension Fund of Ukraine replaced the Social Insurance Fund from 2023-01-01.**
    **The mistake:** the CCG cited the Social Insurance Fund. Origin: HRBS-14331. (No official source
    recorded.)

19. **4DF and D1 are monthly for legal entities from 2026-01-01; only FOP is quarterly.**
    Law 4536-IX; MinFin Orders 4/243/284.
    **The mistake:** quarterly 4DF. Origin: HRBS-12631 (CCG v1.2).

20. **Statutory reports are built in Ukrainian and carry the header tags.**
    D1, D5, D6 and 4DF are annexes of form J05 (011/012/013 -> HZ/HZN/HZU with C_DOC_STAN 1/2/3).
    **The mistake:** specs without HBOS/HBUH tags (and the header tags on D5/D6). The tags were added
    from the DPS schema; chief_accountant_name in the DD feeds HBUH. Origin: SR-160/161/162/163.

21. **D5 is event-driven (seven event types).**
    Report Matrix, section 5 p. 34.
    **The mistake:** reading the trigger as "start date inside the period only". Origin: SR-162.

22. **D6 validates against form J0510611 (v11), in force from 2026-07-17, not v10.**
    **The mistake:** the sample was validated against the superseded v10. Origin: SR-163.

23. **Part-Time Indicator is Mandatory with no default.**
    **The mistake:** CM (conditional mandatory) with an automatic default. Origin: SR-160.

24. **1-PV "staff" is the Labour Registry Person Category (D5) 1-2; category 3 (civil-law) is excluded.**
    Derzhstat order r. 1070.
    **The mistake:** mapping staff by Employment Contract Type. Origin: SR-414. The quarterly 1-PV is
    XML template S0301121, signed with a qualified e-signature (KEP), electronic only, through the
    Respondent's Cabinet (Кабінет респондента), Law 2524-IX art. 10(4). Origin: SR-415.

25. **Research on USC/ESV must use the primary law, not secondary articles.**
    **The mistake:** several blog sources agreed on a wrong USC/ESV answer while the primary law had
    reverted. Origin: USC incident, research chat of 2026-10-01.

## Open items

- Sick-leave calculation period: 6 months (HRBS-14331, WTC columns K/X, Postanova 1266 p. 4) versus
  12 months (HRBS-12631, HRBS-13392, and the sick-leave rules text added to the guide in HRBS-14331
  itself). Not resolved; do not publish a period until confirmed.
- Sick-leave payout tiers by insurance record: HRBS-13389 (under 5 years 60%, 5-8 80%, 8+ 100%)
  versus HRBS-14331 (under 3 years 50%, 3-5 60%, 5-8 70%, over 8 100%). It is not known which entered CCG V1.5.
- 4DF 128 for maternity: the local specialist says 128 is only for the 126 + 14 days sick-leave
  maternity case and that 65700-65712 should be 101 or 126; this contradicts the CCG.
- WT 65808 label: HRBS-12181 and WTC v3.8 name it Representation expenses (financial), 65810 is Life
  insurance; HRBS-14331 calls 65808 "Life Insurance (BIK)" and our reply reused that label.
- Maternity: 22% ESV and exemption from PDFO/Military Levy are recorded, but classification of
  maternity and 65805/65809 (4DF 126 -> 125) await the client.
- Stock options: scenario A/B and recharge handling depend on client or global-team input.
- Severance 62180/62181 outside the ESV base; per diem inside/outside the cap for 62570,
  65570-65572, 65580-65582, 62965 (double-taxation risk): asked after the ticket was Resolved, unanswered.
- Final design of the BIK gross-up: engine rule versus aggregated pay element 58134 (never built).
- Statutory values still without an official source in the hub: PIT 18%, Military Levy 5%, ESV 22%,
  minimum wage UAH 8,647, ESV maximum base UAH 172,940, Diia City PIT 5%, Social Insurance Fund merger.
- Civil-contract "(if main place of work)" caveat on the ESV minimum base: kept against the local
  specialist's objection, with no rejoinder recorded.
- SR-163: possible developer error ("Chief Accountant RNOCPP" mapped to director_signatory_rnocpp).
- Version history gap: CCG V1.4 is not cited anywhere.
