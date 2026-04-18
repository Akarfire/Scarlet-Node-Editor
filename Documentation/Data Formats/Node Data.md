Information that describes node's functionality, applicability and possible configuration. This information is stored in some sort of a database and accessed by *Node Type Name*.

```json
"NodeType_1" : {
	
	"display_name" : "Node_1",
	"description" : "This is a pretty cool node that does something.",
	"inputs" : {
		"in_pin_1" : {
			"allowed_types" : ["float", "int"],
			"display_name" : "Number",
			"max_connections" : 1,
			"default_value": NONE // NONE means this input has no default value and must have at least one valid connection. Alternatively you can specify any default value, that will be used in cases, when nothing is connected to this input pin.
		},
		...
	},
	"outputs" : {
		"out_pin_1" : {
			"type" : "string",
			"display_name" : "Text",
			"max_connections" : 0 // 0 means unlimited connections
		},
		...
	},
	
	// Non-input parameters, that can affect node's behavior
	// This parameters are inputted/controlled through custom node UI
	"configuration_parameters" : {
		"param_1" : {
			"default_value" : "1" // Configuration parameters MUST provide a default value
		}
	},
	
	"display" : {
		"node_html" : "Nodes/node.html",
		"custom_css" : "<css code here>"
	}
}
```