# $NetBSD: Makefile,v 1.26 2021/05/24 19:49:07 wiz Exp $

DISTNAME=	MusicBrainz-Queries-0.11
PKGNAME=	p5-${DISTNAME}
PKGREVISION=	13
CATEGORIES=	audio perl5
MASTER_SITES=	${MASTER_SITE_PERL_CPAN:=MusicBrainz/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://www.musicbrainz.org/
COMMENT=	Provide access to the Music Brainz RDF Query Constants
LICENSE=	${PERL5_LICENSE}

PERL5_PACKLIST=		auto/MusicBrainz/Queries/.packlist

.include "../../audio/musicbrainz/buildlink3.mk"
.include "../../lang/perl5/module.mk"
.include "../../mk/bsd.pkg.mk"
