## About
rtorrent + rutorrent based on 
[crazymax/rtorrent-rutorrent](https://github.com/crazy-max/docker-rtorrent-rutorrent)
with minor adjustments to meet my needs.

To read about features and usage examples visit 
[crazymax's repo](https://github.com/crazy-max/docker-rtorrent-rutorrent)

## Changes
- Disabled webdav
- Updated `rtorrent.rc` to disable DHT and increase some limits
- Updated `rtorrent.rc` and `rtlocal.rc` to change where rtorrent ports will 
be configured from
- Updated `rtlocal.rc` to include a drop ins directory
- Removed temp and completed directories from `rtlocal.rc` Torrent just download to the main dir

## Wishlist
- Include FloodUI
- Fix configuration drop-ins -> Not being parsed or used for some reason


## Usage Example
```bash
docker build -t gbourdin/rtorrent-rutorrent:0.0.dev0 .
docker run --rm -it --name rtorrent_rutorrent \
  --ulimit nproc=65535 \
  --ulimit nofile=32000:40000 \
  -p 8080:8080 \
  -p 50000:50000 \
  -p 50000:50000/udp \
  -v $(pwd)/data:/data \
  -v $(pwd)/downloads:/downloads \
  -v $(pwd)/passwd:/passwd \
  rtorrent-rutorrent:0.0.dev0
  ```
  