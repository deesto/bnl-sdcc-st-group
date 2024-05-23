# BNL SDCC S&T Group
Work logs for the S&amp;T Group in the SDCC at BNL.

## Ongoing Meetings
- ATLAS ADC (weekly)
- Belle II BNL Software & Computing (weekly, BNL, remote)
- Belle II Conditions Database Coordination (monthly, remote)
- Belle II Distributed Computing (weekly, KEK, remote)
- CVMFS Coordination (monthly, CERN, remote)
- NPP All Hands Meetings (quarterly)
- NPPS Group Meetings (bi-weekly)
- Rucio Token Working Group (monthly, CERN, remote)
- SDCC ATLAS Tier 1 (weekly, remote)
- SDCC Liaison (monthly)
- SDCC Services & Tools (weekly)
- SDCC Staff (monthly)
- SDCC Technical (monthly)
- SDCC User Services section (weekly)
- US ATLAS Computing Facility (weekly, remote)
- US ATLAS Facilities Research & Development (bi-weekly, remote)
- US ATLAS Tier 2 (weekly)
- WLCG AuthZ Working Group (bi-weekly, remote)
- WLCG Frontier Meeting (remote)
- WLCG Unified Token (GUT) Profile Working Group (monthly, remote)

## 20-25 May
- ATLAS: continues to [report CVMFS client errors on WNs at many sites](https://os-atlas.cern.ch/dashboards/app/dashboards?security_tenant=#/view/a312a030-8b0e-11e8-a7e3-ffbb2f24f6b4?_g=(refreshInterval:(display:Off,pause:!f,value:0),time:(from:now-24h,mode:quick,to:now))&_a=(description:'',filters:!(('$state':(store:appState),meta:(alias:!n,disabled:!f,index:'006980c0-857a-11ea-9233-1dd73e396ea6',key:nativeexitcode,negate:!f,params:(query:64),type:phrase),query:(match_phrase:(nativeexitcode:64)))),fullScreenMode:!f,options:(darkTheme:!f,hidePanelTitles:!f,useMargins:!t),query:(language:lucene,query:''),timeRestore:!t,title:'Harvester%20particular%20computingsite',viewMode:view)) that fail new pilot checks
  - More troubleshooting of IO and extended file attribute errors from CVMFS clients at UofM
  - More reports of local errors on BNL worker nodes
- ATLAS: VO user management, questions, troubleshooting
- Belle II: travel for pre-B2GM & B2GM workshops (25 May - 8 Jun)
- Belle II: continued review & revision of conditions database migration [written proposal](https://docs.google.com/document/d/1DBDWV-wPtdnMPKqn6-vfSjagkq-wFXIRuUIjt1Lukw4/edit?usp=sharing) & [B2 Distributed Computing proposal slides](https://docs.google.com/presentation/d/1IUyvAfTALiDYxVi32YTHFng8mllI42zj9EYEGzesYro/edit?usp=sharing)
- Belle II: removed Jitendra (no longer with conditions team) from [BNL T1 CDB support email alias](mailto:t1-belle2-cdb@bnl.gov); added RT Databases queue address so new requests will be tracked there
- Belle II: [merge request](https://gitlab.desy.de/belle2/admin/jwt-server/-/merge_requests/16/commits) from Feb to remove Jitendra from validation GT list finally approved (23 May)
- Belle II: investigated issue with all BNL jobs being held since DIRAC upgrade
  - All submitted jobs held due to expression match with cryptic condition output; job error output showed issues with new DIRAC option (`--CVMFS_locations`)
- Belle II: investigated slowness reported on single, user-created global tag (user_rihoppe_tracking_momSF_v0)
  - Heavy request load seen from a few sites (UVic, DESY, GridKa), but no service issues seen and reasonable response times to tests
- BNL: all-hands meeting
- NPP: all-hands meeting (safety)
- SDCC: consideration with Alexei of possible future collaboration & contributions by A. Alekseev to facility monitoring
- SDCC: [Jira issue created](https://racfjira.atlassian.net/browse/WEB-25) to document current state of web infrastructure and services, which badly need to be updated
- WLCG Frontier: more follow-ups to past reports of excessive ATLAS site squid use and repeated requests within jobs

## 11-17 May
- ATLAS: VO user management, questions, troubleshooting
  - Fix for broken Rucio user names due to errant VOMS user nicknames (defects invisible in VOMS interface)
  - Full list of inconsistencies [reported by Petr](https://docs.google.com/spreadsheets/d/1lLktYujJizY-cZ02qFn7rWwZ-qyQMScp-RYIHLe_pB0/edit#gid=0)
- ATLAS: VO admin [workshop](https://indico.cern.ch/event/1417057/) to demonstrate and [discuss](https://indico.cern.ch/event/1417057/?note=280430#2-discussion) IAM user account and proxy workflows ([slides](https://indico.cern.ch/event/1417057/contributions/5956704/attachments/2856275/5000690/IAM-user-registration-v02a-atlas-update.pdf))
- ATLAS: [user issues](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36767) with grid authentication due to cron missing from EL9 upgrade to ATLAS CVMFS build host (had been reported to ADC DPA list but not elsewhere)
- Belle II: investigated new, excessive conditions request traffic from Trieste WNs bypassing site cache
- Belle II: KEK DIRAC upgrade 14 May, drained jobs 13 May to clear queue until upgrade concludes
- Belle II: organized & chaired conditions database coordination meeting, provided production payload deployment details, reviewed HSF CDB proposal
- CVMFS: reported ATLAS pilot/wrapper repo check issues to WLCG CVMFS WG, issues with SELinux file system labeling in Stratum One deployment in EL9 
- CVMFS: added new domain, key, templates, replication for new OSG ardc.edu.au domain and neurodesk.ardc.edu.au repo per [RT #36682](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36682)
- OSG: testing of proxy initialization in voms-2.1.0-0.31.rc3.2.osg23.el9.x86_64 regression patch on EL9 WNs 
- SDCC: User Services discussions on [user reported documentation issues](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36746), and resulting doc [[1](https://racfjira.atlassian.net/browse/WEB-22), [2](https://racfjira.atlassian.net/browse/WEB-23)] web migration [[3](https://racfjira.atlassian.net/browse/WEB-24)] mitigation plans.
- SDCC: extensive User Services, General Services, and liaison discussions on coordinating NX server reboot downtime
- US ATLAS: further investigation of ATLAS auth and VOMS roles, groups issues for NET2 admin
  - CERN OpenSearch [Harvester site dashboard](https://os-atlas.cern.ch/dashboards/goto/04b4aaf4d9ff578d358fde708fbbe17d?security_tenant=global) auth seems to rely on some CERN egroup, not VO/VOMS/IAM
- US ATLAS: questions, help for US ATLAS T2 admins trying to access SDCC Mattermost
  - Overly complicated and obscure registration process prompted requests for docs improvement, login form relabeling
    - 'docs.sdcc.bnl.gov' site with improved docs made public and moved into production (Louis)
    - gitea repo moved from Louis's personal area to SDCC org, problems with absolute linking to doc base found

## 4-10 May
- ATLAS: VO user management, questions, troubleshooting
- ATLAS: multiple changes, events related to VOMS->IAM transition
  - Inconsistencies with user VO status sync
    - `>`50 users disabled in IAM but valid in VOMS had to be fixed by hand (IAM curl API commands)
  - Phase-out of VOMS servers in WLCG (ATLAS)
    - Removal of `/etc/vomses`. reliance on LSC files for end points [ADC Jira](https://its.cern.ch/jira/browse/ADCINFR-214)
    - OSG published updated VO package (v136) on 9 May (OSG 3.6 loses support 30 Jun)
  - Upcoming training/info sessions for VO admins to discuss & demo IAM
- Belle II: proposal for moving conditions database from isolated kubelets to SDCC OKD/OpenShift (Ruslan)
  - Internal discussions on partitioning, funding potential OpenShift provisioning and storage
  - Gained statistics on payload storage (27G), files (572048), average sizes (47.2K)
- Belle II: requires HTCondor-CE upgrade, new robot proxies installed on gate keepers [RT#36756](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36756)
- BNL: annual JTA review & confirmation
- BNL: issue reported by HR with submitted timecard from Sep 2023 not being submitted
  - Sep 2023 was transition month from PeopleSoft to Workday. Card was properly submitted. HR is investigating.
- CVMFS: added replication of new CMS repository (cms-griddata.cern.ch) per [GGUS #166626](https://ggus.eu/index.php?mode=ticket_info&ticket_id=166626)
- CVMFS: investigation of periodic I/O issues on replica inhibiting updates of large repos over weekend
  - Cron collecting repo size stats runs every weekend, uses too much CPU & I/O
  - Possibility to replace cron with stats from native NetApp API for directory sizes
- CVMFS: investigation of reported WN issues leading to ATLAS site black listing
  - ATLAS repos on old clients ran out of file descriptors; other repos unaffected
- SDCC: staff position interviews [1]
- SDCC: User Services group discussions on NX upgrade, Foreman upgrade, Mattermost upgrade, web server space issues (web01)
  - Need to upgrade old (EL6/7) web servers 
- sPHENIX: meeting (Saroj, Chris P) to discuss NX upgrade, KDE client settings migration (which is [simple](https://discuss.kde.org/t/how-do-i-migrate-my-kde-settings/3074/2))
- US ATLAS: VOMS role, group fixes for NET2 admin

## 27 Apr - 3 May
- ATLAS Frontier: local caches overloaded again by analysis client requests for six days (23-28 Apr)
  - Investigation continues with Frontier WG, ADC; no response to local coordination inqueries
- ATLAS: VO user management, questions, troubleshooting
- Belle II: conditions DB host EOL, testing on HSF OKD replacement
  - Production DB dumps, infrastructure review, component replication
- Belle II: issues with conditions access reported by Software build team
  - Overnight build from DESY (30 Apr) failed due to timed-out requests for global tags
  - Metadata request times peaked at 30 seconds for a short period (18:30-20:30 30 Apr)
  - Trieste squid sent > [1 million queries over three-hour span](https://monitoring.sdcc.bnl.gov/pub/grafana/d/b2cdb-gt-access/client-global-tag-access?orgId=1&from=1714512572684&to=1714523372684)
- CVMFS: WLCG reports of slow replication of unpacked repo (28 Apr)
  - No issues seen in service, possibly related to throughput slowdown due to degraded network ports
  - Weekly spike in disk IO on Saturdays may be causing interference
  - RHEV stole 1/3 of VM system memory (125G to 84G) as not guaranteed
    - Required reconfiguration of VM memory in RHEV, reboot of Stratum One host (cvmfs-s1c) to reclaim lost memory
- CVMFS: network issues on NetApp A400
  - Issues found on two of four ports, no issues seen on network
  - Firmware upgrade on A400 to attempt to fix, clear reported port issues
  - Required post-upgrade fix to set one of two inter-connection ports to use proper route (Joe, Mark)
- SDCC: ePIC/sPHENIX PD FY25 meeting, outline review, subject summary
- SDCC: ePIC Phonebook/InvenioRDM intergration meeting
- SDCC: monitoring PD FY24 meetings, discussions, outline of work
  - Monitoring/Prometheus proposal accepted by BNL for Program Development FY24 reserve funds for EIC 
- SDCC: many services affected by EL7 EOL need to be migrated (e.g., Belle II CDB & DDM, CVMFS infra)
  - GS to obtain extended support for EL7 guests within RHEV from ITD (while RHEV remains in support)
- US ATLAS: summary of CERN IAM deployment status & changes for R&D group

## 22-26 Apr
- ATLAS: VO user management, questions, troubleshooting
- ATLAS: found & opened [new Github issue](https://github.com/indigo-iam/iam/issues/755) for IAM not displaying users' institution info to admins
- CVMFS: minor upgrade to client and server versions on server and replica hosts due to useless GeoIP DB issue
- CVMFS: continued discussions on [request from OSG](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36682) 
- SDCC: ePIC/sPHENIX PD FY25 meeting
- US ATLAS: ATLAS/IRIS-HEP Kubernetes Hackathon, [Chicago](https://indico.cern.ch/event/1384683/)

## 13-19 Apr
- ATLAS: VO user management, questions, troubleshooting
- Belle II: continued extensive investigation of reported conditions database access failures from KEKCC & DESY
  - Still no local issues found in the conditions services, servers, logs; all service, connection, & data read tests continue to succeed
  - Multiple non-service-related issues found with payload upload operations:
    - JWT formatting errors (wrong number of '.' characters inserted into issued JWTs, path to token files not recognized)
    - Too many payload files uploaded to a single GT (73k)
    - Extended JWT lifetimes not long enough for Calibration & Data Processing upload procedures
    - IOV aggregation code for cloning GTs [needs improvement](https://gitlab.desy.de/belle2/software/basf2/-/issues/8119/)
- Belle II: Rucio load issues caused by invalid client GeoIP location requests
- BNL: asset validation (laptop, desktop, and a server & JBOD that GS group has moved to CDCE as spares)
- CVMFS: revived investigation of ATLAS reports of CVMFS client issues on WNs ([RT#36674](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36674))
  - Also seen at other sites with same WN setup as BNL, e.g., [AGLT2](https://github.com/cvmfs/cvmfs/issues/3517)
- CVMFS: [request from OSG](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36682) to replicate a new repo (neurodesk) in a new non-OSG, Australian domain (ardc.edu.au)
- Jira: issue, epic type fixes for Linux Farm & WLCG Monitoring projects, moved epic from one to the other (Doug)
- SDCC: ePIC Phonebook/InvenioRDM intergration meeting
- SDCC: ePIC/sPHENIX PD FY25 meeting

## US ATLAS quarterly summary (Apr 2024)
- ATLAS: VO administration, maintenance, troubleshooting, user support; VOMS->IAM/token planning, testing
- ATLAS: Frontier site cache maintenance, troubleshooting, support
- CVMFS: Stratum Zero (US ATLAS/SDCC), Stratum One (ATLAS + all of OSG & WLCG) servers, caches, repository support & maintenance
- SDCC: facility infrastructure and support (staff & users)
- SDCC: User Support section leadership (user accounts, web presence, service troubleshooting)

## 8-12 Apr 2024
- Belle II: continued extensive investigation of reported conditions database access failures from KEKCC & DESY
  - No issues found in the conditions services, servers, logs; all read-only tests succeed
  - Issues seen only in jobs using authorized JWT tokens on payload uploads to large global tags (~73k files)
  - Possible issues with [implementation](https://gitlab.desy.de/belle2/software/basf2/-/blob/main/framework/scripts/conditions_db/cli_main.py?ref_type=heads#L400-402) of construction of global tag end points in basf2 client framework
- NPP: all-hands meeting (DEI topics only)
- NPPS: [ePIC collaboration tools and technologies](https://indico.bnl.gov/event/22938/) meeting
- SDCC: [ACAT Highlights meeting](https://indico.bnl.gov/event/22928/) (NPPS & SDCC) meeting
- SDCC: RT user support
- SDCC: staff opening interviews [1]
- Vacation: excess days taken [1]

## 1-5 Apr 2024
- Belle II: continued investigation and mitigation of broken k8s repos for conditions database hosts & packages
  - DB dump and test DB server configuration for new OKD testbed
- Belle II: investigated reports by calibration, data processing teams of low failure rate (~0.1%) connectivity from KEK to conditions database
  - Extensive connectivity & load testing with zero failure rate, errors possible in calibration setup environment at KEK
  - Excessive requests coming from INFN Squid overloaded service, caused response times <30s for brief periods
- Belle II Sites meeting off-hours participation, status reports & collaboration on site plans (w/Hiro)
- CVMFS: continued investigation of reports of WNs with problematic ATLAS CVMFS client mounts
  - [RT#36646](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36646) yet another case, this time on a spar node
- CVMFS: [confirmed with PHENIX](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36548 ) that recent config updates & file limit increases solved their container repo issues
- SDCC: Prometheus intro talk at [Services & Tools group meeting](https://docs.google.com/document/d/1Ggue0K_m-5rEBjO5unRMr5qZquTN1BbjKqik_q3CaSU/edit); exploratory discussions with staff, sPHENIX
  - Louis setting up new test instance
- US ATLAS: changes to web site authentication & SSO to enable CERN login (Chris, Louis)
  - Changes to login workflow to simplify process & options for US ATLAS users
  - CERN SNOW request for CERN SSO OAuth 2.0 client ID & secret ([INC3810204](https://cern.service-now.com/service-portal?id=ticket&table=u_request_fulfillment&n=INC3810204),[RQF2622183](https://cern.service-now.com/service-portal?id=ticket&table=u_request_fulfillment&n=RQF2622183))

## 25-29 Mar 2024
- ATLAS: continued investigation of BNL & ATLAS-wide pilot failures related to reported CVMFS client mount issues
- ATLAS: edited software tutorial documentation to clarify references to VO membership
  - https://gitlab.cern.ch/atlas-sw-git/atlassoftwaredocs/-/merge_requests/693
- ATLAS: VO user management, questions, extensive troubleshooting
  - Investigation of reported compromised identity ("Mark Rosenbaum") & attempts to acquire VO membership (EGI-CSIRT, Mario)
  - Issues with user VO membership expiration caused by ATLAS IAM upgrade, nullifying VO AUP signing dates
  - [Bug filed with IAM](https://indico.cern.ch/event/1397721/?note=273984) to extend VOMS Admin's ability to re-sign AUP agreements in IAM
- Belle II: conditions database infrastructure deployment and maintenance issues
  - Google has moved Kubernetes repo [from previous hosting](https://packages.cloud.google.com/yum/repos/kubernetes-el7-\$basearch) to [new platform](https://pkgs.k8s.io), dropped our production package versions
  - Exploring possible migration of all services to new platform & versions, or possible migration to OKD
  - Temporarily disabled k8s repo file in production on all conditions hosts to fix broken Puppet runs
- BNL: training renewal requirement for Brookhaven Computer Facility (BCF) in ITD, (AO-BCF)
- Jira: accounting issue reported, finally opened related feature request
  - https://support.atlassian.com/requests/JST-975586
  - https://jira.atlassian.com/browse/ACCESS-1781
- SDCC: fixes for problematic Nagios changes adding NSLS2 alerting groups and contacts
- SDCC: [proposal talk](https://docs.google.com/presentation/d/1HWq_BFYPGfpjnXIPqDoyAzxG-ghD0WiDt49dagPK2Qk/edit?usp=sharing) with Louis to [EIC Computing Retreat](https://indico.bnl.gov/event/22825/) for improved monitoring (Prometheus, ELK, grok)

## 18 - 22 Mar 2024
- Belle II: HSF proposal document for conditions database migration (Ruslan)
- Belle II: Google repo hosting version of kubernetes for conditions has disappeared
  -  Migrated to new hosting platform & URL; our production versions have been dropped
- CVMFS: continued discussion of SFT repo probes in ATLAS job pilot, wrapper
- Globus transfer testing (for Joe & Iris)
- SDCC ATLAS workshop: preparation, setup, logistics for meeting at BNL (Indico, events, logistics)
- SDCC interviews [1]
- SDCC Jira Work Management: continued debugging issue with user log reporting and active user licensing (JST-975586)
  - Feature request required to fix bug (in progress)
- SDCC Projects: initial discussion on possible Prometheus/ELK monitoring pilot
- Vacation: excess days taken [1]

## 11 - 15 Mar 2024
- ATLAS Frontier: continued investigation, treatment of heavily loaded caches
  - Analysis of cache logs, associated Frontier, Panda IDs and jobs
  - All excessive load possibly associated with jobs run by [a single user](https://bigpanda.cern.ch/tasks/?username=Zachary%20Pollock) due to high mem usage, [many failures](https://bigpanda.cern.ch/task/37387219/) on single core queues
  - ADC, Frontier group now following up with user, investigating resource limit enforcement
- CVMFS: added disk to Stratum Zero (with Joe), increased file size limits for PHENIX repo
- SDCC ATLAS workshop: preparations and setup for meeting at BNL (Indico, events, logistics)
- SDCC interviews [2]
- SDCC Jira Work Management: continued debugging issue with user log reporting and active user licensing (JST-975586)

## 4 - 8 Mar 2024
- ATLAS Frontier: continued investigation, treatment of heavily loaded caches
- ATLAS: VO user management, questions, troubleshooting
- Belle II: conditions database maintenance, co-convener meeting, minutes, docs
- Belle II: DIRAC, nginx debugging on development nodes (Hiro)
- Belle II: HTCondor submission issues caused by tokens on test CE at GridKa (GGUS [#164242](https://ggus.eu/index.php?mode=ticket_info&ticket_id=164242))
- CVMFS: continued debugging of ATLAS pilot reports of WN client issues
  - Proved that issue was with pilot check, not with CVMFS client
  - Pilot check code [has been fixed](https://github.com/PanDAWMS/pilot-wrapper/blob/master/runpilot2-wrapper.sh#L185-L199) as a result
- CVMFS: issues with oversized files in PHENIX repository
  - caused warnings to user on publish
  - caused spool and server partitions to run out of space (RT [#36548](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36548))
- ITD/SDCC IDP changes & consolidation discussions
- SDCC interviews [3]
- SDCC Jira Work Management issue with user log reporting and active user licensing (JST-975586)
- SDCC Webdocs web site redirection, maintenance, turning off Drupal (Louis)
- US ATLAS issues with custom Drupal caching & views designed by DataArt (Christian, Louis; RT [#36546](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36546))

## 26 Feb - 1 Mar 2024
- Vacation: excess days taken (2)
- CVMFS: fixed broken frontier/squid/awstats log rotation on reverse proxies with [cron hack](https://webdocs.sdcc.bnl.gov/cgit/puppet/catalog/commit/grid/cvmfs/files/frontier-rsyslog-fix.cron?id=8c3a8bf8a20f27d6d5e5dbd634ecf42699484080) to restart rsyslog
- CVMFS: new OSG storage repos replicated per request (scisoft, ligo-test)
- CVMFS: troubleshooting ATLAS nodes flagged by HC
- Frontier: rampant use of and heavy load on local ATLAS caches for > 1 week, cause or campaign unknown
- User Services: issues with authentication for US ATLAS IB voting page
- HSF/WLCG Analysis Pipelines Workshop ([remote](https://indico.cern.ch/event/1375507/registrations/103067/))
- ATLAS VO user management, questions, troubleshooting
  
