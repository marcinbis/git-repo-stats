# Repository statistics

This project generates visual summaries of Git activity for a repository.

## Usage

From the root of the repository you want to analyze:

```shell
cd /path/to/your/repo
/path/to/repo-stats/mkstats.sh > index.html
```

Sample outputs are available under `examples/`:

* [git-repo-stats-index.html](examples/git-repo-stats-index.html) - Example from this repository, representing an edge case with only a single contributor and a small number of commits.
* [linux-kernel-index.html](examples/linux-kernel-index.html) - Example from the Linux Kernel repository, representing the opposite extreme. This file contains 1.5MB of data and the resulting graphs can be difficult to interpret. Nevertheless, the script executes correctly even on such large codebases.

## Most frequently changed files

The twenty files with the most changes over the past year. A single file standing out often indicates where most development or bugs resolution is concentrated.

```shell
git log --format=format: --name-only --since="1 year ago" | sort | uniq -c | sort -nr | head -20
```

## Contributors

Contributors ranked by commit count. The first chart covers the full project history; the second is limited to the year-to-date. Together they help illustrate whether participation is stable or whether the contributor mix shifts over time.

This metric also provides insight into the project's bus factor, indicating how many contributors would need to become unavailable before knowledge or progress is significantly impacted.

```shell
git shortlog -sn --no-merges #--since="1 year ago
```

## Commit velocity

Commits aggregated by calendar month, useful for observing trends in activity over time.

```shell
git log --format='%ad' --date=format:'%Y-%m' | sort | uniq -c
```

## Disclaimer

These statistics are a coarse view of repository activity. They should not be used as the primary basis for performance reviews or compensation decisions. Commit counts and similar aggregates are weak proxies for value delivered.

* Complex work (for example, difficult algorithms or careful design) may require substantial time while producing relatively few commits.
* Areas such as optimization or hardware-related troubleshooting in embedded systems often involve extensive investigation and testing that does not map cleanly to commit volume.
