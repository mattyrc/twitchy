# twitchy
livestreamer wrapper for twitch.tv

**Requires livestreamer, python3**

This script hopefully fulfills the needs of the discerning git cloner who wants to watch Twitch, hates the CPU utilization of having a browser/flash running, and has only a terminal handy.

Features:
* Integration with your conky instance.
* Tracking of most watched channels.
* View VODs
* Music identification (uses twitchecho.com)
* Sync your followed accounts to a local sqlite database that does not judge you.
* Stream as many... streams as you want at once.
* The ability to display alternate names for games / streamers. If your happiness is somehow contingent upon displaying "Hearthstone: Heroes of Warcraft" as "Wizard Poker", well, you've come to the right place.

## Usage

    $ twitchy [ARGUMENT] [OPTIONS]
    
    [ARGUMENT] to the script is used as a search string for channels in the local database.
    
    [OPTIONS]
    -h, --help                      This helpful message
    -a <channel name>               Add channel(s)
    -an                             Set/unset alternate names
    --configure                     Configure options
    --conky [ np / tw / go ]        Generate data for conky
    -d                              Delete channel(s) from database
    -f                              Check if your favorite channels are online
    -s <username>                   Sync followed channels from specified account
    --update                        Update to the latest git revision
    -v <channel name>               Watch channel's recorded videos
    -w <channel name>               Watch specified channel(s)
    
    While playing:
    <m> to attempt music identification with twitchecho
    <q> to quit
    
    Conky options. Execute script with:
    --conky np                      Get name of the currently playing stream
    --conky tw                      Time spent Watching the currently playing stream
    --conky go                      Get comma separated list of Online channels
    The script will exit with exit code 1 in case either np or tw is used while nothing is playing.
    
## Examples

Using no argument while launching the script will check the status of every channel in the local database:
![alt tag](https://imgur.com/cwdHy7L.png)
    
Add "bobross" to local database:

    $ twitchy -a bobross
    
Display all strings matching *obr*:

    $ twitchy obr
    Checking channels...
    Creative
    1 bobross                   80085                       The Joy of Painting Monday Season 7 Marathon #painting...
    Sonic: Generations
    2 mariobro                  123                         #WhereMuhPrincessAt?
    Wizard Poker                               
    3 flatulentcobra            6969                        Playing secret Paladin. Killing a puppy later.
    Channel number(s): 1-h 2-s 3-l

    Custom quality settings: Specify with hyphen next to channel number.
    E.g. <1-h 2-s 3-l> will simultaneously play channel 1 in high quality, 2 in source quality, and 3 in low quality.
    
Watch specified channel(s) - Do not have to be in local database:

    $ twitchy -w northernlion cobaltstreak
    Checking channels...
    The Binding of Isaac: Afterbirth
    1 northernlion                5757                      Egg
    Offline
    x cobaltstreak
    Channel number(s): 1
