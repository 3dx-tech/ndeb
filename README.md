# ndeb

Utility to aid in creating Debian (.deb) packages for NodeJS.

### Install
`yarn add ndeb`

### Dependencies:
- `dpkg`
- `fakeroot`

---

## How it uses?

Just run this command with [arguments](#arguments):

```bash
ndeb --arg1 --arg2 -arg3
```

This command will add all of the above files and directories to a Debian package as well as generate the scripts
necessary to install, uninstall, start, and stop your application. On installation, via `dpkg -i $your_package_name`,
dedicated Unix users and groups will be created and your distribution's default init system will start and monitor
the process.

### Arguments
Name  | About | Type | Default
------------- | -------------  | ------------- | -------------
```v```  | Package version | <span style="color: yellow">required</span> |  -
```n``` ```pkg-name```  | Package name for configurations and in the name of the app directory with source files.| <span style="color: yellow">required</span> |  -
```dir``` | Folder with source files for packaging. | <span style="color: yellow">required</span> |  -
```a``` | Architecture. For example, here are some any supported [arch](https://wiki.debian.org/SupportedArchitectures). | <span style="color: gray">optional</span> | all
```b ```  | Build number | <span style="color: gray">optional</span> |  -
```verbose```  | Debug mode| <span style="color: gray">optional</span> |  -
```desc```  | Comments for DEBIAN files. | <span style="color: gray">optional</span> |  -
```deb-dir```  | Directory for output deb files | <span style="color: gray">optional</span> |  deb
```sd-doc```  | Link to documentation | <span style="color: gray">optional</span> |  -
```--sd-env``` | Link to documentation | <span style="color: gray">optional</span> |  -

Folder with source files for packaging.
```bash
--desc #required
```
Comments for DEBIAN files.
```bash
--verbose #required
```
### Example

`ndeb --b=123 --n=PackageName --user=UserName --group=GroupName --sources=SourceFolder --maintainer="John Doe" --desc="Any text" --depends=Dep1,Dep2 --sd-restart="on-failure" sd-execstart="/usr/bin/node /opt/packageName/app/build/server.js" --sd-doc=DocLink --sd-env="CONST_NAME=true,NODE_ENV=production"`

These are all available through `apt` and `brew`.

---

### Support

`ndeb` only officially supports the currently supported versions of Debian and Ubuntu (LTS). This includes both
for building packages and deploying packages. Care has been taken to ensure this packages correctly on macOS, and macOS
specific issues should still be reported.
