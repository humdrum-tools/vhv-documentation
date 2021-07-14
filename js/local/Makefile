
WGET = `which wget`
CURL = `which curl`
SRC = https://raw.githubusercontent.com/humdrum-tools/verovio-script/gh-pages/scripts/verovio-toolkit-wasm.js
BASE = verovio-toolkit-wasm.js


all:
ifneq (,$(WGET))
	$(WGET) $(SRC) -O $(BASE)
else
	$(CURL) -LO $(SRC) -o $(BASE)
endif


clean:
	@rm $(BASE)
