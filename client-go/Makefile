GOBIN = $(shell pwd)/bin

define go-install-tool
@[ -f $(1) ] || {\
set -e ;\
GOBIN=$(GOBIN) go install $(2) ;\
}
endef

tools = conversion-gen deepcopy-gen defaulter-gen
.PHONY: tools
tools: $(tools)

$(tools):
	$(call go-install-tool,$(GOBIN)/$@,k8s.io/code-generator/cmd/$@@$(shell go list -m k8s.io/code-generator | cut -d' ' -f 2))