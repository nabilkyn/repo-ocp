openshift-platform/
├── README.md
├── .gitignore
├── .yamllint.yaml
├── Makefile
│
├── components/
│   ├── cluster-configuration/
│   │   ├── oauth/
│   │   │   ├── base/
│   │   │   │   ├── oauth.yaml
│   │   │   │   └── kustomization.yaml
│   │   │   └── providers/
│   │   │       ├── ldap/
│   │   │       │   ├── patch-oauth.yaml
│   │   │       │   └── kustomization.yaml
│   │   │       └── oidc/
│   │   │           ├── patch-oauth.yaml
│   │   │           └── kustomization.yaml
│   │   │
│   │   ├── ingress/
│   │   │   ├── base/
│   │   │   │   ├── patch-ingresscontroller.yaml
│   │   │   │   └── kustomization.yaml
│   │   │   └── profiles/
│   │   │       ├── standard/
│   │   │       └── production/
│   │   │
│   │   ├── image-registry/
│   │   │   ├── base/
│   │   │   │   ├── patch-config.yaml
│   │   │   │   └── kustomization.yaml
│   │   │   └── storage/
│   │   │       ├── odf-rwx/
│   │   │       └── external-object-storage/
│   │   │
│   │   ├── chrony/
│   │   │   ├── base/
│   │   │   │   ├── machineconfig-chrony.yaml
│   │   │   │   └── kustomization.yaml
│   │   │   └── datacenters/
│   │   │       ├── primary/
│   │   │       │   ├── patch-ntp-servers.yaml
│   │   │       │   └── kustomization.yaml
│   │   │       └── secondary/
│   │   │           ├── patch-ntp-servers.yaml
│   │   │           └── kustomization.yaml
│   │   │
│   │   ├── monitoring/
│   │   │   ├── cluster-monitoring/
│   │   │   │   ├── base/
│   │   │   │   │   ├── cluster-monitoring-config.yaml
│   │   │   │   │   └── kustomization.yaml
│   │   │   │   └── profiles/
│   │   │   │       ├── nonproduction/
│   │   │   │       └── production/
│   │   │   ├── user-workload-monitoring/
│   │   │   │   ├── base/
│   │   │   │   └── profiles/
│   │   │   └── alertmanager/
│   │   │       ├── base/
│   │   │       └── receivers/
│   │   │
│   │   ├── proxy/
│   │   ├── trust-bundle/
│   │   ├── certificates/
│   │   ├── audit/
│   │   ├── scheduler/
│   │   ├── network/
│   │   └── node-configuration/
│   │
│   └── platform-services/
│       ├── odf/
│       │   ├── operator/
│       │   │   ├── base/
│       │   │   │   ├── namespace.yaml
│       │   │   │   ├── operatorgroup.yaml
│       │   │   │   ├── subscription.yaml
│       │   │   │   └── kustomization.yaml
│       │   │   └── versions/
│       │   │       └── 4.18/
│       │   │           ├── patch-subscription.yaml
│       │   │           └── kustomization.yaml
│       │   └── instance/
│       │       ├── base/
│       │       │   ├── storagecluster.yaml
│       │       │   └── kustomization.yaml
│       │       └── profiles/
│       │           ├── compact/
│       │           ├── standard/
│       │           └── production/
│       │
│       ├── logging/
│       │   ├── operator/
│       │   │   ├── base/
│       │   │   └── versions/
│       │   └── instance/
│       │       ├── base/
│       │       └── profiles/
│       │           ├── nonproduction/
│       │           └── production/
│       │
│       ├── loki/
│       │   ├── operator/
│       │   │   ├── base/
│       │   │   └── versions/
│       │   └── instance/
│       │       ├── base/
│       │       └── profiles/
│       │           ├── nonproduction/
│       │           └── production/
│       │
│       ├── compliance/
│       │   ├── operator/
│       │   │   ├── base/
│       │   │   └── versions/
│       │   └── instance/
│       │       ├── base/
│       │       └── profiles/
│       │           └── corporate/
│       │
│       ├── k10/
│       │   ├── operator/
│       │   │   ├── base/
│       │   │   └── versions/
│       │   └── instance/
│       │       ├── base/
│       │       └── profiles/
│       │           ├── primary-datacenter/
│       │           └── secondary-datacenter/
│       │
│       └── volsync/
│           ├── operator/
│           │   ├── base/
│           │   └── versions/
│           └── instance/
│               ├── base/
│               └── profiles/
│                   ├── source/
│                   └── destination/
│
├── groups/
│   ├── all/
│   │   └── kustomization.yaml
│   ├── nonproduction/
│   │   ├── monitoring/
│   │   ├── logging/
│   │   └── kustomization.yaml
│   ├── production/
│   │   ├── monitoring/
│   │   ├── logging/
│   │   ├── backup/
│   │   └── kustomization.yaml
│   ├── primary-datacenter/
│   │   ├── chrony/
│   │   ├── backup/
│   │   └── kustomization.yaml
│   └── secondary-datacenter/
│       ├── chrony/
│       ├── replication/
│       └── kustomization.yaml
│
├── clusters/
│   ├── cer01ocp01t/
│   │   ├── cluster-config/
│   │   │   ├── oauth/
│   │   │   ├── ingress/
│   │   │   ├── image-registry/
│   │   │   └── monitoring/
│   │   ├── platform-services/
│   │   │   ├── odf/
│   │   │   ├── logging/
│   │   │   ├── loki/
│   │   │   ├── compliance/
│   │   │   ├── k10/
│   │   │   └── volsync/
│   │   └── kustomization.yaml
│   │
│   ├── cer01ocp01x/
│   │   ├── cluster-config/
│   │   ├── platform-services/
│   │   └── kustomization.yaml
│   │
│   └── sft01ocp01x/
│       ├── cluster-config/
│       ├── platform-services/
│       └── kustomization.yaml
│
├── docs/
│   ├── architecture.md
│   ├── repository-model.md
│   ├── deployment-order.md
│   ├── cluster-matrix.md
│   ├── upgrade-procedure.md
│   └── rollback-procedure.md
│
└── scripts/
    ├── validate.sh
    ├── render.sh
    ├── diff.sh
    ├── deploy.sh
    └── verify.sh