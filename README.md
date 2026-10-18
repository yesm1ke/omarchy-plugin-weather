# Weather for the Omarchy bar, 9-day forecast

[![Ko-fi](https://img.shields.io/badge/Ko--fi-support-FF5E5B?logo=ko-fi&logoColor=white)](https://ko-fi.com/mike_g)

The stock Omarchy weather widget with a longer forecast: the popup shows nine
days in a 3 × 3 grid instead of three in a row.

## Changes from stock

- `Panel.qml`: requests 10 days from Open-Meteo (`forecast_days=10`) instead
  of 4, and lays the forecast out as a three-column grid.
- `Model.js`: keeps nine Open-Meteo forecast days instead of three. The wttr.in
  fallback still gives three, which is all that service returns.

## Install

```sh
omarchy plugin add https://github.com/yesm1ke/omarchy-plugin-weather --enable
omarchy plugin disable omarchy.weather   # the stock widget it replaces
```

## Staying current with Omarchy

This is a copy of the stock widget with changes on top, so it would not pick
up Omarchy's own fixes by itself. The repository keeps them apart:

- branch `upstream` holds the stock files exactly as Omarchy ships them, one
  commit per Omarchy version that changed them;
- branch `main` is `upstream` plus the changes described above.

After an Omarchy update, run `./sync-upstream` in the installed plugin
(`~/.config/omarchy/plugins/<id>/`). It records the installed stock files on
`upstream` and merges them into `main`; on a conflict it aborts the merge and
leaves everything as it was, to be resolved with `git merge upstream`.
`./sync-upstream --check` only reports whether anything changed. It can be run
automatically from an Omarchy `post-update` hook.

## License

MIT, see [LICENSE](LICENSE). Based on the Omarchy weather widget, © David
Heinemeier Hansson, MIT.
