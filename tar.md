Here’s an overview of how to use the tar utility in Linux/Unix.
tar (short for tape archive) is used to create, extract, and manipulate archive files.

⸻

Basic Syntax

tar [OPTIONS] [ARCHIVE_FILE] [FILES...]

	•	OPTIONS: Flags that control what tar does.
	•	ARCHIVE_FILE: The archive you want to create or extract.
	•	FILES…: The files or directories to include.

⸻

Common Options

Creating Archives
	•	-c → Create a new archive.
	•	-f → Specify the archive filename (must follow directly).
	•	-v → Verbose (list files being processed).
	•	-z → Compress with gzip (.tar.gz or .tgz).
	•	-j → Compress with bzip2 (.tar.bz2).
	•	-J → Compress with xz (.tar.xz).

Example: Create a compressed archive

tar -czvf archive.tar.gz /path/to/files


⸻

Extracting Archives
	•	-x → Extract files.
	•	-f → Specify the archive filename.
	•	-C → Extract into a specific directory.

Example: Extract a .tar.gz into /tmp

tar -xzvf archive.tar.gz -C /tmp


⸻

Viewing Archives
	•	-t → List contents without extracting.

Example:

tar -tvf archive.tar.gz


⸻

Appending/Updating
	•	-r → Append files to an archive (not with compression).
	•	-u → Update files in an archive if they are newer.

Example:

tar -rvf archive.tar newfile.txt


⸻

Common Patterns
	•	Create archive: tar -cvf archive.tar file1 dir1
	•	Create gzip archive: tar -czvf archive.tar.gz file1 dir1
	•	Extract gzip archive: tar -xzvf archive.tar.gz
	•	List contents: tar -tvf archive.tar.gz

⸻

👉 Quick mnemonic: create, extract, table (list), file, verbose, z (gzip).

⸻

Would you like me to make you a cheat sheet table with the most used tar commands and examples all in one view?
