# $FreeBSD$

PORTNAME=	wx
PORTVERSION=	3.0.2
PORTREVISION?=	3
CATEGORIES=	x11-toolkits
MASTER_SITES=	SF/wxwindows/${PORTVERSION}
PKGNAMESUFFIX=	30-gtk2
DISTNAME=	wxWidgets-${PORTVERSION}

MAINTAINER=	portmaster@bsdforge.com
COMMENT=	The wxWidgets GUI toolkit with GTK+ bindings

LIB_DEPENDS+=	libpng.so:${PORTSDIR}/graphics/png\
		libtiff.so:${PORTSDIR}/graphics/tiff\
		libexpat.so:${PORTSDIR}/textproc/expat2\
		libwebkitgtk-1.0.so:${PORTSDIR}/www/webkit-gtk2

USES+=		compiler:c++11-lib gmake iconv jpeg pkgconfig tar:bzip2
USE_XORG=	x11 sm xxf86vm xinerama
USE_GL=		glu
USE_GNOME=	gtk20
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--with-libpng=sys\
		--with-libjpeg=sys\
		--with-libtiff=sys\
		--with-zlib=sys\
		--with-expat=sys\
		--with-opengl\
		--with-libmspack\
		--with-gtk\
		--disable-backtrace\
		--enable-webview\
		--enable-graphics_ctx \
		--enable-compat26 \
		--enable-compat28
CONFIGURE_ENV=	X11BASE="${LOCALBASE}" \
		ac_cv_header_sys_inotify_h=no
CPPFLAGS+=	-I${LOCALBASE}/include
CXXFLAGS+=	-std=c++11
LIBS+=		-L${LOCALBASE}/lib

OPTIONS_DEFINE=	GSTREAMER MSPACK NLS
OPTIONS_DEFAULT=GSTREAMER MSPACK
MSPACK_DESC=	MS archives support
OPTIONS_SUB=	yes

NLS_USES=	gettext
GSTREAMER_ENABLE=	mediactrl
GSTREAMER_USE=	GNOME=gconf2 GSTREAMER=yes
MSPACK_CONFIGURE_WITH=	libmspack
MSPACK_LIB_DEPENDS=	libmspack.so:${PORTSDIR}/archivers/libmspack

.include <bsd.port.pre.mk>

# PR 196703, 197031
.if ${COMPILER_TYPE} == "gcc"
CONFIGURE_ARGS+=--disable-precomp-headers
.endif

.include <bsd.port.post.mk>
