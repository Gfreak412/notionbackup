# sink-switch Packaging & Release Guide
## 🛠️ Initial Setup (Done Once)
### 🔐 GitHub
- Create a repository: **sink-switch**
- Add:
- `sink-switch.sh`
- `LICENSE` (MIT)
- `README.md`
### 📦 Fedora COPR
1. Create a **COPR project**: `sink-switch`
1. Install required tools:
```shell
sudo dnf install rpmdevtools copr-cli
rpmdev-setuptree
```
1. Create a `.spec` file (based on `sink-switch.spec`)
1. Tar the source:
```shell
tar -czvf sink-switch-1.0.tar.gz sink-switch-1.0/
```
1. Build RPM locally:
```shell
rpmbuild -ba sink-switch.spec
```
1. Upload to COPR:
```shell
copr-cli build sink-switch ~/rpmbuild/SRPMS/sink-switch-1.0-1.fc*.src.rpm
```
### 🧱 Arch Linux AUR
1. Create an account on [AUR](https://aur.archlinux.org/)
1. Generate SSH key (OpenSSH format) and upload to AUR
1. Clone AUR repo:
```shell
git clone ssh://aur@aur.archlinux.org/sink-switch.git
cd sink-switch
```
1. Add `PKGBUILD` and `.SRCINFO`
```shell
makepkg --printsrcinfo > .SRCINFO
git add PKGBUILD .SRCINFO
git commit -m "initial release"
git push
```
---
## 🚀 Releasing a New Version
1. ✅ **Update GitHub**
- Push updated code
- Create new release: e.g. `v1.1`
- Use tarball URL in `.spec` and `PKGBUILD`:
```plain text
<https://github.com/KanishkMishra143/sink-switch/archive/refs/tags/v1.1.tar.gz>
```
1. ✅ **Update **`**.spec**`** (Fedora)**
- Update `Version`, `Source0`, `%changelog`
- Retar folder: `sink-switch-1.1.tar.gz`
- Rebuild:
```shell
rpmbuild -ba sink-switch.spec
copr-cli build sink-switch ~/rpmbuild/SRPMS/sink-switch-1.1-1.fc*.src.rpm
```
1. ✅ **Update **`**PKGBUILD**`** (AUR)**
- Update:
```shell
pkgver=1.1
source=(...v1.1.tar.gz)
sha256sums=('...')  # Update with `sha256sum <tar.gz>`
```
- Regenerate `.SRCINFO`:
```shell
makepkg --printsrcinfo > .SRCINFO
```
- Commit and push:
```shell
git add PKGBUILD .SRCINFO
git commit -m "v1.1 release"
git push
```
---
## 🧩 FAQ & Common Issues
### ❓ **Q: "invalid .SRCINFO, does not contain pkgbase"**
- **A:** Run `makepkg --printsrcinfo > .SRCINFO` again.
### ❓ **Q: "source tarball not found"**
- **A:** Ensure GitHub release is created and `source=(...)` URL matches exactly.
### ❓ **Q: "remote: Support for password authentication was removed..."**
- **A:** You must use SSH authentication for pushing to GitHub/AUR. Add correct SSH key.
### ❓ **Q: **`**rpmbuild**`** fails on **`**%prep**`**: No such file or directory**
- **A:** Ensure the folder inside the tarball is named correctly like `sink-switch-1.1/`.
### ❓ **Q: How to clear old RPMs?**
- **A:** They’re in:
Remove old builds if needed:
```shell
~/rpmbuild/RPMS
~/rpmbuild/SRPMS
```
```shell
rm -rf ~/rpmbuild/RPMS/* ~/rpmbuild/SRPMS/*
```
### ❓ **Q: How to check if AUR download link works?**
- Click the tarball link you used in `source=...` — if it downloads, you're good.
---
---
# General DevTools
# Project Release & Packaging Guide
## Getting re-setup after a switch (or hop)
# AUR
# 🚀 AUR SSH Access Setup Guide (Using `id_rsa`)
This guide sets up SSH access to the AUR (`aur.archlinux.org`) using the `id_rsa` key, perfect for restoring after switching systems (e.g. Fedora KDE → GNOME).
---
## 🛠️ 1. Restore or Generate Your SSH Key
### ➤ If restoring from backup:
```shell
mkdir -p ~/.ssh
cp /path/to/backup/id_rsa ~/.ssh/
cp /path/to/backup/id_rsa.pub ~/.ssh/
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
```
### ➤ If generating new:
```shell
ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa -C "kanishkmishra143@aur"
```
Upload the contents of `~/.ssh/id_rsa.pub` to your AUR profile:
[https://aur.archlinux.org/account/kanishkmishra143/](https://aur.archlinux.org/account/kanishkmishra143/)
---
## 🔐 2. Configure SSH for AUR
Edit SSH config:
```shell
nano ~/.ssh/config
```
Add:
```plain text
Host aur.archlinux.org
User aur
IdentityFile ~/.ssh/id_rsa
IdentitiesOnly yes
```
Set permissions:
```shell
chmod 700 ~/.ssh
chmod 600 ~/.ssh/config
chmod 600 ~/.ssh/id_rsa
```
---
## 🔁 3. Start SSH Agent and Add the Key
### ➤ Standard method:
```shell
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```
### ➤ If agent refuses operation (Wayland/GNOME issue):
```shell
export SSH_AUTH_SOCK=$(gpgconf --list-dirs agent-ssh-socket)
gpgconf --launch gpg-agent
ssh-add ~/.ssh/id_rsa
```
---
## ✅ 4. Test SSH Access to AUR
```shell
ssh -T aur@aur.archlinux.org
```
Expected output:
```plain text
Welcome to AUR, kanishkmishra143! Interactive shell is disabled.
```
---
## 🚀 5. Push to AUR Git Repository
### ➤ Set remote inside local AUR repo (e.g. sink-switch):
```shell
git remote remove origin || true
git remote add origin ssh://aur@aur.archlinux.org/sink-switch.git
```
### ➤ First-time push:
```shell
git push --set-upstream origin master
```
---
✅ You're now ready to publish and maintain AUR packages from this machine.
# Copr
# 🚀 COPR Package Publish Setup (sink-switch example)
This guide covers everything: from `.spec` file → `.src.rpm` → uploading to your existing COPR repo (`viking412/sink-switch`).
---
## ⚙️ 1. System Requirements
```shell
sudo dnf install -y rpm-build rpmdevtools copr-cli fedora-packager
```
---
## 📦 2. Project Structure
Inside your `sink-switch/` directory, structure should look like:
```plain text
sink-switch/
├── sink-switch
├── sink-switch.spec
├── LICENSE
├── README.md
```
- `sink-switch` → your executable script (must be marked executable)
- `sink-switch.spec` → RPM packaging spec
- `sink-switch-<version>.tar.gz` → autogenerated from `source` directive (optional for script-only)
---
## 🧱 3. Build Source RPM
Run this inside your project folder:
```shell
rpmbuild -bs --define "_sourcedir $(pwd)" --define "_srcrpmdir $(pwd)" sink-switch.spec
```
This will create:
```plain text
sink-switch-<version>.src.rpm
```
---
## 🚀 4. Upload to COPR
Make sure your config is set in `~/.config/copr`:
```plain text
[copr-cli]
login = viking412
username = viking412
token = <your_token>
copr_url = <https://copr.fedorainfracloud.org>
```
Then upload the `.src.rpm`:
```shell
copr build viking412/sink-switch sink-switch-<version>.src.rpm
```
Or auto-match with wildcard:
```shell
copr build viking412/sink-switch sink-switch-*.src.rpm
```
---
## ✅ 5. Check Status
```shell
copr list-builds viking412/sink-switch
```
Or visit:
🔗 [https://copr.fedorainfracloud.org/coprs/viking412/sink-switch/builds/](https://copr.fedorainfracloud.org/coprs/viking412/sink-switch/builds/)
---
## 🧼 6. Clean Up (Optional)
```shell
rm -f *.src.rpm
```
---
## 📌 Notes
- Your `.spec` file should have a `Source0:` line matching your source archive name (or none if script-only)
- Your script (`sink-switch`) must be marked as executable:
```shell
chmod +x sink-switch
```
---
✅ You’re now fully set up to publish and maintain Fedora RPMs via COPR.
## 🛠 Initial Setup
### COPR (Fedora)
1. **Set up your RPM build environment:**
```shell
sudo dnf install rpmdevtools rpmlint fedora-packager rpmdev-setuptree
```
1. **Create your **`**.spec**`** file** inside `~/rpmbuild/SPECS/`.
1. **Place your source tarball** in `~/rpmbuild/SOURCES/`:
```shell
wget <https://github.com/><username>/<repo>/archive/refs/tags/v1.0.tar.gz -O <project>-1.0.tar.gz
```
1. **Build the RPM:**
```shell
rpmbuild -ba ~/rpmbuild/SPECS/<project>.spec
```
1. **Upload to COPR:**
- Create a new project at [https://copr.fedorainfracloud.org/coprs/](https://copr.fedorainfracloud.org/coprs/)<username>/
- Install CLI:
```shell
sudo dnf install copr-cli
```
- Authenticate via `~/.config/copr` (use the API token from COPR web interface).
- Upload:
```shell
copr-cli build <project> ~/rpmbuild/SRPMS/<project>-1.0-1.fc*.src.rpm
```
## 🧰 AUR (Arch Linux)
1. **Create SSH key** (if not already):
```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
```
- Add public key to AUR account.
1. **Generate **`**PKGBUILD**`** and **`**.SRCINFO**`**:**
```shell
makepkg --printsrcinfo > .SRCINFO
```
1. **Push to AUR:**
```shell
git clone ssh://aur@aur.archlinux.org/<project>.git
cd <project>
cp PKGBUILD .SRCINFO LICENSE README.md .
git add .
git commit -m "Initial commit"
git push
```
---
## 🚀 Releasing a New Version
1. **Tag a new release on GitHub:**
- Bump version in your project
- Push and create a new release (vX.Y)
1. **Update spec file:**
- Change `Version`, `Release`, `Source0` accordingly.
- Bump `%changelog`.
1. **Update **`**PKGBUILD**`**:**
- Change `pkgver` and update `source` link and `sha256sums`:
```shell
updpkgsums
makepkg --printsrcinfo > .SRCINFO
```
1. **Rebuild:**
- For RPM: `rpmbuild -ba <spec>`
- For AUR: `git commit -am "vX.Y release"` and push
---
## ❓ Common Issues & Fixes
| Issue | Fix | 
| ---- | ---- | 
| `invalid .SRCINFO` on AUR push | Ensure `.SRCINFO` is generated after editing `PKGBUILD` | 
| COPR `%prep` fails | Check that tarball matches the folder it extracts to | 
| Authentication failure (GitHub) | Use SSH remote and add correct SSH key | 
| AUR push error: `refspec master` | Run `git branch -M master` before pushing | 
| Missing license/doc | Ensure `LICENSE` and `README.md` exist in your source | 
