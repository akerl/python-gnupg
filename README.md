# python-gnupg #

Fork of [python-gnupg-0.3.2](https://code.google.com/p/python-gnupg/), patched
to fix a potential vulnerability which could result in remote code execution,
do to unsanitised inputs being passed to ```subprocess.Popen([...], shell=True)```.

### Installation ###

#### From [PyPI](https://pypi.python.org) ####
It's simple. Just do:
```
[sudo] pip install gnupg
```

#### From this git repository ####
To install this package from this git repository, do:

```
git clone https://github.com/isislovecruft/python-gnupg.git
cd python-gnupg
make install
make test
```

Optionally to build the documentation after installation, do:
```
make docs
```

To get started using python-gnupg's API, see the [online documentation](https://python-gnupg.readthedocs.org/en/latest/),
and import the module like so:
```
>>> import gnupg
```

The primary interface class you'll likely want to interact with is
[```gnupg.GPG```](https://python-gnupg.readthedocs.org/en/latest/gnupg.html#gpg):
```
>>> gpg = gnupg.GPG(binary='/usr/bin/gpg',
...     homedir='./keys',
...     keyring='pubring.gpg',
...     secring='secring.gpg')
>>> batch_key_input = gpg.gen_key_input(
...     key_type='RSA',
...     key_length=4096)
>>> print batch_key_input
Key-Type: RSA
Name-Email: isis@wintermute
Key-Length: 4096
Name-Real: Autogenerated Key
%commit

>>> key = gpg.gen_key(batch_key_input)
>>> print key.fingerprint
245D8FA30F543B742053949F553C0E154F2E7A98

```

### Bug Reports & Feature Requests ###

Currently, the bugtracker is
[here](https://github.com/isislovecruft/python-gnupg/issues) on Github. This
may change in the future, but for now please feel free to use it to make
bugreports and feature requests.

Public comments and discussions are also welcome on the bugtracker, or as
[tweets](https://twitter.com/isislovecruft).

Patches are greatly appreciated, and if unsuitable for merging I will make
improvement suggestions based on code review until the patch is acceptable.
