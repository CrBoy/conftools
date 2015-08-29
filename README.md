# conftools - A tool describing conference stuffs

It's a crazy idea. I am imagining a tool for conference organizers.
The basic is to design a DSL for writing a "spec" of a conf.
After the spec, an automated process may be performed, to determine the schedule of preparation.

(Oops, it seems like the flow of EDA tools? Haha.)

## Document First

At first, I am trying to design the DSL (in Ruby). The tool itself exists in the future.

```
require 'conftools'

foodconf = Conference.new "Food Conf 2015" # the conf title

foodconf.must_have 2.tracks

# a possible syntax
# foodconf.must_have :lightning_talk, at: '17:00', duration: '1h'
foodconf.must_have :lightning_talk { |lt|
	lt.at '17:00'
	# lt.duration '1h'
	lt.must_have 10.slots
	lt.each_with 5.minutes, rest: 1.minute
}

foodconf.may_have :stickers, designer: 'Nobody'

foodconf.launch!
```

## Patches Welcome!

This project is welcome for patches, design or code.