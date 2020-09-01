# Parsing boolean options in Python
## Introduction
Python has the module argparse to parse command line options. I use this occassionally but I had some trouble using it to parse boolean options.
I hope this page helps others like me who also want to parse boolean options.

## The Code
```
#!/usr/bin/env python
import argparse

if __name__ == '__main__':

    parser = argparse.ArgumentParser(description='Example code to parse boolean options')
    parser.add_argument('--publish', action='store_false', required=False, help='Publish something')
    parser.add_argument('--update', action='store_true', required=False, help='Update something')

    args = parser.parse_args()
    
    print('Update: %s' % (args.update))
    print('Publish: %s' % (args.publish))
```

## Explanation
The key to parsing boolean options is use `action='store_true' or action='store_false'`.
If the action is `store_true`, and the option is not specified on the command line, the variable will be `False`.
If the option is specified, it will be `True`.

For `action=store_false`, the opposite is true. If the option is specified on command line, the variable will be `False`.

## Sample Output

Without specifying any options:
```
$ ./parsebool.py 
Update: False
Publish: True
```

The update flag is false while the publish flag is true.

When we specify the options, the update flag is true and the publish flag is false.
```
$ ./parsebool.py --update --publish
Update: True
Publish: False
```
