# Sdip25588.github.io

Personal GitHub Pages site containing web assignments and projects.

## Site Structure

| Path | Description |
|------|-------------|
| `MmpGitHubAssignment/Index.html` | Travel adventures home page |
| `FinalGitHub/final.html` | "Quiet Motion" animation project (video + audio) |
| `FinalGitHub/Image.html` | Design process image page |

## Viewing the Site

The site is served by **GitHub Pages** directly from the `main` branch — no build step required.

Live URL: `https://sdip25588.github.io/`

Individual pages are accessible at their full paths, for example:
- `https://sdip25588.github.io/MmpGitHubAssignment/Index.html`
- `https://sdip25588.github.io/FinalGitHub/final.html`

### Running locally

Open any HTML file directly in your browser:

```bash
# macOS
open FinalGitHub/final.html

# Linux
xdg-open FinalGitHub/final.html

# Windows
start FinalGitHub/final.html
```

Or use Python's built-in server to avoid CORS restrictions with local media files:

```bash
python3 -m http.server 8080
# Then open http://localhost:8080/FinalGitHub/final.html
```

---

## Related: Taunggyi2025 Streamlit App

The AI English tutoring app lives in [Sdip25588/Taunggyi2025](https://github.com/Sdip25588/Taunggyi2025).

### Prerequisites

- Python 3.9+
- Azure Cognitive Services credentials (Speech SDK) — copy `.env.example` to `.env` and fill in values

### Run locally

```bash
git clone https://github.com/Sdip25588/Taunggyi2025.git
cd Taunggyi2025
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run main.py
```

The app opens automatically at `http://localhost:8501`.

### Smoke-test (no Azure credentials needed)

```bash
python -c "import main"          # checks for import/syntax errors
```

### PR #4 status

[PR #4 (Add voice-first conversation mode)](https://github.com/Sdip25588/Taunggyi2025/pull/4) adds a
dialog-state-machine (`ConversationState`) to `learning_orchestrator.py` and conversation UI to
`gui_engine.py`. The branch `copilot/add-conversation-mode` currently has merge conflicts with `main`
that must be resolved before it can be merged (see PR page for conflict details).

---

## CI

A GitHub Actions workflow (`.github/workflows/ci.yml`) runs on every push and pull request:

1. **Conflict-marker check** — fails if any `<<<<<<<` / `=======` / `>>>>>>>` markers are found in HTML files.
2. **HTML validation** — runs `html-validate` (structural rules only) on all `.html` files.
3. **Internal-link check** — verifies every relative `href`/`src` in HTML files resolves to an existing file.