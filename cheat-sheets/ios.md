# iOS

### Cleaning Simulators & Test Device Files

List simulators in ~/Library/Developer/CoreSimulator: `xcrun simctl list devices`

Delete unavailable simulators: `xcrun simctl delete unavailable`

Delete simulator: `xcrun simctl delete DEVICE-ID-HERE`

Clear derived data: `rm -rf ~/Library/Developer/Xcode/DerivedData/*`

Delete old test device support files: `open ~/Library/Developer/Xcode/iOS\ DeviceSupport/`

Go into Xcode Organizer and delete old Archives.

