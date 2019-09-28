# Small API App Using Express, Typescript and Nest.js Secured by Auth0 :banana:

Basic API app utilizing Nest.js to bring us Typescript to an Express server. Able to pull and post.

## Getting Started :memo:

### Prerequisites

You should have installed:

- [Node.js](https://nodejs.org/)

### Installing

Once Node.js is installed, install these packages:

```

npm i @nestjs/common @nestjs/core @nestjs/microservices @nestjs/websockets rxjs typescript reflect-metadata body-parser express-jwt jwks-rsa @types/express-jwt
npm i -D @types/node ts-node
```

Finally clone the repository and your all set.

## Demo :rocket:

To demo the app, run your server:
```
node index
```

It should be running on localhost:3000.

To fetch an `access_token` from Auth0, first we need to set three variables: `CLIENT_ID`, `CLIENT_SECRET`, `AUTH0_DOMAIN`.
These variables have to be copied from our *Client* on Auth0's management dashboard.

After that, we can submit a request to Auth0's endpoint to get an `access_token`:
```bash
JWT=$(curl -X POST -H 'content-type: application/json' -d '{
    "client_id": "'$CLIENT_ID'",
    "client_secret": "'$CLIENT_SECRET'",
    "audience": "http://localhost:3000/",
    "grant_type": "client_credentials"
}' https://$AUTH0_DOMAIN/oauth/token  | jq '.access_token')
```

With this token, we can issue requests to secured endpoints:

```bash
# issuing GET request to fetch companies
curl -H 'authorization: Bearer '$JWT http://localhost:3000/companies
```

## Built With :hammer:

- [Visual Studio Code](https://code.visualstudio.com/) - code editor

## Acknowledgments :clap:

- [Nest.js Brings TypeScript to Node.js and Express](https://auth0.com/blog/nestjs-brings-typescript-to-nodejs-and-express/#Securing-Nest-js-Applications)