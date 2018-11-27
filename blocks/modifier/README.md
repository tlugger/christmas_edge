Modifier
========
The modifier block adds attributes to existing signals as specified. If the `exclude` flag is set, the block instantiates new (generic) signals and passes them along with *only* the specified `fields`.

Properties
----------
- **exclude**: If checked (true), the attributes of the incoming signal will be excluded from the outgoing signal. If unchecked (false), the attributes of the incoming signal will be included in the outgoing signal.
- **fields**: List of attribute names and corresponding values to add to the incoming signals.

Inputs
------
- **default**: Any list of signals.

Outputs
-------
- **default**: One signal for every incoming signal, modified according to `fields`.

Commands
--------
None

