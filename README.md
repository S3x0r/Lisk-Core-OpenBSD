# Tutorial how to install Lisk Core node on OpenBSD 6.4 amd64

1. Install tools needed:
   pkg_add curl automake libtool git

2. Install nodejs:
   pkg_add node

3. Install postgresql:
   pkg_add postgresql-server

4. Create user "lisk":
   adduser lisk

5. Configure postgresql:
   su _postgresql
   initdb -D /var/postgresql/data -U lisk
   rcctl enable postgresql
   rcctl start postgresql
   createdb lisk_test -O lisk

6. Clone Lisk sources:
   git clone https://github.com/LiskHQ/lisk.git
   cd lisk
   git checkout (version) -b (version)
   npm install

   >if there is an error: "cb() never called", again:
   npm install

7. Install modules:
   npm install node-gyp-build
   npm install sodium-native@1

8. Edit file: node_modules/sc-uws/src/Hub.cpp
   comment lines: 128, 130, 131, 132

9. Rebuild module:
   npm rebuild

10. Start node:
    node app.js --network testnet

Done!
