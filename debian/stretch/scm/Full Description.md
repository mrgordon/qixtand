# Tags and respective Dockerfile links

- [`qixtand/debian-stretch-scm` (*debian/stretch/scm/Dockerfile*)](https://github.com/qixtand/qixtand/blob/master/debian/stretch/scm/Dockerfile)

# Quick reference
-	**Where to file issues**:
	[https://github.com/qixtand/qixtand/issues](https://github.com/qixtand/qixtand/issues)

-	**Maintained by**:
	[Jesse Washburn](https://github.com/qixtand/qixtand)

-	**Supported Docker versions**:
	[the latest release](https://github.com/docker/docker-ce/releases/latest) (down to 1.6 on a best-effort basis)

# How to use this image

## Create a `Dockerfile` in your project directory

```dockerfile
FROM qixtand/debian-stretch-scm
CMD ["./your-daemon-or-script.sh"]
```

Put this file in the root of your project.

You can then build and run the image:

```console
$ docker build -t my-app .
$ docker run -it --name my-running-script my-app
```
