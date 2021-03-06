# Created by: Ying-Chieh Liao <ijliao@FreeBSD.org>
# $FreeBSD$
#    $MCom: ports/editors/poedit/Makefile,v 1.2 2006/10/05 07:03:09 mezz Exp $

PORTNAME=	poedit
PORTVERSION=	1.8.4
CATEGORIES=	editors
MASTER_SITES=	http://github.com/vslavik/${PORTNAME}/releases/download/v${PORTVERSION}-oss/

MAINTAINER=	rodrigo@FreeBSD.org
COMMENT=	Gettext catalogs (.po files) editor

LICENSE=	BSD2CLAUSE

BUILD_DEPENDS=	zip:${PORTSDIR}/archivers/zip
LIB_DEPENDS=	libgtkspell.so:${PORTSDIR}/textproc/gtkspell \
		libboost_thread.so:${PORTSDIR}/devel/boost-libs \
		liblucene++.so:${PORTSDIR}/textproc/luceneplusplus

USES=		gettext gmake pkgconfig desktop-file-utils
USE_WX=		3.0
WX_CONF_ARGS=	absolute
WX_UNICODE=	yes
USE_BDB=	yes
WITH_BDB_HIGHEST=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ENV=	WXRC="${WXRC_CMD}"
INSTALLS_ICONS=	yes

CPPFLAGS+=	-I${BDB_INCLUDE_DIR} -I${LOCALBASE}/include
LDFLAGS+=	-lpthread -L${BDB_LIB_DIR} -L${LOCALBASE}/lib

OPTIONS_DEFINE=	NLS
OPTIONS_SUB=yes

NLS_USES= gettext
NLS_CONFIGURE_ENABLE= nls

post-patch:
	@${REINPLACE_CMD} -e \
		's/for version in .*;/for version in ${BDB_VER};/ ; \
		s/-ldb-$$version/-l${BDB_LIB_NAME}/' ${WRKSRC}/configure

.include <bsd.port.mk>
