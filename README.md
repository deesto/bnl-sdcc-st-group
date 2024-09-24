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

# 30 Sep - 5 Oct

- BNL travel (Tsukuba, 4-12 Oct)

# 23-29 Sep
- ATLAS: VO, IAM user management, questions, troubleshooting
  - Several problems with user grid access, missing group management privileges, disk quota issues, incorrect user metadata (e.g., email address and nickname records)
- Belle II: problems with user certificates issued by CILogon and RC2-40-CBC encryption algorithm
  - Users must add `-legacy` flag when extracting certificate/key pair from issued .p12 container for grid use
- Belle II: US mgmt wants to reinstate Motomo statistics service, currently hampered by GeoIP inacuracy
  - Only a few user visits to the site per year may not justify dev work toward fixing dedicated service
- CVMFS: Stratum One operations still flagged with slowness by WLCG during intensive weekend operations
  - 17 hour delay on 'unpacked' repo snapshot due to garbage collection
- SDCC: more issues with SSO/MFA causing service failures
  - User self-service token page broke: 500 gateway error after entering life number
  - Several RT tickets from users who could not delete their own tokens
    - Tickets [closed](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37235) by manually deleting user tokens, without action toward fixing or diagnosing service issue
    - Service found to be broken since July
   - PrivacyIdea token updated recently was faulty, needed to be regenerated with 'admin' role, replaced (`pi-manage api createtoken -r admin`)
   - Email and web entry form templates updated with more user-friendly prompts and info
   - Details added to [ongoing Jira SSO issue](https://racfjira.atlassian.net/browse/SSO-90)
- BNL: renewed expiring ['Brookhaven Training Qualification (TQ-PROPERTY)' mandatory training course](https://training.bnl.gov/portal/TQ-PROPERTY)
- BNL travel (San Diego, 28 Sep - 4 Oct)


# 14-21 Sep
- ATLAS: VO, IAM user management, questions, troubleshooting
  - Discussions on clean-up of defunct "software" roles in atlas/cn/usatlas
  - Discrepencies between IAM features on CERN instances in OpenShift and k8s, due to lack of restart on one instance; fixed with "rollout restart"
  - Issues with outdated documentation on [CERN ATLAS TWiki](https://twiki.cern.ch/twiki/bin/viewauth/AtlasComputing/WorkBookStartingGrid)
- ATLAS: ongoing discussion on eliminating invalid ATLAS job requests for 'projects' CVMFS repo on BNL WNs
- Belle II: issues with held jobs on BNL HTCondor gatekeepers, resulting notifications via GK scripts (Kevin)
- Belle II: follow-up meetings to discuss conditions database migration plans, workflows, effects
- Belle II: user issues with setting grid environment, incompatible encryption levels in CILogon certificates
- Belle II: issues with trying to set up OKD project and persistent storage in RHIC instance for CDB migration
- CVMFS: [workshop at CERN](https://indico.cern.ch/event/1347727/) (16-18 Sep)
  - Gave [talk](https://indico.cern.ch/event/1347727/contributions/5673381/) on ATLAS deployment, status, client issues and fixes
    - Several follow-ups and discussions resulting from the talk (e.g., using `cvmfs_info` utility for possible repo health checks)
  - Coincided with [CERN70 community event](https://indico.cern.ch/event/1421217)
- CVMFS: Stratum One operations still flagged with slowness by WLCG during intensive weekend operations
- SDCC: Jira user, group management for new collaboration member
- SDCC: notified by Atlassian that liccensing cost for Jira Cloud [will increase again this year](https://www.atlassian.com/licensing/future-pricing/cloud-advantaged-pricing-10/faqs)
- US ATLAS: help debugging NHC time-out failures on CVMFS repo mounts (atlas-nightlies)
- BNL travel (Geneva, 14-21 Sep)

# 7-13 Sep
- ATLAS: VO, IAM user management, questions, troubleshooting
  - Users continue to try to access retired VOMS service instead of IAM
  - CERN upgraded IAM instances to v1.10.1, enabled auto-enroll for new users to atlas group, may enable secondary account logins
- ATLAS: following up with ADC on job attempts to access the CERN CVMFS 'projects' repo, which is restricted to CERN and fails everywhere else, filling WN logs with errors
- Belle II: reviews of CDB migration Review Board final report and subsequent documentation
- Belle II: KEKCC outage continues due to failed core services after hardware refresh and migration
- Belle II: help with deployment of new local CVMFS repository for grid tools and software development and testing, remote client configuration and access
- Belle II: migrated KEKCC account data from "old" to "new" login systems per [data migration guidelines](https://wiki.kek.jp/pages/viewpage.action?pageId=399474874)
- CVMFS: ATLAS T1 WNs all upgraded to latest client version (2.11.5) during ATLAS-wide job drain (Costin)
  - Very few CVMFS related issues noted after our implemented upgrade procedure (kill processes, wipe cache, upgrade client, reboot)
  - CMS at CERN [have begun finding](https://github.com/cvmfs/cvmfs/issues/3650) the same client issues [we initially reported](https://github.com/cvmfs/cvmfs/issues/3628) for ATLAS jobs
- CVMFS: Stratum One operations still flagged with slowness by WLCG during intensive weekend operations
- CVMFS: NetApp degraded cluster network alert (Sat 7 Sep)
  - Trigerred again on malfunctioning LACP, but does not affect functionality, can be ignored (Joe)
- SDCC: MFA/IPA logins broke over the weekend, preventing all web service login
  - All 3+ generations of Keycloak/IPA/PrivacyIdea service owners and experts have left facility; services now poorly managed and documented
  - Non-host-based certificates generated by the Tomcat IPA service on IDM server (idm01) expired at 3am on 8 Sep 2024
  - Unknown, unmanaged certificate expiration caused IDM service failure, initialized infinite loop of failed re-installation of already installed IPA client
  - Internal IPA CA certificate expired, caused cascading invalidation of service certificates
  - CA, service certificates renewed manually, valid for another two years
  - Full details in [new Jira issue](https://racfjira.atlassian.net/browse/SSO-90)
- SDCC: token self service login issues (independent from MFA issue) found again on pidea-selfserv01 (10 Sep)
  - httpd broken due to badly formatted IPA Python config file, may have been broken for months before being discovered
  - Details documented in [Jira comment](https://racfjira.atlassian.net/browse/SSO-90?focusedCommentId=31811)
- SDCC: request to OSG to add latest HTCondor packages to OSG23 release line, to solve cgroups v2 issue on farm (Costin)
  - Request denied, even though packages are in '23-upcoming channel; deferred to OSG24, to be added in Oct
- SDCC BNLBox: user [reported access issue](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37209), eventually solved with client browser cache clear
- SDCC BNLBox: more login issues [reported](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37221)
- SDCC Jira: cloud site UI for creating new issues is broken: infinite loop on creating new issues, no error or feedback shown to user
  - Issue creation form is missing required field (Assignee) for some users, fails silently
  - New [Atlassian Support request filed](https://support.atlassian.com/requests/JST-1040335)
- SDCC User Services: discussions on Overleaf issues, monitoring development, promtail/logstash/loki message encoding, SSO service issues
- SDCC Web: [ATLAS VO instructions](https://www.sdcc.bnl.gov/experiments/joining-atlas-vo) corrected (again) to point to ATLAS IAM instead of VOMS
- SDCC Web: SDCC Drupal site search function, results broken; fixed by clearing the Drupal site cache (Louis)

# 1-6 Sep
- ATLAS: VO, IAM user management, questions, troubleshooting
- ATLAS: 50k jobs on 5 nodes failed at BNL during 24h span over holiday weekend, cited CVMFS issues
  - CVMFS was functional, working slowly, with system load was > 1500 on all 5 nodes.
  - Killing processes with CVMFS mounts and wiping client cache releived high load instantly
- ATLAS: another issue with WNs upgrade to CVMFS 2.11.5 found with [SQlite catalog errors](https://github.com/cvmfs/cvmfs/issues/3628#issuecomment-2331757572), seems to have caused ~200 ATLAS job failures within one hour
  - Progress being tracked in [a new issue report](https://github.com/cvmfs/cvmfs/issues/3659)
- Belle II: BNL site "banned" (temporarily closed) for new jobs beginning 1 Sep to prepare for dCache upgrade (4 Sep)
  - Testing of local dCache access and transfers after upgrade (multiple times)
- Belle II: troubleshooting of problematic SSH connections from KEKCC access nodes to login nodes after WN EL9 refresh
  - Also confirmed environment setup issues after refresh
- Belle II: confirmed mitigation for Kibana and ElasticSearch on local DIRAC VMs passed cyber security scans and closed vulnerability
- Belle II: set up new local 'belle' repo for testing DIRAC and other software and configuration changes
  - Added to Stratum Zero, Stratum One replica, and file system on experiment write nodes; signing key not yet pushed out to WNs
- Belle II: added cloud auth credentials files for Napoli, EGI test sites to DIRAC certification server (bldiracvm04) for Silvio
- CVMFS: usual debugging and fixing of clients on ATLAS WNs
  - Pushing for Farm team to upgrade v.4->.5 ASAP since .5 should alleviate most issues seen (and .4 is a known bugged version)
- CVMFS: Stratum One operations still flagged with slowness by WLCG during intensive weekend operations
- Jira: issue [opened in March](https://jira.atlassian.com/browse/ACCESS-1781) to properly display user access dates has now been assigned a "Label" (guard-s7) by Atlassian
- US ATLAS: attended IRIS-HEP Institute Retreat, with breakout session focus on data challenge reactions and planning (remote)
- BNL: 1 holiday [2 Sep]

# 26-30 Aug
- ATLAS: VO, IAM user management, DDM user mapping issues, questions, troubleshooting
  - Users are having trouble adding their own certificates to their VO memberships, requires VO admin to add PEM encoded certificate data
  - Changes to user certificate DNs result in new certificates needing to be added to VO memberships, DDM support for remapping account to new DN
- Belle II: Distributed Computing addressing Kibana vulnerability by moving to OpenSearch dashboards this week
- Belle II: conditions database team need additional privileges in OKD, eventually OpenShift, for viewing (or creating) persisitent storage objects
- Belle II: feedback on HSF CDB migration proposals and planning documentation
- CVMFS: reported issue with WLCG Stratum One monitoring and false "NORESPONSE" error reporting
- CVMFS: investigated [reported issue](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37154) with missing read-only mounts on experiment publishing write nodes after last week's data migration
  - Read-only mounts were set up to share the same base mount point as NFS write mounts
  - All mounts needed to be un/re-mounted individually
  - Scripts deployed by farm on nodes to auto-mount [via puppet](https://webdocs.sdcc.bnl.gov/repos/puppet/puppet/src/branch/production/linuxfarm/farm/manifests/resources.pp) don't seem to work
- CVMFS: Stratum One operations still flagged with slowness by WLCG during intensive weekend operations (25 Aug, 17 hours to complete a snapshot on the unpacked repo), still needs attention & possible reconfiguration
- CVMFS: changes to EL7 Puppet code, write nodes, Stratum Zero to create new Belle II repo for local computing team to test and publish new software versions
  - Plans to port changes and fixes to EL8+ repos next week
- CVMFS: more extensive debugging and fixing of clients on ATLAS WNs throughout the week. Plans to roll out new .5 minor version upgrade next week.
  - Addition of memory (+64G memory and guaranteed) to RHEV VM did not help
- sPHENIX: investigation of shift schedule web site and changes [requested by experiment](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37160). Eventually implemented by Dmitry (no details given).
- SDCC User Services: discussions on web authentication, Matomo visitor stat collection issues with Belle II site, PrivacyIdea issues and fixes
- SDCC/sPHENIX: explanation of CVMFS data migration issues in sPHENIX coordination meeting 

# 19-24 Aug
- ATLAS: VO, IAM user management, questions, troubleshooting
  - Users [still being pointed to VOMS Admin](https://cern.service-now.com/service-portal?id=ticket&table=incident&n=INC4033110) instead of IAM for VO registration
  - Corrected [ATLAS TWiki documentation](https://twiki.cern.ch/twiki/bin/view/AtlasComputing/WorkBookStartingGrid) to remove VOMS Admin link, direct users to IAM
  - VO admin privileges have been moved from a VOMS Admin style group/role, to a separate user property in IAM (can be assigned/revoked to/from any user via UI)
- Belle II: fix to rucio-conveyor-submitter systemd service files to re-enable sleep option
  - also temporarily increased threads to account for imbalance in submitter counts between service VMs
- Belle II/CVMFS: plans to create new Stratum Zero repository for Belle II for testing (Michel)
- Belle II: Cyber Security vulnerability reports from Jerome on Kibana installations on two DIRAC VMs
  - Installed by remote Belle II Distributed Computing team; informed of need to upgrade and mitigate [vulnerabilties](https://discuss.elastic.co/t/kibana-8-14-2-7-17-23-security-update-esa-2024-22/364424)
- CVMFS: rescheduled planned downtime to move Stratum Zero repo sync storage from shared GPFS to dedicated CVMFS NAS (22 Aug)
  - Downtime prolonged (>48 hours) due to multiple issues with data syncs and sync options, NFS/GPFS share export options, NFS mount options, nested sphenix calibration data moun complications (on write nodes, dev node, WNs), mounts on write nodes in fstab vs. automount
  - Downtime issues were inaccurately communicated by some as a CVMFS issue
- CVMFS: continued extensive debugging and troubleshooting of ATLAS WN client issues at BNL, provided output and traces to developers, helping other sites with issues
  - New client version [2.11.5](http://ecsft.cern.ch/dist/cvmfs/cvmfs-2.11.5/) [released for testing](https://github.com/cvmfs/cvmfs/issues/3628#issuecomment-2302950814)
  - Network switch reboot caused additional client issues on some WNs, caused HC site auto-exclusion, required manual fixes (to both the clients and the ATLAS HC queue)
- SDCC: meeting with ePIC (Maxim) on potential plans for web presence, solutions from moving from Github, adding federated login
- SDCC: modifications to 'liaison' alias to remove inactive member causing email bounces (John M.) 
- SDCC: Jira administration, modifications to add new staff to users, groups (James L.)
- SDCC User Services: discussions on [ticket for US ATLAS web site enhancements](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37144 ) for institution and member lists (also merged multiple stray RT tickets into original, sPHENIX [web auth requests](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37124), Belle II web site analytics and site issues, monitoring development
- BNL/SDCC: participated in joint staff/lab/CDS management meeting on SDCC reorganization
- BNL: multiple issues with travel and itineraries for upcoming trips (CVMFS workshop, Rucio workshop, B2GM)
- BNL: participated in Brookhaven Lab DEIA pulse survey (by external provider, Perceptyx)

# 11-16 Aug
- ATLAS: VO, IAM user management, questions, troubleshooting
- Belle II: learned that the GS group [decommissioned](https://racfjira.atlassian.net/browse/SIG-4) the OKD instance in which Belle II (and EPIC) were testing CDB migration and planning to migrate from current deployment
  - No consutation with or announcement to Belle II or EPIC, because the instance was owned by ATLAS, and ATLAS T1 reps OKed the decommissioning
  - GS group propose Belle II move to the [RHIC OKD instance](https://console-openshift-console.apps.rcf.bnl.gov/) while OpenShift is prepared for production (possibly next month)
  - Belle II need estimates on cost of OpenShift hosting (still approximately 5% of overall operational cost, but ~2x current RHEV costs)
- Belle II: updates for issues reported against both [CDBWeb](https://gitlab.desy.de/belle2/software/basf2/-/issues/5539) and the [b2conditionsdb tools](https://gitlab.desy.de/belle2/software/basf2/-/issues/8119), both likely related to slowness and time-outs on copying large quantities of IOVs
- Belle II: new comments on [old conditions issue](https://gitlab.desy.de/belle2/software/basf2/-/issues/6019) involving excessive DB requests during payload queries
  - Also updated [task list](https://gitlab.desy.de/belle2/software/cdb/database/-/issues/1) of other outstanding conditions applications issues
- CVMFS: many more ATLAS Alma 9 WN issues reported over weekend, required manual intervention to restore CVMFS client, caches
  - All mounts restored on all WNs except one (acas0909), which had more problems than CVMFS client mounts alone
  - All problematic WNs also logged segfaults on ATLAS software (MemoryMonitor, athena)
  - Details [here](https://github.com/cvmfs/cvmfs/issues/3628#issuecomment-2283916710)
  - Debugging, fixing, testing of many more hung nodes & repos, scripting to test all necessary ATLAS mounts
  - CERN running the same version (upgraded 11.2.3->.4) on RHEL9, starting to see issues on WNs
  - Issues [also found on CMS nodes at CERN](https://github.com/cvmfs/cvmfs/issues/3650) in both Alma 8 & 9
- CVMFS: dedicated NetApp NAS reported degraded cluster network alert, because LACP is not yet properly configured
- CVMFS: Stratum One operations still flagged with slowness by WLCG during intensive weekend operations (11 Aug), still needs attention & possible reconfiguration
  - +64G memory (memory and guaranteed) added to VM, rebooted (13 Aug)
- ITD: [issue with BNL Indico](https://bnlprod.servicenowservices.com/esc?id=ticket&table=incident&sys_id=6cace3d11b8c5290b34c86ebe54bcb06) and BNL users without Indico accounts
- SDCC: User Services discussions on RT ticket handling and user replies, monitoring improvements, VM resource allocation (and fixes), ePIC web site, NX issues with Puppet modules to create user home dirs, [issues with sPHENIX intranet web login](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37124) via BNL AD

## 5-9 Aug
- ATLAS: VO, IAM user management, questions, troubleshooting
- Belle II: scheduled KEK outage concluded, jobs began to refill HTCondor queues 5 Aug at 5 AM
- Belle II: announced to DC and other computing teams the ITD Networking intervention to upgrade firmware on vulnerible Juniper firewall appliances (7 Aug)
- Belle II: problematic conditions access from Trieste continues; escalated to other groups (DC, Software)
  - [New Distributed Computing issue](https://gitlab.desy.de/belle2/computing/distributed-computing/operations/data-production-shift/-/issues/382) opened, linked to [existing CDB issue](https://gitlab.desy.de/belle2/software/cdb/operations/-/issues/1)
- Belle II: sync of conditions payload files from production to test partition, for possible mounting in OKD test instance
  - Current production payload stats: 607,315 files (reg: 596,806, dir: 10,509), 28.87 GB total size
- CVMFS: EL9 client hung on atlas-nightlies repo on ATLAS WN (acas0934), [required manual fix](https://github.com/cvmfs/cvmfs/issues/3628#issuecomment-2269369105)
  - Recommend client upgrade on all WNs (for better cache management), increase of shared cache from 50G
- CVMFS: announced to SDCC liaisons planned downtime to move Stratum Zero repo sync storage from shared GPFS to dedicated CVMFS NAS (8 Aug)
  - Migration canceled as initial sync of repo partition took > 48h
- CVMFS: manually fixed, synced cobbler mirror of EL9 packages so WNs with client v2.11.x can upgrade to 2.11.4 (Costin)
- CVMFS: fix for permissions, modes on cron files managing cache access log rotation; affected AWStats collection for WLCG
- CVMFS: extensive troubleshooting and debugging of several Alma9 clients that had recently been upgraded (9 Aug, with Ofer, Costin, Valentin)
  - Some clients were recoverable; other clients had a defunct core cvmfs2 client that could not be killed, required host reboot via IPMI
  - Debugging details [here](https://github.com/cvmfs/cvmfs/issues/3628#issuecomment-2278340001) and [here](https://github.com/cvmfs/cvmfs/issues/3628#issuecomment-2278520857)
- SDCC: verified that TSM backups for twiki05 (old US ATLAS TWiki site) should be discontinued; VM was [decommissioned](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37106); other old web VMs being checked
- SDCC: Jira administration to grant staff view access to EL7 host update list (required new role, security scheme creation, permission scheme modifications)
- SDCC: investigation of expired CA chains and certificates overwriting valid files on web proxies, invalidating all web sites
  - Someone moved production proxy to personal git branch with expired files
- SDCC: User Services discussion on monitoring, test bed containers and deployment, Git/Puppet modifications to production proxies and testing changes
- BNL: renewed expiring [Active Shooter (TQ-ACTIVESHOOTER)](https://training.bnl.gov/portal/TQ-ACTIVESHOOTER) training

## 29 Jul - 2 Aug
- ATLAS: VO, IAM user management, questions, troubleshooting
  - Verification, clean-up of group manager lists in ATLAS de, phys-hdbs, uk VO groups
  - Disconnect between group managers and group management roles found, clarified (role to be phased out)
- Belle II: KEK annual summer power outage and maintenance ([2-5 Aug](https://ccwww.kek.jp/kekccnl/CN_NEWS/NEWS_n256.html)) 
- Belle II: DESY moving all account services to [MFA protection via OTP](https://it.desy.de/services/mfa/setup_tokens/index_eng.html)
- CVMFS: v2.11.4 [released](https://cvmfs.readthedocs.io/en/2.11/cpt-releasenotes.html); includes fix for widespread client cache manager clean-up issues
- CVMFS: upgraded servers (Stratum Zero and One) to latest minor version
  - Updates coded in Git, Puppet could not be executed because Cobbler for RHEL7 is broken
  - Manual Cobbler updates, sync fixes required:
    - Cobbler CVMFS repository mirror (cvmfs-x86_64-rhel7) manually synced via Cobbler web interface
    - Cobbler replication script on main server (gcemaster02) for syncing with external Cobbler server (extcob02) cloned and modified to sync only target repo (necessary to exclude broken/abandoned reops that otherwise block sync)
    - On Stratum One (cvmfs-s1c), yum caching of broken repo data fixed by cleaning yum, disabling proxy in yum config, rebuilding yum cache
- CVMFS: I/O issues blocking normal operations on Stratum One during weekly garbage collection continue, additional resources likely required
- CVMFS: OSG request to add a new repo (ligo-test.storage.igwn.org) for replication, which I added [five months ago](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36511), [finally closed on OSG's side](https://support.opensciencegrid.org/support/tickets/public/5748d4e1496005e9a81fc5bd30a25d7373ce61cbc7399f9429878d53b823888d) on 1 Aug
- Phisics: participated in social event engagement survey
- SDCC: requested renewal of Cyber conduit [COND0000417](https://bnlprod.servicenowservices.com/sp?id=form&table=u_csmis&filter=&sys_id=64a7b93fdb201700c4a976721f96193d&v=) for facility-wide Puppet server access
  - Vulerabilities found by CS scan that I can not access, details reported to host network admins (also unknown)
- SDCC: User Services discussions on monitoring work, tape backups of old web areas (with Tim), test GLPI deployment and Puppet code, more Drupal issues caused by upgrade
- BNL: Lab-wide "BBQ", 1 Aug 3pm; lab-wide all-hands meeting beforehand canceled (director was ill)
- BNL: vacation days (3: 29-31 Jul)

## 20-26 Jul
- ATLAS: VO, IAM user management, questions, troubleshooting
  - IAM threshold, timing for detecting user contract gaps, triggering user suspensions [being discussed and mitigated](https://github.com/indigo-iam/iam/issues/805)
- ATLAS: CVMFS client issues on ATLAS WN (acas0934) reported by CRC at ADC daily meeting 24 Jul, forwarded by Ivan
  - 'unpacked' repo was hung, fuse mount stuck [details](https://github.com/cvmfs/cvmfs/issues/3628#issuecomment-2248213577)
- Belle II: migrating current [RocketChat](https://chat.belle2.org/) chat service to [Mattermost](https://b2chat2.kek.jp/) 1-5 Aug
- Belle II: migrating current [Confluence](https://confluence.desy.de/display/BI/) service to [XWiki](https://it-xwiki-tst.desy.de/xwiki/bin/view/BI/) mid-Aug
- Belle II: DIRAC version hot-patched to BelleDIRAC 6.0.1 after last week's upgrade to [deprecate file query workflow](https://gitlab.desy.de/belle2/computing/distributed-computing/developments/belledirac/-/merge_requests/926/diffs)
- CVMFS: fixed problem with OSG 'spt' repo garbage collection that triggered warning from CERN central monitoring
- CVMFS: I/O delays on Stratum One continue weekly while garbage collection runs on 'unpacked' and other large repositories
- CVMFS: GPFS server issues [again caused broken NFS mounts](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37038) on CVMFS Stratum Zero, write nodes, and other sPHENIX hosts (Fri, Sat 19-20 Jul)
- SDCC: User Services discussions on monitoring work, Drupal UI issues caused by upgrade
- BNL: vacation days (3: 23,24,27 Jul)
  - Vacation day on 24 Jul interrupted 18 times by separate BNL "exercise" contacts: 4 text messages, 4 mobile phone calls, 4 office phone calls, 3 work emails, 3 personal emails

## 15-19 Jul
- ATLAS: VO, IAM user management, questions, troubleshooting
  - CERN to move IAM deployment from OpenShift to Kubernetes (OpenStack) [likely in September for ATLAS](https://twiki.cern.ch/twiki/bin/view/LCG/WLCGOpsMinutes240711)
- Belle II: DIRAC version upgraded 16 Jul ("BelleDIRAC" v6.0.1), no downtime (except web app during migration)
- Belle II: SuperKEKB schedule announced for run 2024c: 9 Oct - 27 Dec (or shorter depending on budget)
- Belle II: KEKCC replacement schedule announced by CRC coinciding with summer shutdown (2-5 Aug)
  - Data in current HSM tape system will not be available after 2 Aug, migrated to new system afterward
  - CentOS 7 LSF queues closed 30 Aug, to be resumed in new system 2 Sep in RHEL9
- Belle II: continued testing and analysis of problematic conditions requests from Trieste
- Belle II: participated in US Belle II Climate Survey
- BNL: renewed expiring training requirement for Security Programs and Responsibilities (GE-CIA)
- CVMFS: continued debugging and recommendations for ATLAS sites with hung client mounts
  - Best advice is to update clients and allocate enough cache space for ATLAS jobs (>=50G)
- CVMFS: more analysis of continued VM/NAS slowness during repo garbage collection; more adjustments needed
- CVMFS: investigated reports of OSG complaints about CVMFS, plans to [move to Pelican](https://agenda.hep.wisc.edu/event/2175/contributions/30967/attachments/9736/12132/Pelican%20Overview%20-%20HTC24.pdf), at [HTC '24](https://agenda.hep.wisc.edu/event/2175/)
- CVMFS: fixed problem with OSG 'xenon' repo garbage collection that triggered warning from CERN central monitoring
- SDCC: discussions on collaborating with Sasha Alekseev: funding, integrating monitoring work into facility services
- SDCC: discussions on utilizing PD'24 EIC development funds for monitoring improvements
- SDCC: User Services discussions on monitoring work, Mattermost server profile changes for nicknames [due to RT#37025](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=37025), UptimeRobot license issues
- US ATLAS: participated in US ATLAS Climate Survey
- BNL: vacation days (1.5: 18-19 Jul)

## 6-12 Jul
- ATLAS: VO, IAM user management, questions, troubleshooting
  - Issues with IAM suspending valid VO memberships for users with concurrent contract end/start dates
    - IAM [Github issue opened](https://github.com/indigo-iam/iam/issues/805) for instantiating a grace period to avoid such suspensions
  - Discussions with admins, ADC on whether group manager privileges should be permitted to add/remove/modify other group managers
  - IAM VOMS authority pod on OpenShift [went unavailable overnight (8-9 Jul)](https://cern.service-now.com/service-portal?id=outage&n=otg0150883)
    - Caused by host OpenShift/OKD4 [control plane OOM issue](https://cern.service-now.com/service-portal?id=outage&n=OTG0150648)
- Belle II: [HSF CDB panel review](https://indico.bnl.gov/event/24046/) document preparation, review, meeting (11 Jul)
- Belle II: continued troubleshooting of problematic conditions metadata requests from Trieste site proxy
  - Testing of jobs submitted to grid (versus local submission at Trieste) delayed by world-wide issues, but completed successfully with no strain on metadata services
  - Also found problematic period (4:59-5:18am 11 Jul) during which [89k metadata requests from DESY in 19 minutes](https://monitoring.sdcc.bnl.gov/pub/grafana/d/b2cdb-gt-access/client-global-tag-access?orgId=1&from=1720688351289&to=1720689478301) slowed metadata response times [to >40s](https://monitoring.sdcc.bnl.gov/grafana/d/CGFE-OYGz/cdb-ha-monitor?orgId=1&var-host=blcond03.sdcc.bnl.gov&var-host=blcond04.sdcc.bnl.gov&var-proxy=All&var-sv=All&from=1720688351289&to=1720689478301&viewPanel=25)
    - Another similar load from DESY (12:15-12:20 11 Jul) of 22k requests in 5 minutes pushed metadata response times over one minute
- CVMFS: issues over holiday weekend/vacation with NFS/GPFS shared mounts on publishing write hosts (`cvmfswrite0{1,2}`)
  - Hung mounts on write hosts [reported by sPHENIX](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36978)
  - Write hosts could not reach GPFS server (phnxgpfs02.rcf.bnl.gov); all write mounts hung
  - A WN writing calibration data to the repository also reported hung/down (spool0801)
  - After phnxgpfs02 was recovered (actions unknown), mounts on cvmfswrite02 recovered; mounts on cvmfswrite01 did not
    - cvmfswrite01 was rebooted (also unknown)
- CVMFS: continued debugging of STAR repository publication issues on BNL Stratum Zero (RT#[36960](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36960))
  - Issues with large files/number of files, nested catalogs (followed up with Yuri)
- CVMFS: continued discussion and debugging of ATLAS WN repo hangs in [CVMFS Gitlab bug report](https://github.com/cvmfs/cvmfs/issues/3628)
  - Another BNL shared pool (spool) WN hang reported on ATLAS repos (RT#[36960](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36993)
    - Problem and mitigation detailed in [Github issue](https://github.com/cvmfs/cvmfs/issues/3628#issuecomment-2215522356)
  - Another BNL issue reported on acas0720 in the [SDCC ATLAS MM channel](https://chat.sdcc.bnl.gov/sdcc/pl/mo5tdqqf8j85ppjb657nonfgnr), but node was rebooted before I could investigate
    - Reboot or prior crash caused orphaned inodes, CVMFS client removal of broken, empty cache files, and cache DB rebuild
  - More client issues at AGLT2, possibly due to local cron interference or exceedingly short autofs timeout (45s)
- SDCC: ACL modification of internal Grafana instance [htcondor dashboard area](https://monitoring.sdcc.bnl.gov/grafana/dashboards/f/W7WwOH7mk/htcondor) to permit editing for Ivan
- BNL: vacation days [1.5: 11-12 Jul]

## 1-5 Jul
- ATLAS: VO, IAM user management, questions, troubleshooting
  - Nagoya user [reported broken VOMS access](https://cern.service-now.com/service-portal?id=ticket&table=incident&n=INC3956017) since switchover to IAM
  - Some users having problems with expired VO memberships despite valid contracts; require manual fixes in IAM
- ATLAS: continued investigation of CVMFS client issues at other sites (AGLT2, NET2)
- Belle II: troubleshooting of problematic conditions metadata requests from Trieste site proxy continues
  - Squid reconfiguration, redeployment (as Frontier Squid) did not solve issues as thought previously
  - After much testing, all problematic requests seem to come only from jobs by one specific user
  - Metadata response times during user's jobs spike to 30s; all other jobs from the site cause no load 
- Belle II: HTCondorCE at NGI_DE [seems finally fixed](https://ggus.eu/index.php?mode=ticket_info&ticket_id=164242) and ready for token requests
- Belle II: user support for gbasf2 and grid environment issues
- Belle II: Distributed Computing support for DIRAC ELK monitoring issues on bldiracvm06
- Belle II: SuperKEKB shut down after final cosmic run on 1 Jul, completing 2024ab data taking
  - SuperKEKB to resume operations in October for 2024c
- CVMFS: troubleshooting hung Stratum Zero publication transaction on STAR repository (RT#[36960](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36960))
  - Transaction stuck/hung since 2 Apr, no other repos affected
  - First clear attempt failed with [missing lock file in transaction](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36960#txn-1109739)
  - Subsequent sync during publication affected by user changing files in publication area during transaction, similar changes during previous transaction likely caused initial hang
- CVMFS: discussions with WLCG Stratum Operations teams regarding irrelevant "critical" alerts at replica sites for source repo issues
- SDCC: Indico group/ACL modifications for Luisa, Tony
- SDCC, Physics: discussions on use of project code 27167 for EIC (not possible for me to charge 100% FTE to this project)
- SDCC: User Services discussions on monitoring (Prometheus high availability and federated deployment)
- SDCC: web support for expired certificate on backend server for Physics BMX web server (RT#[36965](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36965)) 
- BNL: holiday [1: 4 Jul], vacation day [1: 5 Jul]

## 24-28 Jun
- ATLAS: VO, IAM user management, questions, troubleshooting
  - ATLAS software tutorial [24-28 Jun](https://indico.cern.ch/event/1412088/) (means more new VO registrations)
- Belle II: more trouble with conditions metadata reqeusts from Trieste proxy (proxy.ts.infn.it)
  - 46k requests in 19 minutes (24 Jun 10:19-10-38 EDT) brought metadata service response time from a few ms avg to 40s at peak (10:26 EDT)
    - Service alert triggered in Grafana, which sent alerts to the 't1-belle2-cdb' mail alias (recipients: me + RT)
      - RT rejected incoming email from Grafana; I removed the alias from the Grafana alerts, which now emails only me directly
  - New Squid config deployed at Trieste, seems to alleviate all issues, suggesting previous config prevented caching
- Belle II: DIRAC Workshop in Lyon last week included [tutorial on DIRAC X install](https://github.com/DIRACGrid/diracx-charts/tree/master/k3s) via [K3s](https://docs.k3s.io/)
- Belle II: further edits and polishing of HSF CDB proposal and roadmap documents, to be reviewed via charter next week
- CVMFS: further tuning of Stratum One VM and attached A400 NAS to alleviate I/O bottlenecks
  - With Joe: added CPU, doubled swap on VM
- CVMFS: added to [central CVMFS Github](https://github.com/cvmfs/cvmfs/issues/3615) issue on ATLAS pilot, site caches, and other client problems
  - Further collaboration with CVMFS devs (Jakob, Valentin) and sites (AGLT2, NET2, SWT2) to debug site client issues
- CVMFS: responded to 27 Jun ATLAS "News of the Day" to explain "1% unavailability for cvmfs.fnal.gov and cvmfs.racf.bnl.gov" related to broken services at RAL, not at FNAL or BNL site replicas
  - Also requested correction of ATLAS monitoring deprecated 'cvmfs.racf.bnl.gov' service alias to 'cvmfs.sdcc.bnl.gov'
- ITD: ITD/SDCC Network meeting on analytics with Prometheus (Louis, Mark, Nick, Ofer)
- ITD: created Sympa account to continue managing legacy [RACF Frontier email list](https://lists.bnl.gov/sympa/review/racf-frontier-l) after transition from mailman list server
  - Opened ITD Help ticket (INC0193929) on broken list archives
    - Migrated archive was broken; fix required an archive rebuild (Dennis)
- Physics: Physics Department Day of Reflection on Safety Meeting (26 Jun)
- SDCC: final edits and updates to WBS docs (milestones, accomplishments, challenges)
- SDCC: more edits and updates to PD request '25 EIC docs (proposal and slides)
- SDCC: User Services group discussions on Prometheus deployment and monitoring services, NX testbed issues, SSH key upload issues
- SDCC: staff appreciation pizza luncheon (26 Jun)
- US ATLAS: '24 OTP review and edit (T1, cloud ops)
- BNL: completed and submitted annual performance goals
- BNL: vacation days [2] (27-28 Jun)

## 15-21 Jun
- ATLAS: provided additional feedback to Collaboration Board on grid access policy document, AUP policy
- ATLAS: [Git merge request](https://gitlab.cern.ch/atlas-sit/librarian/-/merge_requests/29) to clean up Git keyword blacklist finally merged into production
- ATLAS: VO, IAM user management, questions, troubleshooting
  - [One specific issue](https://cern.service-now.com/service-portal?id=ticket&table=incident&n=INC3934249) with concatenating multiple CERN accounts into a VO membership required an API fix via curl (Petr)
  - Other issues with VO memberships and Rucio mappings for service accounts, which must be assigned to user records but can not duplicate email address values
- ATLAS: CERN IAM was [upgraded](https://github.com/indigo-iam/iam/commits/v1.9.0.rc.20240610/?since=2024-01-01), main fixes to AUP features in IAM dashboard
- ATLAS: expressed exploratory interest in [Documentation Coordinator position](https://cern.ch/ckbea), but can not self-nominate due to lack of time and ATLAS FTE
- ATLAS: completed Strategic Collaboration Issues survey
- Belle II: checks and debugging of conditions requests coming from Trieste and overloading the metadata service (Saturday)
  - New [DESY Gitlab issue created](https://gitlab.desy.de/belle2/software/cdb/operations/-/issues/1) to track the problem
- Belle II: participated in [Belle II Mental Wellbeing Workshop](https://indico.belle2.org/event/12235/)
- Belle II: spokesperson election concluded, with highest ranked candidate, Florian Bernlochner, to be ratified by next week
- Belle II, SDCC: VMs for B2 Rucio (blrucio0{3,4}) were reduced to minimum memory by RHEV and ran out of RAM, VMs reconfigured for more memory
- Belle II: follow-ups with Tadeas (calibration) on failed alignment on prompt calibration at BNL, but working at KEKCC
- CVMFS: manual intervention over weekend to manually force check ATLAS replica to clear WLCG "warnings" on repo (Sunday, 11 hours)
- CVMFS: follow-ups with developers on ATLAS pilot checks and issues
- CVMFS: found and reported replication issues with source for OSG's OASIS and all EGI repositories
  - OSG repos were broken/misconfigured and fixed; EGI repos hosted at RAL are unavailable as the entire replica is broken
  - RAL outage causing needless "warning" and "critical" alerts on downstream replicas from WLCG monitoring
- CVMFS: created [Github issue](https://github.com/cvmfs/cvmfs/issues/3615) to centrally track ATLAS debugging efforts
- SDCC: multiple iterations on additions and edits for EIC FY'25 PD proposal doc and presentation
- SDCC: WBS 2.3.1 CVMFS milestone additions and edits to document and scrubbing slides
- SDCC: User Services group discussions on IAM admin and issues, EL7 upgrade inventory sheet, Prometheus deployment, web and docs sites updates, NX testbed issues, SSH key upload issues, user account issues (e.g., [1](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36906), [2](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36915))
  - Discussion and debugging of Puppet deployment and failures on EL8 for test NX campus server (nx-campus01) (Saroj, Joe, Mark, Jason)
- SDCC: proposal for contract work for A. Alekseev on updating monitoring infrastructure (Alexei, Ofer, Louis)
- SDCC: EIC/EPIC collaborative tools discussions and [meeting on Friday](https://indico.bnl.gov/event/23988/)
- SDCC: staff position interviews [2]
- BNL: holiday [1]
  - Observed Juneteenth holiday by reading about its history and origins, watching related content (e.g., PBS's "[Juneteenth: Faith & Freedom](https://www.pbs.org/video/juneteenth-faith-freedom-ap4dcr/)"), discussing with colleagues and friends
- BNL: vacation day [1] (tried to take on 21 Jun but could not)

## 10-14 Jun
- ATLAS: VO, IAM user management, questions, troubleshooting
  - More issues found with IAM and missing functionality (e.g., [account nickname not set](https://github.com/indigo-iam/iam/issues/770), accounts not being synced to Rucio, memberships incorrectly suspended due to unknown contract termination dates) 
- ATLAS: debugging and [followed up with CVMFS developers and experts](https://codimd.web.cern.ch/HEqxj15dSUGi_CUkGk-u6w) on repeated ATLAS pilot reports of CVMFS issues, to be discussed further at CERN
  - [Another BNL WN ticket](https://ggus.eu/index.php?mode=ticket_info&ticket_id=166868) closed without much follow-up by ATLAS
  - Comments and discussion on [new updates to CVMFS checks in the ATLAS pilot](https://github.com/PanDAWMS/pilot3/pull/131/) (Paul N.)
    - Discussion moved to [CERN Jira](https://its.cern.ch/jira/browse/ATLASPANDA-998)
- Belle II: updated expiring DESY account, password
- Belle II: voting for incoming spokesperson to replace K. Trabelsi after current term
- Belle II: continued presentations and discussions on replacing present conditions database deployment with HSF implementation (Ruslan)
  - HSF CDB roadmap review, revisions, additions to new sections on future development and migration
- Belle II: new investigations into excessive conditions request traffic from Trieste WNs via site cache
- CVMFS: slow replcation times on Stratum One caused by repo source garbage collection, slowed by NAS connections
  - With Joe, testing changes to NetApp A400 performance tuning, increasing performance level to ["ultra" or "extreme"](https://docs.netapp.com/us-en/netapp-solutions/xcp/xcp-bp-performance-tuning.html)
- CVMFS: manual garbage collection on ATLAS nightlies and other repos to stop " CRITICAL" and "WARNING" monitoring complaints from CERN ([SLS](https://monit-grafana.cern.ch/d/plTtqczZz/sls-details?orgId=17&var-services=cvmfs_stratum1mon_bnl), [WLCG](http://wlcg-squid-monitor.cern.ch:80/cvmfsmon/api/v1.0/all&format=details&server=bnl))
- SDCC: review, follow-ups to Alexei's FY25 PD proposal; discussions on monitoring, prototpyes, required FTE & hardware
- SDCC: staff position interviews [1]

## 2-8 Jun
- **Belle II: [Belle II General Meeting (B2GM)](https://indico.belle2.org/event/11828/) (KEK, Tsukuba, Japan)**
  - Physics talks dominated by [sudden beam loss (SBL)](https://indico.belle2.org/event/11828/contributions/75666/attachments/28829/42573/20240603B2GM-SBL.pdf) and its possible causes and consequenses
  - First visit to KEKCC facilities (4 Jun)
  - KEK announced annual site-wide power outage 2-5 Aug; BelleDIRAC will remain operational
    - Tape access stopped in Aug for data migration; LSF user batch queue closes 30 Aug for sync, migration
    - Details on computing affects [here](https://indico.belle2.org/event/11828/contributions/75559/attachments/29030/42887/ComputingReport-B2GMJun2024.pdf) (p15)
  - [Initial official proposal to experiment](https://indico.belle2.org/event/11828/contributions/77758/attachments/28893/42674/b2%20hsf%20cdb%202024.pdf) for implementation of HSF conditions database solution, with subsequent questions and technical discussion
- ATLAS: repeated reports of failed jobs due to unavailable CVMFS repos [(GGUS #166868 re-opened)](https://ggus.eu/index.php?mode=ticket_info&ticket_id=166868)
  - Three WNs reported with issues (acas0705, acas0965, acas1036); all investigated, no issues found with any repos on any of these nodes
- ATLAS: switch-over from VOMS Admin to IAM on 3 Jun
  - ATLAS "team" and "alarm" groups [lost GGUS privileges due to IAM move](https://ggus.eu/index.php?mode=ticket_info&ticket_id=167033)
- ATLAS: VO, IAM user management, questions, troubleshooting
  - Had to ask again to remove BNL non-VO admins (Mark, Tommy, Louis) from VO admin group and notification lists (done now, finally)
  - Valid VO memberships are being suspended by IAM due to incorrect membership parameter actions (DISABLE_ACCOUNT) & states (PENDING_SUSPENSION)
  - Current workaround is to change the membership state via [complex token CLI operations](https://codimd.web.cern.ch/muIh9zERRbSoIKK-Z4Qwjw#Using-IAM-API), which is a non-starter for some VO admins
- Belle II: issues with reduced job submission and held jobs continue
- Belle II: issues with specific user requests for conditions timing out
- SDCC: renewed expiring [Working Safely in the 725 SDCC Data Center (AO-SDCC725)](https://training.bnl.gov/Portal/AO-SDCC725) training
- SDCC: feedback/additions to ATLAS Subsystems hardware allocation list
- SDCC: US ATLAS web site [stopped working](https://rt.racf.bnl.gov/rt/Ticket/Display.html?id=36859 ). VM hosting the site was turned off, had to be restarted
- WLCG/EGI: test of [new EGI Helpdesk demo site](https://helpdesk-dev.ggus.eu/) for [GGUS replacement (Zammad)](https://indico.cern.ch/event/1369601/contributions/5917197/attachments/2856680/4996639/WLCG_Helpdesk_WLCG_Workshop_15.05.24-1.pdf)

## 27-31 May
- **Belle II: [Pre-B2GM Distributed Computing Workshop](https://indico.belle2.org/event/11929/) (KEK, Tsukuba, Japan)**
- ATLAS: VO user management, questions, troubleshooting
- ATLAS: feedback to Collaboration Board on updates to ATLAS Grid access policy document
- ATLAS: another report of failed jobs at BNL to due broken CVMFS repos that [do not appear to have been broken](https://ggus.eu/index.php?mode=ticket_info&ticket_id=166868)
- ATLAS: [Git merge request](https://gitlab.cern.ch/atlas-sit/librarian/-/merge_requests/29) to clean up Git keyword blacklist [still not merged after 4 years](https://gitlab.cern.ch/atlas-sit/librarian/-/merge_requests/29#note_8022704)
- Belle II: continued investigation of jobs submission in 2-day waves, from queue max (5k) to near 0
- Belle II: continued review & revision of proposals and slides for conditions database migration to new deployment in ODK/OpenShift

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
- BNL: tried to attend virtual DEI workshop (DEI Seminars and Workshops: Navigating Psychological Safety Hazards) but Zoom was broken (reported)
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
  
