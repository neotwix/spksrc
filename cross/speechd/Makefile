PKG_NAME = speechd
PKG_FULL_NAME = speech-dispatcher
PKG_VERS = 0.7.1
PKG_EXT = tar.gz
PKG_DIR = $(PKG_FULL_NAME)-$(PKG_VERS)
PKG_DIST_NAME = $(PKG_DIR).$(PKG_EXT)
PKG_DIST_SITE = http://devel.freebsoft.org/pub/projects/$(PKG_NAME)
PYTHON_VERS = 2.7.2

DEPENDS  = cross/dotconf cross/glib cross/alsa-oss cross/alsa-utils
DEPENDS += cross/espeak
DEPENDS += native/python

HOMEPAGE = http://devel.freebsoft.org/speechd
COMMENT  = Common interface to speech synthesis
LICENSE  =

GNU_CONFIGURE = 1
CONFIGURE_ARGS  = --with-espeak --with-oss --with-alsa
CONFIGURE_ARGS += PYTHON=$(WORK_DIR)/../../../native/python/work-native/Python-$(PYTHON_VERS)/python

PRE_CONFIGURE_TARGET = myPreConfigure
INSTALL_TARGET = myInstall

SPEECHD_CONFIG_PATHS  = spksrc_spdconforigdir=$(INSTALL_PREFIX)/share/speech-dispatcher/conf spksrc_spdconfdir=$(INSTALL_PREFIX)/etc/speech-dispatcher
SPEECHD_CONFIG_PATHS += spksrc_snddatadir=$(INSTALL_PREFIX)/share/sounds/speech-dispatcher spksrc_spddesktopconforigdir=$(INSTALL_PREFIX)/share/speech-dispatcher/conf/desktop

include ../../mk/spksrc.cross-cc.mk

.PHONY: myPreConfigure
myPreConfigure:
	$(RUN) sed -i -e 's|^#!.*$$|#!$(INSTALL_PREFIX)/bin/python|g' src/python/speechd_config/spd-conf
	$(RUN) automake

.PHONY: myInstall
myInstall:
	$(RUN) make install prefix=$(STAGING_INSTALL_PREFIX) $(SPEECHD_CONFIG_PATHS)

