# Created by: Gea-Suan Lin <gslin@gslin.org>
# $FreeBSD$

PORTNAME=	Astro-SpaceTrack
PORTVERSION=	0.092
CATEGORIES=	astro perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Retrieve orbital data from www.space-track.org

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-HTTP-Date>=0:${PORTSDIR}/www/p5-HTTP-Date \
		p5-HTTP-Message>=6.03:${PORTSDIR}/www/p5-HTTP-Message \
		p5-JSON>=0:${PORTSDIR}/converters/p5-JSON \
		p5-LWP-Protocol-https>=0:${PORTSDIR}/www/p5-LWP-Protocol-https \
		p5-URI>=0:${PORTSDIR}/net/p5-URI \
		p5-libwww>=0:${PORTSDIR}/www/p5-libwww
RUN_DEPENDS:=	${BUILD_DEPENDS}

PORTSCOUT=	limit:^[0-9\.]*$$

CONFIGURE_ARGS=	-y
NO_ARCH=	yes
USES=		perl5
USE_PERL5=	configure

.include <bsd.port.pre.mk>

.if ${PERL_LEVEL} < 501800
BUILD_DEPENDS+=	p5-Getopt-Long>=2.39:${PORTSDIR}/devel/p5-Getopt-Long
RUN_DEPENDS+=	p5-Getopt-Long>=2.39:${PORTSDIR}/devel/p5-Getopt-Long
.endif

.include <bsd.port.post.mk>
