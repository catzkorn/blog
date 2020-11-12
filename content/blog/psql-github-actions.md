---
title: "How to setup Postgres with Github Actions"
date: 2020-11-12
slug: "postgres-github-actions"
description: "Migrations and Postgres Services"
keywords: ["coding", "github", "go", "postgres", "ci" "github actions"]
draft: false
tags: ["code"]
math: false
toc: true #table of contents on the right
---


I was recent having a problem with TravisCI taking ages to run so I spent some time moving a project over to GitHub Actions.

It has slightly different syntax to the setup in `.travis.yml`, and I struggled to get my pre-test migrations script running.

While the [creating postgresql service containers](https://docs.github.com/en/free-pro-team@latest/actions/guides/creating-postgresql-service-containers) documentation details how to start the postgres service, there was little information online about how to run migrations, and most of the documented solutions didn't work at all. So here's how I got it to work (finally).

This example is for Go code, and so my Github Actions setup is in go.yml.


## Postgresql Service Container Set-up

As per the Github Documentation, the first step is to set up the postgresql service:

```yml
# go.yml

# Service containers to run with `container-job`
services:
  # Label used to access the service container
  postgres:
    # Docker Hub image
    image: postgres
    # Provide the password for postgres
    env:
      POSTGRES_PASSWORD: postgres
    # Set health checks to wait until postgres has started
    options: >-
      --health-cmd pg_isready
      --health-interval 10s
      --health-timeout 5s
      --health-retries 5
    ports:
      # Maps tcp port 5432 on service container to the host
      - 5432:5432
```

One important detail here is to set the port mapping between the service and the local container. The documentation talks about using the name of the service as a hostname to connect to, but I couldn't get that to work in any of my testing. The only thing that finally worked was using the port mapping seen above.

## Running Migration Files

Running migration files happens under the `steps:` header. Declare a new step using `-name: your choice of name` and then `run:`.


```yml
# go.yml

steps:
- name: Run migrations
  run: psql -f db/migrations/file_name.sql postgresql://postgres:postgres@localhost:5432/postgres
```
You will want to change `db/migrations/file_name.sql` to your own file path and name. Note that the URL uses "localhost" as the host, since we used the port mapping above.


## DSN & Environmental Variables

The DSN (data source name) for the database is `"user=postgres  host=localhost password=postgres port=5432 database=postgres sslmode=disable"`

If you are storing your DSN as an ENV variable and passing it in within your code, you'll want to grab it under the `-name: Test` step using `env:` and `ENV_NAME:`, for example, if your environment variable was `DATABASE_DSN`:


```yml
# go.yml

- name: Test
      run: go test -v .
      env: 
        DATABASE_DSN: "user=postgres host=localhost password=postgres port=5432 database=postgres sslmode=disable"
```

Make sure to quote the value if you have spaces in it!



## go.yml 

For context, my entire go.yml file looks like:

```yml
# go.yml

name: Go

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:

  build:
    name: Build
    runs-on: ubuntu-latest

    # Service containers to run with `container-job`
    services:
      # Label used to access the service container
      postgres:
        # Docker Hub image
        image: postgres
        # Provide the password for postgres
        env:
          POSTGRES_PASSWORD: postgres
        # Set health checks to wait until postgres has started
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
        ports:
          # Maps tcp port 5432 on service container to the host
          - 5432:5432

    steps:
    - name: Set up Go 1.x
      uses: actions/setup-go@v2
      with:
        go-version: ^1.13

    - name: Check out code into the Go module directory
      uses: actions/checkout@v2

    - name: Get dependencies
      run: |
        go get -v -t -d ./...
        if [ -f Gopkg.toml ]; then
            curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh
            dep ensure
        fi

    - name: Run migrations
      run: psql -f db/migrations/file_name.sql postgresql://postgres:postgres@localhost:5432/postgres

    - name: Build
      run: go build -v .

    - name: Test
      run: go test -v .
      env: 
        DATABASE_DSN: "user=postgres host=localhost password=postgres port=5432 database=postgres sslmode=disable"
```

It is based on the default Go Github Action workflow.

Hopes this helped if you were stuck like I was! 