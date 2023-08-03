# Linux.NFS.Agnostic

SCOM Linux NFS Mount Point Management Pack helps you to discover the NFS Mounts on your Linux Machines.

## Pre-Req:
1. The MP is tested only with RedHat distro.
2. The MP supports only NFS 4. If you are using NFS 2 or 3, then edit the commands to reflect your version in the MP. Below is an equivalent shell command for testing.

`/bin/sh -c "df -kTt nfs4 | awk -F ' nfs4' '{printf \"\\\"%s\\\"\",\$1} {print \$2}' | awk -F\\\" '{for(i=1;i<=NF;i+=2)gsub(/[[:blank:]]/,\",\",\$i)}1' OFS=\\\" | awk -F \",\" '{print \$1 \",\" \$3 \",\" \$9}' | tr -d \"\\\"\" | tail -n +2"`
  
4. Install the UNIX/Linux Authoring MP (https://systemcenter.wiki/?Get-ManagementPack=Unix.Authoring.Library&Version=7.3.1.2).


## Version History:

* 1.0.0.1 - Initial Release - Supports NFS Mount Points with white spaces in the name
