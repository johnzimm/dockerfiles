# base image
FROM pelias/baseimage

# downloader apt dependencies
# note: this is done in one command in order to keep down the size of intermediate containers
RUN apt-get update && apt-get install -y bzip2 && apt-get install -y unzip && rm -rf /var/lib/apt/lists/*

# clone repo
RUN git clone https://github.com/pelias/openstreetmap.git /code/pelias/openstreetmap

# change working dir
WORKDIR /code/pelias/openstreetmap

# consume the build variables
ARG REVISION=production

# switch to desired revision
RUN git checkout $REVISION

# install npm dependencies
RUN npm install

# run tests
RUN npm test
