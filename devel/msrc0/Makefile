# Created by: ajk@waterspout.com
# $FreeBSD$

PORTNAME=	msrc0
PORTVERSION=	0.7
CATEGORIES=	devel
MASTER_SITES=	ftp://ftp.physics.purdue.edu/pub/pundits/ \
		http://www.komquats.com/distfiles/ \
		http://people.freebsd.org/~cy/distfiles/
EXTRACT_SUFX=	.tgz

MAINTAINER=	cy@FreeBSD.org
COMMENT=	Meta source fake-out script for building ksb tools

NO_BUILD=	yes
PLIST_FILES=	bin/makeme
WRKSRC=		${WRKDIR}/${PORTNAME}-0.6

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/makeme ${STAGEDIR}${PREFIX}/bin

.include <bsd.port.mk>
