# Angular中的ngRepeat使用心得

前段时间在实际项目中遇到一个问题，前端通过Ajax获取到一段数据，其中包括一段整形数字，这个数字表示一个动态的业务值，而这个值是由客户决定的。

OK，问题来了，我现在要使用`ngRepeat`来循环这个值，比如，客户设置了10，那么我就要循环10次，如果是12，就循环12次，咋一眼看上去并不难，但是如何用`ngRepeat`来循环呢?

我们都知道，ngRepeat是循环一个数组或对象，比如像下面这样

```html
<tr ne-repeat='t in ["a", "b", "c"]'>
  //....
</tr>
```

但是如果只给你一个值，如何弄呢？这个，我使用了过滤器来解决这个问题

具体看代码：

过滤器代码：

```javascript
app.filter('range', function () {
  return function (total, input, step) {
    //定义步长
    var _step = (angular.isDefined(step) && angular.isNumber(step)) ? step : 1;

    if (angular.isNumber(input)) {
      var _input = parseInt(input);
      //如果步长为1
      if (_step == 1) {
        for (var i = 0; i < _input; i++) {
            total.push(i+1);
        }
      }
      //如果大于1
      if (_step > 1) {
        for (var i = 0; i < _input; i += _step) {
            total.push(i+1);
        }
      }
    }

    return total;
  }
})
```

HTML中则是这样：

```html
<tr ng-repeat="n in [] | toRange : resultsData.tableNum">
```

`resultsData.tableNum` 就是我们拿到了数值，通过过滤器`toRange`，将拿到的数值转换为具有这个数值个数的数组，这个数组会自动赋值给空数组，作为循环对象。
