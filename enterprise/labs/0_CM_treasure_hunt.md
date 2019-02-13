

    1) What is ubertask optimization? 
    R- Ubertasks optimization runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the  mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings.
    
    2) Where in CM is the Kerberos Security Realm value displayed? 
    R- The Kerberos Security Realm value is displayed here: Administration -> Settings -> Kerberos -> Kerberos Security Realm
    
    3) Which CDH service(s) host a property for enabling Kerberos authentication?

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

    4) How do you upgrade the CM agents? 
    R- You need first to upgrade the cloudera manager Server. Once the CM server is upgrade and restarted a wizard pops up to upgrade the cloudera manager agents and optionally the JDK

    5) Give the tsquery statement used to chart Hue's CPU utilization? 
    R- SELECT cpu_system_rate, cpu_user_rate where serviceName='hue'

    6) Name all the roles that make up the Hive service
    R-
    Hive Server2
    Hive Metastore Server
    WebHcat Server
    Hive Gateway (just configuration flies for the clients, no active role)

    7) What steps must be completed before integrating Cloudera Manager with Kerberos?
   
    R-  (**AL STEP ARE: https://kylo.readthedocs.io/en/v0.8.2/installation/KerberosInstallationExample-Cloudera.html)
    
        a) Install openldap-clients on the Cloudera Manager Server host. (https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/openldap)
        
        b) Install krb5-workstation krb5-libs on ALL hosts (yum install krb5-workstation krb5-libs)
        c) Install MIT KDC or use the Active Directory KDC
        d) Create Kerberos Principal for the Cloudera Manager Server
        e) Configure the KDC to allow renewable tickets with non-zero ticket lifetimes. Active Directory KDC allows it by default
        f) Start the Wizard for Kerberos Integration

