# ChangeLog
### 2026.10.04 (fork) Transmission 4.x compatibility
* Fixed
	* Install script now detects the Transmission 4.x Web UI directory (`public_html`) in addition to the legacy `web` directory, so the UI installs to the folder the daemon actually serves. Previously only Synology got this treatment; on Debian/Arch/etc. the installer wrote to `web/` while the daemon served `public_html/`, leaving the stock UI in place.
	* Detection is version-based (`transmission-remote`/`transmission-daemon --version`): 4.x and above -> `public_html`, 2.x/3.x -> `web`; falls back to directory presence when the version cannot be determined.
	* Install script download URLs now point at the fork repository (`frank777777777/transmission-web-control`) so "latest release", "master", and "re-download script" fetch from this fork.
	* Torrent list per-torrent rates (download/upload speed, peers, etc.) no longer stay frozen for torrents that keep downloading/seeding at a steady rate. The UI's periodic refresh used the `recently-active` RPC filter, which only returns torrents whose state changed in the last 30 seconds, so steady-state torrents kept showing stale rates. The UI now performs a full torrent-get on every auto-reload cycle, so the list refreshes at the interval set in the toolbar (e.g. 5 s).
* Note
	* The Web UI itself is compatible with Transmission 4.x RPC (JSON-RPC, rpc-version >= 15): it uses the `free-space` method for the download-dir free space and reads `config-dir` from `session-get`, both of which are still provided by 4.x.

### 2018.03.30 v1.5.1-update2
* Fixed
	* Fix the torrent list to show misplaced bugs; Fixed #169 #170
	* Fix prompt text for some buttons in the torrent Properties window;
	* Fix right-click "Copy download location to clipboard" feature in the torrent list; #171
* Add
	* Add "Restore UI Default Settings" feature;
	* Add "Copy download location to clipboard" in Base>Download Dir ; #171

### 2018.03.29 v1.5.1-update1
* Fixed #165 #166 #167 #168

### 2018.03.28 v1.5.1
#### Note: The new update address will be enabled from this release, please download the installation script again. 

https://github.com/ronggang/transmission-web-control/blob/master/release/install-tr-control.sh

* [-] Delete the src.tar.gz files under this repository, and then no longer save the packaging documents under this repository; 

* [!] Fix the remaining time sorting error; fixed #161
* [!] Fix width of the "Config" window; Fixed #158
* [!] Fix parameter Configuration "Use schedule" when clicked, the Time input box status has no updated bug;

* [*] Update the installation script, the package file address points to the new repository;
* [*] Restore display of the list of BT servers, add parameters can be set; Close #161

* [+] Add the interface state memory function, cancel the "Auto expand attribute" function;
* [+] Add additional parameter setting options for configuring some parameters outside of TR's own function; 
* [+] Add the "Copy Save directory to clipboard" feature;

Before 2018
 - Updated the install tar file
 - Fixed several typos in English interface
 - Added http install script
 - Added install.sh with English comments
 - Updated easyui to 1.5.1 and jquery to 1.12.4 By -- @balonik
 - Fixed issue #20, #21, #23, #39, #40, #43, #44 #53 By -- @balonik
 - Replaced some Chinese comments to English
 - Fixed issue #77，#81 (Please clear your cookies if you encounter any error) By -- @balonik
 - Now the maximum number of torrents per page is 300，meanwhile, you can still modify the file config.js "pagination:true" to "pagination:false" in order to show ALL the torrents. By -- @balonik