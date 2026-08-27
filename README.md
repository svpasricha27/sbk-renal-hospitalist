# Renal Ward Essentials for Hospitalists

Teaching site for the Sunnybrook Health Sciences Centre nephrology program. Six modules, two bedside tools, and a 25 question knowledge check.

Everything is static. There is no build step, no framework and no dependencies to install.

## What is in here

| File | What it is |
|---|---|
| `index.html` | The entire site. All six modules, both tools, the knowledge check and the certificate generator are in this one file. |
| `404.html` | Shown if someone lands on a path that does not exist. |
| `vercel.json` | Clean URLs, and headers that tell search engines not to index the site. |
| `robots.txt` | Also tells crawlers to stay away. See "Making it public" below. |
| `favicon.svg`, `apple-touch-icon.png` | Icons. |
| `.gitignore` | Keeps `.vercel` and OS junk out of the repo. |

## Putting it on GitHub

1. Go to <https://github.com/new> and create a repository. Private is fine, Vercel can read private repos once you connect it.
2. Do **not** tick "Add a README file", since there is one here already.
3. On the empty repository page, click **uploading an existing file**.
4. Drag in everything from this folder.
5. Write a commit message and click **Commit changes**.

If you would rather use the command line:

```bash
cd path/to/this/folder
git init
git add .
git commit -m "Renal ward teaching site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

## Deploying on Vercel

1. Sign in at <https://vercel.com> with your GitHub account.
2. **Add New** then **Project**, and import the repository you just created.
3. Leave every setting alone. Framework preset will say **Other**, and the build and output settings should stay empty. There is nothing to build.
4. Click **Deploy**. It takes under a minute and you get a URL like `your-repo.vercel.app`.

Every push to `main` redeploys automatically, so editing `index.html` on GitHub and committing is enough to update the live site.

### A custom address

In the Vercel project, go to **Settings** then **Domains** and add one. If it is a hospital domain you will need whoever runs DNS to add the record Vercel gives you.

## Things you may want to change

**Making it public to search engines.** The site currently tells crawlers not to index it, which seemed the right default for internal teaching material containing local protocols. To reverse that, delete `robots.txt`, remove the `X-Robots-Tag` block from `vercel.json`, and delete the `<meta name="robots">` line near the top of `index.html`.

**Editing content.** Everything is in `index.html`. Each module is a `<div class="page" id="p-m1">` block and they are in order. The knowledge check questions are in the `QS` array near the bottom of the script. The two tools are the `mountDose` and `mountAnemia` functions.

## Worth knowing before you share the link

- **Progress is held in the browser tab only.** Reloading restarts the current module. Certificates download immediately as PDFs, so nothing is lost as long as people save the file when it appears. Making progress survive a reload would need browser storage or a back end.
- **Nothing is collected.** No accounts, no analytics, no server. Names typed into the certificate form go into the PDF and nowhere else.
- **Two things go stale.** The antimicrobial dosing tool summarises the Sunnybrook stewardship page and does not update itself, and the anemia tool follows the published BC Renal algorithm with iron adapted to local practice. Both should be checked against the live sources before each teaching cycle.
- **The restless legs iron threshold** in Module 5 (ferritin under 100, saturation under 20 percent) is deliberately higher than the anemia protocol threshold. If your program uses different numbers, change them in the module text, the module checkpoint and the matching final check question.
