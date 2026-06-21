# Train sound uploads

Drop real audio files into these folders and point each station's `sounds` entry in `index.html` at the matching file. Missing files can stay `null`; the app will keep using synthesized placeholders until real audio is configured.

## Folders

- `departure-melodies/` — short station melodies that play when the train leaves a station.
- `announcements/` — arrival announcements that play while pulling into a station.
- `ambience/` — optional looped platform ambience for a station.
- `shared/` — route-wide sounds such as door chimes or train-running ambience.

## Naming convention

Use lowercase, hyphen-separated names so files are easy to find and safe to reference from HTML:

```text
sounds/departure-melodies/{line}-{station-number}-{station-slug}-departure-melody.{ext}
sounds/announcements/{line}-{station-number}-{station-slug}-arrival-announcement.{ext}
sounds/ambience/{line}-{station-number}-{station-slug}-platform-ambience.{ext}
sounds/shared/{sound-name}.{ext}
```

- `{line}` is the JR line code in lowercase, for example `jy` or `jc`.
- `{station-number}` is the station number padded to two digits, for example `01`, `05`, or `30`.
- `{station-slug}` is the station romaji in lowercase with spaces/apostrophes replaced by hyphens.
- `{ext}` can be `mp3`, `ogg`, or `wav`; `mp3` is the safest default for browser playback.

## Examples

```text
sounds/departure-melodies/jy-20-shibuya-departure-melody.mp3
sounds/announcements/jy-20-shibuya-arrival-announcement.mp3
sounds/ambience/jy-20-shibuya-platform-ambience.mp3
sounds/shared/door-chime.mp3
sounds/shared/transit-ambience.mp3
```

Then wire the station in `index.html` like this:

```js
sounds:{
  melody:'sounds/departure-melodies/jy-20-shibuya-departure-melody.mp3',
  announcement:'sounds/announcements/jy-20-shibuya-arrival-announcement.mp3',
  ambience:'sounds/ambience/jy-20-shibuya-platform-ambience.mp3'
}
```
