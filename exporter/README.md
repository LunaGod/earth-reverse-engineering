## 1. Model exporter

We can dump a textured 3D model (_.obj with _.bmp and \*.jpg) using the following scripts. They require [Node.js](https://nodejs.org/en/) v8 and [npm](https://www.npmjs.com/):

```sh
# Install dependencies (tested with node@8.15.0, npm@6.4.1)
npm install

# Find octant of latitude and longitude
node lat_long_to_octant.js 37.420806884765625 -122.08419799804688

# Dump octant with max-level 20
node dump_obj.js 20527061605273514 20
```

Exported files will be in `./downloaded_files/obj`. They can be opened in Blender [like this](BLENDER.md).

## 2. Notes

Alternative methods for finding octants:

- LexSong wrote a Python script that takes bounding box coordinates to find octants: [LexSong/earth-reverse-engineering-utils](https://github.com/LexSong/earth-reverse-engineering-utils)
- Manually: [Open maps and dev tools, switch to satellite, fly to destination, search for NodeData, copy octant path from recent request](how_to_find_octant.jpg)

You can use this to dump json and raw data instead of obj:

```
node dump_obj.js 20527061605273514 20 --dump-json --dump-raw
```

## 3. use proxy server

only supports http proxy

1. `lat_long_to_octant.js`

```sh
# before
node lat_long_to_octant.js 37.420806884765625 -122.08419799804688
# after
node lat_long_to_octant.js 37.420806884765625 -122.08419799804688 127.0.0.1 7890 user1 password1

```

2. `dump_obj.js`

```sh
# before
node dump_obj.js 20527061605273514 20
# after
node dump_obj.js 20527061605273514 20 --host=127.0.0.1 --port=7890 --username=user1 --password=password1

```
