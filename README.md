# Repo stats

Generate statistics.

## What changed the most

```shell
git log --format=format: --name-only --since="1 year ago" | sort | uniq -c | sort -nr | head -20
```

The 20 most changed files last year.

## Who Built This

```shell
git shortlog -sn --no-merges
```

Every contributor ranked by commit count.

## Is This Project Accelerating?

```shell
git log --format='%ad' --date=format:'%Y-%m' | sort | uniq -c
```

Commit count by month.
