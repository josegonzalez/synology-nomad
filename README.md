# HashiCorp Nomad Package for Synology DSM 7+

# Building the .spk package

Requires `curl` and `unzip`.
Nomad binary will be downloaded on demand and bundled with the final .spk pacakge.

```bash
git clone https://github.com/prabirshrestha/synology-nomad.git
cd synology-nomad
./build.sh
```

To change the version to nomad binary or architecture set the environment version.

```bash
ARCH=amd64 NOMAD_VERSION=1.4.0 ./build.sh
ARCH=arm64 NOMAD_VERSION=1.4.0 ./build.sh
```

# Installing the package

Use the package center from Synology DSM to import the nomad spk file.
* A user `nomad` will be created.
* A share `nomad` will be created. For example: `/volume1/nomad`.
* Default configuration can be found on the share in `/path_to_nomad_share/etc/nomad.d/nomad.hcl`.
* Data directory for nomad is set as `/path_to_nomad_share/var/lib/nomad`

# Accessing Nomad UI

Nomad is accessiblity via the `synologyip:4646` port. Since acl is enabled you will need to
loging via ssh and run `nomad acl boostrap` to generate the initial token. You can then use the
`SecretID` as token to authorize the UI portal or generate other tokens.

```bash
$ nomad acl bootstrap
Accessor ID  = 5325e529-8048-2a6a-711e-8a1110562c93
Secret ID    = fe672cf4-16b0-af1d-3db5-1832a8ec4c7d
Name         = Bootstrap Token
Type         = management
Global       = true
Create Time  = 2022-12-15 03:04:34.932856392 +0000 UTC
Expiry Time  = <none>
Create Index = 24
Modify Index = 24
Policies     = n/a
Roles        = n/a
```

# LICENSE

MIT.
For nomad binary refer to the Nomad license.
