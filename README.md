Fix for AMD drivers weird issue when the Windows Update installs an older diver on GPU's and APU's instead of the latest versions provided by AMD.
Here is how to fix AMD Driver issues on Windows 10/11.

1. Go to your GPEDIT(Group policies settings) ``Administrative Templates>Windows Update>Do Not Include Drivers With Windows Update`` and set it to ``Enabled``.

**NB! For Windows 11 and Windows 10 Home Owners**

* Turn off automatic driver updates via Registry

* Type ``regedit`` in the Start/taskbar search and then hit the Enter key.

* Go to the following key:

* ``HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching``

* Select ``SearchOrderConfig`` DWORD Value.

* Change the value from the default ``1`` to ``0``. Click the OK button. This setting disables the auto driver installs from Windows Update.

* Reboot your PC to apply the changes.
  
2. Download the web version of the AMD drivers, because it detects and installs both of your GPU and APU drivers on Auto, the big installer file only installs for the GPU.
* https://www.amd.com/en/support/download/drivers.html

3. (Optional) The actual current driver 1,6 GB download for both GPU and APU
* https://www.amd.com/en/resources/support-articles/release-notes/RN-RAD-WIN-25-11-1.html#Downloads

4. Download DDU and run in Safe Mode msconfig>Safe Boot check On. Remove the AMD driver for your GPU.
**If you want Safe Mode on auto, without manually using msconfig with DDU, then just run the amdcleanup utility.**
**AMD Cleanup Utility:**
* https://www.amd.com/en/resources/support-articles/faqs/GPU-601.html

**DDU:**
* https://www.guru3d.com/download/display-driver-uninstaller-download/

5. Reboot into normal mode **msconfig>Safe Boot** uncheck

6. Run the web version of AMD Driver detect and select Minimal or Typical and Factory Reset, wait for installation to finish and reboot.

7. Go to your Device Manager>Display Adapters and check which driver both of your APU and GPU are running.

**NB! Driver Dates for both GPU and APU should be 6/11/2025(at the time of writing this, if you are from the future years then years should correspond).**

**For your 5000/6000/7000/9000 XT or any other AMD GPU it should say (NB! the numbers will change with future driver releases):**

* ``32.0.22029.1019``

**For your APU on Ryzen CPU's (APU's).**
* ``32.0.21033.3005``

**NB! If it says 2024 and uses another driver number then repeat the process, but it should be fixed, if these steps are followed.**

8. (Optional) Some people suggested adding the driver to Windows exclusion policy by Hardware ID, for safe measure.

9. How to check Hardware ID's:
* https://www.guidingtech.com/how-to-check-hardware-devices-id-windows/

10. Adding to GPEDIT- Go to ``Computer Configuration>Administrative Templates>System>Device Installation>Device Installation Restrictions`` and check the link how to proceed.

* https://windowsforum.com/threads/block-a-specific-driver-update-in-windows-11-gp-registry-and-wushowhide.384429/

* Enjoy and sticky this topic somewhere.

**Brought to you by silentgameplays**
https://www.youtube.com/@silentgameplays
