
### Hierarchical Interpretation

This node interpretation results in a hierarchical structure (a tree), where to resolve root node, you would need to recursively resolve nodes from descending branches.

*Real example: Blender's Shader Nodes.*

```cpp
Root:
	Node_1:
		Node_2
		Node_3
		Node_4:
			Node_5
			Node_6
			...
```

Hierarchical interpretation requires one of the two following node formats:
<p align="center">
  <img src="../Images/TreeNodes.png"  width="50%">
</p>
Each node can have as many Input/Output pins, but only one Output/Input one.


### Language Interpretation

This interpretation results in a sequence of root nodes, that are supposed to be interpreted sequentially. Each node in the sequence is, in fact, a root of a node tree, which this node depends on. To resolve the sequence, you would need to sequentially resolve root nodes, that, in their turn, require recursive resolution of descending branches.

*Real example: Unreal Engine's Blueprints.*

```cpp
Node Sequence = [

Node_1:
	Node_2
	Node_3
	Node_4:
		Node_5

Node_6
Node_7:
	Node_8:
		Node_9
		
Node_10

]
```

Language Interpretation nodes, that are structured in a sequence, generally look like this:
<p align="center">
  <img src="../Images/LanguageNode.png"  width="50%">
</p>
Each node of the sequence must have a *Flow Input* and a *Flow Output* pin (exceptions to this rule are "border" nodes that only have one Flow pin: input or output). Such nodes can have as many secondary input and output pins. Inputs can come from either node trees, that branch out from this language node, or from outputs of other language nodes (output values are usually cached, so they can be used by the following nodes).

Nodes that branch out from Inputs are the same as nodes in ***Hierarchical Interpretation***.