---
sidebar_current: "FAQ"
---

<h1 id=#>Frequenly Asked Questions</h1>

This will hopefully serve as a location in which problems people have run into can be aggregated for future Vagrant users.

* [bash: /tmp/vagrant-shell: /bin/bash^M: bad interpreter: No such file or directory](#bad-interpreter)

<h4 id="bad-interpreter"> bash: /tmp/vagrant-shell: /bin/bash^M: bad interpreter: No such file or directory</h4>

This issues is caused when a shell provisioning file has the wrong line endings. By default windows will create files with line endings of crlf (\r\n). Unfortunately linux does not like crlf (\r\n) line ending and requires lf (\n) line endings for shell scripts. If you convert all crlf (\r\n) line endings into lf (\n) this problem should be solved. Below is an example of the issue in action. It creates a test script with crlf (\r\n) line endings, prints out special characters (^M) and then tries to run the file. As you can see the error of bad interpreter is caused by crlf (\r\n) line endings.

```
$ echo -e '#!/bin/bash\r\necho 100\r\nsleep 100' > test.sh && cat -v test.sh && chmod +x test.sh && ./test.sh
#!/bin/bash^M
echo 100^M
sleep 100
bash: ./test.sh: /bin/bash^M: bad interpreter: No such file or directory
```
\[[Back To Top](#)\]
