# Tutorial StorCli command pada Linux

<a href="https://jovial.my.id">
  Test Link
</a>

### Lihat Physical Disk yang ada pada raid controller 
/opt/MegaRAID/storcli/storcli64 /cX /eall /sall show

### Lihat Virtual Disk yang ada pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX/vall show

### Lihat foreign configuration pada raid controller
/opt/MegaRAID/storcli/storcli64 /cX/fall show

### Import foreign configuration apabila ada foreign configuration yang terbaca
/opt/MegaRAID/storcli/storcli64 /cX/fall import
