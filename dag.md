##### Pipeline Flow


```
                                     fetch
                                       |
                                       v
                                 bson-transform-task
                                 |            |
                                 |            |
                                 v          fill-if-not-exist-field-task(when)
                      thrift-transform        |
                                 |            v
                                 v           store-db2
                             store-db1        |
                                 |            v
                                 v           read
                                read
```
