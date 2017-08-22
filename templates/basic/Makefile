#                   ##        .
#             ## ## ##       ==
#          ## ## ## ##      ===
#      /""""""""""""""""\___/ ===
# ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~
#      \______ o          __/
#        \    \        __/
#         \____\______/
#
#         |          |
#      __ |  __   __ | _  __   _
#     /  \| /  \ /   |/  / _\ |
#     \__/| \__/ \__ |\_ \__  |
#

# The name of the container that will be launched by Docker for running the app
# This is usually the same as the name of the app
CONTAINER_NAME = basic-template

help:
	@echo "Please use 'make <target>' where <target> is one of"
	@echo "  drebuild                           rebuilds the image from scratch without using any cached layers"
	@echo "  drun                               run the built docker image and starts a bash"
	@echo "  dbash                              starts bash inside a running container."

dbuild:
	@echo "Building docker image..."
	docker-compose build app

drebuild:
	@echo "Rebuilding docker image..."
	docker-compose rm --force app
	make dbuild

drun:
	make dstop
	make dbuild
	docker-compose run --name ${CONTAINER_NAME} --service-ports --rm app

dbash:
	docker exec -it $(CONTAINER_NAME) /bin/sh

dstop:
	docker-compose stop
