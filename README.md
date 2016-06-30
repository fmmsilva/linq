## linq
[linq.js](http://linqjs.codeplex.com/) - LINQ for JavaScript library packaged for node.js

This contains only the core library without the jquery or rx bindings.

### Installation

    npm install linq

### Examples

    sample/tutorial.js
    
    
```javascript
var jsonArray = [
    { "user": { "id": 100, "screen_name": "d_linq" }, "text": "to objects" },
    { "user": { "id": 130, "screen_name": "c_bill" }, "text": "g" },
    { "user": { "id": 155, "screen_name": "b_mskk" }, "text": "kabushiki kaisha" },
    { "user": { "id": 301, "screen_name": "a_xbox" }, "text": "halo reach" }
]
// ["b_mskk:kabushiki kaisha", "c_bill:g", "d_linq:to objects"]
var queryResult = Enumerable.From(jsonArray)
    .Where(function (x) { return x.user.id < 200 })
    .OrderBy(function (x) { return x.user.screen_name })
    .Select(function (x) { return x.user.screen_name + ':' + x.text })
    .ToArray();
// shortcut! string lambda selector
var queryResult2 = Enumerable.From(jsonArray)
    .Where("$.user.id < 200")
    .OrderBy("$.user.screen_name")
    .Select("$.user.screen_name + ':' + $.text")
    .ToArray();
```

#### What's changed from the browser version?

Not much:

* Minor changes to tests so they can be run on server side
* Sample tutorial is a .js file instead of .htm and can be run directly with node

#### License

[MIT License] (http://opensource.org/licenses/MIT)
