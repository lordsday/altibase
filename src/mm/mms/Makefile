include ../mmEnv.mk

SRCS= $(MMS_SRCS)
OBJS=$(SRCS:$(DEV_DIR)/src/%.cpp=$(TARGET_DIR)/%.$(OBJEXT))


all: $(COMPILE)

compile: $(OBJS)

compile_pp: $(PPOBJS)

compile_pg: $(PGOBJS)

compile_pt: $(PTOBJS)

header :
	@for i in $(SRCS); do ( cp $$i $$i.org ; cat $$i.org | gawk  -f $(TOOL_DIR)/add_header/header.awk > $$i ) done

check :
	@for i in $(SRCS); do (gawk -v API_INPUT=$(TOOL_DIR)/coding_chk/API.txt -v SRC_INPUT=$$i -f $(TOOL_DIR)/coding_chk/apiCheck.awk ) done

alint: $(SRCS:.cpp=.lint)

clean:
	$(RM) $(TARGET_DIR)/src/mm/mms core .dependency *.d SunWS_cache

-include $(OBJS:.$(OBJEXT)=.d)
