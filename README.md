Make your own *.ptn
======================

# 1. Convert *.ptn to *.bms
## Step 1.
1. Open your *.ptn file in hex editor (Anything else).  
2. Find the first EZTR text (in hex, 45 5A 54 52).  
3. Copy 
    > 50 54 46 46 00 06 C0 00 0D 00 0A 43 40 00 A0 3E 00 00 8E 37 11 43 F9 00 01 01 30 2D 61 69 2E 6F 67 67 00 00 41 00 49 00 88 65 47 00 50 65 A6 00 A0 B1 A6 00 9C F6 12 00 70 A1 41 00 C0 F7 12 00 D8 F8 45 00 00 00 00 00 C0 F7 12 00 18 F9 12 00 C1 5C 41 00 C0 F7 12 00 D8 F8 02 00 32 2D 63 6C 61 70 2D 30 31 2E 6F 67 67 00 88 65 47 00 50 65 A6 00 A0 B1 A6 00 9C F6 12 00 70 A1 41 00 C0 F7 12 00 D8 F8 45 00 00 00 00 00 C0 F7 12 00 18 F9 12 00 C1 5C 41 00 C0 F7 12 00 D8 F8 

    This is temporary header data. 
4. and paste this before the first EZTR text (in hex, 45 5A 54 52).  
5. Cut last N-number of EZTR datas (include EZTR text) which have not null datas.  
   
   **Example**:  
   > If you want to make 5 Line pattern, Cut last 5 EZTR datas which have not null datas.  

6. Find the fourth EZTR text, and paste at front of the fourth EZTR text. 
   
    **Example**:  
    > (Copied hexes) 45 5A 54 52 (Some hexes)

7. Save it.


## Step 2.
1. By using ptfluffy(pt2bms), Make *.ptn to *.bms (It can need to change extension to *.pt)  
2. Open your *.bms by BMSE. 
3. Change yours. 
4. Select All notes by Ctrl-A and Copy it Ctrl-C.  
5. Paste it at Notepad, save it, name it "input.txt". This is BMSE ClipBoard Object Data Format.  


# 2. Convert BMS Data to *.ptn Hex Data
1. *.ptn files have In-Game Note datas. Each have 11 byte data.
2. It can make by **bms2hex**.
    ### 2.1 Usage bms2hex
    > ```shell
    > python3 bms2hex.py
    > ```

3. Done !

# 3. Paste Hex Data to *.ptn
1. Output data have several tracks. Track #011 ~ #019 will be key part.
2. Copy each tracks. If you made 5 Line pattern, Copy #011 ~ #015.  
3. Referencing song's original *.ptn, Replace data at last 5 EZTRs.  
   
    **Example:**
    > If you made 5 Line pattern, find last 5 EZTRs. Each EZTRs are 1 Line.  
    #011 Track will be Line 1, #012 Track will be Line 2.... (#012 also can be Line 1)  
    Start by EZTR text, 75~78th bytes mean length of 1 Line note data.     
    Change it (output.txt has length data).  
    After length bytes, Replace your own hex datas.   
    Repeat this.


## ○ Reference
* [ptfluffy](https://sites.google.com/site/twisteroidambassador/ptff)