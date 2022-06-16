## INTRODUCTION

Bash script to AutoUpload Torrents to torrent trackers based on ScarS' bash torrent uploader

## REQUIREMENTS

- bash v3.2+
- curl
- mktorrent v0.6+

### OPTIONAL

- rtorrent
- rtorrent_fast_resume.pl

## INSTALL

### upload

#### With root / sudo access

Change directory to **/usr/local/bin**
Move **upload** file hereto
Run following command
```
sudo chmod 755 /usr/local/bin/upload
```

#### Without root / sudo access

Create a new directory named **~/bin**
```
mkdir ~/bin
```
Move **upload** file hereto
Run following command
```
chmod 755 /home/$USER/bin/upload
```

### Home dir

Create a new directory named **upload/** 
```
mkdir /home/$USER/upload/
```
Move **upload.rc** and **wrapper** hereto
Run following command
```
chmod 600 /home/$USER/upload/.*.rc && chmod 700 /home/$USER/upload/wrapper
```

## Edit upload.rc
**ONLY CHANGE THE FOLLOWING LINES**
Next you have to edit your upload.rc
```
nano /home/$USER/upload/.upload.rc
```
You need to change:
- Username
- Password
- LOGINTXT
- ANNOUNCEURL
- DOWNLOADS
- TORRENTS
- LOGFILE

## Edit wrapper
**ONLY CHANGE THE FOLLOWING LINE**
- HOME (To your home directory. **Without ending slash!**)

## Edit .rtorrent.rc
**ONLY CHANGE THIS IF YOU WANT rTorrent TO AUTOUPLOAD TORRENTS**
Add following line to .rtorrent.rc
```
system.method.set_key = event.download.finished,upload_torrent,"execute=/home/USERNAME/upload/wrapper,rtorrent,$d.get_chunk_size=,$d.get_base_path="
```
If you add above line you have to restart rtorrent, otherwise it won't work
