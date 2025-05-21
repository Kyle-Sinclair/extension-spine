[![Actions Status Alpha](https://github.com/defold/extension-spine/actions/workflows/bob.yml/badge.svg)](https://github.com/defold/extension-spine/actions)


# Testing for skin mixing 

You can find additional methods added to comp_spine_model.cpp ("CompSpineModelAddSkin") and script_spine.cpp ("SpineComp_AddSkin") that allow us to add skins of a spine model in a stacking manner.
I have it working currently and you can see it and test it by using the spine_script.script in the main collection. 

You may run into bugs if the spine model is set to having no default skin.

Remaining questions to investigate are if we need to dispose of old skins memory wise and if there is a better way to stack them, since currently I'm making a new skin,
adding the current skin, then adding the additional skin, then applying that. 

We'd also need to decompose our current skins into pieces, so that Summer would go to "Summer_hair", "Summer_torso" etc. We were going to do this anyway, but it would mean
our existing character skins would need to fire off a list of "add_skin" requests that create their archetypal skin. 

We also need to question if we maintain a fork of the spine extension or submit this change as a PR to the spine extension defold team. I think the PR is the right idea. 

# Spine animations for Defold

Defold [native extension](https://www.defold.com/manuals/extensions/) for interacting with Spine animations.

[Manual, API and setup instructions](https://www.defold.com/extension-spine/) is available on the official Defold site.

## Pull requests
We happily accept [pull requests](https://github.com/defold/extension-spine/compare) that solve [reported issues](https://github.com/defold/extension-spine/issues).

## Updating the Spine runtime version
Updating the Spine runtime version requires a rebuild of the runtime for all supported platforms. There is a build script to rebuild the runtime library in [extension-spine/utils/runtime](https://github.com/defold/extension-spine/tree/main/utils/runtime). The version is defined in the [build_runtime_lib.sh file](https://github.com/defold/extension-spine/blob/main/utils/runtime/build_runtime_lib.sh#L5).

__Make sure to check the change log for breaking changes!__

## Updating the Spine extension plugin for the editor
If the extension code for the editor has to be updated there is also a build script in [`extension-spine/utils/build_plugins.sh’](https://github.com/defold/extension-spine/tree/main/utils/build_plugins.sh). Use it to build the [plugin libs and jar file](https://github.com/defold/extension-spine/tree/main/defold-spine/plugins).
