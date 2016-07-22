# Datomic DynamoDB Local
This repository starts datomic pro starter setup with DynamoDB local storage.

## Usage
1. Add your user credentials to the `./datomic/.credentials` in the format `user@email.com:password` from your [Datomic](http://www.datomic.com/get-datomic.html) account.

2. Add your license key to the `./datomic/config/ddb-local-transactor.properties` from your [Datomic](http://www.datomic.com/get-datomic.html) account.

3. `docker-compose up` to start the containers, you should then see an error mentioning the table does not exist.

4. Whilst the containers are running run `docker-compose run --entrypoint="./bin/datomic" datomic "ensure-transactor ./config/ddb-local-transactor.properties ./config/ddb-local-transactor.properties"`

5. You should see a JSON response saying success.

6. `docker-compose down && docker-compose up` your running containers.

That's it you should have Datomic running with DynamoDB local storage.

### REST API

Whilst Datomic is running you can start up the REST API by running the following command:

`docker-compose run --entrypoint="./bin/rest" datomic -p 8001 ddb-local datomic:ddb-local://dynamodb:8000/example/`

Then visit `http://localhost:8001/` to explore the REST API.

