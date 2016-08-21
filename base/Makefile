run: build
	docker-compose up

build:
	docker build -t $(USER)/devbox-base --build-arg user=$(USER) .

rebuild:
	docker build --no-cache -t $(USER)/devbox-base --pull=true --build-arg user=$(USER) .

clean:
	docker kill $(USER)/devbox-base
	docker rm $(USER)/devbox-base
	docker rmi $(USER)/devbox-base

push:
	docker push $(USER)/devbox-base

publish: rebuild push
