# Train sound uploads

Drop real audio files into these folders and point each station's `sounds` entry in `index.html` at the matching file. **There are no synthesized placeholders** — anything without a real recording is simply silent, so the ride only ever plays audio you supply.

## Folders

- `departure-melodies/` — short station melodies. These play on the platform **before** the train departs: the melody finishes, the doors close (door chime), and only then does the train pull away.
- `announcements/` — arrival announcements that play while pulling into a station.
- `ambience/` — optional looped platform ambience for a station (played while stopped there).
- `shared/` — route-wide sounds: the door chime, the in-transit running-train atmosphere, and a default platform atmosphere. The "Ambient sounds" toggle in setup turns the transit + platform atmosphere on and off.

### Shared sound files

| File | Plays |
| --- | --- |
| `shared/door-chime.mp3` | once as the doors close, just before departure |
| `shared/transit-ambience.mp3` | looped between stations (swells with train speed) |
| `shared/station-ambience.mp3` | looped while stopped at a station that has no `ambience` of its own |

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
