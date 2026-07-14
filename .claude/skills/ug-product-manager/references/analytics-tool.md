# ug-analytics dependency

Use the sibling project at `/Users/elzira/my-proj/ug-analytics` as the deterministic, read-only analytics interface. Do not duplicate its API parsing inside the product skill and do not edit that repository while performing product work.

## Discover available commands

Run the installed command when available:

```bash
ug-analytics --help
```

The currently installed CLI exposes its only implemented operation as the root command:

```bash
ug-analytics EXP_ID --section analysis
ug-analytics EXP_ID --section runs
```

The analytics project specification describes future `raw`, `list`, `show`, and `daily` subcommands, but they may not yet be implemented. Feature-detect them through `--help`; never assume availability.

If the CLI is not installed, use the project environment from `/Users/elzira/my-proj/ug-analytics` according to its README. Do not expose or print `UG_COOKIE`.

## Data interpretation checklist

Before drawing a product conclusion, verify:

1. Experiment ID, name, status, platform, version, segment, and exposure event.
2. Control and variation sample sizes and sample-ratio balance.
3. Metric definition, denominator, attribution window, and data period.
4. Test maturity, including pending trials, refunds, renewals, or delayed retention windows.
5. Absolute values, relative change, uncertainty, and p-value where applicable.
6. Target metric, company-standard guardrails, and segment consistency.
7. Instrumentation changes, missing events, contamination, and post-treatment filters.
8. Whether the observed result is statistically significant, practically meaningful, and decision-ready.

Do not equate `p < 0.05` with product success. Do not equate `p >= 0.05` with proof of no effect. Report uncertainty and decision thresholds.

## Source record

For every numeric conclusion, preserve:

- experiment ID;
- platform and segment;
- metric name and definition;
- control and variation values;
- difference and uncertainty;
- data snapshot date;
- command or source used.

## Failure handling

- If authentication expires, report the CLI message and continue with non-analytics context where useful.
- If the schema is unrecognized, use the unparsed command output only for inspection and flag parser risk.
- If the requested experiment cannot be found, do not substitute a similarly named experiment without confirmation.
- If data conflicts across sources, present the conflict and prefer the source with the valid exposure and population definition.
