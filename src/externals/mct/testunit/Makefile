
SHELL           = /bin/sh

# SOURCE FILES

SRCS_F90	= master.F90		\
		  AttrVect_Test.F90		\

OBJS_ALL	= $(SRCS_F90:.F90=.o)

# MACHINE AND COMPILER FLAGS

include ../Makefile.conf

# ADDITIONAL DEFINITIONS SPECIFIC FOR UTMCT COMPILATION

MCTLIBS    = -L$(MPEUPATH) -L$(MCTPATH) -lmct -lmpeu
UTLDFLAGS  = $(REAL8)
UTCMPFLAGS = $(REAL8) $(INCFLAG)$(MPEUPATH) $(INCFLAG)$(MCTPATH)

# TARGETS

all:	mctTester

mctTester: $(OBJS_ALL)
	$(FC) -o $@ $(OBJS_ALL) $(FCFLAGS) $(UTLDFLAGS) $(MCTLIBS) $(MPILIBS)

# RULES

.SUFFIXES:
.SUFFIXES: .F90 .o

.F90.o:
	$(FC) -c $(INCPATH) $(FPPDEFS) $(FCFLAGS) $(MCTFLAGS) $(UTCMPFLAGS) $<

clean:
	${RM} *.o *.mod mctTester

# DEPENDENCIES:

$(OBJS_ALL): $(MCTPATH)/libmct.a
