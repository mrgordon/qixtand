# Tags and respective Dockerfile links

- [`qixtand/debian-wheezy-buildpack` (*debian/wheezy/buildpack/Dockerfile*)](https://github.com/qixtand/qixtand/blob/c8793c368bc96e8745e9ac03c527d1b9675fc1dd/debian/wheezy/buildpack/Dockerfile)

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
FROM qixtand/debian-wheezy-buildpack
CMD ["./your-daemon-or-script.sh"]
```

Put this file in the root of your project.

You can then build and run the image:

```console
$ docker build -t my-app .
$ docker run -it --name my-running-script my-app
```
