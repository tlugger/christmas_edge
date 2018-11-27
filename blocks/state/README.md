AppendState
===========
The AppendState block adds a 'state' attribute to the `getter` input signal.  The block appends an attribute from `setter` signal to the `getter` input signal, and will the output signal will also include a `prev_state` attribute of the block's previous state. The state's attribute name can be configured with the `State Name` property, and the value is assigned based on the expression in the `State` property.

Properties
----------
- **backup_interval**: An interval of time that specifies how often persisted data is saved.
- **group_by**: The signal attribute on the incoming signal whose values will be used to define groups on the outgoing signal.
- **initial_state**: The state when none has been set by an incoming signal. If the `initial_state` is a python expression, it is evaluated at configuration. For example, if the `initial_state` is configured as `{{ datetime.datetime.utctime() }}`, the value of `initial_state` will the be time at configuration.
- **load_from_persistence**: If `True`, the block’s state will be saved when the block is stopped, and reloaded once the block is restarted.
- **state_expr**: Property used to assign a state. If the expression cannot be evaluated, the state will not change.
- **state_name**: String property that is the name of the signal attribute for the appended state.

Inputs
------
- **getter**: Any list of signals. These signals will get assigned a state and/or pass through the block.
- **setter**: Signals passed to this input set the state of the block. Each signal is evaluated against `state_expr` to determine the new state of the block for the signal's group.

Outputs
-------
- **default**: The original signal along with the configured `state_name` attribute and the `prev_state` attribute.

Commands
--------
- **current_state**: Get the current state of the block is applying to the signals.
- **groups**: Display the current groupings of signals.

StateChange
===========
The StateChange block maintains a state based on an attribute of the input signal.  When the state changes, a signal is emitted that contains the `state` and `prev_state`.

Properties
----------
- **backup_interval**: An interval of time that specifies how often persisted data is saved.
- **exclude**: If checked (true), the original signal sent into the block will be excluded from the signal sent out of the block. If unchecked (false), the output signal will include the original signal sent into the block.
- **group_by**: The signal attribute on the incoming signal whose values will be used to define groups on the outgoing signal.
- **initial_state**: The state when none has been set by an incoming signal. If the `initial_state` is a python expression, it is evaluated at configuration. For example, if the `initial_state` is configured as `{{ datetime.datetime.utctime() }}`, the value of `initial_state` will the be time at configuration.
- **load_from_persistence**: If `True`, the block’s state will be saved when the block is stopped, and reloaded once the block is restarted.
- **state_expr**: Property used to assign a state and be monitored for a change in value. If the expression cannot be evaluated, the state will not change.
- **state_name**: String property that is the name of the signal attribute for the appended state.

Inputs
------
- **default**: Signal with attribute to be set and watched as state.

Outputs
-------
- **default**: When state changes, a signal is notified with attributes `state`, `prev_state`, and `group`. If `exclude` is _unchecked_ then the signal that changed the state will have the attributes added to it.

Commands
--------
- **current_state**: Get the current state of the block is applying to the signals.
- **groups**: Display the current groupings of signals.

Switch
======
The Switch block emits signals from either the True or False output terminal based on what the `State` expression evaluates to.  The `getter` input signal is what gets passed along, and the `setter` input signal is used to determine the state.

Properties
----------
- **backup_interval**: An interval of time that specifies how often persisted data is saved.
- **group_by**: The signal attribute on the incoming signal whose values will be used to define groups on the outgoing signal.
- **initial_state**: The state when none has been set by an incoming signal. If the `initial_state` is a python expression, it is evaluated at configuration. For example, if the `initial_state` is configured as `{{ datetime.datetime.utctime() }}`, the value of `initial_state` will the be time at configuration.
- **load_from_persistence**: If `True`, the block’s state will be saved when the block is stopped, and reloaded once the block is restarted.
- **state_expr**: Property that evaluates to a true or false state. If the expression cannot be evaluated, the state will not change.

Inputs
------
- **getter**: Any list of signals. Signals that get assigned a state and/or pass through the block.
- **setter**: Signals passed to this input set the state of the block. Each signal is evaluated against `state_expr` to determine the new state of the block for the signal's group.

Outputs
-------
- **false**: getter signals pass through to the false output by default until state is changed to `True`.
- **true**: getter signals pass through to the true output if the last setter signal set the state to `True`.

Commands
--------
- **current_state**: Get the current state of the block is applying to the signals.
- **groups**: Display the current groupings of signals.

