
Report of Issues raised in **JANUARY**
Issue1: Share the MariaDB creds for stage for nimbus
	ReportedBy: 
	AddressedBy: VISTARA
	Recommendation: Report via JIRAVISTA

Issue2: Getting Host '192.168.13.1' is blocked because of many connection errors for stage db (MAX CONNECTIONS)
	ReportedBy: [@sre-ins-oncall]
	AddressedBy: IssueTrackerBot
	Recommendation: 1. Click on **'Close Issue'** button, it should open a form. 2. Fill out required details and submit it. 3. Please provide one liner RCA as well.

Issue3: Generating sudo cert 
	ReportedBy: @sanju.rakonde
	AddressedBy: IssueTrackerBot
	Recommendation:  
	Tagged: [@prasad.kumarasamy] [@rahul.devale]

Issue4: Getting Aerospike Write Exception
	ReportedBy: SWE
	AddressedBy: VISTARA 
	Recommendation: Report via JIRAVISTA

Issue5: Unable to connect to ==stg-aerospikepp401.phonepe.nb6==
	ReportedBy: Dev 
	AddressedBy: VISTARA 
	Recommendation: Report via JIRAVISTA, to create new JIRA as cluster is already deprecated. 

```
Venkateshwar Reddy  [12:50 PM]  

@here We are seeing scale flux disk issue in this stg-clouddb573.phonepe.nb6 hence we are taking OOR.Following VM's will be effected.  
root@stg-clouddb573:/home/sre# virsh list --all  

 Id   Name                    State
----------------------------------------
 1    stg-hdptstore310        running
 2    stg-asconnect203        running
 4    stg-aerospikepymts003   running
 5    stg-rmqpymts102         running
 6    stg-aerospikepp664      running
 7    stg-azproxy001          running
 8    stg-sftp101             running
 -    stg-lvspp402            shut off


Venkateshwar Reddy  [2:05 PM]  

VMs are up scaleflux disk issue resolved
```


Issue5: drove stage - instance getting killed every 5 mins ==stg-droveexec039.phonepe.nb6, stg-droveexec058.phonepe.nb6==
	ReportedBy: Software Engineer, UPI Payments 
	AddressedBy: VISTARA 
	Recommendation: Report via JIRAVISTA, there was OOM

Issue6: Stage aerospike not able to acquire DLM lock
	ReportedBy: [@sregrowth-oncall](https://phonepetalk.slack.com/admin/user_groups) 
	AddressedBy: Faisal 
	Recommendation: cluster health looks fine. I can see read/write for offerengine namespace

Issue7: Nginx error stating resource not found for existing resource
	ReportedBy: [@api-oncall](https://phonepetalk.slack.com/admin/user_groups)
	AddressedBy: VISTARA
	Recommendation: [@Venkateshwar Reddy](https://phonepetalk.slack.com/team/U036X4MF3GT) it is due to expired  or missing auth token , retry with fresh token should work.
```
 Getting 400 error    

Request completely sent off
< HTTP/1.1 400 PR000
< x-requested-method: GET
< x-response-backend-time: 1767951356918
< x-request-backend-time: 1767951356918
< x-api-exception-code: PR000
< content-length: 45
<
* Connection #0 to host api.nixy.stg-drove.phonepe.nb6 left intact
{"errorCode":"PR000","message":"Bad Request"}%
```



Issue8: Stage aerospike not able to acquire DLM lock
	ReportedBy: [@sregrowth-oncall](https://phonepetalk.slack.com/admin/user_groups) 
	AddressedBy: Faisal 
	Recommendation: cluster health looks fine. I can see read/write for offerengine namespace

Issue9: [Urgent] [IMP] Not able to login on stage box -: ==stg-olympusim002.phonepe.mh6==, and client getting 404 while login
	ReportedBy: [@prod-sre-paas-oncall](https://phonepetalk.slack.com/admin/user_groups)
	AddressedBy: Arati Kulkarni SREPLAT
	Recommendation: nginx logs has filled up the root disk
	Tagged: [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R) [@arati.kulkarni](https://phonepetalk.slack.com/team/U010L8VDWPP)
```
sre@stg-olympusim002:~$ du -cshx /var/log/nginx/*
0	/var/log/nginx/access.log
43G	/var/log/nginx/access.log.1
0	/var/log/nginx/error.log
342M	/var/log/nginx/error.log.1
43G	total
```

Issue10: Nginx Error:  resource not found for existing resource (404)
	ReportedBy: [@paas-on-call](https://phonepetalk.slack.com/admin/user_groups)
	AddressedBy: VISTARA 
	Recommendation: t is due to expired  or missing auth token , retry with fresh token should work.

Issue11: Getting 404 on api-testing endpoints
	ReportedBy: [@api-oncall](https://phonepetalk.slack.com/admin/user_groups)
	AddressedBy:
	Recommendation: 

Issue12: Stage apps getting timeouts from ==stg-es60x== making the apps crash
	ReportedBy:  [@srees-oncall-for-prod-issues](https://phonepetalk.slack.com/admin/user_groups)
	AddressedBy: VISTARA
	Recommendation: cluster health looks fine. I can see read/write for offerengine namespace
	Tagged: @kuruba.mallesh

Issue13: Issue connecting to ES host foxtrot ==stg-es601.phonepe.nb6==
	ReportedBy: [@srees-oncall-for-prod-issues](https://phonepetalk.slack.com/admin/user_groups)
	AddressedBy: vishwasbhat.d (SRE HDP), VISTARA
	Recommendation: Elasticserach storage is full, increasing the disk size, increased the size to 600G, 
	Tagged: [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R) [@Amith R](https://phonepetalk.slack.com/team/U07C2578SC8) [@harshada.patel](https://phonepetalk.slack.com/team/U07SXP3F8TS)

Issue14: Facing issue while connecting to stage mariadb cluster
	ReportedBy: 
	AddressedBy: VISTARA, passed on to Shiv
	Recommendation: 
	Tagged: [@sreinfra-prod-oncall](https://phonepetalk.slack.com/admin/user_groups), [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R) [@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3) Shivanand

```
Krishnakumar  

@here We will be decommissioning the below mentioned clusters of old versions which are there in STG and not being used in PROD.  

RMQ:
  '3.6.6':
    - stg-rmq001.phonepe.nb6
  '3.7.9':
    - stg-rmq10{1..3}.phonepe.nb6
  '3.7.14':
    - stg-rmq20{1..3}.phonepe.nb6

ElasticSearch:
  '7.3.0':
    - stg-es30{1..3}.phonepe.nb6
  '7.12.0':
    - stg-es50{1..3}.phonepe.nb6
  '7.10.2':
    - stg-tekes70{2..4}.phonepe.nb6

  
  
If you are using old version , Aerospike to move to new version please raise a jira via  [https://stage-shared-jiravista.phonepe.com/home](https://stage-shared-jiravista.phonepe.com/home)  
  
New versions:-  

Aerospike:

  '6.1.0.40':
    - stg-corecertifiedaerospike61{1..3}.phonepe.nb6
  '6.4.0.23':
    - stg-corecertifiedaerospike64{1..3}.phonepe.nb6
  '8.0.0.8':
    - stg-corecertifiedaerospike80{1..3}.phonepe.nb6

RMQ:
  '3.11.2':
    - stg-corecertifiedrmq31{1..3}.phonepe.nb6
  '3.13.7':
    - stg-corecertifiedrmq33{1..3}.phonepe.nb6
  '4.0.6':
    - stg-corecertifiedrmq40{1..3}.phonepe.nb6

ElasticSearch:
  '8.9.2':
    - stg-corecertifiedes89{1..3}.phonepe.nb6
  '8.11.3':
    - stg-corecertifiedes81{1..3}.phonepe.nb6
  '8.15.3':
    - stg-corecertifiedes85{1..4}.phonepe.nb6
  '9.1.2':
    - stg-corecertifiedes91{1..3}.phonepe.nb6
```

Issue13: Unable to write to DB via service - ==[stg-dbvipstagepp07.phonepe.nb6]==
	ReportedBy: [@srees-oncall-for-prod-issues](https://phonepetalk.slack.com/admin/user_groups)
	AddressedBy: vishwasbhat.d (SRE HDP), VISTARA
	Recommendation:  
	Tagged:[@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3), [@aniruddh.singh](https://phonepetalk.slack.com/team/U07AYQL3V8F) @/srees-oncall handle

```
Hi Team,  
We're taking restart of stg-clouddb562.phonepe.nb6 due to hardware issue.  
Following VMs will be afftected.  

stg-hdplucy117
stg-hdpplatformad001
stg-es601
stg-hdplucysuperset004
stg-hdptesthbase005
```

Issue14: Unable to access stage box ==stg-olympusim002.phonepe.mh6== even after infosec approval
	ReportedBy: Software Engineer | OlympusIM
	AddressedBy: vishwasbhat.d (SRE HDP), VISTARA
	Recommendation:check with your respective SRE team, they will be able to help you here `**Process Update: Dev Sudo Access on Non-Shared Boxes**` Didn't receive any mail regarding this
	Tagged:[@Amith R](https://phonepetalk.slack.com/team/U07C2578SC8) / [@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3) [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R)  not related [@srees-oncall-for-prod-issues](https://phonepetalk.slack.com/admin/user_groups)

Issue15: Calls to ES are failing via merchant-onboarding ==stg-tekes702.phonepe.nb6==
	ReportedBy: QA: Merchant Offline : PB App |  Mahesh P | 
	AddressedBy: Akshit SRE 
	Recommendation:there is a version mismatch of ES between prod and stage hence an architectural change is required.

Issue16: need to increase request size
	ReportedBy: [@Vrishti Gupta](https://phonepetalk.slack.com/team/U05KG5NGZQA) | Lending 
	AddressedBy:  VISTARA @stage-sre-oncall
	Recommendation:Raised a JIRA 
	Tagged: @stage-sre-oncall


Issue17: Connection pool exhausted from payments to mariadb when run via Autotest suite
	ReportedBy: [@payment-stage-oncall](https://phonepetalk.slack.com/admin/user_groups)
	AddressedBy: [@Shashank Uniyal](https://phonepetalk.slack.com/team/U01QJEF8SBG)
	Recommendation:
	Tagged: [@Shashank Uniyal](https://phonepetalk.slack.com/team/U01QJEF8SBG) [@Ratnakar](https://phonepetalk.slack.com/team/U05QC1HBMS5)


Issue18: Service is not restarting after updating the rmq cluster version 
	ReportedBy: [@kirti.sain](https://phonepetalk.slack.com/team/U07MM3ZJQS0) SWE 
	AddressedBy: mridul/iyer
	Recommendation: 
	Tagged: [@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3) - Actual | [@sre-stockbroking-oncall](https://phonepetalk.slack.com/admin/user_groups) @mridul/iyer SRE AZURE 


Issue19: Help in creating ES indices for nexus
	ReportedBy: 
	AddressedBy: vishwasbhat.d | [@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3)
	Recommendation: Please raise a Jira via JIRAVISTA
	Tagged: [@srees-oncall-for-prod-issues](https://phonepetalk.slack.com/admin/user_groups) | vishwasbhat.d | [@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3), [@aniruddh.singh](https://phonepetalk.slack.com/team/U07AYQL3V8F)


Issue20: ==stg-corecertifiedaerospike803.phonepe.nb6== 4333 Error 65: Login failed
	ReportedBy: dev @CSX
	AddressedBy: Krishnakumar
	Recommendation: JIRA raised
	Tagged: [@sre-cs-oncall](https://phonepetalk.slack.com/admin/user_groups)


Issue21: Stage proxy configuration query
	ReportedBy: Software Engineer - Nexus
	AddressedBy: VISTARA 
	Recommendation: JIRA RAISED
	Tagged:[@sre-merchant-nexus-oncall](https://phonepetalk.slack.com/admin/user_groups) | VISTARA

Issue22: [https://ultron-ui-stage-internal.phonepe.com](https://ultron-ui-stage-internal.phonepe.com) giving 504 [Error occured while trying to proxy to: ultron-ui.nixy.stg-drove.phonepe.nb6/v1/localization/enabled/PHONEPE_MX/VOICEBOT?configType=TEXT]
	ReportedBy: Backend@CSX
	AddressedBy:  [@cs-oncall](https://phonepetalk.slack.com/admin/user_groups)
	Recommendation: JIRA Raised
	Tagged: [@cs-oncall](https://phonepetalk.slack.com/admin/user_groups) [@cs-ui-oncall](https://phonepetalk.slack.com/admin/user_groups) | @Venkat

Venkateshwar Reddy  [12:05 PM]  

```
Hi Team,  
  
The BM stg-clouddb529.phonepe.nb6 is currently experiencing an SSD disk issue. We attempted to take a backup of the disk, but the process failed due to an I/O error.  
Following VMs will be affected.  

 Id    Name                           State
----------------------------------------------------
 -     stg-hbaselucy001               shut off
 -     stg-hdplucysuperset002         shut off
 -     stg-lucyapps002                shut off
 -     stg-lucyllap001                shut off
 -     stg-mankuthimma001             shut off
 -     stg-praz001                    shut off
 -     stg-uates601                   shut off

Note:- If the above VM's are required ,Please raise a Jira with provisioning team.  
CC: [@rahul.devale]
```

Issue23: One of the api when being hit from app is throwing 404 though it exisit in the Incentivization feature env
	ReportedBy:  dev [@anjali.tulsyan](https://phonepetalk.slack.com/team/U08S8SLSWD9)
	AddressedBy: IssueBot
	Recommendation: 
	Tagged: [@sre-ads-oncall](https://phonepetalk.slack.com/admin/user_groups) 

Issue24: Connectivity between hadoop to drove executor.
	ReportedBy: DEv - [@Jagrit Drolia](https://phonepetalk.slack.com/team/U03G41NCM0X)
	AddressedBy: [@skasif.raja](https://phonepetalk.slack.com/team/U055LTAUS14)
	Recommendation:  if you need help from shared  stage sre team , please raise jira request [https://stage-shared-jiravista.phonepe.com/](https://stage-shared-jiravista.phonepe.com/) 
	Tagged: [@skasif.raja](https://phonepetalk.slack.com/team/U055LTAUS14) [@Venkateshwar Reddy](https://phonepetalk.slack.com/team/U036X4MF3GT) [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R)
	(NOT RESOLVED) - couldnt find the right tempelate for this issuw

Issue25: getting 404 gnix from proxies "[insurance-sandbox-testing.phonepe.com](http://insurance-sandbox-testing.phonepe.com)" &  "[insurancewebsite-stage-internal.phonepe.com](http://insurancewebsite-stage-internal.phonepe.com)" Hey [@sre-ins-oncall](https://phonepetalk.slack.com/admin/user_groups) we are observing an outage on the following proxies could you please check and restore connectivity
	ReportedBy: Rohan Kumar -Dev
	AddressedBy: 
	Recommendation: looks like these are hosted in nb6 not azure, nor are the upstream pointing to ad1 services,  @sre-uat-oncall can you pls help here. JIRA raised
	Tagged: [@sre-ins-oncall](https://phonepetalk.slack.com/admin/user_groups)

Issue26: I am taking and restoring the db from one database to another database.
	ReportedBy: Backend @Ads/Growth
	AddressedBy: VISTARA
	Recommendation: Raised JIRA ... MIGRATION
	Tagged: [@sre-ads-oncall](https://phonepetalk.slack.com/admin/user_groups)

Issue27: Stage grafana details
	ReportedBy: amber kulkarni
	AddressedBy: 
	Recommendation: not managed by rahul, Rahul " we dont manage the data inside the grafana usually maintained by respective devs" 
	Tagged: [@ppi-oncall-group](https://phonepetalk.slack.com/admin/user_groups) | Rahul

Issue28: ES exception
	ReportedBy: Dev - Manoj Kumar Sadhu
	AddressedBy: 
	Recommendation: 
	Tagged: [@tstore-on-call](https://phonepetalk.slack.com/admin/user_groups) [@sre-es-tstore-oncall](https://phonepetalk.slack.com/admin/user_groups) 

Issue29: Orbis Hbase is down
	ReportedBy: Backend @ Central Platforms - Abhigyan Bharati
	AddressedBy: Sameer - SREHDP
	Recommendation: addressed by Sameer
	" The **stg-hdporbis** cluster is recovering from a crash loop caused by a Kerberos authentication failure with replication peer, which has been resolved by manually deleting the peer from ZooKeeper. Although critical disk space was cleared by purging 100GB+ of Ranger and `oldWALs` to resolve HDFS write blocks, the cluster remains stuck in a recovery deadlock.  
	Specifically, **SplitWALProcedures** (PIDs `333854`, `334056`) are attempting to replay corrupted logs from the previous crashes, causing RegionServers to cycle repeatedly.  
	We are currently aborting these hung procedures and sidelining the corrupted WAL files in HDFS to allow the `hbase:meta` table to finally come online.  
	We still need /data folder cleanups on all the 3 nodes 201,202 and 203, since they crossed 90%. Working on this. Will update you on this. "
	Tagged: [@srehdp-stg-oncall](https://phonepetalk.slack.com/admin/user_groups) | Sameer

Issue30: Aerospike Error :Error -3,1,30000,1000,5: Cluster is empty" } }
	ReportedBy: Dev at PaymentPreprocessor - MCP 
	AddressedBy: Rahul | Krishna 
	Recommendation: new namespace created in new cluster . JIRA Raised
	Tagged: [@srehdp-stg-oncall](https://phonepetalk.slack.com/admin/user_groups) - Wrongly tagged | @rahul

Issue31: R999 issue from API gateway | [testing.phonepe.com/apis/legion/v2/auth/login/initiate](https://api-testing.phonepe.com/apis/legion/v2/auth/login/initiate)
	ReportedBy: Dev 
	AddressedBy: 
	Recommendation: 
	Tagged: [@paas-on-call](https://phonepetalk.slack.com/admin/user_groups)

Report of Issues raised in **FEBRUARY**
Issue32: Service not able to connect to stage AS nodes.
	ReportedBy: Dev - Paras Jain
	AddressedBy: VISTARA 
	Recommendation: JIRA RAISED
	Tagged: [@payments-infra-oncall](https://phonepetalk.slack.com/admin/user_groups) 

Issue33: Any new RMQ version was pushed to ==stg-rmq50{1...5}.phonepe.nb6== recently
	ReportedBy: SWE| PaaS | Rosey | Autoscaler
	AddressedBy: Rahul 
	Recommendation: JIRA raising was asked, but didn't do
	Tagged: [@sumit.bana](https://phonepetalk.slack.com/team/U09CHHU1BNK) [@arati.kulkarni](https://phonepetalk.slack.com/team/U010L8VDWPP) 

Issue34: Zookeeper Connection CICD Pipeline ==stg-appzkobserver007==
	ReportedBy: Dev - Basant Kumar
	AddressedBy: Ankit Das
	Recommendation: The ZK node is up and running with no issues
	Tagged:[@sre-acc-oncall](https://phonepetalk.slack.com/admin/user_groups) / [@basant.kumar2](https://phonepetalk.slack.com/team/U08BM6G88JU) 
```
sre@stg-appzkobserver007:~$ echo mntr | nc localhost 2181
zk_version	3.8.4-9316c2a7a97e1666d8f4593f34dd6fc36ecc436c, built on 2024-02-12 22:16 UTC
zk_server_state	observer
zk_peer_state	observing - broadcast
zk_observer_master_id	2
zk_ephemerals_count	5436
zk_num_alive_connections	418
zk_avg_latency	0.2151
zk_outstanding_requests	4
zk_znode_count	15959
zk_global_sessions	1266
zk_non_mtls_remote_conn_count	6309338
zk_last_client_response_size	84
zk_packets_sent	8736002036
zk_packets_received	8730108132
zk_max_client_response_size	15101
zk_connection_drop_probability	0.0
zk_watch_count	410
zk_auth_failed_count	0
zk_min_latency	0
zk_max_file_descriptor_count	500000
zk_approximate_data_size	1662151
zk_open_file_descriptor_count	531
```

Issue35: getting error: Did not find any key for team: accounting
	ReportedBy:  Software Engineer - Accounting
	AddressedBy: Muhammed.k
	Recommendation:Please check with SDE/stage team - not addressed
	Tagged: [@money-management-oncall](https://phonepetalk.slack.com/admin/user_groups) [@sre-acc-oncall](https://phonepetalk.slack.com/admin/user_groups) 
	UNRESOLVED | UNADDRESSED

Issue36: Suddenly roles assigned for ES syster user got chnaged
	ReportedBy: SWE - Chandu
	AddressedBy: 
	Recommendation: 
	Tagged: [@jebastin.r](https://phonepetalk.slack.com/team/U02CCH0QB7W) / [@Venkatesan V](https://phonepetalk.slack.com/team/U02HU0HU5EG)
	UNRESOLVED | HOPPING TOOK PLACE

Issue36: kafka queue caretion
	ReportedBy: Dev - Vishnu Narayanan S
	AddressedBy: [@vishnu.narayanans](https://phonepetalk.slack.com/team/U060C6GSVT6)
	Recommendation: None .. resolved
	Tagged: [@srehdp-stg-oncall](https://phonepetalk.slack.com/admin/user_groups) 

Issue37: whitelisting /apis/nimbus and /apis/athena [SRESTAGE-6264]
	ReportedBy: [@rutul.darji](https://phonepetalk.slack.com/team/U04G6T8SHLH) Dev@MPS
	AddressedBy: 
	Recommendation: 
	Tagged: [@paas-on-call](https://phonepetalk.slack.com/admin/user_groups)
	UNRESOLVED | UNADDRESSED

Issue38: unable to connect to Aerospike from WebForm. It’s failing with AEROSPIKE_ERR_INVALID_HOST (“Invalid hostname”).
	ReportedBy: Kamal Joshi | Software Engineer UI
	AddressedBy: 
	Recommendation: 
	Tagged: [@sre-cs-oncall](https://phonepetalk.slack.com/admin/user_groups) 
	UNRESOLVED | UNADDRESSED

Issue39: We are seeing connection refused to stg-appzkobserver003-stg-clouddb606.phonepe.nb6/10.57.10.51:2181,
	ReportedBy: Nagendra Jha - Insurance
	AddressedBy: 
	Recommendation: Ignore it guys, its resolved.  Gone through Stage Zookeeper Decomissioning Activity email.  Thanks
	Tagged: [@srehdp-stg-oncall](https://phonepetalk.slack.com/admin/user_groups) | [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R) 

Issue40: Docker image pulls failing
	ReportedBy: Prejith Premkumar - Data Scientist
	AddressedBy: 
	Recommendation: check with [#ci-cd-support](https://phonepetalk.slack.com/archives/C05EPBPHWSG) | 
	Tagged:[@paas-on-call](https://phonepetalk.slack.com/admin/user_groups) | [@chandanpreet.saini](https://phonepetalk.slack.com/team/U0481G9JV6G) [@aditya.mittal](https://phonepetalk.slack.com/team/U029375PA21) 
	{it got deployed after a lot of retries but the docker image pull issue used to be rare before, and now its very regular}

Issue41: getting the error screen after app launch
	ReportedBy:Dev - Atul Kumar Jain
	AddressedBy: Atul, Priya Sharma, Kesavan Vinod Kumar
	Recommendation: [@Atul Kumar Jain](https://phonepetalk.slack.com/team/U053L9Y7KLH)
	Tagged:[@sreinfra-prod-oncall](https://phonepetalk.slack.com/admin/user_groups) | [@app-user-oncall](https://phonepetalk.slack.com/admin/user_groups) | 

Issue42:Kindly provide drop permissions to mariadb user
	ReportedBy: Harsh Chaurasiya | Backend @Ads/Growth
	AddressedBy: VISTARA 
	Recommendation: JIRA raised .. but too much of conversation on slack thread, issue with shard name exchange and existing permissions
	Tagged: [@sre-ads-oncall](https://phonepetalk.slack.com/admin/user_groups) | [@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3) | 

Issue43: instances are not allocating for new deployments
	ReportedBy: Dev - Manoj Kumar Sadhu
	AddressedBy: 
	Recommendation: 
	Tagged: [@srehdp-stg-oncall](https://phonepetalk.slack.com/admin/user_groups)  | [@srehdp-oncall](https://phonepetalk.slack.com/admin/user_groups) | [@manasa.reddym](https://phonepetalk.slack.com/team/U03RC79CP4P) /[@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3) | [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R) 
	UNRESOLVED | UNADDRESSED

Issue44: Need to grant SHOW VIEW privilege to all the views present in payment_shard1 and payment_shard2 
	ReportedBy: Aditya Atri - DEV
	AddressedBy: 
	Recommendation: JIRA raised via JiraVista
	Tagged: [@payment-stage-oncall](https://phonepetalk.slack.com/admin/user_groups)  | @Shivam Gupta

Issue45: X-OBP functionality is not working in the Stage environment (==nb6 tinyproxy==)?
	ReportedBy: [@apurv.tiwari](https://phonepetalk.slack.com/team/U094NMSCB1A) | 
	AddressedBy: 
	Recommendation: 
	Tagged: ? 

Issue46: **:** Table 'payment_meta_shard1.delegate_requesters' doesn't exist in engine
	ReportedBy:  Shorya Chauhan | Payments Mgmt & Experience- Dev
	AddressedBy: ? 
	Recommendation: ? 
	Tagged:[@payments-infra-oncall](https://phonepetalk.slack.com/admin/user_groups) | SRESTAGE EM

Issue47: i am not able to scale this deployment [https://stg-nb6.drove.phonepe.com/applications/docs-gpt-2_0_5-snapshot](https://stg-nb6.drove.phonepe.com/applications/docs-gpt-2_0_5-snapshot) Can you pls check it
	ReportedBy: Nikhil Sandilya | Software Engineer @FRA
	AddressedBy: vamsi.a 
	Recommendation: Resolved
	Tagged: [@sweta.shaw](https://phonepetalk.slack.com/team/U031ZSQEBS8) | [@manasa.reddym](https://phonepetalk.slack.com/team/U03RC79CP4P) 
	

Issue48: Issue with fabricator proxy. Getting 503 after rosey restart for [https://fabricator-stage-internal.phonepe.com](https://fabricator-stage-internal.phonepe.com) even if service is up.
	ReportedBy: Soumyashis Pradhan | Web Platforms | Fabricator
	AddressedBy: [@sreinfra-prod-oncall](https://phonepetalk.slack.com/admin/user_groups) | vishnu.naini 
	Recommendation: 
	There is a config issue in one app that triggered exceptions in drove gateway   "feature-environment-name": "$FEATURE_ENVIRONMENT_NAME"[@ccd-oncall](https://phonepetalk.slack.com/admin/user_groups) killing this app `ccd-ftfinaltestfeaturefactoryf95jqkdl26mjzlapp2602101628313800360538`
	Tagged: [@ccd-oncall](https://phonepetalk.slack.com/admin/user_groups) | 
	


Issue49: calls getting rejected at nginx with 400
	ReportedBy: Ashish Patel | payments-mgmt-and-experiences
	AddressedBy: 
	Recommendation: to connect to teh right POC ... attached the old pinned thread
	Tagged:[@sreinfra-prod-oncall](https://phonepetalk.slack.com/admin/user_groups) | wrongly tagged 


```
vishnu.naini  [2:22 PM]  

replied to

Please do not tag [@sreinfra-prod-oncall](https://phonepetalk.slack.com/admin/user_groups). We are not the POC for any stage issues
```


Issue50:  right POC not tagged and instruction not followed by Developer 
	ReportedBy: Ashish Patel 
	AddressedBy: 
	Recommendation: right POC not tagged , DEv issue
	Tagged: Rahul
	

Issue51: Rmq node is unhealthy
	ReportedBy: Apoorv Rajput | Software Engineer BE | Discovery
	AddressedBy: 
	Recommendation: 
	Tagged:[@sreinfra-prod-oncall](https://phonepetalk.slack.com/admin/user_groups)  WRONGLY TAGGED


Issue52: ==stg-dbvipstagepp07.phonepe.nb6== vartalap serves is not able to connect DB
	ReportedBy: Sakti Behura Web Platforms | Fabricator (4F - 973)
	AddressedBy: VISTARA 
	Recommendation: JIRA RAISED 
	Tagged: 
	

Issue53: DB connectivity issue on stage ==stg-dbvipstagepp07.phonepe.nb6==
	ReportedBy: vishal malhotra - Software Engineer
	AddressedBy: Neha p 
	Recommendation: 
	Tagged: [@sre-fra-oncall](https://phonepetalk.slack.com/admin/user_groups)  WRONGLY TAGGED 


```
Hi team, Is there any api available or any SOP on how to validate google oauth2 tokens on our service level?
```

Issue54: Write to kafka topics are failing
	ReportedBy: Manoj Kumar Sadhu - Dev
	AddressedBy: 
	Recommendation: 
	Tagged: [@srehdp-oncall](https://phonepetalk.slack.com/admin/user_groups)
	
Issue55: Not able to connect to kafka brokers ==(stg-tstorekafkasource001-3.phonepe.nb6)==
	ReportedBy: Rahul Ram | Software Engineer @ Incentivization
	AddressedBy: Prakash Roy SREHDP - OND/INDUS/INS/LEN/BFSI
	Recommendation: We are facing unrecoverable disk failures on this cluster.
	We need you to move your clients to another staging environment.
	Tagged: [@srehdp-stg-oncall](https://phonepetalk.slack.com/admin/user_groups) | 

```
Krishnakumar  [12:28 PM]  

Hi Team,  
We're restarting services on below mention mariadb cluster for [STGSHARED-543](https://jira.phonepe.com/browse/STGSHARED-543),  
stg-corecertifiedmaria21{1..3}.phonepe.nb6  
Mentioned cluster will not be operational for sometime.  
We will let you once the cluster is up.  
CC : [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R) [@remyasree.mk](https://phonepetalk.slack.com/team/U010N24R2H4)

```
	
Issue56:[@sre-cs-oncall](https://phonepetalk.slack.com/admin/user_groups)  Facing issue with webform stage proxy url  https://webform-stage.phonepe.com/](https://webform-stage.phonepe.com/)  Its showing bad gateway 502  Although an instance is up on stage and can able to load it using  instance id and port number  [http://stg-droveexec036.phonepe.nb6:18755/](http://stg-droveexec036.phonepe.nb6:18755/)
	ReportedBy:Dev - Devendra Deotale
	AddressedBy: VISTARA
	Recommendation: JIRA to be raised with issue "issues in existing infra components"
	Tagged: [@Krishnakumar](https://phonepetalk.slack.com/team/U01MU5MEHM3) [@Venkateshwar Reddy](https://phonepetalk.slack.com/team/U036X4MF3GT) | [@manasa.reddym](https://phonepetalk.slack.com/team/U03RC79CP4P)
	
	
Issue57: STAGE nginx config for /support  location.
	ReportedBy: Akshaykumar Purad | Software Engineer
	AddressedBy: chaturya.rajput
	Recommendation: All the routings for `*.internal.share.market` is managed by PPI SRE team. Stockbroking dev team only manages routings for ==sb-testing.phonepe.com==
	Tagged: [@sre-stockbroking-oncall](https://phonepetalk.slack.com/admin/user_groups)
	
Issue58: Db Connection pool is getting closed
	ReportedBy: Dewanshi Paul | Backend @OM
	AddressedBy: Vibhav.mishra
	Recommendation: Please make sure that issues are escalated to the correct team handles.
	Tagged:[@sre-merchant-nexus-oncall](https://phonepetalk.slack.com/admin/user_groups)| [@samarth.tankasali](https://phonepetalk.slack.com/team/U094LDK16E6)
	WRONGLY TAGGED 
	
Issue59: [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R) need your assistance with upgrading the tls version of our outbound proxy to version **TLS 1.3** since our downstream vendor has made it compulsory.  outbound proxy: `krapancheck-cvlindia-com.stgob.phonepe.nb6`
	ReportedBy: 
	AddressedBy: 
	Recommendation: JIRA raisedContext:  Kindly ensure your application are making request using below specified ciphers.
	List of cipher supported by TLS 1.3 for CVL Applications
	TLS_AES_128_GCM_SHA256 (0x1301)
	TLS_AES_256_GCM_SHA384 (0x1302)
	TLS_CHACHA20_POLY1305_SHA256 (0x1303)
	Tagged: [@rahul.devale](https://phonepetalk.slack.com/team/U03C7ALC44R)

Issue60: Couldn't resolve host address for zkHost : ==stg-appzkobserver004.phonepe.nb6==, service not booting up.
	ReportedBy: Dev - Yash Budukh
	AddressedBy: AJIMON SIJI
	Recommendation: Config provided
	Tagged: [@paas-on-call](https://phonepetalk.slack.com/admin/user_groups)
	
Issue61: 
	ReportedBy: 
	AddressedBy: 
	Recommendation: 
	Tagged: 
	
Issue47: 
	ReportedBy: 
	AddressedBy: 
	Recommendation: 
	Tagged: 
	
Issue47: 
	ReportedBy: 
	AddressedBy: 
	Recommendation: 
	Tagged: 
	
Issue47: 
	ReportedBy: 
	AddressedBy: 
	Recommendation: 
	Tagged: 
	








- not able to find the right template on JIRAVISTA
- not finding the right team tag or sre to address the specific issue
- issue is being dogged 
- let me know the poc for this proxy
- Nobody address the issue , issue stays unresolved
- Repetative Response to raise JIRA--need to keep it as a bot response to reduce 
- Wrongly Taggged
- People who are not taaged ... still tag the wrong team and the issue gets diverted 
- Dev Mentioned @all for some normal issue ... and wasnt able to read the message
- Wrongly tagged ... issue mostly not addressed - Feb month
- 