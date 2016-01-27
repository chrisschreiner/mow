#Mow

###Purpose

Clean up your folders of ripped movies. Changes filenames (of recognized movies) with a format that is more useful to you and your typical movie app (Air Video HD/Plex etc).

Metadata and posters are also retrieved. A future version will enable extraction and processing of more data.

### Requirements

- Mac/Linux 

- Python 3.5

### Installation

Ready-made can be downloaded using the python pip utility.

$> `pip install mow`

Don't have pip? https://pip.readthedocs.org/en/stable/installing/#install-pip

### Usage
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


### Use-case 1: **Scan**
_Pretend you have a folder with downloaded movies from the public domain. You want to clean it up and at the same time fetch meta-data and posters._

```shell
$> mow scan --help
Usage: mow scan [OPTIONS] INPUT OUTPUT UNKNOWN                    
                                                                  
Options:                                                          
  -r, --reset-cache  Reset cache before scanning
  --help             Show this message and exit.   

$> pwd
~
$> ls movies
Beau Ideal - 1931 ripper by someone.mp4
The-Big-Cat-[1949]-redray-stolen.mkv
Bird.of.Paradise (1932) pirates-r-us.avi
Giant.Leeches-1959-pb.mp4
Homemovie-Aug-2012-playback.mp4
...
$> mow scan movie-folder properly-formatted-files unrecognized-files
```

Look at the results in the following folders when completed:
```shell
~/properly-formatted-files/.
~/properly-formatted-files/unrecognized/.
~/Library/Cache/mow-cache.json
~/Library/Cache/posters/.
```

*Please note:*

`~/properly-formatted-files/.` contain hard-links to the original file.
### Use-case 2: **List**
_Pretend you've completed the previous use-case, and you want to show a listing of all movies recognized

```shell
$> mow list --help
Usage: mow list [OPTIONS] OUTPUT IP-ADDRESS
                                                                  
Options:                                                            
  --help             Show this message and exit.   
```

```
$> mow list
Adventure  Romance    War          79 min   5.3   Beau Ideal                          ~/output/Beau Ideal (1931).mp4
Action     Adventure  Drama        75 min   5.1   The Big Cat                         ~/output/The Big Cat (1949).mkv
Horror     Sci-Fi                  62 min   3.5   Attack of the Giant Leeches         ~/output/Attack of the Giant Leeches (1959).mp4
```

