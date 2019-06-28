# Rails

For the life of me, I can never get the `mysql2` to install correctly the first
time, usually due to openssl and homebrew.  Here is the command to fix it.

```
gem install mysql2 -v '0.5.2' -- --with-ldflags=-L/usr/local/opt/openssl/lib
--with-cppflags=-I/usr/local/opt/openssl/include
```
