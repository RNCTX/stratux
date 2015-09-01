Modification of the distribution disk image of the Stratux project at https://github.com/cyoung/stratux as follows...

1) support for Buffalo AirStation N150 Wireless USB Adapter WLI-UC-GNM, Realtek wifi AP support disabled, hostapd updated with most recent source, WPA enabled, default passphrase is asdf1234, original hostapd/hostapd_cli executables are in the pi user's home folder

2) read-only filesystem implemented to help preserve the integrity and longevity of the root SD card, unionFS used to mount /etc/ and /var/, permanent folders exist at /etc_org/ and /var_org/, read/write folders mounted at /etc_rw/ and /var_rw/, swap file disabled/removed, cron disabled/removed, x11 disabled/removed, triggerhappy disabled/removed, wolfram-system disabled/removed, rsyslog disabled/removed and replaced with busybox for temporary RAM stored logs, sound driver disabled, fastboot enabled

3) root's bashrc modified to show current filesystem mode (ro or rw) and easily switch between the two with aliases in the default bash profile ('ro' executed when logged in as root changes root filesystem to read only, 'rw' executed when logged in as root changes root filesystem to read/write, 'ro' flag is reset to default state when/if root user logs out of the system)

4) default user 'pi' still intact with default password 'raspberry', same password set for sudo/root, sshd restricted to hosts outside of the wifi ip range being served (effectively making it ethernet-only, do not have your ethernet router also serving IPs from 192.168.10.0/24 if you care about ssh!), ifplugd modified to monitor ethernet port only

5) watchdog installed, set to monitor dhcpd and hostapd PIDs, and a free memory threshold of 20MB, any failure of these will trigger a reboot

Maintenance of this fork will likely go away when the main stratux project adds these features, until then it will be maintained as new versions with major bug fixes/functionality improvements come along.
