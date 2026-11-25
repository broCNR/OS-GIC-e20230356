# Lab 2 — Linux Navigation and File Management: individual report

**Student name/ID:** Chea Somanarath / e20230356
**Ubuntu username:** gic-chea-somanarath
**My values (`oslab values lab2`):** file1 = vendor list.txt, file2 = budget 2026.txt, owner = Finance, reader = HR, third = Support
**Files:** evidence/paths.txt, evidence/tree.txt, evidence/checkpoint.txt

## What I Did

| Step | My command | Current folder when I ran it |
|---|---|---|
| Move the first file (relative destination) | `mv -- "$file1" ../reports/` | `~/oslab-work/lab2/incoming` |
| Move the second file (absolute paths) | `mv -- "$OSLAB_WORKSPACE/lab2/incoming/$file2" "$OSLAB_WORKSPACE/lab2/reports/"` | `~/oslab-work/lab2` |
| Read the report from my reader department (relative path) | `cat "../$owner/$file1"` | `~/oslab-work/lab2/TechCorp/HR` |
| The path error I made on purpose, and its message | `cat "reports/$file1"` gave `cat: 'reports/vendor list.txt': No such file or directory` | `~/oslab-work/lab2/TechCorp/HR` |
| The relative path that fixed it | `../../reports/vendor list.txt` | `~/oslab-work/lab2/TechCorp/HR` |

## Explanation

A correct file name can still give "No such file or directory" because a relative path starts from the folder I am in, not from the lab folder. From `TechCorp/HR` there is no `reports` folder, so `reports/vendor list.txt` points to a place that does not exist, even though the file is real. I had to go up two folders with `../..` to reach the lab folder first. The other problem I hit was empty variables: when `$file1` had no value, `mv` looked for a file with an empty name.

`mv` moves a file: after `mv` of `vendor list.txt` into `reports/`, it was no longer in `incoming/`. `cp` makes a copy: after I copied `vendor list.txt` into `TechCorp/Finance/`, the original stayed in `reports/`, so there were two files.

## What My Tests Do Not Prove

`ls` only shows that a file with the right name exists, not that its contents are right. `cmp` shows that two copies have identical bytes, but it does not prove the original contents were correct, or that the file is in the folder the task wanted.
