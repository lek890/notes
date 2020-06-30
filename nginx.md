### nginx get part after url

```
location ~* ^/api/(.+)$ {
      proxy_pass      http://192.168.0.108:8080/$1;
    }
```

## proxy pass rest of a url path

```
location ~* ^/api/(.+)$ {
   proxy_pass      http://192.168.0.108:8080/$1;
}
```

proxy pass rest of a url path (inlcuding get args)

```
location ~* ^/service/(.*) {
  proxy_pass http://apache/$1$is_args$args;
}
```
