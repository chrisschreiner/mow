# mow
Clean up your movie-folders. 

The reason I wrote this was to have the filenames themselves be the name of the movie, for those old movie players that never get an update and only presents filenames when browsing (e.g. Air Video HD).

### wat?

Your filesystem is littered with this:

```
Dying.of.the.dark.2017.HDRip.XViD-juggs[ETRG].avi
Earth to bocho  2012  1080p.mp4
Edge.of.Yesterday.2015.1080p.BluRay.x264.YIFY.mp4
Drinking.Elysium.(2011).1080p.BluRay.x264.YIFY.mp4
```

mow makes it look like this:

```
Dying of the dark - 2017.avi
Earth to bocho - 2012.mp4
Edge of Yesterday - 2015.mp4
Drinking Elysium - 2011.mp4
```

Metadata related to the movie (and posters) are also retrieved (when possible.)

### Next

No idea

### Requirements
Anything with a filesystem running Python 3.5

## Installation
Ready-made can be downloaded using [pip](https://pip.readthedocs.org/en/stable/installing/#install-pip).
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

#### **Scan**

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

`~/output/recognized-files-folder/.` contains hard-links to the original file.

------

#### **List**

You want to show a listing of all movies recognized:

```
$> mow list
Adventure  Romance    War          79 min   5.3   Beau Ideal                          ~/output/Beau Ideal (1931).mp4
Action     Adventure  Drama        75 min   5.1   The Big Cat                         ~/output/The Big Cat (1949).mkv
Horror     Sci-Fi                  62 min   3.5   Attack of the Giant Leeches         ~/output/Attack of the Giant Leeches (1959).mp4
```
