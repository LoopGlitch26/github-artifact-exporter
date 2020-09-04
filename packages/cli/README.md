# github-exporter

Exporter for GitHub

<!-- toc -->
* [github-exporter](#github-exporter)
* [Usage](#usage)
* [Commands](#commands)
<!-- tocstop -->

# Usage

This script requires a `personal access token` with access to the repository you are exporting from. The `owner` and `repo` arguments can be found in the repository url.

See the table below for examples of `owner` and `repo`

| Description               | URL                        | owner | repo |
| ------------------------- | -------------------------- | ----- | ---- |
| GitHub.com example        | https://github.com/foo/bar | foo   | bar  |
| GitHub Enterprise example | https://ghe.host/foo/bar   | foo   | bar  |

<!-- usage -->
```sh-session
$ npm install -g @github/github-exporter-cli
$ github-exporter COMMAND
running command...
$ github-exporter (-v|--version|version)
@github/github-exporter-cli/1.5.8 darwin-x64 node-v12.18.1
$ github-exporter --help [COMMAND]
USAGE
  $ github-exporter COMMAND
...
```
<!-- usagestop -->

## Examples

### Exporting issues

```
github-exporter.exe search:issues --owner github --repo caseflow --token <github-token> --since 2020-06-01 --until 2020-06-08 --format CSV > issue_export.csv
```

### Exporting closed issues with specific labels

```
github-exporter.exe search:issues --owner github --repo caseflow --token <github-token> --state closed --updatedSince 2020-06-01 --updatedUntil 2020-06-08 --labels "Type: Bug" --format CSV > issue_export.csv
```

### Exporting commits

```
github-exporter.exe repo:commits --owner github --repo caseflow --token <github-token> --since 2020-06-01 --until 2020-06-08 --format CSV > commit_export.csv
```

### Exporting pull requests

```
github-exporter.exe repo:pulls --owner github --repo caseflow --token $GITHUB_TOKEN --format CSV > pulls_export.csv
```

# Commands

<!-- commands -->
* [`github-exporter help [COMMAND]`](#github-exporter-help-command)
* [`github-exporter repo`](#github-exporter-repo)
* [`github-exporter repo:commits`](#github-exporter-repocommits)
* [`github-exporter repo:milestones`](#github-exporter-repomilestones)
* [`github-exporter repo:pulls`](#github-exporter-repopulls)
* [`github-exporter repo:releases`](#github-exporter-reporeleases)
* [`github-exporter search`](#github-exporter-search)
* [`github-exporter search:issues`](#github-exporter-searchissues)

## `github-exporter help [COMMAND]`

display help for github-exporter

```
USAGE
  $ github-exporter help [COMMAND]

ARGUMENTS
  COMMAND  command to show help for

OPTIONS
  --all  see all commands in CLI
```

_See code: [@oclif/plugin-help](https://github.com/oclif/plugin-help/blob/v3.1.0/src/commands/help.ts)_

## `github-exporter repo`

Export GitHub artifacts from a repository

```
USAGE
  $ github-exporter repo

OPTIONS
  --baseUrl=baseUrl    [default: https://api.github.com] GitHub base url
  --format=(JSON|CSV)  [default: JSON] export format
  --owner=owner        GitHub repository owner
  --repo=repo          GitHub repository name
  --token=token        (required) GitHub personal access token
```

_See code: [src/commands/repo.ts](https://github.com/github/github-exporter/blob/v1.5.8/src/commands/repo.ts)_

## `github-exporter repo:commits`

Export GitHub Commits for a repository

```
USAGE
  $ github-exporter repo:commits

OPTIONS
  --baseUrl=baseUrl    [default: https://api.github.com] GitHub base url
  --branch=branch      [default: master] git branch to export commits for
  --format=(JSON|CSV)  [default: JSON] export format
  --owner=owner        GitHub repository owner
  --repo=repo          GitHub repository name
  --since=since        search commits created after yyyy-mm-dd
  --token=token        (required) GitHub personal access token
  --until=until        search commits created before yyyy-mm-dd
```

_See code: [src/commands/repo/commits.ts](https://github.com/github/github-exporter/blob/v1.5.8/src/commands/repo/commits.ts)_

## `github-exporter repo:milestones`

Export GitHub Milestones for a repository

```
USAGE
  $ github-exporter repo:milestones

OPTIONS
  --baseUrl=baseUrl    [default: https://api.github.com] GitHub base url
  --format=(JSON|CSV)  [default: JSON] export format
  --owner=owner        GitHub repository owner
  --repo=repo          GitHub repository name
  --token=token        (required) GitHub personal access token
```

_See code: [src/commands/repo/milestones.ts](https://github.com/github/github-exporter/blob/v1.5.8/src/commands/repo/milestones.ts)_

## `github-exporter repo:pulls`

Export GitHub Pull Requests for a repository

```
USAGE
  $ github-exporter repo:pulls

OPTIONS
  --baseUrl=baseUrl    [default: https://api.github.com] GitHub base url
  --format=(JSON|CSV)  [default: JSON] export format
  --owner=owner        (required) GitHub repository owner
  --repo=repo          (required) GitHub repository name
  --token=token        (required) GitHub personal access token
```

_See code: [src/commands/repo/pulls.ts](https://github.com/github/github-exporter/blob/v1.5.8/src/commands/repo/pulls.ts)_

## `github-exporter repo:releases`

Export GitHub Releases for a repository

```
USAGE
  $ github-exporter repo:releases

OPTIONS
  --baseUrl=baseUrl    [default: https://api.github.com] GitHub base url
  --format=(JSON|CSV)  [default: JSON] export format
  --owner=owner        GitHub repository owner
  --repo=repo          GitHub repository name
  --token=token        (required) GitHub personal access token
```

_See code: [src/commands/repo/releases.ts](https://github.com/github/github-exporter/blob/v1.5.8/src/commands/repo/releases.ts)_

## `github-exporter search`

GitHub Search base command

```
USAGE
  $ github-exporter search

OPTIONS
  --baseUrl=baseUrl    [default: https://api.github.com] GitHub base url
  --format=(JSON|CSV)  [default: JSON] export format
  --owner=owner        GitHub repository owner
  --repo=repo          GitHub repository name
  --token=token        (required) GitHub personal access token
```

_See code: [src/commands/search.ts](https://github.com/github/github-exporter/blob/v1.5.8/src/commands/search.ts)_

## `github-exporter search:issues`

Export GitHub Issues using Search

```
USAGE
  $ github-exporter search:issues

OPTIONS
  --baseUrl=baseUrl            [default: https://api.github.com] GitHub base url
  --format=(JSON|CSV)          [default: JSON] export format
  --jira                       transform output into a usable format for importing to Jira
  --labels=labels              search issues with these labels (comma seperated)
  --owner=owner                GitHub repository owner
  --query=query                Search query matching GitHub issue search syntax
  --repo=repo                  GitHub repository name
  --since=since                search issues created after yyyy-mm-dd
  --state=(open|closed)        search issues in this state
  --token=token                (required) GitHub personal access token
  --until=until                search issues created before yyyy-mm-dd
  --updatedSince=updatedSince  search issues updated after yyyy-mm-dd
  --updatedUntil=updatedUntil  search issues updated before yyyy-mm-dd
```

_See code: [src/commands/search/issues.ts](https://github.com/github/github-exporter/blob/v1.5.8/src/commands/search/issues.ts)_
<!-- commandsstop -->