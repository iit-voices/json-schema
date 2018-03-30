# Voices of the Holocaust JSON Schema

Individual interviews, including the person being interviewed and the interview itself, are the core
content of the Voices project. Listings by language, nationality, and so on can all be derived from
these individual records.

## Portions in Flux

* **Locations**: The location at time of invasion is a single place, if it is known. By contrast,
  many of the survivors were interned in multiple concentration camps, so an array of locations
  better represents that data. The survivor’s location at the time of liberation may include
  additional information, including a specific liberation date and the name of the liberating
  force’s country. Trying to make these uniformly accessible is the trick:
  `interviewee.locations.invasion.location`, `interviewee.locations.liberation.location`. But that
  is more verbose for the single invasion location.
* **Audio time markers**: The duration field uses an `HH:MM:SS` notation, while the start times in
  transcripts use seconds and a three-place decimal value: `SSS.SSS`. Need to research which of
  those are better to present (probably the seconds), and make them uniform throughout. That will
  include some kind of conversion, much like for the conversion of dates from the US-style
  `August 12, 1946` to ISO-style `YYYY-MM-DD` format, `1946-08-12`.
* **HTML content**: Some of the content, particularly the English translations, have inline links
  (`<a>`) on certain keywords, including locations. The query-string URL destinations in the links
  will no longer be valid on the new site, which is one problem. The other problem is whether to
  preserve and present only the HTML/hyperlinked version, or to have parallel HTML and plaintext
  versions in the JSON file.
* **Multiline strings**: JSON seems incapable of rendering multiline strings, meaning that a newline
  character seems likely to break the JSON. Need to investigate that, but it probably ultimately
  doesn't matter (it just makes the example schema here a little harder to read in full).
