# rstappdev — site

Single-page studio site for application and web development work.
No build step, no dependencies, no trackers.

    index.html     the whole site (CSS + JS inline, self-contained)
    404.html       matching not-found page
    robots.txt     allow all
    .nojekyll      tells GitHub Pages to serve files verbatim (no Jekyll)
    _headers       security headers for hosts that read it (Netlify/Cloudflare)

## Contact details

The contact section links to `rstappdev@gmail.com` — a `mailto:` call to action
plus a copy-to-clipboard button. To change the address, update both places in
`index.html`:

    the .reach-mail href   (the mailto: link)
    the .reach-copy data-copy attribute

Deliberately *not* on the page, because they were never supplied: a phone or
WhatsApp number, business name and registration details, and a location. Add
them if you want them public.

Also confirm the stack list reflects what you actually want to advertise.

## Deploying to GitHub Pages

Two routes, depending on your GitHub **username**. Check it at
https://github.com/settings/profile before choosing.

### Route A — your username IS `rstappdev`

Name the repository exactly `rstappdev.github.io`. The site then serves from the
domain root.

    git remote add origin https://github.com/rstappdev/rstappdev.github.io.git
    git push -u origin main

Live at: https://rstappdev.github.io/

### Route B — your username is something else

Name the repository `rstappdev`. The site serves from a sub-path.

    git remote add origin https://github.com/<YOUR-USERNAME>/rstappdev.git
    git push -u origin main

Live at: https://<YOUR-USERNAME>.github.io/rstappdev/

### Both routes — turn Pages on

Only public repositories get Pages on a free account.

1. Repo → **Settings** → **Pages** (left sidebar)
2. Source: **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)** → **Save**
4. Wait 1–2 minutes; the URL appears at the top of that page

### Set your identity before pushing

git needs a name and email on the commit. This repo currently carries a
placeholder:

    git config user.name  "Your Name"
    git config user.email "you@example.com"
    git commit --amend --reset-author --no-edit

### Authentication

GitHub no longer accepts account passwords over HTTPS. Use a Personal Access
Token (Settings → Developer settings → Personal access tokens) with `repo`
scope, and paste it as the password when git prompts. Or set up an SSH key.

### Custom domain (optional, paid)

Buy the domain first (a `.co.za` is a few hundred rand a year), then:

1. Repo → Settings → Pages → **Custom domain** → enter it → Save
2. Create a file named `CNAME` in the repo root containing only the bare domain
3. At your DNS provider add the records GitHub displays — for an apex domain
   four `A` records to GitHub's IPs, for `www` a `CNAME` to `<user>.github.io`
4. Tick **Enforce HTTPS** once the certificate issues

## Alternative hosts

    Netlify          drag the folder onto https://app.netlify.com/drop
    Cloudflare Pages Workers & Pages → Create → Pages → Upload assets
