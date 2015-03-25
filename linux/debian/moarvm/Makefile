.PHONY: help rpm deb clean

help:
	@echo "Possible make targets: deb, rpm, clean"

VERSION=2015.03

MoarVM-$(VERSION).tar.gz:
	wget http://moarvm.org/releases/MoarVM-$(VERSION).tar.gz

download-moarvm: MoarVM-$(VERSION).tar.gz


DEBUILD_DIR=/tmp/moarvm_debuild
deb: download-moarvm
	if [ -d $(DEBUILD_DIR) ]; then rm -r $(DEBUILD_DIR); fi
	mkdir -p $(DEBUILD_DIR)
	cp MoarVM-$(VERSION).tar.gz $(DEBUILD_DIR)/moarvm_$(VERSION).orig.tar.gz
	tar -C $(DEBUILD_DIR) -xvzf $(DEBUILD_DIR)/moarvm_$(VERSION).orig.tar.gz
	mv $(DEBUILD_DIR)/MoarVM-$(VERSION) $(DEBUILD_DIR)/moarvm-$(VERSION)
	cp -r debian $(DEBUILD_DIR)/moarvm-$(VERSION)/
	cd $(DEBUILD_DIR)/moarvm-$(VERSION)/debian; debuild -us -uc
	@echo "Now check the .deb file in $(DEBUILD_DIR)"

clean:
	rm -rf $(DEBUILD_DIR)
