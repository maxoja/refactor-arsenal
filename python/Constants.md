Hardcoded literals should be somehow taken care so that it's less vulnerable to changing and typing mistakes.
As python's core does not support read-only variable, specifically for this language, there're some steps for handling this (not in order and depending on context).

- Extract variables with all caps convention even though it will still be rewritable : `READ_ONLY_VARIABLE_NAME`
- Extract enum classes : Refer to Enums.md
- Extract a seperate code file that only keeps constant/enums
