These are ai generated examples , just to help see what it would look like, incase its very new to anyone.
below each a link to fastify.dev/related-context to help further understanding.

### schema
```javascript
const fastify = require('fastify')()

fastify.post('/register', {
  schema: {
    body: {
      type: 'object',
      required: ['username', 'age'],
      properties: {
        username: { type: 'string' },
        age: { type: 'integer', minimum: 13 }
      }
    }
  }
}, async (request, reply) => {
  // If validation passes, this runs
  reply.send({ status: 'ok' })
})
```

If someone sends: 
```javascript
{ "username": "santi", "age": 12 }

```
Fastify rejects it with a 400 error because age is below the minimum.
You don’t need to write if (age < 13) the schema does it for you.

link [more on schemas in fastify:](https://fastify.dev/docs/latest/Reference/Validation-and-Serialization/)

### error handling example

```javascript
fastify.setErrorHandler((error, request, reply) => {
  reply.status(500).send({ error: 'Something went wrong!' })
})
```

even if the route throws 
```javascript
throw new Error('Database failed')

```

link [more on errors in fastify:](https://fastify.dev/docs/latest/Reference/Errors/)

### lifecycle hooks example

```javascript
fastify.addHook('preHandler', async (request, reply) => {
  if (!request.headers['x-auth']) {
    reply.code(401).send({ error: 'Unauthorized' })
  }
})

```
This runs before your route logic and blocks unauthorized requests.

link [more on lifecycles in fastify:](https://fastify.dev/docs/latest/Reference/Lifecycle/)
