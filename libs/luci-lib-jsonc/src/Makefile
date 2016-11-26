JSONC_CFLAGS = -std=gnu99 -I/koolshare/include -I/koolshare/include/json-c
JSONC_LDFLAGS = -L/koolshare/lib -llua -lm -ljson-c
JSONC_OBJ = jsonc.o
JSONC_LIB = jsonc.so
FPIC= -fPIC

%.o: %.c
	$(CC) $(CPPFLAGS) $(CFLAGS) $(LUA_CFLAGS) $(JSONC_CFLAGS) $(FPIC) -c -o $@ $<

compile: $(JSONC_OBJ)
	$(CC) $(LDFLAGS) -shared -o $(JSONC_LIB) $(JSONC_OBJ) $(JSONC_LDFLAGS)

install: compile
	mkdir -p $(DESTDIR)/koolshare/lib/lua/luci
	cp $(JSONC_LIB) $(DESTDIR)/koolshare/lib/lua/luci/$(JSONC_LIB)

clean:
	rm -f *.o *.so
