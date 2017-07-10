# f5-agility-labs

This repository contains the build infrastructure used to create lab content
for F5 Networks Agility Labs hosted at http://clouddocs.f5.com

It is recommended that you use the Sphinx lab template here:

https://github.com/0xHiteshPatel/f5-agility-lab-template

This repository leverages a CI/CD toolchain with full build, test and publish
to production environment.

# Install/Build Content

- `git clone https://github.com/f5devcentral/f5-agility-labs.git`
- `cd f5-agility-labs`
- `script/setup`
- Built content will be in the `_build` directory
- `script/server` will start a python SimpleHTTPServer in `_build`
- Browse to `http://localhost:8000`

# Adding your Lab

**At this time only F5 Networks employees can request addition of a lab**

To add your lab to this repository please email:

 - Hitesh Patel
 - Nicolas Menant

Be sure to include your lab repository URL.

# Repo Structure

All labs are included as git submodules in the `labs` directory.  The submodule
tracks the `master` branch on the remote repository.  It should be assumed that
all commits to `master` will be published to a production environment.

The scripts in the `script` directory automatically build HTML and PDF content
and output to the `_build/<lab_name>/[html|pdf]/` directory.

During build an index page is generated using the Sphinx project in `docs`.  The
generated index is then copied to the `_build` directory.

# Branches

- `master`: Protected branch; **HEAD publishes to production**; No push access
- `develop`: Protected branch; Pull Requests are tested through Travis CI
  before merge

All modifications to this repo should be via a Pull Request to the `develop`
branch.  PR's will be tested before merge.  Repo admins will then merge
`develop` to `master` as required to publish to production.

# Update Lab Submodule

To `pull` the latest commits for **ALL** submodules:

`git submodule update --recursive --remote`

To `pull` the latest commits for a specific submodule:

`git submodule status labs/<name>`

Push new commit hashes for submodules:

- `git commit -a -m "commit msg"`
- `git push`

# Add Lab Submodule

- `git submodule add <repo_url> labs/<name>`
- `git commit -a -m "commit msg"`
- `git push`
