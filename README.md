# tce-kcd-workshop

## Step 1: Install TCE

Latest TCE version as this writing is `v0.11.0`

Installation instructions:

- TLDR;
- [MacOS](#macos)
  - Install with Homebrew
  - Install with tar ball manually
- [Linux](#linux)
  - Install with Homebrew
  - Install with tar ball manually
- [Windows](#windows)
  - Install with Chocolatey
  - Install with zip manually

We are skipping installation from TCE source code as that takes quiet some time

### TLDR; Manual installation

Manual installation on Mac/Linux/Windows

- Download the release tarball based on your operating system.
- Unpack the release tarball.
  - Unzip on Windows.
  - `tar zxvf <release-tarball-path>` on Mac/Linux.
  - Enter the directory of the unpacked release.
  - Run the install script.
    - `.\install.bat` on Windows as Administrator.
    - `./install.sh` on Mac/Linux

### MacOS

#### Install with Homebrew (`brew`)

Ensure [Homebrew](https://brew.sh/) is installed

```bash
brew install vmware-tanzu/tanzu/tanzu-community-edition

${HOMEBREW_EXEC_DIR}/configure-tce.sh
```

#### Install with tar ball manually

```bash
# download the tar ball with your favorite browser or something like wget or curl
wget https://github.com/vmware-tanzu/community-edition/releases/download/v0.11.0/tce-darwin-amd64-v0.11.0.tar.gz

# extract the tar ball using Finder or a CLI tool like tar
tar xvzf tce-darwin-amd64-v0.11.0.tar.gz

# cd into the extracted directory
cd tce-darwin-amd64-v0.11.0

# run install.sh
./install.sh
```

### Linux

#### Install with Homebrew (`brew`)

Ensure [Homebrew](https://brew.sh/) is installed

```bash
brew install vmware-tanzu/tanzu/tanzu-community-edition

${HOMEBREW_EXEC_DIR}/configure-tce.sh
```

#### Install with tar ball manually

```bash
# download the tar ball with your favorite browser or something like wget or curl
wget https://github.com/vmware-tanzu/community-edition/releases/download/v0.11.0/tce-linux-amd64-v0.11.0.tar.gz

# extract the tar ball using Finder or a CLI tool like tar
tar xvzf tce-linux-amd64-v0.11.0.tar.gz

# cd into the extracted directory
cd tce-linux-amd64-v0.11.0

# run install.sh
./install.sh
```

### Windows

#### Install with Chocolatey

```
choco install tanzu-community-edition --version 0.11.0
```

#### Install with zip manually

Download the zip with your favorite browser or something like `Invoke-WebRequest` or `wget` or `curl` etc

Link - https://github.com/vmware-tanzu/community-edition/releases/download/v0.11.0/tce-windows-amd64-v0.11.0.zip

```
$source = 'https://github.com/vmware-tanzu/community-edition/releases/download/v0.11.0/tce-windows-amd64-v0.11.0.zip'
$destination = '<destination-path>\tce-windows-amd64-v0.11.0.zip'
Invoke-WebRequest -Uri $source -OutFile $destination
```

Then extract the zip file using File explorer or something like `Expand-Archive`

```
Expand-Archive -LiteralPath "<destination-path>\tce-windows-amd64-v0.11.0.zip" -Destination '<destination-path-for-extracted-directory>'
```

Change directory into the extracted directory

```
cd <destination-path-for-extracted-directory>\tce-windows-amd64-v0.11.0
```

Run `install.bat` script

```
.\install.bat
```
