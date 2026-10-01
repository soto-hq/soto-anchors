# soto-anchors

Daily anchors of the SOTO record chain, as required by ADR-000 rule 11.

- Record page and rules: https://soto-record.soto-hq.workers.dev/
- ADR-000 (raw): https://soto-record.soto-hq.workers.dev/adr-000.md  (SHA-256 1bd75421d340cc3e4babbbb448d91283d478b3eec96b08eef5f70f2c98bdb8c7)
- Genesis hash: 10baca9148e0d037b9b905e931933395f6845d9cded5e8bf8d363437bec5ede9

`anchors/genesis-record.json` is the exact genesis record (ADR-000 rule 4); `.ots` is its OpenTimestamps proof.
From the day of the first registered call, each day at 23:59 Pacific an `anchors/YYYY-MM-DD.txt` file with the latest chain head and its `.ots` proof are added here, and the same head is posted on X by @sotosignals.
Verify an anchor: `ots verify anchors/YYYY-MM-DD.txt.ots`.

`chain.jsonl` is the full SOTO record chain, one canonical JSON record per line, in order (genesis first). Recompute it: h(0) is 64 zeros; h(n) is the SHA-256 (lowercase hex) of the 64-character h(n-1) followed immediately by the UTF-8 bytes of record n's line (without the newline). The last h is the head that the daily anchor files and posts carry (ADR-000 rule 4).

```python
import hashlib
h = "0" * 64
for line in open("chain.jsonl"):
    h = hashlib.sha256((h + line.rstrip("\n")).encode()).hexdigest()
print(h)
```
