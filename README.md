# SCC — Sloc, Cloc & Code  
A fast, multi‑language code counter used to estimate project size, complexity, and audit scope.

`scc` scans a codebase and reports:
- Total lines of code (LOC)
- Comments, blanks, and file counts
- Language‑by‑language breakdown
- Complexity estimates
- Optional cost models (COCOMO, LOCOMO)
- Optional DRYness / unique‑lines metrics (ULOC)

This helps auditors quickly understand project size and estimate review effort.

---

## 🚀 What You Need to Do

### 1. Install SCC

Choose the method that matches your environment:

**Go toolchain**
```
go install github.com/boyter/scc/v3@latest
```

**Homebrew (macOS/Linux)**
```
brew install scc
```

**Windows**
- **Scoop:** `scoop install scc`
- **Chocolatey:** `choco install scc`
- **WinGet:** `winget install --id benboyter.scc`

**Linux**
- **Snap:** `sudo snap install scc`
- **Fedora:** `sudo dnf copr enable lihaohong/scc && sudo dnf install scc`
- **FreeBSD:** `pkg install scc`

**Docker (no installation needed)**
```
docker run --rm -it -v "$PWD:/pwd" ghcr.io/boyter/scc:master scc /pwd
```

---

## ▶️ 2. Run SCC on a Codebase

From inside the project directory:

```
scc
```

Or specify paths:

```
scc src/ backend/ frontend/
```

This produces:
- A table of languages, files, LOC, comments, blanks, complexity
- Total project size
- Optional cost estimates

---

## 📊 Example Output (simplified)

```
Language     Files   Lines   Code   Comments
--------------------------------------------
Go            120    45,210  32,100   5,430
Markdown       18     2,340   2,340       0
JSON           12       980     980       0
--------------------------------------------
Total         150    48,530  35,420   5,430
```

---

## 🔧 Useful Options

**Show per‑file detail**
```
scc --by-file
```

**Include only certain languages**
```
scc --include-ext go,rs,py
```

**Exclude large/minified/generated files**
```
scc --no-large --no-min --no-gen
```

**Calculate unique lines (ULOC) & DRYness**
```
scc --uloc
scc --dryness
```

**Include cost estimates**
```
scc --cocomo-project-type organic
scc --locomo
```

---

## 🎯 Summary for Audit Clients

To prepare for a source‑code audit:

1. **Install `scc`** using any method above  
2. **Run `scc` in the project root**  
3. **Send us the output**, which gives:
   - Total LOC  
   - Language breakdown  
   - Complexity indicators

This helps us gauge the size of the project and allocate review time appropriately.

