---
title: subprocess
date: 2018-07-31 00:30:19
tags:
---


https://stackoverflow.com/questions/6657690/python-getoutput-equivalent-in-subprocess

[python Subprocess](https://docs.python.org/3/library/subprocess.html#module-subprocess)

import subprocess
process = subprocess.Popen(['ls', '-a'], stdout=subprocess.PIPE)
out, err = process.communicate()
print(out)
