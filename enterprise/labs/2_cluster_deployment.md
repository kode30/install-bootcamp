*[root@edge journal]# curl -u kode30:cloudera 'http://ec2-35-180-198-7.eu-west-3.compute.amazonaws.com:7180/api/v2/cm/deployment'
```
{
  "timestamp" : "2019-02-13T11:34:52.172Z",
  "clusters" : [ {
    "name" : "Kode30",
    "version" : "CDH5",
    "services" : [ {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "771751936"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-64a3d74aa3c2c216c8b4c40d1deeaf04",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "8394072a-1197-4a6a-976d-4999687fa88c"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2xb6tuswc1y1rj89nnfs50le1"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-72b18a28eefd4ecb2c473925343a0804",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "4f82d40c-6c91-4ebf-8cf6-11acbfd18098"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6zn8imj83v4h5ou411a8xody4"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-b0911dadf3f58bc819b877bc6629e666",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_health_suppression_zookeeper_server_data_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_zookeeper_server_data_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_zookeeper_server_heap_dump_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_zookeeper_server_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_jceks_password",
            "value" : "19je43zufgjj0ux93l6359333"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "edge.cloudera.es"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "771751936"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-b0911dadf3f58bc819b877bc6629e666",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_health_suppression_oozie_server_heap_dump_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_oozie_server_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_jceks_password",
            "value" : "54qpxbvp5pf72zgt6e4mi2ih3"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "edge.cloudera.es"
        }, {
          "name" : "database_password",
          "value" : "hue"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-HTTPFS-64a3d74aa3c2c216c8b4c40d1deeaf04"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_LOAD_BALANCER-b0911dadf3f58bc819b877bc6629e666",
        "type" : "HUE_LOAD_BALANCER",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_health_suppression_hue_load_balancer_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_jceks_password",
            "value" : "apyrtg6qvqhtgaqbp5amtacgw"
          } ]
        }
      }, {
        "name" : "hue-HUE_SERVER-b0911dadf3f58bc819b877bc6629e666",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ {
            "name" : "navmetadataserver_cmdb_password",
            "value" : "a4c53c59-17a9-4b5e-bc80-c2d725d060ad"
          }, {
            "name" : "role_health_suppression_hue_server_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_jceks_password",
            "value" : "aszemyjlxq3xapzn8ej055umx"
          }, {
            "name" : "secret_key",
            "value" : "BUlgQfyYIIO9XjEgw4wqi4gUPTXIyB"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "771751936"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn,/clouderadata/dfs/dn,/clouderadata/dfs/dn2"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "2683094220"
          }, {
            "name" : "dfs_datanode_failed_volumes_tolerated",
            "value" : "2"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "400"
          }, {
            "name" : "rm_io_weight",
            "value" : "200"
          }, {
            "name" : "role_config_suppression_datanode_failed_volumes_validator",
            "value" : "true"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/clouderadata/journal"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn,/clouderadata/dfs/nn,/clouderadata/dfs/nn2"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "fs_trash_checkpoint_interval",
            "value" : "3"
          }, {
            "name" : "fs_trash_interval",
            "value" : "5"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "7GfVvDmNT4FtUIc3drdZIEBKrRap8n"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "30rcd8M81EnLhrYEzUDfyLijtQIIXn"
        }, {
          "name" : "hdfs_under_replicated_blocks_thresholds",
          "value" : "{\"warning\":10,\"critical\":60}"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "Wh6yfxAtRjGGn53d1zuyajDCY6hyiY"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "20"
        }, {
          "name" : "service_health_suppression_hdfs_canary_health",
          "value" : "true"
        }, {
          "name" : "service_health_suppression_hdfs_under_replicated_blocks",
          "value" : "true"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-b0911dadf3f58bc819b877bc6629e666",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-1010bd69e07747d76979cf8d9a25ea58",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "a9fe277a-c345-497a-a6bd-4d6a18d47fdf"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dc2i9i76ha9hwmnqx4yl0g8bb"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-b0911dadf3f58bc819b877bc6629e666",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_health_suppression_data_node_heap_dump_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_data_node_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_datanode_data_directories_free_space",
            "value" : "true"
          }, {
            "name" : "role_jceks_password",
            "value" : "eupckiod5xhbqxpm8mnwfho9x"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-b9b8e56d51acd257a48580421edb0d6b",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "b3e182ae-e3f7-4777-9cba-ba8c72a2e37c"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "84hu3ft32gp7c6ixdhox6z16z"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-64a3d74aa3c2c216c8b4c40d1deeaf04",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "8394072a-1197-4a6a-976d-4999687fa88c"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4rgba4k9ahzvtj39xz99s5y2y"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-72b18a28eefd4ecb2c473925343a0804",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "4f82d40c-6c91-4ebf-8cf6-11acbfd18098"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3dwg4z6vnut2h0nwjg2wdn5s5"
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-64a3d74aa3c2c216c8b4c40d1deeaf04",
        "type" : "HTTPFS",
        "hostRef" : {
          "hostId" : "8394072a-1197-4a6a-976d-4999687fa88c"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3re07lvaz0t278861u9p2jnx1"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-64a3d74aa3c2c216c8b4c40d1deeaf04",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "8394072a-1197-4a6a-976d-4999687fa88c"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1pf1mfuurqug3p3tobkelj2m9"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-72b18a28eefd4ecb2c473925343a0804",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "4f82d40c-6c91-4ebf-8cf6-11acbfd18098"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8v0wv04ps6vt1brqed7vq2qu6"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-b0911dadf3f58bc819b877bc6629e666",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_health_suppression_journal_node_edits_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_journal_node_heap_dump_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_journal_node_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_jceks_password",
            "value" : "fyvj464n1zqb9q9w5k7wstlf"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-64a3d74aa3c2c216c8b4c40d1deeaf04",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "8394072a-1197-4a6a-976d-4999687fa88c"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "59"
          }, {
            "name" : "role_jceks_password",
            "value" : "a729p233xp222nd3q9g1m9eqy"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-72b18a28eefd4ecb2c473925343a0804",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "4f82d40c-6c91-4ebf-8cf6-11acbfd18098"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "40"
          }, {
            "name" : "role_jceks_password",
            "value" : "9nryfdhqfk3ljd1n8yj8latr7"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "4"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "2"
          }, {
            "name" : "role_config_suppression_mapreduce_replication_validator",
            "value" : "true"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1600"
          }, {
            "name" : "rm_io_weight",
            "value" : "800"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm,/clouderadata/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs,/clouderadata/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "5579"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "5579"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "80"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "F2fo2C5dYOQcbAGI39omurOsXxRu1d"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-72b18a28eefd4ecb2c473925343a0804",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "4f82d40c-6c91-4ebf-8cf6-11acbfd18098"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dde646xpbx7gjpyp75do96k4m"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-1010bd69e07747d76979cf8d9a25ea58",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "a9fe277a-c345-497a-a6bd-4d6a18d47fdf"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dkyi9po1su8l8hce7vx67w5il"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-b9b8e56d51acd257a48580421edb0d6b",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "b3e182ae-e3f7-4777-9cba-ba8c72a2e37c"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "d41633wg47pkp1ok4naov6ext"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-72b18a28eefd4ecb2c473925343a0804",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "4f82d40c-6c91-4ebf-8cf6-11acbfd18098"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "45"
          }, {
            "name" : "role_jceks_password",
            "value" : "38xzd713mh2dkjcg0h9fl6kzg"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "771751936"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "771751936"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "4972504678"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "836"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "edge.cloudera.es"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-b0911dadf3f58bc819b877bc6629e666",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-b0911dadf3f58bc819b877bc6629e666",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_health_suppression_hivemetastore_heap_dump_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_hivemetastore_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_jceks_password",
            "value" : "cvho15xt229pyx9tfd4jcinh3"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-b0911dadf3f58bc819b877bc6629e666",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_health_suppression_hiveserver2_heap_dump_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_health_suppression_hiveserver2_log_directory_free_space",
            "value" : "true"
          }, {
            "name" : "role_jceks_password",
            "value" : "akyubxeh26u0yxj14h40n2bh0"
          } ]
        }
      } ],
      "displayName" : "Hive"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a",
    "ipAddress" : "172.31.34.49",
    "hostname" : "edge.cloudera.es",
    "rackId" : "/default",
    "config" : {
      "items" : [ {
        "name" : "host_config_suppression_memory_overcommitted_validator",
        "value" : "true"
      }, {
        "name" : "host_health_suppression_host_agent_parcel_directory_free_space",
        "value" : "true"
      } ]
    }
  }, {
    "hostId" : "4f82d40c-6c91-4ebf-8cf6-11acbfd18098",
    "ipAddress" : "172.31.43.192",
    "hostname" : "master1.cloudera.es",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "8394072a-1197-4a6a-976d-4999687fa88c",
    "ipAddress" : "172.31.36.36",
    "hostname" : "master2.cloudera.es",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "a9fe277a-c345-497a-a6bd-4d6a18d47fdf",
    "ipAddress" : "172.31.38.139",
    "hostname" : "worker1.cloudera.es",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "b3e182ae-e3f7-4777-9cba-ba8c72a2e37c",
    "ipAddress" : "172.31.36.148",
    "hostname" : "worker2.cloudera.es",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__hue-HUE_SERVER-b0911dadf3f58bc819b877bc6629e666",
    "roles" : [ "ROLE_NAVIGATOR_ADMIN" ],
    "pwHash" : "16f6cc043f8e1f0a4157eacd25b664397dc906df47874646eb6dcc150d50e073",
    "pwSalt" : 6322234924418552053,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-ACTIVITYMONITOR-b0911dadf3f58bc819b877bc6629e666",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "cb5538372ddc4c56fdb94a7b6c2ca82749534476989f5e27896c3bd2509bf6a7",
    "pwSalt" : 777393658639982940,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-b0911dadf3f58bc819b877bc6629e666",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "0b6715f6d79f628e331bd3e8d691b386a63580ba8f24805a92fab866de05769e",
    "pwSalt" : 2648642678281475341,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-b0911dadf3f58bc819b877bc6629e666",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "9a39d91d8addbdb84018d75f9d862b857f33a315b959e68e5a683969bc3fbd05",
    "pwSalt" : -2866796612188293512,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-b0911dadf3f58bc819b877bc6629e666",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "9b7afc527aef36890f2a9621c444fe1fe8729f6645bf29a7d90e52b15160dd63",
    "pwSalt" : 5886332085064812657,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-b0911dadf3f58bc819b877bc6629e666",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "ce0e556e419d0c6127dca626392a564dfa83cdcf7a436eef7e371fa6a00a5253",
    "pwSalt" : -670964977054870640,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "0a9a5d0422d0f26fb6d41ece70ae6a7c3dd02dc25191a166ee0395134ac3e466",
    "pwSalt" : -5583793552816656715,
    "pwLogin" : true
  }, {
    "name" : "kode30",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "6cb280829de9cda381f59cbea971300dbac74f430a068d4c4fc546a0e6ae1528",
    "pwSalt" : 1321468407941524165,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "6db9b73312914263597a321dfd9b67553334266376ee203eda67c387042c172e",
    "pwSalt" : 8095248721658462484,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.16.1",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20181120-1809",
    "gitHash" : "6a13b87a6fcdf4afad6d4474a68a9434b24d6c67",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "ACTIVITYMONITOR",
        "items" : [ {
          "name" : "firehose_database_host",
          "value" : "edge.cloudera.es"
        }, {
          "name" : "firehose_database_name",
          "value" : "amon"
        }, {
          "name" : "firehose_database_password",
          "value" : "amon"
        }, {
          "name" : "firehose_database_user",
          "value" : "amon"
        }, {
          "name" : "firehose_heapsize",
          "value" : "771751936"
        }, {
          "name" : "role_health_suppression_activity_monitor_heap_dump_directory_free_space",
          "value" : "true"
        } ]
      }, {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "771751936"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "771751936"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1003487232"
        }, {
          "name" : "role_config_suppression_firehose_host_monitor_heap_role_validator",
          "value" : "true"
        }, {
          "name" : "role_config_suppression_firehose_host_monitor_non_java_memory_role_validator",
          "value" : "true"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "edge.cloudera.es"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "771751936"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "771751936"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1003487232"
        }, {
          "name" : "role_config_suppression_firehose_service_monitor_heap_role_validator",
          "value" : "true"
        }, {
          "name" : "role_config_suppression_firehose_service_monitor_non_java_memory_role_validator",
          "value" : "true"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-b0911dadf3f58bc819b877bc6629e666",
      "type" : "ACTIVITYMONITOR",
      "hostRef" : {
        "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_health_suppression_activity_monitor_log_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_jceks_password",
          "value" : "8ac4egqzf8e1keuaujqswagfq"
        } ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-b0911dadf3f58bc819b877bc6629e666",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_health_suppression_alert_publisher_heap_dump_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_alert_publisher_log_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_jceks_password",
          "value" : "bg3hd28ow91jsm7hg64bt0vvm"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-b0911dadf3f58bc819b877bc6629e666",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_health_suppression_event_server_heap_dump_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_event_server_index_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_event_server_log_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_jceks_password",
          "value" : "4f47i0yjlgunsoyr2pdyg4psd"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-b0911dadf3f58bc819b877bc6629e666",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_health_suppression_host_monitor_heap_dump_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_host_monitor_log_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_host_monitor_storage_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_jceks_password",
          "value" : "584mwfenmb094e0m4x876tt2e"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-b0911dadf3f58bc819b877bc6629e666",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_health_suppression_reports_manager_heap_dump_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_reports_manager_log_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_reports_manager_scratch_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_jceks_password",
          "value" : "7hrab4gz3fr64ij1z5hse9kr2"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-b0911dadf3f58bc819b877bc6629e666",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "0acc3f1a-69b3-49be-99c3-02e3508c288a"
      },
      "config" : {
        "items" : [ {
          "name" : "role_health_suppression_service_monitor_heap_dump_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_service_monitor_log_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_health_suppression_service_monitor_storage_directory_free_space",
          "value" : "true"
        }, {
          "name" : "role_jceks_password",
          "value" : "9ce4iugys0y73f7pwvapnm82p"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/26/2012 17:30"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,http://archive.cloudera.com/kudu/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/,http://edge.cloudera.es/cdh/5/rpms"
    } ]
  }
 ```
