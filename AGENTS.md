# Repository agent notes

## Protocol regeneration (Avlos)

The Avlos CLI used to regenerate `src/tinymovr.hpp`, `src/tinymovr.cpp` and
`src/helpers.hpp` from a Tinymovr spec lives in the sibling repo's virtualenv:

    source ~/Projects/Tinymovr_Avlos/venv/bin/activate
    avlos from file ~/Projects/Tinymovr_Avlos/studio/Python/tinymovr/specs/<spec>.yaml --config=./avlos_config.yaml

Available specs live under `~/Projects/Tinymovr_Avlos/studio/Python/tinymovr/specs/`
(e.g. `tinymovr_3_0_x.yaml`).

The generator configuration is [avlos_config.yaml](avlos_config.yaml); it
controls which files Avlos writes.

## Release flow

1. Branch off `main` (e.g. `update_protocol_<ver>`).
2. Regenerate the protocol sources with Avlos using the appropriate spec.
3. Bump `version=` in [library.properties](library.properties).
4. Open a PR into `main`. After merge, tag the release on `main` as bare
   `X.Y.Z` (no `v` prefix) and create a matching GitHub Release.
