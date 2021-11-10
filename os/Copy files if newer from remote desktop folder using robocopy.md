# Copy files if newer from remote desktop folder using robocopy

```powershell
$source = "\\tsclient\<your-remote-access-disk>\<your-folder>"
$destination = "<remote-local-disk>:\<remote-local-folder>"
robocopy $source $destination /e /xo /mt
```

parameters:

- /e: Copies subdirectories. This option automatically includes empty directories.
- /xo: Excludes existing files older than the copy in the source directory.
- /mt[:n]: Creates multi-threaded copies with n threads. n must be an integer between 1 and 128. The default value for n is 8.
  
---

From:

- [Microsoft Doc / robocopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy)