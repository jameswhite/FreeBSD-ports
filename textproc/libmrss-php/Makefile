# Created by: Rodrigo Osorio <rodrigo@FreeBSD.org>
# $FreeBSD$

PORTNAME=	libmrss
PORTVERSION=	0.19.2
PORTREVISION=	2
CATEGORIES=	textproc
MASTER_SITES=	http://www.autistici.org/bakunin/libmrss/
PKGNAMESUFFIX=	-php

MAINTAINER=	ports@FreeBSD.org
COMMENT=	PHP library for parsing, writing, and creating RSS

LICENSE=	LGPL21 # or later
LICENSE_FILE=	${WRKSRC}/../COPYING

LIB_DEPENDS=	libmrss.so:${PORTSDIR}/textproc/libmrss

GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

USES=		libtool
USE_LDCONFIG=	yes

USE_PHP=	yes
USE_PHPEXT=	yes
PHP_MODNAME=	mrss
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}/phpmrss

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/php/${PHP_EXT_DIR}/mrss.so

.include <bsd.port.mk>
