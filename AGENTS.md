# AGENTS.md: Notes Garden (Org-Roam Digital Garden)

## Repository Layout
- `org-files/`: Org-Roam notes in `.org` format. This is the content.
- `org-files/org-roam.db`: Org-Roam SQLite database (auto-generated, committed for publishing).
- `org-files/img/`: Images referenced in notes.
- `.github/workflows/publish.yml`: GitHub Action that builds and deploys the interactive site.

## Building and Testing
```bash
# Local preview (requires publish-org-roam-ui cloned)
git clone https://github.com/ikoamu/publish-org-roam-ui.git
cd publish-org-roam-ui
./local.sh ../notes-garden/org-files org-roam.db

# Regenerate org-roam.db after editing notes (in Emacs)
# M-x org-roam-db-sync
# Then copy: cp ~/Notes/org-roam.db org-files/org-roam.db
```

## Publishing
Push to `main`. GitHub Actions builds the site and deploys to:
`https://boluwajioadepojuworkp.github.io/notes-garden/`

## Note Workflow
1. Take notes in Emacs with Org-Roam (`~/Notes/`)
2. After editing, sync the DB: `M-x org-roam-db-sync`
3. Copy notes to garden: `cp ~/Notes/*.org org-files/`
4. Copy the DB: `cp ~/Notes/org-roam.db org-files/org-roam.db`
5. Commit and push: notes auto-publish

## Commit Messages
- Follow the [Chris Beams](http://chris.beams.io/posts/git-commit-style/) style.
- Prefix note updates with `notes:`.

## Review Checklist
- `org-roam.db` is up to date with latest notes.
- No broken internal links (`file:` links resolve correctly).
- Images referenced in notes exist in `org-files/img/`.
- Site builds without errors (check Actions tab).
