"Vanilla" is the name for the java version of Minecraft that Mojang releases. It is compiled to bytecode, so the JAR is very obfuscated. To help with modding and understanding the code, Mojang selflessly provides `Obfuscation map`s for each version. This can then be used in development of mods or standalone projects.

# Acquiring source

In Pumpkin development, we use yarn to apply these mappings. Here is how to get them:

```bash
git clone https://github.com/FabricMC/yarn.git
cd yarn 
./gradlew decompileVineflower
```

After that you can find the decompiled source in `build/namedSrc`. Note that this is not a fully deobfuscated jar, so variables in functions and other names may be missing. But usually you can understand from context what these should be.