# PowerShellForGitHub PowerShell Module
## Changelog

  [0.14.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.14.0) - (2020/05/30)
### Features:
+ The module will now asynchronously check for updates up to once per day.  This can be disabled
  if desired with the `Set-GitHubConfiguration -DisableUpdateCheck`.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/185) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/a9f48a8aec796195664c3d86eb11755a1394d34e)
+ It turns out that `Group-GitHubPullRequest` which was written back in `0.2.0` was never actually
  exported.  Now it is.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/180) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/b7e1ea1cb912493e110b9854b0ec7700462254a0)

### Fixes:
- Fixes the behavior of `Get-GitHubRepository`.  It actually had a number of issues:
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/179) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/c4c1ec344a357489d248b9cf1bc2837484d4915f)
  - `-GetAllPublicRepositories` didn't acutally work.  Now it does, along with the newly
     added `Since` parameters.
  - Fixed the ParameterSet handling for all parameters to make sure that users can only specify
    the correct combination of parameters.
- Fixes multi-result behavior across all versions of PowerShell.  You can now reliably capture
  the result of an API call like this: `@(Get-GitHubRepository ...)` and be assured that you'll
  get an array result with the proper count of items.  As a result, this fixes all remaining failing
  UT's on PowerShell 7.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/199) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/bcd0a5616e1395ca480bc7f3b64776eada2a6670)
- Fixed an erroneous exception that occurred when calling `New-GitHubRepository` when specifying
  a `TeamId`.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/196) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/587e2042621091c79cc06be2aa9cc6ea836561f4)
- The module is now PSScriptAnalyzer clean (again).  This also fixed pipeline handling in
  `Group-GitHubPullRequest`, `Group-GitHubIssue` and `ConvertFrom-GitHubMarkdown`.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/180) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/b7e1ea1cb912493e110b9854b0ec7700462254a0)
- Fixed some documentation which referenced that private repos were only available to paid GitHub
  plans.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/191) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/3c70b8d2702a4a7b5674bb72decacb385f1a47a8)
- Fixed a bug preventing quering for a specifically named branch with `Get-GitHubRepositoryBranch`.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/188) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/5807d00ed0a3acd293057d8a9c06a9d68b6030db)
- Correctly fixed the hash that catches whether or not a developer has updated the settings file used
  when running this module's unit tests.  It involved updating the hash and then also ensuring we
  always check the file out with consistent line endings.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/181) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/93689d69eedc50f084982a6fba21183857507dbb) &&
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/183) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/b4439f4a6b12f89d755851b313eff0e9ea0b3ab5)
- Documentation updates around configuring unattended authentication.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/173) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/3440909f5f1264865ccfca85ce2364af3ce85425)

Authors:
   * [**@HowardWolosky**](https://github.com/HowardWolosky)

------

  [0.13.1](https://github.com/PowerShell/PowerShellForGitHub/tree/0.13.1) - (2020/05/12)
### Fixes:
- Ensure progress bar for Wait-JobWithAnimation gets marked as Completed
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/169) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/bb2ad45f61f4e55ba763d5eb402c80de5991bb6b)

Authors:
   * [**@HowardWolosky**](https://github.com/HowardWolosky)

------

  [0.13.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.13.0) - (2020/05/12)
### Improvement:
- Migrate REST API progress status to use Write-Progress
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/167) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/992f67871cd659dac20833487b326bdad7b85bd8)

Authors:
   * [**@HowardWolosky**](https://github.com/HowardWolosky)

------

 [0.12.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.12.0) - (2020/05/12)
### Features:
+ Added core support for Projects
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/160) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/1cdaac1a5af873589458bd0b40b3651187ec7e19)
+ Added suport for Project Columns
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/162) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/85170ce517dc4941518d51d788843a87612e25e0)
+ Added suport for Project Cards
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/163) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/3a87f2bd50a811f554d6cfaf085fede7aede6c76)
+ Added sample usage documentation for the new Project API's
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/164) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/1556b8b39cd61735aad14be0fb237c14e763f696)

### Fixes:
- Minor spelling fixes in documentation throughout module
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/165) | [[cl]](https://github.com/microsoft/PowerShellForGitHub/commit/6735ba57a5a43b61a37ef09d4021296dcd417dba)
- Fixed confirmation message for `Rename-GitHubRepository`
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/161) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/3fab72464e38cb573408add7e99d5a6bb0db2ea1)

Authors:
   * [**@jpomfret**](https://github.com/jpomfret)
   * [**@HowardWolosky**](https://github.com/HowardWolosky)

------

  [0.11.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.11.0) - (2020/04/03)
### Features:
+ Added `Get-GitHubContents`
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/146) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/9a45908dc65b3e8dd0227083fab281099cf07b1b)

Author: [**@Shazwazza**](https://github.com/Shazwazza)

------

  [0.10.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.10.0) - (2020/03/02)
### Features:
+ Added `Rename-GitHubRepository`
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/145) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/536b762425d51a181166c2c47ad2b00014911d1d)

Author: [**@mtboren**](https://github.com/mtboren)

------

  [0.9.2](https://github.com/PowerShell/PowerShellForGitHub/tree/0.9.2) - (2019/11/11)
### Fixes:
- Reduces the warning noise seen during execution of the unit tests.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/130) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/89f69f1132505f04e6b2ac38b6f5a93aef6ac947)

Author: [**@smaglio81**](https://github.com/smaglio81)

------

 [0.9.1](https://github.com/PowerShell/PowerShellForGitHub/tree/0.9.1) - (2019/09/24)
### Fixes:
- Ensure Milestone `due_on` always gets set to the desired date.
  (Attempts to work around odd GitHub behavior which uses PST/PDT's midnight to determine the date instead of UTC.)
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/133) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/013452b5cd8a7d7655cb32031d5ebdb580af16d9)
- Fix `Update-GitHubRepository` to work correctly
  - The REST endpoint had a typo in it
    [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/137) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/27920b1abefd3d33082cbf930e8965af36f86a6a)
  - The `Archived` switch's value was being incorrectly inverted
    [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/135) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/9bdb37c053f98f108d346050622b609d8488fd45)

Author: [**@HowardWolosky**](https://github.com/HowardWolosky)

------

 [0.9.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.9.0) - (2019/09/19)
### Features:
+ Added `Get-GitHubRelease`
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/125) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/7ea773c715525273dddd451d2a05f429e7fe69e1)
+ Added `New-GitHubPullRequest`
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/111) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/788465faec1b6d6331537aa87c2d94039682e373)

### Fixes:
- Updates the GitHub Enterprise support to use the `http(s)://[hostname]/api/v3` syntax
  instead of the non-standard `http(s)://api.[hostname]/` syntax.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/118) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/f7b956da4ae169ec6ec1bb6582ce742372677f5c)
- Minor Comment Based Help (CBH) update for Get-GitHubRepository
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/120) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/220333a71214fb88a33093b5e907d431dcfdb4c8)

Authors:
   * [**@smaglio81**](https://github.com/smaglio81)
   * [**@rjmholt**](https://github.com/rjmholt)
   * [**@v2kiran**](https://github.com/v2kiran)
   * [**@PrzemyslawKlys**](https://github.com/PrzemyslawKlys)

------

 [0.8.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.8.0) - (2019/04/12)
### Features:
+ Added support for GitHub Enterprise users by adding a new `ApiHostName` configuration value.
  ([more info](https://github.com/Microsoft/PowerShellForGitHub/blob/master/README.md#github-enterprise))
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/101) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/d5acd0f73d97f6692914976ce9366456a59cbf70)

### Fixes:
- Renamed `ConvertFrom-Markdown` to `ConvertFrom-GitHubMarkdown` to avoid a conflict with
  PSCore's new `ConvertFrom-Markdown` command.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/100) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/088f95b5a1340c7ce570e6e68a41967fd5760c46)

Authors:
   * [**@Cellivar**](https://github.com/Cellivar)
   * [**@HowardWolosky**](https://github.com/HowardWolosky)

------

 [0.7.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.7.0) - (2019/03/15)
### Features:
+ Added `Test-GitHubOrganizationMember` to test if a user is in an organization.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/90) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/c60bb29ac02e7ab9fcd2e29db865b63876cb0125)
+ Updated `Get-GitHubTeamMember` to optionally work directly with a TeamId.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/90) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/c60bb29ac02e7ab9fcd2e29db865b63876cb0125)

### Fixes:
- Modified all [int] parameters to be [int64] to avoid out of bounds issues with large ID's.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/94) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/a22739e7f535faf4c5f486694bd213782437e82a)
- `Split-GitHubUri` updated to work with the `https://api.github.com/*` uri's included in some of
  the REST responses.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/88) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/592167de9b3f07635c49365e291082fd3f712586)

Author: [**@HowardWolosky**](https://github.com/HowardWolosky)

------

 [0.6.4](https://github.com/PowerShell/PowerShellForGitHub/tree/0.6.4) - (2019/01/16)
### Fixes:
- Updated the `*-GitHubIssue` functions to support specifying the `MediaType` that should be used
  for the returned result.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/83) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/e3b6c53017abd36fc70253e1a49c31046c885ad1)

Author: [**@joseartrivera**](https://github.com/joseartrivera)

------

## [0.6.3](https://github.com/PowerShell/PowerShellForGitHub/tree/0.6.3) - (2019/01/07)
### Fixes:
- Updated all parameter sets to use `CamelCase` for the permitted options, and stopped
  any use of abbreviation, to be more consistent with the rest of PowerShell.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/81) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/185441078efeb0e6693eafeb023785388a1a5a69)

Author: [**@HowardWolosky**](https://github.com/HowardWolosky)

------

## [0.6.2](https://github.com/PowerShell/PowerShellForGitHub/tree/0.6.2) - (2018/12/13)
### Fixes:
- Fixes a bug preventing Labels from being correctly added at the time of new Issue creation or
  modified when updating an issue.
  {[[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/76) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/3b6e84cbafaf044e2154a06612b1c43a873cd002) and
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/78) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/577f07bd219e9b5c03d481e562fd7f2fc3586474)}

Authors:
   * [**@lazywinadmin**](https://github.com/lazywinadmin)
   * [**@HowardWolosky**](https://github.com/HowardWolosky)

------

## [0.6.1](https://github.com/PowerShell/PowerShellForGitHub/tree/0.6.1) - (2018/12/13)
### Fixes:
- Fixes a bug with checking Issues.  When trying to list all issues, it tried to speficially look
  for Issue 0.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/73) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/bf6764080ce1291cfe2530a39ffd292f38b37440)

Authors:
   * [**@joseartrivera**](https://github.com/joseartrivera)

------

## [0.6.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.6.0) - (2018/12/13)
### Features:
+ Completes all support for GitHub Issue API's:
  + Added support for the [Issue Event](https://developer.github.com/v3/issues/events/) API's.
    [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/64) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/06e25243086954013b50c1fa7e3eb11bc34a9501)
  + Added support for the [Issue Milestone](https://developer.github.com/v3/issues/milestones/) API's.
    [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/62) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/2bd244768d0bed85943e5e8375bb3f5bebdc763b)
  + Added support for the [Issue Label](https://developer.github.com/v3/issues/labels/) API's.
    [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/59) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/6c7355424828d5ada457bdbe2182c8fdf6845641)
+ Added new `LogRequestBody` configuration option to help with development, allowing you to see the
  exact body of the REST request being sent before it is sent over the wire.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/60) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/98aec29d61bf013a153705079703ae027cc25c9f)

Authors:
   * [**@HowardWolosky**](https://github.com/HowardWolosky)
   * [**@joseartrivera**](https://github.com/joseartrivera)
   * [**@etgottli**](https://github.com/etgottli)

------

## [0.5.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.5.0) - (2018/11/30)
### Features:
+ Added support for the [Issue Comment](https://developer.github.com/v3/issues/comments/) API's.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/53) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/28b314bd7c0a810848e1acb3df43a1d83291be7b)
+ Added support for the [Issue Assignee](https://developer.github.com/v3/issues/assignees/) API's.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/54) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/680696a833b3cc753e961fc8c723b0be9b39ecc2)

### Fixes:
- Fixed bug that caused single or empty arrays returned within objects to be flattened
  (instead of remaining as arrays)
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/56) | [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/6cf344fb38485275f94b1e85c1a5f932e1b519c3)

Authors:
   * [**@HowardWolosky**](https://github.com/HowardWolosky)
   * [**@joseartrivera**](https://github.com/joseartrivera)

------

## [0.4.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.4.0) - (2018/11/16)
### Features:
+ Added support for the [Repository Traffic API's](https://developer.github.com/v3/repos/traffic/).
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/49) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/8d2e76f9059f0939b892d08386fe43f0e2722bb0)

### Fixes:
- Made NuGet dll retrieval more robust by preventing potential file access problems from being
  written to the error stream.
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/48) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/b614f4a0fbcb570ef462fea64f776ca85480de86)
- Prevented the possibility of Access Tokens from being written into the log file in plain text
  if explicitly passed-in
  [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/50) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/c6835f4cb1ef0e78e23a8195949eb9ad2555fd4a)

Authors:
   * [**@HowardWolosky**](https://github.com/HowardWolosky)
   * [**@joseartrivera**](https://github.com/joseartrivera)

------

## [0.3.1](https://github.com/PowerShell/PowerShellForGitHub/tree/0.3.1) - (2018/11/13)
### Fixes:
- Minor static analysis issues fixed.
- Corrected name of the test file for `GitHubRepositoryForks`
- Ensured the `getParams` are used during execution of `Get-GitHubRepositoryFork`

More Info: [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/42) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/5703295d497f20fe8eec91d6ed47d126cc518592)

Author: [**@HowardWolosky**](https://github.com/HowardWolosky)

------

## [0.3.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.3.0) - (2018/11/13)
### Features:
+ Added support for querying forks and creating new ones.

### Fixes:
- Will only perform a retry when receiving a `202` response on a `GET` request.  Previously, it would
  retry regardless of the method of the request.

More Info: [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/41) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/1076239d7639497984a6e0b04df1e69019c4ec28)

Author: [**@HowardWolosky**](https://github.com/HowardWolosky)

------

## [0.2.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.2.0) - (2018/11/13)
### Features:
+ Significant restructing and refactoring of entire module to make future expansion easier.
+ Significant documentation updates ([CHANGELOG](./CHANGELOG.md), [CONTRIBUTING.md](./CONTRIBUTING.md),
  [GOVERNANCE.md](./GOVERNANCE.md), [README.md](./README.md), [USAGE.md](./USAGE.md))
+ Added `Set-GitHubAuthentication` (and related methods) for securely caching the Access Token
+ Added `Set-GitHubConfiguration` (and related methods) to enable short and long-term configuration
  of the module.
+ Added ability to asynchronously see status update of REST requests.
+ Added logging and telemetry to the module (each can be disabled if desired).
+ Tests now auto-configure themselves across whatever account information is supplied in
  [Tests/Config/Settings.ps1](./Tests/Config/Settings.ps1)
+ Added support for a number of additional GitHub API's:
  + All [Miscellaneous API's](https://developer.github.com/v3/misc/)
  + Ability to fully query, update, remove, lock, and unlock Issues.
  + Enhanced pull request querying support
  + Ability tofully query, create, and remove Repositories, as well as transfer ownership,
    get tags, get/set topic and current used programming languages.
  + Enhanced user query support as well as being able update information for the current user.

### Fixes:
- Made parameter ordering consistent across all functions (OwnerName is now first, then RepositoryName)
- Normalized all parameters to use SentenceCase
- All functions that can take a Uri or OwnerName/RepositoryName now support both options.
- Made all parameter names consistent across functions:
  - `GitHubAccessToken` -> `AccessToken`
  - `RepositoryUrl` -> `Uri`
  - `Organization` -> `OrganizationName`
  - `Repository` -> `RepositoryName`
  - `Owner` -> `OwnerName`
- Normalized usage of Verbose, Info and Error streams

### Functionality Modified from 0.1.0:
* `New-GitHubLabels` was renamed to `Set-GitHubLabel` and can now optionally take in the labels
  to apply to the Repository.
* `Get-GitHubIssueForRepository` has been removed and replaced with `Get-GitHubIssue`.
  The key difference between these two is that it no longer accepts multiple repositories as single
  input, and filtering on creation/closed date can be done after the fact piping the results into
  `Where-Object` now that the returned objects from `Get-GitHubIssue` have actual `[DateTime]` values
  for the date properties.  For an updated example of doing this, refer to [example usage](USAGE.md#querying-issues).
* `Get-GitHubWeeklyIssueForRepository` has been removed and functionally replaced by `Group-GitHubIssue`.
  For an updated example of using it, refer to [example usage](USAGE.md#querying-issues)
* `Get-GitHubTopIssueRepository` has been removed.  We have [updated examples](USAGE.md#querying-issues)
  for how to accomplish the same scenario.
* `Get-GitHubPullRequestForRepository` has been removed and replaced with `Get-GitHubPullRequest`.
  The key difference between these two is that it no longer accepts multiple repositories as single
  input, and filtering on creation/merged date can be done after the fact piping the results into
  `Where-Object` now that the returned objects from `Get-GitHubPullRequest` have actual `[DateTime]` values
  for the date properties.  For an updated example of doing this, refer to [example usage](USAGE.md#querying-pull-requests).
* `Get-GitHubWeeklyPullRequestForRepository` has been removed and functionally replaced by `Group-GitHubPullRequest`.
  For an updated example of using it, refer to [example usage](USAGE.md#querying-pull-requests)
* `Get-GitHubTopPullRequestRepository` has been removed.  We have [updated examples](USAGE.md#querying-pull-requests)
  for how to accomplish the same scenario.
* `Get-GitHubRepositoryNameFromUrl` and `GitHubRepositoryOwnerFromUrl` have been removed and
  functionally replaced by `Split-GitHubUri`
* `Get-GitHubRepositoryUniqueContributor` has been removed.  We have an
  [updated example](USAGE.md#querying-contributors) for how to accomplish the same scenario.
* `GitHubOrganizationRepository` has been removed.  You can now retrieve repositories for an
  organization via `Get-GitHubRepository -OrganizationName <name>`.
* `Get-GitHubAuthenticatedUser` has been replaced with `Get-GitHubUser -Current`.

More Info: [[pr]](https://github.com/PowerShell/PowerShellForGitHub/pull/39) | [[cl]](https://github.com/PowerShell/PowerHellForGitHub/commit/eb33688e5b8d688d28e8582b76b526da3c4428be)

Author: [**@HowardWolosky**](https://github.com/HowardWolosky)

------

## [0.1.0](https://github.com/PowerShell/PowerShellForGitHub/tree/0.1.0) - (2016/11/29)
### Features:
+ Initial public release

More Info: [[cl]](https://github.com/PowerShell/PowerShellForGitHub/commit/6a3b400019d6a97ccc2f08a951fd4b2d09282eb5)

Author: [**@KarolKaczmarek**](https://github.com/KarolKaczmarek)
