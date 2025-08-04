# Tutorial StorCLI pada Linux
Storage Command Line Tool (StorCLI) adalah tools atau command line atau software yang digunakan untuk me-manage produk MegaRaid Raid Controller.

### Lihat Physical Disk yang ada pada raid controller 
/opt/MegaRAID/storcli/storcli64 /cX /eall /sall show

### Lihat Virtual Disk yang ada pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX/vall show

### Lihat foreign configuration pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX/fall show

### Import foreign configuration apabila ada foreign configuration yang terbaca
/opt/MegaRAID/storcli/storcli64 /cX/fall import
