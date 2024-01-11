# elasticsearch-reindex-remote

Skip the Remote elasticsearch SSL and Whitelist the Remote elasticsearch IP (Add below lines in destination elasticsearch config)
```
elasticsearch.yml: |
  reindex.ssl.verification_mode: none
  reindex.remote.whitelist: "<IP address>:9200"
```

Run the below command from destination elasticsearch Kibana Devtools section.

```
POST _reindex
{
  "source": {
    "remote": {
      "host": "https://<IP address>:9200",
      "username": "username",
      "password": "password"
    },
    "index": "test-index"
  },
  "dest": {
    "index": "test-index"
  }
}
```
