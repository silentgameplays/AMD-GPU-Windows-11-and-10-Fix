# AMD-GPU-Windows-11-and-10-Fix
Fix for AMD drivers weird issue when the Windows Update installs an older diver on APU and GPU insteadc of the latest versions.
 Here is how to fix AMD Driver issues on Windows 10/11.

1. Go to your GPEDIT(Group policies settings) Administrative Templates>Windows Update>Do Not Include Drivers With Windows Update and set it to Enabled. That disables the auto driver installs

2. Download the web version of the AMD drivers, because it detects and installs both of your GPU and APU drivers on Auto, the big installer file only installs for the GPU.

3. https://www.amd.com/en/support/download/drivers.html

4. (Optional) The actual driver 1,6 GB download for both GPU and APU https://www.amd.com/en/resources/support-articles/release-notes/RN-RAD-WIN-25-11-1.html#Downloads

5. Download DDU and run in Safe Mode msconfig>Safe Boot check on. Remove the AMD driver for your GPU. If you want it on auto then just run the amdcleanup utility.

6. Reboot into normal mode msconfig>Safe Boot uncheck

7. Run the web version of AMD Driver detect and select Minimal and Factory Reset, wait for install to finish and reboot.

8. Go to your Device Manager>Display Adapters and check which driver both of your APU and GPU are running.

**Driver Date for both should be 6/11/2025**

**For your 5000/6000/7000/9000 XT or any other AMD GPU it should say:**

* ``32.0.22029.1019``

**For your APU on Ryzen CPUs.**

* ``32.0.21033.3005``

**NB! If it says 2024 and uses another driver number then repeat the process,but it should be fixed.**

8. (Optional) Some people suggested adding the driver to Windows exclusion policy by Hardware ID, for safe measure.

9. How to check Hardware ID: https://www.guidingtech.com/how-to-check-hardware-devices-id-windows/

10. Adding to GPEDIT-Computer Configuration → Administrative Templates → System → Device Installation → Device Installation Restrictions.
https://windowsforum.com/threads/block-a-specific-driver-update-in-windows-11-gp-registry-and-wushowhide.384429/

* That's it the driver issuse should be fixed

**Brought to you by silentgameplays.**
https://www.youtube.com/@silentgameplays
