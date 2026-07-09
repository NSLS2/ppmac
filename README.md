# This serves as the top level source to build Power PMAC ioc binary for NSLS-II Power PMAC systems.

Changes July '26
Refactored database files and removed stream device.
Changes to subsitution files in refactor:

motor.substitutions - remove Mtr from PVs
motorstatus.substitions - Move second block Sys Dev to SYSC DEVC in first block, delete second block, change P0 to M0
pmacStatus.substitutions - change M0 to P0
cs.substitutions  - change motor.db to cs_motor.db, change all P0 to M0, change SPORT to PORT, remove Mtr from PVs

Remove these from st.cmd 
dbLoadTemplate("${TOP}/db/pmac_asyn_motor.substitutions")
dbLoadTemplate("${TOP}/db/pmacaux.substitutions", PORT=P0)
dbLoadTemplate("${TOP}/db/pmac_physical_limit.substitutions", PORT=P0)
dbLoadRecords("${PPMAC}/db/kill_all.db","Sys=${SYS},Dev={MC:05},Port=P0")
