#Mow

###Purpose

Clean up your folders of ripped movies. Changes filenames (of recognized movies) with a format that your movie app (tvOS/Plex etc) can detect.

Posters and metadata is also retrieved. A future version will enable extraction and processing of more data.

### Requirements

- Mac/Linux 

- Python 3.5

### Installation

`$> pip install mow`

Don't have pip? https://pip.readthedocs.org/en/stable/installing/#install-pip

### Usage
```script
$> mow --help
Usage: mow [OPTIONS] COMMAND [ARGS]...

Options:
  -v, --verbose INTEGER  verbose
  -p, --preview          preview
  -t, --trace INTEGER    Include a trace in output
  --help                 Show this message and exit.

Commands:
  scan
```


### Use-case 1: Scan
_Pretend you have a folder with downloaded movies from the public domain. You want to clean it up and at the same time fetch meta-data and posters._

```script
$> mow scan --help
Usage: mow scan [OPTIONS] INPUT OUTPUT UNKNOWN                    
                                                                  
Options:                                                          
  -r, --reset-cache  Reset cache before scanning
  --help             Show this message and exit.   

$> pwd
~
$> ls movies
Beau Ideal - 1931 ripper by someone.mp4
The-Big-Cat-[1949]-redray-stolen.mks
Bird.of.Paradise (1932) pirates-r-us.avi
Giant.Leeches-1959-pb.mp4
...
$> mow scan  movies  properly-formatted-files  unrecognized-files
```

Look at the results in the following folders when completed:
```
~/properly-formatted-files/.
~/properly-formatted-files/unrecognized/.
~/Library/Cache/mow-cache.json
~/Library/Cache/posters/.
```

*Please note:*

~/properly-formatted-files/. contain hard-links to the original file.