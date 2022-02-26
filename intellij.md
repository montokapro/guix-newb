## Installing

```
guix environment --ad-hoc flatpak -- bash -c "flatpak remote-add --user --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo && flatpak install --user flathub com.jetbrains.IntelliJ-IDEA-Community"
```

## Running

```
guix environment --ad-hoc flatpak -- flatpak run com.jetbrains.IntelliJ-IDEA-Community
```
