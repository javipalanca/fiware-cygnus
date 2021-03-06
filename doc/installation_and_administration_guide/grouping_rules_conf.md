#<a name="top"></a>Grouping Rules configuration
The file `grouping_rules.conf` can be instantiated from a template given in the Cygnus repository, `conf/grouping_rules.conf.template`. 

The rules are writting in Json format. The following Json code is just an example:

```
{
    "grouping_rules": [
        {
            "id": 1,
            "fields": [
                ...
            ],
            "regex": "...",
            "destination": "...",
            "fiware_service_path": "..."
        },
        ...
    ]
}
```

Being:

* <b>id</b>: A unique unsigned integer-based identifier. Not really used in the current implementation, but could be useful in the future.
* <b>fields</b>: These are the fields that will be concatenated for regular expression matching. The available dictionary of fields for concatenation is "entityId", "entityType" and "servicePath". The order of these fields is important since the concatenation is made from left to right.
* <b>regex</b>: Java-like regular expression to be applied on the concatenated fields. Special characters like '\' must be escaped ('\' is escaped as "\\\\").
* <b>destination</b>: Name of the HDFS file or CKAN resource where the data will be effectively persisted. In the case of MySQL, Mongo and STH this sufixes the table/collection name. Please, have a look to [doc/design/naming_conventions.md](doc/design/naming_conventions.md) for more details.
* <b>fiware\_service\_path</b>: New `fiware-servicePath` replacing the notified one. The sinks will translate this into the name of the HDFS folder or CKAN package where the above destination entity will be placed. In the case of MySQL, Mongo and STH this prefixes the table/collection name. Please, have a look to [doc/design/naming_conventions.md](doc/design/naming_conventions.md) for more details.
