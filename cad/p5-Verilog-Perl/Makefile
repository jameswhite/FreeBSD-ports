# Created by: Otacilio de Araujo Ramos Neto <otacilio.neto@ee.ufcg.edu.br>
# $FreeBSD$

PORTNAME=	Verilog-Perl
PORTVERSION=	3.404
PORTREVISION=	1
CATEGORIES=	cad perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	otacilio.neto@ee.ufcg.edu.br
COMMENT=	Building point for Verilog support in the Perl language

BUILD_DEPENDS=	flex>=2.5.35:${PORTSDIR}/textproc/flex

USES=		bison gmake perl5
USE_PERL5=	configure
USE_GCC=	any
CONFIGURE_ENV=	CXX=${CXX}\
		CPP=${CPP}\
		CC=${CC}

.include <bsd.port.pre.mk>

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/${SITE_ARCH_REL}/auto/Verilog/Parser/*.so

regression-test: build
	make test -C ${WRKSRC}

.include <bsd.port.post.mk>
