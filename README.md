# TryHackme - KAPE
An introduction to Kroll Artifact Parser and Extractor (KAPE) for collecting and processing forensic artifacts

## Introduction to Kape
**Q.** From amongst kape.exe and gkape.exe, which binary is used to run GUI version of KAPE?

Answer: **gkape.exe**

**Q.** What is the file extension for KAPE Targets?

Answer: **.tkape**

**Q.** What type of Target will we use if we want to collect multiple artifacts with a single command?

Answer: **Compound Targets**

## Module Options
**Q.** What is the file extension of the Modules files?

Answer: **.mkape**

**Q.** What is the name of the directory where binary files are stored, which may not be present on a typical system, but are required for a particular KAPE Module?

Answer: **bin**

**Q.** In the second to last screenshot above, what target have we selected for collection?

Answer: **KapeTriage**

**Q.** In the second to last screenshot above, what module have we selected for processing?

Answer: **!EZPaerser**

**Q.** What option has to be checked to append date and time information to triage folder name?

Answer: **%d**

**Q.** What option needs to be checked to add machine information to the triage folder name?

Answer: **%m**

##Kape CLI
**Q.** Run the command kape.exe in an elevated shell. Take a look at the different switches and variables. What variable adds the collection timestamp to the target destination?

Answer: **%d**

**Q.** What variable adds the machine information to the target destination?

Answer: **%m**

**Q.** Which switch can be used to show debug information during processing?

Answer: **debug**

**Q.** Which switch is used to list all targets available?

Answer: **tlist**

**Q.** Which flag, when used with batch mode, will delete the _kape.cli, targets and modules files after the execution is complete?
Answer: **cu**

## Hands -on Challenge
Organization X has an Acceptable Use Policy for their Portable Devices, including Laptops. This policy forbids users from connecting removable or Network drives, installing software from unknown locations, and connecting to unknown networks. It looks like one of the users has violated this policy. Can you help Organization X find out if the user violated the Acceptable Use Policy on their device? The user's machine is attached to the room as a VM.

Navigate to the KAPE directory placed on the Desktop in the attached VM. Run KAPE with your desired Target and Module options, and answer the following questions.

**Answer the questions below**

**Q.** Two USB Mass Storage devices were attached to this Virtual Machine. One had a Serial Number  0123456789ABCDE. What is the Serial Number of the other USB Device?

After running the Target (KapeTriage) and module (!EZParser), I had the results saved in to the documents directory.

![img 1](https://github.com/ankrahjoseph/TryHackme-KAPE/blob/main/KAPE/Img%201.png)

I navigated to Document\Module\Registry and looked for any csv file with USB included in the file name.

![img 2](https://github.com/ankrahjoseph/TryHackme-KAPE/blob/main/KAPE/img%202.png)

After opening the second file, I searched for the serial number provided and got a match. The other serial number is what I needed.

Answer: **1C6F654E59A3B0C179D366AE**

In the same Directory, I looked for the RecentApps registry entry and found the answer in the .csv file.

![img 3](https://github.com/ankrahjoseph/TryHackme-KAPE/blob/main/KAPE/img%203.png)

Answer: Z:\Setups

**Q.** What is the execution date and time of CHROMESETUP.EXE in MM/DD/YYYY HH:MM?

In that same .csv file, we find the timestamp.

Answer: **11/25/2021 03:33**

**Q.** What search query was run on the system?

In the WordWheelQuery csv file, the search query is show on the second line

Answer: **RunWallpaperSetup.cmd**

**Q.** When was the network named Network 3 First connected to?

I opened the Known Networks csv file and found the timestamp 

![img 4(https://github.com/ankrahjoseph/TryHackme-KAPE/blob/main/KAPE/img%204.png)

Answer: **11/30/2021 15:44**

**Q.** KAPE was copied from a removable drive. Can you find out what was the drive letter of the drive where KAPE was copied from?

I accessed the Automatic Destinations csv file in FIleFolderAccess Directory then looked through the file and found E:\KAPE.

Answer: **E:**






