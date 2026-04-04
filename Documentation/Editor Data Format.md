
During editing, node graph is stored as an array of node data structures, that contain it's name, editor data and connections to other nodes

```json
[
	{
		"name" : "Node_1",
		"inputs" : {
			"in_pin_1" : {"Node_2" : ["out_pin_1"]}, 
			"in_pin_2" : {"Node_3" : ["out_pin_1"]}, 
			...},
		"outputs" : {
			"out_pin_1" : {"Node_4" : ["in_pin_1"]}, 
			"out_pin_2" : {"Node_4" : ["in_pin_2"]}, 
			...},
		"edit_data" : 
		{
			"position" : [x, y],
			...
		}
	},
	...
]
```
