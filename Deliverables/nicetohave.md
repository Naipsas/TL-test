# Nice to have

This file has the following sections:

1. HTTPS route
2. phpunit tests inside a container
3. xdebug inside the backend container

## HTTPS route

Nginx server is used for this objective. It could be used applying SSL to all conections, but since Nginx is supposed to be the only container accessible from outside, we've decided to secure all incoming connections and then proxy them using http to the final container.

CSR (public) and key (private) have been generated using `openssl req -new`, and `teamleader` has been both the `passphrase` when prompted about it. `challenging password` has been leaved empty because it would ask for an input when deploying or restarting the server, which would lead to less automation for the deployment.

`sudo openssl req -new > new.ssl.csr`

Then, certificate has been generated from this couple using:

```
openssl rsa -in privkey.pem -out new.cert.key
openssl x509 -in new.ssl.csr -out new.cert.cert -req -signkey new.cert.key -days 50
```

We can rename:

```
mv ./new.cert.cert ./server.crt
mv ./new.cert.key ./server.key
```

This files should be located in `Deliverables/Dockerfiles/backend/SSL/` folder. Files are NOT in the repository. Please, generate or provide your own `server.crt` and `server.key` to run this test.

Original HTTP connections have been redirected using HTTP 302, being 301 error avoided because it's stored permanently in browsers, so we want to avoid undesirable behaviours after trying this test.

## phpunit tests inside a container


## xdebug inside the backend container

