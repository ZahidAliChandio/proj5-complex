Setup project

Create Dockerfile.dev inside client directory
cd client
docker build -f Dockerfile.dev .

Create Dockerfile.dev inside worker directory
cd server
Create Dockerfile.dev inside server directory
docker build -f Dockerfile.dev .
docker run aboveImageId (may get error for server)
cd worker
docker build -f Dockerfile.dev .
docker run aboveImageId

create a docker-compose file in the root direcotory
docker-compose up
create and write .travis.yml file inside root

setup default.conf file and we have to create Dockerfile to use default.conf in nginx

-> Pushing .travis.yml images to docker hub
-> For this we have to login to docker cli
- Add docker Username and Password as environmental var in your travis repo (by visiting your repo at travis site then goto inside repo settings).

# -- --coverage it ensures that test script eventually exits with status code either 0 or not zero it test failed.
  - docker run zahidchandio/react-test npm test -- --coverage
after_success:
  # Multiple containers
  - docker build -t zahidchandio/multi-client ./client
  - docker build -t zahidchandio/mutli-nginx ./nginx
  - docker build -t zahidchandio/multi-server ./server
  - docker build -t zahidchandio/multi-worker ./worker