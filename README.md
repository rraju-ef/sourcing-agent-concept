# GitHub Pages (page) + Fly.io (comments API)

Deploy order matters: Fly first (to get the API URL), then GitHub.

## 1. Deploy the API on Fly
Use the deploy-fly bundle:
    fly auth login
    # edit fly.toml: set a unique app name
    fly volumes create comments_data --size 1 --region sjc
    fly deploy
    fly scale count 1
Verify: https://<your-app>.fly.dev/api/comments returns {"comments":[],...}

## 2. Point this page at it
Already done — index.html is pre-configured for
https://ruta-sourcing-agent.fly.dev/api/comments

## 3. Publish on GitHub Pages
    git init && git add . && git commit -m "concept + review page"
    git branch -M main
    git remote add origin git@github.com:<you>/<repo>.git
    git push -u origin main
Then: repo Settings -> Pages -> Source: "Deploy from a branch" -> main, / (root) -> Save.
Page appears at https://<you>.github.io/<repo>/ within a minute or two.

## 4. Verify shared comments
Open the Pages URL, open the comment sidebar (list button, bottom-right):
it must read "SHARED via API". Drop a test comment, then open the URL in an
incognito window — the comment should be there.

## Cautions
- A PUBLIC repo makes the document itself publicly readable (it contains your
  strategy). GitHub Pages on a PRIVATE repo requires a paid GitHub plan.
- Anyone with the page URL can read and write comments. Share deliberately.
- Freeze the page text during a review round: editing sentences orphans the
  comments anchored to them (they show as "anchor not found", not lost).
  Export JSON from the sidebar before pushing revisions.
