# $NetBSD: Makefile,v 1.38 2021/05/24 19:56:06 wiz Exp $

DISTNAME=	xservers-3.3.6.5
PKGREVISION=	3
CATEGORIES=	x11
MASTER_SITES=	${MASTER_SITE_LOCAL}
EXTRACT_SUFX=	.tar.bz2

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	https://www.xfree86.org/
COMMENT=	Old X11 servers for use under XFree86 4.x

ONLY_FOR_PLATFORM=	NetBSD-*-i386

MAKE_JOBS_SAFE=		no

BUILD_TARGET=	World

X11_SUBDIR=	X11R6.3

MESSAGE_SUBST+=	X11_SUBDIR=${X11_SUBDIR}

BUILDLINK_PASSTHRU_RPATHDIRS+=	${PREFIX}/X11R6.3/lib

do-configure:
	${SED} -e 's#@PROJECTROOT@#${PREFIX}/${X11_SUBDIR}#' \
	  ${FILESDIR}/host.def >${WRKSRC}/config/cf/host.def
	${ECHO} "#define NetBSDThreads NO" >>${WRKSRC}/config/cf/host.def

GENERATE_PLIST+= \
	cd ${DESTDIR}${PREFIX} && \
	${FIND} ${X11_SUBDIR} \! -type d -print | ${SORT} -d;

SPECIAL_PERMS+=	${X11_SUBDIR}/bin/Xwrapper ${SETUID_ROOT_PERMS}

INSTALL_MAKE_FLAGS+=	INSTPGMFLAGS=${_STRIPFLAG_INSTALL:Q}\ -o\ ${BINOWN:Q}\ -g\ ${BINGRP:Q}\ -m\ ${BINMODE:Q}
INSTALL_MAKE_FLAGS+=	INSTBINFLAGS=-o\ ${BINOWN:Q}\ -g\ ${BINGRP:Q}\ -m\ ${BINMODE:Q}
INSTALL_MAKE_FLAGS+=	INSTUIDFLAGS=-o\ ${BINOWN:Q}\ -g\ ${BINGRP:Q}\ -m\ ${BINMODE:Q}
INSTALL_MAKE_FLAGS+=	INSTLIBFLAGS=-o\ ${BINOWN:Q}\ -g\ ${BINGRP:Q}\ -m\ ${BINMODE:Q}
INSTALL_MAKE_FLAGS+=	INSTINCFLAGS=-o\ ${SHAREOWN:Q}\ -g\ ${SHAREGRP:Q}\ -m\ ${SHAREMODE:Q}
INSTALL_MAKE_FLAGS+=	INSTMANFLAGS=-o\ ${MANOWN:Q}\ -g\ ${MANGRP:Q}\ -m\ ${MANMODE:Q}
INSTALL_MAKE_FLAGS+=	INSTDATFLAGS=-o\ ${SHAREOWN:Q}\ -g\ ${SHAREGRP:Q}\ -m\ ${SHAREMODE:Q}

.include "../../mk/bsd.pkg.mk"
