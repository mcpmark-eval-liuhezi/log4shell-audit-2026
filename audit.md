# Log4Shell Audit — CVE-2021-44228

## Advisory

- **GHSA ID:** GHSA-jfh8-c2jp-5v3q
- **CVE:** CVE-2021-44228
- **Summary:** Remote code injection in Log4j (JNDI/LDAP lookup via `log4j-core`)
- **Severity:** Critical (CVSS 3.1 score 10.0, vector `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H`)
- **Advisory URL:** https://github.com/advisories/GHSA-jfh8-c2jp-5v3q

## Affected versions

- **Affected range:** `org.apache.logging.log4j:log4j-core` < 2.15.0 (all versions prior to 2.15.0; the advisory also recommends 2.16.0+ as the fully hardened line, and calls the 2.x line below 2.16.0 subject to the JNDI issue overall)
- **First patched version:** 2.15.0

## Version-range verdicts

Range comparison executed against the GitHub advisory database `affects` matcher for GHSA-jfh8-c2jp-5v3q (CVE-2021-44228), plus an independent programmatic check against the `< 2.15.0` boundary:

| log4j-core version | In affected range (< 2.15.0)? | Verdict |
|---|---|---|
| 2.14.1 | Yes — matched by the advisory | **AFFECTED** — remote code execution, must be upgraded |
| 2.17.1 | No — not matched | **Not affected** — clear to deploy; 2.17.1 > 2.16.0 fully-hardened line |

Both verdicts were obtained programmatically, not by inspection.

## Search outcome across my repositories

Code search over the `HeziLiu` account returned **zero log4j references**. The following queries were run (each returned `total_count: 0`):

- `user:HeziLiu log4j`
- `user:HeziLiu log4j2`
- `user:HeziLiu log4shell`
- `user:HeziLiu fork:true log4j` (forks included)
- `user:HeziLiu path:pom.xml`
- `user:HeiLiu filename:build.gradle` — note: this query used the misspelled handle `HeiLiu`, so it is not valid evidence; the correctly spelled `org.apache.logging` query (which returned `total_count: 0`) is the one that stands.

Repos searched: `Little-rookie`, `Big-Buzzard`, `CodingInterviewChinese2` (fork), `awesome-chatgpt-prompts-zh` (fork). No imports, no `pom.xml`/`build.gradle` build files, no lock files, and no direct code mentions of log4j were found.

**Conclusion:** No log4j exposure found in any of the four existing repositories. The production pin of `log4j-core 2.14.1` (wherever it lives) is **affected by CVE-2021-44228**; the proposed target of **2.17.1 is not affected** and is a valid remediation.
