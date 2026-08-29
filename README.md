# TR I Sessions

A TradingView indicator that shades the trading sessions on the chart. Each
session is drawn as a box spanning its own high and low, so the range a session
carved out is visible at a glance, and so is where the next one opened relative
to it.

Tokyo, Frankfurt, London and New York come configured. A fifth slot is free for
a session of your own.

## Installing it

1. Open a chart on TradingView and press **Pine Editor** at the bottom.
2. Paste the contents of [`trading_sessions_indicator.pine`](./trading_sessions_indicator.pine).
3. Press **Add to chart**.
4. To keep it, press **Save**, then find it under Indicators, My scripts.

Written for Pine Script v5.

## What it draws

While a session runs, its box grows with the candles: the top follows the
session high, the bottom follows the session low, and the right edge follows
the current bar. When the session closes, the box is fixed where it stands.

An optional label carries the session name and can sit above or below the box,
aligned to its left edge, centre or right edge.

## Settings

**General**

| Setting | What it does |
|---|---|
| Show History | Keeps the boxes of past sessions. Turn it off to see only the current one |
| Use DST | Switches every session between its two sets of open and close times |

**Box and labels**

| Setting | What it does |
|---|---|
| Box Transparency | 0 is solid, 100 is invisible. The default of 93 leaves the candles readable |
| Display Session Labels | Shows the session name |
| Label Size | tiny, small, normal, large or huge |
| Position | Top or Bottom of the box |
| Align | Left, Center or Right |

**Each session**

| Setting | What it does |
|---|---|
| Enable | Draws this session at all |
| Name | What the label says |
| Color | The box colour, shown at the chosen transparency |
| DST Open, Close | The hours used while Use DST is on |
| No DST Open, Close | The hours used while it is off |
| Extend | Continues the box to the right of the chart |

## The times

Session hours are compared against **UTC**, and every session carries two sets
of them. The one in use is chosen by the Use DST switch rather than by a
calendar, so the switch is flipped by hand twice a year.

| Session | With DST | Without DST | On by default |
|---|---|---|---|
| Tokyo | 00:00 to 09:00 | 00:00 to 09:00 | yes |
| Frankfurt | 08:00 to 16:00 | 07:00 to 15:00 | yes |
| London | 09:00 to 18:00 | 08:00 to 17:00 | yes |
| New York | 14:00 to 23:00 | 13:00 to 22:00 | yes |
| Other | 00:00 to 23:00 | 00:00 to 23:00 | no |

Tokyo carries the same hours in both sets, because Japan keeps no daylight
saving time.

A session whose close is earlier than its open is treated as crossing
midnight, so a window such as 22:00 to 06:00 works.

## Notes

The hours are chosen from a dropdown of whole hours, which is what the sessions
in the default set need. A session that opens at half past the hour cannot be
expressed.

There are no alerts. The indicator draws and does not signal.

Boxes, labels and lines are capped at 500 each, which is what TradingView
allows a single script to hold. On a low timeframe with a long history the
oldest boxes drop off the left of the chart.

## Licence

MIT, see [LICENSE](./LICENSE).
