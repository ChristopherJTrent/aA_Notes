ByeBug is the [[Ruby]] debugger that we use in a/A's course. 
Each file that you wish to debug with ByeBug needs to have the following:
```ruby
require "byebug"

# some code

debugger #Execution will halt here and debugging will begin.
```

Once execution has halted, there will be the following command line options available.
- `l <start>-<end>`: update the displayed code to show the specified line range
- `[s]tep`: enter the next method call. See: Step-Into in visual studio
- `[b]reak <line>`: add a breakpoint at the specified line.
- `[c]ontinue`: proceed with execution until the next breakpoint
- `display <variable>`: display the value of the specified variable

