# $NetBSD: Makefile,v 1.24 2021/04/21 11:42:04 adam Exp $

DISTNAME=	ibus-libpinyin-1.12.0
PKGREVISION=	1
CATEGORIES=	inputmethod chinese
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=libpinyin/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	https://github.com/libpinyin/ibus-libpinyin/
COMMENT=	Intelligent Pinyin engine based on libpinyin for IBus
LICENSE=	gnu-gpl-v3

GNU_CONFIGURE=	yes
USE_TOOLS+=	gmake msgfmt pkg-config
USE_LANGUAGES=	c c++
USE_LIBTOOL=	yes

PYTHON_VERSIONS_INCOMPATIBLE=	27

.include "options.mk"

.include "../../mk/bsd.prefs.mk"
.include "../../mk/compiler.mk"

# msgfmt: unknown option -- desktop
GETTEXT_TOOLS_REQD=	0.19.7

.if (!empty(PKGSRC_COMPILER:Mgcc) && (empty(CC_VERSION:Mgcc-[0-3].*) && empty(CC_VERSION:Mgcc-4.[0-3].*))) || !empty(PKGSRC_COMPILER:Mclang)
CONFIGURE_ARGS+=	--disable-boost
.else
CONFIGURE_ARGS+=	--enable-boost
CONFIGURE_ARGS+=	--with-boost=${BUILDLINK_PREFIX.boost-headers}
.include "../../devel/boost-headers/buildlink3.mk"
.endif

.include "../../devel/glib2/schemas.mk"
.include "../../devel/gettext-lib/buildlink3.mk"
.include "../../databases/sqlite3/buildlink3.mk"
.include "../../inputmethod/ibus/buildlink3.mk"
.include "../../textproc/libpinyin/buildlink3.mk"
.include "../../x11/gtk3/buildlink3.mk"
.include "../../lang/python/application.mk"
.include "../../devel/glib2/schemas.mk"
.include "../../mk/bsd.pkg.mk"
