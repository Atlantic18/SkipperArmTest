# Skipper — Codemagic trigger repo

Malé pomocné repo, které slouží **jen jako spouštěč** buildů na Codemagicu, abychom
mohli Skipper testovat na reálném Apple Silicon Macu (M2/M4) přes VNC. Nekompiluje se
tu — build se stahuje hotový a jen se spouští.

## Fáze 0 — ověřit Codemagic + VNC
`codemagic.yaml` teď obsahuje workflow `vnc-smoke-test`, které jen nastartuje Mac a drží
ho naživu, aby se šlo připojit přes VNC a ověřit, že celá cesta funguje.

## Fáze 1 — Skipper import/export (přidá se pak)
- stáhne Apple Silicon build Skipperu (`curl` z našeho serveru),
- rozbalí a spustí ho,
- necháme přes VNC naimportovat testovací model a vyexportovat výstup,
- vyexportované soubory se posbírají jako `artifacts:` ke stažení.

## Napojení na Codemagic (manuální URL / "Other")
1. Codemagic → Add application → **Other** (connect via URL).
2. Zadat SSH URL tohoto repa.
3. Veřejnou část vygenerovaného SSH klíče přidat do repa jako **deploy key**.
4. Spustit build ručně, připojit se přes VNC.
