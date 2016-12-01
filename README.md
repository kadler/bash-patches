# bash-patches
IBM i specific Bash patches for Bash 4.3

This repository contains a set of branches that correlate with a major Bash release. Each branch contains a set of directories that correlate with an IBM i release and a directory ```any``` that applies to all IBM i releases.

The way to use this repository is:
- clone the branch specific to your version of Bash
- copy the patches from ```any``` to the Bash source directory
- copy the patches from the directory specific to your IBM i release to the Bash source directory
- Apply each patch with ```patch -p1```

Example: Compiling Bash 4.3 on IBM i 7.1

```
tar -xzf bash-4.3.tar.gz
git clone -b 4.3 --single-branch https://github.com/kadler/bash-patches.git patches
cd bash-4.3
cp ../patches/any/*.patch .
cp ../patches/7.1/*.patch .
for f in *.patch
do
  patch -p1 < $f
done
```
