# MongoDB driver for Python Twisted

This package started out as a fork of fiorix/mongo-async-python-driver.
However, to implement the more difficult features of a MongoDB driver such as
failover, it was nearly completely rewritten.

The primary features of the rewrite include:

 * reconfiguration of protocol connections upon master change.
 * failover to new master upon AutoReconnect failure.
 * depend on pymongo to avoid in tree pymongo driver to avoid drift.
 * Use python bson driver rather than in tree version.
 * tries to be careful about building and parsing protocol strings to improve throughput.
 * use namedtuple for message structures.

This particular fork of txmongo has added authentication support for the connection pool.
The authentication is carried out using the "mongo_cred" method. The credentials are cached
for each database and the authorization is carried out on a per socket basis for the connection
pool as and when required. This particular fork uses helper functions from the PyMongo v2.5 to 
perform nonce and key generation to carry out the authentication. 


# Installing

You can use setuptools to install this txmongo fork.

```sh
sudo python setup.py install
```

# Packages

## Debian

Packing for debian exists in debian/, you can build yourself a package
(remember to update debian/changelog) if you make changes.

```sh
dpkg-buildpackage -b
```

Then look for the package in your home directory.

## Fedora

```sh
rpmbuild -bb python-txmongo.spec
```

You might need to download Source0 from the .spec and place it in
rpmbuild/SOURCES first.

# Contributing

If this fork provides the features you need, feel free to add to it. I'll try
to be responsive to merge requests.
