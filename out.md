# High level description of the setup

## Setup task group: init

A series of commands and tools you must absolutely
install first, before doing anything else


### Setup item: Scoop

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|Package Manager|highest|False|False|

#### Description:

The single best package manager on Windows, chocolatey is
similar but scoop is best.



```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
irm get.scoop.sh | iex
```

### Setup item: Aria2

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|Downloader|highest|False|False|

#### Description:

Scoop can leverage Aria2 to download every package using parallel processes
and thus make your installs go much faster. Very important to get first.



```powershell
scoop install aria2
```

### Setup item: git

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|highest|False|False|

#### Description:

You can't do much without git nowadays, this is the most widely used,
if not the 'universal' versioning tool. Any software that is distributed
online is most likely using git at some point of its integration pipeline.
If you don't have git, you can't download much on windows.



```powershell
scoop install git
```

### Setup item: sudo

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|highest|False|False|

#### Description:

A famous command from the unix world that temporarily gives you administrator privileges
for the command you're about to run (only). A great way to quickly obtain admin privileges
while running CLI tools.



```powershell
scoop install sudo
```

### Setup item: Scoop-Buckets

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|Package repositories|highest|False|False|

#### Description:

Buckets are a way to group scoop packages. The barebones required
packages are 'pre-installed' in the 'main' bucket, but then you can
add any bucket to have access to other repositories.



```powershell
scoop bucket add extras
scoop bucket add versions
scoop bucket add nerd-fonts
```

### Setup item: Windows Terminal

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|Terminal|highest|False|False|

#### Description:

Simply the best way to run shells and CLI apps on Windows
as of today.



```powershell
scoop install windows-terminal
reg import $( Resolve-Path "~\scoop\apps\windows-terminal\current\install-context.reg")
scoop install vcredist2022
scoop uninstall vcredist2022
```

### Setup item: coreutils

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|highest|False|False|

#### Description:

A scoop package that helps you have access to important CLI basics which are
usually pre-installed on unix but not on windows.



```powershell
scoop install coreutils
```

### Setup item: psutils

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|highest|False|False|

#### Description:

A scoop package that helps you have access to important CLI basics which are
usually pre-installed on unix but not on windows.



```powershell
scoop install psutils
```

### Setup item: zoxide

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|highest|False|True|

#### Description:

A native powershell implementation of the `z` command that moves you to the best match directory
based on frequency of visited dirs or other variables, no matter your current position.
Equivalent of "teleportation" in terms of `cd` type commands.



```powershell
scoop install zoxide
```

### Setup item: gh

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|highest|False|False|

#### Description:

The very useful github CLI tool, allows to create repos and releases from the command line.
Don't miss this one, very useful :)



```powershell
scoop install gh
```

### Setup item: Python

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|language|highest|True|False|

#### Description:

The slow but insanely popular language most data science & applied math
folks use. We're going to assume you'll be using this language before any other
if you're a random person, or someone who wishes to perform some data related task.
Okay, R exists, but it's much less universal.



```powershell
scoop install python
regedit.exe /s $(Resolve-Path "~/scoop/apps/python/current/install*reg")
```

### Setup item: Go

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|language|highest|False|False|

#### Description:

A relatively fast and C++ like modern language from Google.
A lot of important CLI tools can be instantly installed using
the `go install github.com/<user>/<repo>@latest` which makes it
incredibly potent for fast setups



```powershell
scoop install go
```

### Setup item: Ghrel

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|important|False|False|

#### Description:

A CLI tool that instantly downloads latest releases from github repositories.
You just have to `ghrel github.com/<user>/<repo>@latest` and you instantly get the
content. Very useful to download portable exes or fonts from github



```powershell
go install github.com/jreisinger/ghrel@latest
```

### Setup item: Bat

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|important|False|False|

#### Description:

A much friendlier version of cURL and `irm` written in go



```powershell
go install github.com/astaxie/bat
```

### Setup item: jq-yq

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|important|False|False|

#### Description:

CLI to filter/process json (jq) or YAML (yq).
Both are fairly important and useful, so having them cannot hurt.



```powershell
scoop install jq
scoop install yq
```

### Setup item: Nerd-Fonts

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|font|important|True|False|

#### Description:

Nerd fonts are a special kind of font that has been designed to make code
and other technical (scientific, math) syntax much more pleasing and easy to read.
Most people who code a lot use Nerd-Fonts because it just makes it much more appealing.



```powershell
sudo scoop install -g FiraCode-NF
sudo scoop install -g Iosevka-NF
```

### Setup item: Terminal-Icons

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|UI|preferable|False|False|

#### Description:

Useful as a complement to Nerd fonts and/or starship/oh-my-posh.



```powershell
Install-Module -Name Terminal-Icons -Repository PSGallery
```

### Setup task group: dev

These are developper (or more advanced) options which are good to have,
but are more consuming. They involve downloading Visual Studio C++ Build Tools,
which at least takes 5 minutes. This way you then have access to the entire rust
toolchain and can install rust CLIs and tools.


#### Setup item: Visual Studio Build Tools

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|toolkit|highest|False|False|

##### Description:

The absolute minimum to have in order to compile lots of low level code,
and a necessity to use rust's `cargo install` command.



```powershell
Invoke-WebRequest -Uri 'https://aka.ms/vs/17/release/vs_BuildTools.exe' -OutFile "$env:TEMP\vs_BuildTools.exe"
& "$env:TEMP\vs_BuildTools.exe" --force --quiet --wait --add Microsoft.VisualStudio.Workload.VCTools --includeRecommended --remove Microsoft.VisualStudio.Component.VC.CMake.Project
$startTime = $(Get-Date).Ticks
While ($(ps | sls vs_BuildTools).Length -gt 0) {
  $currTime = $startTime = $(Get-Date).Ticks
  $elapsed = $currTime - $startTime
  Write-
}

```

#### Setup item: Git-Semver

|Type|Priority|Admin Rights|Content to append to PATH|
|:-:|:-:|:-:|:--|
|CLI|useful|False|False|

##### Description:

A go implementation of the git semantic revisioning tag cli.
Automatically bumps versions like 01.32.12 to 01.32.13 etc.



```powershell
go install github.com/maykonlf/semver-cli/cmd/semver@latest
```

