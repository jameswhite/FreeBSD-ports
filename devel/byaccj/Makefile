# Created by: David Xu
# $FreeBSD$

PORTNAME=	byaccj
PORTVERSION=	1.15
CATEGORIES=	devel java
MASTER_SITES=	SF \
		http://www.skysmurf.nl/comp/FreeBSD/distfiles/
DISTNAME=	${PORTNAME}${PORTVERSION}_src

MAINTAINER=	freebsd@skysmurf.nl
COMMENT=	Java extension of BSD YACC-compatible parser generator

PLIST_FILES=	bin/byaccj
WRKSRC=		${WRKDIR}/${PORTNAME}${PORTVERSION}/src

post-patch:
	@${REINPLACE_CMD} -e 's#<malloc.h>#<stdlib.h>#' ${WRKSRC}/defs.h ${WRKSRC}/*c

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/yacc ${STAGEDIR}${PREFIX}/bin/byaccj

.include <bsd.port.mk>
