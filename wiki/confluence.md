# confluence code indent 

1. wiki code marco
    1. insert wiki marco
    2. add : {code}...{code}

2. wiki bq. marco
    1. insert wiki marco
    2. add \: bq. ...

            bq.{
            bq.    "vendor": "Dell",
            bq.    "addresses": [
            bq.        {"ip": "xxx.xxx.xxx.xxx", "dev": "eth0"},
            bq.        {"ip": "xxx.xxx.xxx.xxx", "dev": "eth1"},
            bq.        ...
            bq.    ],
            bq.    "mem": 12001,
            bq.    "cpus": {
            bq.        "count": 2,
            bq.        "cores": 12,
            bq.        "hyper-threading": false,
            bq.        "frequency": 2394,
            bq.        "model": "Intel(R) Xeon(R) CPU E5645 @ 2.40GHz"
            bq.    },
            bq.    "raid": {
            bq.        "policy": {
            bq.            "read": "ReadAheadNone",
            bq.            "write": "WriteBack"
            bq.        },
            bq.        "type": "raid0"
            bq.    },
            bq.    "model": "PowerEdge R610",
            bq.    "disk": {
            bq.        "sas": {
            bq.            "count": 2,
            bq.            "volume": 136
            bq.        }
            bq.    },
            bq.    "cmdb": "D11113147"
            bq.}
