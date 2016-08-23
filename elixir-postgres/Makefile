run: build-deps
	docker-compose up -d

stop:
	docker-compose down

build-deps:
	make -C ../base build

build: build-deps
	docker-compose build

rebuild-deps:
	make -C ../base rebuild

rebuild: rebuild-deps
	docker-compose build --no-cache
