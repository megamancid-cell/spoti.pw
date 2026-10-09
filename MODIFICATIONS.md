# Apple Music-inspired polish (Beta)

Applied to the Beta source tree while preserving its existing structure and GitHub Actions workflow.

## Changes

- `tweak/Sources/Redesigned/Player/PlayerArtwork.x`: reduced the paused artwork shrink from 84% to 94% of its normal size; Reduce Motion uses a 97% scale for a subtler state change.
- `tweak/Sources/Redesigned/Kit/SGRField.m`: lets the artwork-derived background colour fade begin a little lower, preserving more of the album-colour atmosphere, and lengthens field-colour crossfades to at least 1.6 seconds.

## Validation

- Source replacements checked against the original Beta files.
- ZIP integrity checked after packaging.
- Theos compilation and on-device behavior have not been tested in this environment.

## AirPods route icon

- `tweak/Sources/Redesigned/Player/PlayerFooter.x`: the redesigned player's existing Spotify Connect glyph now switches to the regular AirPods (2nd generation) SF Symbol `airpods` while an active audio output's name contains “AirPods” (with `airpodspro` and then `headphones` as compatibility fallbacks), and restores Spotify's original glyph for other routes.
- The glyph refreshes when `AVAudioSessionRouteChangeNotification` fires and fades between states. The surrounding Spotify Connect control is unchanged, so its tap action still opens the normal device picker.
- This is source-level implementation only; Theos compilation and testing with physical AirPods have not been performed here.


## Regular AirPods (2nd generation) icon adjustment

- The connected-state icon now prefers the regular `airpods` SF Symbol rather than the AirPods Pro symbol, with compatibility fallbacks for older symbol catalogs.
- Route detection and Spotify Connect tap behavior remain unchanged.
