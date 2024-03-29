# BNL SDCC S&T Group
Work logs for the S&amp;T Group in the SDCC at BNL.

## Meetings
- ATLAS ADC (weekly)
- Belle II BNL Software & Computing (weekly, BNL, remote)
- Belle II Conditions Database Coordination (monthly, remote)
- Belle II Distributed Computing (weekly, KEK, remote)
- CVMFS Coordination (monthly, CERN, remote)
- Rucio Token Working Group (monthly, CERN, remote)
- SDCC ATLAS Tier 1 (weekly, remote)
- SDCC Liaison (monthly)
- SDCC Services & Tools (weekly)
- SDCC Staff (monthly)
- SDCC Technical (monthly)
- SDCC User Services section (weekly)
- US ATLAS Computing Facility (weekly, remote)
- US ATLAS Facilities Research & Development (bi-weekly, remote)
- WLCG AuthZ Working Group (bi-weekly, remote)
- WLCG Frontier Meeting (remote)
- WLCG Unified Token (GUT) Profile Working Group (monthly, remote)

## 25-29 Mar 2024
- ATLAS: continued investigation of BNL & ATLAS-wide pilot failures related to reported CVMFS client mount issues
- ATLAS: edited software tutorial documentation to clarify references to VO membership
  - https://gitlab.cern.ch/atlas-sw-git/atlassoftwaredocs/-/merge_requests/693
- ATLAS: VO user management, questions, extensive troubleshooting
  - Investigation of reported compromised identity ("Mark Rosenbaum") & attempts to acquire VO membership (EGI-CSIRT, Mario)
  - Issues with user VO membership expiration caused by ATLAS IAM upgrade, nullifying VO AUP signing dates
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
  
