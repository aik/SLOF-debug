# *****************************************************************************
# * Copyright (c) 2015-2020 IBM Corporation
# * All rights reserved.
# * This program and the accompanying materials
# * are made available under the terms of the BSD License
# * which accompanies this distribution, and is available at
# * http://www.opensource.org/licenses/bsd-license.php
# *
# * Contributors:
# *     IBM Corporation - initial implementation
# ****************************************************************************/

TOPCMNDIR ?= ../..

CPPFLAGS = -I../libc/include $(CPUARCHDEF) -I$(INCLBRDDIR) \
	   -I$(INCLCMNDIR) -I$(INCLCMNDIR)/$(CPUARCH) -I$(SLOFCMNDIR)
CPPFLAGS += -I../libhvcall
CPPFLAGS += $(RELEASE)

LDFLAGS = -nostdlib

TARGET = ../libtpm.a


all: $(TARGET)

SRCS = tpm_drivers.c sha.c sha256.c sha512.c tcgbios.c

OBJS = $(SRCS:%.c=%.o)

$(TARGET): $(OBJS)
	$(AR) -rc $@ $(OBJS)
	$(RANLIB) $@

clean:
	$(RM) $(TARGET) $(OBJS)

distclean: clean
	$(RM) Makefile.dep


# Rules for creating the dependency file:
depend:
	$(RM) Makefile.dep
	$(MAKE) Makefile.dep

Makefile.dep: Makefile
	$(CC) -M $(CPPFLAGS) $(CFLAGS) $(SRCS) $(SRCSS) > Makefile.dep

# Include dependency file if available:
-include Makefile.dep
