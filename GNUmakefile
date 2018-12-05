#
#	Makefile for hookAPI
#
# switches:
#	define the ones you want in the CFLAGS definition...
#
#	TRACE		- turn on tracing/debugging code
#
#
#
#

# Version for distribution
VER=1_0r1
GOPATH=$(shell go env GOPATH):$(PWD)

export GOPATH
MAKEFILE=GNUmakefile

# We Use Compact Memory Model

all: bin/go-trade
	@[ -d bin ] || exit

bin/go-trade: trade/main.go
	@[ -d bin ] || mkdir bin
	(cd trade; go build -o ../bin/go-trade)
	@strip $@ || echo "go-trade OK"

win64: bin/trade64.exe
win32: bin/trade32.exe

bin/trade64.exe: bin trade/main.go
	(cd trade; GOOS=windows GOARCH=amd64 go build -o ../bin/trade64.exe)

bin/trade32.exe: bin trade/main.go
	(cd trade; GOOS=windows GOARCH=386 go build -o ../bin/trade32.exe)

clean:

distclean: clean
	@rm -rf bin
