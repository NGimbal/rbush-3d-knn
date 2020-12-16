## rbush-knn [![Build Status](https://travis-ci.org/mourner/rbush-knn.svg?branch=master)](https://travis-ci.org/mourner/rbush-knn)

###WIP
Intended to work with rbush-3d at https://github.com/Eronana/rbush-3d

_k_-nearest neighbors search for [RBush-3d](https://github.com/Eronana/rbush-3d).
Implements a simple depth-first kNN search algorithm using a priority queue.

```js
var RBush = require('rbush');
var knn = require('rbush-knn');

var tree = new RBush(); // create RBush tree
tree.load(data); // bulk insert
var neighbors = knn(tree, 40, 40, 40, 10); // return 10 nearest items around point [40, 40, 40]
```

You can optionally pass a filter function to find k neighbors that satisfy a certain condition:

```js
var neighbors = knn(tree, 40, 40, 40, 10, function (item) {
    return item.foo === 'bar';
});
```

### API

**knn(tree, x, y, z, [k, filterFn, maxDistance])**

- `tree`: an RBush tree
- `x`, `y`: query coordinates
- `k`: number of neighbors to search for (`Infinity` by default)
- `filterFn`: optional filter function; `k` nearest items where `filterFn(item) === true` will be returned.
- `maxDistance` (optional): maximum distance between neighbors and the query coordinates (`Infinity` by default)


Forked from [rbush-knn](https://github.com/mourner/rbush-knn)
