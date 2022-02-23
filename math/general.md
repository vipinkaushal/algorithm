---
description: This page contains general observations for numbers.
---

# General

### Check if number will be out of range \[INT\__MIN, INT\__MAX]:

`if ((cur_num > INT`_`MAX/10 || (cur_`_`num == INT`_`MAX / 10 && next_digit > 7) || (cur_num < INTMIN/10 || (cur_`_`num == INT`_`MIN / 10 && next_`_`digit < -8))){`

`cur`_`num*10+next_`_`digit, will be out of range.`

`}`



