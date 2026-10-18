# Road Rash 1976

A browser re-imagining of the classic *Road Rash* arcade biker game, built for phones.

## Play

Open `index.html` in any mobile browser — no build step, no dependencies.

| Control | Touch | Keyboard |
|---|---|---|
| Steer | Drag anywhere on screen | ← → / A D |
| Brake | Bottom-left pad | Space |
| Boost | Bottom-right pad | Shift |

Pass traffic for score, shave close for a near-miss bonus, and spend nitro to outrun the
denser traffic that shows up the further you get. Crashes cost health and spin the wreck
onto the shoulder; three unbraked hits end the run. Your best score persists locally.

## Deploy

Any static host works. With Docker:

```bash
docker build -t roadrash .
docker run -p 8080:80 roadrash
```

With Coolify: new project → add resource → *Public/Private Repository* → point at this repo
(branch `main`), set Dockerfile as the build pack, port `80`. Coolify serves it over its
generated HTTPS domain.

## Layout

```
index.html   the whole game (markup, styles, engine, rendering, input)
Dockerfile   nginx image serving the static file
nginx.conf   server block with SPA fallback and no-cache on the shell
```