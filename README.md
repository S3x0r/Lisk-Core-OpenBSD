<h2>Tutorial how to install Lisk Core node on OpenBSD 6.4 amd64</h2>

1. Install tools needed:<br>
   pkg_add curl automake libtool git<br>

2. Install nodejs:<br>
   pkg_add node

3. Install postgresql:<br>
   pkg_add postgresql-server

4. Create user "lisk":<br>
   adduser lisk

5. Configure postgresql:<br>
   su _postgresql<br>
   initdb -D /var/postgresql/data -U lisk<br>
   rcctl enable postgresql<br>
   rcctl start postgresql<br>
   createdb lisk_test -O lisk<br>

6. Clone Lisk sources:<br>
   git clone https://github.com/LiskHQ/lisk.git<br>
   cd lisk<br>
   git checkout (version) -b (version)<br>
   npm install<br>

   >if there is an error: "cb() never called", again:<br>
   npm install<br>

7. Install modules:<br>
   npm install node-gyp-build<br>
   npm install sodium-native@1<br>

8. Edit file: node_modules/sc-uws/src/Hub.cpp<br>
   comment lines: 128, 130, 131, 132<br>

9. Rebuild module:<br>
   npm rebuild<br>

10. Start node:<br>
    node app.js --network testnet<br>

Done!
