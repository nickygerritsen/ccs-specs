# Draft

This is a draft standard for the ICPC 2016 Finals, upon approval this
draft status will change to Final Approved status. The Final version
will have a version number and date.

Also, note that this format is not intended for archiving contests.
Instead one should use the [Contest Archive
Format](Contest_Archive_Format "wikilink").

# Introduction

Many Contest Control Systems and related tools rely on the specification
of configuration and control information for both initializing and
running a contest. A *Contest Data Package (CDP)* is an organized
structure of files/directories that are input to and output from a
contest. A CDP is a single arbitrarily-named folder which contains
various explicitly-named files and subfolders as described below.

The purpose of this specification is to identify the Contest Data
Package organization expected by Contest Control Systems and related
tools which support the specifications of the ICPC World Finals. Many of
these software systems and tools can be completely configured simply by
pointing them to a correctly-organized CDP.

A CDP contains two types of data: *Input Data* which is used to
configure and/or control a software system or tool, and *Output Data*
which is generated by the software system or tool and is intended to be
added post-contest to the CDP for archival purposes.

# Input Data

These are files and folders which provide input/configuration
information for a contest.

## config folder

Contains data used to configure a CCS. The name of the folder must be
"config", it must reside directly in the root folder of the CDP, and it
must contain the following files and folders:

  - [contest.yaml](Contest_Control_System#contest.yaml "wikilink")
  - [problemset.yaml](Contest_Control_System#problemset.yaml "wikilink")
  - [groups.tsv](Contest_Control_System#groups.tsv "wikilink")
  - [teams.tsv](Contest_Control_System#teams.tsv "wikilink")
  - [userdata.tsv](Contest_Control_System#userdata.tsv "wikilink")
  - One folder for each contest problem defined in the
    [problemset.yaml](Contest_Control_System#problemset.yaml "wikilink")
    file. The folder name matches the short-name in problemset.yaml for
    that problem. The data for each problem directory is described in
    [Problem format](Problem_format "wikilink")

## images folder

This folder, which must be named "images", contains subfolders for
various types of contest image data, including

  - logo -- holds team (university) logo images
  - team -- holds team pictures (typically, a photograph of the team
    members)
  - icon -- holds icon-sized versions of the team (university) logo
    images
  - overlay -- holds overlay images containing team logos and
    team/university names

### images/logo folder

This folder holds one 600x600 image file for each contest team
containing the team's logo (typically, the University Logo). Each team
logo must be in a separate PNG-format file whose name is X.png, where X
is the team number (e.g., 1.png, 102.png, etc.).

### images/team folder

This folder holds one 1920x1080 image file for each contest team
containing the team's picture (typically for example taken during
contest registration). Each team picture must be in a separate
JPEG-format file whose name is X.jpg, where X is the team number (e.g.,
1.jpg, 102.jpg, etc.).

### images/icon folder

This folder holds one 28x28 image file for each contest team containing
the team's logo (typically, the University Logo) in icon size. Each icon
image must be in a separate PNG-format file whose name is X.png, where X
is the team number (e.g., 1.png, 102.png, etc.).

### images/overlay folder

This folder holds one 1920x1080 image file for each contest team
containing the team's name and logo. Each overlay image must be in a
separate PNG-format file whose name is X.png, where X is the team number
(e.g., 1.png, 102.png, etc.). The name and logo are expected to be
placed in the 1920x1080 image in such a way that makes the image
suitable for use as an "overlay" in, for example, video production.

## present folder

This folder, which must be named "present", holds images and other data
typically used by the ICPC Tools Presentation System, as well as other
ICPC Tools (for example, the ICPC Resolver). The content and format of
the images and data in this folder are dependent on the tools accessing
the particular CDP.

# Output Data

These are files that are output from a contest. Typically, these files
and folders will be added to the CDP at the completion of a contest:
once the contest is complete, the final event feed, submission files,
and other relevant generated data should be added back into the CDP
archive, allowing the CDP to be a complete archive of the contest.

Note that not all contests produce all types of output data. For
example, some contests will have backups, reaction videos, or logos, and
others won't. There is no requirement that a CDP contain any particular
output data; only that IF the corresponding output data exists and is to
be archived in a CDP, then it should be organized as follows.

## submissions folder

This folder, which must be named "submissions", contains a folder for
each run submission which took place during the contest. Each separate
run submission is contained in its own subfolder, named with the run id
of the submission.

### submissions/\#\# folder

Each numbered submisions subfolder contains the following for the run
corresponding to the name of the subfolder:

1.  Team's submitted source code file(s)
2.  [run.properties](run.properties "wikilink") file (optional)

## events folder

This folder, which must be named "events", contains the following event
information generated by the Contest Control System.

1.  A file named *events.xml* containing the finalized event feed from
    the CCS in XML format as specified by the [event feed
    page](Event_Feed "wikilink").
2.  A file named *events.json* containing the finalized event feed from
    the CCS in JSON format.

The events folder may also contain other files in the format
"<x>-events.xml", e.g. "pc2-events.xml".

## results folder

This folder, which must be named "results", contains required output
files from the CCS. Examples may include:

1.  [results.tsv](Contest_Control_System#results.tsv "wikilink")
2.  [scoreboard.tsv](Contest_Control_System#scoreboard.tsv "wikilink")
3.  [submissions.tsv](Contest_Control_System#submissions.tsv "wikilink")

### results/<CCS> folder

The results folder may include subfolders associated with specific CCS
implementations. These might include, for example, Reports generated by
the CCS -- for example,

`results/pc2/results.tsv`  
`results/pc2/scoreboard.tsv`  
`results/pc2/balloonReport.txt`

## video/reactions folder

This folder contains recorded team reaction videos for each submission,
in m2ts format. ("Reaction videos" are recordings made from a team's
local webcam at the time they submit a run to the CCS. These are used
for example in the ICPC World Finals to provide interesting reaction
segments to the ICPCLive television broadcast.) The name of each
reaction video file should be "reactionXX.m2ts", where "XX" is the
submission number for which the team reaction video was recorded.

## backups folder

  - contains backups of each team's working folder in the form
    team<X>.zip.

For team102 their $HOME backup would be stored in *backups/team102.zip*.

# Examples

Here are two examples of implementations of the CDP specfication.

## Sample One

`config/hello/`[`problem.yaml`](problem.yaml "wikilink")  
`config/hello/data/secret/hello.ans`  
`config/hello/data/secret/hello.in`  
`config/hello/data/problem_statement/`[`problem.tex`](problem.tex "wikilink")  
`config/`[`teams.tsv`](teams.tsv "wikilink")  
`config/sumit/`[`problem.yaml`](problem.yaml "wikilink")  
`config/sumit/data/secret/sumit.in`  
`config/sumit/data/secret/sumit.ans`  
`config/sumit/data/problem_statement/`[`problem.tex`](problem.tex "wikilink")  
`config/`[`contest.yaml`](contest.yaml "wikilink")  
`config/`[`problemset.yaml`](problemset.yaml "wikilink")  
`config/`[`groups.tsv`](groups.tsv "wikilink")  
`config/`[`userdata.tsv`](userdata.tsv "wikilink")  
  
`submissions/1/A.java`  
`submissions/3/C.java`  
`submissions/3/A.java`  
`submissions/2/A.java`  
  
`results/`[`runs.tsv`](runs.tsv "wikilink")  
`results/`[`scoreboard.tsv`](scoreboard.tsv "wikilink")  
`results/`[`standings.json`](standings.json "wikilink")  
`results/`[`results.tsv`](results.tsv "wikilink")  
`backups/team1.zip`  
`backups/team2.zip`  
`backups/team3.zip`  
`video/reaction/reaction3.m2ts`  
`video/reaction/reaction1.m2ts`  
`video/reaction/reaction2.m2ts`  
`images/team/3.jpg`  
`images/team/2.jpg`  
`images/team/1.jpg`  
`images/logo/1.png`  
`images/logo/3.png`  
`images/logo/2.png`  
  
`events/`[`eventfeed.json`](eventfeed.json "wikilink")  
`events/`[`eventfeed.xml`](eventfeed.xml "wikilink")

## Sample Two

`backups/team1.tar.gz`  
`backups/team2.tar.gz`  
`backups/team3.tar.gz`  
`config/`[`contest.yaml`](contest.yaml "wikilink")  
`config/`[`groups.tsv`](groups.tsv "wikilink")  
`config/`[`problemset.yaml`](problemset.yaml "wikilink")  
`config/`[`teams.tsv`](teams.tsv "wikilink")  
`config/`[`userdata.tsv`](userdata.tsv "wikilink")  
`config/hello/`[`problem.yaml`](problem.yaml "wikilink")  
`config/hello/data/problem_statement/`[`problem.tex`](problem.tex "wikilink")  
`config/hello/data/secret/hello.ans`  
`config/hello/data/secret/hello.in`  
`config/sumit/data/problem_statement/problem.tex`  
`config/sumit/data/secret/sumit.ans`  
`config/sumit/data/secret/sumit.in`  
`config/sumit/problem.yaml`  
`events/`[`events.json`](events.json "wikilink")  
`events/`[`events.xml`](events.xml "wikilink")  
`images/logo/1.png`  
`images/logo/2.png`  
`images/logo/3.png`  
`images/team/1.jpg`  
`images/team/2.jpg`  
`images/team/3.jpg`  
`results/`[`results.tsv`](results.tsv "wikilink")  
`results/`[`runs.tsv`](runs.tsv "wikilink")  
`results/`[`scoreboard.tsv`](scoreboard.tsv "wikilink")  
`results/`[`standings.json`](standings.json "wikilink")  
`submissions/1/`[`run.properties`](run.properties "wikilink")  
`submissions/1/A.java`  
`submissions/2/A.java`  
`submissions/2/run.properties`  
`submissions/3/`[`run.properties`](run.properties "wikilink")  
`submissions/3/A.java`  
`submissions/3/C.java`  
`video/reactions/reaction1.m2ts`  
`video/reactions/reaction2.m2ts`  
`video/reactions/reaction3.m2ts`