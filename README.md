# FSE_2025
To create a docker image, corresponding to a lecture `01_local_unix`,`02_local_unix`,`03_remote_unix` run the
following command in your terminal:
Pull image

```sh
docker pull ghcr.io/skolai/fse4ai_2025_01_local_unix:25.09.3        
```

```sh
docker pull ghcr.io/skolai/fse4ai_2025_02_local_unix:26.09.02
```

```sh
docker pull ghcr.io/skolai/fse4ai_2025/remote_unix-server:26.09.01
```

Run image
```sh
docker run --rm -it ghcr.io/skolai/fse4ai_2025_01_local_unix:25.09.3
```

```sh
docker run --rm -it ghcr.io/skolai/fse4ai_2025_02_local_unix:26.09.02
```

```sh
docker run --rm -it ghcr.io/skolai/fse4ai_2025/remote_unix-client:26.09.01
```

