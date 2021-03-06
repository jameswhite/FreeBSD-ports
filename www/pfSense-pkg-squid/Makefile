# $FreeBSD$

PORTNAME=	pfSense-pkg-squid
PORTVERSION=	0.2.9
CATEGORIES=	www
MASTER_SITES=	# empty
DISTFILES=	# empty
EXTRACT_ONLY=	# empty

MAINTAINER=	coreteam@pfsense.org
COMMENT=	pfSense package squid

RUN_DEPENDS=	${LOCALBASE}/sbin/squid:${PORTSDIR}/www/squid \
		${LOCALBASE}/libexec/squid/squid_radius_auth:${PORTSDIR}/www/squid_radius_auth \
		${LOCALBASE}/lib/c_icap/virus_scan.so:${PORTSDIR}/www/c-icap-modules \
		${LOCALBASE}/lib/c_icap/squidclamav.so:${PORTSDIR}/www/squidclamav

NO_BUILD=	yes
NO_MTREE=	yes

SUB_FILES=	pkg-install pkg-deinstall
SUB_LIST=	PORTNAME=${PORTNAME}

do-extract:
	${MKDIR} ${WRKSRC}

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/pkg
	${MKDIR} ${STAGEDIR}${PREFIX}/www
	${MKDIR} ${STAGEDIR}${PREFIX}/www/shortcuts
	${MKDIR} ${STAGEDIR}${PREFIX}/bin
	${MKDIR} ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} -m 0644 ${FILESDIR}${PREFIX}/pkg/squid.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid.inc \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_reverse_general.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_reverse_peer.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_reverse_uri.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_reverse_sync.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_sync.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_cache.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_nac.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_traffic.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_upstream.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_reverse.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_reverse.inc \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_auth.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_users.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_antivirus.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/sqpmon.sh \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/swapstate_check.php \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/pkg/squid_reverse_redir.xml \
		${STAGEDIR}${PREFIX}/pkg
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/www/squid_monitor.php \
		${STAGEDIR}${PREFIX}/www
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/www/squid_monitor_data.php \
		${STAGEDIR}${PREFIX}/www
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/www/squid_log_parser.php \
		${STAGEDIR}${PREFIX}/www
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/www/squid_clwarn.php \
		${STAGEDIR}${PREFIX}/www
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/www/shortcuts/pkg_squid.inc \
		${STAGEDIR}${PREFIX}/www/shortcuts
	${INSTALL_DATA} -m 0755 ${FILESDIR}${PREFIX}/bin/check_ip.php \
		${STAGEDIR}${PREFIX}/bin
	${INSTALL_DATA} ${FILESDIR}${DATADIR}/info.xml \
		${STAGEDIR}${DATADIR}

.include <bsd.port.mk>
