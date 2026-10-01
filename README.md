# soto-anchors

Daily anchors of the SOTO record chain, as required by ADR-000 rule 11.

- Record page and rules: https://soto-record.soto-hq.workers.dev/
- ADR-000 (raw): https://soto-record.soto-hq.workers.dev/adr-000.md  (SHA-256 1bd75421d340cc3e4babbbb448d91283d478b3eec96b08eef5f70f2c98bdb8c7)
- Genesis hash: 10baca9148e0d037b9b905e931933395f6845d9cded5e8bf8d363437bec5ede9

`anchors/genesis-record.json` is the exact genesis record (ADR-000 rule 4); `.ots` is its OpenTimestamps proof.
From the day of the first registered call, each day at 23:59 Pacific an `anchors/YYYY-MM-DD.txt` file with the latest chain head and its `.ots` proof are added here, and the same head is posted on X by @sotosignals.
Verify an anchor: `ots verify anchors/YYYY-MM-DD.txt.ots`.
