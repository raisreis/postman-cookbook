# ---


# openSUSE setup


# General 

## Download Postman

Download Postman from their website.

## Create desktop entry file

Create a desktop entry file in `~/.local/share/applications/postman.desktop`:
```conf
[Desktop Entry]
Name=Postman
Comment=Postman Desktop
Exec=<PATH_TO_POSTMAN_EXECUTABLE>
Icon=<PATH_TO_POSTMAN_EXECUTABLE>/app/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
Version=1.0
```


# Example

Let's install the x64 version of Postman on openSUSE (Tumbleweed).

## Download 

Download Postman from: `https://www.postman.com/downloads/`

```console
> cd /opt
> sudo mv ~/Downloads/postman-linux-x64.tar.gz .
> sudo tar -xvzf postman-linux-x64.tar.gz
```

## Create desktop entry file


```console
> touch ~/.local/share/applications/postman.desktop
> vim ~/.local/share/applications/postman.desktop
```

Add the following entry:
```conf
[Desktop Entry]
Name=Postman
Comment=Postman Desktop
Exec=/opt/Postman/app/Postman %U
Icon=/opt/Postman/app/Postman/app/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
Version=1.0
```


## Desktop entry file validation

```console
> desktop-file-validate  ~/.local/share/applications/postman.desktop
```

## Update desktop database

```console
> sudo update-desktop-database
```


# Note: Deprecated desktop `Encoding` entry

Some tutorials may contain the `Encoding` key:
```conf
[Desktop Entry]
Name=Postman
Comment=Postman Desktop
# You may consider removing that line
Encoding=UTF-8
Exec=/opt/Postman/app/Postman %U
Icon=/opt/Postman/app/Postman/app/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
Version=1.0
```

However, this key is marked as deprecated:
(https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)
> The Encoding key is deprecated. It was used to specify whether keys of type
> localestring were encoded in UTF-8 or in the specified locale. Possible values
> are UTF-8 and Legacy-Mixed. 

`desktop-file-validate` issues the same warning:
```console
> desktop-file-validate  ~/.local/share/applications/postman.desktop
  warning: key "Encoding" in group "Desktop Entry" is deprecated
```



# Further reading

https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html