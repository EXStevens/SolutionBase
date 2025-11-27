---
id: Compression
title: Compression (Tar, Bzip2, Gzip, Zip)
---

# Compression (Tar, Bzip2, Gzip, Zip)
*Varribles in Code are marked as CAPITAL LETTERS.*
## `tar`
:::tip
Command parameter structure:
'**tar** (usually -Action+Format+f)'
:::

### Query
```Bash
# List File(s) in the Archive
tar -tf ARCHIVE
# List File(s) in the Archive & Permissions/Owner/Date
tar -tvf ARCHIVE
```

### tar
```Bash
tar -cf FILE.tar FILE
tar -xf FILE.tar ASSIGNED_FILE (-C OUTPUT_DIRECTORY)
```

### tar.GZ [`-z`]
```Bash
tar -czf FILE.tar.gz FILE
tar -xzf FILE.tar.gz ASSIGNED_FILE (-C OUTPUT_DIRECTORY)
```

### tar.BZ2 [`-j`]
```Bash
tar -cjf FILE.tar.bz2 FILE
tar -xjf FILE.tar.bz2 ASSIGNED_FILE (-C OUTPUT_DIRECTORY)
```

### tar.XZ [`-J`]
```Bash
tar -cJf FILE.tar.xz FILE
tar -xJf FILE.tar.xz ASSIGNED_FILE (-C OUTPUT_DIRECTORY)
```

<details>
<summary><strong>Explanation of Parameters</strong></summary>

- **-c**: Create  
- **-x**: Decompress  
- **-f**: Followed by the files to be processed  
- **-t**: Show contents in the archive  
- **-r**: Add file(s) to a tarball  
- **-u**: Update files in the archive  
- **-v**: Show all progress  
- **-f**: Assign an archive  
- **-C**: Change to a specific directory  
- **-P**: Preserve properties and permissions  
- **-N**: Save only files newer than `DATE-OR-FILE`  
- **--exclude=FILE**: Exclude FILE  
- **--remove-files**: Add then remove source files

</details>


## `Bzip2`
:::warning
If need to RETAIN the original file(s), add parameter "-k" or "--keep"
:::
```Bash
bzip2 -c FILE
bzip2 FILE.bz2
```

## `Gzip`
:::warning
Single file only.
Will NOT retain the original file(s)!
:::
```Bash
gzip FILE.gz
gunzip FILE.gz
```

## `Zip`

```Bash
zip FILE.zip FILE
unzip FILE.zip
```