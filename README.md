# indocker

`indocker` is a shell wrapper that makes running commands in docker containers
seamless. It does this by automatically building a docker image for you from a
`Dockerfile` in the current directory, and then executing the command of your
choice (or a shell by default) using that docker image, as your user, with your
current working directory mounted.

## Examples

```
 home ⮁ kyle ⮀ $ ⮀ls
Desktop  Dockerfile  Documents  Music  Pictures  Public  Templates  Videos
 home ⮁ kyle ⮀ $ ⮀whoami
kyle
 home ⮁ kyle ⮀ $ ⮀indocker
Sending build context to Docker daemon 216.2 MB
Step 1 : FROM alpine
 ---> d285ca5058c6
Step 2 : RUN apk update && apk add sudo
 ---> Using cache
 ---> 28e3252b4b9f
Successfully built 28e3252b4b9f
/indocker $ ls
Desktop     Dockerfile  Documents   Music       Pictures    Public      Templates   Videos
/indocker $ whoami
kyle
/indocker $
```

## Tenants / Features

* Users don't need to remember to build anything, whatever `Dockerfile` you have will work (images are built ondemand)
* Code always runs as themselves, the same user outside Docker and inside Docker
* Files in your directory are the same files in the directory inside Docker (`$pwd` is volume mounted as rw)

## License

See `LICENSE`
