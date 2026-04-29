# codex-pkmn demo edits

This repository contains only our hackathon changes, not the full upstream game decompilation repositories. The base projects include copyrighted game code/assets, so this repo is intentionally limited to patch files and our small custom asset delta.

## Base projects

- Ocarina of Time decompilation: [zeldaret/oot](https://github.com/zeldaret/oot)
- Pokemon Emerald decompilation: [pret/pokeemerald](https://github.com/pret/pokeemerald)

## What is included

- `patches/oot/*.patch`: three local OOT commits for the Navi Codex UI / IS64 prompt flow.
- `patches/pokeemerald.patch`: binary-capable patch for the Pokemon Emerald starter replacement work.
- `pokeemerald/graphics/pokemon/custom_starters/`: original custom starter preview/source assets used by the patch.

## Apply the OOT patch

```sh
git clone https://github.com/zeldaret/oot.git
cd oot
git am --3way /path/to/codex-pkmn-demo-edits/patches/oot/*.patch
```

Then follow the upstream `zeldaret/oot` build instructions for your platform. After the normal setup/build, run the produced ROM in an emulator or on your normal OOT development target.

## Apply the pokeemerald patch

```sh
git clone https://github.com/pret/pokeemerald.git
cd pokeemerald
git apply --binary /path/to/codex-pkmn-demo-edits/patches/pokeemerald.patch
cp -R /path/to/codex-pkmn-demo-edits/pokeemerald/graphics/pokemon/custom_starters graphics/pokemon/
make -j
```

The build outputs a GBA ROM from the upstream project. Run it with a GBA emulator after applying the patch and building.

## Notes for judges

The patch-only format is deliberate: it demonstrates the work while avoiding redistribution of the full upstream repositories. To review the implementation, apply the patches to clean checkouts of the linked base projects.
