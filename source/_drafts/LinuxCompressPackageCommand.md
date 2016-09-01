title: Linux压缩与打包
tags:
---

tar(bsdtar): manipulate archive files
First option must be a mode specifier:
  -c Create  -r Add/Replace  -t List  -u Update  -x Extract
Common Options:
  -b #  Use # 512-byte records per I/O block
  -f <filename>  Location of archive
  -v    Verbose
  -w    Interactive
Create: tar -c [options] [<file> | <dir> | @<archive> | -C <dir> ]
  <file>, <dir>  add these items to archive
  -z, -j, -J, --lzma  Compress archive with gzip/bzip2/xz/lzma
  --format {ustar|pax|cpio|shar}  Select archive format
  --exclude <pattern>  Skip files that match pattern
  -C <dir>  Change to <dir> before processing remaining files
  @<archive>  Add entries from <archive> to output
List: tar -t [options] [<patterns>]
  <patterns>  If specified, list only entries that match
Extract: tar -x [options] [<patterns>]
  <patterns>  If specified, extract only entries that match
  -k    Keep (don't overwrite) existing files
  -m    Don't restore modification times
  -O    Write entries to stdout, don't restore to disk
  -p    Restore permissions (including ACLs, owner, file flags)





tar命令(参数)
	
	$ tar -czf <dist.tar.gz> <dist_dir> 	# 压缩
	$ tar -zxf 	<dist.tar.gz> [-C <dist_dir>]	#  解压到当前目录(-C解压到指定目录)
	$ tar -jxvf <dist.tar.bz2> 	# 解压tar.bz2后缀文件
	$ tar -zcvf <dist.tar.gz>  --exclude <Skip files> <source_dir>  # 跳过文件压缩

unzip *.zip  解压zip文件
gzip filename;压缩文件(解压缩：gzip -d filename)