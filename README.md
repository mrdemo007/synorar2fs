# forked from zimme/rar2fs

Minimal `rar2fs` image based on alpine.

This Docker image will run `rar2fs` with `-o allow_other -o auto_unmount
--seek-length=1` by default.

Bind-mount your rar files on `/source` and bind-mount an empty folder on
`/nomorerar` to hold the rar2fs mount.

## Usage

```sh
docker run \
  -d \
  --init \
  --name rar2fs \
  --cap-add SYS_ADMIN \
  --device /dev/fuse \
  -v <path/to/rar/files>:/source \
  -v <path/to/empty/folder>:/nomorerar \
  jonasandren/synorar2fs
```

## Config

To get a list of all config options for `rar2fs` run the following
command.

```sh
docker run --rm jonasandren/synorar2fs --help
```

To run this image with your own config provide your config arguments as
arguments to the image when running.

```sh
docker run \
  -d \
  --init \
  --name rar2fs \
  --cap-add SYS_ADMIN \
  --device /dev/fuse \
  -v <path/to/rar/files>:/source \
  -v <path/to/empty/folder>:/nomorerar \
  jonasandren/synorar2fs \
  <custom rar2fs option> \
  -o <custom fuse option> \
  /source \
  /nomorerar
```
