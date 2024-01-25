# Fauna camera utility scripts
This repository contains helper scripts for processing trail camera images.
Scripts are written for linux systems, compatibility patches and feature requests welcome.

## Examples
```bash

# Dusk 'til Dawn - produce a CSV list of all photos with an EXIF DateTimeOriginal timestamp that occurs between 1hr before sunset, and 1 hour after sunrise for a given lat/long. See individual scripts for optional parameters and defaults. 
# Don't use daylight-savings times on your cameras, they almost certainly don't implement internal DST calenders and automatic switching.
$> ./photos_exif_date /foo/bar | tee photos.csv | ./sunrise_sunset_times > times.csv && \
    ./night_photos --photos photos.csv --times times.csv
```