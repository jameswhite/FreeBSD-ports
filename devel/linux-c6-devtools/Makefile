# Created by: Johannes Meixner <xmj@chaot.net>
# $FreeBSD$

PORTNAME=	devtools
PORTVERSION=	6.6
PORTREVISION=	4
CATEGORIES=	devel
MASTER_SITES=	CENTOS_LINUX CENTOS_LINUX_UPDATES
DISTFILES=	binutils-2.20.51.0.2-5.42.el6.${LINUX_RPM_ARCH}.rpm \
		binutils-devel-2.20.51.0.2-5.42.el6.${LINUX_RPM_ARCH}.rpm \
		glibc-devel-2.12-1.149.el6_6.9.${LINUX_RPM_ARCH}.rpm \
		glibc-headers-2.12-1.149.el6_6.9.${LINUX_RPM_ARCH}.rpm \
		kernel-headers-2.6.32-504.23.4.el6.${LINUX_RPM_ARCH}.rpm \
		libstdc++-devel-4.4.7-11.el6.${LINUX_RPM_ARCH}.rpm \
		libgomp-4.4.7-11.el6.${LINUX_RPM_ARCH}.rpm \
		mpfr-2.4.1-6.el6.${LINUX_RPM_ARCH}.rpm \
		cpp-4.4.7-11.el6.${LINUX_RPM_ARCH}.rpm \
		gcc-4.4.7-11.el6.${LINUX_RPM_ARCH}.rpm \
		gcc-c++-4.4.7-11.el6.${LINUX_RPM_ARCH}.rpm \
		gcc-gfortran-4.4.7-11.el6.${LINUX_RPM_ARCH}.rpm

MAINTAINER=	emulation@FreeBSD.org
COMMENT=	Linux compilers and base libraries (CentOS ${LINUX_DIST_VER})

# LICENSE=	Various GNU

RUN_DEPENDS+=	linux-c6-libgfortran>0:${PORTSDIR}/devel/linux-c6-libgfortran

ONLY_FOR_ARCHS=	i386 amd64
USE_LINUX=	c6
USE_LINUX_RPM=	yes
USE_LDCONFIG=	yes

PLIST_SUB+=	NLS=""

SRC_DISTFILES=	binutils-2.20.51.0.2-5.42.el6.src.rpm:SOURCE \
		glibc-2.12-1.149.el6_6.9.src.rpm:SOURCE \
		kernel-2.6.32-504.23.4.el6.src.rpm:SOURCE \
		mpfr-2.4.1-6.el6.src.rpm:SOURCE \
		gcc-4.4.7-11.el6.src.rpm:SOURCE

post-install:
.	if defined(OVERRIDE_LINUX_BASE_PORT) && ${OVERRIDE_LINUX_BASE_PORT} == "c6_64"
	${LN} -sf ${LINUXBASE}/lib64/libgcc_s.so.1 \
	${STAGEDIR}${PREFIX}/usr/lib/gcc/x86_64-redhat-linux/4.4.4/libgcc_s.so
.	else
	${LN} -sf ${LINUXBASE}/lib/libgcc_s.so.1 \
	${STAGEDIR}${PREFIX}/usr/lib/gcc/i686-redhat-linux/4.4.4/libgcc_s.so
.	endif

.include <bsd.port.mk>
