1. Make sure you have nestjs client is installed 
    nest -v 

    if not installed use this command to install globally: 
        npm install -g @nestjs/cli

2. Create a project 'authApi' 

    nest new <project-name>

3. cd to auth-api 

4. Inside your NestJS project: Install Dependencies and the necessary Prisma packages and database drivers:

    % npm install prisma@7 @prisma/client@7 @prisma/adapter-pg@7 --save-dev

    4.a. approve all the packages installed: 
        npm install-scripts approve --all

5. Initialize prizma:
    npx prisma init --output ../src/generated/prisma

    [
        this will create all the prisma/schema.prisma
        and several other files inside src folder
    ]
6. Update the .env with the url path to your local postgresql server

7. Update src/prisma/schema.prisma with the model Product
    model Product {
        id          Int      @id @default(autoincrement())
        name        String
        price       Float
        description String?
        createdAt   DateTime @default(now())
        updatedAt   DateTime @updatedAt
    }

8. There are some options to synch the prisma schema with the database table. 
    assuming the postgreql is running in a docker container already. 

    1. If you want to pull your existing database table schema into your prisma/schema.prisma do this: 
        npx prisma db pull 

    2. Otherwise, to push your new schema to the postgresql server and create a table do this: 
        npx prisma db push 

    