Replicator
==========
The Replicator block multiplies each incoming signal. The number of multiplied signals will be the same as the length of the list configured in the *list* property.  Each signal emitted will be the same as the original incoming signal, with an added attribute (Attribute Title) whose value corresponds to the *list* value at the same index.

Properties
----------
- **list**: An expression property that needs to evaluate to a list. A signal will be notified from the block for each item in the list.
- **title**: Name of attribute to be added with the corresponding list value.

Inputs
------
None

Outputs
-------
None

Commands
--------
None

Example
-------
Block Config:
```
{
  'title': 'meal',
  'list': '{{ $meals }}'
}
```
Input Signal:
```
{
  'type': 'meal',
  'meals': ['pork chop', 'pizza', 'chicken']
}
```
3 Output Signals:
```
{
  'type': 'meal',
  'meals': ['pork chop', 'pizza', 'chicken'],
  'meal': 'pork chop'
}
{
  'type': 'meal',
  'meals': ['pork chop', 'pizza', 'chicken'],
  'meal': 'pizza'
}
{
  'type': 'meal',
  'meals': ['pork chop', 'pizza', 'chicken'],
  'meal': 'chicken'
}
```

