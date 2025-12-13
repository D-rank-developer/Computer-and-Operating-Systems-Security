# 🛡️ OverTheWire Bandit Wargame — Levels 0 to 11

This document presents a clean, structured walkthrough of the **OverTheWire Bandit** wargame (Levels 0 → 11), based on screenshots taken during the exercise.  
Each section includes:  
- The objective  
- Commands used  
- A short technical analysis  
- The password found  
- The corresponding screenshot (where available)

---

## 📂 Screenshot are used for the Lab 
Images are provided to explain the various commands.  

---

# 🔰 Level-by-Level Analysis

---

## **Level 0 → Level 1**

![Level 0](image_2.png)

**Objective:** Read the password stored in the `readme` file.

### Commands Used
```bash
ls -alps
cat readme
```

### Analysis
Listing the directory revealed a `readme` file. Displaying it using `cat` showed the password.

**Password Found:** `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

---

## **Level 1 → Level 2**

![Level 1](image_5.png)

**Objective:** Find the password stored in a file named `-`.

### Commands Used
```bash
ls -la
cat ./-
```

### Analysis
Since `-` is a special token in Linux, it must be referenced using `./-` to avoid being interpreted as stdin/stdout.

**Password Found:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

---

## **Level 2 → Level 3**

![Level 2](image_9.png)

**Objective:** Read a file with spaces in its name.

### Commands Used
```bash
ls
cat ./--spaces\ in\ this\ filename--
```

### Analysis
Filenames with spaces require escaping (`\`) or quoting to be read correctly.

**Password Found:** `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

---

## **Level 3 → Level 4**

![Level 3](image_1.png)

**Objective:** Find the password inside a hidden file.

### Commands Used
```bash
cd inhere
ls -a
cat .Hiding-From-You
```

### Analysis
Hidden files begin with `.` — using `ls -a` reveals them. Reading the hidden file provided the password.

**Password Found:** `2WmrDFRmJIq3IPxneAaMGhap0pfhF3NJ`

---

## **Level 4 → Level 5**

![Level 4](image_6.png)

**Objective:** Identify the only human-readable file inside `inhere`.

### Commands Used
```bash
cd inhere/
find . -type f | xargs file
cat ./-file07
```

### Analysis
`find` listed all files; piping to `file` revealed file types. The only ASCII text file was `-file07`.

**Password Found:** `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

---

## **Level 5 → Level 6**

![Level 5](image_4.png)

**Objective:** Find a file that is:  
- a regular file  
- exactly **1033 bytes**  
- **not executable**

### Commands Used
```bash
cd inhere/
find . -type f -size 1033c ! -executable
cat ./maybehere07/.file2
```

### Analysis
Using a precise `find` filter isolated the exact file required. Reading it revealed the password.

**Password Found:** `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

---

## **Level 6 → Level 7**
### Commands Used
```bash
find / -type f -user bandit7 -group bandit6 -size 33c
cat /var/lib/dpkg/info/bandit7.password

```
### Analysis
The command searches the entire filesystem for regular files owned by bandit7, belonging to the bandit6 group, and exactly 33 bytes in size. After locating the correct file, cat is used to read its contents.

**Password Found:** `morbNTDkSW6jIltC9YM0dMaLnoIFVAaj`

---

## **Level 7 → Level 8**

![Level 7](image_0.png)

**Objective:** Find the line containing the word **"millionth"**.

### Commands Used
```bash
strings data.txt | grep "millionth"
```

### Analysis
`strings` extracts readable text from binary noise. The grep search produced the target line.

**Password Found:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

---

## **Level 8 → Level 9**

![Level 8](image_7.png)

**Objective:** Identify the only unique line in `data.txt`.

### Commands Used
```bash
sort data.txt | uniq -c
```

### Analysis
`uniq` needs sorted input to count duplicates. The line appearing with count **1** is the password.

**Password Found:** `4CKMh1JI91BUIZZPXDqGanal4xvAg0JM`

---

## **Level 9 → Level 10**

![Level 9](image_3.png)

**Objective:** Extract the password hidden in noisy output, marked by `=` symbols.

### Commands Used
```bash
strings data.txt | grep "="
```

### Analysis
`strings` filtered printable characters; `grep "="` isolated the target line.

**Password Found:** `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

---

## **Level 10 → Level 11**

![Level 10](image_8.png)

**Objective:** Decode the Base64-encoded password.

### Commands Used
```bash
cat data.txt
base64 -d data.txt
```

### Analysis
The contents were clearly Base64 encoded. Decoding it provided the password.

**Password Found:** `dtR173fZKb0RRsDFSGsg2RwnpNvj3qRr`

---

# 🧠 Summary of Skills Demonstrated
✔ Handling special filenames (spaces, hyphens, hidden files)  
✔ Using `find` with advanced filters  
✔ File type identification (`file`)  
✔ Sorting, filtering, and counting (`sort`, `uniq`, `grep`)  
✔ Extracting readable strings (`strings`)  
✔ Decoding Base64  
✔ Navigating nested directories  
✔ Understanding Linux file system behavior  

---

# ✔️ End of Documentation
This README is fully GitHub-ready, clean, structured, and suitable for public viewing.

