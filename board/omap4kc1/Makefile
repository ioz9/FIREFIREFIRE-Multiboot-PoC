#
# (C) Copyright 2009
# Texas Instruments, <www.ti.com>
#
# (C) Copyright 2000, 2001, 2002
# Wolfgang Denk, DENX Software Engineering, wd@denx.de.
#
# See file CREDITS for list of people who contributed to this
# project.
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# version 2 as published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston,
# MA 02111-1307 USA
#

include $(TOPDIR)/config.mk

LIB	= lib$(BOARD).a

OBJS	:= omap4kc1.o mmc.o normalboot.o recoveryboot.o boot2.o

$(LIB):	$(OBJS)
	$(AR) crv $@ $^

normalboot.o:
	$(OBJCOPY) -I binary -O elf32-littlearm -B arm normalboot.rle $@

recoveryboot.o:
	$(OBJCOPY) -I binary -O elf32-littlearm -B arm recoveryboot.rle $@

boot2.o:
	$(OBJCOPY) -I binary -O elf32-littlearm -B arm boot2.rle $@

clean:
	rm -f $(OBJS)

distclean:	clean
	rm -f $(LIB) core *.bak .depend

#########################################################################

.depend:	Makefile $(OBJS:.o=.c)
		$(CC) -M $(CPPFLAGS) $(OBJS:.o=.c) > $@

-include .depend

#########################################################################
