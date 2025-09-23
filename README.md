# Working With LAMMPS

## Task 1

Rebase the `rigid-shear` branch onto the `develop` branch, squashing the branch changes down to a single commit, and modifying the commit message for this single commit to include your GitHub username.
Resolve any conflicts during the rebase in favor of the changes from the `rigid-shear` branch.

In the `maintenance` branch is a commit with the commit message `add missing override`.
Use `cherry-pick` to add this commit to your `rigid-shear` branch.
If you get a conflict, resolve it in a reasonable way.
It might help to look up any C++ keywords you see.

You should now have two commits in your `rigid-shear` branch.
Swap the order these two commits (hint: remember that when you rebase interactively, you provide an *ordered* list of the commits that should be included).

Push the changes to the `rigid-shear` branch to your GitHub repo, and make a PR from this branch to the `develop` branch.

## Task 2

In the `msse` branch, some work has been done to partially implement a LAMMPS [fix](https://docs.lammps.org/fix.html) called `msse`.
Make updates to this branch that allow the `msse` fix to be usable, and to print `Hello World!` every timestep that LAMMPS runs.
The `msse` fix should be built as a [LAMMPS Package](https://docs.lammps.org/Packages.html) when LAMMPS is configured with a `-D PKG_MSSE=yes` flag.
For example:

```bash
cmake -D PKG_RIGID=yes -D PKG_MOLECULE=yes -D PKG_KSPACE=yes -D PKG_MSSE=yes ../cmake
```

You should check how other LAMMPS packages, such as `KSPACE`, are integrated into the LAMMPS CMake configuration process in order to do this properly.

To make things easier, this branch includes `run.sh` and `run.bat` scripts that will launch an interactive development image that has everything you need to build and run LAMMPS.
The branch also includes files in an `msse_test` directory for running a quick test calculation.
You can run the test by executing the `test.sh` script, or by executing `<path_to_lmp_executable> -in lammps.in` inside this directory.

You may find the following line useful:

```c++
  utils::logmesg(lmp,"Hello World!\n");
```

Make a PR from the `msse` branch into the `develop` branch.

In the Answers section below, provide a 2-3 paragraph description of what you have learned about LAMMPS.
In particular:

1. Explain how your fix causes "Hello World!" to be printed every timestep.
2. From a software engineering standpoint, what are some appealing features of the "fix" concept, as implemented in LAMMPS?
3. At a basic level, how do "LAMMPS Packages" fit into LAMMPS' overall CMake configuration strategy?

## Answers

