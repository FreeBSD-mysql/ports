PORTNAME=	pocl
PORTVERSION=	1.8
DISTVERSIONPREFIX=v
CATEGORIES=	lang

MAINTAINER=	ohartmann@freebsd-de.org
COMMENT=	POrtable Computing Language (POCL)

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

ONLY_FOR_ARCHS=	aarch64 amd64 i386
ONLY_FOR_ARCHS_REASON=	only tested on x86

BUILD_DEPENDS=	llvm${LLVM_VERSION}>=10:devel/llvm${LLVM_VERSION} \
		opencl>=2.2:devel/opencl
LIB_DEPENDS=	libhwloc.so:devel/hwloc2 libOpenCL.so:devel/ocl-icd
RUN_DEPENDS=	${BUILD_DEPENDS}

USES=		cmake localbase:ldflags ncurses pkgconfig
USE_GITHUB=	yes
USE_LDCONFIG=	yes

LLVM_VERSION=	${MESA_LLVM_VER:U13}
CMAKE_ARGS=	-DWITH_LLVM_CONFIG="${LOCALBASE}/llvm${LLVM_VERSION}/bin/llvm-config" \
		-DPOCL_INSTALL_PKGCONFIG_DIR="${PREFIX}/libdata/pkgconfig" \
		-DSINGLE_LLVM_LIB=ON \
		${CMAKE_ARGS_${ARCH}}

CMAKE_ARGS_aarch64=	-DLLC_HOST_CPU=cortex-a53
CMAKE_ARGS_amd64=	-DKERNELLIB_HOST_CPU_VARIANTS="distro"

PLIST_SUB=	CONFIGURE_TARGET=${CONFIGURE_TARGET:S/amd64/x86_64/}

OPTIONS_DEFINE=	DOCS

DOCS_DESC=	Build documentation (needs sphinx)
DOCS_CMAKE_OFF=	-DENABLE_DOCS=OFF
DOCS_CMAKE_ON=	-DENABLE_DOCS=ON
DOCS_USES=	python:3.6+
DOCS_BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}sphinx>=0,1:textproc/py-sphinx@${PY_FLAVOR}

.include <bsd.port.options.mk>

.if ${ARCH} == aarch64
PLIST_SUB+=     AARCH64=""
PLIST_SUB+=	X86="@comment "
.else
PLIST_SUB+=     AARCH64="@comment "
PLIST_SUB+=	X86=""
.endif
PLIST_SUB+=	CONFIGURE_TARGET=${CONFIGURE_TARGET:S/amd64/x86_64/}

.include <bsd.port.mk>
