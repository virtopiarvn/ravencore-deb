IMG_NAME=ravencore_build
NO_CACHE=false

.PHONY: clean

all:
	docker build --no-cache=$(NO_CACHE) --rm -t "$(IMG_NAME)" .
	docker run --name="$(IMG_NAME)" -d "$(IMG_NAME)" /bin/true
	docker export ravencore_build | tar --wildcards -x 'root/*.deb'
	docker rm ravencore_build
	docker rmi ravencore_build
	mv ./root/*.deb ./
	rmdir ./root

clean:
	rm *.deb
