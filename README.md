# Tutorial how to install Lisk Core node on OpenBSD 6.4 amd64

1. Install tools needed:<br>
   pkg_add curl automake libtool git
<br>
2. Install nodejs:<br>
   pkg_add node
<br>
3. Install postgresql:<br>
   pkg_add postgresql-server
<br>
4. Create user "lisk":<br>
   adduser lisk
<br>
5. Configure postgresql:<br>
   su _postgresql
   initdb -D /var/postgresql/data -U lisk
   rcctl enable postgresql
   rcctl start postgresql
   createdb lisk_test -O lisk
<br>
6. Clone Lisk sources:<br>
   git clone https://github.com/LiskHQ/lisk.git
   cd lisk
   git checkout (version) -b (version)
   npm install
<br><br>
   >if there is an error: "cb() never called", again:
   npm install
<br>
7. Install modules:<br>
   npm install node-gyp-build
   npm install sodium-native@1
<br>
8. Edit file: node_modules/sc-uws/src/Hub.cpp<br>
   comment lines: 128, 130, 131, 132
<br>
9. Rebuild module:<br>
   npm rebuild
<br>
10. Start node:<br>
    node app.js --network testnet
<br><br>
Done!
