
.PHONY: all ci k8s-zilliqa k8s-scilla

# build the default zilliqa docker image same as the one on Docker Hub
all:
	docker build .

# build zilliqa docker image for CI usage
ci:


check-commit:
	@if [ -z "$(COMMIT)" ]; \
	then \
		echo "COMMIT=xxxxxxx is not passed in after make target"; \
		exit 1; \
	fi

# build zilliqa docker image for Kubernetes usage
k8s-zilliqa: check-commit
	cat Dockerfile Dockerfile.k8s | docker build -t zilliqa:$(COMMIT) \
		--build-arg COMMIT=$(COMMIT) .

k8s-scilla: check-commit
	cat Dockerfile Dockerfile.k8s | docker build -t zilliqa:$(COMMIT)+scilla \
		--build-arg COMMIT=$(COMMIT) --build-arg BASE=zilliqa/scilla .

