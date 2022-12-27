OAUTH_PROVIDER_BINARY=oauthProviderApp

## up: starts all containers in the background without forcing build
up:
	@echo "Starting Docker images..."
	docker compose up -d
	@echo "Docker images started!"

## up_build: stops docker compose (if running), builds all projects and starts docker compose
up_build: build_oauth_provider
	@echo "Stopping docker images (if running...)"
	docker compose down
	@echo "Building (when required) and starting docker images..."
	docker compose up --build -d
	@echo "Docker images built and started!"

## down: stop docker compose
down:
	@echo "Stopping docker compose..."
	docker compose down
	@echo "Done!"

## down: stop docker compose and remove every thing
down_v:
	@echo "Stopping docker compose..."
	docker compose down -v
	@echo "Done!"

## build_oauth_provider: builds the Oauth Provider binary as a linux executable
build_oauth_provider:
	@echo "Building Oauth Provider binary..."
	cd ../oauth-provider && env GOOS=linux CGO_ENABLED=0 go build -o ${OAUTH_PROVIDER_BINARY} ./cmd/api
	@echo "Done!"