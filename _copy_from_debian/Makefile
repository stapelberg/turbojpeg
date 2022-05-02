
all: ../jpeg/libturbojpeg_arm64.syso

../jpeg/libturbojpeg_arm64.syso: Dockerfile
	docker build --rm -t libturbojpeg .
	docker run --rm -v $$(pwd)/../jpeg:/tmp/gokrazy/ libturbojpeg sh -c 'cp  /usr/include/turbojpeg.h /usr/include/aarch64-linux-gnu/jconfig.h /usr/include/jerror.h /usr/include/jmorecfg.h /usr/include/jpegint.h /usr/include/jpeglib.h /tmp/gokrazy/ && cd $$(mktemp -d) && aarch64-linux-gnu-ar x /usr/lib/aarch64-linux-gnu/libturbojpeg.a && aarch64-linux-gnu-ld -r *.o -o /tmp/gokrazy/libturbojpeg_arm64.syso'

clean:
	cd ../jpeg && rm -f jconfig.h jerror.h jmorecfg.h jpegint.h jpeglib.h libturbojpeg_arm64.syso turbojpeg.h 

