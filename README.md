# Soccer 2026 - Match Schedule Data

This repository contains the match schedule data for the FIFA World Cup 2026 app.

## Data Files

| File | Description |
|------|-------------|
| `world-cup-schedule.json` | Base schedule with all 104 matches (72 group + 32 knockout) |
| `mock-after-groups.json` | Mock state after group stage complete |
| `mock-after-round32.json` | Mock state after Round of 32 complete |
| `mock-after-round16.json` | Mock state after Round of 16 complete |
| `mock-after-quarterfinals.json` | Mock state after Quarterfinals complete |
| `mock-after-semifinals.json` | Mock state after Semifinals complete |
| `mock-germany-won-final.json` | Mock: Germany wins World Cup |
| `mock-germany-lost-final.json` | Mock: Germany loses in semifinal |

## Match Data Schema

Each match object contains:

```json
{
  "id": "m1",
  "homeTeamId": "usa",
  "awayTeamId": "mex",
  "dateTime": "2026-06-11T20:00:00-04:00",
  "venue": "MetLife Stadium",
  "city": "New York",
  "stage": "GROUP",
  "groupMatchNumber": 1,
  "homeScore": null,
  "awayScore": null,
  "homePenalties": null,
  "awayPenalties": null,
  "status": "SCHEDULED",
  "possibleHomeTeamIds": null,
  "possibleAwayTeamIds": null
}
```

### Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique match identifier (e.g., "m1", "r32_1", "qf_1", "sf_1", "final") |
| `homeTeamId` | string/null | 3-letter country code (null if TBD) |
| `awayTeamId` | string/null | 3-letter country code (null if TBD) |
| `dateTime` | string | ISO 8601 datetime with timezone |
| `venue` | string | Stadium name |
| `city` | string | Host city |
| `stage` | string | Tournament stage (GROUP, ROUND_OF_32, ROUND_OF_16, QUARTERFINAL, SEMIFINAL, THIRD_PLACE, FINAL) |
| `groupMatchNumber` | number/null | Match number within group (1-3), null for knockout |
| `homeScore` | number/null | Final home score (null if not played) |
| `awayScore` | number/null | Final away score (null if not played) |
| `homePenalties` | number/null | Penalty shootout goals for home (null if no shootout) |
| `awayPenalties` | number/null | Penalty shootout goals for away (null if no shootout) |
| `status` | string | "SCHEDULED" or "FINISHED" |
| `possibleHomeTeamIds` | array/null | Possible teams for scheduled knockout matches |
| `possibleAwayTeamIds` | array/null | Possible teams for scheduled knockout matches |

## Tournament Bracket

### Round of 32 to Round of 16
- R16 matchups based on R32 winners from specific pairings
- R32_1 winner vs R32_7 winner = R16_1
- R32_2 winner vs R32_8 winner = R16_2
- etc.

### Round of 16 to Quarterfinals
- QF_1: R16_1 winner vs R16_2 winner
- QF_2: R16_3 winner vs R16_4 winner
- QF_3: R16_5 winner vs R16_6 winner
- QF_4: R16_7 winner vs R16_8 winner

### Quarterfinals to Semifinals
- SF_1: QF_1 winner vs QF_2 winner
- SF_2: QF_3 winner vs QF_4 winner

### Semifinals to Final
- 3rd Place: SF_1 loser vs SF_2 loser
- Final: SF_1 winner vs SF_2 winner

## Usage

The app fetches data from GitHub raw URLs:

```
https://raw.githubusercontent.com/mhollweck/s2026data/main/world-cup-schedule.json
```

## Team Codes

Teams use 3-letter ISO country codes:
- `usa` - United States
- `mex` - Mexico
- `can` - Canada
- `ger` - Germany
- `fra` - France
- `eng` - England
- `arg` - Argentina
- `bra` - Brazil
- `esp` - Spain
- etc.

## License

Data is for the Soccer 2026 app project.
