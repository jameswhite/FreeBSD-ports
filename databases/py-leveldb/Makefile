# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>
# $FreeBSD$

PORTNAME=	leveldb
PORTVERSION=	0.1.20130428
PORTREVISION=	3
CATEGORIES=	databases python
MASTER_SITES=	LOCAL/sunpoet
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	py-${PORTNAME}-${PORTVERSION}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Thread-safe Python binding for LevelDB

LICENSE=	BSD3CLAUSE

LIB_DEPENDS=	libleveldb.so:${PORTSDIR}/databases/leveldb

USE_PYTHON=	autoplist distutils
USES=		python tar:xz

post-patch:
	@${REINPLACE_CMD} \
		-e "s|^\(extra_compile_args = \).*$$|\1\['-I${LOCALBASE}/include'\]|" \
		-e "s|^\(extra_link_args = \).*$$|\1\['-L${LOCALBASE}/lib', '-lleveldb'\]|" \
			${WRKSRC}/setup.py

post-install:
	${STRIP_CMD} ${STAGEDIR}${PYTHON_SITELIBDIR}/leveldb.so

.include <bsd.port.mk>
