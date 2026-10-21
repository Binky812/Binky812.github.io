# Binky812.github.io

Simple GitHub Pages download website with:
- A home page (`index.html`)
- A downloads page (`downloads.html`)
- Data-driven file metadata (`downloads.json`)

## How to add a new downloadable file

1. Add the file to `/files` (or another path in this repository).
2. Add an entry to `downloads.json` with:
   - `displayName` (human-friendly title)
   - `description`
   - `fileName` (actual file name shown on the page)
   - `downloadPath` (repository-relative path, such as `files/my-file.zip`)
3. Commit and push changes. GitHub Pages will publish the update.

You do **not** need to edit page HTML/JS when adding normal new files; only add the file and metadata entry.

## Security and upload workflow limitations

GitHub Pages is static hosting. A secure "upload from the website" admin panel cannot be implemented in this repository alone without exposing credentials/tokens in client-side code, which is unsafe.

Safe practical workflows:
- Use GitHub web UI to upload files and edit `downloads.json` in authenticated GitHub sessions.
- Or use a separate authenticated GitHub Actions workflow (manual dispatch + repository permissions) to manage uploads/metadata, keeping secrets in GitHub Actions secrets (never in page code).