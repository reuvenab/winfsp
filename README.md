# WinFsp - Windows File System Proxy

![WinFsp Demo](http://www.secfs.net/winfsp/files/cap.gif)

WinFsp is a set of software components for Windows computers that allows the creation of user mode file systems. In this sense it is similar to FUSE (Filesystem in Userspace), which provides the same functionality on UNIX-like computers.

Some of the benefits and features of using WinFsp are listed below:

* Allows for easy development of file systems in user mode. There are no restrictions on what a process can do in order to implement a file system (other than respond in a timely manner to file system requests).
* Support for disk and network based file systems.
* Support for NTFS level security and access control.
* Support for memory mapped files, cached files and the NT cache manager.
* Support for file change notifications.
* Support for file locking.
* Correct NT semantics with respect to file sharing, file deletion and renaming.

To learn more about WinFsp, please visit its website: http://www.secfs.net/winfsp/

## Project Organization

WinFsp consists of a kernel mode FSD (File System Driver) and a user mode DLL (Dynamic Link Library). The FSD interfaces with NTOS (the Windows kernel) and handles all interactions necessary to present itself as a file system driver to NTOS. The DLL interfaces with the FSD and presents an easy to use API for creating user mode file systems.

The project source code is organized as follows:

* build/VStudio: WinFsp solution and project files.
* doc: WinFsp license, contributor agreement and additional documentation. The WinFsp design documents can be found here.
* ext/tlib: A small test library originally from the secfs (Secure Cloud File System) project.
* ext/test: Submodule pointing to the secfs.test project, which contains a number of tools for testing Windows and POSIX file systems.
* inc/winfsp: Public headers for the WinFsp API.
* inc/fuse: Public headers for the FUSE compatibility layer.
* src/dll: Source code to the WinFsp DLL.
* src/dll/fuse: Source code to the FUSE compatibility layer.
* src/launcher: Source code to the launcher service and the launchctl utility.
* src/sys: Source code to the WinFsp FSD.
* opt/cygfuse: Source code for the Cygwin FUSE package.
* tst/memfs: Source code to an example file system written in C++ (memfs).
* tst/winfsp-tests: WinFsp test suite.

## Building and Running

In order to build WinFsp you will need the following:

* Windows 10
* Visual Studio 2015
* Windows Driver Kit (WDK) 10
* [Wix toolset](http://wixtoolset.org)

If you build the driver yourself it will not be signed and Windows will refuse to load it unless you enable "testsigning". You can enable "testsigning" using the command `bcdedit.exe -set testsigning`. For more information see this [document](http://www.secfs.net/winfsp/develop/debug/).

WinFsp is designed to run on Vista and above. It has been tested on the following platforms so far:

* Windows 8 Pro
* Windows 10 Pro
* Windows Server 2012

## How to Help

I am looking for help in the following areas:

* If you have a file system that runs on FUSE please consider porting it to WinFsp. WinFsp has a native API, but it also has a FUSE (high-level) API.
* If you are working with a language other than C/C++ (e.g. Delphi, C#, etc.) and you are interested in porting/wrapping WinFsp I would love to hear from you.
* There are a number of outstanding issues listed in the [GitHub repository](https://github.com/billziss-gh/winfsp/issues) ~~[BitBucket repository](https://bitbucket.org/billziss/winfsp/issues?status=new&status=open)~~. Many of these require knowledge of Windows kernel-mode and an understanding of the internals of WinFsp so they are not for the faint of heart. If you decide to tackle any of those please coordinate with me as I am actively working on that issue list.

In all cases I can provide ideas and/or support.

## Where to Discuss

If you wish to discuss WinFsp there are now two options:

- [WinFsp Google Group](https://groups.google.com/forum/#!forum/winfsp)
- [Author's Twitter](https://twitter.com/BZissimopoulos)

## License

WinFsp is available under the [AGPLv3](http://www.gnu.org/licenses/agpl-3.0.html) license. If you find the constraints of the AGPLv3 too onerous, a commercial license is also available. Please contact Bill Zissimopoulos <billziss at navimatics.com> for more details.
