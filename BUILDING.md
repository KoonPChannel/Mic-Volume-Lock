# Building QuicklyzXD Mic Volume Lock

Prerequisite: **Go 1.23+**.

No external Go dependencies are required. Target: Windows 10/11 x64.

### On Windows (CMD)

```bat
set GOOS=windows
set GOARCH=amd64
set CGO_ENABLED=0
go build -trimpath -ldflags="-H windowsgui -s -w" -o QuicklyzXD_Mic_Volume_Lock.exe .
```

### On Linux/macOS

```sh
GOOS=windows GOARCH=amd64 CGO_ENABLED=0 go build -trimpath -ldflags='-H windowsgui -s -w' -o QuicklyzXD_Mic_Volume_Lock.exe .
```

This build produces an unsigned executable. Compilation alone does not prove runtime functionality.