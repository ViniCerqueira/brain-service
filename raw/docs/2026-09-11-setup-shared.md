# Clean machine setup — verify environment + install mercans-pipeline/shared

This is a freshly-set-up Windows machine (Git Bash MINGW64) being prepared to
run Mercans compliance pipeline automation. Do the following, in order,
reporting clearly at each step — don't just say "done", show the actual
evidence (command output, file counts, sizes).

## STEP 1 — Verify the environment is genuinely sound

```bash
python --version
pip --version
where python
echo "$PATH" | tr ':' '\n' | grep -i python
```

Confirm: `python --version` returns a real version (not the Windows Store
stub message), `pip --version` works, and `where python` points to a real
install path (e.g. under `AppData\Local\Programs\Python\Python313`), not
`WindowsApps`. If anything here is still broken, stop and report exactly
what failed — don't proceed to install packages on top of a broken Python.

## STEP 2 — Locate the shared.zip transfer file

The user is manually transferring `shared.zip` (a zipped copy of
`~/mercans-pipeline/shared/` from another of their machines) onto this
machine via USB/email/Drive — that transfer is NOT something you can do
yourself, it depends on the user. Check the likely landing spots:

```bash
find "$HOME/Downloads" "$HOME/Desktop" "$HOME" -maxdepth 2 -iname "shared*.zip" 2>/dev/null
```

If nothing is found, stop here and report clearly: "shared.zip not found yet
— waiting on the manual transfer from the other machine." Do not proceed
further, and do not fabricate or guess at file locations.

## STEP 3 — Extract to the correct location (only if Step 2 found the zip)

```bash
mkdir -p "$HOME/mercans-pipeline"
cd "$HOME/mercans-pipeline"
unzip -o "<path to the shared.zip found in Step 2>"
```

Confirm a `shared/` directory now exists directly under `~/mercans-pipeline/`
(not nested one level too deep, e.g. not
`~/mercans-pipeline/shared/shared/`) — if the zip's internal structure
produced a double-nested folder, flatten it so the final path is exactly
`~/mercans-pipeline/shared/<files>`, matching every other machine's layout.

## STEP 4 — Run the real readiness check

If `check_shared_readiness.py` is present in `~/Downloads/`, run it directly
rather than re-implementing its logic:

```bash
python "$HOME/Downloads/check_shared_readiness.py"
```

This checks the 11 required files by name AND opens
`REFERENCE_Payslip_Mozambique.xlsx` for real to count its actual sheets — do
not substitute a simpler existence-only check; the sheet-count verification
is the part that catches a stale or wrong file silently masquerading under
the right filename.

If that script is not present, install openpyxl first
(`pip install openpyxl --break-system-packages` — note: on native Windows
Python, `--break-system-packages` may not be needed or may not exist as a
flag; try plain `pip install openpyxl` first and only add the flag if pip
specifically errors about an externally-managed environment) and inline the
same two checks: (a) all 11 required filenames present with real file sizes
>0 bytes, (b) `REFERENCE_Payslip_Mozambique.xlsx` opens and reports its
sheet count and names.

## STEP 5 — Report

Give a clear final summary: environment status (pass/fail), whether
shared.zip was found and extracted, the full per-file readiness result from
Step 4, and — if anything is missing, broken, or ambiguous — say so plainly
rather than rounding up to "looks good." This machine should not be treated
as pipeline-ready until every required file is confirmed present with real
content, not just by name.
