# rdp_task: the RSP model's commands through MRDP's model, to an image.
CC ?= cc
CFLAGS ?= -O2 -Wall -Wextra
# (the N64's commands: without MRDP_N64 the model is MRDP's, and draws none of a game's)
DEFS ?= -DMRDP_N64
# C32=1: 32-bit colour images (docs/cimg32.md), as the RTL has them with its CIMG32 parameter (build_rtl.sh takes the
# same switch); C32=0: a primitive into one is dropped
C32 ?= 1
ifeq ($(C32),1)
DEFS += -DRDP_CIMG32
endif
M = ../../lang/c/mrdp
SRC = rdp_task.c ../rsp/rsp.c ../rsp/rsp.h $(M)/mrdp.c $(M)/mrdp.h $(M)/mrdp_setup.h
rdp_task: $(SRC)
	$(CC) $(CFLAGS) $(DEFS) -I../rsp -I$(M) rdp_task.c ../rsp/rsp.c $(M)/mrdp.c -o $@
# the same with 32-bit colour images (docs/cimg32.md) whatever C32 says
rdp_task_cimg32: $(SRC)
	$(CC) $(CFLAGS) $(DEFS) -DRDP_CIMG32 -I../rsp -I$(M) rdp_task.c ../rsp/rsp.c $(M)/mrdp.c -o $@
clean:
	rm -f rdp_task rdp_task_cimg32
.PHONY: clean
