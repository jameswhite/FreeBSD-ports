# Created by: Koop Mast <kwm@FreeBSD.org>
# $FreeBSD$

PORTNAME=	evolution-ews
PORTVERSION=	3.16.4
CATEGORIES=	mail gnome
MASTER_SITES=	GNOME
DIST_SUBDIR=	gnome3

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	Evolution Microsoft Exchange plugin through Exchange Web Services

BUILD_DEPENDS=	evolution>=3.0.0:${PORTSDIR}/mail/evolution
LIB_DEPENDS=	libsoup-2.4.so:${PORTSDIR}/devel/libsoup \
		libmspack.so:${PORTSDIR}/archivers/libmspack \
		libical.so:${PORTSDIR}/devel/libical
RUN_DEPENDS=	evolution>=3.0.0:${PORTSDIR}/mail/evolution

PORTSCOUT=	limitw:1,even

USES=		gettext gmake libtool pathfix pkgconfig tar:xz
USE_GNOME=	intlhack
GNU_CONFIGURE=	yes
USE_SQLITE=	3
USE_BDB=	5
USE_OPENLDAP=	yes
USE_LDCONFIG=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
CONFIGURE_ARGS=	--datarootdir=${PREFIX}/share \
		--localedir=${PREFIX}/share/locale \
		--prefix=${PREFIX}
INSTALL_TARGET=	install-strip

post-patch:
	@${REINPLACE_CMD} -e 's|$$(prefix)/$$(DATADIRNAME)/|$$(prefix)/share/|g' \
		${WRKSRC}/configure

.include <bsd.port.mk>
