# Created by: Pierre Guinoiseau <geekounet@poildetroll.net>
# $FreeBSD$

PORTNAME=	grake
PORTVERSION=	0.1.0
PORTREVISION=	1
CATEGORIES=	multimedia
MASTER_SITES=	GOOGLE_CODE

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Command line tool for scanning webpages for Youtube links

LICENSE=	GPLv3 # or later
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	p5-Getopt-ArgvFile>=1.11:${PORTSDIR}/devel/p5-Getopt-ArgvFile \
		p5-Umph-Prompt>=0:${PORTSDIR}/multimedia/p5-Umph-Prompt \
		p5-libwww>=5.835:${PORTSDIR}/www/p5-libwww
RUN_DEPENDS=	p5-Getopt-ArgvFile>=1.11:${PORTSDIR}/devel/p5-Getopt-ArgvFile \
		p5-Umph-Prompt>=0:${PORTSDIR}/multimedia/p5-Umph-Prompt \
		p5-libwww>=5.835:${PORTSDIR}/www/p5-libwww
TEST_DEPENDS=	p5-Test-Pod>=1:${PORTSDIR}/devel/p5-Test-Pod

USES=		perl5
USE_PERL5=	configure
NO_ARCH=	yes

PLIST_FILES=	bin/grake man/man1/grake.1.gz

.include <bsd.port.mk>
