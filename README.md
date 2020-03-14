# EEC-IV_A9L

This repo is forked from the OpenEEC Project. Notable contributions:

- The file `A9L_chucko.txt` is derived from `A9L_lst.txt`, with additional analysis of what the code is actually doing, and how it corresponds to the GUFB strategy document from Ford and the GUFB.xls strategy file for Binary Editor.
- There are several patches which may be of interest. For the most part, they remove code for features the Fox body Mustangs never had (e.g. knock sensor, electric fan, computer-managed cruise control). Each patch speeds up EEC processing slightly. Thus, they may prove useful for engines operating at higher RPM than the stock 5.0.

**DISCLAIMER: Use these patches at your own risk!**

**I cannot accept any responsibility for any damage or injury which may result from others' use of these patches. Use your own best judgment, and be sure to read the rationales for a patch before attempting to use it.**

I have tested several of these patches successfully on my own 1989 Mustang, but not without the occasional "oops." Mistakes happen. I am happy to accept feedback on these files, and when notified of a mistake, will make every attempt to correct it as soon as practicable.

All files here are easiest to read in a fixed width font.

## Suggested order of installing patches

Note that some of these patches require corresponding changes to the strategy document used by tuner software such as Binary Editor and TunerPro RT.

1. Read_HSI patch - the most frequently executed routine at anything over 3750 RPM.
2. 1ms timer patch - most frequently executed routine at lower engine speeds.
3. Spark_calc patch - removes much code that is executed on every PIP - essential at high RPM.
4. Update knock retard patch - bypass background code for the nonexistent knock sensor, while preserving tip-in retard (if you think it's useful).
5. Background task list patch - strips out background routines that do nothing.
6. Set RPM flags patch - reorganizes a key background routine to execute more quickly.

## Experimental patches - still in development

- PIP-high and PIP-low handlers
