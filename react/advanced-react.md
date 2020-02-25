**Reconciliation**

Reconciliation means the restoration of friendly relations or religiously, the end of enstrangement. :D
In React, reconciliation is the term used to denote how the component gets rerendered when something changes.

How does react figure out how to update the UI?

React implements a heuristic O(n) algorithm based on two assumptions:

Two elements of different types will produce different trees.
The developer can hint at which child elements may be stable across different renders with a key prop.

(heuristic - a practical method not guaranteed to be optimal or perfect, but sufficient for the immediate goals)
Note: When a component updates, the instance stays the same, so that state is maintained across renders. 

**The Diffing Algorithm**

1. Dom elements of different types
```
<div>
  <Counter />
</div>

<span>
  <Counter />
</span>
```
Solution: destroy old Counter, mount new Counter

2. Dom elements of the same type
```
<div className="before" title="stuff" />

<div className="after" title="stuff" />
```
Solution: attributes are compared. Here, its smart enough to know only the classname changed. So only that it updated.

3. Recursing on children
```
<ul>
  <li>first</li>
  <li>second</li>
</ul>

<ul>
  <li>first</li>
  <li>second</li>
  <li>third</li>
</ul>
```
Solution: Smart  to know only one item got added. Updates only that.

GOTCHA: adding a new key to the beginning is a bad idea. React would tear all down.

Proper solution: Use keys. Keys has to be unique in the scope. Generate one or use the unique id of the item.
Try not to use index of the map function unless its impossible. If the component supports reordering, it could be an issue.
