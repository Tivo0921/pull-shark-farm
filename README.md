# Pull Shark Farm 🦈

> Automated PR harvesting to cultivate the GitHub **Pull Shark** achievement at scale.

[![PRs](https://img.shields.io/badge/PRs-1024%20merged-blue?logo=github)](https://github.com/Tivo0921/pull-shark-farm/pulls?q=is%3Apr+is%3Amerged)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Shell](https://img.shields.io/badge/shell-bash-lightgrey?logo=gnubash)](farm.sh)

---

## What is this?

The GitHub **Pull Shark** achievement is awarded for merging pull requests. This repository automates the process of creating, merging, and tracking PRs so you can reach any milestone — 2, 16, 128, 1024, or beyond.

| Achievement | PRs Required |
|---|---|
| Pull Shark x1 | 2 |
| Pull Shark x2 | 16 |
| Pull Shark x3 | 128 |
| Pull Shark x4 | 1024 |

This farm has completed **1024 PRs**, unlocking Pull Shark x4.

---

## How it works

```
main ──┬── pull-shark-1 ──(merge)──┬── pull-shark-2 ──(merge)──┬─ ... ─┬── pull-shark-1024 ──(merge)──▶
       └─────────────────────────────────────────────────────────────────┘
```

Each iteration:
1. Checks out a fresh branch from `main`
2. Appends one timestamped line to `pull-shark-log.md`
3. Commits, pushes, opens a PR, and merges it
4. Deletes the remote branch

---

## Getting started

### Prerequisites

- [Git](https://git-scm.com/)
- [GitHub CLI (`gh`)](https://cli.github.com/) — authenticated (`gh auth login`)

### Run

```bash
# Clone
git clone https://github.com/Tivo0921/pull-shark-farm.git
cd pull-shark-farm

# Make executable
chmod +x farm.sh

# Harvest PRs 1 → 1024 (auto-resumes if log already exists)
./farm.sh

# Or specify a custom range
./farm.sh 1 16       # PRs 1–16
./farm.sh 500 1024   # PRs 500–1024
```

The script auto-detects the last completed PR in `pull-shark-log.md` and resumes from there, so it is safe to interrupt and re-run.

---

## File structure

```
pull-shark-farm/
├── farm.sh            # Main harvester script
├── pull-shark-log.md  # Append-only harvest log (one line per PR)
└── README.md
```

---

## pull-shark-log.md format

Each merged PR appends one line:

```
PR <n>: <date>
```

Example:

```
PR 1: Fri May  1 15:11:16 JST 2026
PR 2: Fri May  1 15:11:25 JST 2026
...
PR 1024: Fri May  1 20:54:43 JST 2026
```

---

## Options

| Argument | Default | Description |
|---|---|---|
| `START` | auto (last log entry + 1) | First PR number |
| `END` | `1024` | Last PR number |

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first.

---

## License

MIT
