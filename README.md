# mow

## Gist

Clean up your movie-folders. Attempts to remove heavily adorned filenames as observed on the interweb. Changes the filename (of recognized entries) with sane estethics – this is more useful to you and your typical movie app (Air Video HD/Plex etc).

The reason I wrote this is to have sane movie-information when I browse the filesystem on my tv.

Metadata and posters are also retrieved (when possible.)

## Forward

Broaden the extraction of meta-data.

## Requirements

Anything with a filesystem running Python 3.5

## Installation

Ready-made can be downloaded using the python [pip](https://pip.readthedocs.org/en/stable/installing/#install-pip) utility.

```
$> `pip install mow`
```

## Usage

```shell
$> mow --help
Usage: mow [OPTIONS] COMMAND [ARGS]...

Options:
  -V, --version            Show version information.
  -v, --verbose [0|1|2|3]  Verbose output, higher number indicates more
                           output.
  -p, --preview            Previews paths, but generates no output.
  -t, --trace INTEGER      Include a trace in output, number indicates depth
                           of calls.
  --help                   Show this message and exit.


Commands:
  scan
  list
```

------

#### Use-case 1: **Scan**

If you have a folder with downloaded movies and you want to have readable filenames and at the same time fetch meta-data and posters. You can use `mow scan`

```shell
$> mow scan --help
Usage: mow scan [OPTIONS] INPUT OUTPUT UNKNOWN                    
                                                                  
Options:                                                          
  -r, --reset-cache  Reset cache before scanning
  --help             Show this message and exit.   
```

Go to your movie folder

```shell
$> pwd
~
$> ls ./movies-folder-source
Beau Ideal - 1931 ripped by someone.mp4
The-Big-Cat-[1949]-redray-borrowed.mkv
Bird.of.Paradise (1932) pirates-r-us.avi
Giant.Leeches-1959-pb.mp4
Homemovie-Aug-2012-playback.mp4
...
$> mow scan ./movie-folder-source ./output/recognized-files-folder ./output/unrecognized-files-folder
```

Output:

```shell
~/output/recognized-files-folder/.
~/output/unrecognized-files-folder/.
~/Library/Cache/mow-cache.json
~/Library/Cache/posters/.
```

*Note:*

`~/output/recognized-files-folder/.` contain hard-links to the original file.

------

#### Use-case 2: **List**

You want to show a listing of all movies recognized:
