# The Data

Call of Duty World League data.

## Tabular Data

Tabular data is simply per-player per-game stats for every game in the tournament (aka 1 row per player-game).

 * 2017
    * CWL Champs - Orlando, FL - Aug 9-13, 2017 - [data-2017-08-13-champs.csv](data-2017-08-13-champs.csv)
 * 2018
    * CWL Dallas - Dallas, TX - Dec 8-10, 2017 - [data-2017-12-10-dallas.csv](data-2017-12-10-dallas.csv)
    * CWL New Orleans - New Orleans, LA - Jan 12-14, 2018 - [data-2018-01-14-neworleans.csv](data-2018-01-14-neworleans.csv)
    * CWL Pro League, Stage 1 - Columbus, OH - Jan 23-Apr 8, 2018 - [data-2018-04-08-proleague1.csv](data-2018-04-08-proleague1.csv)

## Structured Data

Structured data is provided as nested json per game, where each game includes individual game events such as spawns and deaths.  See [Structured](structured) for details.

## Definitions

Some definitions:

 * __Basic Stats__ - simple gameplay counting stats (starting at 0 and going up), such as `kills`, `deaths`, `hill time`, `bomb defuses`, `firstbloods`, ...
 * __Derived Stats__ - stats computed from other basic stats, such as `k/d` (`kills` divided by `deaths`), `k per 10min` (`kills` divided by `duration` per 10 minutes), `firstblood %` (`firstbloods` divided by `snd rounds`), ...
 * __Aggregate Stats__ - basic stats summed over a certain period of time (series, tournament, season) then normalized per game to allow player vs player comparisons, such as `season k/d`, `kills per game`, `plants per round`, `points per game`, ...
 * __Advanced Stats__ (aka Sabermetrics) - complex derived stats that *best* describe player performance and/or enable *better* player vs player comparisons, such as `QBR` from football (american), `WAR` and `OPS+` from baseball, `PER` in basketball, ...

For Call of Duty, everything from basic stats to advanced stats is under active investigation.  What stats are best when comparing players, when comparing teams?  What stats best predict future performance?  What stats can be used to succinctly capture the story of the games, the series, the pool, or the tournament?

## The Stats

The basic and derived stats found in the data (aka the columns in the tabular data files):

 * `match id` - unique game id
 * `series id` - unique series id
 * `end time` - game end time in UTC
 * `duration (s)` - game duration in seconds (includes breaks between rounds, halftimes, ...)
 * `mode` - the game mode (`Hardpoint`, `Search & Destroy`, ...)
 * `map` - the map
 * `team` - the team
 * `player` - the player
 * `win?` - `W` if the player won the game, otherwise `L`
 * `score` - the team's score in the game
 * `kills` - kills *for the player*
 * `deaths` - deaths
 * `+/-` - plus-minus (derived, `kills` minus `deaths`)
 * `k/d` - kill-death ratio (derived, `kills` divided by `deaths`)
 * `kills per 10min` - kills per 10 minutes (derived)
 * `deaths per 10min` - deaths per 10 minutes (derived)
 * `assists` - assists
 * `headshots` - kills via headshot
 * `suicides` - kills from the environment (aka falling off the map)
 * `team kills` - friendly fire kills (aka killing a player on your own team)
 * `hits` - hits from a gun
 * `shots` - shots fired from a gun
 * `accuracy (%)` - hits per shot as a percentage (dervied)
 * `num lives` - total number of lives (WW2)
 * `time alive (s)` - total time alive (in s) (WW2)
 * `avg time per life (s)` - average time alive per life (WW2, derived, `time alive` divided by `num lives`)
 * `avg kill dist (m)` - average kill distance
 * `fave weapon` - most used primary gun per loadout
 * `fave rig` - most used rig per loadout (IW)
 * `fave payload` - most used rig payload per loadout (IW)
 * `fave trait` - most used rig trait per loadout (IW)
 * `fave division` - most used division per loadout (WW2)
 * `fave training` - most used basic training per loadout (WW2)
 * `fave scorestreaks` - top 3 scorestreaks used per loadout
 * `hill time (s)` - HP hill time in seconds
 * `hill captures` - HP hill captures
 * `hill defends` - HP hill defends
 * `snd rounds` - SND rounds
 * `snd firstbloods` - SND first kill of the round (killing a teammate does *not* count as firstbloods)
 * `snd firstdeaths` - SND first death of the round (WW2, being killed by a teammate *does* count as a firstdeath)
 * `snd survives` - SND alive at end of the round (WW2)
 * `bomb pickups` - SND bomb pickups
 * `bomb plants` - SND bomb plants
 * `bomb defuses` - SND bomb defuses
 * `bomb sneak defuses` - SND bomb sneak defuses (aka ninja defuse, when defuse completed with at least one opponent alive)
 * `snd 1-kill round` - _exactly_ 1 kill in an SND round
 * `snd 2-kill round` - 2 kills in an SND round
 * `snd 3-kill round` - 3 kills in an SND round
 * `snd 4-kill round` - 4 kills in an SND round (aka an Ace)
 * `uplink dunks` - UPL dunks (IW)
 * `uplink throws` - UPL throws (IW)
 * `uplink points` - UPL points (derived, `dunks` times 2 plus `throws`, IW)
 * `ctf captures` - CTF captures (WW2)
 * `ctf returns` - CTF returns (WW2)
 * `ctf pickups` - CTF pickups (anywhere, not just from opponent base, WW2)
 * `ctf defends` - CTF defends (aka killing an oppenent *near* your flag, WW2)
 * `ctf kill carriers` - CTF kill carriers (aka killing an opposing flag carrier, WW2)
 * `ctf flag carry time (s)` - CTF flag carry time (WW2)
 * `2-piece` - 2 kills by the player without dying, separated by <= 5 seconds (aka 2 kills in 5s max)
 * `3-piece` - 3 kills by the player without dying, each kill separated by <= 5 seconds (aka 3 kills in 10s max)
 * `4-piece` - 4 kills by the player without dying, each kill separated by <= 5 seconds (aka 4 kills in 15s max)
 * `multikills` - total multikills (IW, derived, sum of `2-piece` plus `3-piece` plus `4-piece`)
 * `4-streak` - 4 kills without dying (within a single round, otherwise no time restriction)
 * `5-streak` - 5 kills without dying
 * `6-streak` - 6 kills without dying
 * `7-streak` - 7 kills without dying
 * `8+-streak` - 8 or more kills without dying
 * `4+-streak` - 4 or more kills without dying (IW)
 * `scorestreaks earned` - number of scorestreaks earned
 * `scorestreaks used` - number of scorestreaks used
 * `scorestreaks deployed` - number of times a scorestreak is deployed (WW2, for Flamethrower and other multi-use scorestreaks)
 * `scorestreaks kills` - kills with a scorestreak (WW2)
 * `scorestreaks assists` - assists with a scorestreak (WW2)
 * `payloads earned` - number of payload abilities earned (IW)
 * `payloads used` - number of payload abilities used (IW)

Note: not all stats are present in all seasons or tournaments of Call of Duty World League as the rules can and do change.

## Missing Data

 * 2017
    * CWL Champs (Aug 9-13, 2017)
       - 297 of 298 games have complete data
       - hardware failure during a game between Envyus and Ghost Gaming (Winner's Quarterfinals - Map 2 - Search & Destory on Retaliation) resulted in partial data loss.  The failure occured with Envyus leading 4-0, resulting in data from the first 4 rounds to be lost.  Video replay allowed for manual recovery of all basic stats (`kills`, `deaths`, `firstblood`, `defuses`, ...), but some more complex stats were unrecoverable.
 * 2018
    * CWL Dallas (Dec 8-10, 2017)
       - 269 of 269 *elite* games have data (all pool play, plus both champ brackets)
       - use of a prohibited scorestreak resulted in a forfeit by Rise Nation of game 1 against Red Reserve in pool play, but that data IS included.
    * CWL New Orleans (Jan 12-14, 2018)
       - 280 of 280 *elite* games have data, added new `ctf flag carry time (s)` stat
       - flamethrower scorestreaks can be earned once, but "used" multiple times, fixing..
    * CWL Pro League, Stage 1 (Jan 23-Apr 8, 2018)
       - only week 1-2 so far