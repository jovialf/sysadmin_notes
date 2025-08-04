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

Contoh melihat physical disk yang terpasang pada raid controller 1
```
# /opt/MegaRAID/storcli/storcli64 /c1 /eall /sall show

---------------------------------------------------------------------------------------
EID:Slt DID State DG       Size Intf Med SED PI SeSz Model                     Sp Type
---------------------------------------------------------------------------------------
252:0    10 Onln   0 464.729 GB SATA SSD Y   N  512B Samsung SSD 870 EVO 500GB U  -
252:1    11 Onln   0 110.827 GB SATA SSD N   N  512B ADATA SU650               U  -
---------------------------------------------------------------------------------------
```

### Lihat Virtual Disk yang ada pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX/vall show

Contoh melihat virtual disk yang dikonfigurasi pada raid controller 1
```
# /opt/MegaRAID/storcli/storcli64 /c1/vall show

---------------------------------------------------------------
DG/VD TYPE  State Access Consist Cache Cac sCC       Size Name
---------------------------------------------------------------
0/0   RAID1 Optl  RW     Yes     RAWBD -   ON  110.827 GB
---------------------------------------------------------------
```

### Lihat foreign configuration pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX/fall show

Contoh melihat foreign configuration yang dikonfigurasi pada raid controller 1, pada kondisi ini tidak ada foreign configuration yang terbaca.
```
# /opt/MegaRAID/storcli/storcli64 /c1/fall show
CLI Version = 007.3306.0000.0000 Feb 21, 2025
Operating system = Linux 5.15.0-119-generic
Controller = 1
Status = Success
Description = Couldn't find any foreign Configuration

Total Foreign PDs = 0
```

### Import foreign configuration apabila ada foreign configuration yang terbaca
```
/opt/MegaRAID/storcli/storcli64 /cX/fall import
```

### Set disk menjadi Unconfiguration Good
/opt/MegaRAID/storcli/storcli64 /cX /eXXX /sX set good force.
Dimana eXXX adalah enclosure id dan sX adalah slot id. Yang dapat dilihat menggunakan command /opt/MegaRAID/storcli/storcli64 /cX /eall /sall show pada kolom EID:Slt.
Contoh penggunaanya adalah 
```
/opt/MegaRAID/storcli/storcli64 /c1 /e252 /s0 set good force
```

### Melihat proses rebuild raid pada disk.
```
/opt/MegaRAID/storcli/storcli64 /cX /eXXX /sX show rebuild
```
