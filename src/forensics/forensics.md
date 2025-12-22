# Disk Image Forensics

## Setting up Autopsy 4.x on Linux

This is because the default version on Kali Linux is the outdated 2.x version.

### Steps

- Download the zip file and the `.deb` sleuthkit-java file.

- Install (manually) the dependency.

- Remove old sleuthkit (`sleuthkit` package) and reboot.

- Install the sleuthkit-java deb package.

- From link above, run install_application.sh with the following parameters: `install_application.sh -z zip_path -i install_directory -j java_home`.

An example would be `install_application.sh -z ~/Downloads/autopsy-4.19.2.zip -i ~/autopsy -j /usr/lib/jvm/java-1.17.0-openjdk-amd64`.

The path to the Java 17 home is the last output from the prequisites installation scripts, but typically, the path will be in the result of running `update-java-alternatives -l | grep java-1.17` on Debian-based Linux.

> [!NOTE]
> Note that as of the time of writing, Kali Linux no longer provides Java 17 in its repository.

After successfully installed, run with `/path/to/autopsy/bin/autopsy`.

- Can add path to `.zshrc`:

```bash
PATH+="/path/to/bin/dir"
export PATH
```

- Can start with `--fontsize 16` option for *readable* font size in Linux.

Reference: <https://github.com/sleuthkit/autopsy/blob/develop/Running_Linux_OSX.md>.

### Using Autopsy 4.x

See online docmentation as the UI is very different from version 2.x: <https://sleuthkit.org/autopsy/docs/user-docs>.

For example: to do keyword search, Tool -> Ingest -> Choose keyword search. Need to set up keyword list from Options.