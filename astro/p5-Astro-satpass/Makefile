# Created by: Wen Heping <wenheping@gmail.com>

PORTNAME=	Astro-satpass
PORTVERSION=	0.121
CATEGORIES=	astro perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Classes and app to compute satellite visibility

LICENSE=	ART10 GPLv1+
LICENSE_COMB=	dual
LICENSE_FILE_ART10=	${WRKSRC}/LICENSES/Artistic
LICENSE_FILE_GPLv1+ =	${WRKSRC}/LICENSES/Copying

BUILD_DEPENDS=	${RUN_DEPENDS}
RUN_DEPENDS=	p5-Date-Manip>=1.14:devel/p5-Date-Manip
TEST_DEPENDS=	p5-JSON>=0:converters/p5-JSON

USES=		perl5
USE_PERL5=	configure

CONFIGURE_ARGS=	-y
NO_ARCH=	yes

PORTSCOUT=	limit:^[0-9\.]*$$

OPTIONS_DEFINE=	SIMBAD SOAPLITE SPACETRACK USGS
OPTIONS_DEFAULT=SIMBAD SPACETRACK USGS
SIMBAD_DESC=	Add support for Astro::SIMBAD::Client
SOAPLITE_DESC=	Add support for SOAP::Lite (deprecated)
SPACETRACK_DESC=Add support for Astro::SpaceTrack
USGS_DESC=	Add support for Geo::WebService::Elevation::USGS

SIMBAD_RUN_DEPENDS=	p5-Astro-SIMBAD-Client>=0:astro/p5-Astro-SIMBAD-Client
SOAPLITE_RUN_DEPENDS=	p5-SOAP-Lite>=0:net/p5-SOAP-Lite
SPACETRACK_RUN_DEPENDS=	p5-Astro-SpaceTrack>=0:astro/p5-Astro-SpaceTrack
USGS_RUN_DEPENDS=	p5-Geo-WebService-Elevation-USGS>=0:science/p5-Geo-WebService-Elevation-USGS

.include <bsd.port.mk>
