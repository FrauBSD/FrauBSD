# $FreeBSD$

LIB=	efi
INTERNALLIB=

SRCS=	delay.c efi_console.c efinet.c efipart.c errno.c handles.c \
	libefi.c time.c

.if ${MACHINE_CPUARCH} == "aarch64"
CFLAGS+=	-msoft-float -mgeneral-regs-only
.endif
.if ${MACHINE_ARCH} == "amd64"
CFLAGS+= -fPIC -mno-red-zone
.endif
CFLAGS+= -I${.CURDIR}/../include
CFLAGS+= -I${.CURDIR}/../include/${MACHINE}
CFLAGS+= -I${.CURDIR}/../../../../lib/libstand

# Pick up the bootstrap header for some interface items
CFLAGS+= -I${.CURDIR}/../../common

# Handle FreeBSD specific %b and %D printf format specifiers
CFLAGS+= ${FORMAT_EXTENSIONS}
CFLAGS+= -DTERM_EMU

.include <bsd.lib.mk>
