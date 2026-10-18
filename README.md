# Road Rash — Arcade

A browser remake of the 1990s arcade biker-racer, built for phones. Twenty riders start the
race with you, the corners throw you at the barriers, and the fastest way past a rival is to
put them in the wall.

## The game

**Bike select.** Eight machines with real trade-offs — top speed, acceleration, cornering
grip, weight and punch. The Sunspot ST-6 is the slowest bike on the grid and hits like a
wrecking ball; the Piccolo RSV is rocket-fast and will spin you if you look at it wrong.

**Cities with splits.** Four cities, each splitting twice. Every fork offers three routes:
a safe line, a balanced one, and a fast route that is also trying to kill you. **Your lateral
position at the fork is your choice** — hug the left barrier for the safe road, or throw
yourself down the outside for raw pace. The fast routes also carry more rivals and more
roadside punishment.

**Pack racing.** All 20 rivals race simultaneously. They attack *each other* as well as you,
so the field tears itself apart. Finishers are ranked by time; anyone who goes down is
struck out with the distance they covered.

**Combat.** Punch, kick, headbutt and whip, each with its own reach, damage, knockback and
cooldown. The whip sweeps multiple rivals. You have to actually pull alongside someone to
land a hit — you cannot mash it out over your shoulder.

**Cornering.** Real centrifugal force. Let go of the steering and the bend throws you wide
into the barrier, bleeding speed the whole way. Counter-steer or lose the road.

**Damage.** Every crash, hit and hard landing accumulates damage across three zones, which
costs you top speed and grip for the rest of the race.

**Tournament.** Four cities, points for podium finishes: 10 for the win, 6 for the podium,
3 for a points finish, 1 for finishing. Twenty-five points wins the season.

## Play

Open `index.html` in any mobile browser — no build step, no dependencies.

| Control | Touch | Keyboard |
|---|---|---|
| Steer | Drag anywhere on screen | ← → / A D |
| Brake | BRAKE pad, bottom-left | Space |
| Attack | PUNCH / KICK / HEADBUTT / WHIP pads | 1 2 3 4 |
| Pause | II, top-right | P |

Hold `Shift` for extra pace at the forks. Pull alongside a rival and hit them with the attack
pads. Riding the outside line through a bend needs a counter-steer input — that is the game.

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