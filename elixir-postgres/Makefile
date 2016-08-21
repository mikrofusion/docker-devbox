run: build
	docker-compose up

build-deps:
	make -C ../base build

build: build-deps
	m4 -D __user__=$(USER) Dockerfile.m4 > Dockerfile
	docker build -t $(USER)/devbox-elixir-postgres --build-arg user=$(USER) .

rebuild-deps:
	make -C ../base rebuild

rebuild: rebuild-deps
	m4 -D __user__=$(USER) Dockerfile.m4 > Dockerfile
	docker build --no-cache -t $(USER)/devbox-elixir-postgres --pull=true --build-arg user=$(USER) .

clean:
	docker kill $(USER)/devbox-elixir-postgres
	docker rm $(USER)/devbox-elixir-postgres
	docker rmi $(USER)/devbox-elixir-postgres

push:
	docker push $(USER)/devbox-elixir-postgres

publish: rebuild push
