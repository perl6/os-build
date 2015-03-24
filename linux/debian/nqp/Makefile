.PHONY: help rpm deb clean

help:
	@echo "Possible make targets: deb, rpm, clean"

VERSION=2015.03

nqp-$(VERSION).tar.gz:
	wget http://rakudo.org/downloads/nqp/nqp-$(VERSION).tar.gz

download-nqp: nqp-$(VERSION).tar.gz

DEBUILD_DIR=/tmp/nqp_debuild
deb: download-nqp
	mkdir -p $(DEBUILD_DIR)
	cp nqp-$(VERSION).tar.gz $(DEBUILD_DIR)/nqp_$(VERSION).orig.tar.gz
	tar -C $(DEBUILD_DIR) -xvzf $(DEBUILD_DIR)/nqp_$(VERSION).orig.tar.gz
	cp -r debian $(DEBUILD_DIR)/nqp-$(VERSION)/
	cd $(DEBUILD_DIR)/nqp-$(VERSION)/debian; debuild -us -uc
	cp $(DEBUILD_DIR)/nqp_$(VERSION)-1_all.deb dist
	cd $(DEBUILD_DIR); sudo pbuilder --build nqp_$(VERSION)-1.dsc
	@echo "Now check the .deb file in /var/cache/pbuilder/result"

clean:
	rm -rf $(DEBUILD_DIR)
