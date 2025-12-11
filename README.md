Fix for AMD drivers weird issue when the Windows Update installs an older diver on GPU's and APU's instead of the latest versions provided by AMD.
Here is how to fix AMD Driver issues on Windows 10/11.

1. Go to your GPEDIT(Group policies settings) ``Administrative Templates>Windows Update>Do Not Include Drivers With Windows Update`` and set it to ``Enabled``.

**NB! For Windows 11 and Windows 10 Home Owners**

**Turn off automatic driver updates via Registry**
* Type ``regedit`` in the Start/taskbar search and then hit the Enter key.
* Go to the following key: ``HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching``
* Select ``SearchOrderConfig`` DWORD Value.
* Change the value from the default ``1`` to ``0.``
* Click the OK button. This setting disables the auto driver installs from Windows Update.
* Reboot your PC to apply the changes.

2. Download the web version of the AMD drivers, because it detects and installs both of your GPU and APU drivers on Auto, the big installer file only installs for the GPU. The web installer requires you to run the installation in normal mode with internet enabled, so that it can download and install drivers for both your APU and GPU.

* https://www.amd.com/en/support/download/drivers.html

3. (Optional) The actual current driver 1,7 GB offline download for both GPU and APU. (December version)

* https://www.amd.com/en/resources/support-articles/release-notes/RN-RAD-WIN-25-12-1.html#Downloads

**November version 1,6 GB offline installer**

* https://www.amd.com/en/resources/support-articles/release-notes/RN-RAD-WIN-25-11-1.html#Downloads

4. Download DDU and run in Safe Mode msconfig>Safe Boot check On. Remove the AMD driver for your GPU using the Install a New Graphics Card option, this option will remove all of the leftovers from Windows Update drivers for GPU and APU.

**DDU:**

* https://www.guru3d.com/download/display-driver-uninstaller-download/

5. Reboot into normal mode msconfig>Safe Boot uncheck

6. Run the web version of AMD Driver detect and select Minimal or Typical and Factory Reset, wait for installation to finish and reboot.

7. Go to your Device Manager>Display Adapters and check which driver both of your APU and GPU are running.
NB! Driver Dates for both GPU and APU should be 3/12/2025(at the time of writing this, if you are from the future years then years should correspond).

**For your 5000/6000/7000/9000 XT or any other AMD GPU it should say (NB! the numbers will change with future driver releases):**

* ``32.0.22029.9039``

**For your APU on Ryzen CPU's (APU's).**

* ``32.0.21037.1004``

**NB! If it says 2024 and uses another driver number then repeat the process, but it should be fixed, if these steps are followed.**

8. (Optional) Some people suggested adding the driver to Windows exclusion policy by Hardware ID, for safe measure.

9. How to check Hardware ID's:

https://www.guidingtech.com/how-to-check-hardware-devices-id-windows/

10. Adding to GPEDIT- Go to ``Computer Configuration>Administrative Templates>System>Device Installation>Device Installation Restrictions`` and check the link how to proceed.

https://windowsforum.com/threads/block-a-specific-driver-update-in-windows-11-gp-registry-and-wushowhide.384429/

11. Always check that on your motherboard vendor's website and Adrenalin Software Utility that your Chipset Drivers are up to date, if not- update them.

**NB! If you are still having issues then try these steps as well and then repeat the driver installation related steps**
1. Go to your BIOS/UEFI and make sure it's up to date, if not, then flash it with a USB stick
2. In BIOS/UEFI Check the Secure Boot Settings, make sure it is enabled.
3. Set Secure Boot from Standard to Custom with Factory Defaults.
4. Apply the changes and reboot
5. Go into your ``Event Viewer>Custom>Administrative Events`` and if you see this error  ``"Secure Boot CA/keys need to be updated"`` Event ID 1801 then follow these steps.
6. Open Windows Powershell as Admin and run: ``reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Secureboot /v AvailableUpdates /t REG_DWORD /d 0x5944 /f ``
7. Then run:``Start-ScheduledTask -TaskName "\Microsoft\Windows\PI\Secure-Boot-Update"``
8. Wait for some time 3-5 minutes.
9. Go into regedit and find ``Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecureBoot\Servicing``
10. The value of ``UEFICA2023Status``  key should say ``Updated`` instead of ``In Progress``
11. Reboot. Check the eventviewer for errors again.

*Enjoy and sticky this topic somewhere, so that people know that this is a Microsoft issues not an AMD issue.
**Brought to you by silentgameplays**
* https://www.youtube.com/@silentgameplays
