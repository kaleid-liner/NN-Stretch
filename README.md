## Build Docker

```
docker build -t "mbm:latest" .
```

## Evaluation

```
docker run -it -v configs:/data "mbm:latest" --privileged -v /dev/bus/usb:/dev/bus/usb --name mbm-ae /bin/bash
```

Then, in docker:
```
python src/tools/run_pipeline.py --configs /data
```

### If your host is windows

If your host is windows, you need to install adb first, then running on host:

```
adb -a -P 5037 nodaemon server
```

And start the container with:

```
docker run -it -v configs:/data "mbm:latest" --name mbm-ae /bin/bash
```

Then in docker:
```
python src/tools/run_pipeline.py --configs /data --adb_host host.docker.internal
```
