# Copyright 2014 The Sporting Exchange Limited. All rights reserved.
# Use of this source code is governed by a free license that can be
# found in the LICENSE file.

export CGO_CFLAGS ?= $(shell pkg-config --cflags libzmq)
export CGO_LDFLAGS ?= $(shell pkg-config --libs libzmq)

.PHONY: build clean install

build:
	go install opentsp.org/cmd/collect-statse/...
	go vet opentsp.org/cmd/collect-statse/...
	go test opentsp.org/cmd/collect-statse/...

clean:
	go clean -i opentsp.org/cmd/collect-statse

install:
	install -m 755 -d $(DESTDIR)/usr/bin
	install -m 755 $(GOPATH)/bin/collect-statse $(DESTDIR)/usr/bin
	install -m 755 -d $(DESTDIR)/usr/share/man/man5
	install -m 755 dist/protocol.5 $(DESTDIR)/usr/share/man/man5/statse.5
	install -m 755 -d $(DESTDIR)/usr/share/man/man1
	install -m 755 dist/collector.1 $(DESTDIR)/usr/share/man/man1/collect-statse.1
