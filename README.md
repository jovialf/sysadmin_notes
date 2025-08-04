### Tutorial StorCli command pada Linux

# Lihat Physical Disk yang ada pada raid controller 
/opt/MegaRAID/storcli/storcli64 /cX /eall /sall show

# Lihat Virtual Disk yang ada pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX /eXXX /sX set good force
