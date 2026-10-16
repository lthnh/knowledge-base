The assertions are of two types, mainly immediate and concurrent assertions.
## Immediate Assertions
Simple, can write with if-else construct.

```systemverilog
always @*
	assert( ~(enable && store))
	else $error (“Not able to store the result”);
```

We can also check assertions on the rising edge of clock:

```systemverilog
property NotEnableNotStore;
	@(posedge clk) (~(enable && store));
endproperty
```
## Concurrent Assertions
This type is used most of the time.

The general rule of thumb is to separate assertion and property.