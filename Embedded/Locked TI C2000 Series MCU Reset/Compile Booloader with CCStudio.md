---
id: Compile Booloader with CCStudio
aliases: []
tags: []
---
We have tried installing CCStudio cleanly using Distrobox but missing udev service does not allow the installation to be complete. We can install CCS directly but I'm afraid this would make my system messy.

Another solution we can try is to use prebuilt Docker container. This actually looks more feasible and better. I check the version of CCS which the author of CANopenNode_C2000_bootloader is using. It's v10.2.0, which is kind of old. It should work with version a bit higher than that.

Here are links of CCS containers:
- <https://github.com/uoohyo/docker-ccstudio-ide>
- <https://github.com/zfb132/ccstudio>

Update 11:06 27/07/2026: This is the headless CI/CD environment for CCS, not what we are looking for.

Update 13:51 28/07/2026: After trying to get this project to compile, I realizes the author also uses headless CLIs to compile his project. It's just that we need to install CCS to get those. We run into 2 problems:
1. Wrong compile args passing to the compiler.
2. Missing CANopenNode library.
For problem 1, we need to go into CCS to edit compile args in project properties. I haven't found a way to do it without CCS yet.
For problem 2, the author has already included CANopenNode library as a *submodule*. Hence when we pull we need to:

```git
git submodule update --init --recursive
```

if this is the first time we pull. If you have finished init, you can just leave out the `--init` argument. To update the submodule to its latest commit from its parent repo, we add `--remote` argument.

We have successfully compiled the project without any errors.
