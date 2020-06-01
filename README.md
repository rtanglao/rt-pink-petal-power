# rt-pink-petal-power
tights, tshirts and other stuff from pink vancouver petals april-may2020

* You can find the source images at:
    * https://www.flickr.com/photos/roland/albums/72157714184799381
## 31may2020 create the  thumbnails
as per: http://rolandtanglao.com/2020/02/17/p1-how-i-made-art-of-where-tights-berlin/

* 1\. get the filenames
```bash
ls -d /home/roland/GIT/rt-pink-petal-power/ORIGINALS/*.jpg > pink_petal_power_jpg_filenames.txt
```
* 2\.get the maximum number of 75x75 positions in each original file
    * i am lazy so i just copied in https://github.com/rtanglao/rt-berlin-january-2020/blob/master/print-file-width-length-max75-x-max75-y.rb to this directory
```bash
./print-file-width-length-max75-x-max75-y.rb pink_petal_power_jpg_filenames.txt \
> pink-petal-power-75px-75px-max-x-maxy.txt
```

* 3\. make the 75x75 pixel thumbnails

```bash
mkdir 75PX_BY_75PX_PATCHES
cd !$
../create-75px-75px-patches.rb ../pink-petal-power-75px-75px-max-x-maxy.txt 10000
```
