# rt-pink-petal-power
tights, tshirts and other stuff from pink vancouver petals april-may2020

* You can find the source images at:
    * https://www.flickr.com/photos/roland/albums/72157714184799381

## 01june2020 create the right and left leg from the shuffled files

```bash
montage -verbose -adjoin -tile 45x85 +frame +shadow +label -adjoin \
-geometry '75x75+0+0<' @right-leg-shuffled-3825-pink-petal-jpgs.txt \
right-leg_thumbnail-artofwhere-pink-petal-2020.png
montage -verbose -adjoin -tile 45x85 +frame +shadow +label -adjoin \
-geometry '75x75+0+0<' @left-leg-shuffled-3825-pink-petal-jpgs.txt \
left-leg_thumbnail_artofwhere-pink-petal-2020.png
```

## 01june2020 shuffle the files to create right and left leg

```bash
cat 11-times-all-thumbnails-path-names.txt | \
shuf -n 3825 > right-leg-shuffled-3825-pink-petal-jpgs.txt
cat 11-times-all-thumbnails-path-names.txt | \
shuf -n 3825 > left-leg-shuffled-3825-pink-petal-jpgs.txt
```

## 01june2020 create file to shuffle for right and left leg

```bash
ls -d $PWD/thumb*.png > all-thumbnails-path-names.txt
for i in {1..11}; do cat all-thumbnails-path-names.txt \
>>11-times-all-thumbnails-path-names.txt; done
```
## 01june2020 create 75x75 thumbnails

```bash
mkdir /home/roland/GIT/rt-pink-petal-power/THUMBS_75X75
cd !$
# The exclamation mark means distort if the original is not a square
magick '../ORIGINALS/*.jpg' -resize 75x75\! thumbnail%03d.png &
```
## 31may2020 create the left and right leg graphics

* 1\. 3825 jpegs per leg

```bash
ls -1 *.jpg | shuf -n 3825 > right-leg-shuffled-3825-pink-petal-jpgs.txt
ls -1 *.jpg | shuf -n 3825 > left-leg-shuffled-3825-pink-petal-jpgs.txt
montage -verbose -adjoin -tile 45x85 +frame +shadow +label -adjoin \
-geometry '75x75+0+0<' @right-leg-shuffled-3825-pink-petal-jpgs.txt \
right-leg_artofwhere-pink-petal-2020.png
montage -verbose -adjoin -tile 45x85 +frame +shadow +label -adjoin \
-geometry '75x75+0+0<' @left-leg-shuffled-3825-pink-petal-jpgs.txt \
left-leg_artofwhere-pink-petal-2020.png
```

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
