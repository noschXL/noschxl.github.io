
# Posts: 

 - [Decrypting a Malware](#the-malware)

---

# Other:
 - [Sources](#sources)
---
# The Malware
## Stage 1: The Minecraft Mod

The orignial mod was made for Fabric, it was supposed to be a dupe for the version 1.21,  
though after putting it in [Recaf](https://github.com/Col-E/Recaf)  
i saw that it wasnt.

cause who would put a file in there called *mysecret.dll*
`
$ ls -p | grep -v /
cfg.json
Dupe1.21.jar
fabric.mod.json
LICENSE_newmod
mysecret.dll
newmod.mixins.json
newmod-refmap.json
`

and low and behold: looking at dev/majanito there is a file  
called "Secret.class".

decompiling it with [CFR](https://www.benf.org/other/cfr/) gives:
```
$ cfr Secret.class 
/*
 * Decompiled with CFR 0.152.
 */
package dev.majanito;

import dev.majanito.NativeUtils;

public class Secret {
    public static final String VALUE;

    private static native String loadSecret();

    static {
        String libPath = "/native/" + System.mapLibraryName("mysecret");
        NativeUtils.loadLibraryFromJar(libPath);
        VALUE = Secret.loadSecret();
    }
}
```

looking into the Main function at dev/majanito/NewMod.class gives:
[Dump](#sources)

---

# sources
## Malware Analysis
 - [Original Virus](./assets/malware-analysis/stage1/Malware.jar)
 - [dev/majanito/NewMod.class dump](./assets/malware-analysis/stage1/unpacked/dev/majanito/NewMod.class)
