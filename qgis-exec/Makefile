.PHONY: install
install: .venv/bin/docker-compose

.PHONY: build
build: deb/.copy.ts
	docker build -t qgis-exec .

.PHONY: stack-up
stack-up: .venv/bin/docker-compose
	.venv/bin/docker-compose up

.PHONY: stack-down
stack-down: .venv/bin/docker-compose
	.venv/bin/docker-compose rm -sf

.PHONY: clean
clean:
	rm -rf .venv

.venv/bin/docker-compose: .venv/bin/python3
	.venv/bin/pip install docker-compose

.venv/bin/python3:
	virtualenv .venv

deb/.copy.ts:
ifndef DEBSRCDIR
	$(error DEBSRCDIR not defined)
else
	@mkdir -p $(dir $@)
	@cp $(shell find $(DEBSRCDIR) -name *.deb) deb/
	@touch $@
endif