name = control-files-bad

all:
	echo '2.0' > debian-binary
	mkdir -p usr/share/doc/$(name)
	cp copyright changelog usr/share/doc/$(name)
	gzip -9 usr/share/doc/$(name)/changelog
	tar cfz data.tar.gz usr
	chown 0:0 control
	chmod 644 control
	md5sum usr/share/doc/$(name)/* > md5sums
	chmod 755 md5sums
	tar -czf control.tar.gz --owner=nobody control md5sums
	ar rc $(name).deb \
	    debian-binary control.tar.gz data.tar.gz

clean:
	rm -f *.tar.gz *.tar.lzma *.deb md5sums debian-binary
	rm -rf usr