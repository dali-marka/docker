# IRSSI in Docker

## How to use

```bash
docker run --rm -it chadrien/irssi:arm
```

If you'd like to use you own irssi configuration, there is a volume for
this purpose :

```bash
docker run --rm -it -v /path/to/your/config:/home/irssi/.irssi chadrien/irssi:arm
```
