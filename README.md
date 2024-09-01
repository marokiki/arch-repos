# arch-repos
This reposity is derived from https://github.com/rf-castle/my-arch-packages.

It contains the builded packages for Arch User Repository (AUR).

You should create a new repository for your own packages.

## How to build
1. Clone the repository:
```
git clone https://github.com/marokiki/arch-repos.git
```

2. Change to the repository directory:
```
cd packages
```

3. Add the package you want to build by git submodule:
```
git submodule add https://aur.archlinux.org/<package>.git packages/<package>
git submodule update --init --recursive
```

4. Push the changes to the repository:
```
git add .
git commit -m "Add <package>"
git push
```

5. GitHub Actions will build the package and upload it to the repository.

## How to use
1. Add the following lines to your `/etc/pacman.conf`:
```
[parrot]
SigLevel = Optional TrustAll
Server = https://marokiki.github.io/arch-repos/
```

2. Update the package database:
```
sudo pacman -Sy
```

3. Install the package you want:
```
sudo pacman -S <package>
```
