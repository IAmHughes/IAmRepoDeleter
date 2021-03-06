# IAmRepoCleaner
This script, `repo-cleaner`, will delete every repository matching a specific pattern for either a user or organization based on options passed through the command line. This solves the problem many of us experience when doing testing where multiple repositories are created and need to be deleted after the testing/debugging is finished.

## PRE-REQUISITES

#### AUTHENTICATION:
Before running this script, you must create a Personal Access Token (PAT) (see: [creating a personal access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) for more info) with the permissions `<repo>` and `<delete_repo>` scopes. You can read more about [Scopes for OAuth Apps here](https://developer.github.com/apps/building-oauth-apps/scopes-for-oauth-apps/). Once created, you must export your PAT as an environment variable named `<GITHUB_TOKEN>`.

  * Exporting PAT as `GITHUB_TOKEN`
 
```shell
export GITHUB_TOKEN=abcd1234efg567
```

## RUNNING THE SCRIPT

#### NAME:
repo-cleaner - Deletes every repository matching a specific name pattern for the user or org specified up to 30 at a time

#### SYNOPSIS:

```
repo-cleaner [-o=<org_name>] [-u=<username>] [-s=<string-to-match-against>]
```

#### DESCRIPTION:
Deletes every repository for the user (if `-u=<username>` is used) or for an organization (if `-o=<org_name>` is used instead) that matches the string (specified by `-s=<string-to-match-against>`). If `-s` is omitted it will list the repos available to delete instead. Will delete up to 30 repositories with every execution due to default pagination.

#### OPTIONS:

`--org` | `-o`

When running the tool, this flag sets the API endpoint to point to an organization (specififed by `-o=<org_name>`), deleting the repos that match the given string from `-s` (see below).
* _NOTE:_ Can NOT be used with the `-u` option.

`--user` | `-u`

When running the tool, this flag sets the API endpoint to point to a user (specified by `-u=<username>`), deleting the repos that match the given string from `-s` (see below).
* _NOTE:_ Can NOT be used with the `-o` option.

`--string` | `-s`

When running the tool, this flag sets the string to match against the name of the repo(s) you are wanting to delete. If omitted will list repositories for given user or organization (specified by `-u=<username>` or `-o=<org_name>`) without deleting any.

#### EXAMPLES:
* Lists repos under user account `IAmHughes` that are available to be deleted.

```shell
bash repo-cleaner -u=IAmHughes
```

* Deletes repos under org `TheBeardedTom` that are named `Test_Repo_`
  * For example: `Test_Repo_`, `Test_Repo_qa`, `Test_Repo_234`, etc. would be deleted.

```shell
bash repo-cleaner -o=TheBeardedTom -s=Test_Repo_
```

* Deletes repos under user `IAmHughes` that are named `MyRepo`
  * For example: `MyRepo`, `MyRepo1`, `MyRepo99`, `MyRepoQA`, etc. would all be deleted.

```shell
bash repo-cleaner -u=IAmHughes -s=MyRepo
```

#### API DOCUMENTATION:
All documentation can be found at the [GitHub Developer Docs](https://developer.github.com/v3/) page.

## CONTRIBUTING

Please read [CONTRIBUTING.md](https://github.com/IAmHughes/IAmRepoCleaner/blob/master/.github/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## AUTHORS

* **Thomas Hughes** - _Maintainer / On-Going Support_ - [@IAmHughes](https://GitHub.com/IAmHughes)
* **Michael Johnson** - _Initial Work_ - [@Migarjo](https://GitHub.com/Migarjo)

See also the list of [contributors](https://github.com/IAmHughes/IAmRepoCleaner/contributors) who participated in this project.

## LICENSE

This project is licensed under the MIT License - see the [LICENSE](https://github.com/IAmHughes/IAmRepoCleaner/blob/master/LICENSE) file for details.

## ACKNOWLEDGEMENTS

* Thanks to [@Migarjo](https://GitHub.com/Migarjo) for the initial base for the script.
