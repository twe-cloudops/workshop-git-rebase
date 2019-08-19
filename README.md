# Workshop `git rebase`

## Learn `git rebase` with a poem

**The objective of this kata is to learn how to use git rebase command.**

🌲 **set up**

```
git clone git@github.com:coralieco/workshop-git-rebase.git
cd workshop-git-rebase
git checkout poem
git checkout paragraph_1
```
🌲 **goal**

- Reconstitute the full poem in correct order
- The best configuration is to keep the historic in order, such as commit list in order:

```
# paragraph_1
P1/l1
P1/l2
P1/l3
P1/L4
P1/l4 corrected
P1/l5

# paragraph_2
P2

# paragraph_3
P3/l1
P3/l2
P3/l3
P3/l4
P3/l5

# paragraph_4
P4/l1
P4/l2
P4/l3
P4/l4
P4/l5

# title
Title
Author
```

🌲 **visualize branches**

![](images/schema_git_rebase.jpeg?raw=true)


Seeing that, the challenges are:

- For `paragraph_1`, use the correct commit for `l4` (corrected) and not take the `bad` commit
- For `paragraph_2`, just rebase
- For `paragraph_3`, manage the 3 different branches, don't take the bad commit on `paragraph_3_bis_bis` branch
- For `paragraph_4`, put the two first commits in the correct order (`l1` before `l2`)
- For `bad_branch`, do not merge any of the commits into`poem` when merging `paragraph_4`
- For `title` branch, squash the 2 commits related to titles

🌲 **rules**

- You can use `git rebase` with options as much as you want
- You can't use `cherry-pick`
- you have to merge into `poem` (do not use `master`)
- level 1: You can't commit anything
- level 2: You have to preserve merges

🌲 **help**

- There is one commit per line of the poem (except for `paragraph_2` where there is a unique commit): `P1/l3` means this is a line 3 of Paragraph 1.
- Start in order: `paragraph_1` / `paragraph_2` / `paragraph_3` / `paragraph_4` / `Title`
- Some of these command are really helpful:
  - `git log`
  - `git reflog`
  - `git reset --hard`
- There will be conflicts to resolve ! Do not focus too much on resolving conflicts, this is not the workshop purpose. You can use the final poem below (lines are indicated) to help you out resolving the conflicts..

🌲 **final poem**

```
1. The Road Not Taken
2. BY ROBERT FROST
3.
4. Two roads diverged in a yellow wood,
5. And sorry I could not travel both
6. And be one traveler, long I stood
7. And looked down one as far as I could
8. To where it bent in the undergrowth;
9.
10. Then took the other, as just as fair,
11. And having perhaps the better claim,
12. Because it was grassy and wanted wear;
13. Though as for that the passing there
14. Had worn them really about the same,
15.
16. And both that morning equally lay
17. In leaves no step had trodden black.
18. Oh, I kept the first for another day!
19. Yet knowing how way leads on to way,
20. I doubted if I should ever come back.
21.
22. I shall be telling this with a sigh
23. Somewhere ages and ages hence:
24. Two roads diverged in a wood, and I—
25. I took the one less traveled by,
26. And that has made all the difference.
```

To resolve conflicts, information about lines number can be very useful.

🌲 **more help**

Don't read this, if you don't want too much help.

- `paragraph_1`: `git rebase -i` expected
- `paragraph_2`: `git rebase` expected
- `paragraph_3`: `git rebase -i` expected - `git reset -hard` can be used
- `paragraph_4`: `git rebase -onto` expected
- `title`: `git rebase -i` expected

---

## Conclusion

Hope you had fun and learnt more about `git rebase` with this workshop !
