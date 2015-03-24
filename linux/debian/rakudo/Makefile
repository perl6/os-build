.PHONY: help rpm deb clean

help:
	@echo "Possible make targets: deb, rpm, clean"

VERSION=2015.03

rakudo-$(VERSION).tar.gz:
	wget http://rakudo.org/downloads/rakudo/rakudo-$(VERSION).tar.gz

download-rakudo: rakudo-$(VERSION).tar.gz

RPMBUILD_DIR=/tmp/rakudo_rpmbuild
rpm: download-rakudo
	mkdir -p $(RPMBUILD_DIR)
	mkdir -p $(RPMBUILD_DIR)/BUILD
	mkdir -p $(RPMBUILD_DIR)/BUILDROOT
	mkdir -p $(RPMBUILD_DIR)/RPMS
	mkdir -p $(RPMBUILD_DIR)/SOURCES
	mkdir -p $(RPMBUILD_DIR)/SPECS
	mkdir -p $(RPMBUILD_DIR)/SRPMS
	cp rpm/rakudo.spec $(RPMBUILD_DIR)/SPECS/
	cp rakudo-$(VERSION).tar.gz $(RPMBUILD_DIR)/SOURCES/
	rpmbuild -ba $(RPMBUILD_DIR)/SPECS/rakudo.spec

DEBUILD_DIR=/tmp/rakudo_debuild
deb: download-rakudo
	mkdir -p $(DEBUILD_DIR)
	cp rakudo-$(VERSION).tar.gz $(DEBUILD_DIR)/rakudo_$(VERSION).orig.tar.gz
	tar -C $(DEBUILD_DIR) -xvzf $(DEBUILD_DIR)/rakudo_$(VERSION).orig.tar.gz
	cp -r debian $(DEBUILD_DIR)/rakudo-$(VERSION)/
	cd $(DEBUILD_DIR)/rakudo-$(VERSION)/debian; debuild -us -uc
	cp $(DEBUILD_DIR)/rakudo_$(VERSION)-1_all.deb dist
	cd $(DEBUILD_DIR); sudo pbuilder --build rakudo_$(VERSION)-1.dsc
	@echo "Now check the .deb file in /var/cache/pbuilder/result"

clean:
	rm -rf $(RPMBUILD_DIR) $(DEBUILD_DIR)
