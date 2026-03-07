# MRKI Tweaks

Fixes and modifications for the Kerbal Space Program mod [MRKI](https://github.com/KerbalHub/MRKI/).

## Configuration

Some of the patches can be configured in `Settings.cfg` with the following options:

- `dayLength` (default = 86,400) — The length of Kerbin's synodic rotation period, i.e. the time between successive sunrises, in seconds.
- `daysPerYear` (default = 175) — The length of Kerbin's orbital period around the Sun in units of `dayLength`.
- `monthsPerYear` (default = 12) — The number of synodic cycles of the Mun's phases in one orbit of Kerbin around the Sun.

All other patches are designed to stand alone so can be opted out of simply by deleting them, but note that the behaviour of one patch may affect another. For example, `ModifyMunOrbitalPeriod` depends on Kerbin's orbital period which is set by `ModifyPlanetOrbitalPeriods`.

## Fixes

### FixKerbinRotationPeriod

MRKI's default configuration sets Kerbin's sidereal rotation period to 86,400s (24 hours) which yields a synodic period slightly longer than 24 hours.

This patch corrects the synodic period to exactly 24 hours, like the Earth, and additionally adjusts the offset time of the in-game clock when using Kronometer so that it shows the proper solar time at the KSC.

## Modifications

### ModifyPlanetOrbitalPeriods

Changes the mass of the Sun to yield the desired length of Kerbin's orbit, naturally also scaling all the other planets with it. The default configuration of 175 days should be much less punishing and closer to quarter-scale than MRKI's default 464 days, even longer than Earth's!

### ModifyMunOrbitalPeriod

Changes the Mun's orbit to fit an exact number of synodic months into Kerbin's year. The default configuration results in a change in the Mun's semi-major axis of less than 0.1%.

### ModifyQuarterScale

I thought it was a bit silly that MRKI was scaled to *exactly* 2.67x stock size, producing a 1,602km Kerbin for example, when it was intended to follow JNSQ's model of a 1,600km Kerbin. MRKI's `Stock` scale option rescales all celestial bodies by a factor of 0.374531835x (≈1/2.67), producing some especially ugly numbers for no good design reason.

This patch changes the size of all planets and moons by just a smidge for nicer looking numbers and changes the `Stock` scale option to a 0.375x rescale.

### ModifyBodySizes

In contrast to the universal tiny changes of `ModifyQuarterScale`, this patch rescales specifically Eve, Gilly, Minmus, Laythe, Bop and Pol to slightly more realistic radii based on their surface gravity.

Current configuration:

- Eve: ~~1,715,000m~~ 2,080,000m
- Gilly: ~~17,500m~~ 48,000m
- Minmus: ~~107,000m~~ 216,000m
- Laythe: ~~1335,000m~~ 1104,000m
- Bop: ~~25,000m~~ 56,000m
- Pol: ~~44,000m~~ 120,000m

## Extra stuff

### CustomKronometerCalendar

A custom 12-month, 175-day lunisolar calendar configured using the required mod Kronometer, complete with Kerbalised analogues of our terrestrial months.

## Compatibility

### Required

- [MRKI (1.0.6)](https://github.com/KerbalHub/MRKI)

### Supported

- [Kronometer (1.11.0)](https://github.com/Kopernicus/Kronometer)

## License

Distributed under the MIT License.
