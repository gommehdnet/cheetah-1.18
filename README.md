# GommeHD.net Cheetah 1.18

This is a fork of PaperSpigot tailored for the use at GommeHD.net

## How to build
- Clone this repository
- Open a shell (e.g. using Git Bash on Windows)
- Run `./gradlew applyPatches` to apply the patches
- Run `./gradlew build` to build the jar files
- Run `./gradlew createReobfBundlerJar` to create the final jar file
- The final jar file can be found in `build/libs/cheetah-1.18-bundler-1.18.1-R0.1-SNAPSHOT-reobf.jar`

## How to use the API with Maven?
- Run `./gradlew publishMavenPublicationToMavenLocal` after building
- Add the following maven dependency:
```xml
<dependency>
    <groupId>net.gommehd.cheetah</groupId>
    <artifactId>cheetah-api</artifactId>
    <version>1.18.1-R0.1-SNAPSHOT</version>
</dependency>
```
- If accessing NMS code is required as well, add the server dependency along with the `cheetah-api` dependency:
```xml
<dependency>
    <groupId>net.gommehd.cheetah</groupId>
    <artifactId>cheetah-server</artifactId>
    <version>1.18.1-R0.1-SNAPSHOT</version>
</dependency>
  ```
## How to apply changes
- First apply the patches using `./gradlew applyPatches`
- Perform the changes to the code
- If you are a missing file, you can import it from NMS. For this, add a new line to `build-data/dev-imports.txt`, e.g. `minecraft net.minecraft.world.level.entity.LevelEntityGetterAdapter` to import the LevelEntityGetterAdapter. Then apply the patches again (`./gradlew applyPatches`). Keep in mind that all uncommited changes to the code will get LOST by this!
- Once all changes have been applied, switch to the Subproject in your Shell (`cd Cheetah-Server` or `cd Cheetah-API`) and run `git add .`. Then, commit your changes using `git commit -m "NAME OF PATCH"`
- Switch back to the project root and rebuild the patches: `./gradlew rebuildPatches`
- Commit the changed patch files the `patches/` folder to the root git repository

## Contributing
Only pull requests of the GommeHD.net dev team members are accepted. If you want to add a patch others could benefit from as well, consider submitting it to the upstream (https://github.com/PaperMC/Paper).