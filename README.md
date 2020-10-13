# Configuration

## To run the project.

- Install the dependencys:
`yarn`

You need to be running 3 databases
- 1- Postgres - name: "gostack_gobarber"
- 2- MongoDB - name: "mongodb"
- 3- Redis - nam: "redis"

## You can create these databases with the terminal commands, using docker:
- `docker run --name gostack_gobarber -e POSTGRES_PASWORD=docker -p 5432:5432 -d postgres`
- `docker run --name mongodb -p 27017:27017 -d -t mongo`
- `docker run --name redis -p 6379:6379 -d -t redis:alpine`

Create the tables on database:
`yarn typeorm migration:run`

create the files `.env` and `.ormconfig`, the ormconfig file you need to create if the project is in development, in production you not need create this file.

- Now you need to configure Amazon S3 service IAM, and create an user:
- Users > Add User > Set Permissions - Attach existing policies directly - AmazonS3FullAcess(This service is not the best, for production, the user would have full access, we can manually configure permissions, for development, we will use this) > continue until the user is created.

- It will generate Acces key ID and Secret key, we put this information into our `.env`.

- Now go to the services tab, search for s3 and create a new bucket

run `yarn dev:server`

The project will probably run.
