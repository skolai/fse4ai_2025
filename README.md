# FSE_2025
Pull image
```sh
docker pull ghcr.io/skolai/fse4ai_2025_01_local_unix:25.09.3        
```
Run image
```sh
docker run --rm -it ghcr.io/skolai/fse4ai_2025_01_local_unix:25.09.3
```
To create a docker image, corresponding to a lecture `01\_Unix`, run the
following command in your terminal:
```sh
docker compose run --rm fse4ai_01
```
To run a container for a lecture `02\_Unix`, run the following command:
```sh
docker compose run --rm fse4ai_02
```