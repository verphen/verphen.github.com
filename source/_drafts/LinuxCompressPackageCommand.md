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


> 压缩命令
     。zip  <压缩后的文件名>   <源文件>          - - 压缩文件
         zip -r   <压缩后的文件>     <源目录>          - -压缩目录
         unzip <压缩文件>      - - 解压( -d dir 解压到其他目录)
     。tar -cvf   <打包文件名>      <源文件>     - - 压缩文件
          -c      创建 | 打包
          -C, --directory=DIR        改变(解压)目录；change to directory DIR
          -v      显示过程
          -f      指定打包后的文件名

          -x      解压打包
          -z      压缩以打包文件为.tar.gz
                   $ tar -zcvf   <压缩后的文件名.tar.gz>    <待压缩的文件名1  待压缩的文件名2  ...>
          -t      测试压缩文件，便于查看压缩文件里面的目录和文件
                  $ tar -ztvf   <压缩后的文件名.tar.gz>            - - 参数v便于显示压缩文件内容

          -j       压缩已打包文件为.tar.bz2
                    $ tar -jcvf   <压缩后的文件名.tar.bz2>    <待压缩的文件名>

         tar -zxvf test.tar.gz -C /usr           - - 通过参数大写C解压test.tar.gz到/usr目录


unzip *.zip  解压zip文件
gzip filename;压缩文件(解压缩：gzip -d filename)

