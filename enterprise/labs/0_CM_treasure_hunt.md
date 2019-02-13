

    What is ubertask optimization? Ubertasks optimization runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings.
    Where in CM is the Kerberos Security Realm value displayed? The Kerberos Security Realm value is displayed here: Administration -> Settings -> Kerberos -> Kerberos Security Realm
    Which CDH service(s) host a property for enabling Kerberos authentication?

    Flume
    HBase
    HCatalog
    Hive
    HttpFS
    Hue
    Impala
    Llama
    Oozie
    Solr
    Spark
    Sqoop
    ZooKeeper

    How do you upgrade the CM agents? You need first to upgrade the cloudera manager Server. Once the CM server is upgrade and restarted a wizard pops up to upgrade the cloudera manager agents and optionally the JDK

    Give the tsquery statement used to chart Hue's CPU utilization? SELECT cpu_system_rate, cpu_user_rate where serviceName='hue'

    Name all the roles that make up the Hive service

    Hive Server2
    Hive Metastore Server
    WebHcat Server
    Hive Gateway (just configuration flies for the clients, no active role)

    What steps must be completed before integrating Cloudera Manager with Kerberos?

    Install openldap-clients on the Cloudera Manager Server host. Install krb5-workstation krb5-libs on ALL hosts
    Install MIT KDC or use the Active Directory KDC
    Create Kerberos Principal for the Cloudera Manager Server
    Configure the KDC to allow renewable tickets with non-zero ticket lifetimes. Active Directory KDC allows it by default
    Start the Wizard for Kerberos Integration

