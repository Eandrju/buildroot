# Based on ftDev Buildroot Repository

## How to build it with docker

Build docker image:
```bash
docker build -t buildroot-fastboot-rpi-builder .
```
Create volume for buildroot directory:
```bash
docker volume create fastboot_buildroot_volume
```

Run with:
```bash
docker run -v fastboot_buildroot_volume:/buildroot -it buildroot-fastboot-rpi-builder
```

Then as instructed in ftDev repo:
```bash
make ftdev_rpi3_fastboot_defconfig && \
make -j8 2>&1 | tee output_buildroot.log && \
./build-rpi3-qt.sh 2>&1 | tee output_qt.log
```

Generated files in our volume can be now used to compile static QT app. 
