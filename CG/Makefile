SHELL=/bin/sh
BENCHMARK=cg
BENCHMARKU=CG
MKL_LINKER=/opt/intel/oneapi/mkl/latest/bin/intel64/mkl_link_tool

include ../config/make.def

OBJS = cg.o ${COMMON}/c_print_results.o  \
       ${COMMON}/c_${RAND}.o ${COMMON}/c_timers.o ${COMMON}/c_wtime.o

include ../sys/make.common

${PROGRAM}: config ${OBJS}
	${MKL_LINKER} clang ${CLINKFLAGS} -o ${PROGRAM} ${OBJS} ${C_LIB} -lm -fopenmp

cg.o:		cg.c  npbparams.h
	${MKL_LINKER} ${CCOMPILE} cg.c -fopenmp 

clean:
	- rm -f *.o *~ 
	- rm -f npbparams.h core



