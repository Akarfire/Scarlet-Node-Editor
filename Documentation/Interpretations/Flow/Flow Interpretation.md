
*Example resulting flow*

**Flow Chart**:
Contains information about the node graph's execution order.
```c++
Node_0:
	Node_1
	
Node_1:
	Node_2
	
Node_2:
	Node_3
	Node_4
	
Node_3:
	Node_5
	
Node_4:
	Node_5
	Node_2 // Backlink, results in a loop
	
Node_5:
	Node_6	
```

**Input Chart**:
Contains information about each node's inputs.
```c++
Node_0:

Node_1:
	(Node_0, out_0)
	(HNode_1, out_0)
	NONE
	
Node_2:
	(HNode_3, out_0):
		(HNode_1, out_0)
		(HNode_2, out_0)
		(HNode_1, out_0)
		
Node_3:
	NONE
	NONE
	(HNode_3, out_1):
		(HNode_1, out_0)
		(HNode_2, out_0)
		(HNode_1, out_0)

Node_4:
	(HNode_3, out_2):
		(HNode_1, out_0)
		(HNode_2, out_0)
		(HNode_1, out_0)
		
Node_5:
	NONE
	NONE
	NONE
	
Node_6:
	NONE
	(Node_5, out_0)
	NONE
```

Flow node interpretation requires the following node format:
<p align="center">
  <img src="../../Images/FlowNode.png"  width="50%">
</p>
Each node of the sequence must have at least one *Flow Input* and at least one *Flow Output* pin (exceptions to this rule are "border" nodes that only have one type of Flow pins: input or output). Such nodes can have any number of secondary input and output pins. Inputs can come from either node hierarchies (see [Hierarchical Interpretation](../Hierarchical/Hierarchical%20Interpretation.md)), that branch out from the flow nodes, or from outputs of other flow nodes (output values are usually cached, so they can be used by the following nodes).

Nodes that branch out from Inputs are the same as nodes in ***Hierarchical Interpretation***.