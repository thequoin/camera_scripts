# Fauna camera utility scripts
This repository contains helper scripts for processing trail camera images.
Scripts are written for linux systems, compatibility patches and feature requests welcome.

Scripts are intended for processing hundreds of GB per invocation.

## Examples
```bash

# Dusk 'til Dawn - produce a CSV list of all photos with an EXIF DateTimeOriginal timestamp that
# occurs between 1hr before sunset, and 1 hour after sunrise for a given lat/long.
#
# See individual scripts for optional parameters and defaults.
#
# Don't use daylight-savings times on your cameras, they almost certainly don't implement
# internal DST calenders and automatic switching.

# one-liner
$> ./photos_exif_date /foo/bar | tee photos.csv | ./sunrise_sunset_times > times.csv && \
    ./night_photos photos.csv times.csv > foo_bar_night_photos.csv

# produce photos.csv first so you can check its progress using `wc -l` in another terminal
$> ./photos_exif_date /foo/bar > photos.csv

# produce sunrise/sunset times from the unique dates in photos.csv
$> cat photos.csv | ./sunsrise_sunset_times > times.csv

# produce list of photos taken between dusk and dawn
$> ./night_photos photos.csv times.csv > night_photos.csv
```
