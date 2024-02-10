Rspec is a [[Ruby]] testing framework that allows us to write unit tests for our ruby code.

Rspec projects are required to have the following directory structure:
```
/project
	/lib
		<ruby code files matching /(?<filename>*.)\.rb/>
	/spec
		<ruby spec files matching /\k{filename}_spec\.rb/>
```

