# docker-basics

For each line in Dockerfile, new container with process is created - use `&&` instead of `newline` as much as possible

```
//good
RUN apk add --no-cache make gcc g++ python && \
  npm install --production --silent && \
  apk del make gcc g++ python
  
//bad
RUN apk add --no-cache make gcc g++ python
RUN npm install --production --silent
RUN apk del make gcc g++ python
```

