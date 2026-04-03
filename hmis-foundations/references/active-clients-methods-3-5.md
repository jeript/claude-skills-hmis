# Active Clients - Methods 3 and 5 (Full Pseudocode)

## Method 3: Active Clients in Residence

Requires client to be in residence at a project. Applies to any lodging or residential project.

```
[project start date] <= [report end date]
and (
    [project exit date] is null or [project exit date] > [report start date]
)
and (
    (   [project type] = 1
        and
        [date of bed-night] >= [report start date]
        and
        [date of bed-night] <= [report end date]
        and
        [date of bed-night] >= [project start date]
        and
        ( [date of bed-night] < [project exit date] or [project exit date] is null )
    )
    or (
        [project type] = 0, 2, 8
    )
    or (
        [project type] = 3, 9, 10, 13
        and
        [housing move-in date] <= [report end date]
        and
        [housing move-in date] >= [project start date]
        and
        ( [housing move-in date] < [project exit date] or [project exit date] is null )
    )
)
```

## Method 5: 1+ Nights Active

Some reports require filtering active clients to only include those active at least one night in the report period. Similar to Method 3, except PH projects do NOT require a [housing move-in date] before the [report end date].

```
[project start date] <= [report end date]
and (
    [project exit date] is null or [project exit date] > [report start date]
)
and (
    (   [project type] = 1
        and
        [date of bed-night] >= [report start date]
        and
        [date of bed-night] <= [report end date]
        and
        [date of bed-night] >= [project start date]
        and
        ( [date of bed-night] < [project exit date] or [project exit date] is null )
    )
    or (
        [project type] = 0, 2, 3, 8, 9, 10, 13
    )
)
```
