# StreamingHowTo
###Here you'll find a guide to use a few services to get your Movies and TV Shows

##Level 1 - Sloth
**Difficulty level:** Easy
PC/Laptop + Plex + Chromecast
**Who is this for:** Someone who doesn’t really want to geek out too much

##Level 2 - Gluttony
**DIfficulty Level:** Easy
NAS+Gaming Console
**Who is this for:** Someone who already owns a gaming console such as the Xbox or a playstation


##Level 3 - Greed
**Difficulty level:** Moderate-Easy
HTPC + External HDD/NAS + Kodi + Chromecast
**Who this is for:** Someone who already has  an old PC lying around and has an extensive collection of media on a hard disk


##Level 4 - Lust
**Difficulty level:** Moderate
HTPC + NAS + OpenElec + Plex
**Who this is for:** Someone who is willing to go the extra mile for keeping media on a NAS or there are many users in a single house/room

##Level 5 - Wrath
**Difficulty Level:** Moderate
RP2 + Torrent client + NAS + Kodi + Yatze
**Who this is for:** Someone who isn't too fussy about content, but still wants remote downloading and storage on the network

##Level 6 - Envy
**Difficulty Level:** Hard
RP2 + qt transmission + ExtHDD/NAS + filebot + OpenElec + Plex + Chromecast/Roku
**Who this is for:** Someone who has a good internet plan and wants to remotely download stuff, and is very particular about interfaces and media organization

##Level 7 - Pride
**Difficulty level:** Hard
HTPC + RP2 + OpenELEC + Plex + torrent client + filebot + Couch potato + Sickrage
**Who this is for:** Someone who writes a script for automating everything.



##What you need

###Software:
- FileBot
- Torrent Downloader-Bittorrent, utorrent, Deluge, Transmission
- Plex
- Couch Potato+Extension
- Dropbox
- Sonarr

###Hardware:

 - HTPC/Raspberry Pi2
 - Chromecast/TeeVee
 - External Hard disk/NAS





##Steps for couchpotato:
 1. Install couch potato.
 2. Open the web interface at localhost:5050/wizard
 3. Fill in username and password. Port can be default.
 4. Set directory to save the .torrent files.
 5. Turn on the services you want to use
 6. You can set to rename the downloaded movies in couch potato or use an external service like filebot.
 7. List item

Couchpotato is set. Now any movie you select will be downloaded to the folder.

##Steps for utorrent:

 1. Install utorrent
 2. Set the location to pull the torrent files from. (You can do this by going to Options>Directories>Automatically load .torrents from).
 3. Next go to Advanced>Run Program. Here we will use a script to run filebot every time a torrent completes (Downloading+Seeding)
````filebot -script fn:amc --output "X:/Media" --action copy --conflict skip -non-strict --log-file amc.log --def unsorted=y music=y artwork=y "ut_label=%L" "ut_state=%S" "ut_title=%N" "ut_kind=%K" "ut_file=%F" "ut_dir=%D"````
 4. Here you need to change the output directory to the location where you want to store the downloaded files. Change the --output "X:/Media" to your location such as --output “C:/Users/Digit/Downloads/Media”




You’re done setting up utorrent.

##Steps for plex: 

 1. Download and install the server version for windows from plex.tv
 2. After the installation of the application, the web interface will load up to sign up for plex. You can do this in a few minutes and should not be a hassle.
 3. Plex should automatically start running in the background and you can launch it by clicking the icon on the taskbar or by searching for the application shortcut.
Now, you’ll land in a web interface, where you can set up the basic configuration for plex.
 4. Set a friendly name for your server. This is the name you will use to identify the server. Here, we have it as TheBigBlue
 5. You will be asked to add libraries. Here, you can add different libraries as the folders in your hard disk containing the movies, TV shows and music you have.

As long as plex is running in the background, you’ll be able to access your media on the same network. Plex provides a premium service called as Plex Pass which you can use to stream your content outside the network as well.

##Steps for filebot:

Filebot just needs to be installed along with JRE(Java Runtime Environment). utorrent automatically calls filebot and renames the files


##Steps for TV Shows

 1. For TV shows, we’ll use a fork of the popular sickbeard, called sickrage or you can use sonarr. Sickrage is a python application which will allow you to search for TV shows and add it to your library. Whenever a new episode becomes available, it downloads the torrent file on to a folder. Sonarr does the same thing, but is more accessible owing to its easy installer
 2. You can either clone the github repo or download the zip at https://github.com/SiCKRAGETV/SickRage for sickrage and get sonarr at https://sonarr.tv/
 3. Extract the files and double click on SickBeard.py, but make sure you already have at least python 2.7.10 installed. Sonarr can just be installed as a service on windows using the installer.
 4. Both SickRage and Sonarr will load up a web interface where you can add TV Shows. Once you add a show, it will list the individual episodes. These episodes can be marked as wanted, downloaded, archived and so on.


 When you mark an episode as wanted, sickrage will search for that episode on torrents and download the torrent file. To save the torrent file to a particular location, you can go to Settings>Search settings>Torrent Search>Send .torrent files to, and select Black hole and give a directory to save these. It can be the same as the one for movies.
Now, as long as sickrage is running, it will refresh automatically to find new episodes of the TV shows and add the torrents automatically.




##Points:

 - Plex transcodes video files so even mkv can be played on devices which don't support the playback, because of this, some low powered NAS boxes and RPi2 may not allow transcoding of some files due to insufficient CPU power.
 - Roku works the best with plex. Little lag, but it could be because of the NAS.
 - Any streaming stick such as the Chromecast, Roku and FireTV will be a bit slow to load owing it the low powered nature of the devices.

