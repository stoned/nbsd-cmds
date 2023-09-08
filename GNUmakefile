INSTALL?=	install

BSDINCDIR?=	/usr/include/bsd
BSDLIB?=	-lbsd
BSDLIB_PKG?=	libbsd-devel
PKG_INSTALL?=	sudo yum install -y

PREFIX?=	/usr/local
BINDIR?=	$(PREFIX)/bin
MAN1DIR?=	$(PREFIX)/share/man/man1

jot_LIB=	-lm

all: apply jot

%: %.c $(BSDINCDIR)
	gcc $< -o $@ -isystem $(BSDINCDIR) -DLIBBSD_OVERLAY=1 -D__dead= $(BSDLIB) $($@_LIB)

$(BSDINCDIR):
	$(PKG_INSTALL) $(BSDLIB_PKG)

install: apply apply.1 jot jot.1
	$(INSTALL) -c -m 755 apply $(BINDIR)/apply
	$(INSTALL) -c -m 755 jot $(BINDIR)/jot
	$(INSTALL) -c -m 644 apply.1 $(MAN1DIR)/apply.1
	$(INSTALL) -c -m 644 jot.1 $(MAN1DIR)/jot.1

clean:
	-rm -f apply jot
