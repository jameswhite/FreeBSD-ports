# Created by: Torsten Zühlsdorff <ports@toco-domains.de>
# $FreeBSD$

PORTNAME=	sidetiq
PORTVERSION=	0.6.3
CATEGORIES=	devel rubygems
MASTER_SITES=	RG

MAINTAINER=	ruby@freebsd.org
COMMENT=	Recurring jobs for Sidekiq

LICENSE=	BSD

RUN_DEPENDS=	rubygem-celluloid>=0.14.1:${PORTSDIR}/devel/rubygem-celluloid \
		rubygem-ice_cube>=0.11.1:${PORTSDIR}/devel/rubygem-ice_cube \
		rubygem-sidekiq>=3.0.0:${PORTSDIR}/devel/rubygem-sidekiq

NO_ARCH=	yes

USE_RUBY=	yes
USE_RUBYGEMS=	yes
RUBYGEM_AUTOPLIST=	yes

.include <bsd.port.mk>
