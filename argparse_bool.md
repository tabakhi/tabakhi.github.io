# Introduction
Python has the module argparse to parse command line options. I use this occassionally but I had some trouble using it to parse boolean options.
I hope this page helps others like me who also want to parse boolean options.

# The Code
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
