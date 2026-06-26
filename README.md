# FluidSeal AB — Staff Training & Certification

Standalone internal training site, published to **https://training.fluidsealab.com/**.

This is a **dedicated employee training portal**, separate from the Marion sealing-products
chat agent (marion.fluidsealab.com). It contains the training modules only — there is no chat
agent and no path to Marion from here. Employees get a clean, single-purpose link.

## Files

| File | Published URL | Purpose |
|------|---------------|---------|
| `index.html` | `/` | Training hub — links the 3 modules |
| `product-profiles-training.html` | `/product-profiles-training.html` | Module 1 — Product Profiles Guide (130+ series) |
| `fluidseal_training.html` | `/fluidseal_training.html` | Module 2 — Caliper & Measurement (diagram, video, quiz) |
| `training-certificate.html` | `/training-certificate.html` | Module 3 — 6-level staff certification |
| `fluidseal_training_video.html` | `/fluidseal_training_video.html` | Standalone caliper video (also embedded in Module 2) |
| `CNAME` | — | Pins the custom domain training.fluidsealab.com |

## Relationship to Marion

These same training pages also exist inside the Marion repo at `marion.fluidsealab.com/training/`,
so Marion can still link staff to training from chat. This standalone site is a **separate copy**
with its own repo and domain — the two are independent. If you update a training page, update it
in both places (or decide one is the master and copy across).

## Deployment (GitHub Pages)

1. Create a new GitHub repo (e.g. `fluidseal-training`) and push these files.
2. In the repo: **Settings → Pages → Source: Deploy from branch → main / root**.
3. Pages reads the `CNAME` file and serves at `training.fluidsealab.com`.
4. Add the DNS record at your domain registrar (see DNS below).
5. Back in Settings → Pages, tick **Enforce HTTPS** once the certificate is issued.

## DNS setup (one record)

At the DNS host for `fluidsealab.com`, add a **CNAME record**:

```
Type:  CNAME
Host:  training
Value: <your-github-username>.github.io
TTL:   default
```

(That's the same pattern marion.fluidsealab.com already uses — a CNAME pointing the subdomain
at GitHub Pages. GitHub then matches it to this repo via the CNAME file.)

DNS can take a few minutes to a few hours to propagate. Once it resolves and HTTPS is enforced,
`https://training.fluidsealab.com/` is the employee training link.
