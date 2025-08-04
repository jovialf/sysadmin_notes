# Tutorial StorCLI pada Linux
Storage Command Line Tool (StorCLI) adalah tools atau command line atau software yang digunakan untuk me-manage produk MegaRaid Raid Controller.

### Lihat Raid Controller yang tersedia
/opt/MegaRAID/storcli/storcli64 show all
```
-------------------------------------------------------------------------------
Ctl Model              Ports PDs DGs DNOpt VDs VNOpt BBU sPR DS  EHS ASOs Hlth
-------------------------------------------------------------------------------
  0 LSI3108MegaRAID        8   0   0     0   0     0 N/A On  1&2 Y      3 Opt
  1 LSIMegaRAID9361-8i     8   2   1     0   1     0 Opt On  1&2 Y      2 Opt
-------------------------------------------------------------------------------.
```

### Lihat Physical Disk yang ada pada raid controller 
/opt/MegaRAID/storcli/storcli64 /cX /eall /sall show

### Lihat Virtual Disk yang ada pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX/vall show

### Lihat foreign configuration pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX/fall show

### Import foreign configuration apabila ada foreign configuration yang terbaca
/opt/MegaRAID/storcli/storcli64 /cX/fall import
