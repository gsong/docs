# License and License Keys

Each `Cluster` resource has a `licenseKey` parameter in its definition.

A `licenseKey` is always required for the operator to work.

The only exception is when you run the operator with Community PostgreSQL:
in this case, if the `licenseKey` parameter is unset, a cluster will be
started with the default trial license - which automatically expires after 30 days.

!!! Important
    After the license expiration, the operator will cease any reconciliation attempt
    on the cluster, effectively stopping to manage its status.
    The pods and the data will still be available.

You can find the expiration date, as well as more information about the license,
in the cluster status:

```sh
kubectl get cluster cluster_example -o yaml
[...]
status:
  [...]
  licenseStatus:
    licenseExpiration: "2021-11-06T09:36:02Z"
    licenseStatus: Trial
    valid: true
[...]
```

A cluster license key can be updated with a new one at any moment, to extend
the expiration date or move the cluster to a production license.

Cloud Native PostgreSQL is distributed under the EnterpriseDB Limited Usage License
Agreement, available at [enterprisedb.com/limited-use-license](https://www.enterprisedb.com/limited-use-license).

Cloud Native PostgreSQL: Copyright (C) 2019-2020 EnterpriseDB.
