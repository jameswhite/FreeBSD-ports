# $FreeBSD$

PORTNAME=	renpy
PORTVERSION=	6.99.5
DISTVERSIONSUFFIX=-sdk
PORTREVISION=	1
CATEGORIES=	devel games
MASTER_SITES=	http://www.renpy.org/dl/${PORTVERSION}/

MAINTAINER=	jbeich@FreeBSD.org
COMMENT=	Framework for developing visual-novel type games

LICENSE=	APACHE20 BSD3CLAUSE DejaVu LGPL21 MIT OFL11 ZLIB
LICENSE_COMB=	multi
LICENSE_NAME_DejaVu=	Bitstream Vera and Arev fonts license
LICENSE_FILE_DejaVu=	${WRKSRC}/renpy/common/DejaVuSans.txt
LICENSE_PERMS_DejaVu=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}game_sdl2>=6.99.5:${PORTSDIR}/devel/py-game_sdl2 \
		cython:${PORTSDIR}/lang/cython
LIB_DEPENDS=	libfribidi.so:${PORTSDIR}/converters/fribidi \
		libGLEW.so:${PORTSDIR}/graphics/glew \
		libpng.so:${PORTSDIR}/graphics/png \
		libavcodec.so:${PORTSDIR}/multimedia/ffmpeg \
		libfreetype.so:${PORTSDIR}/print/freetype2
RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}game_sdl2>=6.99.5:${PORTSDIR}/devel/py-game_sdl2

# Upstream tends to reroll distfiles before moving under /release/
PORTSCOUT=	site:http://www.renpy.org/dl/release/

USES=		python:2.7 shebangfix tar:bz2
USE_PYTHON=	autoplist distutils
USE_SDL=	sdl2
EXCLUDE=	gen 'module/*.py[co]' 'renpy/*.py[co]'
EXTRACT_AFTER_ARGS=${EXCLUDE:S,^,--exclude ,}
SHEBANG_FILES=	renpy.py launcher/game/tkaskdir.py
python_OLD_CMD=	/usr/bin/env python
BUILD_WRKSRC=	${WRKSRC}/module
INSTALL_WRKSRC=	${BUILD_WRKSRC}
MAKE_ENV+=	RENPY_DEPS_INSTALL="${LOCALBASE}"
PORTDATA=	launcher renpy renpy.py templates
PORTDOCS=	*
PLIST_FILES=	bin/${PORTNAME}

DESKTOP_ENTRIES="Ren'Py" \
		"" \
		"${DATADIR}/launcher/game/images/logo32.png" \
		"${PORTNAME} %f" \
		"Development;Game;AdventureGame;" \
		""

OPTIONS_DEFAULT=TKINTER DIST
OPTIONS_DEFINE=	DOCS DIST EXAMPLES TKINTER

DIST_DESC=	Distribution runtimes for Windows, OS X, Linux
TKINTER_DESC=	Install Tkinter to allow choosing Projects Directory
TKINTER_RUN_DEPENDS=${PYTHON_PKGNAMEPREFIX}tkinter>0:${PORTSDIR}/x11-toolkits/py-tkinter

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MDIST}
LICENSE+=	ART20 PSFL
PORTDATA+=	lib renpy.app renpy.exe renpy.sh
. for lic in FREETYPE LIBJPEG LIBPNG MSVCR90
LICENSE+=	${lic}
LICENSE_NAME_${lic}=	${lic} license
LICENSE_FILE_${lic}=	${WRKSRC}/LICENSE.txt
LICENSE_PERMS_${lic}=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept
. endfor
.endif

.if ${PORT_OPTIONS:MEXAMPLES}
PORTDATA+=	the_question tutorial
.endif

post-patch:
	@${REINPLACE_CMD} -e 's,/usr/bin/python,${PYTHON_CMD},' \
		${WRKSRC}/launcher/game/choose_directory.rpy
# Avoid having to add -I/usr/include -L/usr/lib
	@${REINPLACE_CMD} '/library("z")/d' ${BUILD_WRKSRC}/${PYSETUP}

post-build:
	@${PYTHON_CMD} -m compileall -d ${DATADIR} ${WRKSRC}
	@${PYTHON_CMD} -O -m compileall -d ${DATADIR} ${WRKSRC}

add-plist-post: add-empty-dirs
add-empty-dirs:
# Keep images directory in templates, see renpy@d81ea29
	${FIND} ${WRKSRC}/templates -type d ! -name "saves" -empty | \
		${SED} 's,^${WRKSRC},@dir ${DATADIR},' >>${TMPPLIST}

post-install:
	${FIND} ${STAGEDIR}${PYTHONPREFIX_SITELIBDIR} -name \*.so \
		-exec ${STRIP_CMD} {} +
	${LN} -fs ${DATADIR}/renpy.py \
		${STAGEDIR}${PREFIX}/bin/${PORTNAME}
	(cd ${WRKSRC} && ${COPYTREE_SHARE} \
		"${PORTDATA}" ${STAGEDIR}${DATADIR} \
		"! -name *.orig ! -name *.bak \
		 ! -name saves ! -name log.txt")
	${CHMOD} +x ${STAGEDIR}${DATADIR}/renpy.py
	${CHMOD} -R u+w ${STAGEDIR}${DATADIR}/templates

post-install-DOCS-on:
	(cd ${WRKSRC}/doc && ${COPYTREE_SHARE} \
		. ${STAGEDIR}${DOCSDIR} \
		"! -name *.orig ! -name *.bak")

.include <bsd.port.mk>
